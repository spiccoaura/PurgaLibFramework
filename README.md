## 🛠️ Plugin Creation Tutorial

Follow these steps to create a plugin.

### 1️⃣ Add PurgaLibFramework.dll
Include `PurgaLibFramework.dll` in your C# plugin project.
Place it in **LabAPI/plugins/Global**.
OR:
**you can simply search the pack in nuget, the name is PurgaLibFramework.**
`dotnet add package PurgaLibFramework --version 0.1.9`

### 2️⃣ Create `Config.cs`
```csharp
using PurgaLibFramework.PurgaLibFramework.PurgaLib.PurgaLibEvent.Events.PluginManager;

namespace ExamplePurgaLib
{
    public class Config : IConfig
    {
        public bool Enabled { get; set; } = true;
    }
}
```
### 2️⃣ Create `Plugin.cs`
```csharp
using System;
using PurgaLibFramework.PurgaLibFramework.PurgaLib.PurgaLib_API.Server;
using PurgaLibFramework.PurgaLibFramework.PurgaLib.PurgaLibEvent.Events.PluginManager;

namespace ExamplePurgaLib
{
    public class Main : Plugin<Config>
    {
        public override string Name { get; } = "Example Plugin";
        public override string Author { get; } = "Florentina<3";
        public override string Description { get; } = "Test plugin for PurgaLib";
        public override Version Version { get; } = new Version(1,0,0);
        public override Version RequiredPurgaLibVersion { get; } = new Version(PurgaLibProperties.CurrVersion);
        
        protected override void OnEnabled()
        {
            Logged.Info("Hi from Plugin PurgaLib!");
        }

        protected override void OnDisabled()
        {
            Logged.Info("Bye from Plugin PurgaLib!");
        }
    }
}

```
