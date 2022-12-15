# JavaScript Projects Built with Puppeteer

Puppeteer is an open-source automation testing tool initially developed by Google in January 2018. Being open-source, developers all around the world can freely use Puppeteer, contribute to making it better, or even build branching projects from it. Today, developers are fast exploiting Puppeteer’s solid framework to create better tools in the automation testing space. 

In this article, we will discuss seven popular tools that use Puppeteer as its foundation for development. 


## What is Puppeteer?

Puppeteer is a Node.js library that controls Chrome and Chromium projects over the DevTool protocols. It uses a headless mode to automate processes on a website. By headless mode, we mean the driver does not require a GUI (head) to navigate to a website and interface with it.

Puppeteer is widely used for automation testing and web scraping. The tool is capable of performing pretty much any task a human can do with a mouse and keyboard. This makes Puppeteer great for UI testing as well.

Puppeteer is widely for activities such as automatically filling a form online, taking a screenshot of a page, tracking the price of a product on an e-commerce store, generating PDFs from web pages, and so on.


## Why Puppeteer is a Popular Option for Automation testing

There are a number of automation testing tools with Selenium being a long-standing champion. However, within less than five years, Puppeteer has distinguished itself as one of the go-to tools for UI testing, and web automation. Why is that? \
First, Puppeteer is relatively faster. Because it is headless, the browsers do not have to download the rendered graphics on a website. It rather accesses the webpage content right after the server has responded to the request. It can also send multiple requests to a website server in parallel. This means that you can run multiple test cases concurrently. 

Asides from that, Puppeteer is easy to use. Because it is based on the DevTools Protocol, it uses the same protocol as Chrome Developer Tools. Thus, if you have some knowledge of Chrome Developer Tools, getting up and running with Puppeteer would be easier.

Further to that, Puppeteer has a lot of helper functions for common tasks. For instance, you do not need to write from scratch a function that takes a screenshot of a webpage. Puppeteer has an inbuilt function for that. It has functions for navigating a URL, operating the mouse and keyboard, debugging, handling events, and so on.

Puppeteer also serves as the foundation for other projects. Here are some projects that were built on top of Puppeteer.


## Projects that Use Puppeteer



### 1. [Percollate](https://github.com/danburzo/percollate)

Percollate is a Node.js tool for converting web pages into beautiful PDFs, EPUBs, or HTML files. It can also properly handle figures, create customized tables and relevant bibliographies.

Percollate can combine multiple web pages into a PDF, customize page size, change font stacks, edit hyperlinks, perform customized pagination, and so on. 

Puppeteer is particularly used in Percollate to render PDFs given that Puppeteer has a helper function for converting webpages to PDFs. 



### 2. [WhatsApp-Web.js](https://github.com/pedroslopez/whatsapp-web.js)

WhatsApp-Web.js is an API built on Puppeteer to access the WhatsApp Web application programmatically. WhatsApp is quite strict with eliminating bots from their platform. Thus, automating WhatsApp web can be difficult. However, because Puppeteer has the ability to simulate the activities of humans (both with respect to mouse and keyboard), WhatsApp-Web.js can be used. The tool is however still not perfect.

WhatsApp-Web.js can be used for sending/receiving messages, sending/receiving media, joining a group, adding group members, reacting to a message, getting location, and many other actions on WhatsApp.



### 3. [Venom](https://github.com/orkestral/venom)

Venom claims to be the most complete JavaScript library for creating WhatsApp bots. It is a Puppeteer-based, open-source tool for interfacing with WhatsApp. It uses a RESTful API to transfer information between the client and server. Venom can be used with different programming languages such as PHP, Python, C#, etc. 

Puppeteer is applied in the Venom project for downloading files on WhatsApp. This is because it has robust functionality for converting web pages into PDFs. 



### 4. [Puppeteer Extra](https://github.com/berstend/puppeteer-extra/tree/master/packages/puppeteer-extra)

Puppeteer is a great tool on its own but still has its challenges. These challenges are what Puppeteer Extra seeks to solve. Puppeteer Extra is an extension of puppeteer for additional functionalities. It has several plugins for different applications. For instance, the Puppeteer Extra Plugin Stealth is an extra layer of security to avoid being detected as a bot. The Puppeteer Extra Plugin reCAPTCHA helps solve CAPTCHAs automatically. There is also the Puppeteer Extra Plugin AdBlocker that blocks ads while using Puppeteer. This significantly reduces the load times of web servers. Other plugins include the Puppeteer Extra Plugin REPL for debugging with an interactive REPL and Puppeteer Extra Anonymize UA for an anonymous user-agent experience.



### 5. [Puppeteer Web Perf](https://github.com/addyosmani/puppeteer-webperf)

Puppeteer Web Perf is a tool abstracted from Puppeteer but specifically for automating performance testing. It has the framework and metrics used to automate web performance measurement. It can get a performance trace for a page load or for user interaction. It can also measure the runtime performance metrics for a website and generate a report. Puppeteer Web Perf can as well emulate a slow network and CPU, measure memory links, block third-party domains, and many other performance testing operations.



### 6. [Screenshooteer](https://github.com/vladocar/screenshoteer) 

Screenshoteer is a simple tool based on Puppeteer used for getting screenshots of a webpage. It can take screenshots for both web and mobile emulations. Upon installing screenshoteer, getting a screenshot of a link requires a line of code in your terminal.

This tool is specifically relevant if you want to see how a web page is rendered without having to navigate there manually. Since Puppeteer is headless, requests are returned faster. This is one reason why Screenshoteer uses Puppeteer to power the project rather than Selenium which is not headless.



### 7. [Fake browser](https://github.com/kkoooqq/fakebrowser)

Although it is more difficult to detect Puppeteer as a bot, powerful platforms such as Google, Facebook, and WhatsApp can detect vanilla Puppeteer. A fake browser is a tool built on top of Puppeteer to make it undetectable. It tweaks some of Puppeteer’s properties and provides an easy-to-use API for a seamless bot operation.

The motion of the mouse and keyboard is one way to identify a human from a bot. Fake browsers simulate this movement using Puppeteer Extra and dumpDD.js. It then moves the mouse, clicks, and types as though it were a human. 


## Wrapping Up

Without a doubt, the vanilla puppeteer provides the framework for top-notch automation and testing processes. But it can get even better and easier. Since the tool is open-source, the tech community has used Puppeteer's framework as the foundation for other exciting projects. We have discussed seven in this article but the list is inexhaustive. Now, you can take advantage of other branch-offs of Puppeteer for your specific use case.