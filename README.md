# Closures Lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.

## Question 1

Write a function named `applyKTimes` that takes an integer `K` and a closure and calls the closure K times. The closure will not take any parameters and will not have a return value.

Function Definition:
func applyKTimes(_ K: Int, _ closure: () -> ())

Example:
Input:

```swift
applyKTimes(3) {
    print("Hello Closures!")
}
```
Output:

```swift
Hello Closures!
Hello Closures!
Hello Closures!
```
```swift
func applyKTimes(_ K: Int, _ closure: () -> ()){
for i in 0..<K{
closure()
}
}

applyKTimes(3) {
print("Hello Closures!")
}
```


## Question 2

Use `filter` to create an array called `multiples` that contains all the multiples of 3 from `numbers` and then print it.

`let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Example:
Input: `let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Expected values: `multiples = [3, 6, 9, 3, 12]`

```swift
let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]

let multiples = numbers.filter {$0 % 3 == 0}
print(multiples)
```


## Question 3

Find the largest number from `numbers` and then print it. Use `reduce` to solve this exercise.

Example:
Input: `let numbers = [4, 7, 1, 9, 6, 5, 6, 9]`

Output: `9`
```swift
let numbers = [4, 7, 1, 9, 6, 5, 6, 9]

let bigNum = numbers.reduce(0, { x,y in x > y ? x : y})
print(bigNum)
```

## Question 4

Join all the strings from `strings` into one using `reduce`. Add spaces in between strings. Print your result.

Example:
Input: `let strings = ["We", "Heart", "Swift"]`

Output: `"We Heart Swift"`
```swift
let strings = ["We", "Heart", "Swift"]

let combine = strings.reduce("",{$0 + " " + $1})
print(combine)
```


## Question 5

`let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]`

a. Use `sortedBy` to sort `cities` in alphabetical order.

b. Use `sortedBy` to sort `cities` alphabetical order of the second character of the city name.

c. Use `sortedBy` to sort `cities` in order of the length of the city name.

```swift 
//1.
let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]

print(cities.sorted(by: <))

//2.
print(cities.sorted(by:{(s1: String, s2: String)-> Bool in
return (s1.dropFirst(1)) < (s2.dropFirst(1))}))

//3.
print(cities.sorted(by: {(s1: String,s2: String)->Bool in
return s1.count > s2.count
}))

```
## Question 6

`let citiesWithPopulation: [(String, Int)] = [("Shanghai", 24256800), ("Beijing", 21516000), ("Delhi", 16787941), ("Lagos", 16060303), ("Tianjin", 15200000), ("Karachi", 14910352), ("Karachi", 14160467), ("Tokyo", 13513734), ("Guangzhou", 13080500), ("Mumbai", 12442373), ("Moscow", 12380664), ("São Paulo", 12038175)]`

a. Use `sortedBy` to sort `citiesWithPopulation` in ascending order of population.

b. Use `sortedBy` to sort `citiesWithPopulation` in reverse alphabetical order of the last character in the city name.

```swift
//1.
print(citiesWithPopulation.sorted(by: {(s1: (String,Int), s2: (String,Int)) ->Bool in return s1.1 < s2.1}))

//2.
print(citiesWithPopulation.sorted(by: {(s1: (String,Int), s2: (String,Int)) ->Bool in return s1.0.last! > s2.0.last!}))
```

## Question 7

Sort `numbers` in ascending order by the number of divisors. If two numbers have the same number of divisors the order in which they appear in the sorted array does not matter.

`var numbers = [1, 2, 3, 4, 5, 6]`

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output:

```swift
numbers = [1, 2, 3, 5, 4, 6]
// 1 has one divisor
// 2, 3 and 5 have 2
// 4 has 3 divisors
// 6 has 4 divisors

// [1, 5, 2, 3, 4, 6] would also have been a valid solution
```
```swift
// I didn't use closure sorry
var index = 0

func divisor()-> Int{
var count = 0

for i in 1...numbers[index]{
if numbers[index] % i == 0{
count += 1
}

}
index += 1
return count
}
var a = 0
while a < 6{
print("The number: \(numbers[index])  has \(divisor()) divisors")
a += 1
}
```

## Question 8

Find the sum of the squares of all the odd numbers from `numbers` and then print it.

`var numbers = [1, 2, 3, 4, 5, 6]`

a. Write code that removes all the odd numbers from the array.

b. Write code that squares all the numbers in the array.

c. Write code that finds the sum of the array.

d. Now use `map`, `filter` and `reduce` to solve this problem.

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output: `35 // 1 + 9 + 25 -> 35`

```swift
var numbers = [1, 2, 3, 4, 5, 6]
//a.
var index = 0
for i in numbers{
if i % 2 != 0{
numbers.remove(at: index)
index += 1
}
}
print(numbers)
//b.
var numbers = [1, 2, 3, 4, 5, 6]
//b.
var index = 0
for i in numbers{
numbers[index] = i * i
index += 1
}
print(numbers)
//c.
var numbers = [1, 2, 3, 4, 5, 6]
var sum = 0
//c.
for i in numbers{
sum = sum + i
}
print(sum)
//d.
print(((numbers.filter{$0 % 2 != 0}).map{$0 * $0}).reduce(0, +))
```


## Question 9

Implement a function `forEach(array: [Int], _ closure: Int -> ())` that takes an array of integers and a closure and runs the closure for each element of the array.

Example:
Function with Input:

```swift
forEach([1, 2, 3, 4]) {
    print($0 * $0)
}
```

Output:

```swift
1
4
9
16
```
```swift
var numbers = [1, 2, 3, 4, 5, 6]

func forEach(_ array: [Int], _ closure: (Int) -> ()){
for i in array{
closure(i)
}
}
forEach(numbers) {
print($0 * $0)
}
```

## Question 10

Implement a function `combineArrays` that takes 2 arrays and a closure that combines 2 Ints into a single Int. The function combines the two arrays into a single array using the provided closure. Assume that the 2 arrays have equal length.

Example:
Input:

```swift
var array1 = [1,2,3,4]
var array2 = [5,5,5,3]
combineArrays(array1,array2) {
    $0 * $1
}
```

Output: `[5,10,15,12]`
```swift
func combineArrays (arr1 : [Int], arr2: [Int], _ closure: (Int,Int)->()){
var index = 0
for i in arr1{
closure(i , arr2[index])
index += 1
}
}

var array1 = [1,2,3,4]
var array2 = [5,5,5,3]

combineArrays(arr1: array1, arr2: array2, {
print($0 * $1)
})
```

## Question 11

a) Write a function called `intsToStrings` that takes an array of Ints and a closure as parameters and returns an array of Strings. The closure should take an Int and return a String. The function should apply the closure to the ints in the array.

`let theInts = [1, 2, 3, 44, 555, 6600, 10763]`

b) Define a closure assigned to a constant called `asString` that just turns an Int to a String and pass it to `intsToStrings`.

c) Define a closure assigned to a constant called `evenOdd` that returns "odd" or "even" if the Int is odd or even and pass it to `intsToStrings`.

d) Define a closure assigned to a constant called `englishWords` that returns the written english word of each digit in an Int, 234 -> "two three four", and pass it to `intsToStrings`.

e) Use the built in `map` method on `theInts` to recreate the answers for b, c and d.

Example:
Input:

```swift
let a = intsToStrings(arr: theInts, toString: asString)
let b = intsToStrings(arr: theInts, toString: evenOdd)
let c = intsToStrings(arr: theInts, toString: englishWords)
```

Output:

```swift
a) ["1", "2", "3", "44", "555", "6600", "10763"]
b) ["odd", "even", "odd", "even", "odd", "even", "odd"]
c) ["one ", "two ", "three ", "four four ", "five five five ", "six six zero zero ", "one zero seven six three "]
```
```swift
//a.
let theInts = [1, 2, 3, 44, 555, 6600, 10763]
var emptyArr = [String]()

func intsToStrings(_ arr: [Int],_ closure: (Int)->String){
for i in arr{
emptyArr.append(closure(i))
}
}

intsToStrings(theInts, { (String($0)) })
print(emptyArr)

//b.
let theInts = [1, 2, 3, 44, 555, 6600, 10763]
let asString = { (a: Int) -> String in return String(a)}

func intsToStrings(arr: [Int],toString closure: (Int) -> String) -> [String] {
var emptyArr = [String]()
for i in arr {
emptyArr.append(closure(i))
}
return emptyArr
}

let a = intsToStrings(arr: theInts, toString: asString)
print(a)

//c.
let theInts = [1, 2, 3, 44, 555, 6600, 10763]
let evenOdd = { (a: Int) -> String in
if a % 2 == 0{
return "Even"
}
else{
return "Odd"
}
}

func intsToStrings(arr: [Int],toString closure: (Int) -> String) -> [String] {
var emptyArr = [String]()
for i in arr {
emptyArr.append(closure(i))
}
return emptyArr
}

let a = intsToStrings(arr: theInts, toString: evenOdd)
print(a)
//d.
let theInts = [1, 2, 3, 44, 555, 6600, 10763]
let englishWords = { (a: Int) -> String in
var emptyString = String()

for num in String(a){
switch num {
case "1":
emptyString += "One"
case "2":
emptyString += "Two"
case "3":
emptyString += "Three"
case "4":
emptyString += "Four"
case "5":
emptyString += "Five"
case "6":
emptyString += "Six"
case "7":
emptyString += "Seven"
case "8":
emptyString += "Eight"
case "9":
emptyString += "Nine"
case "0":
emptyString += "Zero"
default:
emptyString += "Over 9000 "
}
}
return emptyString
}

func intsToStrings(arr: [Int],toString closure: (Int) -> String) -> [String] {
var emptyArr = [String]()
for i in arr {
emptyArr.append(closure(i))
}
return emptyArr
}

let a = intsToStrings(arr: theInts, toString: englishWords)
print(a)

//e.
//sub B.
let theInts = [1, 2, 3, 44, 555, 6600, 10763]
let test = theInts.map{String($0)}
print(test)
//sub C.
let theInts = [1, 2, 3, 44, 555, 6600, 10763]
let test = theInts.map{ (a: Int) -> String in
if a % 2 == 0{
return "Even"
}
else{
return "Odd"
}
}
print(test)
//sub D.
let theInts = [1, 2, 3, 44, 555, 6600, 10763]
let test = theInts.map{ (a: Int) -> String in
var emptyString = String()

for num in String(a){
switch num {
case "1":
emptyString += "One"
case "2":
emptyString += "Two"
case "3":
emptyString += "Three"
case "4":
emptyString += "Four"
case "5":
emptyString += "Five"
case "6":
emptyString += "Six"
case "7":
emptyString += "Seven"
case "8":
emptyString += "Eight"
case "9":
emptyString += "Nine"
case "0":
emptyString += "Zero"
default:
emptyString += "Over 9000 "
}
}
return emptyString
}
print(test)

```

## Question 12

let myArray = [34,42,42,1,3,4,3,2,49]

a) Sort `myArray` in ascending order by defining the constant `ascendingOrder` below.

```swift
var myArray = [34,42,42,1,3,4,3,2,49]

let ascendingOrder = {(a: Int, b: Int) -> Bool in return a < b}
var mySortedArray = myArray.sort(by: ascendingOrder)
print(myArray)
```

b) Sort `myArray` in descending order by defining the constant `descendingOrder` below.

```swift
let descendingOrder = {(a: Int, b: Int) -> Bool in return a > b}
let mySecondSortedArray = myArray.sort(descendingOrder)
print(myArray)
```


## Question 13

`let arrayOfArrays = [[3,65,2,4],[25,3,1,6],[245,2,3,5,74]]`

a) Sort `arrayOfArrays` in ascending order by the **3rd element** in each array. You can assume each array will have at least 3 elements.

b) Sort `arrayOfArrays` in ascending order by the 3rd element in each array. Don't assume each array will have at least 3 elements. Put all arrays that have less than 3 elements at the end in any order.

```swift
//a.
let arrayOfArrays = [[3,65,2,4],
[25,3,1,6],
[245,2,3,5,74]]

var arrMatrix = arrayOfArrays.sorted(by: {(a:[Int],b:[Int])->Bool in
if a[2] > b[2]{
return true
}
else{
return false
}
})
print(arrMatrix)
//b.
// has an error tried making an array of 2 ints but got error
var arrayOfArrays = [[3,65,2,4],
[25,3,1,6],
[245,2,3,5,74],
[1,2]]

var arrMatrix = arrayOfArrays.sorted(by: {(a:[Int],b:[Int])->Bool in
if a.count <= 3 && b.count <= 3{
arrayOfArrays.append(a)
return false
}
else if a[2] > b[2]{
return true
}
else{
return false
}
})
print(arrMatrix)

```


## Question 14

```swift
let letterValues = [
"a" : 54,
"b" : 24,
"c" : 42,
"d" : 31,
"e" : 35,
"f" : 14,
"g" : 15,
"h" : 311,
"i" : 312,
"j" : 32,
"k" : 93,
"l" : 203,
"m" : 212,
"n" : 41,
"o" : 102,
"p" : 999,
"q" : 1044,
"r" : 404,
"s" : 649,
"t" : 414,
"u" : 121,
"v" : 838,
"w" : 555,
"x" : 1001,
"y" : 123,
"z" : 432
]
```

a) Sort the string below in descending order according the dictionary `letterValues`:

`var codeString = "aldfjaekwjnfaekjnf"`

b) Sort the string below in ascending order according the dictionary `letterValues`

`var codeStringTwo = "znwemnrfewpiqn"`

```swift
//a.
var codeString = "aldfjaekwjnfaekjnf"
let stringArr = Array(codeString)

let test = stringArr.sorted(by: {(a: Character, b: Character)-> Bool in
letterValues
return a > b
})
print(String(test))

//b.
var codeStringTwo = "znwemnrfewpiqn"
let stringArr = Array(codeStringTwo)

let ascending = stringArr.sorted(by: {(a: Character, b: Character)-> Bool in
letterValues
return a < b
})
print(String(ascending))

```

## Question 15

```swift
let firstAndLastTuples = [("Johann S.", "Bach"),
("Claudio", "Monteverdi"),
("Duke", "Ellington"),
("W. A.", "Mozart"),
("Nicolai","Rimsky-Korsakov"),
("Scott","Joplin"),
("Josquin","Des Prez")]
```

Sort the array of tuples by last name. Print the sorted array using string interpolation so that the output looks like:

```swift
Bach, Johann S.
Des Prez, Josquin
...etc
```

## Question 16

a) Write a function called `myFilter` that takes an array of Doubles and a closure as parameters and returns an array of Doubles. The closure should take a Double and return a Bool. The function should apply the closure to the doubles in the array.

`let theDoubles = [11.45, 3.2, 4.0, 5.67, 58.65, 66.0, 5.2, 5.0]`

b) Define a closure assigned to a constant called `biggerThanTen` that takes a double and returns true if it is greater or equal to 10.0 and pass it to `myFilter`.

c) Define a closure assigned to a constant called `wholeNumber` that takes a double and returns true if it is a whole number and pass it to `myFilter`.

d) Define a closure assigned to a constant called `justEven` that takes a double and returns true if the number to the left of the point is even and pass it to `myFilter`.

e. Use the built in filter method on `theDoubles` to recreate the answers for b, c and d.

Example
Input:

```swift
let a = myFilter(arr: theDoubles, filter: biggerThanTen)
let b = myFilter(arr: theDoubles, filter: wholeNumber)
let c = myFilter(arr: theDoubles, filter: justEven)
```

output:

```swift
a. [11.45, 58.65, 66]
b. [4, 66, 5]
c. [4, 58.65, 66]
```
