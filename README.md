# News Site Progression - Parts 1-4

We're going to build the front page of a newspaper website. The page will contain a collection of article cards within a grid layout. Each card will be have a photo, topic tag, title, and a brief description.

The following is a wireframe for the page.

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-wireframe.png)

[And here is a link to the finished page.](https://hopeful-kepler-e0ecef.netlify.app/)
## Part 1 - Article Grid

Your task for Part 1 of this assignment is to build a grid of article cards.

![](https://raw.githubusercontent.com/hoc-labs/images/main/article-grid.png)

### Define Default Colors

The starter project contains these pre-defined colors that we'll use throughout the web page. 
[MDN CSS Custom Properties Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)

```css
:root {
    --primary-color: #c72727;
    --light-color: #f3f3f3;
    --dark-color: #333;
    --link-color: #333;

    --sports-color: #f99500;
    --arts-color: #a66bbe;
    --tech-color: #009cff;
    --science-color: #3bd142;
    --food-color: #d1483b;
}
```
### Setting Page Defaults
* Set the background color to --light-color
* Set the color of links to --link-color
* Remove the underline from links
* Pick a Google Font and import via `<link>` element. [See Google Fonts Topic](https://chnn-anne.gitbook.io/html-css-fall-2021/appendix/google-fonts)

### Creating a Grid
There are two components to establishing a grid layout. The parent element that acts as the grid container and the child elements that need to be organized within that container.
Here is the basic layout for our article grid. The `<section>` element is the parent container and each `<article>` element is a child that will be arranged within that container. Our grid will have two rows, with three article cards in each row.

**Grid HTML**

```html
<body>
    <main>
        <section class="articles">
            <article></article>
            <article></article>
            <article></article>
            <article></article>
            <article></article>
            <article></article>
      </section>
    </main> 
</body>
```

**Grid CSS**

Define how many columns and rows we want the grid to have. In our case, we only need to define the number of columns and the grid will automatically wrap and start a new row after the number of columns we have specified have been filled.

Grids have introduced a new unit, called a fractional unit (FR), that allows you to express the percentage of the overall width or height very easily. One FR is one unit and you can simply define each column's width in FR units. Our grid is going to have three columns with equal width. So the value of the grid-template-columns property is just 1fr for each column. If, for example, we wanted the middle column to be twice as wide as the other two, we would simply change the middle 1fr to 2fr.

* Use the display property on the parent container to arrange the child `<article>` elements in a 3x3 grid.

The grid-gap property specifies the padding between each of the cells in the grid. These are often referred to as the grid "gutters".
* Create a gap between the grid elements

### Article Card

Next, we'll start filling out each article card with an image. Add an `<img>` element to each card. There are six images in the project images folder to use if you don't want to get your own.

Refresh your page and you'll notice that the images are very large. They are displaying with their original size. To fix this, add a style to set the image width to 100%. This will force the image to take up 100% of the width of the parent element.

Your page should now look like this.

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-1.png)

**Styling the Card**

We'd like to add a little styling to make each article card have a frame around it. 

To do this, define a CSS selector to be able to target all of the article cards in the section. 

For each:
* set the background color to white
* add a padding to each article card

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-2.png)

### Topic Pills

Add a topic tag to each article. These are often referred to as "pills".

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-3.png)


**Topic Pill HTML**

You will need to create two CSS styles for the topic pills. The general topic style will set those styles that are common to all the pills. Then, you will also need to define a topic-specific style to be able to set the topic-specific color for the pill.

Try to do it on your own first, but if you need help, see the solution at the end of the document for the topic-specific pill styles.

The topic pill should look like the following with the section-specific CSS style set.

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-4.png)

Next, you need to style the general topic style.
* set the text color to white
* set the font size to 9px
* set the text to be uppercase (text-transform)
* increase the padding
* round the corners (border-radius)

Here's what the page should look like with the topic pill styles complete.

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-5.png)

### Add Card Title/Abstract

Last, we're going to add a title and description to each card. This is simply adding a header followed by a paragraph element. Typically, we would have the title be a link to the article page, but we're just focusing on the single articles page for now, so we'll leave the href attribute empty. The `<h3>` element has a nice default value, so there's no need for us to change it.
Copy/Paste the `<h3>` and `<p>` elements into each of the articles in the page.

```html
<h3><a href="">Lorem ipsum dolor sit amet.</a></h3>
  <p>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Et ea
    impedit libero, beatae animi provident nesciunt molestias ipsam
    nemo ad.
  </p>
```

Here's what the page should look like with the Title/Abstracts added.

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-6.png)

### Making the Grid Responsive

Currently our Grid is not responsive, meaning that the layout isn't adjusting to accommodate narrower screen sizes. In order to make our grid responsive, we are going to use media queries.

Media queries allow you to specify CSS property values that should be used when different screen widths are detected. Best practice is to start off designing for "mobile-first", and then expanding the content as the screen width increases. We built our grid for desktop-first, but we're going to go back and make the default case be mobile-first, and then create a media query to change the layout for wider viewports.

Below is screen capture within the Chrome Developer Tools showing you how to open the screen size viewer to test your media queries.

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-7.png)

<br/>
The only change necessary to make our grid responsive is to set the default number of columns in the grid to one as the default and then create a media query to expand the grid to have three columns when the target viewport width is greater than 600px. The media query syntax is defined in more detail in the 

[MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)


* change the default for the grid-template-columns to be a single column.
* add a @media query block and if the mid-width>=600px, then you change the grid-template-columns to be three columns.

```css
@media (min-width:600px) {
  .articles {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
```

Now, when the width is less than 600px, there is just one column.

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-8.png)

<br/>

## Part 2 - Showcase Article

Your task for Part 2 of this assignment is to build a section to display a showcase article that would link to a feature article. This is known as a **hero** section. You will get practice using a background image to enable displaying content on top of an image.

This is what you should be aiming for.

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-9.png)

### HTML Structure
* create a `<section>` element immediately above the article section to hold the showcase article.
* give it a class "showcase" so that you can style it.


### Setting a Background Image

The showcase section will have a background image with text and a button layered on top of it. The technique necessary to get the image to be in a layer below the text and buttons is to set it using the CSS background property, instead of inserting an `<img>` element within the HTML page.

Read the [Background Image](https://chnn-anne.gitbook.io/html-css-fall-2021/miscellaneous-topics/background-image) topic and then try configuring the background image CSS on your own. There are lots of CSS properties to control different aspects of the image, so it's good spend some time to play around with them to try to understand what each one does.

Once you've given it a try, and are still having trouble, look at the solution at the end of this document.

### Setting the Showcase Height
Set the height to 40vh, which means 40% of the viewport, or visible screen. 


### Adding the Article Summary Content
Add the HTML content, which includes the topic tag, title, and abstract. We're going to stick with the default settings for the font size and weight for the text, so we don't need to add any additional CSS.

See the solution at the end of the document if you need help.

### Other Styles
* Create some padding around the showcase content 
* Set the text color to white.
* Set the width of the `<p>` element within the showcase section to 50% so that the paragraph text doesn't obscure all of the image.

### Adding a "Learn More" Button
The last item we need to add is the button at the bottom of the showcase section that links to the article. 

* add a `<button>` element at the end of the showcase section with the text "Learn More".
* give it a class "btn" so that you can style it.
* add the CSS selector for the btn class
  * remove the border
  * set the background color to --dark-color
  * set the text color to white
  * increase the padding 
  * add a selector for the button :hover event to change the opacity of the button to .9 when the user hovers over the button. [MDN Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover)

<br/>

## Part 3 - Navigation Bar

Your task for Part 3 of this assignment is to build a navigation bar that displays a logo along the top, followed by links to topic sections.

This is what you should be aiming for.

![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-11.png)

**HTML Content**

* add a `<nav>` element to wrap the navigation bar content.
* add an `<img>`, using images/logo.png, element for the logo.
* wrap the `<img>` logo element with an `<a>`. This is how to create a link with an image instead of text. When the user clicks on the logo, it would take them to the home page.
* add an unordered list, containing an `<a>` for each of the links. Since we're just creating a single page, you can leave the href attributes empty.
  
**CSS Styling**

Unordered list elements (`<ul>`, `<li>`) are used to implement navigation bars because they are ideally suited to the task since they are designed to represent a hierarchical structure of any depth. This navigation bar is only one level, but that's not always the case (take a look at the navigation bar on the cnbc.com site)

There are three CSS properties on the list element (`<ul>` or `<ol>`) that must be changed from the defaults to make a list into a navigation bar.

* **list-style-type**: none This removes to bullet icon for each list item
* **display: flex**  In this situation we are using it to cause the list items to flow from left to right across the available space.
* **padding:0** The default style for lists indents them from the left.
* **margin:0** Remove the default margin.

* set the font weight to bold for the list items.

**Adding a :hover selector for mouse-over events**

We used this in the last exercise to hover over the "Learn More" button on the showcase article. We're going to apply the same technique here on the navigation item links. The link color will change as long as the user's mouse remains hovered over the list item.

* create a :hover selector on the `<a>` element within the navigation container.

<br/>

## Part 4 - Footer

Your task for Part 4 of this assignment is to build a footer that displays three columns of typical information that goes on a footer.

This is what you should be aiming for.
  
![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-12.png)

**Footer Container HTML**

* add a `<footer>` element to contain the content.
* **first column**
  * add an `<img>` element, using the images/logo_light.png.
  * add a `<p>` below the image to hold the text.
  * set the width of the image to 150px
* **second column**
  * add a `<form>` element
    * add an `<input>` element to enter email address
    * add an `<button>` for the Subscribe button
* **third column**
  * add a `<h3>` for the "Connect with Us" heading
  * use a `<ul>`/`<li>` for the list

**Footer Container Styles**

* **general styles**
  * set the background color to --dark-color
  * set the text color to white
  * add padding of 32px
  * use a grid with three columns to arrange the footer content with a grid gap of 24px
* **second column**
  * email input
    * add padding of 8px
    * add margin on the bottom of 8px
* **third column**
  * set the text color for links in the footer to white
  * set the hover color for links in the footer to red

Use an attribute selector to select the `<input>` element for the email address.
[MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors)

Here's an example of how to use it:

```css
.footer-container input[type='email'] {
}
```
### Making the Footer Responsive

The modifications to the footer are similar to those for the article grid, just changing the default number of columns to be one and increasing it to three when the screen width is greater than 600px.

  
![](https://raw.githubusercontent.com/hoc-labs/images/main/news-site-progression-article-grid-13.png)


## Solutions

### Topic Pills

```html
<span class="topic topic-science">Science</span>
```

```css
.topic-sports {
  background-color: var(--sports-color);
}
.topic-arts {
  background-color: var(--arts-color);
}
.topic-technology {
  background-color: var(--tech-color);
}
.topic-food {
  background-color: var(--food-color);
}
.topic-science {
  background-color: var(--science-color);
}
```
### Showcase Background Image
The background property has the following values that we will set:
* url(the location of the image)
* center/cover - cover tells the browser to make sure the image always covers the entire container, even if it has to stretch the image or cut a little bit off one of the edges.

Like the border property, you can use the background property and combine multiple properties, or set each individual, such as background-image, background-repeat, background-position, background-size...
```css
.showcase {
  background: url('../images/robot.jpg') center/cover;
}
```

### Showcase Article Summary Content
```html
<span class="topic topic-technology">Technology</span>
 <h1>An Article About Technology</h1>
  <p>
  Lorem ipsum dolor sit amet consectetur adipisicing elit. Expedita
  recusandae consequatur similique doloribus. Corporis, et a ullam
  praesentium facere veritatis veniam? Aperiam ipsa totam veniam,
  atque illo sed suscipit accusamus.
  </p>
```
























