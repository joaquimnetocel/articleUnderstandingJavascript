# FUNCTIONS

QUITE OFTEN WE NEED TO PERFORM A SIMILAR ACTION IN MANY PLACES OF THE SCRIPT. FUNCTIONS ARE THE MAIN “BUILDING BLOCKS” OF THE PROGRAM. THEY ALLOW THE CODE TO BE CALLED MANY TIMES WITHOUT REPETITION.

## FUNCTION DECLARATION

TO CREATE A FUNCTION WE CAN USE A FUNCTION DECLARATION. IT LOOKS LIKE THIS:

```javascript
// FUNCTION DEFINITION
function functionSayHello(){
    const stringName = "JOHN";
    console.log("HELLO " + stringName);
};
/////
// FUNCTION EXECUTION
functionSayHello(); // SHOWS: HELLO JOHN
functionSayHello(); // SHOWS: HELLO JOHN
functionSayHello(); // SHOWS: HELLO JOHN
/////
```

THE CALL `functionSayHello()` EXECUTES THE CODE OF THE FUNCTION. THIS EXAMPLE CLEARLY DEMONSTRATES ONE OF THE MAIN PURPOSES OF FUNCTIONS: TO AVOID CODE DUPLICATION.

## PARAMETERS

FUNCTIONS CAN ALSO DEPEND ON PARAMETERS THAT CAN ASSUME DIFFERENT VALUES WHEN THE FUNCTION IS EXECUTED. IN THE EXAMPLE BELOW, THE FUNCTION HAS TWO PARAMETERS: `parSize` AND `parColor`.

```javascript
// FUNCTION DEFINITION
function functionSaySomethingAboutTheHouse(parSize, parColor){
    console.log(`THE HOUSE IS ${parSize} AND ${parColor}.`);
};
/////
// FUNCTION EXECUTIONS
functionSaySomethingAboutTheHouse("SMALL", "GREEN"); // SHOWS: THE HOUSE IS SMALL AND GREEN.
functionSaySomethingAboutTheHouse("BIG", "WHITE"); // SHOWS: THE HOUSE IS BIG AND WHITE.
functionSaySomethingAboutTheHouse("SMALL", "RED"); // SHOWS: THE HOUSE IS SMALL AND RED.
/////
```

## ARGUMENTS

WHEN A VALUE IS PASSED AS A FUNCTION PARAMETER, IT’S ALSO CALLED AN ARGUMENT. IN OTHER WORDS, TO PUT THESE TERMS STRAIGHT:

* A PARAMETER IS THE VARIABLE LISTED INSIDE THE PARENTHESES IN THE FUNCTION DECLARATION (IT’S A DECLARATION TIME TERM).
* AN ARGUMENT IS THE VALUE THAT IS PASSED TO THE FUNCTION WHEN IT IS CALLED (IT'S A CALL TIME TERM).

WE DECLARE FUNCTIONS LISTING THEIR PARAMETERS, THEN CALL THEM PASSING ARGUMENTS.

IN THE EXAMPLE ABOVE, ONE MIGHT SAY THAT THE FUNCTION IS DECLARED WITH TWO PARAMETERS `parSize` AND `parColor`, THEN CALLED WITH THE ARGUMENTS: "SMALL", "GREEN", "BIG", "WHITE" AND "RED".

## DEFAULT VALUES

IF A FUNCTION IS CALLED, BUT AN ARGUMENT IS NOT PROVIDED, THEN THE CORRESPONDING VALUE BECOMES `undefined`. FOR INSTANCE, THE AFOREMENTIONED FUNCTION `functionSaySomethingAboutTheHouse(parSize, parColor)` CAN BE CALLED WITH A SINGLE ARGUMENT:

```javascript
// FUNCTION DEFINITION
function functionSaySomethingAboutTheHouse(parSize, parColor){
    console.log(`THE HOUSE IS ${parSize} AND ${parColor}.`);
};
/////
// FUNCTION EXECUTION
functionSaySomethingAboutTheHouse("BIG"); // SHOWS: THE HOUSE IS BIG AND undefined.
/////
```

WE CAN SPECIFY THE SO-CALLED "DEFAULT" (TO USE IF OMITTED) VALUE FOR A PARAMETER IN THE FUNCTION DECLARATION:

```javascript
// FUNCTION DEFINITION
function functionSaySomethingAboutTheHouse(parSize="HUGE", parColor="WHITE"){
    console.log(`THE HOUSE IS ${parSize} AND ${parColor}.`);
};
/////
// FUNCTION EXECUTION
functionSaySomethingAboutTheHouse("SMALL"); // SHOWS: THE HOUSE IS SMALL AND WHITE.
/////
```

THE DEFAULT VALUE ALSO JUMPS IN IF THE PARAMETER EXISTS, BUT STRICTLY EQUALS UNDEFINED, LIKE THIS:

```javascript
// FUNCTION EXECUTION
functionSaySomethingAboutTheHouse(undefined, "RED"); // SHOWS: THE HOUSE IS HUGE AND RED.
/////
```

## RETURN

A FUNCTION CAN RETURN A VALUE BACK INTO THE CALLING CODE AS THE RESULT. THE SIMPLEST EXAMPLE WOULD BE A FUNCTION THAT SUMS TWO VALUES:

```javascript
function functionSum(parNumber1, parNumber2){
    return parNumber1 + parNumber2;
};
const numberResult = functionSum(2,4);
console.log(numberResult); // SHOWS: 6.
```

THE DIRECTIVE RETURN CAN BE IN ANY PLACE OF THE FUNCTION. WHEN THE EXECUTION REACHES IT, THE FUNCTION STOPS, AND THE VALUE IS RETURNED TO THE CALLING CODE (ASSIGNED TO RESULT ABOVE).

THERE MAY BE MANY OCCURRENCES OF RETURN IN A SINGLE FUNCTION. FOR INSTANCE:

```javascript
function functionIsExpensive(parPrice) {
    if (parPrice > 100) {
        return true;
    } 
    return false;
}

const numberPrice = 80;

if ( functionIsExpensive(numberPrice) ) {
    console.log("NO, THANKS!"); // THIS LINE IS NOT EXECUTTED.
} else {
    console.log("GREAT! I WILL BUY."); // SHOWS: GREAT! I WILL BUY.
}
```

## NO RETURNS

A FUNCTION WITH AN EMPTY RETURN OR WITHOUT IT RETURNS `undefined`. IN OTHER WORDS, IF A FUNCTION DOES NOT RETURN A VALUE, IT IS THE SAME AS IF IT RETURNS `undefined`:

```javascript
function functionDoNothing() {}
console.log( functionDoNothing() ); // SHOWS: undefined
```

AN EMPTY RETURN IS ALSO THE SAME AS RETURN `undefined`:

```javascript
function functionDoNothing() {
    return;
}
console.log( functionDoNothing() ); // SHOWS: undefined
```

## LOCAL VARIABLES

A VARIABLE DECLARED INSIDE A FUNCTION IS ONLY VISIBLE INSIDE THAT FUNCTION. FOR EXAMPLE:

```javascript
// FUNCTION DEFINITION
function functionShowMessage() {
    const stringMessage = "HELLO!"; // LOCAL VARIABLE
    console.log(stringMessage);
}
// FUNCTION EXECUTION
functionShowMessage(); // SHOWS: HELLO!
/////
console.log(stringMessage); // ERROR: THE VARIABLE I LOCAL TO THE FUNCTION.
```

## OUTER VARIABLES

A FUNCTION CAN ACCESS AN OUTER VARIABLE AS WELL, FOR EXAMPLE:

```javascript
let stringName = "JOHN";

function functionShowMessage() {
    let stringMessage = "HELLO " + stringName;
    console.log(stringMessage);
}
functionShowMessage(); // SHOWS: HELLO JOHN
```

THE FUNCTION HAS FULL ACCESS TO THE OUTER VARIABLE. IT CAN MODIFY IT AS WELL. FOR INSTANCE:

```javascript
let stringName = "JOHN";

function functionShowMessage() {
    stringName = "BOB"; // CHANGED THE OUTER VARIABLE.
    console.log("HELLO " + stringName);
}

console.log(stringName); // SHOWS: JOHN
functionShowMessage(); // SHOWS: HELLO BOB
console.log(stringName); // SHOWS: BOB
```

THE OUTER VARIABLE IS ONLY USED IF THERE'S NO LOCAL ONE. IF A SAME-NAMED VARIABLE IS DECLARED INSIDE THE FUNCTION THEN IT SHADOWS THE OUTER ONE. FOR INSTANCE, IN THE CODE BELOW THE FUNCTION USES THE LOCAL stringNAME. THE OUTER ONE IS IGNORED:

```javascript
let stringName = "JOHN"; // GLOBAL VARIABLE

function functionShowMessage() {
    let stringName = "BOB"; // LOCAL VARIABLE
    console.log("HELLO " + stringName); // SHOWS: HELLO BOB
}

functionShowMessage(); // THE FUNCTION WILL CREATE AND USE ITS OWN stringName.

console.log(stringName); // SHOWS JOHN, UNCHANGED, THE FUNCTION DID NOT ACCESS THE OUTER VARIABLE.
```

VARIABLES DEFINED OUTSIDE OF FUNCTIONS ARE CALLED **GLOBAL**. IT'S A GOOD PRACTICE TO MINIMIZE THE USE OF GLOBAL VARIABLES. MODERN CODE HAS FEW OR NO GLOBALS. MOST VARIABLES RESIDE IN THEIR FUNCTIONS.

## FUNCTION EXPRESSION

```javascript
const functionSayHello = function(){
    console.log("HELLO!");
    console.log("HOW ARE YOU?");
    console.log("AS YOU CAN SEE, INSIDE A FUNCTION WE CAN DO A LOT OF THINGS.");
};
functionSayHello();
```

## ARROW FUNCTION

```javascript
const functionSquare = (argNumber)=>{
    return argNumber * argNumber;
};
console.log( functionSquare(3) ); // 9
console.log( functionSquare(4) ); // 16
```

```javascript
const functionSquare = argNumber => argNumber * argNumber;
console.log( functionSquare(3) ); // 9
console.log( functionSquare(4) ); // 16
```
