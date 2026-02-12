## Commands

### Access Properties or other Item
```
// $_ takes each item from a list (such as eventID7,11,12-14, 22,23,25)
Where-Object { $_.Properties[5].Value -like '*DismCore.dll*' }

Where-Object { $_.<Member2Search>.Value -like '*DismCore.dll*' }

```
### Where-Obj
```
Where-Object { Condition }
// short-form
? { Condition }

Operator	Meaning
-eq	equals
-ne	not equal
-gt	greater than
-ge	greater or equal
-lt	less than
-le	less or equal
-like	wildcard match (*word*)
-notlike	wildcard not match
-match	regex match
-notmatch	regex not match
-contains	collection contains
-notcontains	collection does not contain
-in	value is in a list
-notin	value is not in a list
```
### Enum Table Cols

```
// Pipe the cmd to Get-Member to make use of Format-List
// Returns MemberType and Definition
$data = <command>
$data | Get-Member
// just return first row
$data | Get-Member

// Pipe to Format-Table 
$data -MaxEvents 1 | Format-Table *
// If data getting truncated use 
Format-Table -Wrap

// Or use 
Format-List

// Reference properties Directly 
($data[0]).psobject.Properties.<Prop_Name>

// Force Format-Table to show all Cols
$data | Select-Object * | Format-Table -Autosize 
```




#powershell
