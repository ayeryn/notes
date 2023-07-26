# Swift (IOS)

Swift is a __functional__ language.   
Swift is a strong type language but the compiler is able to infer.

## View
`View`: a rectangular area on the screen

The view (self) is an immutable object. All the views are being rebuilt constantly.

```swift
struct ContentView: View {
    
    // type of body is "something" that behaves like a view
    // kinda like legos
    
    // some View is a suggestion to the complier
    // the complier will look at the code and replace it with proper type
    var body: some View {
        
        /* ZStack: "bag of legos", a combiner
         * stacks elements on top of each other
         */
        
        // equivalent to ZStack(alignment: .., content {})
        // anytime there's a function at the end of the stack
        // the kw can be dropped (purely for looks!! lmfao)

        ZStack {
            /* RoundedRectangle and Text are both functions
             * it's actually a return but the kw is hidden
             */
                        
            RoundedRectangle(cornerRadius: 25)
            // cornerRadius is a label
                .stroke(lineWidth: 5)

            Text("Hello, world!")
        }
        .padding(.horizontal)
        .foregroundColor(.red)
        // default and passed down to elements inside
    }
}
```

### ZStack
ZStack is a combiner that stacks elements on top of each other

### HStack
HStack is a horizontal stack

## Strings and Characters
### String Interpolation
You can use __extended string delimiters__ to create strings containing characters that would otherwise be treated as a string interpolation. For example,
```swift
print(#"Write a string using\(multiplier)."#)
// Prints "Write a string using\(multiplier)."
```
To use string interpolation inside a string that uses extended delimiters, match the number of number signs after the backslash to the number of number signs at the beginning and end of the string. for example,
```swift
print(#"6 times 7 is \#(6*7)."#)
// Prints "6 times 7 is 42."
```

### Counting Characters
Swift's use of __extended grapheme clusters" for `Character` values means that string concatenation and modification may not always affect a string's character count.
```swift
var word = "cafe"
print("The number of characters in \(word) is \(word.count)")
// Prints "The number of characters in cafe is 4"

word += "\u{301}"  // COMBINING ACUTE ACCENT, U+0301
print("The number of characters in \(word) is \(word.count)")
// Prints "The number of characters in café is 4"
```

### String Indices
Since different characters can require different amounts of memory to store, so in order to determine which `Character` is at a particular position, you must iterate over each Unicode scalar from the start or end of that `String`. Therefore, Swift string __cannot__ be indexed by integer values.

- `startIndex`: the position _of_ the first `Character` of a `String`
- `endIndex` : the position _after_ the last character in a `String`
- If a `String` is empty, `startIndex` is equal to `endIndex`.

## Arrays
### Declaration with data type
```swift
var fruits = ["apple","banana","cherry"]
var fruits: Array<String> = ["apple","banana","cherry"]
var fruits: [String] = ["apple","banana","cherry"]
```

## Optional
An optional represents two possibilities: Either there is a value, and you can unwrap the optional to access that value, or there isn't a value at all.

An optional is an __enum__!!
```swift
struct Optional<T> {
    case none
    case some<T>
}
```
```swift
let hello: String? = ...
print(hello)

// Logic behind the scene
switch hello {
    case .none: // throw an error
    case .some(let data): print(data)
}
```

### `??` Nil-Coalescing Operator
`??` unwraps an optional `a` if it contains a value, or returns a default value `b` if `a` is `nil`. It's shorthand for
`a != nil ? a! : b`
> IF the value of `a` is a non-`nil`, the value of `b` isn't evaluated. This is known as _short-circuit evaluation_.

```swift
let x: String? = ...
let y = s ?? "foo"

// Logic behind
switch x {
    case .none: y = "foo"
    case. some(let data): y = data
}
```

### Optional Chaining


## Control Transfer Statements
### `continue`
The `continue` statement tells a loop to stop what it's doing and start again at the beginning of the next iteration through the loop.     
- AKA. "I'm done with the current loop iteration" without leaving the loop altogether.
- Kind of like a skip

### `break`
The `break` statement ends execution of an entire control flow statement __immediately__.     
The `break` statement can be used inside a `switch` or loop statement when you want to __terminate the execution__ of the `switch` or loop statement earlier than would.

loops and conditional statements can be __labeled__ so that when multiple loops are involved, we can be specific about which loop to break or continue.

### `fallthrough`
This enables `switch` to behave like C switches, such that a statement can match more than one case.

### `return`
### `throw`

## Early Exit
### `guard`
A `guard` statement, like an `if` statement, executes statements depending on the Boolean value of an expression. An `else` must be specified.    
It improves the readability of your code.

### `defer`
The code inside of the `defer` always runs, regardless of how the program exists that scope. That includes code like an early exit from a function, breaking out of a `for` loop, or throwing an error.    
This behavior makes `defer` useful for operations where you need to guarantee a pair of actions happen. For instance, manually allocating and freeing memory, opening and closing low-level file descriptors and beginning and ending transactions in a database. 

## Closures
Closures are self-contained blocks of functionality that can be passed around and used in your code.    
Closure expressions are a way to write inline closures in a brief, focused syntax.

### Closure Expression (The Sorted Example)
`sorted(by:)` is a standard library method that sorts an array of values of a know type, based on the output of a sorting closure that you provide.
```
sorted(by:)
Returns the elements of the sequence, sorted using the given predicate as the comparison between elements.
```
_\* A predicate is a function of a set of parameters that returns a boolean as an answer_

```swift
// Sort names in descending order
let names = ["Zelda", "Xavier", "Jen", "Peter", "Aaron", "Yeji"]
let sortedNames = names.sorted(by:/* predicate*/)
```

1. We can use a function as the predicate
```swift
func backward(_ s1: String, _ s2: String) -> Bool {
    return s1 > s2
}

let sortedNames = names.sorted(by:backward)
```

2. We can use a closure expression as the predicate
```swift
let sortedNames = names.sorted(by: {(s1: String, s2: String) -> Bool in return s1 > s2})
```

3. We can simplify the closure expression because of __type inference__
```swift
let sortedNames = names.sorted(by: {s1, s2 in return s1 > s2})
```

4. We can omit `return` in __single-expression closures__
```swift
let sortedNames = names.sorted(by: {s1, s2 in s1 > s2})
```

5. We can omit the parameter list by using __shorthand argument names__
```swift
let sortedNames = names.sorted(by: {$0 > $1})
```

6. We can provide operator to call on __operator methods__
```swift
let sortedNames = names.sorted(by: >)
```

### Trailing Closure
If you need to pass a closure expression to a function as the function's final argument and the closure expression is long, it can be useful to write it as a _trailing closure_ instead.    
When it's used, you don't write the argument label for the first closure as part of the function call.    
For instance, the shorthand argument version of `sorted` from above can be rewritten as:
```swift
names.sorted(){ $0 > $1 }
```

If it's the only argument then `()` can be omitted as well -
```swift
names.sorted { $0 > $1 }
```

If a function takes multiple closure, you omit the argument for the first trailing closure and you label the remaining closures.


Tailing closure are most useful when the closure is sufficiently long.

#### `map`
```
map(_:)
Transforms all elements from the upstream publisher with a provided closure.
```
The closure is called once for each item in the array, and returns an alternative mapped value for that item.
```swift
// Convert an array of Int into an array of String
let digitNames = [
    0: "zero", 1: "one", 2: "two", 3: "three", 4: "four", 
    5: "five", 6: "six", 7: "seven", 8: "eight", 9: "nine"
]
let numbers = [16, 58, 510]

let strings = numbers.map { (number) -> String in 
    var number = number
    var output = ""
    repeat {
        // dictionary subscripts return an optional value to indicate 
        // that the dictionary lookup can fail if they key doesn't exist
        // In this case, it's guaranteed to exist
        output = digitNames[number % 10]! + output
        number /= 10
    } while number > 0
    return output
}
```

## Enumerations
An enumeration defines a common type for a group of related values and enables you to work with those values in a type-safe way within your code.

```swift
enum CompassPoint {
    case north
    case south
    case west
    case east
}

// or defined on the single line
enum CompassPoint {
    case north, south, west, east
}
```
> Swift enumeration cases don't have an integer value set by default, unlike languages like C. In the example above, `north`, `south`, `west`. `east` don't implicitly equal `0, 1, 2,` and `3`. Instead, the different enumeration cases are values in their own right, with an explicitly defined type of `CompassPoint`.

The type of an enum case is inferred upon initialization. It can be set to a different case using a shorter dot syntax because the type is already known at that point.
```swift
var direction = CompassPoint.west

direction = .east
```

### Associated Values
It's sometimes useful to be able to store values of types alongside these case values. The value types can be different for each case of the enumeration if needed. _Known as discriminated unions, tagged unions, or variants in other languages._

```swift
// Define an enumeration type called Barcode,
// which can take either a value of upc with an associated value of type
// (Int, Int, Int, Int), or
// a value of qrCode with an associated value of type String
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
}

// either NOT both
var productBarcode = Barcode.upc(8, 85909, 51226, 3)

productBarcode = .qrCode("ABCDEFG")

switch productBarcode {
    case .upc(let numberSystem, let manufacturer, let product, let check):
        print("UPC:\(numberSystem), \(manufacturer), \(product), \(check)")
    case .qrCode(let code):
        print("QR CODE: \(code)")
}
```

If all of the associated values for an enumeration case are extracted as constants, or if all are extracted as variables, you can place a single `let` or `var` annotation before the case name for brevity:
```swift
switch productBarcode {
    case let .upc(numberSystem, manufacturer, product, check):
        print("UPC:\(numberSystem), \(manufacturer), \(product), \(check)")
    case let .qrCode(code):
        print("QR CODE: \(code)")
}
```

## Protocols and Extensions
Classes, enumerations, and structures can all adopt protocols.

### Extensions
USe `extensions` to add functionality to an existing type, such as new methods and computed properties.


## Structures and Classes
As a general guideline, prefer structures because they're easier to reason about, and use classes when they're appropriate or necessary. In practice, this means most of the custom types you define will be structures and enumerations.
> Swift is able to detect changes in structs and not classes.

### Structures and Enumerations Are Value Types
A __value type__ is a type whose value is copied when it's assigned to a variable or constant, or when it's passed to a function.
- All of the basic types in Swift are value types, and are implemented as structures BTS
- All structures and enumerations are value types in Swift

### Classes Are Reference Types
Rather than a copy, a reference to the same existing instance is used.
- This also shows how reference types can be harder to reason about.

#### Identity Operators
Whether two constants or variables refer to exactly the same instance of a class.
- Identical to (`===`)
- Not identical to (`!==`)

## Initialization
### Initialization Parameters
```swift
struct Celsius {
    var tempInC: Double

    init(fromFahrenheit fahrenheit: Double){
        tempInC = (fahrenheit - 32.0) 1.8
    }

    init(fromKelvin kelvin: Double) {
        tempInC = kelvin - 273.15
    }
}

let boilingPointOfWater = Celsius(fromFahrenheit: 212.0)
let boilingPointOfWater = Celsius(fromKelvin: 273.15)
```
- `fromFahrenheit` and `fromKelvin` are argument labels for use when calling the initializer
- `fahrenheit` and `kelvin` are parameter names to be used inside methods
----
Swift provides an automatic argument label for every parameter in an initializer if not provided.
```swift
struct Color {
    var red, green, blue: Double
    init(red: Double, green: Double, blue: Double) {
        self.red = red
        self.green = green
        self.blue = blue
    }

    init(white: Double) {
        red = white
        green = white
        blue = white
    }
}

let white = Color(white: 0.5)
let magenta = Color(red: 1.0, green: 0.0, blue: 1.0)
```

### Initializer parameters without argument labels
Use underscore `-`
```swift
struct Celsius {
    var tempInC: Double

    init(fromFahrenheit fahrenheit: Double){
        tempInC = (fahrenheit - 32.0) 1.8
    }

    init(fromKelvin kelvin: Double) {
        tempInC = kelvin - 273.15
    }

    init(_ celsius: Double) {
        tempInC = celsius
    }
}

let boiling = Celsius(100.0)
```

### Default Initializers
The default initializer simply creates a new instance with all of its properties set to their default values.
```swift
class ShoppingList {
    var name: String?
    var quantity = 1
    var purchased = false
}

var list = ShoppingList()
```

_Structure_ types automatically receive a _memberwise initializer_ if they don't define any of their own custom initializers.    
You can omit values for any properties that have default values.
```swift
struct Size {
    var width = 0.0, height = 0.0
}

let twoByTwo = Size(width: 2.0, height: 2.0)
let threeByZero = Size(width: 3.0)
let zeroByZero = Size()
```