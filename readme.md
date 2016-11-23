# Abertay Space Society Style Guide


This style guide is a set of guidelines that should be followed when writing
code for Abertay Space Society projects, when it is sensible to do so. The
general rationale behind those guidelines is to make code as readable as
possible.

If you have doubts about how to write a piece of code, go for the solution that
will be the easier to understand to someone else, and be consistent with the
rest of the file and project.

## 1. Naming Conventions

When naming types, classes, variables and functions, always favour readability
over excessive brevity. `stoi()` is much less obvious than `stringToInt()`,
but `class RadioClass` is unnecessary (`class Radio` is just as descriptive).

1. Variable names should be written in camelCase, starting with a lowercase
   letter.

	````cpp
	// Bad example
	int MyVariable;

	// Bad example
	int my_variable;

	// Good example
	int myVariable;
	````

2. Classes, structs and types names in general should be in CamelCase starting
   with an uppercase letter. Do not add a `_t` suffix at the end of the name,
   those are reserved to the C standard library.
  
	````cpp
	// Bad example
	class myClass { }

	// Bad example
	class my_class { }

	// Bad example
	class my_class_t { }

	// Good example
	class MyClass { }
	````

3. In C, all structures (`struct`) should be typedef-ed: `foo(MyStruct* param)`
   is shorter and more readable than `foo(struct MyStruct* param)`. This also
   allows better interaction with C++.
	
	````c
	// Bad example
	struct RadioPacket {
		int		id;
		char	contents[512];
	};
	
	// Good example
	typedef struct RadioPacket {
		int		id;
		char	contents[512];
	} RadioPacket;
	````
	

4. Variable names should not contain redundant information about their type
   (Hungarian notation). `Pointer` in `Radio* transmissionModulePointer` is
   useless since the type of the variable is typed out.

5. Non-obvious abbreviations should be avoided as much as possible. Widely-used
   ones (`len => length`, `num => number` ...) are accepted but should be
   avoided when space is not an issue.


## 2. Indentation, Spacing and Braces

1. Blocks of code should be indented with tabs (4 character wide)..

2. The opening brace of a block should appear at the end of the line opening the
   block:
  
	````cpp
	// Bad example
	void badlyBracedFunction(int arg)
	{
		doSomething();
	}

	// Bad example
	void anotherBadFunction(int arg)
		{
			doSomething();
		}

	// Good example
	void goodExample(int arg) {
		doSomething();
	}
	````

## 3. Structure

1. Short, single-purpose functions should always be preferred over monolithic
   ones. Single-purpose functions are more modular and easier to combine to
   obtain different behaviours.

2. Global variables should be avoided as much as possible. They make it harder
   to understand program behaviour, and lead to conflicts between functions and
   threading problems.

3. When possible, *pure functions* should be preferred. A pure function is a
   function whose output depends solely on its parameters, and which does not
   read or write any global variable. Pure functions make it easier to predict
   the outcome of a program and write unit tests.
  
	````cpp 		
	int currentCount = 0;

	// Not a pure function, depends on global [currentCount]
	int newCount(int number) {
		currentCount += number;
		number;
	}

	// Pure function
	int newCount(int currentCount, int number) {
		return currentCount + number;
	}
	````

## 4. Documentation and Comments

1. Each function should have a brief, 1/2-line description comment. If you
   follow the guidelines from §3, it should be enough to explain what the
   function does.
  
   If the function relies on some non-trivial behaviour or algorithm, it should
   be explained in a paragraph below the brief description.
  
	````cpp	
	// Prints a character to the console
	void print(const char* string) {
		...
	}


	// Shortly, *what* the function does
	//
	// Less shortly, *how* it does it, if an explanation is necessary.
	// Some more explaining. And then some.
	void someComplexProcessingFunction(int array[], size_t length) {
		...
	}
	````

2. Limit comments inside a function's body to things that are not obvious. If
   the naming and structure guidelines in §2 et §3 are followed, few comments
   are necessary inside functions.
  
	````cpp  		
	// Bad example:
	int userID; // int to store the userID
	````

3. The top of each file should have a comment header that specifies the project
   the file is part of, the purpose of the functions declared in the file and
   the users that have worked on the file (in format `name/username <email>`):

	````cpp  
	//
	// FlightSoftware-Core
	// radio_transmit.c - functions used to send data through radio
	//
	// [longer description if required]
	//
	// authors:		Jane Doe <janedoe@foo.bar>
	//				John Doe <john123@bar.foo>
	//

	...
	````

