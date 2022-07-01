# Client-Side Internet Technologies
## Lecture 1:
Client side programming: Preferred if possible. Eg. Google map, database query
Server side programming: More cost for server, require more internet

Terms:
HTML: Hypertext Markup Language
HTTP: Hypertext Transport Protocol
  Hypertext: Link text not line by line, but as a graph of reference
  Markup: Add style information for plain text, e.g. “This paragraph needs to be bold and 24pt with times font”
CSS: Cascading style sheet
  HTML and CSS: CSS provide format information, HTML provides skeleton of content (text, table, …)
XML: Extensible Markup Language

HTML is not case sensitive, XML is. (HTML does not care Href, href, or HrEf)
some tags might not have start or end tag, for example, </br>, <br></br>, <br> all works (but it’s better to use </br> because it’s XML format)

Tags: A way to tell computer styles. Eg. <i>Go</i>
  Some tags have attributes, <a href = “http://www.stanford.edu”> Stanford</a>, “href” here is the attribute of “a tag”
  Different tags:
    Inline/ Text-level tags: <b><b/> for example, use in line
    Block Level Tags: Create blocks in text, eg. <p>, <h1>, …, <h6>lock tags, some cannot, eg. put a <h1> inside a table cell.
      Block Level Tags can have Inline Tags (a <h1> title can be Italic), but not vice versa
      Some block level tags can have other b
    File Level/ Structural Tags:
An example of HTML:
<html lang = “en”> The language used in this page
<head>
<meta charset = “UTF-8” /> This is the information of which language to use, eg. English not Japnese
<title>New Example</title> This is the text shown in the tag of the page
</head> Head stores some required information that will not be shown on page
<body>
  …
</body> Things inside body are all things shown on the page
</html>

## Lecture 2:
HTML Style validator: validator.w3.org
CSS: Cascading Styling Sheets
HTML Semetics, CSS Presentaitons, their syntax are different a lot because they are in different purposes
Good points for separating HTML and CSS: can keep HTML semetics but change CSS presentations in different time
CSS Selection Decorator Block
ol: ordered list; ul: unordered list; li: list element(in both ol and ul)
```
ol li {color:red;} means all li inside ol is red
ol>li {color:red;} means only first layer of ol is red
```


class selector: 
```
.important {
  fontColor: red;
} // So that all class of “important” will be in color red
<h3 class=“important”>Title</h3>

or
p.important{…} // This will only affect important “p” styles.

<h2 class=“important cal”>Cal</h2> //This means in two classes, “important” and “cal”, this is why its called cascading, means multiple layers from top to bottom
```
```
//If we want to change all “stanford” word to red in an HTML, we find all “stanford” and replace to :
<span class=“stanford”>stanford</span>
//Then in style, all:
span.stanford{color: red}
//Span allows us to take a lot of words and change color. We can use as many span as we want
//Difference between span and div: span is text-level tag, div is block-level tag
```
```
//Another important selector is the “id” selector, for example
<h2 id=“other”>Others</h2>
//Then in style:
#other {background-color: gray}
//id cannot be used for more than 1 tags, unlike class which can be used multiple times
//Different Comments:
/*This is CSS comment, cannt use “//“*/
<! - - This is an HTML comment - ->
```
Use CSS inside HTML:
```
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
  <h1 class=“important”>Game</h1> 
</body>
```
If we want to make the style as an external file, need to: change<style> tag to <link ref = >, then move everyhing inside style (not include <style> tag):
```
<link href=“example.css” rel = “stylesheet” />
// “stylesheet” is relationship, “rel” is different than “type”
```
One html can use multiple css. If there are conflicts for a same class in different css files, the latest file works
Similarly, one css can be applied to multiple htmls.
	
