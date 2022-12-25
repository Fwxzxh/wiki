---
title: MVVM WPF XAML
description: Notas del curso de WPF usando el patrón MVVM y XAML
published: true
date: 2022-12-24T18:10:29.260Z
tags: cursos, mvvm, c#, wpf, xaml
editor: markdown
dateCreated: 2022-12-24T18:10:23.800Z
---

# Recursos

- [Awesome WPF](https://github.com/Carlos487/awesome-wpf)
- [WpfTutorial](https:www.wpf-tutorial.com)

# MVVM

- Significa Model, View, ViewModel.
- En el Model tenemos las clases que modelan los datos de nuestra
  aplicación.
- En el View, tenemos las vistas o las pantallas (UI) de nuestra
  aplicación.
- En el ViewModel tenemos la lógica de la UI y conecta al Model y al
  ViewModel.
- Lo común es tenerlo en carpetas separadas, pero también pueden estar
  en proyectos separados.
- Esto nos ayuda a tener una aplicación más fácil de mantener, de
  extender y testear.
- Se basa en el Binding.

## Funcionamiento

- El `View`, obtiene información mediante el `DataBinding` y recibe
  notificaciones del `ViewModel`.
- EL `ViewModel` manda actualizaciones al `Model` y recibe
  notificaciones del `Model`.

## El `Model`

- Tiene el modelo de los datos.
- Contiene la lógica de negocio y de validación.
- Todo tipo de clases en general.

## La `View`

- El código de lo que se ve en la pantalla.
- `Code behind` limitado, sin lógica de negocio.
- Obtiene datos del `ViewModel` a través de `bindings` o métodos.

## El `ViewModel`

- Intermediario entre el `View` y el `Model`.
- Contiene la lógica del `View`.
- Provee datos desde el `Model` a la `View`.

## `INotifyPropertyChanged`

Es una interfaz que podemos implementar para saber cuando el valor de
una propiedad ha cambiado

Cuando dos propiedades se les hizo `Binding`, ambas reciben la
notificación:

- El `View` se mantiene actualizado con los valores del `Modelo`
  (`OneWay`).
- El `Model` se mantiene actualizado con los valores de la `View` y
  viceversa. (`TwoWay`)

Funciona de la siguiente manera:

1.  La clase que representa el `ViewModel` implementa la interfaz
    `INotifyPropertyChanged`.
2.  Cambios a una propiedad disparan un evento.
3.  Propiedades que hicieron `Binding` a esa propiedad responden al
    evento actualizándose.

### Ejemplo:

Hacemos que nuestra clase que va a funcionar como el `ViewModel`
implemente la interfaz.

``` csharp
public class WeatherViewModel : INotifyPropertyChanged {

    // El evento que vamos a levantar cada que una propiedad cambie.
    public event PropertyChangedEventHandler? PropertyChanged;

    // El método que usaremos para lanzar el evento.
    [NotifyPropertyChangedInvocator]
    protected virtual void OnPropertyChanged([CallerMemberName] string? propertyName = null) {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
}
```

Entonces podemos hacer nuestras propiedades reaccionar a los cambios.

``` csharp
public class WeatherViewModel : INotifyPropertyChanged {

    private string? _query;

    public string? Query {
        get => _query;
        set {
            _query = value;
            // el OnPropertyChanged viene de implementar la interfaz INotifyPropertyChanged
            OnPropertyChanged(nameof(Query));
        }
    }

    // El evento que vamos a levantar cada que una propiedad cambie.
    public event PropertyChangedEventHandler? PropertyChanged;

    // El método que usaremos para lanzar el evento.
    [NotifyPropertyChangedInvocator]
    protected virtual void OnPropertyChanged([CallerMemberName] string? propertyName = null) {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
}
```

Una vez hecho eso podemos usar nuestra propiedad en el `View` y hacer
`Binding`.

``` xml
<!-- El binding va a la propiedad llamada Query,
El modo TwoWay es para que se actualice la propiedad y el campo de texto al mismo tiempo si cambia alguno de los dos,
El Update SourceTrigger se usa para Poner en que condiciones se hace el update.  -->
<TextBox Margin="5 5"
            Text="{Binding Query,
            Mode=TwoWay,
            UpdateSourceTrigger=PropertyChanged}"/>
```

Con esto nuestra propiedad siempre se mantendrá actualizada.

## `ICommand`

Más información [aquí](https://www.c-sharpcorner.com/UploadFile/20c06b/icommand-and-relaycommand-in-wpf/)

Es la propiedad que usaremos para reemplazar eventos en el patrón
`MVVM`.

Los comandos pueden mover algo de la lógica del `Code behind` al
`ViewModel`, esto tiene ventajas:

- Limpia la capa del `View`.
- Permite reutilizarlos entre ventanas.

Existe como una propiedad para los botones.

- Lo cual lo vuelve un remplazo perfecto para `Event Handlers`.

Funciona de la siguiente manera:

1.  El `ViewModel` implementa la interfaz `ICommand`.
2.  La funcionalidad es agregada al método `Execute`.
3.  Validaciones opcionales pueden ser agregadas en el método
    `CanExecute`.
4.  El comando es asignado.

### Ejemplo

Podemos crear el comando en una clase afuera de nuestro `ViewModel` como
en el siguiente ejemplo.

Primero deberíamos de crear el método en nuestro `ViewModel` que
deseamos ejecutar con el comando

``` csharp
public async Task MakeQuery() {
    if (Query != null) {
        var cities = await AccuWeatherHelper.GetCities(Query);

        Cities.Clear();
        foreach (var city in cities)
            Cities.Add(city);
    }
}
```

Después dentro del directorio `ViewModel` Podemos crear una carpeta
llamada `Commands` y allí agregar la clase en la que implementaremos la
interfaz `ICommand`.

``` csharp
public class SearchCommand : ICommand {

    // propiedad del tipo del VM.
    public WeatherViewModel WeatherVm { get; set; }

    // Constructor, obtiene la clase del VM al que pertenece.
    public SearchCommand(WeatherViewModel viewModel) {
        WeatherVm = viewModel;
    }

    // Método que verifica si se puede ejecutar el comando (opcional).
    public bool CanExecute(object? parameter) {
        var query = parameter as string;
        return !string.IsNullOrWhiteSpace(query);
    }

    // Método que ejecuta el commando dado de alta en VM.
    public async void Execute(object? parameter) {
        await WeatherVm.MakeQuery();
    }

    // se encarga de actualizar el valor que se chequea.
    public event EventHandler? CanExecuteChanged {
        // Evento que se triguerea cuando cambia el parametro que se manda al canExecute
        // Dice que hacer con el valor cuando este cambia
        add => CommandManager.RequerySuggested += value;
        remove => CommandManager.RequerySuggested -= value;
    }
}
```

Ahora podemos hacer `Binding` en el `View` para ejecutar el comando,
pero antes necesitamos crear una propiedad en el `ViewModel` para que
nuestro `View` pueda verla.

``` csharp
public class WeatherViewModel : INotifyPropertyChanged {

    // ...

    // Creamos nuestra propedad con el nobre y el tipo de nuestro comando.
    public SearchCommand SearchCommand { get; set; }

    // El método que ejecutará el comando.
    public async Task MakeQuery() {
        if (Query != null) {
            var cities = await AccuWeatherHelper.GetCities(Query);

            Cities.Clear();
            foreach (var city in cities)
                Cities.Add(city);
        }
    }

    // Necesitamos Crear un constructor en nuestro ViewModel
    public WeatherViewModel() {

        // Necesitamos instanciar nuestro comando desde el constructor del ViewModel,
        // Esto porque el constructor de nuestra clase SearchCommand, tiene como parametro
        // Un objeto tipo WheatherViewModel.
        SearchCommand = new SearchCommand(this);
    }

    // ...
}
```

Ahora podemos hacer `Binding` en el `View` Libremente.

``` xml
<!-- El command se hace el binding a una propiedad del VM,
La propiedad se inicializa desde el constructor del VM,
La propiedad es una clase que implementa la interfaz ICommand,
El CommandParameter es el parámetro que se le va a mandar al commando,
Se hizo el binding a la propiedad Query del VM la cual manda una señal cuando cambia,
Y se maneja en evento CanExecuteChanged el cual viene de la interfaz ICommand -->
<Button Margin="5 5"
        Command="{Binding SearchCommand}"
        CommandParameter="{Binding Query}"
        Content="Search"/>
```

El argumento `CommandParameter` sirve para mandar un argumento opcional
al comando, en caso de que sea necesario.

## la clase `ObservableCollection`

Una `ObservableCollection` es una lista que esta al pendiente de
cambios.

Funciona de la siguiente manera:

1.  necesitamos una clase que herede de la clase
    `ObservableCollection<T>`.
2.  Esa clase ya habrá implementado la interfaz
    `INotifyPropertyChanged`.
3.  Se establece una `Binding Source`.
4.  Se actualiza la UI.

### Ejemplo

Primero necesitamos una propiedad de tipo `ObservableCollection` en
nuestro ViewModel.

``` csharp
public ObservableCollection<City> Cities { get; set; }
```

Esta propiedad ya implementa la `INotifyPropertyChanged` así que no
necesitamos nada más

Ahora debemos inicializar la lista en el constructor ya que si esta
lista es inicializada otra vez, el `Binding` se pierde.

``` csharp
public WeatherViewModel() {
    SearchCommand = new SearchCommand(this);
    // Inicalizamos la ObservableCollecition
    Cities = new ObservableCollection<City>();
}
```

Siempre que queramos limpiar o rellenar la lista debemos limpiarla y
rellenarla elemento por elemento o el `Binding` se perderá.

``` csharp
public async Task MakeQuery() {
    if (Query != null) {
        var cities = await AccuWeatherHelper.GetCities(Query);

        Cities.Clear(); // Limpiamos la lista
        foreach (var city in cities) // Agregamos elemento por elemento.
            Cities.Add(city);
    }
}
```

Ahora podemos hacer `Binding` en el `View` para mostrar la lista.

``` xml
<!-- Desde la view hacemos binding a una propiedad del vm como ItemsSource,
y hacemos binding Del SelectedValue a una propiedad del vm -->
<ListView ItemsSource="{Binding Cities}"
          SelectedValue="{Binding SelectedCity}">
    <ListView.ItemTemplate>
        <DataTemplate>
            <Grid>
                <!-- Como ItemsSource fue definido en la listView, nuestro data context es ese,
                asi que podemos acceder a los elementos de ese dataContext -->
                <TextBlock Text="{Binding LocalizedName}"/>
            </Grid>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

El argumento `SelectedValue`, es otra propiedad que podemos usar si
queremos saber que Valor esta siendo seleccionado de la lista, Aquí
creamos una propiedad llamada `SelectedCity` para guardar este valor.

## `IValueConverter`

Más información [aquí](https://www.wpf-tutorial.com/es/39/ligado-de-datos/conversion-de-valores-con-ivalueconverter/)

Nos permite:

- Cambiar el `Model` a lo que la `View` necesita.
- Cambiando entradas en la `View` para el `Model`.

Funciona de la siguiente manera:

1.  Una clase implementa la interfaz `IValueConverter`.
2.  El método `Convert` convierte el `Modelo` a la `View`.
3.  El método `ConvertBack` convierte el `View` a la `Model`

### Ejemplo

Primero deberíamos crear una carpeta dentro de nuestro `ViewModel`
llamada `Converters` y crear una nueva clase que implemente la interfaz
`IValueConverter`.

``` csharp
public class BoolToRainConverter : IValueConverter {

    public object Convert(object value, Type targetType, object parameter, CultureInfo culture) {
        var isRaining = (bool) value;
        if (isRaining)
            return "Currently raining";
        return "Currently not raining";
    }

    public object ConvertBack(object value, Type targetType, object parameter, CultureInfo culture) {
        var isRaining = (string) value;

        return isRaining == "Currently raining";
    }
}
```

Ahora debemos agregar nuestro convertidor a la `View`

Primero debemos agregar el `namespace` donde esta nuestro convertidor en
el `View`, en este caso lo llamamos `converter`.

``` xml
<Window x:Class="WeatherApp.View.WeatherWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:vm="clr-namespace:WeatherApp.ViewModel"
        xmlns:converters="clr-namespace:WeatherApp.ViewModel.ValueConverters"
        mc:Ignorable="d"
        Title="WeatherWindow" Height="600" Width="400">

      <!-- ... -->

</Window>
```

Después debemos agregar el recurso a la `View`.

``` xml
<!-- Declaramos los recursos de la ventana,
La clase WeatherViewModel y declaramos el namespace vm arriba con el namespace del vm  -->
<Window.Resources>
    <vm:WeatherViewModel x:Key="Vm"/>
    <!-- Declaramos nuestro convertidor -->
    <converters:BoolToRainConverter x:Key="BoolToRain"/>
</Window.Resources>
```

Ahora podemos Usar el convertidor donde lo necesitemos.

``` xml
<!-- Usamos un convertidor añadiendo el namespace, el recurso en window.resources
y lo llamamos como se muestra abajo. -->
<TextBlock Text="{Binding HasPrecipitation, Converter={StaticResource BoolToRain}}"
            Foreground="#f4f4f8"
            FontSize="16"
            Margin="20 0"/>
```

El convertidor tomara el `Bool` que hicimos `Binding` en
`HasPrecipitation` y lo pasara por el convertidor dando un resultado.

## Código Ejemplo

App ejemplo de los conceptos usados:

Archivo `WheatherWindow.xaml`, el `View` de la aplicación:

``` xml
<Window x:Class="WeatherApp.View.WeatherWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:vm="clr-namespace:WeatherApp.ViewModel"
        xmlns:converters="clr-namespace:WeatherApp.ViewModel.ValueConverters"
        mc:Ignorable="d"
        Title="WeatherWindow" Height="600" Width="400">
    <!-- aaa -->

    <!-- Declaramos los recursos de la ventana,
    La clase WeatherViewModel y declaramos el namespace vm arriba con el namespace del vm  -->
    <Window.Resources>
        <vm:WeatherViewModel x:Key="Vm"/>
        <!-- Declaramos nuestro convertidor -->
        <converters:BoolToRainConverter x:Key="BoolToRain"/>
    </Window.Resources>

    <!-- Podemos declarar un contexto de datos para el binding de los elementos
    dentro de el elemento, le pasamos el nombre del recurso dado arriba. -->
    <Grid DataContext="{StaticResource Vm}">
        <Grid.RowDefinitions>
            <RowDefinition Height="*"/>
            <RowDefinition Height="auto"/>
        </Grid.RowDefinitions>

        <!-- Panel principal -->
        <StackPanel Margin="20">
            <TextBlock Text="Search for a city:"
                       Margin="5 0"/>

            <!-- El binding va a la propiedad llamada Query,
            El modo TwoWay es para que se actualice la propiedad y el campo de texto al mismo tiempo,
            El Update SourceTrigger se usa para Poner en que condiciones se hace el update.  -->
            <TextBox Margin="5 5"
                     Text="{Binding Query,
                     Mode=TwoWay,
                     UpdateSourceTrigger=PropertyChanged}"/>

            <!-- El command se hace el binding a una propiedad del VM,
            La propiedad se inicializa desde el constructor del VM,
            La propiedad es una clase que implementa la interfaz ICommand,
            El CommandParameter es el parámetro que se le va a mandar al commando,
            Se hizo el binding a la propiedad Query del VM la cual manda una señal cuando cambia,
            Y se maneja en evento CanExecuteChanged el cual viene de la interfaz ICommand -->
            <Button Margin="5 5"
                    Command="{Binding SearchCommand}"
                    CommandParameter="{Binding Query}"
                    Content="Search"/>

            <!-- Desde la view hacemos binding a una propiedad del vm como ItemsSource,
            y hacemos binding Del SelectedItem a una propiedad del vm -->
            <ListView ItemsSource="{Binding Cities}"
                      SelectedValue="{Binding SelectedCity}">
                <ListView.ItemTemplate>
                    <DataTemplate>
                        <Grid>
                            <!-- Como ItemsSource fue definido en la listView, nuestro data context es ese,
                            asi que podemos acceder a los elementos de ese dataContext -->
                            <TextBlock Text="{Binding LocalizedName}"/>
                        </Grid>
                    </DataTemplate>
                </ListView.ItemTemplate>
            </ListView>

        </StackPanel>

        <!-- Aquí se declaro un data context para este cacho de la grid,
        el binding se hizo a una propiedad compleja De tipo nombre CurrentConditions,
        para hacer binding a los elementos de esta propiedad en otros lados -->
        <Grid Grid.Row="1"
              Background="#4392f1"
              DataContext="{Binding CurrentConditions}">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="Auto"/>
            </Grid.ColumnDefinitions>

            <StackPanel Margin="0 10">
                <TextBlock DataContext="{StaticResource Vm}"
                           Text="{Binding SelectedCity.LocalizedName}"
                           Foreground="#f4f4f8"
                           FontSize="20"
                           Margin="20 0"/>

                <!-- WeatherText es un campo parte de la propiedad CurrentConditions -->
                <TextBlock Text="{Binding WeatherText}"
                           Foreground="#f4f4f8"
                           FontSize="18"
                           Margin="20 0"/>

                <!-- Usamos un convertidor añadiendo el namespace, el recurso en window.resources
                y lo llamamos como se muestra abajo. -->
                <TextBlock Text="{Binding HasPrecipitation,
                Converter={StaticResource BoolToRain}}"
                           Foreground="#f4f4f8"
                           FontSize="16"
                           Margin="20 0"/>
            </StackPanel>
            <TextBlock Grid.Column="1"
                       VerticalAlignment="Center"
                       Text="{Binding Temperature.Metric.Value, StringFormat={}{0}°C}"
                       Foreground="#f4f4f8"
                       FontSize="30"
                       Margin="20 0"/>
        </Grid>
    </Grid>
</Window>
```

Archivo `WheatherViewModel`, el `ViewModel` de la aplicación:

``` csharp
using System.Collections.ObjectModel;
using System.ComponentModel;
using System.Runtime.CompilerServices;
using System.Threading.Tasks;
using System.Windows;
using WeatherApp.Annotations;
using WeatherApp.Model;
using WeatherApp.ViewModel.Commands;
using WeatherApp.ViewModel.Helpers;

namespace WeatherApp.ViewModel;

public class WeatherViewModel : INotifyPropertyChanged {

    private string? _query;

    public string? Query {
        get => _query;
        set {
            _query = value;
            // el OnPropertyChanged viene de implementar la interfaz INotifyPropertyChanged
            OnPropertyChanged(nameof(Query));
        }
    }

    private CurrentConditions _currentConditions;

    public CurrentConditions CurrentConditions {
        get => _currentConditions;
        set {
            _currentConditions = value;
            OnPropertyChanged(nameof(CurrentConditions));
        }
    }

    public ObservableCollection<City> Cities { get; set; }

    private City _selectedCity;

    public City SelectedCity {
        get => _selectedCity;

        set {
            _selectedCity = value;
            OnPropertyChanged(nameof(SelectedCity));
            GetCurrentConditions();
        }
    }

    public SearchCommand SearchCommand { get; set; }

    public WeatherViewModel() {

        // Asignamos valores solo para previsualizarlos en el preview
        if (DesignerProperties.GetIsInDesignMode(new DependencyObject())) {
            SelectedCity = new City {
                LocalizedName = "New york"
            };
            CurrentConditions = new CurrentConditions {
                WeatherText = "Partly Cloudy",
                Temperature = new Temperature {
                    Metric = new Units {
                        Value = "21"
                    }
                }
            };
        }

        SearchCommand = new SearchCommand(this);
        Cities = new ObservableCollection<City>();
    }

    private async void GetCurrentConditions() {
        Query = string.Empty;
        Cities.Clear();

        CurrentConditions = await AccuWeatherHelper.GetCurrentConditions(SelectedCity.Key);
    }

    public async Task MakeQuery() {
        if (Query != null) {
            var cities = await AccuWeatherHelper.GetCities(Query);

            Cities.Clear();
            foreach (var city in cities)
                Cities.Add(city);
        }
    }

    public event PropertyChangedEventHandler? PropertyChanged;

    [NotifyPropertyChangedInvocator]
    protected virtual void OnPropertyChanged([CallerMemberName] string? propertyName = null) {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
}
```

Archivo `City.cs` El `Model` de la aplicación (Cada clase debería de ir
en su propio archivo)

``` csharp
namespace WeatherApp.Model;

public class Area
{
    public string ID { get; set; }
    public string LocalizedName { get; set; }
}

public class City
{
    public int Version { get; set; }
    public string Key { get; set; }
    public string Type { get; set; }
    public int Rank { get; set; }
    public string LocalizedName { get; set; }
    public City Country { get; set; }
    public City AdministrativeArea { get; set; }
}

public class Units
{
    public string Value { get; set; }
    public string Unit { get; set; }
    public int UnitType { get; set; }
}

public class Temperature
{
    public Units Metric { get; set; }
    public Units Imperial { get; set; }
}

public class CurrentConditions
{
    public DateTime LocalObservationDateTime { get; set; }
    public int EpochTime { get; set; }
    public string WeatherText { get; set; }
    public int WeatherIcon { get; set; }
    public bool HasPrecipitation { get; set; }
    public object PrecipitationType { get; set; }
    public bool IsDayTime { get; set; }
    public Temperature Temperature { get; set; }
    public string MobileLink { get; set; }
    public string Link { get; set; }
}
```

# XAML

## Definir pantalla de inicio

Para definir que pantalla se debe de abrir al iniciar nuestra aplicación
debemos de modificar nuestro `App.xaml`

``` xml
<Application x:Class="WeatherApp.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:local="clr-namespace:WeatherApp"
             StartupUri="View/WeatherWindow.xaml">
    <Application.Resources>

    </Application.Resources>
</Application>
```

Tenemos que modificar el argumento `StartupUri` en el cual pondremos la
ruta a nuestra pantalla.

En este caso Nuestra pantalla esta en una carpeta llamada `View` y se
llama `WheatherWindow.xaml`.

## Lanzando, abriendo y cerrando ventanas

Para abrir una nueva ventana tenemos que instanciar una nueva instancia
de la nueva ventana

``` csharp
var newContactWindow = new NewContact();
newContactWindow.ShowDialog();
```

Si usamos el método `ShowDialog` la nueva ventana bloqueara la ventana
anterior, por el contrario si usamos el método `Show` abrirá la nueva
pestaña y podremos hacer cosas en la nueva pestaña y en la anterior.

# Estilos

- Podemos estilizar cada componente de nuestra aplicación, pero lo ideal
  es usar recursos estáticos (static resources).
- Esto para poder tener estilos empaquetados y poderlos modificar y
  reutilizar en diferentes partes de nuestra aplicación.

## Static Resources

- Podemos definir los recursos que va a utilizar nuestra pantalla actual
  declarando

``` xml
<window.Resources>
  <!-- Recursos -->
</Window.Resources>
```

Por ejemplo podemos declarar un `solidColorBrush` dentro de nuestros
recursos estáticos.

``` xml
<window.Resources>
  <SolidColorBrush x:key="numbersColor" Color="#444444"/>
  <SolidColorBrush x:key="operatorsColor" Color="Orange"/>
</Window.Resources>
```

Y podemos llamarlos de la siguiente manera\>

``` xml
<Button Content="+/-"
        Background="{StaticResource numbersColor}"
        x:Name="SignButton"
        Grid.Row="1"
        Grid.Column="1"/>
```

Esto puede aplicar para cualquier tipo de recurso estático, no solo
Estilos.

## Estilos para toda la aplicación

- Para tener estilos en toda la aplicación debemos de definirlos en el
  archivo `App.xaml`.

El `App.xaml` debería lucir así por defecto.

``` xml
<Application x:Class="Calculadora.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:local="clr-namespace:Calculadora"
             StartupUri="MainWindow.xaml">
    <Application.Resources>

    </Application.Resources>
</Application>
```

Entonces podríamos tener nuestro archivo así para tener los mismos
estilos.

``` xml
<Application x:Class="Calculadora.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:local="clr-namespace:Calculadora"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
          <!-- Con los estilos que teniamos antes -->
         <SolidColorBrush x:Key="numbersColors"
                         Color="#444444"/>

        <SolidColorBrush x:Key="operatorsColor"
                         Color="Orange"/>

        <SolidColorBrush x:Key="foregroundColor"
                         Color="White"/>

    </Application.Resources>
</Application>
```

## Estilos implícitos

Podemos definir estilos que se aplican a cierto tipo de elementos

Dentro de nuestra etiqueta `Application.Resources` en `App.xaml` podemos

``` xml
<!-- Este estilo se aplicara a los Botones -->
<Style TargetType="Button">
    <!-- Cada setter es para una propiedad -->
    <Setter Property="Foreground" Value="White"/>
    <Setter Property="FontSize" Value="25"/>
    <Setter Property="Margin" Value="5"/>
</Style>
```

También podemos sobrescribir este estilo en el elemento que deseemos.

## Estilos Explícitos

Podemos definir estilos que son llamados por su nombre y solo se aplican
si lo decimos explicitamente

``` xml
<!-- Este estilo se aplicara a los Botones y se llama con el nombre de numberButtonStyle -->
<!-- La diferencia es que declaramos una key con el parametro x:Key=""  -->
<Style TargetType="Button" x:Key="numberButtonStyle">
    <Setter Property="Foreground" Value="White"/>
    <Setter Property="FontSize" Value="25"/>
    <Setter Property="Margin" Value="5"/>
    <Setter Property="Background" Value="{StaticResource numbersColors}"/>
</Style>
```

Ahora podemos usar este estilo donde queramos haciendo uso de argumento
`Style`.

``` xml
<!-- Declaramos que es un Recurso estatico y ponemos la key del estilo -->
<Button Content="8"
        Style="{StaticResource numberButtonStyle}"
        x:Name="EightButton"
        Click="NumberButton_Click"
        Grid.Row="2"
        Grid.Column="1"/>
```

Otra cosa que podemos hacer es basar unos estilos en otros.

``` xml
<!-- Usamos el argumento BasedOn y linkeamos el Recurso estatico asi heredamos los compomentes del estilo deseado -->
<Style TargetType="Button" x:Key="operatorButtonStyle" BasedOn="{StaticResource numberButtonStyle}">
    <Setter Property="Background" Value="{StaticResource operatorsColor}"/>
</Style>
```
