# Structure/Scope

## Limited Scope
Variables and functions should be scoped to the smallest visibility needed. Prefer in order: local, global, export.

### Example
If you need the variable for one function, you declare the variable local within the function.

## Resource/Script Naming

Never use spaces, "_" and "-" are acceptable alternatives. You may also chose to do camelCase as well.

## Indentation

You should not exceed 4 levels of indentation if you can avoid it. Any more impacts the readability of code. Effective use of guard functions will be necessary to cut down on this.