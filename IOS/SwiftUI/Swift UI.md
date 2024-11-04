> [!info] Definition
>  SwiftUI es un framework de apple para crear UI de manera fácil y sin makup.

# Estructura básica de una View.

![[SwiftUI_Basic_Structure.svg]]
> Partes de la view básica de SwiftUI.

> [!info] 
> La syntaxis del VStack es llamada `trailing closure syntax` 

## Estado mutable en una view

Para poder mutar estado dentro de una view debemos de usar `@State`
 ```swift
struct CardView: View {
    @State var faceUp = false // <- We mark it as mutable

    var body: some View {
        ZStack {
			// Some code
        }
        .onTapGesture {
            faceUp = !faceUp // <- Mutable state.
        }
    }
}
 ```

> [!info]
> Esto internamente crea un puntero a la variable que marcamos como `@State`
> para poder mutarla.

La mayoría del estado mutable de la aplicación debe de estar en la lógica de la aplicación, no en la `view`.

Pero esto es útil para estado que solo ocurre en la `view`.
