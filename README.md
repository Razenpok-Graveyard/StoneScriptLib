# StoneScriptLib

StoneScriptLib is a library with stuff which adds some juicy classes for your
scripting needs

## Installing

1. [Download source code](https://github.com/Razenpok/StoneScriptLib/archive/master.zip)
2. Unpack zip file into [save-file folder](https://stonestoryrpg.com/faq.html#Technical%20Help)
3. Rename folder to "StoneScriptLib". StoneScriptLib.txt file should have the following path:
```
   (save-file folder)/Stonescript/StoneScriptLib/StoneScriptLib.txt
```

## Using

To use StoneScriptLib, you need to import main namespace into your script

```
var StoneScriptLib = import StoneScriptLib/StoneScriptLib
```

After that you can use any of the provided classes

```
var List = StoneScriptLib.System.List

var list = List.New()
list.Add(42)
```

## Classes

Documentation for classes is presented in a
[Learn X in Y minutes](https://learnxinyminutes.com/) style

### List

```
var StoneScriptLib = import StoneScriptLib/StoneScriptLib
var List = StoneScriptLib.System.List

// To instantiate a list call List.New
var list = List.New()

// Basic list operations are same as in any other language
list.Add(42)
list.Add("foo")
list.Add(false)
list.Add("foo")

var isTrue = list.Contains(42)
var isFalse = list.Contains(13)

var firstIndex = IndexOf("foo")
var lastIndex = LastIndexOf("foo")

list.Remove(42)
list.RemoveAll("foo")

list.Reverse()
list.Sort()

list.Clear()

// Index-based operations use zero-based indexing

// Use Get and Set to get or set items at index
var item = list.Get(3)
list.Set(2, "foo")

// Use Insert to insert a new item to a specified index 
list.Insert(1, "foo")

// Use RemoveAt to remove an item at a specified index 
list.RemoveAt(0)

// List provides a set of range operations
var otherList = List.New()
otherList.Add(1)
otherList.Add(2)
otherList.Add(3)

// You can add a range of items using AddRange
list.AddRange(otherList)

// You can insert a range of items using InsertRange
list.InsertRange(4, otherList)

// You can remove a range of items using RemoveRange
// This command removes 5 items starting from index 2
list.RemoveRange(2, 5)
```

### TypeCheck

```
var StoneScriptLib = import StoneScriptLib/StoneScriptLib
var TypeCheck = StoneScriptLib.System.TypeCheck

// TypeCheck provides type checks as methods opposed to built-in Type(value)

var isTrue = TypeCheck.IsInt(42)
var isFalse = TypeCheck.IsInt("foo")

isTrue = TypeCheck.IsString("foo")
isFalse = TypeCheck.IsString(42)

isTrue = TypeCheck.IsBool(true)
isFalse = TypeCheck.IsBool(null)

isTrue = TypeCheck.IsNull(null)
isFalse = TypeCheck.IsNull(42)

// TypeCheck also provides a way to check if an object is an instance
// of StoneScriptLib type

var List = StoneScriptLib.System.List
var list = List.New()

isTrue = TypeCheck.IsType(list, List)
isFalse = TypeCheck.IsType("foo", List)
```

### Reference

```
var StoneScriptLib = import StoneScriptLib/StoneScriptLib
var Reference = StoneScriptLib.System.Reference

// Reference allows you to pass values as a reference without creating new classes
func Increment(number)
  number.value++

var count = Reference.New(0)
Increment(count)
Increment(count)
Increment(count)

// count.value is now 3
var result = count.value
```

## Contributing

If you want to contribute to StoneScriptLib, follow its code style and
project structure.

StoneScriptLib uses internal unit testing framework to execute a test suite
which is used to develop a bug-free framework. To run a test suite use following
commands:

```
var runner = import StoneScriptLib/Tests/TestRunner
runner.Update()
```

If you want to fix a bug which is not covered by unit tests, add a new
one which reproduces the bug, and then fix it.

If you want to add new functionality, add corresponding unit tests and
README documentation.