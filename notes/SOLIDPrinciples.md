
# SOLID principles
    SOLID principles complement each other and work together in unision to acheieve the common purpose of well-designed software 
![SOLID](image.png) 

## Single Responsibility principle (SRP)

    every software component should have one and only one responsibility (reson to change)

- Cohesion and Coupling 
    - **cohesion** is the degree to which the valurios parts of a software component are realted **aim for high cohesion**
    - **couplin** is defined as the level of inter dependecy between various software components **aim for losse coupling**
- **Reasons for Change** : Each responsibility or reason for change introduces complexity and potential fragility into code, so separating responsibilities helps mitigate these issues.

- benefits : 
    - making code more readable, maintainable, reusable, testable, and less complex.
    - This leads to easier debugging and enhances overall code quality and scalability.
##### Before SRP (Single Class with Multiple Responsibilities)
```js
class ReportGenerator {
  generateReport(data) {
    const filteredData = this.filterData(data);
    const formattedData = this.formatData(filteredData);
    this.saveReport(formattedData);
  }

  filterData(data) {
    // Code to filter data
  }

  formatData(data) {
    // Code to format data
  }

  saveReport(data) {
    // Code to save report to database
  }
}

```

##### After SRP (Separate Classes for Each Responsibility)
```js
class DataFilter {
  filter(data) {
    // Code to filter data
  }
}

class DataFormatter {
  format(data) {
    // Code to format data
  }
}

class ReportRepository {
  save(data) {
    // Code to save report to database
  }
}

class ReportGenerator {
  constructor() {
    this.dataFilter = new DataFilter();
    this.dataFormatter = new DataFormatter();
    this.reportRepository = new ReportRepository();
  }

  generateReport(data) {
    const filteredData = this.dataFilter.filter(data);
    const formattedData = this.dataFormatter.format(filteredData);
    this.reportRepository.save(formattedData);
  }
}
```

## Open-Closed Principle (OCP)
    software entities should be open for extension, but closed for modification

- new features getting added to the software doesn modify esixting code 
- software component should be expandable to add new features and new behaviors 

- benefits : 
    - ease of adding new features
    - minimal cost of deleopint and testing software 
    - requires decoupling which make it follows single responsibilty principle 

**Note :** Do not follow the open Closed Principle blindly.You will end up with a huge number of classes that can complicate your overall design. But if you see repeated occurences of certain kinds of bugs you should consider it 


##### Before (Violating OCP)
```js
class Shape {
  constructor(type, dimensions) {
    this.type = type;
    this.dimensions = dimensions;
  }

  getArea() {
    if (this.type === 'circle') {
      return Math.PI * Math.pow(this.dimensions.radius, 2);
    } else if (this.type === 'rectangle') {
      return this.dimensions.width * this.dimensions.height;
    }
    // Need to modify this function if we add more shapes
    return 0;
  }
}

// Usage
const circle = new Shape('circle', { radius: 5 });
const rectangle = new Shape('rectangle', { width: 10, height: 5 });

console.log(circle.getArea());      // Output: 78.54
console.log(rectangle.getArea());   // Output: 50
```
##### after (Following OCP)
To follow the Open-Closed Principle, we can use polymorphism. Each shape type will have its own class, implementing a getArea method. The Shape class is now open for extension but closed for modification.

```js
class Shape {
  getArea() {
    throw new Error("Method 'getArea()' must be implemented.");
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.radius = radius;
  }

  getArea() {
    return Math.PI * Math.pow(this.radius, 2);
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  getArea() {
    return this.width * this.height;
  }
}

// Usage
const circle = new Circle(5);
const rectangle = new Rectangle(10, 5);

console.log(circle.getArea());      // Output: 78.54
console.log(rectangle.getArea());   // Output: 50
```

## Liskov Substitution Principle (LSP)
    Objects should be replaceable with their subtypes without affecting the correctness of the program

- subclasses should behave in a way that doesn’t break the expectations of the parent class’s interface

For instance, if class Animal has a method move(), and a subclass Bird overrides move() to fly, any code using Animal should work correctly even if it’s given a Bird object.

##### Before (Violating LSP):
In this example, Bird inherits from FlyingAnimal, but Penguin throws an error when it tries to fly(), which breaks LSP.

```js
class FlyingAnimal {
  fly() {
    console.log("Flying in the sky!");
  }
}

class Bird extends FlyingAnimal {
  fly() {
    console.log("Bird is flying!");
  }
}

class Penguin extends FlyingAnimal {
  fly() {
    throw new Error("Penguins can't fly!");
  }
}

function makeAnimalFly(animal) {
  animal.fly();
}

const sparrow = new Bird();
makeAnimalFly(sparrow); // Bird is flying!

const penguin = new Penguin();
makeAnimalFly(penguin); // Error: Penguins can't fly!

```

##### After (Following LSP):
We can separate FlyingAnimal from NonFlyingAnimal to avoid the problematic fly() method for animals that can’t fly.

```js 
class Animal {
  move() {
    console.log("Animal is moving!");
  }
}

class FlyingAnimal extends Animal {
  fly() {
    console.log("Flying in the sky!");
  }
}

class Bird extends FlyingAnimal {
  fly() {
    console.log("Bird is flying!");
  }
}

class Penguin extends Animal {
  move() {
    console.log("Penguin is swimming!");
  }
}

function moveAnimal(animal) {
  animal.move();
}

const sparrow = new Bird();
moveAnimal(sparrow); // Animal is moving!

const penguin = new Penguin();
moveAnimal(penguin); // Penguin is swimming!

```

**Liskov Substitution Principle (LSP)** encourages a proper hierarchy where subclasses can be substituted for their parent class without changing the correctness of the program.

**Breaking the Hierarchy** happens when subclasses fail to adhere to this principle, leading to behavior that breaks expectations.

**Tell, Don’t Ask** is a principle of encapsulation. It means you should avoid querying an object's internal state and then making decisions outside; instead, you should tell the object what to do, and it should manage its own state and behavior.


## Interface Segregation Principle (ISP)
    no code should be forced to depend on methods it does not use.

- **code should be** : 
    - Small, Specific Interfaces
    - Avoid Large Interfaces
    - More Focused Clients
- **identify violations of ISP**: 
    - fat interfaces 
    - low cohesion 
    - empty method implementiations (in the extened classes)

##### Before Interface Segregation Principle (ISP)

```
public interface IAnimal
{
    void Eat();
    void Sleep();
    void Swim();
    void Fly();
}

public class Penguin : IAnimal
{
    public void Eat()
    {
        // Method implementation
    }

    public void Sleep()
    {
        // Method implementation
    }

    public void Swim()
    {
        // Method implementation
    }

    public void Fly()
    {
        throw new NotImplementedException("Penguins cannot fly");
    }
}
```

##### After Interface Segregation Principle (ISP)
```
public interface IEating
{
    void Eat();
}

public interface ISleeping
{
    void Sleep();
}

public interface ISwimming
{
    void Swim();
}

public interface IFlying
{
    void Fly();
}

public class Penguin : IEating, ISleeping, ISwimming
{
    public void Eat()
    {
        // Method implementation
    }

    public void Sleep()
    {
        // Method implementation
    }

    public void Swim()
    {
        // Method implementation
    }
}

```

- Benefits:
    - **Flexibility:** It allows adding new functionalities without changing existing code.
    -  **Maintainability:** Each class or module is more focused, making it easier to manage and extend.
    - **Clearer Contracts:** Interfaces are tailored to the specific needs of each client.

## Dependency Inversion Principle (DIP)

    High Level Modules should not depend on Low Level Modules. Both should depend on abstractions

    Abstractions should not depend on details. Details should depend on abstractions


- Benefits:
    - It decouples high-level logic from low-level implementation details.
    - Makes code more modular, easier to test, and reduces dependency.
    - Enables substituting one implementation with another, supporting extensibility and scalability.

##### Before DIP (Tightly Coupled Code)

```
// Low-level module
class UserDatabase {
  save(user) {
    console.log(`Saving user to the database: ${user}`);
  }
}

// High-level module
class UserService {
  constructor() {
    this.database = new UserDatabase(); // Direct dependency on UserDatabase
  }

  saveUser(user) {
    this.database.save(user);
  }
}

// Usage
const userService = new UserService();
userService.saveUser("John Doe");

```

##### Applying DIP (Using Abstractions)

```
// Abstraction
class Database {
  save(user) {
    throw new Error("Method 'save()' must be implemented.");
  }
}

// Low-level module
class UserDatabase extends Database {
  save(user) {
    console.log(`Saving user to the database: ${user}`);
  }
}

// Another low-level module (could be for testing or an alternative storage mechanism)
class InMemoryDatabase extends Database {
  save(user) {
    console.log(`Saving user to in-memory storage: ${user}`);
  }
}

// High-level module
class UserService {
  constructor(database) {
    this.database = database; // Depends on the abstraction, not a specific implementation
  }

  saveUser(user) {
    this.database.save(user);
  }
}

// Usage with UserDatabase
const userService = new UserService(new UserDatabase());
userService.saveUser("John Doe");

// Usage with InMemoryDatabase
const testUserService = new UserService(new InMemoryDatabase());
testUserService.saveUser("Jane Doe");
```

### Dependency Injection

    Dependency Injection (DI) is a design pattern that provides an object’s dependencies from the outside, rather than creating them within the object itself. This promotes loose coupling, easier testing, and better maintainability.

Without DI:

```js
class App {
  constructor() {
    this.dbService = new DatabaseService();
  }
}
```

With DI:

```js
class App {
  constructor(dbService) {
    this.dbService = dbService;
  }
}
```
By injecting dbService into App, the code becomes modular and allows easy swapping of dbService implementations, such as using a mock during testing.


### Inversion Of Control
    Inversion of Control (IoC) is a design principle where the control of objects or portions of a program is transferred from within the component to an external entity. This makes components less dependent on each other and improves flexibility, testability, and modularity.
    Dependency Injection (DI) is one common technique to achieve IoC.






