# MSBuild.AssemblyVersion
MSBuild targets for updating Assembly version during build process.
AssemblyInfo can be set by initializing MSBuild property `$(AssemblyVersionNumber)`
before MSBuild target `AssemblyVersionUpdate` is called.

## Examples
1. Initialize property `$(AssemblyVersionNumber)` from command line:
   ```
   msbuild.exe MySolution.sln /p:AssemblyVersionNumber=1.2.3.4
   ```
   
2. Initialize or update property `$(AssemblyVersionNumber)` declaratively in MSBuild project or a referenced .props file:
   ```xml
   <PropertyGroup>
       <AssemblyVersionNumber>1.2.3.4</AssemblyVersionNumber>
   </PropertyGroup>
   ```
   
3. Update property `$(AssemblyVersionNumber)` in a custom target:
   ```xml
   <Target Name="MyCustomUpdateAssemblyVersionNumber"
           BeforeTargets="AssemblyVersionUpdate">
       <PropertyGroup>
           <AssemblyVersionNumber>1.2.3.4</AssemblyVersionNumber>
        </PropertyGroup>
   </Target>
   ```
