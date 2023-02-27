# Tables

## Use object access for constant keys, array access for non-constant
```lua
    local company = {
        boss = "Sam"
    }
```
```lua title="BAD"
    local boss = company["boss"]
```
```lua title="GOOD"
    local boss = company.boss
```

## When using table values multiple times, store it in a local variable
This increases readability, but also increases performance as you are not accessing the table constantly.
```lua title="BAD"
    local concatenation = myTable["key"] .. myTable["key"]
```
```lua title="GOOD"
    local myTableValue = myTable["key"]
    local concatenation = myTableValue .. myTableValue
```

## table.insert() sucks
It is not efficient/performant, you should only use this when you need to insert at a specific index.
### Inserting at the end of a table
```lua title="BAD"
    table.insert(myTable, "value")
```
```lua title="GOOD"
    myTable[#myTable + 1] = "value"
```
### Inserting/Overwriting a given key
```lua title="BAD"
    table.insert(myTable, "key", "value")
```
```lua title="GOOD"
    myTable["key"] = "value"
```