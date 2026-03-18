# psbundle

PSBundle is a tiny package manager for PowerShell.

## Installation
Run the following command:
```PowerShell
Install-Module psbundle -Force -AcceptLicense
```


## Usage

### 1. Initialization

To initialize PSBundle environment, firstly import the module, and then use `psbundle new`:
```PowerShell
Import-Module psbundle
psbundle new
```
This will create two directories named `dist` and `psbundle_modules` in the current directory. Now the current directory is PSBundle project root.

### 2. Package installation

Use `psbundle install` to install packages from PSGallery or any other repositories configured in your PowerShell. Dependencies will be resolved automatically.
```PowerShell
psbundle install ModuleName
```

### 3. Building

Use `psbundle build` to create a simple PowerShell bundle. Simple PowerShell bundle is a combination of all project files in one script (`dist\bundle.ps1`).
```PowerShell
psbundle build
```
Use `psbundle build -Target exe` to create a Windows program from your PowerShell project. Your program will be placed to `dist\bundle.exe`. All dependencies will be included; you can also bundle PowerShell Core runtime.
```
# Build EXE containing all the code and dependencies
psbundle build -Target exe

# Build EXE containing all the code, dependencies and PowerShell Core runtime
psbundle build -Target exe -BundlePSCore

# You can use -HideConsole switch to hide console of your application
psbundle build -Target exe -BundlePSCore -HideConsole
```
