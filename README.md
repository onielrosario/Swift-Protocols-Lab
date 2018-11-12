
## Protocols Lab

## Instructions for lab submission 

1. Fork the assignment repo
1. Clone your Fork to your machine
1. Complete the lab
1. Push your changes to your Fork
1. Submit a Pull Request back to the assignment repo
1. Paste a link of the pull request on Canvas and submit

<pre> 
Question 1.
Create a Human class with two properties: name of type String, and age of type Int. You'll need to 
create a memberwise initializer for the class. Initialize two Human instances.

Make the Human class adopt the CustomStringConvertible. Print both of your previously initialized
Human objects.

Make the Human class adopt the Equatable protocol. Two instances of Human should be considered equal
if their names and ages are identical to one another. Print the result of a boolean expression 
evaluating whether or not your two previously initialized Human objects are equal to eachother
(using ==). Then print the result of a boolean expression evaluating whether or not your two
previously initialized Human objects are not equal to eachother (using !=).

Make the Human class adopt the Comparable protocol. Sorting should be based on age. Create another
three instances of a Human, then create an array called people of type [Human] with all of the
Human objects that you have initialized. Create a new array called sortedPeople of type [Human] 
that is the people array sorted by age.
</pre> 

```swift
class Person: CustomStringConvertible, Equatable, Comparable {


var age: Int
var occupation: String

var description: String {
return "the person\'s age is \(age) and occupation is \(occupation)."
}

init(age: Int, occupation: String) {
self.age = age
self.occupation = occupation
}

static func == (lhs: Person, rhs: Person) -> Bool {
return
lhs.age == rhs.age &&
lhs.occupation == rhs.occupation
}

static func < (lhs: Person, rhs: Person) -> Bool {
return
lhs.age < rhs.age
}
}

//create instances of person object

let kathy = Person.init(age: 20, occupation: "Data scientist")
let genesis = Person.init(age: 21, occupation: "Software Developer")
//let genesis = Person.init(age: 20, occupation: "Data scientist")
print(kathy)

if kathy == genesis {
print("same person")
} else{
print("different individuals")
}

let sortedPeople = [kathy,genesis].sorted{$0 < $1}
print(sortedPeople)
```

</br> </br> 


<pre> 
Question 2. 
Create a protocol called Vehicle with two requirements: a nonsettable numberOfWheels property of
type Int, and a function called drive().

Define a Car struct that implements the Vehicle protocol. numberOfWheels should return a value of 4,
and drive() should print "Vroom, vroom!" Create an instance of Car, print its number of wheels, 
then call drive().

Define a Bike struct that implements the Vehicle protocol. numberOfWheels should return a value of 2,
and drive() should print "Begin pedaling!". Create an instance of Bike, print its number of wheels,
then call drive().
</pre>  

```swift

protocol Vehicle {
var numberOfWheels: Int {get}

static func drive()

}

struct Car: Vehicle {
var numberOfWheels: Int {
return 4
}

static func drive() {
print("Vroom, vroom!")
}

}
let car = Car()
print(car.numberOfWheels)

Car.drive()

struct Bike: Vehicle {
var numberOfWheels: Int {
return 2
}

static func drive() {
print("Begin pedaling!")
}
}
let bike = Bike()
print(bike.numberOfWheels)
Bike.drive()
```

</br> </br> 

<pre> 
Question 3. 
// Given the below two protocols, create a struct for penguin(a flightless bird) and an eagle.
Give your structs some properties and have them conform to the appropriate protocols.

protocol Bird {
 var name: String { get }
 var canFly: Bool { get }
}

protocol Flyable {
 var airspeedVelocity: Double { get }
}
</pre> 
```swift

protocol Bird {
var name: String { get }
var canFly: Bool { get }
}

protocol Flyable {
var airspeedVelocity: Double { get }
}

struct Penguin: Bird {
var name: String
var canFly: Bool
}

struct Eagle: Bird, Flyable {
var name: String
var canFly: Bool
var airspeedVelocity: Double
}

let penguin = Penguin.init(name: "Penguin", canFly: false)
let eagle = Eagle.init(name: "Eagle", canFly: true, airspeedVelocity: 40.0)
```

</br> </br> 

<pre>
Question 4. 
// Create a protocol called Transformation

// create a mutating method called transform

// Make an enum called SuperHero (have it conform to Transformation) and an instance of it named
bruceBanner. Make it so that when the transform function is called that bruceBanner turns from 
.notHulk to .hulk.

enum SuperHero: Transformation {
    // write code here.
}

Example Output: 
var bruceBanner = SuperHero.notHulk

bruceBanner.transform() . // hulk

bruceBanner.transform()  // notHulk
</pre> 
```swift

protocol Transformation {

mutating func tranfsform()
}

enum SuperHero: Transformation {
case peterParker
case bruceBanner
case steveRodgers
case hulk




mutating func tranfsform()  {
switch self {
case .hulk: self = .bruceBanner
print("no Gamma rays effect")

case .bruceBanner: self = .hulk
print("Gamma rays detected")
case .steveRodgers:
print("not Hulk")
default:
print("rip stan lee")

}
}
}

var bruceBanner = SuperHero.hulk
bruceBanner.tranfsform()
```

</br> </br> 

<pre>
Question 5. 
// 1. Create a protocol called Communication

// 2. Give it a property called talk, of type String, and assign it an explicit getter.

// 3. Create three Classes. Cow, Dog, Cat.

// 4. Have your three classes conform to Communication

// 5. talk should return a unique message for each animal when talk is called.

// 6. Put an instance of each of your Classes in an array.

// 7. Iterate over the array and have them print talk.
</pre> 
```swift

protocol Communication {
var talk: String {get}


}
class Dog: Communication{
var talk: String {
return "The Dog goes: Woof!"
}


}
class Cow: Communication{
var talk: String {
return "The Cow goes: Moo!"
}


}
class Cat: Communication{
var talk: String {
return "The Cat goes: Meow!"
}


}
let houseCat = Cat.init()
let gaurdDog = Dog.init()
let farmCow = Cow.init()
let animals: [Communication] = [houseCat,gaurdDog,farmCow]
for animal in animals {
print(animal.talk)
}

```


