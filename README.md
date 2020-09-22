# Array

## Array Initialization 

```swift 
let genericArraySyntax: Array<String> = ["Alex", "John", "Steve", "Wozniak"]
let arrayLiteral = [1, 2, 3, 4, 5]
var emptyArray = [Int]()

var bucketsArray = Array(repeating: [Int](), count: 4)
print(bucketsArray) // [[], [], [], []]
```

## Adding and Removing 

```swift 
var jobsApplied = ["Apple", "Peloton", "Google", "Box", "Zoom", "Bloomberg"]

var companiesToApply = ["Houzz", "ZocDoc", "Stockpile"]
```

#### Insert  
```swift 
jobsApplied.insert("Zwift", at: 1) // ["Apple", "Zwift", "Peloton", "Google", "Box", "Zoom", "Bloomberg"]
```

#### Append 

We can `append` a single element or we can append a sequence e.g `companiesToApply`

```swift 
jobsApplied.append(contentsOf: companiesToApply) // ["Apple", "Zwift", "Peloton", "Google", "Box", "Zoom", "Bloomberg", "Houzz", "ZocDoc", "Stockpile"]
```

#### Remove

```swift 
jobsApplied.removeLast() // removes the last element - THIS WILL CRASH IF THE ARRAY IS EMPTY - PROCEED WITH CAUTION
```

```swift 
jobsApplied.popLast() // safer as it returns an optional so will safely work on an empty array
```


## Search 

#### `firstIndex(of:_)`

```swift 
let names = ["Bob", "Sally", "John", "Heather"]

if let index = names.firstIndex(of: "Bob") { // O(n) runtime operation
  print("found name at index \(index)") // found name at index 0
}
```

#### `contains`

```swift 
if names.contains("John") {
  print("Hi John Appleseed.") // Hi John Appleseed.
}
```

## Accessing Elements 

```swift 
let fruits = ["apple", "banana", "oranges", "kiwi"]
```

#### `first` element 

```swift 
if let first = fruits.first {
  print("The first fruit is \(first)") // The first fruit is apple
}
```

#### `last` element 

```swift 
if let last = fruits.last {
  print("The last fruit is \(last)") // The last fruit is kiwi
}
```

#### `randomElement`

```swift 
if let randomFruit = fruits.randomElement() {
  print("Randomly picking \(randomFruit)") // Randomly picking banana
}
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

## Stride 

```swift 
let names = ["Beth", "Josh", "Nancy", "Quincy", "Mary"]

for index in stride(from: 0, through: names.count - 1, by: 1) {
  print(names[index])
}

/*
 Beth
 Josh
 Nancy
 Quincy
 Mary
*/
```

## Reordering an Array's elements  

#### `swapAt(Int, Int)`

```swift 
var priorityList = ["Applying to jobs", "DSA", "Learning Advance Topics", "Independent Project", "Networking"]

priorityList.swapAt(0, priorityList.count - 1)

print(priorityList) // ["Networking", "DSA", "Learning Advance Topics", "Independent Project", "Applying to jobs"]
```

#### `shuffle()`

```swift 
var lunchOptions = ["salad", "pasta", "tacos", "fish and chips", "veggie burger"]

lunchOptions.shuffle() // shuffles array in-place

print(lunchOptions) // ["salad", "pasta", "veggie burger", "fish and chips", "tacos"]
```

#### `sort()`

```swift 
lunchOptions.sort() // sorts in-place

print(lunchOptions) // ["fish and chips", "pasta", "salad", "tacos", "veggie burger"]
```

#### `partition(by: (Element) -> Bool) -> Int` 

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

## (2D Array, matrix or grid) Case Study 

Given the following Tic Tac Toe board below.  

```swift 
let ticTacToe = [["X", "O", "O"],
                 ["X", "O", "X"],
                 ["X", "X", "O"]]
```

Perform the following operations: 

#### Print the rows of the tic tac toe board

<details> 
  <summary>Solution</summary> 

```swift 
for row in 0..<ticTacToe.count {
  print(ticTacToe[row])
}

/*
 ["X", "O", "O"]
 ["X", "O", "X"]
 ["X", "X", "O"]
*/
```

</details> 

</br>

#### Print all the individual values of the tic tac toe board

<details> 
  <summary>Solution</summary> 

```swift 
for row in 0..<ticTacToe.count {
  for col in 0..<ticTacToe.count {
    print(ticTacToe[row][col], terminator: " ")
  }
}
// X O O X O X X X O
```

</details> 

</br>

#### Print the columns of the tic tac toe board

```swift 
/*
 ["X", "O", "O"]
 ["X", "O", "X"]
 ["X", "X", "O"]
*/

/*
 [0,0]  [0,1]  [0,2]
 [1,0]  [1,1]  [1,2]
 [2,0]  [2,1]  [2,2]
*/
```

<details> 
  <summary>Solution</summary> 

```swift 
var colIndex = 0
for col in colIndex..<ticTacToe.count { // 0, 1, 2
  for row in 0..<ticTacToe.count { // 0, 1, 2
    print("\(ticTacToe[row][col])")
  }
  print()
}

/*
 X
 X
 X

 O
 O
 X

 O
 X
 O
*/
```

</details> 

</br>

#### Print the diagonals of the tic tac toe board

```swift 
/*
 ["X", "O", "O"]
 ["X", "O", "X"]
 ["X", "X", "O"]
*/

/*
 [0,0]  [0,1]  [0,2]
 [1,0]  [1,1]  [1,2]
 [2,0]  [2,1]  [2,2]
 
 
 [0,0]  [1,1]  [2,2] - leftTop -> rightBottom
 [2,0]  [1,1]  [0,2] - leftBottom -> rightTop
*/
```

<details> 
  <summary>Solution</summary> 

```swift 
// [0,0]  [1,1]  [2,2] - leftTop -> rightBottom
for i in 0..<ticTacToe.count {
  print(ticTacToe[i][i])
}
// X O O


// [2,0]  [1,1]  [0,2] - leftBottom -> rightTop
for i in 0..<ticTacToe.count {
  print(ticTacToe[ticTacToe.count - 1 - i][i]) // 2, 1, 0
}
// X O O
```

</details> 

</br>


### Challenges 

#### Challenge 1

Constraints: do the problem below withou using built-in `reverse()`

[HackerRank - Reverse Array](https://www.hackerrank.com/challenges/arrays-ds/problem)

#### Challenge 2 

[HackerRank - Hour Glass](https://www.hackerrank.com/challenges/2d-array/problem)

#### Challenge 3 

[LeetCode - Valid Tic Tac Toe State](https://leetcode.com/problems/valid-tic-tac-toe-state/)

## Resources 

1. [Apple documentation - Array](https://developer.apple.com/documentation/swift/array)
2. [LeetCode - Array](https://leetcode.com/tag/array/)


