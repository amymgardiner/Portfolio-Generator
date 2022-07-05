## Node.js Portfolio Generator

For Module 9 of my coding bootcamp class, I built a program that creates an HTML portfolio page. In this module we learned about Node.js and used it to build a tool that uses the command line to capture and place user input in a JavaScript function that provides the finished HTML page as output.

# How to use this program

Because this is a Node.js application that runs from a machine and not a browser, I can't deploy this to GitHub pages. Instead, the user will need to clone it to their own local machine and run it from there, by entering node app into their command line and answers the prompted questions.

The final HTML and CSS pages will be created in the dist folder from the root directory.

# How the program works

The program starts by asking the user for their information with Inquirer prompts; this returns all of the data as an object in a Promise.

The promptProject() function captures the returning data from promptUser() and it recursively calls promptProject() for as many projects as the user wants to add. Each project will be pushed into a projects array in the collection of portfolio information, and when it's done, the final set of data is returned to the next .then().

The finished portfolio data object is returned as portfolioData and sent into the generatePage() function, which will return the finished HTML template code into pageHTML.

The program then passes pageHTML into the newly created writeFile() function, which returns a Promise. This is why it uses return here, so the Promise is returned into the next .then() method.

Upon a successful file creation, it takes the writeFileResponse object provided by the writeFile() function's resolve() execution to log it, and then it returns copyFile().

The Promise returned by copyFile() then lets the user know if the CSS file was copied correctly, and if so, they're all done!
