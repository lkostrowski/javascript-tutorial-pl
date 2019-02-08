
Backticks embed the expression inside `${...}` into the string.
Backticksy osadzają wyrażenie zawarte w `${...}` w ciągu znaków.

```js run
let name = "Ilya";

// wyrażenie jest liczbą 1
alert( `hello ${1}` ); // hello 1

// wyrażenie jest ciągiem znaków "name"
alert( `hello ${"name"}` ); // hello name

// wyrażenie jest zmienną, osadź ją
alert( `hello ${name}` ); // hello Ilya
```
