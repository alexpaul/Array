# Array

## Array Initialization 

```swift 
let genericArraySyntax: Array<String> = ["Alex", "John", "Steve", "Wozniak"]
let arrayLiteral = [1, 2, 3, 4, 5]
var emptyArray = [Int]()

var bucketsArray = Array(repeating: [Int](), count: 4)
```

## Heterogeneous Array 

```swift 
let arr: [Any] = [1, 2, 3.3, 4.3, 5.3, 6.3, "7.0"] // Heterogeneous collection must have an explicit type [Any]

for element in arr {
  if let char = element as? Character {
    print("\(char) is a Character")
  }
  if let int = element as? Int {
    print("\(int) is an Int")
  }
  if let double = element as? Double {
    print("\(double) is a Double")
  }
  if let string = element as? String,
     let stringValue = Double(string) {
    print("\(stringValue) is a Double")
  }
}
```

## Partition 

```swift 
var ages = [7, 1, 34, 2, 23, 2, 4, 90, 34, 10]

let partitionIndex = ages.partition { $0 > 10 }

print(partitionIndex) // 6

print(ages) // [7, 1, 10, 2, 4, 2, 23, 90, 34, 34]

let ages10AndLess = ages[..<partitionIndex]
let agesOlderThan10 = ages[partitionIndex...]

print(ages10AndLess) // [7, 1, 10, 2, 4, 2]
print(agesOlderThan10) // [23, 90, 34, 34]
```
