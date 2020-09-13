# Array

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
