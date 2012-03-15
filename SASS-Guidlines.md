# General SASS notes, advice and guidelines

**[Follow me on Twitter](http://twitter.com/anotheruiguy) and [tweet these guidelines](https://twitter.com/intent/tweet?text=SCSS+Guidelines+how+to+https://github.com/blackfalcon/SASS-Guidlines).**

## Syntax and formatting

SASS is written using the multi-line format very similar to CSS. While SASS is the language, SCSS is a version of the syntax. There is no right or wrong, better or worse. Some prefer the SASS syntax, I prefer to work with SCSS. For the purpose of this document I will refer SASS as the language, but code examples will be written as SCSS and file names as ‘.scss‘.  

### SASS v. SCSS

Some key differences to be illustrated are, SASS uses less characters and a 'double space' tab for child selector delineation, exactly like HAML. While SCSS uses a syntax that is more representational of CSS and you can use a full 'tab' for child selector delineation. See examples.

**SASS**

  .your_new_class
    margin: 0
    padding: 0
    
**SCSS**

	.your_new_class {
		margin: 0;
		padding: 0;
	}


### Indenting

Indenting in SASS is not like indenting in CSS. In SASS indenting has meaning. SASS uses the intention white space to declare parent child relationships. Indention allows the developer to inherit the parent selector, but be mindful, it is easy to fall into the trap of insane selector inheritance. Rule of thumb, if you are tabbing in a third time, is this style really that specific to this namespace or can you abstract at style to be used more universally? 

Just because you are using SASS doesn't mean that you should toss all CSS and OOCSS best practices out the window. 

**The Good **

	.your_new_class {
		margin: 0;
		padding: 0;
		p {
			color: red;
		}
		a {
			color: blue;
			text-decoration: none;
		}
		li {
			float: left;
			width: 100%;
		}
	}
	
	
**The Bad**

	.your_new_class {
		margin: 0;
		padding: 0;
		div {
			p {
				color: red:
				a {
					color: blue
					text-decoration: none;
				}
			}
			ul {
				li {
					float: left;
					width: 100%;
					a {
						color: blue;
						text-decoration: none;
					}
				}
			}
		}
	}
	
	
### Style attribute best practice

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


### Selector naming conventions

I personally use underscore delimited lowercase selectors. Why? I can double click on a selector and get the whole thing. `.CamelCase{}`, `.hyphen-delimited{}`, or `.underscore_delimited{}`, as long as you are consistent, rock on!


## Working with partials

A partial in SASS is a document with an underscore preceding the name.  Example, `_widget.scss`. Using this convention, when processed, SASS will not output a standalone CSS file. A partial is simply a resource file that other docs can consume and use. This is essential for managing large libraries of SASS logic, element and widget styles. 

I have found that the simplest way to manage your SASS files is via a core.scss file consisting of Imported partials and a logical grouping of sub files. With SASS @import works and it works really well, unlike standard CSS. It is encouraged to break your files into smaller manageable chunks of code. 

If you can't decide to use either SASS or SCSS, the good news is that you don't. SASS and SCSS files can live together in perfect harmony. So if you have a reason for using one syntax over another for specific use cases, this is acceptable. For example, some like to use SCSS for logic building and then use SASS for design building. You do not need to state either SCSS or SASS with the @import function, just the path to the partial.

## Mixins

Mixins are a great way to keep your code DRY as well as create logical chunks of code to be reused again and again. It is considered best practice to only use a mixin  of you are also using arguments. Simply using a mixin to let the robot copy and paste your styles is not considered a best practice. 

	@mixin the_box ($padding, $background, $border, $style, $color) {
		padding: $padding;
		background: $background;
		border: #{$border}px $style $color;
	}

## @extend

If you are not using arguments in your mixin, you should consider creating this as a CSS class object and apply using the @extend function.  


## Comments

SCSS supports both invisible and visible comments. Using `//` before any SCSS, this will place a comment in your SCSS code, but will not be output in the processed CSS. 

Using the standard `/* */` CSS comments in your SCSS, when processed this will be output in your CSS.  

Comments in code is awesome. Especially when working with a team. Be kind, leave instructions. 