---
title: JavaScript Style Guide
---

## 1. Linting

Use JSHint to detect errors and potential problems. Every jQuery project has a
Grunt task for linting all JavaScript files: `grunt jshint`. The options for
JSHint are stored in a `.jshintrc` file; many repositories will have multiple
`.jshintrc` files based on the type of code in each directory.

Each `.jshintrc` file follows a specific format. All options must be alphabetized
and grouped:

```json
{
	"common1": true,
	"common2": true,

	"repoSpecific1": true,
	"repoSpecific2": true,

	"globals": {
		"repoGlobal1": true,
		"repoGlobal2": false
	}
}
```

The following common options must be used in all projects:

```json
{
	"boss": true,
	"curly": true,
	"eqeqeq": true,
	"eqnull": true,
	"expr": true,
	"immed": true,
	"noarg": true,
	"onevar": true,
	"quotmark": "double",
	"smarttabs": true,
	"trailing": true,
	"undef": true,
	"unused": true
}
```

##  2. Spacing

- Indentation with tabs.
- No end of line whitespace.
- No blank line whitespace.
- Liberal spacing in code.
- `if`/`else`/`for`/`while`/`try` always have braces and always go on multiple lines.

### Bad Examples

```js

// Bad
if(condition) doSomething();

// Bad
while(condition) iterating++;

// Bad
for(var i=0;i<100;i++) someIterativeFn();

// Bad
object[array[0]];
```

### Good Examples

```js

// Good
if ( condition ) {
	// expressions
}

// Good
while ( condition ) {
	// expressions
}

// Good
var i = 0;

for ( ; i < 100; i++ ) {
	// expressions
}

// Good
var prop;

for ( prop in object ) {
	// expressions
}

// Good
if ( condition ) {
	// expressions
} else {
	// expressions
}

// Good
if ( condition ) {
	// expressions
} else if ( condition ) {
	// expressions
} else {
	// expressions
}

// Good
try {
	// expressions
} catch ( e ) {
	// expressions
}

// Good
try {
	// expressions
} catch ( e ) {
	// expressions
} finally {
	// expressions
}

// Good
object[ array[ 0 ] ];
```


### Arrays and Objects

Empty objects and arrays don't need filler spaces

```js
var object = {},
	array = [];
```



### Function Calls

Always include extra spaces around the arguments:

```js
foo( arg );

foo( "string", object );

foo( options, callback );

foo( node, "property", 2 );
```

Exceptions:

```js
// Empty function calls
foo();

// Functions with callbacks
foo(function() {
	// Note there is no extra space between the first paren
	// of the executing function call and the word "function"
});

// Function accepting an array, no space
foo([ "alpha", "beta" ]);


// Function accepting an object, no space
foo({
	a: "alpha",
	b: "beta"
});
```

## 3. Assignments

Assignments should always have a semicolon after them.

Semicolons should always be followed by a newline.

Assignments in a declaration should always be on their own line. Declarations that don't have an assignment should be listed together at the start of the declaration. For example:

```js
// Bad
var foo = true;
var bar = false;
var a;
var b;
var c;

// Good
var a, b, c,
	foo = true,
	bar = false;
```

## 4. Equality

Strict equality checks (===) should be used in favor of ==. The _only_ exception is when checking for `undefined` and `null` by way of `null`.

```js
// Check for both undefined and null values, for some important reason.
undefOrNull == null;
```

## 5. Type Checks

- String: `typeof object === "string"`
- Number: `typeof object === "number"`
- Boolean: `typeof object === "boolean"`
- Object: `typeof object === "object"`
- Plain Object: `jQuery.isPlainObject( object )`
- Function: `jQuery.isFunction( object )`
- Array: `jQuery.isArray( object )`
- Element: `object.nodeType`
- null: `object === null`
- null or undefined: `object == null`
- undefined:
	- Global Variables: `typeof variable === "undefined"`
	- Local Variables: `variable === undefined`
	- Properties: `object.prop === undefined`


## 6. Comments

Single line comments go OVER the line they refer to:

```js
// We need an explicit "bar", because later in the code foo is checked.
var foo = "bar";
```

For long comments, use:

```js
/*
Four score and seven—pause—minutes ago...
*/
```

Inline comments are allowed as an exception when used to annotate special arguments in formal parameter lists:

```js
function foo( types, selector, data, fn, /*INTERNAL*/ one ) {
	// do stuff.
}
```

## 7. Quotes

jQuery uses double quotes.

```js
var double = "I am wrapped in double quotes";
```

Strings that require inner quoting must use double outside and single inside.

```js
var html = "<div id='my-id'></div>";
```

## 8. DOM Node Rules

`.nodeName` should always be used in favor of `.tagName`.

`.nodeType` should be used to determine the classification of a node (not `.nodeName`).
