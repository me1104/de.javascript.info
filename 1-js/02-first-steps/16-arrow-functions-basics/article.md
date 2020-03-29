# Pfeilfunktionen, die Grundlagen

Es gibt eine kurze und einfache Syntax für das Erstellen von Funktionen, die oftmals besser als Funktionsausdrücke sind.

Sie werden Pfeilfunktionen genannt weil sie so aussehen:

```js
let func = (arg1, arg2, ...argN) => expression
```

...Das erzeugt eine Funktion `func` die, die Argumente `arg1..argN` akzeptiert. Danach wird der Ausdruck `expression` auf
der rechten Seite ausgewertet und das Ergebnis zurückgegeben.

In anderen Worten: es ist die kurze Version von:

```js
let func = function(arg1, arg2, ...argN) {
  return expression;
};
```

Sehen wir uns ein Beispiel an:

```js run
let sum = (a, b) => a + b;

/* Diese Pfeilfunktion ist die kurze Form von:

let sum = function(a, b) {
  return a + b;
};
*/

alert( sum(1, 2) ); // 3
```

Wie zu sehen ist, hat `(a, b) => a + b` die Bedeutung einer Funktion, die 2 Parameter akzeptiert `a` und `b`. Bei der Ausführung, wird
der Ausdruck `a + b` aufgewertet und das Ergebnis zurückgegeben.

- Wenn es nur ein Argument gibt, können die Klammern um den Parameter entfallen, welches den Audruck weiter verkürzt.

    Zum Beispiel:

    ```js run
    *!*
    let double = n => n * 2;
    // ungefähr das Gleiche wie: let double = function(n) { return n * 2 }
    */!*

    alert( double(3) ); // 6
    ```

- Wenn es kein Argument gibt, ist die Klammer leer (sollte aber vorhanden sein):

    ```js run
    let sayHi = () => alert("Hallo!");

    sayHi();
    ```

Pfeilfunktionen können in derselben Weise genutzt werden wie Funktionsausdrücke.

Zum Beispiel, um dynamisch Funktionen zu erzeugen:

```js run
let age = prompt("Wie alt bist Du?", 18);

let welcome = (age < 18) ?
  () => alert('Hallo') :
  () => alert("Grüße!");

welcome(); // jetzt so aufrufbar 
```

Arrow functions may appear unfamiliar and not very readable at first, but that quickly changes as the eyes get used to the structure.

They are very convenient for simple one-line actions, when we're just too lazy to write many words.

## Multiline arrow functions

The examples above took arguments from the left of `=>` and evaluated the right-side expression with them.

Sometimes we need something a little bit more complex, like multiple expressions or statements. It is also possible, but we should enclose them in curly braces. Then use a normal `return` within them.

Like this:

```js run
let sum = (a, b) => {  // the curly brace opens a multiline function
  let result = a + b;
*!*
  return result; // if we use curly braces, then we need an explicit "return" 
*/!*
};

alert( sum(1, 2) ); // 3
```

```smart header="More to come"
Here we praised arrow functions for brevity. But that's not all!

Arrow functions have other interesting features.

To study them in-depth, we first need to get to know some other aspects of JavaScript, so we'll return to arrow functions later in the chapter <info:arrow-functions>.

For now, we can already use arrow functions for one-line actions and callbacks.
```

## Summary

Arrow functions are handy for one-liners. They come in two flavors:

1. Without curly braces: `(...args) => expression` -- the right side is an expression: the function evaluates it and returns the result.
2. With curly braces: `(...args) => { body }` -- brackets allow us to write multiple statements inside the function, but we need an explicit `return` to return something.
