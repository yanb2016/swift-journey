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

