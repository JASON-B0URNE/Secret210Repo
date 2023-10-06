## Introduction:
Samuel Brescia  
2 October 2023  
Lab 2

## Executive Summary:

Labs 2a and 2b implemented JavaScript and HTTPS to add functionality and security to the web application. JavaScript was utilized to save a user task list within the local browser database. Security was added via HTTPS traffic, which was allowed by running certbot on the AWS server. 

## Design Overview

In lab 2a, I was responsible for creating a dynamic task list that changed based on user input. This meant using JavaScript to create, read, update, and delete different elements of the list. The JavaScript manipulated a Database in the browser's local storage and then changed the DOM based on the information stored there. This allowed the data to persist after closing the tab or browser.

In lab 2b, I was responsible for creating a domain name for my website and enabling HTTPS. The domain name was created by establishing a static IP address for my webpage and then creating an A record that linked a domain name to that IP address. An additional CNAME record was created to redirect a different alias domain to the main domain. Lastly, certbot was used to generate an HTTPS certificate and enable traffic over HTTPS. 

### UML Diagram
![UML Diagram of the Process](/lab2/images/umlDiagram.png)

### CNAME Redirect
![Screenshot of the CNAME Redirect](/lab2/images/cnameRedirect.png)

### DNS Records
![Screenshot of the DNS records](/lab2/images/dnsRecords.png)

### HTTPS Enabled with Certificate
![Screenshot of the HTTPS Certificate](/lab2/images/httpsCert.png)

### Data in Local Browser Database
![Screenshot of the Browser Database in Browser Developer Tools](/lab2/images/localBrowserDB.png)

### File Descriptions

* index.html - Provides the skeleton and content of the HTML page
* css/styles.css - Provides the styling for the HTML page
* js/scipt.js - Allows the user to create, read, update, and delete tasks in the task list. This is implemented by storing the list in the browser storage and then manipulating the stored data. 
* resources/bkg_pic.png - Background image for the website  
* resources/DroidobeshDepot-gxmVe.otf - Custom Star Wars font for the header.
* favicon.ico - R2-D2 page icon

## Questions:

1. What are two differences and similarities between JavaScript and a previous language you have used (e.g. C++ or Python)? (Think of differences and similarities that are more unique to these 2 languages, not all languages in general.)

- One difference between JavaScript and C++ is that C++ is a lot more strict when it comes to declaring variables or comparing variable types. JavaScript easily initializes any variable type (dynamically typed), while in C++, each variable type needs to be clearly defined (statically typed). Additionally, in C++, only variables of the same type can be compared, while JavaScript easily compares all variable types. Another difference is that JavaScript is focused on programming web applications, while C++ is a more universal language. JavaScript has built-in objects that manipulate the DOM and provide functionality to web pages. C++ is universally used and has thousands of libraries that are implemented in many different uses. 

- One similarity between C++ and JavaScript is they have similar syntax: ending lines with a comment, method of declaring functions, method of declaring loops, and method of accessing functions. Another similarity between C++ and JavaScript is that both are used in the server back-end. JavaScript provides a connection between back-end computation and front-end functionality. C++ is lightweight and fast, which makes it useful for efficiently processing requests and other resource-intensive tasks. 

2. What is the difference between JSON and JavaScript objects?

- JSON is a method of storing data in a string that contains a key and a value. Without a compiler or interpreter giving meaning to the data in the string it is only a string. On the other hand, JavaScript objects are parsed versions of JSON strings, meaning that the keys and values are associated with each other in computer memory. JavaScript objects can then be called as variables in functions or can be used for other computational purposes. Many coding languages use JSON to transmit and store data, but each language parses the JSON as its own object. 

3. If you open your web page in two different browsers, will changes on one appear on the other? Why or why not?

- No, the changes will not save over different browsers. The javascript code saves the task list in the local storage of the browser in use. Unfortunately, the data cannot be transferred between different browsers because they have separate local storage locations.

4. How long did you spend on this lab?

- I spent approximately 3 hours on this lab. 

5. What is the difference between HTTP and HTTPS?

- HTTP is a protocol that transmits web data in plaintext. This means that if you submit data via a GET or POST request the information is transmitted without encryption. HTTPS adds an S for secure. This means that the data is encrypted before transmission, stopping nefarious actors from easily obtaining sensitive information.

6. What does the A record do in your DNS domain?

- The A record associates a domain name with a static IP address. It associates that this domain name is found at this location and sends the user to that IP address. 

7. Which key does the `certbot` tool send to Let's Encrypt to be embedded in the certificate; the public key or the private key?

- The public key is embedded in the certificate. 

8. What is the TTL setting in DNS, what are the units, and what does it do?

- The TTL stands for Time to Live. Its units are in seconds, and it states the amount of time the record should be stored on the computer. A computer wants to work as efficiently as possible, so if you frequently go to a website, it does not want to keep requesting the DNS record for that location. Instead, it will store the information on the computer, and the TTL represents the amount of time that the record should be stored.

9. The DNS tool is new this semester. What did you like about it? What could we do to improve it? (Any answer gets full credit.)

- I liked that it was intuitive to use. It was easy for me to make an A record and the txt record. The difficult part was making a CNAME record. It would have been useful to provide example text of how we needed to type the domains as the placeholder text in each of the text boxes. Another solution could be more straightforward instructions on the formatting.

## Lessons Learned:

### Be Cautious When Recursively Changing File Ownership

During lab 2b, I was running a command that enabled the apache2 service to access the certificate files. I was trying to change the ownership of a file stored in a directory, that was stored in the /etc/ directory. Instead of specifying that specific directory, I recursively changed the ownership of the entire /etc/ directory. This mistake changed the ownership of the sudoers file, which then removed my access to the sudo command. After multiple attempts to troubleshoot the issue, I ended up deleting that AWS instance and creating another. From this, I learned the importance of double-checking commands that I run in the command line and the importance of taking snapshots of a virtual machine's state. 

### Creating a Page Redirect with a CNAME Record

I had difficulty creating a page redirect in the late stages of lab 2b. I followed the lab instructions, but the DNS page would not let me generate a CNAME record. I tried formatting the domain names differently, but no matter what I tried, it did not work. After talking with the TAs, I learned the required format for the CNAME record, and after fixing it, my redirect worked. I learned how to properly format the CNAME record, but I also learned that I need to quickly reach out to TAs when I am facing a problem that I cannot solve. 

### Handling Updates to a Task in the Task List

During lab 2a, I had difficulties displaying a task as checked once the boolean value had been changed in the database. It was difficult for me to conceptually determine how to display the task as checked. I tried multiple ways but realized that I was repeating code. Eventually, I determined that I could check the boolean value while the list was being printed on the screen. At this point in the code, I could initiate a change in the CSS class. I reached this conclusion by mapping out the process on paper and walking through each of the different steps. In the future, I need to do better at making a game plan for how I will implement functions before I begin programming. 

## Conclusions :

- Create, Read, Update, and Read user data with Javascript
- Create a domain on a DNS server that points to a static IP address
- Utilize local browser storage to store user input
- Manipulate HTML and CSS using Javascript functions
- Enable traffic over HTTPS and generate a certificate

## References

- https://www.w3schools.com/jsref/dom_obj_all.asp
- https://www.w3schools.com/jsref/api_storage.asp
- https://byu-itc-210.github.io/walkthrough/JSON-localStorage
- https://byu-itc-210.github.io/walkthrough/JsAndDom