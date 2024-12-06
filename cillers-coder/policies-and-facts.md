# Policies And Facts

Policies and Facts are specified in XML files in the `.cillers/coder/policies` and `.cillers/coder/facts` directories with one `policy-group` or `fact-group`per file. Both `policy-group and fact-group` elements may contain a `scope` element that specifies for which code the Policies/Facts in the group are applicable to.&#x20;

Here is an example of a `policy-group`that is included by default when you run `cillers coder-init.`

```xml
<policy-group id="go" title="Go">
    <scope>
        All Go code
    </scope>
    <policy id="go-project-structure" title="Go Project Structure">
       <specification>
           * A project should have a mod.go file. 
           * main.go should be the only file in the main package. All other files should be in sub packages. 
           * The entry point to the application should be the main function in the main.go file.
           * The main function should call another function called 'app' that returns an error if unsuccessful.
           * The main function should exit with a non-zero error if the 'app' function returns an error.
           * The main and app functions should be the only functions in the main.go file. All other functions
           should be in other files. 
           * If the project is small with less than 8 files, new go files should be created in the lib package unless
           otherwise specified. 
       </specification>
    </policy>
</policy-group>
```

And, here is an example of a `fact-group` that is also included by default.&#x20;

```xml
<fact-group id="go" Title="Go">
    <scope>
        All Go code.
    </scope>
    <fact id="only-non-deprecated-packages" title="Deprecated Package Restrictions">
       <specification>
           The following Go packages are deprecated and must not be used:
           * io/ioutil
       </specification>
    </fact>
    <fact id="limited-glob-functionality" title="Glob Pattern Limitations">
       <specification>
           Go doesn't support ** in its glob functionality.
       </specification>
    </fact>
    <fact id="no-unused-packages" title="Package Import Requirements">
       <specification>
           Go files must not contain imports of unused packages.
       </specification>
    </fact>
</fact-group>
```

As you can see these groups are scoped so they are only applied to Go code.&#x20;

You can add, change and remove Policies and Facts in existing groups and create new Policy and Fact groups. All files with Policy and Fact groups in their respective directories are automatically included in the prompt as appropriate. Make sure to validate your XML, this is currently not validated, but will be soon.&#x20;
