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