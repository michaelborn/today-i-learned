# Write Getter and Setter Functions in Native Javascript

Whoa! You can do [getter][1] and [setter][2] functions in native Javascript? How cool is that!

```js
var Car = {
    get wheels() {
        return this.frontwheels + this.rearwheels;
    },
    set color( color ) {
      this.color = color;
    },
    frontwheels: 2,
    rearwheels: 2,
    color: "black"
};
console.log(Car.wheels); // returns 4
Car.color = "blue";
console.log(Car.color) // returns "blue"
```

Sweet! This is not much different than simply creating an object method, but it is displayed a little different in the FF and Chrome console.

Then the setter method is just as simple:

```js
var Car = {
    set interior( color ) {
      this.color.interior = color;
    },
    set exterior( color ) {
      this.color.exterior = color;
    },
    get interior( ) {
      return this.color.interior;
    },
    get exterior( ) {
      return this.color.exterior;
    },
    color: {
      exterior: "black",
      interior: "black"
    }
};
Car.exterior = "blue";
console.log(Car.exterior) // returns "blue"
```

[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get
[2]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set