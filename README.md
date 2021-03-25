# ERP10 SDK

In this repository you will find a real demo on how to use SDK controls with PRIMAVERABSS ERP V10.

## What is PRIMAVERA SDK?

The PRIMAVERA SDK100 is a library of standards and business components for the PRIMAVERA environment, which enables partners and external development teams to create ERP add-ons more quickly and easily. Where some samples:

* F4
* F4Entidade
* F4Moeda
* F4TabelaSQL
* TiposEntidade
* TiposEntidade
* Anexos
* PriGrelha

To make possible to use it, you need to add reference to the PRISDK100.dll assembly, available in the "C:\ProgramFiles\PRIMAVERA\SG100\APL" folder. Keep in mind that the SDK only works with PRIMAVERA ERP and it doesn't works with other systems.

## How to use?

In order to the components work the first thing you must do is initialize the SDK Context. The initialization will validate if the ERP is available and return the PSO and BSO.

Where how you can do:

``` csharp

sealed class PriSDKContext
{
    // .NET guarantees thread safety for static initialization
    public static readonly clsSDKContexto SdkContext = new clsSDKContexto();
    private static bool contextInitialized = false;

    /// <summary>
    /// Private constructor
    /// </summary>
    private PriSDKContext()
    {
    }

    public static void Initialize(dynamic BSO, dynamic PSO)
    {
        if (!contextInitialized)
        {
            SdkContext.Inicializa(BSO, "ERP");
            PSO.InicializaPlataforma(SdkContext);

            contextInitialized = true;
        }
    }
}

```

After create the context you can use it to initialize any SDK component. Where how you can do:

```csharp
/// <summary>
/// Loads the form and initialize the SDK context and the SDK controls
/// </summary>
private void InicializeSDKContext()
{
    //Initializes context 
    PriSDKContext.Initialize(BSO, PSO);

    //Initializes controls
    if (!controlsInitialized)
    {
        //Initializes the components with the ERP context
        treeContasEstado1.Inicializa(PriSDKContext.SdkContext);
        tiposEntidade1.Inicializa(PriSDKContext.SdkContext);
        f4Entidade.Inicializa(PriSDKContext.SdkContext);

        controlsInitialized = true;
    }
}
```

Other important thing is to release all the resources use by each component, to do that user the *Termina()* method:

```csharp
private void Dispose()
{
    treeContasEstado1.Termina();
    tiposEntidade1.Termina();
    f4Entidade.Termina();
}
```

## Enumeration

The SDK provide some constants that are useful to configure the controls behavior. This enums are available in the class *clsSDKTypes*.

```csharp
clsSDKTypes.EnumCategoria.Clientes;
```

## Contributing and Feedback

Everyone is free to contribute to the repository.

Any bugs detected in the code samples can be reported in the *Issues* section of this repository.

## License

Unless otherwise specified, the code samples are released under the [MIT license](https://pt.wikipedia.org/wiki/Licen%C3%A7a_MIT).
