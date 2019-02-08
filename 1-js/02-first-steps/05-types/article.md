# Typy danych

Zmienna w JavaScriptcie może przechowywać dowolne dane. W tym momencie może być stringiem, a za chwilę przchowywać wartość liczbową:

```js
// bezbłędne
let message = "hello";
mesage = 123456;
```

Języki programowania, które pozwalają na takie rzeczy nazywane są "dynamicznie typowanymi", co oznacza, że występują typy danych, ale zmienne nie są związane z żadnym z nich.

Jest siedem podstawowych typoów danych w JavaScripcie. Tutaj poznamy podstawy, a w kolejnych rodziałach pomówimy szegółowo o każdym z nich.

## Liczby (number)

```js
let n = 123;
n = 12.345;
```

*Liczbowy* typ danych obsługuje zarówno liczby całkowite, jak i liczby zmiennoprzecinkowe (ułamki).

Jest wiele operacji dla liczb, na przykład mnożenie `*`, dzielenie `/`, dodawanie `+`, odejmowanie `-` i tak dalej.

Poza zwykłymi liczbami, są też tak zwane "specjalne wartości liczbowe", które również należą do tego typu: `Infinity`, `-Infinity` i `NaN`.

- `Infinity` reprezentuje matematyczną [nieskończoność](https://en.wikipedia.org/wiki/Infinity) ∞. Jest to specjalna wartość, która jest większa od jakiejkolwiek liczby.

	Możemy otrzymać ją jako wynik dzielenia przez zerio:

	```js run
	alert( 1 / 0 ); // Infinity
	```

	Lub po prostu wpisując ją bezpośrednio w kodzi:

	```js run
	alert( Infinity ); // Infinity
	```

- `NaN` reprezentuje bład obliczeniowy. Jest wynikiem nieprawidłowej lub niezdefiniowanej operacji matematycznej, na przykład:

	```js run
	alert( "nie liczba" / 2 ); // Nan, takie dzielenie jest błędne
	```

	`NaN` jest "lepkie". Jakakolwiek przyszła operacja na wartości `NaN` zwróci `NaN`:

	```js run
	alert( "nie liczba" / 2 + 5 ); // NaN
	```

	Dlatego też, jeśli `NaN` jest gdzieś w wyrażeniu matematycznym, decyduje o ostatecznym wyniku.

```smart header="Operacje matematyczne są bezpieczne"
Liczenie jest bezpieczne w JavaScripcie. Możemy zrobić cokolwiek: podzielić przez zero, potraktować nieliczbowe ciągi znaków jako liczby, etc.

Skrypt nigdy nie zakończy się fatal errorem ("umrze"). W najgorszym przypadku, jako wynik, dostaniemy `NaN`.
```

Specjalne wartości liczbowe formalnie należą do typu liczbowego. Oczywiście nie są liczbami w powszechnym znaczeniu tego słowa.

Dowiemy się jeszcze o pracowaniu z liczbami w tym rozdziale <info:number>.

## Ciągi znaków (string)

Ciąg znaków muszą być w JavaScripcie cytowane.

```js
let str = "Witaj";
let str2 = 'Apostrofy są też ok';
let phrase = `Można osadzać ${str}`;
```

W JavaScripcie są trzy typy cytowania.

1. Cudzysłów: `"Hello"`.
2. Apostrof: `'Hello'`
3. Backticksy: <code>&#96;Hello&#96;</code>

Cudzysłów i apostrofy są "prostymi" sposobami cytowania. Nie ma różnicy pomiędzy nimi w JavaScripcie.

Backticksy są cytowaniem z "rozszerzoną funkcjonalnością". Pozwalają nam osadzać zmienne i wyrażenia w ciągu znaków poprzez zamykanie ich w `${...}`, na przykład:

```js run
let name = "John";

// osadzanie zmiennej
alert( `Hello, *!*${name}*/!*!` ); // Hello, John!

// osadzenie wyrażenia
alert( `wynikiem jest *!*${1+2}*/!*` ); // wynikiem jest 3
```

Wyrażenie zawarte w `${...}` jest obliczane, a wynik staje się częścią ciągu znaków. Możemy umieścić w tym miejscu cokolwiek: zmienną taką jak `name` lub wyrażenie matematyczne jak `1+2` lub coś bardziej skomplikowanego.

Proszę zwrócić uwagę, że może to być zrobione tylko z wykorzytaniem backticksów. Inne typy cytowania nie pozwalają na takie osadzanie!

```js run
alert( "wynikiem jest ${1 + 2}" ); // wynikiem jest ${1 + 2} (cudzysłów nie działa)
```

Omówimy ciągi znaków bardziej dogłębnie w rodziale <info:string>.

```smart header="Nie ma typu *znakowego*."
W niektórych językach jest specjalny typ znakowy dla pojedynczego znaku. Przykładowo w języku C i w Javie jest nim `char`.

W JavaScripcie nie ma takiego typu. Jest tylko jeden typ: `string`. Ciąg znaków może składać się tylko z jednego znaku lub wielu z nich.
```

## Boolean (typ logiczny)

Typ boolean ma tylko dwie wartości: `true` i `false`.

Typ ten jest powszechnie używany do przechowywania wartości tak/nie: `true` oznacza "tak, poprawne", a `false` oznacza "nie, niepoprawne".

Na przykład:

```js
let nameFieldChecked = true; // tak, pole z nazwą jest zaznaczone
let ageFieldChecked = false; // nie, pole z wiekiem nie jest zaznaczone
```

Wartości boolean powstają również jako wynik porównań:

```js run
let isGreater = 4 > 1;

alert( isGreater ); // true (wartość porówniania to "tak")
```

Poznamy booleany bardziej dogłębnie później, w tym rozdziale <info:logical-operators>.

## Wartość "null"

Wartość specjalna `null` nie należy do żadnego z typów danych opisanych powyżej.

Tworzy on swój własny typ, który zawiera tylko wartość `null`:

```js
let age = null;
```

W JavaScripcie `null` nie jest "referencją do nie istniejącego obiektu" lub "null pointerem (wskaźnikiem do obiektu null)" tak jak w niektórych innych językach.

Jest to po prostu specjalna wartość, która oznacza "nic", "coś pustego", lub "nieznaną wartość".

Kod powyżej stwierdza, że `age` jest nieznana lub pusta z jakiegoś powodu.

## Wartość "undefined"

Specjalna wartość `undefined` wyróżnia się. Tworzy typ sama prez siebie, tak jak `null`.

Znaczenie `undefined` to "wartość nie jest przypisana".

Jeśli zmienna jest zadeklarowana, lecz nie zainicjowana, wtedy jej wartość to dokładnie `undefined`:

```js run
 let x;
 alert(x); // pokazuje "undefined"
```

Technicznie możliwe jest przypisanie `undefined` dowolnej zmiennej:

```js run
let x = 123;

x = undefined;

alert(x); // "undefined"
```

...Nie jest rekomendowane, by tak robić. Normalnie, używamy `null` do zapisania wartości "pustej" lub "nieznanej" w zmiennej, a `undefined` jest używane jedynie do sprawdzenia, czy zmienna jest zainicjowana lub czegoś podobnego.

## Obiekty i symbole

Typ `obiektowy` jest specjalny.

Wszystkie inne typy nazywane są "prostymi", ponieważ ich wartość może zawierać tylko pojedynczą rzecz (może to być ciąg znaków, liczba lub cokolwiek). W przeciwieństwie do nich, obiekty są używane do przechowywania zbiorów danych i bardziej skomplikowanych jednostek. Poradzimy sobie z nimi później, w rodziale <info:object> po tym jak dostatecznie poznamy typy proste.

Typ `symbol` jest używany do tworzenia unikalnych identyfikatorów dla obiektów. Musimy o tym wspomnieć dla kompletności, ale lepiej będzie nauczyć się o nich po obiektach.

## Operator typeof [#type-typeof]

Operator `typeof` zwraca typ przekazanego argumentu. Jest to przydatne, kiedy chcemy przetwarzać wartości różnych typów w inny sposób, lub po prostu chcemy zrobić szybkie sprawdzenie.

Wspiera on dwie formy składni:

1. Jako operator: `typeof x`.
2. Jako funkcja: `typeof(x)`.

Innymi słowy, działa on w obu przypadkach, razem z nawiasami, jak i bez nich. Rezultat jest ten sam.

Wywowałanie `typeof x` zwraca ciąg znaków z nazwą typu.

```js
typeof undefined // "undefined"

typeof 0 // "number"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

*!*
typeof Math // "object"  (1)
*/!*

*!*
typeof null // "object"  (2)
*/!*

*!*
typeof alert // "function"  (3)
*/!*
```

Być może ostatnie trzy linijki potrzebują dodatkowego wyjaśnienia:

1. `Math` jest wbudowanym obiektem, który dostarcza operacji matematycznych. Nauczymy się o nim w rozdziale <info:number>. Tutaj służy on po prostu jako przykład obiektu.
2. Wynikiem `typeof null` jest `"object"`. Jest to błędne, zostało oficjalnie rozpoznane jako błąd w `typeof` i zostawione w celu zachowania kompatybilności. Oczywiście, `null` nie jest obiektem. Jest specjalną wartością z własnym odrębnym typem. Więc, jeszcze raz, to jest bład w języku.
3. Rezultatem `typeof alert` jest `"function"`, ponieważ `alert` jest funckją języka. Poznamy funkcje w kolejnych rozdziałach i zobaczymy, że nie ma specjalnego typu "function" w tym języku. Funkcje należą do typu obiektowego, jednak `typeof` traktuje je inaczej. Formalnie, jest to niepoprawne, lecz bardzo wygodne w praktyce.


## Podsumowanie

Jest 7 podstawowych typów w JavaScripcie.

- `number` dla liczb jakiegokolwiek typu: całkowitych lub zmiennoprzecinkowych
- `string` dla ciągów znaków. Ciąg znaków może mieć jeden lub więcej znaków, nie ma oddzielnego typu dla pojedynczych znaków.
- `boolean` dla `true`/`false` (prawda, fałsz)
- `null` dla wartości nieznanych -- oddzielny typ, który ma pojedynczą wartość, `null`.
- `undefined` dla wartości nieprzypisanych -- oddzielny typ, który ma jedną wartość, `undefined`.
- `object` dla bardziej skomplikowanyh struktur danych.
- `symbol` dla unikalnych identyfikatorów.

Operator `typeof` pozwala nam zobaczyć jaki typ jest przechowywany w zmiennej.

- Dwie formy: `typeof x` lub `typeof(x)`.
- Zwraca ciąg znaków z nazwą typu, jak `"string"`.
- Dla `null` zwraca `"object"` -- jest to błąd w języku, w reczywistości nie jest to obiekt

 W kolejnych rozdziałach skoncentrujemy się na prostych wartościach i kiedy już się z nimi zapoznamy, wtedy przejdziemy do obiektów.