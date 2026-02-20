# How Websites Work?
> I'll know how websites are created and will be introduced to some basic security issues.

## Hands-on exercies

### How websites work section
What term best describes the component of a web application rendered by your browser?

> *Front end* because that is what the user "sees" and is rendered by the browser.

### HTML section

One of the images on the cat website is broken - fix it, and the image will reveal the hidden text answer!

> *HTMLHERO*. In order to find the message I had to repair the website, by adding the file
extension for the cat image. I supposed it still a .png file as the first picture.

```html
<img src='img/cat-1.jpg'>
<img src='img/cat-2.jpg'> <!-- added .jpg to /img/cat-2-->

```

Add a dog image to the page by adding another img tag (<img>) on line 11. The dog image location is img/dog-1.png. What is the text in the dog image?

> *DOGHERO*. I added an HTML line with the provided location for the picture 'img/dog-1.png'

```html
<img src='img/cat-1.jpg'>
<img src='img/cat-2.jpg'>
<img src='img/dog-1.png'> <!-- new entry added -->
```

### Javascript section

Click the "View Site" button on this task. On the right-hand side, add JavaScript that changes the demo element's content to "Hack the Planet"

> *JSISFUN*. To get this flag I have added a new line of JS code in the marked region to change its original
HTML content and a button appeared after viewing the site.

```javascript
document.getElementById("demo").innerHTML = "Hack the Planet";
```

Add the button HTML from this task that changes the element's text to "Button Clicked" on the editor on the right, update the code by clicking the "Render HTML+JS Code" button and then click the button.

```javascript
<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>Click Me!</button>
```


