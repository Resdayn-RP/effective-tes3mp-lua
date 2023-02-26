# Variables
## Naming
### Name Constants using ALL_CAPS
Variables that you do not intend to change (a constant), should follow the following naming scheme.
```lua
    local MY_CONSTANT = "constant value"
    MY_GLOBAL_CONSTANT = "another constant value"
```
### camelCase for non-constant local variables
```lua
    local myVariable = "variable value"
```
### PascalCase non-constant global variables
```lua
    MyGlobalVariable = "global variable value"
```
### Use underscore "_" as the name of a variable that cannot be deleted, but is unused
```lua
    local function printValues(map)
        for _, v in pairs(map) do
            print(v)
        end
    end
```

## Location

Always keep variables close to where they are used and grouped together. Global variables should be grouped together and declared at the top of a file (or in a seperate file).