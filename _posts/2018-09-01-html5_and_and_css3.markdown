---
layout: post
title:      "HTML5 && CSS3"
date:       2018-09-01 18:53:37 +0000
permalink:  html5_and_and_css3
---

HTML stand for Hypertext Markup Languagea and CSS Cascading Style Sheets. HTML provides structure such as  headers, body, paragraph, text, table, listings so on  and CSS visual , layout, colors, fonts, animations, transform, background for  web pages.
## HTML New Features 
The first thing you'll notice document decleration: 
    ``` <!DOCTYPE HTML> ```
		
### Integrated API(Application Programming Interface)
* **Drag and Drop**
* **Audio and Video**
* **Offline Web Applications**
* **Geolocation**
* **History**
* **Local Storage**
* **Web Messaging**

		
### HTML Media Elements
| Feature | Description |
| ------ | ------ |
| ```<audio>``` | Defines sound content |
|```<track>``` | Defines text tracks for media elements (```<video>``` and ```<audio>```) |
| ```<video> ``` | Defines video or movie |
| ```<source>``` | Define nultiple resource for media elemnts|
| ```<embed>``` | Defines a container for an external application |

### HTML5 Graphic Elements
| Feature | Description |
| ------ | ------ |
| ```<canvas>``` | Draw graphics, on the fly, via scripting |
|```<svg>``` | Draw scalabe vector graphics |

### HTML5 Input Types
| Input Types | Input Attributes |
| ------ | ------ |
| color | autocomplete |
| date | autofocus |
| datetime | form |
| datetime-local | formaction |
| email | formenctype |
| month | formmethod |
| number | formvalidate |
| range | formtarget |
| search | height and width |
| tel | list |
| time | min and max |
| url | multiple |
| week | pattern (regexp) |
|  | pattern (regexp) |
|  | placeholder |
|  | required |
|  | step |

### New Structural Elements

| Feature | Description |
| ------ | ------ |
| ```<article>``` | Defines an article in a document |
| ```<aside>``` | Defines content aside from the page content |
| ```<bdi>``` | Isolates a part of text that might be formatted in a different direction from other text outside it |
| ```<header>``` | Defines a header for a document or section |
| ```<footer>``` | Defines a footer for a document or section |
| ```<nav>``` | Defines navigation links |
| ```<progress>``` | Represents the progress of a task |
| ```<meter>``` | Defines a scalar measurement within a known range (a gauge) |
| ```<main>``` | Defines the main content of a document |
| ```<figure>``` | Defines self-contained content |
| ```<figcaption>``` | Defines a caption for a <figure> element |
| ```<details>``` | Defines additional details that the user can view or hide |
| ```<summary>``` | Defines a visible heading for a ```<details>``` element |
| ```<section>``` | Defines a section in a document |
| ```<time>``` | Defines a date/time |
| ```<wbr>``` | Defines a possible line-break |
| ```<rp>``` | Defines what to show in browsers that do not support ruby annotations |
| ```<rt>``` | Defines an explanation/pronunciation of characters (for East Asian typography) |
| ```<ruby>``` | Defines a ruby annotation (for East Asian typography) |
| ```<mark>``` | Defines marked/highlighted text |


## CSS3 New Features
CSS3 is the lastest standard for CSS. CSS3 is completely compatible with earlier CSS versions.

Some of the most significant new features are:
* **Border radius** - allows us to create rounded corners for elements.
* **Border images** - allows us to specify an image as the border around an element.
* **Multiple backgrounds** - applies multiple backgrounds to elements.
* **Animations and effects, and much more!**  
## CSS Vendor Prefixes
CSS vendor prefixes or CSS browser prefixes are a way for browser makers to add support for new CSS features during periods of testing and experimentation. Browser prefixes are used to add new features that may not be part of the final and formal CSS specification. 
Example: 
``` -webkit-border-radius: 24px; ```

| Brwoser | Vendor Prefix |
| ------ | ------ |
| Firefox | -moz- |
| Safari  | -webkit- |
| Chrome | -webkit- |
| Opera | -o- |
| INternet Explorer | -ms |

### The border-radius Property
* You can give any element "rounded corners" by using border-radius property.

**CSS:**
```border-radius: 20px;``` ```background-color:green;```
```color: white;```
* You can specify border radius values for border-radius propert in the following order **top-left**, **top-right**, **bottom-right**, **bottom-left**.
``` border-radius: 0 0 10px 10px;```
* bottom-right and bottom-left corners rounded


### The box-shadow Property: 
The CSS3 box-shadow property applies shadow to the elements.
``` 
div {
   width: 300px;
   height: 100px;
   background-color: #5894f4;
   box-shadow: 10px 10px #1161e0;
}
```
* first length for the horizontal offset
* second length for the vertical offset
* last one for the color

### Blur and Spread:
There are two optional values for the box-shadow element which are blur and spread.
```box-shadow: 10px 10px 5px 5px #6bb0f4;```
* If you want use negative values you can use
### Creating an Innner Shadow:
You can draw inner shadow by using inset keyword

```box-shadow: inset 5px 10px 5px #6bb0f4;```
``` 
box-shadow: 
inset 5px 5px 5px #6bb0f4, 
inset -5px -5px 5px #6bb0f4;
```

## Pseudo-Classes
The CSS pseudo-classes allow us to style elements, or parts of elements, that exist in the document tree without using JavaScript

The most commonly used pseudo-classes are: first-child, last-child, nth-child(even), nth-child(odd), nth-child(number)

**HTML:**
```
<div id="parent">
   <p>First paragraph</p>
   <p>Second paragraph</p>
   <p>Third paragraph</p>
   <p>Fourth paragraph</p>
</div>
```
**CSS3:**
```
#parent p:first-child {
   color: blue;
   text-decoration: underline;   
}
```
**Another example:**
```
#parent p:last-child {
   color: green;
   text-decoration: underline;   
}
```

**Another example:**
```
#parent p:nth-child(even) {
   color: green;
   text-decoration: underline;   
}
```

**Another example:**
```
#parent p:nth-child(odd) {
   color: green;
   text-decoration: underline;   
}
```
**Another example:**
```
#parent p:nth-child(2) {
   color: green;
   text-decoration: underline;   
}
```

## Pseudo Elements:
Pseudo elements are used to select specific parts of an element. There are five pseudo elements.

| Element | Description |
| ----- | ----- |
| **::first-line** | the first line of the text in a selector |
**::first-letter** | the first letter of the text in a selector |
  **::selection** | selects the portion of an element that is selected by a user |
   **::before** | inserts some content before an element |
|**::after** | inserts some content after an element |

**Examples:**
``` 
p::first-line {
   color: #7899;
} 
```
```
p::-moz-selection {
   background: #8bc34a;
   color: #fff;
}
```

```
p::before {
   content: url("me.jpg");
}
```
##  word-wrap Property
The word-wrap property allows long words to be broken and wrapped into the next line. It takes two values: normal and break-word.

**Examples:**
```
p {
   width: 300px; 
   height: 100px;
   border: 1px solid #7899;
   word-wrap: normal;
}
```

```
p {
   width: 300px; 
   height: 100px;
   border: 1px solid #7899;
   word-wrap: break-word;
}
```

## Multiple Backgrounds
With CSS3 there is ability to have multiple background images.
**Examles:**
```
div {
  width: 700px;
  height: 400px;
  background-image: url(logo.png), url(me.jpg);
  background-position: right bottom, left top;
  background-repeat: no-repeat;
}
```

## Transparent Borders:
We will user backgroun-clip property to set borders transparent.

**Examples:**
```
border: 20px solid rgba(0, 0, 0, 0.8);
-webkit-background-clip: padding-box;    
background-clip: padding-box; 
```
## Radial Gradient
To create radial gradient you should define at least two color stops. The radial gradient define d by its(object) center.
**Syntax:**
```
background: radial-gradient(position, shape or size, color-stops);
```
**Examples:**
```
div.radialg {
   height: 250px;
   width: 300px;
   color: #aaa;
   background: -webkit-radial-gradient(green 5%, yellow 15%, blue 60%); 
}
```
## Linear Gradients
CSS3 linear gradient you should define at least two color stops.
**Examples:**

```
div.linearg {
   float: left;
   width: 300px; 
   height: 100px;
   margin: 4px;
   background:-moz-linear-gradient(100deg, orange, red, white);
}
```

**repeating-linear-gradient:**
```
background:-moz-repeating-linear-gradient(blue, black 20px);
```

## Transitions
CSS3 transitions allow us to change from one property value to another over a given duration.

| transiton | Description |
| ----- | ----- |
| **transition-property** | specifies the property to be transitioned |
| **transition-duration** | specifies the duration over which transitions should occur |
| **transition-timing-function** |  specifies how the pace of the transition changes over |
| **transition-delay** | specifies a delay (in seconds) for the transition effect |

**Examples:**
```transition: transform 5s ease-in;```

### transition-timing-function
The transition-timing-function property specifies the speed curve of the transition effect. It can have the following values:
| transiton-timing | Description |
| ----- | ----- |
| **ease** | the animation starts slowly, then accelerates quickly |
| **ease-in** | starts slowly, then accelerates, and stops abruptly |
| **ease-out** | starts quickly, but decelerates to a stop |
| **ease-in-out** |similar to ease, but with more subtle acceleration and deceleration |
| **linear** |constant speed throughout the animation; often best for color or opacity change |
**Example:**
``` transition-timing-function: cubic-bezier(0,0,1,1); ```

### Transform
CSS3 transforms allow you to translate, rotate, scale, skew elements. You can rotate objects **clockwise** and **counter-clockwise**

**Example:**
```
.positive {
   width: 300px;
   height: 150px;
   margin-top: 30px;
   background-color: #7899;
   transform: rotate(30deg);
}
.negative {
   width: 300px;
   height: 150px;
   margin-top: 30px;
   background-color: #7899;
   transform: rotate(-30deg);
}
```

// **created_by** @rahymov





