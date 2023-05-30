# Problem
How to use Dependency Injection (DI) in Azure Functions


# Environment
Visual Studio 2022

# Solution
## Follow the following steps to add DI in Azure Function


## Step 1
Create an Azure Function with HttpTrigger and add new class file and named it as Startup and make this public.

```
namespace DemoAzFunction
{
    public class Startup
    {
    }
}
```

## Step 2
Add a Nuget Package Microsoft.Azure.Functions.Extensions.DependencyInjection.
Inherit this Startup class from FunctionsStartup.

```
namespace DemoAzFunction
{
    public class Startup : FunctionsStartup
    {
    }
}
```

## Step 3
By keeping your cursor on FunctionsStartup, press 'ctrl + dot(.)' and select implement this abstract class. Your code will look like this.

```
namespace DemoAzFunction
{
    public class Startup : FunctionsStartup
    {
        public override void Configure(IFunctionsHostBuilder builder)
        {
            throw new NotImplementedException();
        }
    }
}
```

## Step 4
Now to register this type as Function startup, to do this add the assembly directive and your code will look like this.

```
[assembly: FunctionsStartup(typeof(DemoAzFunction.Startup ))]
namespace DemoAzFunction
{
    public class Startup : FunctionsStartup
    {
        public override void Configure(IFunctionsHostBuilder builder)
        {
            throw new NotImplementedException();
        }
    }
}
```

## Step 5
So with that setup, we can now start registering inside the builder the dependencies that for this particular Azure Function.
Let remove the NotImplementedException and add the dependency of IMessageProcessor interface and its implementation as MessageProcessor.


```
[assembly: FunctionsStartup(typeof(DemoAzFunction.Startup ))]
namespace DemoAzFunction
{
    public class Startup : FunctionsStartup
    {
        public override void Configure(IFunctionsHostBuilder builder)
        {
            builder.Services.AddTransient<IMessageProcessor, MessageProcessor>();
        }
    }
}
```
