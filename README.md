r# Strings Lab 2

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.

## Question 1

You are given a string stored in variable `problem`. Write code so that you print each word of the string on a new line.

```swift
var problem = "split this string into words and print them on separate lines"
var probToArray = problem.components(separatedBy: " ")

for word in probToArray{print(word)}
```

Example

Input:
`var problem ="split this string into words and print them on separate lines"`

Output:
```swift
split
this
string
into
words
and
print
them
on
separate
lines
```


## Question 2

Given a string `testString` create a new variable called `condensedString` that has any consecutive spaces in `testString` replaced with a single space.

```swift
let testString = "  How   about      thesespaces  ?  "
//condensedString = " How about thesespaces ? "


var condensedString = testString.replacingOccurrences(of: "[\\s]+", with: " ", options: .regularExpression, range: nil)
print(condensedString)

```


## Question 3

Given a string with multiple words. Reverse the string word by word.

Example:

Sample Input: `"Swift is the best language"`

Sample Output: `"language best the is Swift"`


```
swift
var input = "Swift is the best language"
var inputArray = input.components(separatedBy: " ")
var output = String()

for word in inputArray{
output = word + " " + output
}
print(output)
```


## Question 4

Given a string with multiple words. Write code that prints how many of them are palindromes.

Example:

Sample Input: `"danaerys dad cat civic bottle"`

Sample Output: `2`

```
swift
func isPalindrome(str:String)-> Bool{
let reversedStr = String(str.reversed())
if str == reversedStr{return true}
else{return false}
}

var input = "danaerys dad cat civic bottle"
var toArray = input.components(separatedBy: " ")
var counter = 0

for word in toArray{
if(isPalindrome(str: word)){counter += 1}
}; print(counter)

```


## Question 5

You are given a string representing an **attendance record** for a student. The record only contains the following three characters:

`'A' : Absent.`

`'L' : Late.`

`'P' : Present.`

If a student has more than one 'A' or more than 2 continuous 'L's that student should not be rewarded. Print true if student is to be rewarded and False if they shouldn't.

Example:

Sample Input: `"PPALLP"`

Sample Output: `true`

```
var text = "PPALLP"

//let pattern1 = "A"
let pattern2 = "LL{2,}"  

func reward(input: String) -> Bool{
    var aCounter = 0
    for i in input {
        if(i == "A"){aCounter += 1}
}
if (aCounter > 1) || (text.range(of: pattern2, options:.regularExpression) != nil){ return false}  //No reward because there is a match
else{return true}   //reward
}
print(reward(input:text))

```



## Question 6

Given a tuple with two strings. The first string is a **ransom note**, the second string being the characters from a magazine. Determine whether or not you can construct the ransom note using the characters from the magazine.

Each letter from the magazine can only be used once. You can assume all letters are lowercased.

Examples:

Sample Input1: `("a", "b")`

Sample Output1: `False`

Sample Input2: `("aa", "aab")`

Sample Output2: `True`

```
var tuple = (str1: "aa", str2: "aab")
var dictionary: [String:Int] = [:]

//tuple.str1.count > tuple.str2.count ? print("False") : print("True")

for char in tuple.str2 {
    if dictionary.keys.contains("\(char)"){ //dict.keys.contains(key)
        dictionary.updateValue(dictionary["\(char)"]!+1, forKey: "\(char)")
    }else{
        dictionary["\(char)"] = 1
    }
}

func ransomNote() -> Bool{

for char1 in tuple.str1{
    if dictionary.keys.contains("\(char1)"){
        if dictionary["\(char1)"]! > 0{
            dictionary.updateValue(dictionary["\(char1)"]!-1, forKey: "\(char1)")
        }else {return false}
    }else {return false}
}
    return true
}
print(ransomNote())

```



