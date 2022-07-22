# Client-Side Internet Technologies
## Lecture 1:
Client side programming: Preferred if possible. Eg. Google map, database query
Server side programming: More cost for server, require more internet

### Terms:
HTML: Hypertext Markup Language
HTTP: Hypertext Transport Protocol
  Hypertext: Link text not line by line, but as a graph of reference
  Markup: Add style information for plain text, e.g. “This paragraph needs to be bold and 24pt with times font”
CSS: Cascading style sheet
  HTML and CSS: CSS provide format information, HTML provides skeleton of content (text, table, …)
XML: Extensible Markup Language

HTML is not case sensitive, XML is. (HTML does not care Href, href, or HrEf)
some tags might not have start or end tag, for example, `</br>`, `<br></br>`, `<br>` all works (but it’s better to use `</br>` because it’s XML format)

Tags: A way to tell computer styles. Eg. `<i>Go</i>`
	Some tags have attributes, `<a href = “http://www.stanford.edu”> Stanford</a>`, “href” here is the attribute of “a tag”
	Different tags:
		Inline/ Text-level tags: `<b><b/>` for example, use in line
		Block Level Tags: Create blocks in text, eg. `<p>`, `<h1>`, …, `<h6>`lock tags, some cannot, eg. put a `<h1>` inside a table cell.
			Block Level Tags can have Inline Tags (a `<h1>` title can be Italic), but not vice versa
			Some block level tags can have other b
		File Level/ Structural Tags:

An example of HTML:
```html
<html lang = “en”> The language used in this page
	<head>
		<meta charset = “UTF-8” /> <!--This is the information of which language to use, eg. English not Japnese-->
		<title>New Example</title> <!--This is the text shown in the tag of the page-->
	</head> <!--Head stores some required information that will not be shown on page-->
	<body>
	  …
	</body> <!--Things inside body are all things shown on the page-->
</html>
```

## Lecture 2:
HTML Style validator: validator.w3.org
CSS: Cascading Styling Sheets
HTML Semetics, CSS Presentaitons, their syntax are different a lot because they are in different purposes
Good points for separating HTML and CSS: can keep HTML semetics but change CSS presentations in different time
CSS Selection Decorator Block
```
/*This is CSS comment, cannt use “//“*/
<!--This is an HTML comment-->
```
### Lists
ol: ordered list; ul: unordered list; li: list element(in both ol and ul)
```css
ol li {color:red;} /*means all li inside ol is red*/
ol>li {color:red;} /*means only first layer of ol is red*/
```
### class selector
```html
<style>
	.important {
	  fontColor: red;
	} <!--So that all class of “important” will be in color red-->
	p.important{…} <!--This will only affect important “p” styles-->
</style>
<body>
	<h3 class=“important”>Title</h3>
	<h4 class=“important cal”>Cal</h2> <!--This means in two classes, “important” and “cal”, 
						this is why its called cascading, means multiple layers from top to bottom-->
</body>
```
If we want to change all “stanford” word to red in an HTML, we find all “stanford” and replace to :
```html
<span class=“stanford”>stanford</span>
<!--Then in style, all:-->
span.stanford{color: red}
<!--Span allows us to take a lot of words and change color. We can use as many span as we want-->
<!--Difference between span and div: span is text-level tag, div is block-level tag-->
```
Another important selector is the “id” selector, for example:
```html
<h2 id=“other”>Others</h2>
<!--Then in style:-->
#other {background-color: gray}
<!--id cannot be used for more than 1 tags, unlike class which can be used multiple times-->
```
Style is for CSS, and body is for HTML (content shown on page)
```html
<style></style>
<body></body>
```
### Internal and External CSS
Use CSS inside HTML:
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset=“UTF-8” />
		<title> The Big Game</title>
		<style>
			h1 {color: red;}
		</style>
	</head>
	<body>
		h1 class=“important”>Game</h1> 
	</body>
```
If we want to make the style as an external file, need to: change`<style>` tag to `<link ref = >`, 
then move everyhing inside style (not include `<style>` tag):

```html
<link href=“example.css” rel = “stylesheet” />
<!--“stylesheet” is relationship, “rel” is different than “type”-->
```

One html can use multiple css. If there are conflicts for a same class in different css files, the latest file works
Similarly, one css can be applied to multiple htmls.

For some tag, for example `<h1>`, if we donot want the internal attributes, 
for example border, margin and padding, we can use the reset file:
Just google reset.css (CSS: the missing manual, myweb.com)
	
### CSS Custom Properties:
```css
:root {--my-color: rdb(140, 21,21);}
h1 {background-color: var(--my-color);}
/*--my-color is called custom property, kind of like variable*/
p {width: cal(100% - 4em)} /* cal is for calculation*/
```
Property types in CSS:
Font Properties
Text Properties
Box Properties
Classification Properties
Color and Background

### CSS Anker Property
CSS can even change anker prpperty:
```html
<style>
	a {color: red;
	   text-decoration: none;}
</style>
<body>
	<a href = "">
</body>
```
### Pseudo Element / Class
Act as actual element on webpage but not actually there
```html
<style>
	a:hover {color: red;
	text-decoration: overline underline;}
	p::first-letter {font-size: 1in}
</style>
<body>
	<p>...</p> <!--THis will make only the first letter of paragraph be 1in, 
			but actually there is no specific tag around that first letter, 
			so this is why we call it "Pseudo element". Use double colons-->
	<a href=""/> <!--This is the Pseudo Class example, use single colon-->
</body>
```
### Fragments
a href can ref inpage ids:
```html
<a href="#ttag"/>
<h1 id="ttag"></h1>
```
### Image
img alt: Better to specify how large is this image so that if someone cannot download it they can know
```html
<style>
	#puppy {float: left;}
</style>
<body>
	<img id="puppy" src="puppy,jpg" alt="Molly"/>
</body>
```
### Box
Image Rightmost Pixel <-- Padding --> Border <-- Margin --> Other Blocks
Border must clarify properties: color, width, style
You can control different margins on top, bottom, left, right
### Sprite
Display several images from one download image file, so that we can put lots of icons inside one image (e.g. amazon)

## Lecture 3
### Four Layout Techniques
- Table-based Layout: early magazines, papers. 
	- Has table tag, way to create rows and columns, also tables can be put into tables
	- Issue1: May be very chunky if multi tables inside a table (e.g., left half is whole table, right half has multiple cols&rows)
	- Issue2: Old techniqe, so might be formatting problem if opening in 2022 browser
	- Issue3: We hardwire layout and cannot have different layout for laptop and cellphones (This is the biggest issue)
- Float-based Layout: 2000 to until few years ago
	```html
	<style>
		#puppy {float: left;}
	</style>
	<body>
		<img id="puppy" src="puppy,jpg" alt="Molly"/>
	</body>
	<!-- Puppy will be frozen in page left side, and text will adjust based on page size -->
	```
	- Two `<img>` or `<div>` can float together. For example, if both images are floating left, they will be in a same line if space allowed. (if space not allowed one will be at below another instead of same line, but we wrap those two into a big `<div>` and fix width to keep them moving down when space not allowed)
	- If we donot define float width, the float will automatically take the full page width
	- If things from two different `<div>`s floating together, we can add `clear:both` style on the bottom of the top div, so that there is a `<div>` bar that forbid both left and right side of it to be floated with. (addd `overflow: hidden` in `<div>` can have the same effect)
	- `<div>`s can contain `<div>`s, but when we have irregular grids, the `<div>`s can still be messy, which is why we are in favor of flexbox layout more
- FlexBox Layout
	- FlexBox and Grid-based layout are always used together, larger block use grid and small block use flexbox. You can use flexbox to design a web, but flexbox is not intended or designed to do entire web 
	- Flexbox is like container has lots of items, each item has same weight, we can list those items in row or in columns, depends on different view purpose (laptop or phone). For example:
		- ```
		- #main {
		- display: flex;
		- flex-direction: column;}
		- ```
	- flexbox can be used to adjust alignment, very flexible
	- Flex is designed for small section of website, not entire web (you can but not recommended)
- Grid-Based Layout: Recommended by Professor
	- The specification of grid and felx is on the parent-level, not the children-level
		```html
		<head>
			<style>
				body {display: grid; grid-template-columns: 100px 100px; grid-template-rows: 100px 100px;}
				div {border: 1px splid blue; margin: 2px;}
				#a{grid-column-start: 1; grid-row-start: 1;}
				#b{grid-column-start: 2; grid-row-start: 1;}
				#c{grid-column-start: 1; grid-row-start: 2;}
				#d{grid-column-start: 2; grid-row-start: 2;}
			</style>
		</head>
		<body>
			<div id='a'>Alpha</div>
			<div id='b'>Alpha</div>
			<div id='c'>Alpha</div>
			<div id='d'>Alpha</div>
		</body>
		```
	- What if a grid is crossing multiple rows or columns? 
		- Way1: Using `#a{grid-column-start: 1; grid-column-end: 3;}`(this will make this grid taking `1col*2row` at lefttop corner, not `1*3` but `1*2`)
		- Way2: Using `#a{grid-column-start: 1; grid-row: 1/3;}`
		- Way3: Using `#a{grid-column-start: 1; grid-row: 1 / span 2;}`
	- How to define size of grid?
		- `body {display: grid; grid-template-columns: 100px 100px;}`
		- `body {display: grid; grid-template-columns: 50% 50%;}`
		- `body {display: grid; grid-template-columns: 75px 1fr 2fr;}` There will be three grids in the row, the first is fixed size, the other two are changing based on the page size, and the third one is always two times wider than the second one. "template-column" means the width of the grid
		- `body {display: grid; grid-template-rows: auto 100px auto;}` auto means just enough space to wrap content
	- Overflow: ```body {display: grid; grid-template-columns: 100px 100px; grid-template-rows: 100px 100px;}
		       #a{grid-column-start: 1; grid-row-start: 1; overflow-hidden}``` this overflow hidden will truncate the content more than grid_a's size. Other wise, the content will flow out of grid_a
	


How to determine which techniques to use? Think about who your audience is. (Check `caniuse.com`)
E.g., in developing countries which computer support is not enough, grid-based layout may not suit (~5% of global users)

