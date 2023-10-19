### Using the Browser Local Storage with JavaScript
**_The Instructions are Specifically for Windows_**

#### Introduction
Have you ever been filling out a form on a website when, due to an uncontrollable circumstance, you lose the information in that text field? That is most likely because the web application was not utilizing the browser's local storage. Browsers are responsible for parsing multiple coding languages, allowing users to seamlessly interact with web applications. The majority of web applications are stored on servers that can be accessed via the Internet. Often the browser is concerned with three coding languages: HTML, CSS, and JavaScript. For this tutorial, we will be mostly concerned with HTML (which provides web applications with structure) and JavaScript (which provides web applications with functionality). You can start to develop your own web application right now!

#### Getting Started with HTML
Open Notepad and paste the following:

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

Then select _save as_, and change the _save as type_ from .txt to all files. Name the file _app.html_ and save the file on your desktop. Now navigate to your desktop and double-click on app.html so that it opens in a web browser. 

You should see something like:
<br><br>
<img width="285" alt="Basic Web Page" src="https://github.com/JASON-B0URNE/Secret210Repo/assets/106118000/7ad58e54-e57e-4ae0-a59e-e8851a9cb9b4">
<br>
Figure 1: Basic Web Page
<br><br>
The text **This is a Heading** and **This is a paragraph** are known as different elements. Each element forms the structure of the web application and provides content. These elements are a huge part of web applications! These elements can display user information, receive user input, or accomplish any other task. The primary coding language that interacts with and changes these elements is JavaScript. You likely see JavaScript change your experience on the internet every day without realizing it. 

#### Getting Started with JavaScript
To add JavaScript to our web application, we will add the following code:

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

Edit your app.html file with the following code, and then refresh the web application in your browser. You should now see a button that says _Click Me_. Click the button and see what happens.

You should see something like: 
<br><br>
<img width="335" alt="JavaScript Alert" src="https://github.com/JASON-B0URNE/Secret210Repo/assets/106118000/595e6822-050e-47ab-a1d6-ea95fc4078ab">
<br>
Figure 2: JavaScript Alert
<br><br>
In this example, we added a button element. This button element is linked to a JavaScript function via the **onclick** attribute. This HTML attribute tells the browser to run JavaScript once the button is clicked. We stored our JavaScript between the **<script>...</script>** tags. This tells the browser where it can find our JavaScript code. We need a way for the browser to link the onclick attribute to our JavaScript stored in the <script> tags. We do this by defining and calling a function. The **function buttonClick() {...}** between the <script> tags, defines what JavaScript code needs to be executed when buttonClick() is referenced in the HTML. Thus, when **onclick="buttonClick()"** is added in the <button> element, it tells the browser to execute the JavaScript code defined in our **function buttonClick() {...}**.

#### Getting Started with Browser Local Storage

In a web application, there may be situations where data needs to be saved, but the developer does not want to waste storage space on the server with this data; circumstances where short-term storage needs to be utilized. The best option in these instances is to use the browser's local storage. Data in this storage container is specific to the web application and the browser; meaning that the data will not be accessible via another browser or another website. You can always examine the contents of the browser's local storage by using the key combination -shift- + -ctrl- + -i-. This will open up a subwindow in your browser that looks like this:
<br><br>
<img width="515" alt="Browser Developer Tools" src="https://github.com/JASON-B0URNE/Secret210Repo/assets/106118000/87c9d9c4-5d40-4f70-bfd3-0ec511c680f4">
<br>
Figure 3: Browser Developer Tools
<br><br>
You can then select the **>>** two arrows and select **Application** from the drop-down window. On the left side menu, click on **Local storage**. This screen should look like this:
<br><br>
<img width="518" alt="Local Storage Under the Application Tab" src="https://github.com/JASON-B0URNE/Secret210Repo/assets/106118000/0278bbd7-f682-4553-9aea-401c60fcb628">
<br>
Figure 4: Local Storage Under the Application Tab
<br>

#### Implementing JavaScript with the Browser Local Storage
Now that we know how to access the contents of the browser's local storage, we can now use JavaScript to store data there. First, we need an HTML element that can receive user input. To do this, we will use the form and input tag. We can implement these elements with the following code:

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
  <input type="text" name="userInput" placeholder="Type Here">
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

Your application should now look like this, and clicking on the save button should bring up the same alert prompt:
<br><br>
<img width="649" alt="Add a Form and Text Input to the Application" src="https://github.com/JASON-B0URNE/Secret210Repo/assets/106118000/66867fde-72fd-41a8-91e7-44990355c781">
<br>
Figure 5: Add a Form and Text Input to the Application
<br><br>
Now, we need to read the data submitted within the input task. We do this by utilizing event handlers within JavaScript. Events are different things that happen on a webpage and help execute JavaScript when an action is performed. We can use an event handler to read the input of the form, as seen in the following code:

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
  <input type="text" name="userInput" placeholder="Type Here">
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

When you click the save button, it should alert you with the text that you typed into the text box. The code **new FormData(event.currentTarget)** pulls the submitted data within the form and the following line **Object.fromEntries(formData)** forms a JavaScript object. JavaScript objects store data in a key->value format; meaning that a specific "keyword" is matched with a specific value. In this case, we select the userInput key, which is attached to the value that the user entered. Now that we can select the user data, we can store that value in the local storage with the following code:

##### Store Input in the Browser Local Storage
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
  <input type="text" name="userInput" placeholder="Type Here">
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

If we look at the contents of our local storage, we will see that we successfully stored data. We were able to store a key 'database' and the value as another key-value pair in string format, but now we have another problem to address. How do we not clear the contents of the input element when hitting the save button? One possible solution is to change how the JavaScript handles the event. A solution to this problem can be seen with the following code:

##### Prevent the Input Box from Clearing while Saving
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
  <input type="text" name="userInput" placeholder="Type Here">
  <br>
  <button type="submit">Save</button>
  <br>
</form>
<script>
function buttonClick(event) {
  event.preventDefault();
  let formData = new FormData(event.currentTarget);
  let json = Object.fromEntries(formData);
  let jsonString = JSON.stringify(json);
  localStorage.setItem("database", jsonString);
}
</script>

</body>
</html>
```

After hitting the save button, our input stays in the text box, and the value is updated in the local storage. The code **event.preventDefault()** stops the HTML from performing the normal functions of the submit form, which means that the data in the input box will not be wiped and that our JavaScript code will also be executed, which saves values to local storage. Our application appears to be functioning normally except for one bug. After refreshing the page, closing the tab, or closing the browser, the data that is stored in local storage is not populating the input field. To do this we need to set the <input> element attribute **value** to whatever is in the local storage. The following code implements this change:

##### Populate the Input Field When Loading the Page
```html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body onload="fillInput(event)">

<h1>This is a Heading</h1>
<p>This is a paragraph.</p>

<form onsubmit="buttonClick(event)">
  <input type="text" name="userInput" placeholder="Type Here">
  <br>
  <button type="submit">Save</button>
  <br>
</form>
<script>
function buttonClick(event) {
  event.preventDefault();
  let formData = new FormData(event.currentTarget);
  let json = Object.fromEntries(formData);
  let jsonString = JSON.stringify(json);
  localStorage.setItem("database", jsonString);
}
function fillInput(event) {
  event.preventDefault();
  let jsonObject = JSON.parse(localStorage.getItem('database'));
  let element = document.getElementsByName("userInput");
  if (element.length > 0) {
    element[0].setAttribute("value", jsonObject.userInput);
  }
}
</script>

</body>
</html>
```

In this code, we linked the **fillInput** function to run whenever the page is loaded. This function retrieves the data stored in the local storage **JSON.parse(localStorage.getItem('database'))**, and then retrieves the <input> element by its name userInput **document.getElementsByName("userInput")**. If this element exists **element.length > 0**, then it will set its value attribute to whatever is stored in local storage **element[0].setAttribute("value", jsonObject.userInput)**. 

#### Conclusion
We did it! We were able to utilize both HTML and JavaScript to store and retrieve information from the browser's local storage. Remember that no sensitive information should be stored in this local database. It is meant to conveniently store short-term data that should not go to the server. Now that you understand the basics, it is time for you to explore other implementations of JavaScript and the browser's local storage. I reccomend using the resources at [w3schools.com](w3schools.com "w3schools"), specifically, [HTML Events](https://www.w3schools.com/jsref/dom_obj_event.asp "HTML Events"), [JavaScript Tutorials](https://www.w3schools.com/js/default.asp "JavaScript Tutorials"), [Local Storage](https://www.w3schools.com/jsref/prop_win_localstorage.asp "Local Storage"), and [JavaScript and HTML Elements](https://www.w3schools.com/jsref/dom_obj_all.asp "JavaScript and HTML Elements"). Your fundamental understanding of these resources should be able to help you further develop your skills and knowledge. The teaching style at w3schools is very similar to this blog post. It was through w3schools that I learned to program, and these posts are an essential resource to any web programmer. Additionally, the company Mozilla has excellent [resources](https://developer.mozilla.org/en-US/docs/Web/javascript "resources") to help you learn and understand JavaScript. Web programming can be difficult to learn, but if you stick with it, you can start to develop great applications. 
