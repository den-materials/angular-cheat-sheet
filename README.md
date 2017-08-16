# angular-cheat-sheet

TypeScript is a superset of of JavaScript that transpiles to vanilla JavaScript

Since TypeScript is a superset of JavaScript, any valid JavaScript is also valid TypeScript

TypeScript was developed by and is maintained by Microsoft

Released in 2012

TypeScript adds optional types, classes, and modules to JavaScript 

        class Person {
            private name: string;
            private age: number;
            private salary: number;

            constructor(name: string, age: number, salary: number) {
                this.name = name;
                this.age = age;
                this.salary = salary;
            }

It is transpiled using the command "tsc"

When transpiles, it makes ES6 features ES5 compatible (which is awesome)

