
## Introduction:
Samuel Brescia  
18 September 2023  
Lab 1  

## Executive Summary:

Labs 1a and 1b implement HTML and CSS to generate and style a basic web page. Docker is used in order to deploy a local version of the application, and the live version of the web application is deployed using Amazon AWS resources. 

## Design Overview

### Web Page
![Screenshot of the webpage ](/lab1/images/webpage.png)

### Amazon AWS Instance
![Screenshot of the Amazon AWS instance](/lab1/images/amazon.png)

### Apache Web Server
![Screenshot of current status of the apache2 web server](/lab1/images/apache.png)

### Docker Container
![Screenshot the Docker Desktop application](/lab1/images/docker.png)

### File Descriptions

* index.html - Provides the skeleton and content of the HTML page
* css/styles.css - Provides the styling for the HTML page
* js/scipt.js - Provides a script to show the submitted form in JSON format
* resources/bkg_pic.png - Background image for the website  
* resources/DroidobeshDepot-gxmVe.otf - Custom Star Wars font for the header.
* favicon.ico - R2-D2 page icon

## Questions:

1. What is the purpose of using Docker containers?
  -The Docker container provides a local test enviornment for applications. Docker provides a sandbox where features can be tested before being deployed on the live internet. 

2. Why is it useful to have both a development environment and a live server enviornment?
  -The development enviornment allows the developer to test new features without destroying the existing application. It gives the developer the opportunity to find bugs and test the security of the application. The live server enviornment is where users can interact with and use the application. The live server is in the real world, with real people and security threats.

3. What is the purpose of using a code versioning tool (i.e. Git)?
  -The purpose of a code versioning tool is to provide a log for developers to monitor how their application changes over time. These tools allow developers to confidently change code while knowing they can revert to a previous version. It also allows a team of developers to work simultaneously on an application and quickly download each others changes. 

4. What is the difference between a CSS rule with an *element* selector (i.e. h1, p, div etc.) and one with a *class* selector (i.e. .task, .task-done etc.)? When would you use each?
  -An element selector chooses all the instances of that html tag. An example where an element selector would be helpful is if you wanted to apply a specific font to all of the paragraphs <p></p> in a html file. Element selectors are useful for providing uniform style changes in an html document. A class selector chooses specific elements placed in a class. An example where a class selector would be helpful is changing the style of a specific heading elements that display important legal information. Class selectors are useful for providing specific style changes in a html document.

5. What are the advantages of putting your styles in a separate .css stylesheed instead of in the '<style>' element of '<head'>?
  -An advantage 

6. How do web browsers choose which CSS to use for an HTML element whe the CSS rules contradict each other? What is the order of precedence for CSS rules?
  -Web browsers follow a specificity hierarchy in determining which CSS rule to apply. The specificity hierarchy in order of most to least prevalent is: inline styles, IDs, classes, and elements. If there are two contradictory rules then the latest rule takes the precedence.

7. Why should you disable directory access for your server?
  -Directory access needs to be disabled because sensitive user information can be found in log and database files. If a hacker was able to see the directory they could gain insights into how the web application acts that would allow them to deploy exploits against the system.

## Lessons Learned:

### JavaScript Comparisons  

JavaScript does extremely loose comparisons. Therefore if (thisVar == 0) will evaluate true if thisVar = 0 or null or “” or false. This problem often arises when doing an if statement where you want to check if something is not blank but 0 is a good value. To solve this problem use === or !==. These mean an exact comparison, not a loose comparison. Therefore if (thisVar === “”) and thisVar = 0 it will be false. On the other hand if (thisVar == “”) and thisVar = 0 it will evaluate true.

*There should be 3 lessons learned in your write-up, not just one.*

## Conclusions :

- Configure and run an Amazon AWS cloud server
- Install and configure a Docker container
- Install and configure an Apache2 web server
- Pass user entered data into a JSON string
- Create and design a web page
- Use a code repository tool to dynamically change source code

## References

https://www.w3schools.com/css/css_specificity.asp

