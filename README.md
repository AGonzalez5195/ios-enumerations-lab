# Enumerations lab

## Question 1

a) Define an enumeration called `iOSDeviceType` with member values `iPhone`, `iPad`, `iWatch`. Create a variable called `myDevice` and assign it one member value.
```
enum iOSDeviceType {

case iPhone

case iPad

case iWatch
}
let myDevice = iOSDeviceType.iPhone
```
b) Adjust your code above so that `iPhone` and `iPad` have associated values of type String which represents the model number, eg: `iPhone("6 Plus")`. Use a switch case and let syntax to print out the model number of each device.
```
enum iOSDeviceType {

case iPhone (String)

case iPad (String)

case iWatch (Int)

    func printDescription() { //let modelType is a variable being made from the associated type, String.
    switch self {
    case .iPhone (let modelType):
        print("This is an iPhone \(modelType)")
    case .iPad (let modelType):
        print("This is an iPad \(modelType)")
    case .iWatch (let versionNumber):
        print("This is an iWatch \(versionNumber)")
}
}
}
let myDevice = iOSDeviceType.iPhone("6Plus") //This creates an instance of the enum iOSDeviceType and assigns it to the constant, 'myDevice'.

//Using that instance, we can now utilize the function made in the enum and call it for myDevice.

myDevice.printDescription()

//However, the constant does not necessarily need to even be made in order to call the function. In this case, since 'myDevice' is equal to 'iOSDeviceType.iPhone("6Plus")', simply using the full name of the latter and calling the function on that will return the same result. Example:

let myDeviceExample = iOSDeviceType.iPhone("6Plus")
myDevice.printDescription() == iOSDeviceType.iPhone("6Plus").printDescription() //true

```
 
## Question 2

a) Write an enum called `Shape` and give it cases for `triangle`, `rectangle`, `square`, `pentagon`, and `hexagon`.

b) Write a method inside `Shape` that returns how many sides the shape has. Create a variable called `myFavoritePolygon` and assign it to one of the shapes above, then print out how many sides it has.

```
enum shape {
case triangle
case rectangle
case square
case pentagon
case hexagon

    func  numOfSides ()-> String{
    switch self{
    case .triangle:
        return "Triangle has 3 sides"
    case .rectangle:
        return " Rectangle has 4 Sides"
    case .square:
        return "Square has 4 Sides"
    case .pentagon:
        return "Pentagon 5 Sides"
    case .hexagon:
    return "Hexagon has 6 Sides"
}
}
}

let myFaveShape = shape.hexagon

print(myFaveShape.numOfSides())
```

c) Re-write `Shape` so that each case has an associated value of type Int that will represent the length of the sides (assume the shapes are regular polygons so all the sides are the same length) and write a method inside that returns the perimeter of the shape.


```
enum shape {
case triangle
case rectangle
case square
case pentagon
case hexagon

    func perimeter (num: Int)-> Int{
    switch self {
    case  .triangle:
        return num * 3
    case  .rectangle:
        return num * 4
    case  .square:
        return num * 4
    case .pentagon:
        return num * 5
    case .hexagon:
        return num * 6
}
}
}

let myFaveShape = shape.triangle

print(myFaveShape.perimeter(num: 5))
```
## Question 3

Write an enum called `OperatingSystem` and give it cases for `windows`, `mac`, and `linux`. Create an array of 10 `OperatingSystem` objects where each one is set to a random operating system. Then, iterate through the array and print out a message depending on the operating system.

```
enum OperatingSystem {

case windows

case mac

case linux

}

let l = OperatingSystem.linux

let w = OperatingSystem.windows

let m = OperatingSystem.mac

var array: [OperatingSystem] = [l,w,m,w,l,l,w,m,w,l]

for stuff in array {
    if stuff == OperatingSystem.mac {
            print ("macs are overpriced")
        }
        if stuff == OperatingSystem.linux {
            print("linux is for nerds")
        }
        if stuff == OperatingSystem.windows {
            print("windows is ugly")
            }
    }
```

## Question 4

You are working on a game in which your character is exploring a grid-like map. You get the original location of the character and the steps he will take.

- A step .up will increase the y coordinate by 1.
- A step .down will decrease the y coordinate by 1.
- A step .right will increase the x coordinate by 1.
- A step .left will decrease the x coordinate by 1.
- Print the final location of the character after all the steps have been taken.

```swift
enum Direction {
    case up
    case down
    case left
    case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

for direction in steps {
    print("The current location is at x: \(location.x) and y: \(location.y)")
    print("I am about to go \(direction)")
    switch direction {
    case .up:
        location.y += 1
    case .down:
        location.y -= 1
    case .left:
        location.x -= 1
    case .right:
        location.x += 1
    }
}

print("The final location is: \(location)")
```


## Question 5

a) Define an enumeration named `HandShape` with three members: `.rock`, `.paper`, `.scissors`.

b) Define an enumeration named `MatchResult` with three members: `.win`, `.draw`, `.lose`.

c) Write a function called `match` that takes two `HandShapes` and returns a `MatchResult`. It should return the outcome for the first player (the one with the first hand shape).

Hint: Rock beats scissors, paper beats rock, scissor beats paper
```
enum HandShape {
    case rock
    case paper
    case scissors
}

enum MatchResult {
    case win
    case draw
    case lose
}

func match(firstShape: HandShape, secondShape: HandShape) -> MatchResult {
    switch firstShape {
    case .rock:
        switch secondShape {
        case .rock: return .draw
        case .paper: return .lose
        case .scissors: return .win
        }
    case .paper:
        switch secondShape {
        case .rock: return .win
        case .paper: return .draw
        case .scissors: return .lose
        }
    case .scissors:
        switch secondShape {
        case .rock: return .lose
        case .paper: return .win
        case .scissors: return .draw
        }

    }
}

```


## Question 6

a) You are given a `CoinType` enumeration which describes different coin values. Print the total value of the coins in the array `moneyArray` which contains tuples of type (`quantity`, `CoinType`).

```swift
enum CoinType: Int {
    case penny = 1
    case nickle = 5
    case dime = 10
    case quarter = 25
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
                                   (15,.nickle),
                                   (3,.quarter),
                                   (20,.penny),
                                   (3,.dime),
                                   (7,.quarter)]

// your code here
```

b) Write a method in the `CoinType` enum that returns an Int representing how many coins of that type you need to have a dollar. Then, create an instance of `CoinType` set to `.nickle` and use your method to print out how many nickels you need to have to make a dollar.


## Question 7

a) Write an enum called `DayOfWeek` to represent the days of the week with a raw value of type String.

b) Given the array `poorlyFormattedDays`, write code that will produce an array of enums that match the days.

`let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]`

c) Write a method in `DayOfWeek` called `isWeekend` that determines whether a day is part of the weekend or not and write code to calculate how many week days appear in `poorlyFormattedDays`.


## Question 8

a) Create an enum called `MetroLine` with cases for the colors of the metro train lines. Create an instance of `MetroLine`.
```
enum MetroLine {
case orange
case purple
case green

}

let metroLineChoice = MetroLine.orange

```

b) Modify your enum so that each case has an associated value of either Character or Int that will represent the train on that line. Create a new instance of `MetroLine` and give it an appropriate train letter or number.

```
enum MetroLine {
case orange (Int)
case purple (Int)
case green (Character)

}

let metroLineChoice = MetroLine.orange(69)
print(metroLineChoice)
let otherMetroLineChoice = MetroLine.green("K")
print(otherMetroLineChoice)

```

c) Write code that prints the train letter or number of your instance of `MetroLine`.

```
enum MetroLine {
case orange (Int)
case purple (Int)
case green (Character)

func printDescription() {
switch self {
case .orange (let trainNumber):
print("I am taking the orange \(trainNumber).")
case .purple (let trainNumber):
print("I am taking the purple \(trainNumber).")
case .green  (let trainLetter):
print("I am taking the green \(trainLetter).")

}

}
}
let myChoice = MetroLine.orange(69)
myChoice.printDescription()

```

## Question 9

a) Think of your own example of something that can be modeled as an enum and write it. Remember that enums allow you to create instances of a defined list of cases.

b) Add a method to your enum.... try to have the method make sense.
