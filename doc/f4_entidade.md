# F4

This component work's like the F4 control that can be found in PRIMAVERA V10.

## How to use?

* Initialize the component SDK context. 
* Select a category attribute in the toolbox. 
* Set a value for the module atribute.

## Properties

| Property               | Description |
| ----------             | ------------- |
| Categoria              | The entity that the control will display. |
| PermiteDrillDown       | Allows the drill-down operation. |
| SelectionFormula       | Filter the values when print the list. |
| Restricao              | Filter the values returned.|
| MostraDescricao        | Show the description field. |
| MostraLink             | Show the drill down link. |

```csharp

// Some samples how to use the attributes.

f4.Categoria = clsSDKTypes.EnumCategoria.Clientes;
f4.PermiteDrillDown = true;
f4.SelectionFormula = "Pais='PT'";
f4.Restricao = "{clientes.Pais} = 'PT'"

```