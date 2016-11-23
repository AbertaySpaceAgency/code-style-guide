# Abertay Space Society Style Guide


This style guide is a set of guidelines that should be followed when writing
code for Abertay Space Society projects, when it is sensible to do so. The
general rationale behind those guidelines is to make code as readable as
possible.

If you have doubts about how to write a piece of code, go for the solution that
will be the easier to understand to someone else, and be consistent with the
rest of the file and project.

## Naming Conventions

When naming types, classes, variables and functions, always favour readability
over excessive brevity. `stoi()` is much less obvious than `stringToInt()`,
but `class RadioClass` is unecessary (`class Radio` is just as descriptive).

* Variable names should be written in camelCase, starting with a lowercase
  letter.
  	
		// Bad example
		int MyVariable;
		
		// Bad example
		int my_variable;
		
		// Good example
		int myVariable;

* Classes, structs and types names in general should be in CamelCase starting
  with an uppercase letter. Do not add a `_t` suffix at the end of the name,
  those are reserved to the C standard library.
  
		// Bad example
		class myClass { }

		// Bad example
		class my_class { }
		
		// Bad example
		class my_class_t { }

		// Good example
		class myClass { }

* Variable name should contain redundant information about their type (Hungarian
  notation). `Pointer` in `Radio* transmissionModulePointer` is useless since
  the type of the variable is typed out.

* Non-obvious abbreviations should be avoided as much as possible. Widely-used
  ones (`len => length`, `num => number` ...) are accepted but should be avoided
  when space is not an issue.


## Indentation, Spacing and Braces

* Blocks of code should be indented with tabs (4 character wide)..

* The opening brace of a block should appear at the end of the line opening the
  block:
  
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


## Documentation and Comments

## Functions

