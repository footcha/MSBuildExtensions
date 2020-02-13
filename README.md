# MSBuild.AssemblyVersion
MSBuild targets for updating Assembly version and optionally Assembly Informational Version during build process.
AssemblyInfo can be set by initializing MSBuild property `$(AssemblyVersionNumber)` and optionally `$(AssemblyInformationalVersion)` 
before MSBuild target `AssemblyVersionUpdate` is called.

## Examples
Example 1: Initialize property `$(AssemblyVersionNumber)` from command line:

   ```
   msbuild.exe MySolution.sln /p:AssemblyVersionNumber=1.2.3.4
   ```
   Or with AssemblyInformationalVersion.
   ```
   msbuild.exe MySolution.sln /p:AssemblyVersionNumber=1.2.3.4 /p:AssemblyInformationalVersion=1.2.3-alpha
   ```
  
Example 2: Initialize or update property `$(AssemblyVersionNumber)` and optionally `$(AssemblyInformationalVersion)` declaratively in MSBuild project or a referenced .props file:
   ```xml
   <PropertyGroup>
       <AssemblyVersionNumber>1.2.3.4</AssemblyVersionNumber>
       <AssemblyInformationalVersion>1.2.3.4-alpha</AssemblyInformationalVersion>
   </PropertyGroup>
   ```
  
Example 3: Update property `$(AssemblyVersionNumber)` and optionally `$(AssemblyInformationalVersion)` in a custom target:
   ```xml
   <Target Name="MyCustomUpdateAssemblyVersionNumber"
           BeforeTargets="AssemblyVersionUpdate">
       <PropertyGroup>
           <AssemblyVersionNumber>1.2.3.4</AssemblyVersionNumber>
            <AssemblyInformationalVersion>1.2.3.4-alpha</AssemblyInformationalVersion>
        </PropertyGroup>
   </Target>
   ```
