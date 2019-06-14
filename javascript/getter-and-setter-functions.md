# Write Getter and Setter Functions in Native Javascript

Whoa! You can do [getter][1] and [setter][2] functions in native Javascript? How cool is that!

```js
var Car = {
    get wheels() {
        return this.frontwheels + this.rearwheels;
    },
    frontwheels: 2,
    rearwheels: 2
};
console.log(Car.wheels); // returns 4
```

Sweet! This is not much different than simply creating an object method, but it is displayed a little different in the FF and Chrome console.

[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get
[2]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set