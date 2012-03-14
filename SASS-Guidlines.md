# General SASS notes, advice and guidelines

**[Follow me on Twitter](http://twitter.com/anotheruiguy) and [tweet these guidelines](https://twitter.com/intent/tweet?text=SCSS+Guidelines+how+to+https://github.com/blackfalcon/SASS-Guidlines).**


## SCSS documents

I have found that the simplest way to manage and catalog you SCSS files is via a core.scss file consisting of @imports and a logical grouping of sub files. With SASS @imports work and they work really well, so it is encouraged to break your files into smaller manageable chunks of code. 

You do not want to render all your SASS into CSS files. To keep this from happening name your files with an underscore like '_widget_alpha.scss'. 

### Syntax and formatting

By default SCSS is written using the multi-line format very similure to CSS. You can use single-line, but why? That's just hard to read and the processed CSS will minify your code. Do yourself a favor and make your SCSS easy to read and troubleshoot. 

I personally use underscore delimited lowercase selectors. Why? I can double click on a selector and get the whole thing. '.CamelCase{}', '.hyphen-delimited{}', or '.underscore_delimited{}', as long as you are consistent the rock on!

Always use a trailing semi-colon on the last declaration in a SCSS ruleset to avoid any potential confusion and syntax errors over the life of the document. Good practice, clean code habits. 


## Comments

SCSS supports both invisible and visible comments. Using '//' before any SCSS, this will place a comment in your SCSS code, but not the processed CSS. 

Using the standard '/* */' CSS comments in your SCSS, when processed this will be output in your CSS.  Comments in code is awesome. Especially when working with a team. Be kind, leave instructions. 
