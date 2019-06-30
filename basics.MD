## simple values
use let to make a constant let thisConstant = 10
use var to make a variable var thisVariable = 5 thisVariable = 15

> When create variable or constant, keep value type as the same
> Question: Since constant value can not be changed, why mention keep the constant value type same


### Operand should be made with same data type or make an instance of the desired type

> change width from Int to String

    let label = "The width is "
    let width = 94
    let widthLabel = label + String(width)


### another way to include values in strings: Write the value in parentheses, and write a backslash (\) before the parentheses

let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."


### use """  three double quotation marks for multiple-line strings, string should be started in a new line

    """
    Hi, there,
    nice to meet you today,
    please let me know if you have any quesitons
    """

### Create arrays and dictionaries using brackets ([]), and access their elements by writing the index or key in brackets.

#### create new empty array, dic, array auto grow
let emptyArray = [String]() emptyArray.append("firstElement")
let emptyDictionary = [String: Float]()

> If type information can be inferred, you can write an empty array as [] and an empty dictionary as [:]—for example, when you set a new value for a variable or pass an argument to a function.

    shoppingList = []
    occupations = [:]

    Control Flow

### Use if and switch to make conditionals, and use for-in, while, and repeat-while to make loops. Parentheses around the condition or loop variable are optional. Braces around the body are required.

> for in loop like for of in js

    for score in scores {
        if score > 50 {
            teamScore += 3
        } else {
            teamScore += 1
        }
    }

### In an if statement, the conditional must be a Boolean expression—this means that code such as if score { ... } is an error, not an implicit comparison to zero.

You can use if and let together to work with values that might be missing. These values are represented as optionals. An optional value either contains a value or contains nil to indicate that a value is missing. Write a question mark (?) after the type of a value to mark the value as optional.


    var optionalString: String? = "Hello"
    print(optionalString == nil) // false

    var optionalName: String? = "John Appleseed"
    var greeting = "Hello!"
    if let name = optionalName {
        greeting = "Hello, \(name)"
        print(greeting) // Hello, John Appleseed
    }

> Another way to handle optional values is to provide a default value using the ?? operator. If the optional value is missing, the default value is used instead

> var can set like var name: String, but let can not. let name: String will show error, constant should be inistialized before using


### Switches support any kind of data and a wide variety of comparison operations—they aren’t limited to integers and tests for equality.

    let vegetable = "red pepper"
    switch vegetable {
        case "celery":
            print("Add some raisins and make ants on a log.")
        case "cucumber", "watercress":
            print("That would make a good tea sandwich.")
        case let x where x.hasSuffix("pepper"):
            print("Is it a spicy \(x)?")
        default:
            print("Everything tastes good in soup.")
    }


After executing the code inside the switch case that matched, the program exits from the switch statement. Execution doesn’t continue to the next case, so there is no need to explicitly break out of the switch at the end of each case’s code.

    let interestingNumbers = [
        "Prime": [2, 3, 5, 7, 11, 13],
        "Fibonacci": [1, 1, 2, 3, 5, 8],
        "Square": [1, 4, 9, 16, 25],
    ]
    var largest = 0
    for (kind, numbers) in interestingNumbers {
        for number in numbers {
            if number > largest {
                largest = number
            }
        }
    }
    print(largest) // 25

### Use while to repeat a block of code until a condition changes. The condition of a loop can be at the end instead, ensuring that the loop is run at least once.

### You can keep an index in a loop by using ..< to make a range of indexes.

    var total = 0
    for i in 0..<4 {
        total += i
    }
>  Use ..< to make a range that omits its upper value, and use ... to make a range that includes both values

0..4 -> 0, 1, 2, 3
0...4 -> 0,1,2,3,4


## Functions and Closures

1. Use func to declare a function
2. Use -> to separate the parameter names and types from the function’s return type.

    func greet(person: String, day: String) -> String {
        return "Hello \(person), today is \(day)."
    }
    greet(person: "Bob", day: "Tuesday")

3. By default, functions use their parameter names as labels for their arguments. Write a custom argument label before the parameter name, or write _ to use no argument label.

    func greet(_ person: String, on day: String) -> String {
        return "Hello \(person), today is \(day)."
    }
    greet("John", on: "Wednesday")

4. Use a tuple to make a compound value—for example, to return multiple values from a function. The elements of a tuple can be referred to either by name or by number.

    func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
        var min = scores[0]
        var max = scores[0]
        var sum = 0

        for score in scores {
            if score > max {
                max = score
            } else if score < min {
                min = score
            }
            sum += score
        }

        return (min, max, sum)
    }
    let statistics = calculateStatistics(scores: [5, 3, 100, 3, 9])
    print(statistics.sum)
    print(statistics.2)

5. ***closure*** Functions can be nested. Nested functions have access to variables that were declared in the outer function. You can use nested functions to organize the code in a function that is long or complex.

    func returnFifteen() -> Int {
        var y = 10
        func add() {
            y += 5
        }
        add()
        return y
    }
    returnFifteen()

6. Functions are a first-class type. This means that a function can return another function as its value.

    func makeIncrementer() -> ((Int) -> Int) {
        func addOne(number: Int) -> Int {
            return 1 + number
        }
        return addOne
    }
    var increment = makeIncrementer()
    increment(7)

7.  ***callback*** A function can take another function as one of its arguments.

    func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
        for item in list {
            if condition(item) {
                return true
            }
        }
        return false
    }
    func lessThanTen(number: Int) -> Bool {
        return number < 10
    }
    var numbers = [20, 19, 7, 12]
    hasAnyMatches(list: numbers, condition: lessThanTen)


8. Functions are actually a special case of closures: blocks of code that can be called later. The code in a closure has access to things like variables and functions that were available in the scope where the closure was created, even if the closure is in a different scope when it is executed—you saw an example of this already with nested functions. You can write a closure without a name by surrounding code with braces ({}). Use in to separate the arguments and return type from the body.

    numbers.map({ (number: Int) -> Int in
        let result = 3 * number
        return result
    })


9. several options for writing closures more concisely. When a closure’s type is already known, such as the callback for a delegate, you can omit the type of its parameters, its return type, or both. Single statement closures implicitly return the value of their only statement.

let mappedNumbers = numbers.map({ number in 3 * number })
print(mappedNumbers)


10.  You can refer to parameters by number instead of by name—this approach is especially useful in very short closures. A closure passed as the last argument to a function can appear immediately after the parentheses. When a closure is the only argument to a function, you can omit the parentheses entirely.

    let sortedNumbers = numbers.sorted { $0 > $1 }
    print(sortedNumbers)