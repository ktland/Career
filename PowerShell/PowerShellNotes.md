# PowerShell Notes

## Locate Commands

- *cmdlet*: a compiled command that is invoked in PowerShell
  - named according to a verb-noun naming standard
  - can view a list of approved verbs by using the `Get-Verb` cmdlet
  - verbs are organized by activity type and function
- Three core cmdlets:
  - `Get-Command`: lists all the available cmdlets on your system
  - `Get-Help`: invokes a built-in help system
    - can also run alias `help` command to invoke `Get-Help`
  - `Get-Member`: when you call a command, the response is an object that contains many properties
    - allows you to drill down into the response and learn more about it

### Locate Commands by using Get-Command

- `-Noun` flag targets the part of the command name that's related to the noun
  - example: `Get-Command -Noun a-noun*`
  - searches for all cmdlets whose noun part starts with `a-noun`
- `-Verb` flag targets the part of the command name that's related to the verb
  - the `-Verb` and `-Noun` flags can be combined to create a more detailed search query and type
  - example: `Get-Command -Verb Get - Noun a-noun*`
