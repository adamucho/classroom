![](http://c2journal.com/wp-content/uploads/2014/07/css3-markup.jpg)
# CSS - Basics

Learning Objectives

- Add Styles to a Web Page
- Use Basic Selectors to Target Elements for Styling
- Write Basic CSS Rules

## Roadmap
1. Intro to Cascading Style Sheets
2. CSS Properties
3. Adding Styles to a Web Page
4. CSS Selectors
5. Further Study

### 1. Intro to Cascading Style Sheets

#### What is CSS?

CSS is a web technology used to format HTML documents. With the advent of CSS3, CSS can also provide some stylistic behaviors using CSS animations.

CSS enables us to separate the structure & content (HTML) of a document from its presentation.  This concept of *separation of concerns* is widespread throughout software development because it helps make programs more maintainable and provides better code reuse.

Like most skills related to development, your CSS chops will continually develop over time with each front-end project you're involved with.

#### Basic CSS Syntax

The following graphic shows the basic syntax of a CSS rule:

![](http://learnwebcode.com/wp-content/uploads/2010/02/anatomy-of-a-css-rule.gif)

Let's discuss the individual components above:

- **Selectors**:
    - Used to target the element(s) to be styled.
    - Can range from simple to complex.
    - Multiple selectors can be separated with commas.
- **Properties**:
    - There are over two hundred CSS properties that can be used to style the color, size, text, position, border, animation, etc. of elements.
- **Value**:
    - The value to apply to a property is, of course, specific to that property. For example, the CSS property, _font-family_, accepts values of names of fonts such as _Georgia_, _Arial_, etc. Other properties may have numeric values along with a type of unit assigned to them, for example, you might set the width of a border to _5px_.
- **Declaration**:
    - The combination of a _property_ and _value_, separated by a colon and ending with a semi-color, makes a _declaration_.

### 2. CSS Properties

#### Basic Properties

We're going to pair up and research CSS Properties. Take 5 minutes to read through the linked document. Be prapred to answer 

- What the property styles (usually obvious thanks to logical naming)
- Some of the values that can be applied to the property.

- Color - https://developer.mozilla.org/en-US/docs/Web/CSS/color
- Borders - https://developer.mozilla.org/en-US/docs/Web/CSS/border
- Margin - https://developer.mozilla.org/en-US/docs/Web/CSS/margin
- Padding - https://developer.mozilla.org/en-US/docs/Web/CSS/padding
- Background - https://developer.mozilla.org/en-US/docs/Web/CSS/background
- Text Decoration - https://developer.mozilla.org/en-US/docs/Web/CSS/Text-Decoration
- Font - https://developer.mozilla.org/en-US/docs/Web/CSS/font
- Transform - https://developer.mozilla.org/en-US/docs/Web/CSS/Transform
- Transition - https://developer.mozilla.org/en-US/docs/Web/CSS/transition

#### Shorthand Properties

Shorthand properties are CSS properties that let you set the values of several CSS properties simultaneously.
   
Using a shorthand property, a web developer can write more concise and often more readable CSS.
  
A shorthand property groups properties of a common theme.  Here are some examples:

##### font
  
```css
p {
   font-style: italic;
   font-weight: bold;
   font-size: 12px;
   line-height: 14px;
   font-family: Helvetica;
}
```

The five lines of CSS declarations above can be merged into a single declaration as follows:

```css
p {
   font: italic bold 12px/14px Helvetica;
}
```

##### margin
  
```css
div {
   margin-top: 10px;
   margin-right: 5px;
   margin-bottom: 15px;
   margin-left: 25px;
}
```

The four lines of CSS declarations above can be merged into a single declaration as follows:
  
```css
div {
   margin: 10px 5px 15px 25px;
}
```
   
The above `margin` example specifies margins for all four sides (top, right, bottom & left - in that order).

A good word to help remember the order of these values is **TR**ou**BL**e (top-right-bottom-left).
   
[This documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties) explains all about shorthand properties.

### 3. Adding Styles to a Web Page

#### Setup

Before we can add styles to a web page, we're going to need one to style!

In Terminal (don't type the `$`):

```
$ mkdir intro-to-css
$ cd intro-to-css
$ touch index.html
$ subl .
```

Now let's add some HTML to `index.html`.  Depending upon the packages you have installed in Sublime Text, you may be able to just type `!` followed by `[tab]` to insert the HTML boilerplate:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <h1>WDI Rocks!</h1>
</body>
</html>
```

With our boilerplate in place, let's check it out in the browser by right-clicking in the editor and selecting _Open in Browser_ or by typing _open index.html_ in terminal.

#### Three Ways to Add Styles

There are three ways to add styling to a web page:

  - Inline Styles
  - Internal Stylesheets
  - External Stylesheets

These three techniques are not mutually exclusive, you can use one or more of them in the same webpage.

##### Inline Styles

An **inline style** can be used to apply style to a single element using the `style` attribute.

The use of inline styles breaks our separation of concerns by mixing content with presentation, therefore avoid using this technique unless there's a good reason to do so, for example, when testing or debugging styles.

>Note: Several JS libraries and frameworks such as _AngularJS_ add inline styles dynamically to perform their magic. _ReactJS_ actually encourages the use of inline styling when defining _ReactJS_ components. However, as developers, we will rarely use inline styling for our application's CSS.

To demonstrate inline styling, let's use it to change the color of the  background and font:

```html
<body style="background-color: #eedd8e; color: darkblue">
``` 

Above we have used both a "[named color](http://www.w3schools.com/cssref/css_colornames.asp)" and a RGB hex value. There's a link in the References section if you want to learn more about colors in CSS.

Save and refresh - bam!

##### Internal Stylesheet

The second of the three techniques we can use is **internal stylesheets**.

An **internal stylesheet** can be created by using a `<style>` element nested within the document's `<head>` element:

```html
<head>
  <meta charset="UTF-8">
  <title>CSS Basics</title>
  <!-- inline stylesheet -->
  <style>
    h1 {
      text-align: center;
    }
  </style>
</head>
```

Now the text within our `<h1>` will be centered!

Although an improvement over using inline styling, inline stylesheets are also not the preferred method to add styles to your web page. However, they can be handy for quick styling - like we might do during a lesson :)

##### External Stylesheets

The last of the three techniques available to add styling is **external stylesheets**.

Styling a page using **external stylesheets** is considered a best practice because it provides the best separation of concerns, reusability and maintainability.

External stylesheets are separate files with a `.css` extension and are "linked" to the document using the `<link>` element.

First, let's create our stylesheet inside of a new `css` folder:

```
$ mkdir css
$ touch css/style.css
```

Now we can link in the `style.css` external stylesheet like this:

```html
<head>
  <meta charset="UTF-8">
  <title>CSS Basics</title>
  <style>
    h1 {
      text-align: center;
    }
  </style>
  <!-- bring in an external stylesheet -->
  <link rel="stylesheet" href="css/style.css">
</head>
```

>Note that the *href* path in this case is relative to **index.html**.  
     
Let's add a css rule inside our new `style.css` file to test it out:

```css
body {
  font-family: "Lucida Grande";
}
```
Save & refresh - cool!

#### Load Order Matters

Often, you will need to include multiple CSS stylesheets in your web page. For example, you will often want to load the CSS file of a third-party CSS framework and include your own custom CSS file as well.

When multiple stylesheets exist, the load order matters if they define the same CSS rule.

To see this in action, let's purposely create a conflict between an internal and external stylesheet.

Update `style.css` as follows:

```css
/* style.css (external stylesheet) */

body {
  font-family: "Lucida Grande";
  background-color: red;  /* conflicts with earlier inline-styling */
}

h1 {
  text-align: right;  /* conflicts with the internal stylesheet */
}
```
Save, refresh and answer the following:

**? - When there's a conflict between an internal and/or external stylesheets conflict, who wins?**

**? - Who wins between stylesheets and inline styling?**

**? - What are the three methods to add styles to a HTML document?**

**? - Which method is considered a best practice and why?** 

### 4. CSS Selectors

As shown earlier, the **CSS Selector** portion of a CSS rule, targets an element, or elements, to be styled by CSS _property:value_ declarations.

#### Setup

To practice with CSS selectors, copy & paste this additional HTML inside of the `<body>` below our existing `<h1>`:

```html
  <p>This is a paragraph element</p>

  <div>This is a DIV</div>
  <div class="crazy">This is another DIV</div>
  <div class="crazy super-cool">
    <p>This is a paragraph inside of the third DIV</p>
  </div>

  <p id="comments-title">Comments</p>
  <ul>
    <li>Comment One</li>
    <li class="super-cool">Comment Two</li>
    <li>Comment Three</li>
  </ul>
```

Next, let's rid ourselves of that inline stylesheet and inline style on the `<body>`.

Lastly, let's update `style.css` to start with the following:

```css
body {
  font-family: "Lucida Grande";
}

h1 {
  text-align: center;
}
```

Now it's time to learn about the different types of CSS selectors...


#### Basic Selectors

##### *element* Selector

This is how we could select all `<h1>` and `<h2>` tags:

```css
h1, h2 { ... }
```

**PRACTICE:<br>- Set the margin on the `<body>` element to 15 pixels on all four sides<br>- Set the text color of all `<div>` elements to blue.**

##### *ID* Selector

We select an element that matches the value of an `id` attribute by prefixing it with `#`:

```css
#id-name { ... }
```

>Note: **id**'s on elements should always be unique.

**PRACTICE:<br>- Set the size of the font to 28px on the `<p>` element with an `id="comments-title"`**

##### *class* Selector

Selects elements that match one of the values of the *class* attribute - yes, the *class* attribute accepts multiple space separated values!

To target elements with a given class, or classes, we prefix the name of the class with a period:

```css
.my-class { ... }  /* Target all elements having the class of "my-class" */
span.my-class { ... }  /* Target all <span class="my-class"> elements */
li.item.special { ... }  /* Target all <li class="item special"> elements */
```

**PRACTICE:<br>- Set the border of the `<li>` with a class of `super-cool` to be solid, 2px in width and red in color.**

##### *attribute* Selector

Selects elements based upon its attributes.

Less common, but if you come across square brackets in a selector, you'll know what they are for!

```css
[style] { ... }  /* Matches elements that have a 'style' attribute */
a[href="#about"] { ... }  /* Targets anchor tags with an 'href' set to "#about" */
```

#### Combinators

Combinators provide a powerful way to select elements based upon their relationship to other elements.

The most common combinator is the **descendant selector**.

We use the _descendant selector_ to target elements **nested** within another element, regardless of the depth of the nesting.

A _descendant selector_ is defined by using a space between two other selectors:

```css
/* This will match all <span> tags nested anywhere within a <h3> tag having a class of "sub-title" */
h3.sub-title span { ... }
```

**PRACTICE:<br>- Using a _descendant selector_, set the background color of the `<p>` tag with the text of "This is a paragraph inside of the third DIV" to yellow.**

##### There are three additional combinators:

These are not quite as common but can come in handy...

- The **child selector** (`>`)

    The _child selector_ is similar to the _descendant selector_, except that it only matches elements that are **direct** children, that is, nested only one-level deep:

    ```css
    /* Selects all <p> tags that are direct children of a <div> */
    div > p {...}
    ```
    
- The **adjacent sibling selector** (`+`)

    ```css
    div + p {...}
    ```

   Would select `<p>` tags only if they were preceded immediately by a `<div>` at the same level (sibling).

- The **general sibling selector** (`~`)

    Similar to the _adjacent sibling selector_, except that it targets **all** siblings, not just the adjacent one:

    ```css
    div.my-class ~ p {...}
    ```

    Would target all `<p>` tags that are siblings following a `<div>` with a class of "my-class".
    
**Questions?**

#### Specificity

*Specificity* is the means by which a browser decides which CSS rule gets applied when there is a conflict.  For example:

```css
.my-class {
    color: blue;
}

div {
    color: red;
}

<div class="my-class">What color am I?</div>
```

A conflict exists because the `<div>` matches both CSS selector rules.

**? - What color will the `<div>` in the above example be?**

The selector with the **highest** *Specificity* wins based upon this list of increasing specificity:

- Universal (*) selector
- Type (element) selectors
- Class selectors
- Attributes selectors
- Pseudo-classes
- ID selectors
- Inline styles

There is an exception to the concept of *specificity* known as the **!important** declaration.  Use of *!important* is not recommended because it can make debugging CSS more difficult than it already is.

#### Pseudo-classes

Pseudo-classes (along with pseudo-elements) let you style elements not just based upon their class, type, id or position in the document, but also their state. For example, whether an `<input type="checkbox">` is checked or not.

Some common pseudo-classes are `:active`, `:disabled`, `:empty`, `:first-child`, `:nth-child`, `:nth-of-type`, `:focus`, `:hover`, and many more!

We can also chain pseudo-classes for extra good fun time!  `li:nth-child(3):hover`

**PRACTICE:<br>- Use the `:hover` pseudo-class to change the cursor to the little hand-pointer when it's over any of the `<li>` elements.<br>- Use the `::first-letter` pseudo-element to set the size of the "C" in "Comments" to be 60px.**

Here's a link to learn more about [pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/pseudo-classes) and [pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements).

#### CSS Selectors - Key Takeaways

CSS selectors provide enormous capability and flexibility to target any element(s) for styling!

CSS selectors allow us to target an element, or elements, without having to resort to assigning a bunch of id's.

As a general note, lean toward using classes instead of id's - remember, id's need to be unique.

### 5. Further Study

Learning CSS, like much of coding, is a never-ending process and in this lesson, we've done slightly more than scratch the surface.

As you code, you will undoubtably rely on the numerous resources available to you on the Internet. Hopefully, this lesson has provided you with some context to help you better understand the results returned by your web searches.

Lastly, Chrome's DevTools are invaluable in helping debug among other things, CSS.  [Here's a link to Google's docs that discuss inspecting pages and styles](https://developers.google.com/web/tools/iterate/inspect-styles/basics)

## Resources

[CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS)

[CSS3 cheat sheet](https://www.kobzarev.com/wp-content/uploads/cheatsheets/css/css3-cheat-sheet.pdf)

[CSS Colors](http://www.w3schools.com/cssref/css_colors.asp)

[css-tricks](https://css-tricks.com/almanac)

[codrops](http://tympanus.net/codrops/css_reference) 
