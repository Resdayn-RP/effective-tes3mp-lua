# Conditionals
## Default Values
Smart use of the 'or' operator instead of nil checks increases readability.
```lua title="BAD"
    if name then
        return name
    else
        return "John Doe"
    end
```
```lua title="GOOD"
    return name or "John Doe"
```
## Don't write "if true then return true"
Just use ternary operators to evaluate the expression
```lua title="BAD"
    if name == "mark" or name == "stacy"
        return true
    else
        return false
    end
```
```lua title="GOOD"
    return name == "mark" or name == "stacy" -- Will return true if name is either mark or stacy
```