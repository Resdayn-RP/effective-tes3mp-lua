# Functions

## Size \& Scope
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

