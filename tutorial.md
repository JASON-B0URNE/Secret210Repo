### Using the Browser Local Storage with JavaScript
###### This tutorial is meant for users with a Windows machine.
#### Introduction
Have you ever been filling out a form on a website when due to an uncontrollable circumstance you lose the information in that text field? That is most likely because the web application was not utilizing the browser's local storage. Browsers are responsible for parsing multiple coding languages allowing a user to seamlessly interact with a web application. The majority of web applications are stored on servers which can be connected to via the internet. Often the browser is concerned with 3 coding languages: HTML, CSS, and JavaScript. For the purposes of this tutorial we will be mostly concerned with HTML (which provides web applications with structure) and JavaScript (which provides web applications with functionality). You can start to develop your own web application right now!

#### Getting Started with HTML
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



The text **This is a Heading** and **This is a paragraph** are known as different elements. Each of these elements form the structure of the web application and provide content. These elements are a huge part of web applications! These elements can display user information, recieve user input, or preform a variety of different functions. The primary coding language that interacts and changes these elements is JavaScript. You likely see JavaScript change your experience on the internet everyday without realizing it. 

#### Getting Started with JavaScript
In order to add JavaScript to our web application we will add the following code:

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



In this example we added a button element. This button element is linked to a JavaScript function via the **onclick** attribute. This HTML attribute tells the browser to run JavaScript once the button is clicked. We stored our JavaScript between the **<script>...</script>** tags. This tells the browser where it can find our JavaScript code. We need a way for the browser to link the onclick attribute to our JavaScript stored in the <script> tags. We do this by defining and calling a function. The **function buttonClick() {...}** between the <script> tags defines what JavaScript code needs to be executed when buttonClick() is mentioned in the HTML. Thus, when **onclick="buttonClick()"** is added in the <button> element it tells the browser to execute the JavaScript code defined in our **function buttonClick() {...}**.

#### Getting Started with Browser Local Storage

In a web application their may be situations where data needs to be saved, but the developer does not want to waste storage space on the server with this data. Circumstances where a less secure short term storage can be utilized. The best option in these instances is to use the browser local storage. Data in this storage container is specific to the web application and the browser. Meaning that the data will not be accessible via another browser or another website. You can always examine the contents of the browser local storage by using the key combination -shift- + -ctrl- + -i-. This will open up a subwindow in your browser that looks like:



You can then select the **>>** two arrows and select application from the drop down window. On the left side menu click on **Local storage**. This screen should look like:



#### Implementing JavaScript with the Browser Local Storage
Now that we know how to access the contents of the browser local storage we can now use JavaScript to store data there. In order to store data in the local storage we need an HTML element that can recieve user input. To do this we will use the form and input tag. We can implement these elements with the following code:

##### Add the HTML Form
```html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>

<h1>This is a Heading</h1>
<p>This is a paragraph.</p>

<form onsubmit="buttonClick()">
  <input type="text" name="userInput" placeholder="Type Here"></input>
  <br>
  <button type="submit">Save</button>
  <br>
</form>
<script>
function buttonClick() {
  alert("You Clicked The Button");
}
</script>

</body>
</html>
```

Your application should know look like this, and clicking on the save button should bring up the same alert prompt:



Now we need to read the data submitted within the input task. We do this by utilizing event handlers within JavaScript. Events are different things that happen on a webpage, and help execute JavaScript when an action is preformed. We can use an event handler to read the input of the form. In order to do this we can implement the following code:

##### Add the Event Handler
```html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>

<h1>This is a Heading</h1>
<p>This is a paragraph.</p>

<form onsubmit="buttonClick(event)">
  <input type="text" name="userInput" placeholder="Type Here"></input>
  <br>
  <button type="submit">Save</button>
  <br>
</form>
<script>
function buttonClick(event) {
  let formData = new FormData(event.currentTarget);
  let json = Object.fromEntries(formData);
  alert(json.userInput);
}
</script>

</body>
</html>
```

Now when you click the save button it should alert you with the text that you typed into the text box. The code **new FormData(event.currentTarget)** pulls the submitted data within the form, and the following line **Object.fromEntries(formData)** forms a JavaScript object. JavaScript objects store data in a key->value format. Meaning that a specific "keyword" is matched with a specific value. In this case we select the userInput key, which is attached to the value that the user types into the <input> tag. Now that we can select the user data we can now store that value in the local storage with the following code:

```html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>

<h1>This is a Heading</h1>
<p>This is a paragraph.</p>

<form onsubmit="buttonClick(event)">
  <input type="text" name="userInput" placeholder="Type Here"></input>
  <br>
  <button type="submit">Save</button>
  <br>
</form>
<script>
function buttonClick(event) {
  let formData = new FormData(event.currentTarget);
  let json = Object.fromEntries(formData);
  let jsonString = JSON.stringify(json);
  localStorage.setItem("database", jsonString);
}
</script>

</body>
</html>
```

Now if we look at the contents of our local storage we will see that we successfully stored data. We were able to store a key-database and the value as another key-value pair for the user input, but now we have another problem to address. How do we not clear the contents of the input element when hitting the save button? One possible solution is that we can change the attribute **value** on the <input> tag to refresh with our saved user input. This can be implemented with the following code: 

```html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>

<h1>This is a Heading</h1>
<p>This is a paragraph.</p>

<form onsubmit="buttonClick(event)">
  <input type="text" name="userInput" placeholder="Type Here"></input>
  <br>
  <button type="submit">Save</button>
  <br>
</form>
<script>
function buttonClick(event) {
  let formData = new FormData(event.currentTarget);
  let json = Object.fromEntries(formData);
  let jsonString = JSON.stringify(json);
  localStorage.setItem("database", jsonString);
  const element = document.getElementsByTagName("input");
  element[0].setAttribute("value", jsonString);
}
</script>

</body>
</html>
```


