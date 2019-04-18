

## ES6 JavaScript

##### _Use ``(back ticks) instead of ""_
```console.log("string 1\n" + "string");```  _ES5_


```console.log(`string
continue in next line with next string or text without the + sign`)```   _ES6_

#####_var is hoisted (var is moved to the top)_ 
//example

```
const name = "whatever";
const day = "whatever";
const instructor = {
    name: "Chris",
    lesson:"ES6",
    greet: function() {
        return `Hello ${this.name} whatever lesson is ${this.lesson}`
    }
}

console.log("Hello my name is"+ " "  +  name  + " "+ "I hope you have a great" +" "+ day); //ES5

console.log(`Hello ${instructor.name} whatever lesson is ${instructor.lesson}`) //ES6

console.log(instructor.greet())
```



_//const also accepts uppercase_ 
_//const's value can not be reassigned unlike let and var_

##### old way...
```function hello(name) {
    name = name || 'Mystery Person';
    console.log("Hello" + name + "!")
}
hello("Bobby");
hello();
```
##### ES6 way ...
```
function hello(name = 'Mystery Person') {
    console.log(`Hello ${name} is it me`)
}
hello("Bobby");
hello();
```

##### Arrow Functions1
```
const teacher = {
    name: "Jimmy",
    speak: function() {
 
        //bind a function to specific context
        let boundFunction = function(){
        console.log('later my name is' + " " +this.name);
        }.bind(this);
        //bound function will always run in bound context
        setTimeout(boundFunction,1000);
    }
};
teacher.speak();
```

##### same thing with Arrowfunction....
```
const teacher = {
    name: "Jimmy",
    speak() {
        //Lexical binding - they bind to scope where they are defined not where they are used
        let boundFunction =() => {
        console.log('later my name is' + " " +this.name);
        };
        
        setTimeout(boundFunction,1000);
    }
};
teacher.speak();

let students = [
    {name: 'Hugo' },
    {name: 'Candace'},
    {name: 'Taylor'}
];
let names = students.map((student) => student.name);
// The ArrowFunction here is same as 
let names = students.map((student) => {
    return student.name
});
console.log(names);
```


##### REST
```
function add() {
    console.log('argument object:', arguments);

    var numbers = Array.prototype.slice.call(arguments);

    var sum = 0;

    numbers.forEach(function(number){
        sum += number;
    });
    return sum;
}
console.log(add(1,2,3,4,5,6,7,8,));
```
##### With ES6
```
let add = (...numbers) => {
    console.log("rest parameters", numbers);

     let sum = 0;
    numbers.forEach(function(number){
        sum += number;
        //or
        let add = (...numbers) => numbers.reduce((sum, number) => sum += number,0);
    
    return sum;
};
console.log(add(1,2,3,4,5,6,7,8,));
```


##### Spread Operator
```
let random = ['hello', 'world', true, 99]
let newArray = [1,2, ...random, 3]
console.log(newArray);
```

##### spreadEx
```
let spreadEx = (item) => {
    let spreadArray = [...item]
    console.log(spreadArray);
    return spreadArray
}
spreadEx('hello world')

//put the above in rest
let restEx = (...z) => {
    console.log(z)
    return z
}
restEx("hello", "world")
```

##### Destructuring Arrays

```
var students = ['julie', 'amy', 'Marie']
var x = students[0];
var y = students[1];

console.log(x,y,z);
other way
let students = ['julie', 'amy', 'Marie'];
let [x,y,z] = students
or
let [x,...rest] = students;
    console.log(x,rest);
console.log(students);
```


```
let completedHomework = ()=> {
    return ['julie',"amy", "marie"];
}
let [x,y,z] = completedHomework();
console.log(x,y,z);

let dessert = ["cake", "creme", "custard"];

function eat(cake, creme) {
 console.log(cake);
}
eat(dessert);
```

##### Object Oriented stuff
##### Constructor function
```
function Person (name, job) {
    this.name = name;
    this.job = job;
}
Person.prototype.getName = function getName() {
    return this.name;
    
}

var goodGuy = new Person ("aang", "Avatar");
console.log(goodGuy.getName())
```
#####//////////////Or
```
class Person {
    constructor(name, job){
        this.name = name;
        this.job = job;
    }
    getName() {
        return this.name;
    }
    getJob() {
        return this.job;
    }
}
let goodGuy = new Person ('Neo', 'the one');
console.log(goodGuy); 
```


#####Setter and Getter
```
class Person {
    constructor(name) {
        this.name = name;
    }
}
let goodGuy = new Person('Jim G');
console.log(goodGuy.name);
goodGuy.name = "James R"
```


#####Map,    Key-Value Pair in the parentheses -->
```
let student = {name:"A-aron"};
let status = new Map();

status.set(student.name, "A-Aron");
status.set("stubborn", "churlish");

console.log(status.get(student.name));
console.log(status.get("feeling"));```
```