## The canvas element:

## you can use the < canvas > tags not just like using img tag elements, you can put it from the html tags or you can use it from the DOM properties, but the difference is using canvas from html you have to insert a height and width to the canvas, while using the DOM properties it will be added by default with 300 px for width and 150 px high, if it's not sized well from the DOM properties attributes explicitly in the canvas attributes, you can style the canvas just like any element in the HTML using CSS with ( margin, boder,padding etc..).

## Some browsers is not supporting canvas which it should have a open and closing tags not like the image tags, so these browsers will accept the canvas by using the DOM properties with id, here we will use the 2D rendering context.

## How we can add canvas ?

## The < canvas > element has a method called getContext() used to obtain the rendering context and it's drawing functions, which takes only one parameter that is the type of context for the 2D graphics.

**Let canvas = document.getElementById('')
let ctx=canvas.getContext('2D');**

## Also you can check if the browser is supporting the canvas or not using if else statements to check it, and we can draw in the canvas area, It seems that you will have a lot of canvas work these days because it's important which you can draw many things rectangles triangles and many other shapes using JavaScript.

## You can also change styles in canvas colors, backgrounds, line width, line cap, line Join and line dashes which is good to use. In canvas area also you can write text with changing text styles.

**[First reference ](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_usage)**
**[Second reference ](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes)**
**[Third reference ](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)**
**[Fourth reference ](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_text)**