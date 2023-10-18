### Using the Browser Local Storage with JavaScript
#### A Beginner's Look at the Web

Have you ever been filling out a form on a website when due to an uncontrollable circumstance you lose the information in that text field? That is most likely because the web application was not utilizing the browser's local storage. Browsers are responsible for parsing multiple coding languages allowing a user to seamlessly interact with a web application. The majority of web applications are stored on servers which can be connected to via the internet. Often the browser is concerned with 3 coding languages: HTML, CSS, and JavaScript. For the purposes of this tutorial we will be mostly concerned with HTML (which provides web applications with structure) and JavaScript (which provides web applications with functionality). You can start to develop your own web application right now!

Open notepad and paste the following:

```html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>

<h1>This is a Heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

Then select _save as_, and change the _save as type_ from .txt to all files. Name the file as _app.html_ and save the file on your desktop. Now navigate to your desktop and double click on app.html, so that it opens in a web browser. 

You should see something like:



The text **This is a Heading** and **This is a paragraph** are known as different elements. Each of these elements form the structure of the web application and provide content. These elements are a huge part of web applications! These elements can display user information, recieve user input, or preform a variety of different functions. The primary coding language that interacts and changes these elements is JavaScript. You likely see JavaScript change your experience on the internet everyday without realizing it. In order to add JavaScript to our web application we will add the following code:

```html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>

<h1>This is a Heading</h1>
<p>This is a paragraph.</p>

<button onclick="buttonClick()">Click Me</button>

<script>
function buttonClick() {
  alert("You Clicked The Button");
}
</script>

</body>
</html>
```

Edit your app.html file with the following code and then refresh your web application in your browser. You should now see a button that says _Click Me_. Click the button and see what happens.

You should see something like: 



In this example we added a button element. This button element is linked to a JavaScript function via the **onclick** attribute. This HTML attribute tells the browser to run JavaScript once the button is clicked. We stored our JavaScript between the **<script>...</script>** tags. This tells the browser where it can find our JavaScript code. 
