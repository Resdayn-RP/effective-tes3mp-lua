# Functions

## Size & Scope
- Functions should remain small and do a singular task
- Functions shouldn't really exceed 10 lines, if it is, you are likely doing more than one thing
- Utility functions should be in their own file, and then the use of ```require``` to call them into the main script.

### Example
```lua title="functions.lua"
    ---@class functions
    local functions = {} 
    
    ---@param message string
    function functions.log(message)
        tes3mp.LogMessage(enumerations.log.VERBOSE, message)
    end

    return functions
```

```lua title="main.lua"
    ---@class core
    local core = {}

    core.functions = require 'custom.example.functions'

    function core.onServerPostInit()
        core.functions.log("Hello World!")
    end

    customEventHooks.registerHandler("onServerPostInit", core.onServerPostInit)

    return core
```

## Naming
- Local functions should only be in camelCase, while global functions should be in PascalCase
- Function names should start with a leading verb.

### Example
```lua title="BAD"
    function player() -- global
    local function PlayerDrop() -- local
```
```lua title="GOOD"
    function GetPlayerObject() -- global
    local function dropPlayer() -- local
```

## Parameters
### Parameter Count
Never exceed 3 parameters, doing so means that you should probably create a table and then pass the table as an argument.

#### Example
```lua title="BAD"
    function CreateChar(name, age, height, birthday, nationality)
    end
```

```lua title="GOOD"
    function CreateChar(char)
    end
```

### Avoid passing implied functions as arguments
Just declare the function as a local variable and then pass the variable as the argument This benefits performance (especially when coroutines/threads are used). Beyond that, it will also increase said readability of the code.
```lua title="BAD"
    customEventHooks.registerHandler("onServerInit", function()
        print("Hello")
    end)
```
```lua title="GOOD"
    local core = {}
    core.onServerInit = function()
        print("Hello")
    end
    customEventHooks.registerHandler("onServerInit", core.onServerInit)
```

## Documentation
Always use [lua-language-server annotation](https://github.com/sumneko/lua-language-server/wiki/Annotations), this not only helps you remember the structure and how your code works, it provides an API so that you can see it when you call functions in other files.
```lua
    --- Puts a space between a first and last name
    ---@param first string first name
    ---@param last string last name
    ---@return string full name
    function core.formatName(first, last)
        return first .. ' ' .. last
    end
```

## Nesting
Never nest if possible. Do not exceed 4 levels of indentation. Use guard clauses where applicable. Nesting code makes the code dificult to read, it also makes it seem as if it is doing multiple things.

```lua title="BAD"
    function core.getFullName(first, last)
        if first and last then
            return first .. last
        else
            return nil
        end
    end
```

```lua title="GOOD"
    function core.getFullName(first, last)
        if not (first and last) then return end
        return first .. last
    end
```