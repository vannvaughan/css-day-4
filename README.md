# More CSS -- Media Queries and Odds & Ends

## Overview
Today we're shoring up any CSS concepts that may still need work, and we're covering some of the more niche or advanced concepts that you might need from time to time. 

## Topics
- [Box-Sizing and Box-Model](#user-content-box-sizing-and-box-model)
- [Flexbox](#user-content-flexbox)
- [Reset Files](#user-content-reset-files)
- [Backgrounds](#user-content-backgrounds)
- [Animations](#user-content-animations)
- [Responsiveness](#user-content-responsiveness)

## Explanations
### Box-Sizing and Box Model
I may have covered this ad nauseum with some of the groups, so I apologize, but let's review this one last time.

#### Box Model
The box represents the content, padding, margin, and border of each html element. 

<img src="http://codewithme.us/portland/main-curriculum/images/box-model.png">

#### Box Sizing
By default, the height and width you apply to an element in your CSS control the size of the content, but any margins, padding, or border you specify will be added to the size. 

To avoid unexpected additions, we often specify: 

```
* {
   box-sizing: border-box;
}
```
### Flexbox
You know the main properties already, but you might want to play around with some other features of flexbox: 

- Flex-basis
- Flex-direction
- Flex-grow

### Reset Files
One way or another, you'll want to reset your files, so find a reset file that works for you and add it to your project. Remember to put the link for this file above your own stylesheet. Otherwise, you might reset your own styles. 

```
      <link href="styles/reset.css" rel="stylesheet">
      <link href="styles/main.css" rel="stylesheet">
```

Here is one reset file you can use from Eric Meyer. The author, by the way, recommends tailoring the file to your needs.

[Eric Meyer's Reset File](https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.css)

### Backgrounds
As you already know, background images will be your constant companion in CSS. To review, here are a few of the properties you will likely set: 

```
.background-image-container {
   background-color: #eee;
   background-image: url("amazing-image.jpg");
   background-position: center center;
   background-size: cover;
   background-repeat: no-repeat;
}
```
Of course, if you get tired of typing all of those properties, you can type them all in the background property: 
```
.background-image-container {
   background: #eee url("some-image.jpg") center center / cover no-repeat;
}
```
Notice that I have to separate the position from the size with a slash. That allows CSS to read either a single position value or two. (If you don't specify a second value, it defaults to 'center.')

### Animations
This part isn't strictly necessary. It's just for fun. 

CSS animations can make elements appear, move across the screen, or rotate. To use these animations, you need to first define the nature of the animation in a keyframe: 

```
@keyframes appear {
      from {
            opacity: 0;
      }
      to {
            opacity: 1
      }
}

```
Keyframes always begin with the `@keyframes` label and are followed by the name you give it. I chose 'appear,' but you could have chosen any name. 

Inside the keyframe, we define the two endpoints of the animation with `from` and `to`. We could also define multiple stages with `0%`, `25%`...`100%`. 

Inside the stages of the keyframe, we define the properties we want to animate and the values they should have at each stage. 

After defining the keyframe, we can use it as a value for the animation-name property on another element, along with a few accompanying properties:

```
.intro {
      animation-name: appear;
      animation-duration: 1s;
      animation-timing-function: ease-in-out;
}
```

Or I could use a shorthand property: 
```
.intro {
      animation: appear 1s ease-in-out;
}
```
You can animate other properties, and you can use transitions to animate property changes as well. 

### Responsiveness
So let's take a look at the project for today to see an example of responsiveness: [Wide Open Tech](http://wideopentech.com)

Open up your console and resize the page. Notice how the elements change. 

- What seem to be the major breakpoints? 
- What are the major changes?

You might also check out this visual display of responsive vs. unresponsive design: [A Visual Comparison of Responsive Web Design](https://www.venveo.com/blog/a-visual-comparison-of-responsive-web-design)
Whatever the properties we're trying to change, we need to target the size at which to change those values. To do that, we can use media queries.


#### Relative Units
To make the site friendlier at different viewport sizes,we could use relative units. The `em`, `rem`, and `%` units will allow font sizes and element sizes to expand with the viewport. 

The `em` and the `rem` units are based off of the size of the root element, or html. Typically, this size is 16px, but users can change it in their settings. Thus, 1em would be 16px and 2em would be 32px. 

The difference lies in stability. The `em` value can be reassigned within a block of your code and thus change its size. The `rem` value remains constant throughout your CSS file. See Zell Liew's blog for more information: [REM vs EM – The Great Debate](https://zellwk.com/blog/rem-vs-em/)

#### Media Queries
Media queries target the screen type and size of your user and apply styles accordingly. In order to make media queries work better on mobile devices, we include a viewport meta tag in the head of the html:

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

The media query itself begins with an `@media` keyword and is followed by the view type and view properties:

```
@media screen and (min-width: 400px) {

}
```

This media query will target all screen views with a minimum width of 400px. 

Besides `screen`, you can also specify the following values: 
- print
- only (targets only browsers that support media queries) 
- all

Inside the media query, you can target any elements and set any properties you need. For example, you might change the size of a column, the direction of a flex, or the display of an element. 

```
@media screen and (max-width: 400px) {
      .main-nav {
            display: none;
      }
      .mobile-nav {
            display: block;
      }
}
```
