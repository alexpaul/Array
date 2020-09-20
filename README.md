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

## 2D Array Case Study 

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

