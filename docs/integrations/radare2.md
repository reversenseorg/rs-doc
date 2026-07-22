# Radare2 plugins

The platform allows users to add several types of plugins or external tool such as decompiler.

*Radare2* is the default decompiler for executable files and it is shipped with Reversense. So, you don't require extra configuration to use it.

Disassembler and decompiler are recognized as **NativeAnalyzer** inside the platform. Such analyzers offer a set of common interface that assures you can switch to your favorite decompiler seemlessly.  

## 1. Set as default decompiler and executable analyzer


!!! warning "Default decompiler cannot be configured"
Currently, there is no way to define Radare2 as the default decompiler from the graphical interface. It should not be a problem as R2 is the default backend for decompiling. You must necessarily use environment variables or the configuration file.
The solely available way to set another decompiler as the default decompiler is to call it directly from an Inspector listener using Dexcalibur API like that:
```typescript
pEvent.getContext().getAnalyzer().getNativeAnalyzer().discover(
    modelFile,
    { extraOpts:null, backend:NativeBackend.R2 });
```

## 2. Updating the decompiler

The Reversense platform treats Radare2 as a standard executable. When needed, it launches the tool and uses an internal pipe-based component to parse command output and send instructions. Updating Radare2 to a newer version is straightforward: simply update the binary and ensure the configured path to Radare2 remains unchanged.

Note that the platform does not provide control over the arguments or the way the Radare2 process is invoked, so this must be considered when updating Radare2 or modifying its behavior.

## 3. Install r2 plugins 

Core plugins such as Radare2 Hermes and Radare2 Flutter can be installed directly from Reversense. 
For other plugins, open Radare2 from a command prompt and install them using the appropriate command. Once installed, these plugins are automatically available in Reversense, as the platform inherits all plugins from your Radare2 setup during execution.

```bash
r2pm -ci r2flutter
```