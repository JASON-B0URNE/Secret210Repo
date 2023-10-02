
## Introduction:
Samuel Brescia  
2 October 2023  
Lab 2

## Executive Summary:

Labs 1a and 1b implement HTML and CSS to generate and style a basic web page. Docker is used in order to deploy a local version of your application. The live version of the web application is deployed using Amazon AWS resources. 

### Web Page
![Example Screenshots](./Screenshot (152).png)

### Amazon AWS Instance
![Example Screenshots]("Screenshot (150).png")

### Apache Web Server
![Example Screenshots]("Screenshot (153).png")

### Docker Container
![Example Screenshots]("Screenshot (154).png")

### File Descriptions

* index.html - Provides the skeleton and content of the HTML page
* css/styles.css - Provides the styling for the HTML page
* js/scipt.js - Provides a script to show the submitted form in JSON format
* resources/bkg_pic.png - Background image for the website  
* resources/DroidobeshDepot-gxmVe.otf - Custom Star Wars font for the header.
* favicon.ico - CR2-D2 page icon

## Questions:

1. What is the purpose of using Docker containers?
  -

2. Why is it useful to have both a development environment and a live server enviornment?
  -

3. What is the purpose of using a code versioning tool (i.e. Git)?
  -

4. What is the difference between a CSS rule with an *element* selector (i.e. h1, p, div etc.) and one with a *class* selector (i.e. .task, .task-done etc.)? When would you use each?
  -

5. What are the advantages of putting your styles in a separate .css stylesheed instead of in the '<style>' element of '<head'?
  -

6. How do web browsers choose which CSS to use for an HTML element whe the CSS rules contradict each other? What is the order of precedence for CSS rules?
  -

7. Why should you disable directory access for your server?
  -

## Lessons Learned:

### JavaScript Comparisons  

JavaScript does extremely loose comparisons. Therefore if (thisVar == 0) will evaluate true if thisVar = 0 or null or “” or false. This problem often arises when doing an if statement where you want to check if something is not blank but 0 is a good value. To solve this problem use === or !==. These mean an exact comparison, not a loose comparison. Therefore if (thisVar === “”) and thisVar = 0 it will be false. On the other hand if (thisVar == “”) and thisVar = 0 it will evaluate true.

*There should be 3 lessons learned in your write-up, not just one.*

## Conclusions :

- Use nodejs to create an API
- Install packages using npm
- Create an SSL certificate
- Create firewall rules to allow traffic

## References

https://nodejs.org/docs/latest/api/  
https://certbot.eff.org/  
https://docs.aws.amazon.com/network-firewall/latest/developerguide/rule-groups.html
