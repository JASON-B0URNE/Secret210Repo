## Introduction:
Samuel Brescia  
18 September 2023  
Lab 1  

## Executive Summary:

Labs 1B and 1B implement HTML and CSS to generate and style a basic web page. Docker is used to deploy a local version of the application, and the live version of the web application is disblayed using Amazon AWS resources. 

## Design Overview

I was responsible for creating a webpage that displayed a user task list. This task list needed to display a due date, task description, checkbox, and a delete icon. Lab 1A focused entirely on establishing the structure of this webpage with HTML. This page also needed to utilize a header, navbar, and a form where a user could input data.

In Lab 1B, the focus changed to styling the webpage with CSS. I was responsible for linking an external CSS stylesheet and applying various classes and IDs to style the webpage. I added dynamic changes to the task list, which changed the task description and checkbox once a task was marked complete. These changes did not change the content of the page, but they significantly changed the look and feel of the page.

All of my code was stored in a Git repository that logged my changes over time. This Git repository was stored locally on my computer and I observed how my changes affected the webpage via Docker. A Docker container acted as a test web server environment where I could monitor the effect of my changes. Once I was satisfied with the functionality of my page, I deployed it to the internet via an Amazon AWS web server. The Amazon AWS web server was running Apache services that were accessible via http. 

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

- The Docker container provides a local test environment for applications. Docker provides a sandbox where features can be tested before being deployed on the live internet. 

2. Why is it useful to have both a development environment and a live server environment?
 
- The development environment allows the developer to test new features without destroying the existing application. It allows the developer to find bugs and test the security of the application. The live server environment is where users can interact with and use the application. The live server is in the real world, with real people and security threats.

3. What is the purpose of using a code versioning tool (i.e. Git)?

- The purpose of a code versioning tool is to provide a log for developers to monitor how their application changes over time. These tools allow developers to confidently change code while knowing they can revert to a previous version. It also allows a team of developers to work simultaneously on an application and quickly download each other's changes. 

4. What is the difference between a CSS rule with an *element* selector (i.e. h1, p, div, etc.) and one with a *class* selector (i.e. .task, .task-done, etc.)? When would you use each?

- An element selector chooses all the instances of that HTML tag. An example where an element selector would be helpful is if you wanted to apply a specific font to all of the paragraph tags in an HTML file. Element selectors are useful for providing uniform style changes in an HTML document. A class selector chooses specific elements placed in a class. An example where a class selector would be helpful is changing the style of specific heading elements that display important legal information. Class selectors are useful for providing specific style changes in an HTML document.

5. What are the advantages of putting your styles in a separate .css stylesheet instead of in the '<style>' element of '<head'>?

- An advantage is that the style of the entire page can be instantly changed. Instead of having to edit all of the code in the HTML document a new style sheet can be attached giving the site a whole new feel. A good example of this is the website CSS Zen Garden where the same HTML content is given a different look and feel because of the external style sheet.

6. How do web browsers choose which CSS to use for an HTML element when the CSS rules contradict each other? What is the order of precedence for CSS rules?
 
- Web browsers follow a specificity hierarchy in determining which CSS rule to apply. The specificity hierarchy in order of most to least prevalent is inline styles, IDs, classes, and elements. If there are two contradictory rules then the latest rule takes precedence.

7. Why should you disable directory access for your server?
  
- Directory access needs to be disabled because sensitive user information can be found in log and database files. If a hacker was able to see the directory they could gain insights into how the web application acts that would allow them to deploy exploits against the system.

## Lessons Learned:

### Styling a Specific Condition in CSS

During lab 1B I ran into difficulties selecting specific HTML conditions. I wanted to color my checkbox orange after it was marked complete. I made several attempts to adjust the style, but everything I tried did not work. After some research in w3schools, I realized that the provided code created a pseudo-element for the checkbox after it was completed, and that I needed to style the pseudo-element. With this knowledge, I was able to make the proper changes in the CSS.

### Syncing the Git Repository on the Live Server

Early on in Lab 1A, I was confused as to why the live server was not reflecting the changes I was pushing to my Git repository. I kept seeing the local changes on my docker container, but these changes were not mirrored on the live website. After reading the command list on git I realized that local versions of git repositories are asynchronous and that I need to manually sync the changes onto the live server. After running the correct command I was able to view my changes on the live server. I realized that this asynchronous handling of data also helps preserve a local backup copy of a previous iteration and does not erase another user's local changes.

### Disabling Directory Access on the Apache2 Web Server

Another problem that I ran into during Lab 1A was that I had difficulty disabling the directory access. This was because I did not have my source folder specified in the settings file. This was a difficult bug to figure out because I had all of the settings inputted correctly, but the web server was not reflecting my changes. After browsing the help docs on Apache, I was able to discover that I needed to input the directory containing all my web files. After specifying this directory on the Amazon AWS server the directory view was successfully disabled. 

## Conclusions :

- Configure and run an Amazon AWS cloud server
- Install and configure a Docker container
- Install and configure an Apache2 web server
- Pass user entered data into a JSON string
- Create and design a web page
- Use a code repository tool to dynamically change source code

## References

- https://www.w3schools.com/css/css_specificity.asp
- https://www.csszengarden.com/
- https://www.w3schools.com/CSS/
- https://git-scm.com/docs/git
- https://httpd.apache.org/
