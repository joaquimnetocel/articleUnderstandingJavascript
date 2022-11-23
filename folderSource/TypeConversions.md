# TYPE CONVERSIONS

MOST OF THE TIME, OPERATORS AND FUNCTIONS AUTOMATICALLY CONVERT THE VALUES GIVEN TO THEM TO THE RIGHT TYPE.

HOWEVER, THERE ARE ALSO CASES WHEN WE NEED TO EXPLICITLY CONVERT A VALUE TO THE EXPECTED TYPE.

## THE `typeof` OPERATOR

BEFORE WE LEARN ABOUT TYPE CONVERSION, LET'S SEE AN OPERATOR THAT RETURNS THE TYPE OF A GIVEN DATA: THE `typeof` OPERATOR. IT'S USEFUL WHEN WE WANT TO PROCESS VALUES OF DIFFERENT TYPES DIFFERENTLY OR JUST WANT TO DO A QUICK CHECK. A CALL TO TYPEOF RETURNS A STRING WITH THE TYPE NAME:

```javascript
typeof undefined // SHOWS "undefined"
typeof 0 // SHOWS "number"
typeof true // SHOWS "boolean"
typeof "foo" // SHOWS "string"
```

## STRING CONVERSION

STRING CONVERSION HAPPENS WHEN WE NEED THE STRING FORM OF A VALUE. WE CAN CALL THE `String` FUNCTION TO CONVERT A VALUE TO A STRING:

```javascript
let value = true;
console.log(typeof value); // SHOWS boolean
value = String(value); // NOW VALUE IS A STRING "true"
console.log(typeof value); // SHOWS string
```

String conversion is mostly obvious. A false becomes "false", null becomes "null", etc.

## NUMERIC CONVERSION

NUMERIC CONVERSION HAPPENS IN MATHEMATICAL FUNCTIONS AND EXPRESSIONS AUTOMATICALLY. FOR EXAMPLE, WHEN DIVISION IS APPLIED TO NON-NUMBERS:

```javascript
console.log("6" / "2"); // SHOWS 3, BECAUSE STRINGS ARE CONVERTED TO NUMBERS
```

We can use the `Number` function to explicitly convert a value to a number:

```javascript
let value = "123";
console.log(typeof value); // SHOWS string
let num = Number(str); // BECOMES A NUMBER 123
console.log(typeof num); // SHOWS number
```

EXPLICIT CONVERSION IS USUALLY REQUIRED WHEN WE READ A VALUE FROM A STRING-BASED SOURCE LIKE A TEXT FORM BUT EXPECT A NUMBER TO BE ENTERED.

IF THE STRING IS NOT A VALID NUMBER, THE RESULT OF SUCH A CONVERSION IS `NaN`. FOR INSTANCE:

```javascript
let age = Number("an arbitrary string instead of a number");
console.log(age); // SHOWS NaN
```

VALUE | BECOMES...
---------|----------
 `undefined` | `NaN`
 `null` | `0`
 `true` | `1`
 `false` | `0`
 string | Whitespaces (includes spaces, tabs \t, newlines \n etc.) from the start and end are removed. If the remaining string is empty, the result is 0. Otherwise, the number is "read" from the string. An error gives NaN.

EXAMPLES:

```javascript
console.log(Number("   123   ")); // SHOWS 123
console.log(Number("123z") ); // SHOWS NaN (error reading a number at "z")
console.log(Number(true)); // SHOWS 1
console.log(Number(false)); // SHOWS 0
```

MOST MATHEMATICAL OPERATORS ALSO PERFORM SUCH CONVERSION, WE'LL SEE THAT IN THE NEXT CHAPTER.

## BOOLEAN CONVERSION

BOOLEAN CONVERSION IS THE SIMPLEST ONE. IT HAPPENS IN LOGICAL OPERATIONS BUT CAN ALSO BE PERFORMED EXPLICITLY WITH A CALL TO `Boolean` FUNCTION.

THE CONVERSION RULE: VALUES THAT ARE INTUITIVELY "EMPTY", LIKE `0`, AN EMPTY STRING, `null`, `undefined`, AND `NaN`, BECOME `false`. OTHER VALUES BECOME `true`. FOR INSTANCE:

```javascript
console.log(Boolean(1)); // SHOWS true
console.log(Boolean(0)); // SHOWS false
console.log(Boolean("hello")); // SHOWS true
console.log(Boolean("")); // SHOWS false
```

PLEASE NOTE: THE STRING WITH ZERO "0" IS `true` SOME LANGUAGES (NAMELY PHP) TREAT "0" AS `false`. BUT IN JAVASCRIPT, A NON-EMPTY STRING IS ALWAYS `true`:

```javascript
console.log(Boolean("0")); // SHOWS true
console.log(Boolean(" ")); // SHOWS true
```
