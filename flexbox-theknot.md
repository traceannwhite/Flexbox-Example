![](/ga_cog.png)

---

Title: Introduction to Flexbox<br>
Author: Joe Keohan<br>
Duration: 3.5hrs+<br>
Competencies: CSS, Flexbox<br>
Prerequisites: HTML, CSS basics<br>

---

<img src="https://i.ytimg.com/vi/JVYVDpdvdMo/maxresdefault.jpg" width=500/>

## Prerequisites

- Familiarity with display property values such as: block, inline, inline-block

## Objectives

By the end of this you should be able to:

- Know when and where to apply flexbox
- Work with several flexbox properties available to a flexbox container
- Work with several flexbox properties are available to a flexbox child element
- Implement a design using parent and child flexbox properties

## Intro

### A Very Brief History

Flexbox was introduced as part of CSS3 and has been around since ~2008. Despite being a technology that has been around for nearly 12 years, it lacked consistent browser support (until recently) and thus developers have often had to fall back on some of the following older layout approaches:

- changing and elements **display** property from **inline** to **block** or **inline-block** or vice versa.
- using the **float** or **position** property to take an element out of the document flow

Floats are now best used to: [Wrap Text Around An Image](https://codepen.io/jkeohan/pen/eepKXQ)

Position can be used to: [Place Content Into A Specific Position(www.signesduquotidien.org)](https://www.signesduquotidien.org/)

#### Can I use flexbox?

Flexbox has near universal support from all major modern browsers. You can find out what browsers support by going to [caniuse.com](http://caniuse.com/) , this website also documents support for just about anything else you might want to put in the browser, inclulding HTML and JavaScript.

#### Vendor Prefixes

At times **vendor prefixes** are required for flexbox and other css properties.  You can determine if a specific properrty requires a prefix by going to [shouldiprefix](http://shouldiprefix.com/):

```
.page-wrap {
  display: -webkit-box;  /* OLD - iOS 6-, Safari 3.1-6, BB7 */
  display: -ms-flexbox;  /* TWEENER - IE 10 */
  display: -webkit-flex; /* NEW - Safari 6.1+. iOS 7.1+, BB10 */
  display: flex;         /* NEW, Spec - Firefox, Chrome, Opera */
}
```

In SEIR we will only build site for the Chrome browser and won't worry ourselves about including vendor prefixes. 

### Flexbox is its own thing

Flexbox is built with its own logic and its properties:values are much more descriptive such as: 
-  **justify-content: space-between or space-around** 
- **flex-direction: column or row** 

Flexbox targets two types of elements:

- **flex container** - parent
- **flex items** - children

[Basics & Terminology Of Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

#### Flexbox Axes

Flexbox is one dimensional in that it either applies to elements in a **row** or **column**.  

<img src="https://i.imgur.com/dEnifVE.png" width=500/>

It contains both a **main** and a **cross** axes which are used to position the elements. 

<img src="https://i.imgur.com/8vyhPm1.png" width=500/>

If working on a **row** the **main axis** is horizontal, however if set to **column** the **main axis** will be vertical.  

<img src="https://i.imgur.com/DNh7whQ.png" width=500/>

#### Flexbox Playground

The best way to really convey the power of Flexbox is to toy around with a few settings using  [Flexbox Playground](https://codepen.io/jkeohan/live/zdKJOY).

### Use Cases for Flexbox

A few good use cases for Flexbox are: 

- layout patterns often associated with **cards**. Cards are often used to advertise services on a company web site or display products for an online shopping.
- navigation items

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - We Do -  2min

One site that represents a modern layout and is a beautifully desinged is [The Knot](https://www.theknot.com/).

Let's take a look at two sections highlighted in red that are positioned using flexbox

<img src="https://i.imgur.com/tpJe9lz.jpg" width=500/>


<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - You Do - 3min

Examine the following [Mars](https://02nz9.csb.app/) site (remake of the original one) and locate where flexbox is being applied. 

Post your findings in the slack thread when asked by the instructor. 

<hr>




### What We Are Building Today

Below is an attempt at redesigning the **services section** of The Knot, located at the bottom of the site.  

<img src="https://i.imgur.com/cFqzpzh.png" width=500/>

We will be using **Flexbox** to position the elements, define their widths and leverage **flex-wrap** to wrap elements dynamically. 

Here is the desktop version we will build displayed as 2 rows and 4 columns.

<img src="https://i.imgur.com/WJgWKuE.png" width=600/>

Of course we also need to build it with responsiveness in mind:

<img src="https://i.imgur.com/TRX3MrM.png" width=700/>

### Getting Started

#### Starter-Code Directory

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 2min

Navigate to the **starter-code-theknot** directory where you will find the following files:
- **index.html** 
- **default.css** 
- **main.css** - this is the **ONLY** file that you will be coding in for this morning's exercise

<hr>

#### Examine The HTML

Let's take a moment to examine the **index.html** file. 

In the **head** we will see some additional css being imported for [Font Awesome](). It's an online library that provides all of the free icons were using in today's design. 

```html
<!-- FONT AWESOME -->
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.2.0/css/all.css"/>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"/>
```

##### Main.css
For this lesson we will only be editing **main.css.** however you are encouraged to examine the **default.css** file as it contains additional settings being applied to the desing.

```html
<!-- OUR CSS -->
<link rel="stylesheet" href="default.css" />
<link rel="stylesheet" href="main.css" />
```

#### ListContainer 
The **.ListContainer** section contains the **nav > ul > li** elements that make up the design.

```html
<nav class="ListContainer">
 <ul>
  <li class="ItemContainer">
   <a href="#">
   <div class="ImageContainer"><i class="far fa-heart fa-2x"></i></div>
   <div class="ItemContentContainer">
    <h4 class="ItemHeader">Wedding Vision</h4>
     <p class="ItemHeading">
	Define your wedding style and get matched with local vendors.
     </p>
   </div>
   </a>
  </li>
 </ul>
</nav>
```

<hr>

:question: What use case do you think justifies using a **nav** element as the parent for the ul? 

<hr>

### Getting Started


Open **index.html** in your browser and it should look like below.

<img src="https://i.imgur.com/KVXcYLe.png" width=400/>

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 2min

- Take a moment to examine the elements in **DevTools**
- Determine what property is being used to center the content in the li's


When asked slack your response in a thread created by the instructor

<hr>

HTML applies some default CSS which we can clearly see being represented here as the **dot** and spacing between the elements. 

There are times when front end devs want to start with a clean slate and so they have to manually add CSS that removes the defaults being applied. 

Lucky for us there is a css library that does that for us already, it's called **reset.css** and will add that to our **head**

```html
<!-- RESET CSS -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.min.css"/>
```

Once applied we should see the HTML updated to be the following.

<img src="https://i.imgur.com/1TxmIWd.png" width=500/>

#### Borders...Borders...Borders..

Open the **main.css** file.  As you can see it's a blank slate.  This is where we will be writing all our CSS.

Before we define any CSS settings specific to the design, let's turn on borders for all elements so we can clearly see their dimensions.

```html
* {
  border: 1px solid;
}
```

Hmmm...why didn't that apply? Any ideas?...

<hr>

#### <g-emoji class="g-emoji" alias="alarm_clock" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/23f0.png">⏰</g-emoji> Activity - 5min

- Take a moment to examine the elements in **DevTools**
- Review both the **Styles** and **Computed** tabs and see if they provide any insight.

When asked slack your response in a thread created by the instructor

<hr>

#### The !important Flag

So we've determined that adding **reset.css** has applied styles that override the wild card settings. We can fix this by adding the **!important** flag to make this setting  so that it take precedence.

```css
* {
 border: 1px solid !important;
}
```

<img src="https://i.imgur.com/iihi35C.png" width=500/>

#### Center The Nav

Let's horizontally center the nav by assigning it a width and a margin. 

```css
nav.ListContainer {
 max-width: 800px;
 margin: 0 auto;
}
```

### Adding Flexbox

You have already been exposed to the display property and that elements are assigned a default value of either **inline** or **block** by default. 

Another value that we can assign to the display property is **flex**.

The main properties that are specific to the to the **flex** parent are:

| Property        | What's It Do?                           | Examples                                  |
| --------------- | --------------------------------------- | ----------------------------------------- |
| display         | Turns on flexbox                        | **flex**                                    |
| flex-direction  | Sets the directional flow of flex items | **row**, **column**                           |
| justify-content | Align along main axis                   | **center**, **space-between**, **space-around** |
| align-items     | Align along cross-axis                  | **flex-start**, **center**                    |
| flex-wrap       | Wraps elements to the next line         | **wrap**, **wrap-reverse**                    |

#### The Flex Container

Let's make the ul a flex container by adding the following code.

```css
nav.ListContainer ul {
 display: flex;
}
```

This will horizontally align the elements. 

<img src="https://i.imgur.com/J4lz2Be.png" width=800/>

#### Flex Wrap

The elements shouldn't all be on the same line so let's see if we can partially fix that with **flex-wrap**

```css
nav.ListContainer ul{
  display: flex;
  flex-wrap: wrap;
}
```

The elements expanded in width and wrap around to the next row leaving free space to the right of the ul. 

<img src="https://i.imgur.com/0XnhLUK.png" width=500/>

#### Space Around

Let's take advantage of that free space on the right and divy it on both sides of the li's using **justify-content:around**

```css
nav.ListContainer ul {
 display: flex;
 flex-wrap: wrap;
 justify-content: space-around;
}
```

<img src="https://i.imgur.com/gwFH7Ej.png" width=500/>

#### The Flex Children

Here are the main properties that are specific to **flex** children:

| Property    | What's It Do?                                       | Examples                     |
| ----------- | --------------------------------------------------- | ---------------------------- |
| flex-grow   | Element will grow                                   | **flex-grow: 1**               |
| flex-shrink | Element will shrink                                 | **flex-shrink: 1**             |
| flex-basis  | Default size of an element before space distributed | **flex-basis: 100px**          |
| flex        | Shorthand for the above 3                           | **flex:1** ,**flex: 1 0 100px**, |
| align-self  | Default alignment                                   | **align-self:center**          |
| order  | Reorder the elements                                | **order:1**          |

For this design each li will have a defined width so let's see what the the **flex** shorthand property will do for us. 

```css
li.ItemContainer {
 flex: 1;
}
```

This property is a combination of **flex-grow**, **flex-shrink**, **flex-basis**.  By default the elements will only expand to fit their content, hence the grow.  **Flex-basis** provides a way to define a starting width for the elements before any available free space is divided up. 


<img src="https://i.imgur.com/4dr734f.png" width=500/>

If we include **flex-shrink** and **flex-basis** we can get closer to the design.

```css
li.ItemContainer {
	flex: 1 0 185px;
}
```

**Flex-basis** states that the elements must be a min width of **185px** but can grow if there is any additional space available. 

<img src="https://i.imgur.com/suEtHkd.png" width=500/>

#### Max-Width

It looks good however if we **decrease** the width of the page we can see that the last 2 elements increase in width thanks to **flex-basis**.  

Sometimes thats what you want, and it's good to know that this is a possibility, however that doesn't fit our design.

<img src="https://i.imgur.com/DHfrbFa.png" width=500/>

 So let's constrain the width of the elements and assign a **max-width**.  

```css
li.ItemContainer {
 flex: 1 0 185px;
 max-width: 185px;
}
```

#### Remove Borders
Were almost at our final design. Let's remove the borders and see where we stand.

<img src="https://i.imgur.com/VhKBva3.png" width=500/>

So it seems like the elements lost some space vertically between them.  This is due to borders providing a boundary for the elements to push against.  

Since we have removed that boundary they are now much closer. 

#### Margin or Padding

So let's create space between the elements on all sides. Margin is usually the way to go when elements want to push away from something so let's try adding margin to the top,bottom, left and right of the element. 

```css
li.ItemContainer {
 flex: 1 0 185px;
 max-width: 185px;
 margin: 20px;
}
```

<img src="https://i.imgur.com/XPyMklL.png" width=500/>

Although this creates space wanted we no longer have the items display in 2 rows with 4 elements per row. That is because margin adds to the space occupied by the element and flexbox doesn't take margin into consideration.

Another option to create the illusion of space is replace margin with padding.

```css
li.ItemContainer {
 flex: 1 0 185px;
 max-width: 185px;
 padding: 20px;
}
```

That is much better however the last items heading text wraps to the next line.

<img src="https://i.imgur.com/9L01dbm.png" width=500/>

We can fix that by increasing the **max-width** a bit.

```css
li.ItemContainer {
 flex: 1 0 185px;
 max-width: 195px;
 padding: 20px;
}
```

And that completes the design

<img src="https://i.imgur.com/k3P6foE.png" width=500/>

### Bonus: Reordering Elements

There might be a need one day to rearrange the elements in a different order.  Flexbox provides the **order** property for just that reason.  

Let's move **Wedding Vision** element to the end.  

```css
.ListContainer li:first-of-type {
 order: 1
}
```

The order is only applied after all other non-ordered elements are in place.  

<img src="https://i.imgur.com/k228f4p.png" width=500/>

Let's now move **Wedding Websites** to the end as well.  For that we need to target the 2nd li in the list as CSS isn't aware that elements are being moved around. 


```css
.ListContainer li:nth-of-type(2) {
  order: 2
}
```

<img src="https://i.imgur.com/4cmGi3i.png" width=500/>

### Resources

- [Basics & Terminology Of Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [The Most Popular Nav Bars Created With Flexbox](https://medium.com/flexbox-and-grids/the-most-popular-navigation-bars-created-with-flexbox-6c0f59f55686)
