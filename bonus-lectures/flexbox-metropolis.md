![](/ga_cog.png)

---
Title: Introduction to Flexbox<br>
Duration: "60min"+<br>
Competencies: CSS, Flexbox<br>
Prerequisites: HTML, CSS basics<br>

---

<img src="https://i.ytimg.com/vi/JVYVDpdvdMo/maxresdefault.jpg" width=500/>

## Prerequisites

- Familiarity with display property values such as: block, inline, inline-block

## Objectives

By the end of this you should be able to:

- Know when and where to apply flexbox
- What flexbox properties are available to a flexbox container
- What flexbox properties are available to a flexbox child element
- Implement a nav element using flexbox

## Intro

### A Very Brief History
Flexbox was introduced as part of CSS3 and it's been around since ~2008. Despite being a technology that has been around for nearly 12 years, it lacked consistent browser support (until recently) and thus developers have often had to fall back on some of the following older layout approaches:

- changing and elements `display` property from `inline` to `block`
- using the `float` or `position` property to take an element out of the document flow

[Basics & Terminology Of Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

#### Can I use flexbox?
Flexbox, currently has near universal support from all major modern browsers. You can find out what browsers support by going to [caniuse.com](http://caniuse.com/) , this website also documents support for just about anything else you might want to put in the browser, inclulding HTML and JavaScript. 

#### Vendor Prefixes
If you are wondering if you should be using `vendor prefixes` (looks like the code below) and how to write them, a great resourse is [shouldiprefix](http://shouldiprefix.com/):

```
.page-wrap {
  display: -webkit-box;  /* OLD - iOS 6-, Safari 3.1-6, BB7 */
  display: -ms-flexbox;  /* TWEENER - IE 10 */
  display: -webkit-flex; /* NEW - Safari 6.1+. iOS 7.1+, BB10 */
  display: flex;         /* NEW, Spec - Firefox, Chrome, Opera */
}
```


In SEIR we are only worrying about modern browsers and won't be including vendor prefixes in our CSS but we want that you are aware they exist and their purpose. 


### Flexbox is its own thing
Flexbox is built with its own logic. Flexbox properties are more descriptive like `justify-content: space-between;` or `flex-direction: column;` with the spacing and resizing being calculated under the hood. 

Flexbox has just two types of elements, each of which have their own properties.

- `flex container` - `parent`
- `flex items` - `children`

### Use Case for Flexbox
One great use case for flexbox is a layout pattern that is often referred to as `cards`. Cards are often used for online shopping.  Here the cards respond to either a `Wide` or` Narrow` viewport

**Wide**

<img src="https://i.imgur.com/56uik0T.png" width=500/>

**Narrow**

<img src="https://i.imgur.com/LwYtndU.png" width=500/>

Here are some commonly desired layout patterns:
- even spacing between cards
- The number of cards wraps to another row if it doesn't fit the width
- The cards are all the same size
- The first and last element align with other elements on the page to provide uniformity and overal page layout cohesion. No matter the width, the cards behave in a certain way that is expected and generally desired.

### What We Are Building Today
We will be building cards that just have a single letter on them. As we build we will learn about some properties of Flexbox and their behavoirs.

<img src="https://i.imgur.com/TFc73Sf.png" width=500/>


### Getting Started

#### Starter-Code Directory

- Navigate to the starter-code directory
- Inisde are four files and a folder:
	- The folder `metropolis` contains font files (don't worry about them! They are good to go!)
	- `index.html` - it is already set up for you
	- `app.js` - this has functionality to help us add and remove divs on the press of a button so we can focus on writing CSS, rather than HTML - it is already set up for you
	- `starter.css` - a little bit of css to get us started - it is already set up for you
	- `main.css` - this is the **ONLY** file that you will be coding in for this morning's exercise

Open `index.html` in your browser and it should look like this and the buttons should add and remove a letter `card`

<img src="https://i.imgur.com/A6nxcmv.png" width=500/>

### Getting Started

Open the `main.css` file that as we will be writing all our CSS there. 

#### Workflow

Set up all the different windows you will be working in, in a way that helps you have a smooth work flow, so you are limiting the amount you have to minimize and resize your work and you can instead just focus on coding. 

Here is my layout for this lesson. Different layouts will work with different lessons. But always take a minute to try to find a good workflow. 


<img src="https://i.imgur.com/gsk0jCz.png" width=500/>

#### Flexbox Axes

Flexbox is one dimensional in that it either applies to elements in a `row` or `column`.  If working on a `row` the `main axis` is horizontal however if set to `column` the `main axis` will be vertical.  

<img src="https://i.imgur.com/8vyhPm1.png" width=500/>

#### Flexbox Playground

During the lesson we will use [Flexbox Playground](https://codepen.io/jkeohan/live/zdKJOY) to explore the flexbox settings and their effect. 

#### Flexing the cards

Let's add a border to all of our elements so we can see their sizes and layouts. Add the following to the `main.css` file:

```css
* { border: 1px solid gold}
```

Let's open up Chrome Dev Tools, so we can see where the cards are being added and their html.

Adding a few cards using the `+`. 

<img src="https://i.imgur.com/eoarfgP.png" width=200/>

Examine those elements in DevTools and you will see that they have a display set to block

<img src='https://i.imgur.com/tkZmYsG.png' />

The letters are inside of a div that has a class of `card` and the `card` divs are inside a div with a class of `flex-container`

You have already been exposed to the display property and that elements are assigned a default value of either `inline` or `block` by default.  Another value that we can assign to the display property is `flex`. 

The main properties that are specific to the to the `flex` parent are:

| Property | What's It Do? | Examples |
|----------|---------------|----------|
| display | Turns on flexbox              | `flex`   |
| flex-direction| Sets the directional flow of flex items | `row`, `column` |
| justify-content | Align along main axis | `center`, `space-between`, `space-around` |
| align-items | Align along cross-axis | `flex-start`, `center` |
| flex-wrap | Wraps elements to the next line | `wrap`, `wrap-reverse` |

<!-- The main properties that are specific to the to the `flex` children  are:

| Property | What's It Do? | Examples |
|----------|---------------|----------|
| flex-basis | Sets the default size of the element | `px`, `%`, `em` |
| flex-grow |  Item will grow  | 1, 2|
| flex-shrink | Item will shrink | 1, 2|
| order | The order in which they appear | 1, -1|
 -->


#### Turning On Flexbox
Let's make the cards flex items by adding the following code:

```
.flex-container {
  display: flex;
  background-color: #e9ece5;
}
```

The cards now should all add onto one row.

<img src="https://i.imgur.com/KjJusH4.png" width=400/>


#### Styling the cards

Right now our letters look like plain text, let's make them look more like cards. 

We'll change the color of the text, the background, and give some padding and margins, lastly we'll center the letter in the card

```
.card {
  color: white;
  background-color: #b3c2bf;
  padding: .5em;
  margin: .3em;
}
```

<img src="https://i.imgur.com/SotraXD.png" width=400/>

#### Styling the flex container

The flex-container can have any regular properties or it can be a flex item of another container. In our case, its relation to its parent element is non-flex.

It would be nice if the container was a little narrower than the `header` and would stay centered on resizing. We can achieve this by adding:

```
.flex-container {
  display: flex;
  background-color: #e9ece5;
  width: 90%;
  margin: auto;
}
```



<img src="https://i.imgur.com/pEEWZBS.png" width=400/>

If we decrease the width we can see that our cards can move outside of the parent container causing an unexpected and unappealing look

<img src="https://i.imgur.com/8IUBvqs.png" width=400/>


By default, flex items only stay on one row. In this case it is possible for them to overflow their container. 

We can make it look better by making the overflow `hidden` which will not allow the user to see the overflow or `scroll` to allow the user to scroll to the content. 


```

.flex-container {
  display: flex;
  background-color: #e9ece5;
  width: 90%;
  margin: auto;
  overflow:scroll;
}
```

- Flexbox also will let you wrap content into another row, so let's add that

```
.flex-container {
  display: flex;
  background-color: #e9ece5;
  width: 90%;
  margin: auto;
  overflow: scroll;
  flex-wrap: wrap;
}
```

<img src="https://i.imgur.com/j1H4VhV.png" width=300/>

**Bonus:** `flex-wrap` can have a value of `wrap-reverse` how does that orient the cards?

#### Flex-basis

Something looks off, instead of neat rows and columns, we seem to have a bit of a skew from row to row and between elements.

<img src="https://i.imgur.com/SSAhahH.png" width=300/>

By default, Flex items grow to fit their content and no more. These letters all have different widths (quick compare: `H`, `I`, `J`), sometimes, this look is desirable however in our case it isn't. 

Let's set the minimum width using flexbox's `flex-basis` property

```
.card {
  color: white;
  background-color: #b3c2bf;
  padding: .5em;
  margin: .3em;
  flex-basis: 1em;
}
```

<img src="https://i.imgur.com/NMFiLFR.png" width=300/>

Yay! But wait! now our letters are off to the left and no longer centered! Let's fix that using the `text-align:center;` property

```
.card {
  color: white;
  background-color: #b3c2bf;
  padding: .5em;
  margin: .3em;
  flex-basis: 1em;
  text-align: center;
}
```

<img src="https://i.imgur.com/81dqnuN.png" width=300/>


#### Flex-direction
By default, the `flex-direction` is `row`, but we can play around with the order of our `flex-items` by changing the `flex-direction` property of the `flex-container`
Note: we will need to add a `height` in order to see multiple columns

```
.flex-container {
  display: flex;
  background-color: #e9ece5;
  width: 90%;
  margin: auto;
  overflow: scroll;
  flex-wrap: wrap;
  flex-direction: column;
  height: 400px;
}
```

<img src="https://i.imgur.com/xsYH5z5.png" width=300/>

That was fun, but not quite what we want, so let's set flex-direction back to `row` and remove the height property.

#### Justify Content
The `justify-content` property is jam packed with great responsive layout options.

Right now, as we add cards, they add from left to right. But we have other really nice options

Let's start with center:

```
.flex-container {
  display: flex;
  background-color: #e9ece5;
  width: 90%;
  margin: auto;
  overflow: scroll;
  flex-wrap: wrap;
  justify-content: center;
}
```

Take a moment to play around with it, it adds a single centered card and then with each card moves them outwards until the row is full, and then wraps into the next row, where the centering begins again.

**Center:**


<img src="https://i.imgur.com/IHuSg90.png" width=300/>

Right now the elements are clustered in the middle. What if we wanted them centered, but just have ... more space around?

Flexbox has a `space-around` property! Let's give it a whirl

Space-around:

<img src="https://i.imgur.com/kk4lkrD.png" width=300/>

Ok! That's cool, but what if you want the start and end to align with the edges and then any additional elements to have even space between?

Yes flexbox can! With the `space-between` property



<img src="https://i.imgur.com/WGdsDeE.png" width=300/>

<br>


#### Vertical Centering
Another gnarly challenge of responsive design is vertical centering/positioning. This isn't an issue with our alphabet cards because they all have the same height, our .flex-container sizes based on its content and we're already going for flexbox's default. But if you need it, flexbox has it! Look into `align-items`

#### Adding Flex Properties to Individual Flex-Items
Right now, all of our elements are uniform in size and color. This isn't visually intersting and sometimes we need to give it a bit more flair.

##### Set Up `selected` cards
Built into our site, is the ability to toggle a class of `selected` on our cards. All you have to do is click on the card. Right now though, it will only show in the dev tools.

Let's make our selected cards stand out.

```
.selected {
  background-color:  #fae596;
  color: #40A69A;
}
```

Now when you click on them they should toggle between their new look and old look!

#### Flex-grow/Flex-shrink
Sometimes we do want our cards to be different widths. Unlike the default which was based on letter width and lacked conventional proportions, we can make the cards be proportional to each other. Each `flex-item` starts with a `flex-grow`/`flex-shrink` value of 1.

- Add a `flex-grow` value of 2 to our `seleted` cards

```
.selected {
  background-color:  #fae596;
  color: #40A69A;
  flex-grow: 2;
}
```

This will grow the selected cards out proportionally, but if there is not enough space, it will allow for the items to grow but not overflow their container

#### Flex-order
You can also change the order of the flex items. Let's say we want our `selected` cards to be featured on the left

```
.selected {
  background-color:  #fae596;
  color: #40A69A;
  flex-grow: 2;
  order: -1;
}
```

![](https://i.imgur.com/2aYPXWC.png)


#### Final Thoughts
Flexbox's intuitive design and descriptive properties are both powerful and easy to learn.

There are a handful of things this lesson did not cover. Below is the CSS-Tricks `A Complete Guide` - indeed, it is complete and quite short which is a beautiful reflection of the elegance and utility of flexbox.

#### Resources

- [CSS-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Flexplorer](http://bennettfeely.com/flexplorer/)
- [Understanding Flexbox](https://github.com/ohansemmanuel/Understanding-Flexbox/tree/master/08.%20Building%20a%20Music%20app%20Layout%20with%20Flexbox)

