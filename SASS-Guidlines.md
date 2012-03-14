# General SASS notes, advice and guidelines

**[Follow me on Twitter](http://twitter.com/anotheruiguy) and [tweet these guidelines](https://twitter.com/intent/tweet?text=SCSS+Guidelines+how+to+https://github.com/blackfalcon/SASS-Guidlines).**

## SASS vs SCSS

SASS is the language and SCSS is a syntax. There is no right or wrong, better or worse. I prefer to work with the SCSS syntax as it is easier to read for me. For the purpose of this document I will refer SASS as the language, but code examples will be written as SCSS and file names as .scss. 

## Syntax and formatting

By default SCSS is written using the multi-line format very similure to CSS. You can use single-line, but why? That's just hard to read and the processed CSS will minify your code anyway. Do yourself a favor and make your SCSS easy to read and troubleshoot. 

Always use a trailing semi-colon on the last declaration in a SCSS ruleset to avoid any potential confusion and syntax errors over the life of the document. Good practice, clean code habits.


## Selctor naming conventions

I personally use underscore delimited lowercase selectors. Why? I can double click on a selector and get the whole thing. `.CamelCase{}`, `.hyphen-delimited{}`, or `.underscore_delimited{}`, as long as you are consistent the rock on!

## Working with partials


A partial is a SASS document with an underscore preceding the name.  Example, `_widget.scss`. Using this convention, when processed, SASS will not output a standalone CSS file. A partial is simply a resource file that other docs can consume and use. This is essential for managing large libraries of SASS logic, element and widget styles. 

I have found that the simplest way to manage your SASS files is via a core.scss file consisting of Imported partials and a logical grouping of sub files. With SASS @import works and it works really well, so it is encouraged to break your files into smaller manageable chunks of code. 

SASS and SCSS can live together in perfect harmony. So if you have a reason for using one syntax over another for specific use cases, this is acceptable. For example, some like to use SCSS for logic building and then use SASS for design building. You do not need to state either SCSS or SASS with the @import function, just the path to the partial. 


## Comments

SCSS supports both invisible and visible comments. Using `//` before any SCSS, this will place a comment in your SCSS code, but will not be output in the processed CSS. 

Using the standard `/* */` CSS comments in your SCSS, when processed this will be output in your CSS.  

Comments in code is awesome. Especially when working with a team. Be kind, leave instructions. 

## Indenting

Indenting in SASS is a double edged sword. The indent format allows the developer to inherit the parent selector. But be mindful, it is easy to fall into the trap of over qualified selector inheritance. OOCSS for the win. Rule of thumb, if you are tabbing in a third time, is this style really that specific to this namespace or can you abstract at style to be used more universally? 

It is best practice to list your parent specific styles directly under the class name and then the indented child selectors to keep readability as a maximum.  

Example of a parent class with nested selectors:

	.fieldset {
		margin-bottom: 2em;
		p {
			margin-bottom: 0;
			line-height: 1.5em;		
		}
		legend {
			float: left;
			width: 100%;
		}
	}