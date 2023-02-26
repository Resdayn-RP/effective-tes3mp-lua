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