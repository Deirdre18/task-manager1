# Introduction To The Mini Project

LESSON:

Hi and welcome to the Data Centric Design mini project.
My name is Brian O'Grady, and in this project, we're going to create a task manager application.
This task manager will be built using Flask, MongoDB, and a frontend framework called Materialize.
So what will we learn by building this application?
Well, we'll learn how to do create, read, update, and delete calls, otherwise known as CRUD calls, to a Mongo database.
And we'll do that in the context of a Flask application.
We will also create HTML based user interfaces to demonstrate these CRUD calls in action.
And in the spirit of good user experience, we'll style these interfaces using the Materialize framework.
Now let's look at the project we're going to build.
So the home page of our task manager application displays a summary of tasks.
And that summary information is comprised of the task name, the task due date, and a task description.
We can also edit a task, mark a task as complete, or add a new task on the home page.
The information required to create a new task is a task category; a task name; a task description; a task due date, in this case, provided by a calendar where we can specify months, years, and the day; and, finally, the last piece of information is determining whether it's urgent or not.
You can see here, there's our new task added.
You can also edit an existing task.
You might want to change the date or any of the other properties of this task.
Once you update, again, you're brought back to the home page.
And you can see the date has changed.
Now, a task is assigned a category.
And the application will provide you with the ability to edit, delete, and create new categories.
So for example, you might change arts to music.
You can see there that it's updated.
And when we go to create a new task, you can see that that new task category is available.
We can create a new category.
Notice that all our interfaces use the same visual theme.
We're consistent in our use of the Materialize framework.
Our application is responsive, which means it will respond appropriately to the device on which it's being displayed.
So now that we've had a look at it, let's go and build it.

# Database Creation

## What is it?

A new database

## What does it do?

It will store all the data we need for our task manager application

## How do you use it?

You provision a cloud-based database using mLab

LESSON:

When working with data-driven applications, it's always a good idea to start with the data.
Get your data in place first, and then build your application around it.
So with that in mind, we go over to mLab, and we create a new database.
And we'll create two collections.
Let's use the free tier.
In my case, I'm using Europe Ireland.
You use the closest edge server to you that would supply your data with the least amount of delay or latency.
Let's create a database name.
In this case, we're calling it task_manager.
And let's have a look at our setup.
So we're using Amazon.
I'm set up for Europe Ireland.
We have half a gigabyte of data storage, which should be more than enough.
We wait for it to build.
It's still in progress.
Okay, we're ready to go.
So let's click on this to add our collections.
Now, this string here will be the string that we'll use to connect to our MongoDB instance on mLab.
We'll connect to this from Flask using this string.
So let's add a new collection.
The first one we're going to add is a category, or categories.
You can see it has been added.
And then we'll add tasks.
These are our two collections that form the basis of our task manager application.
So let's add our first document.
Mongo is document-based as opposed to table-based, but there are similarities.
You'll recognize patterns.
So for example, we're going to create an entry, a JSON, or BSON when it comes to Mongo.
We're going to create an entry.
And that contains a key value pair called category name, and the value will be home.
Notice that MongoDB also provides an ID, which is similar to a primary key in a relational database.
So that's a valid document.
Then let's create a sample task.
Again, add new document.
Notice in this instance, we're creating the documents directly in the editor, rather than using command-line or terminal commands.
This is just to get us up and running.
One of the key value pairs that we add to a task document is a category name.
You could see that as a foreign key to tie it to the categories collection.
We also add additional properties.
Our task name, in this case, is purchase or buy detergent.
And now we add a task description.
Make sure you have your quotations around your key value pairs, and don't forget your colon as a separator.
We also add the is_urgent.
And because it's a Boolean, it'll be set to true or false.
That will come into play with our check box HTML element that we'll use in the Flask application.
We can also set a due date.
Now, only the task name, the description, and the due date appear in the tasks summary, but we're adding additional properties.
So you can use these and display them as a challenge.
Once you finish the project, you may want to do some sorting, for example.
Explore MongoDB and do some sorting based on a category, based on whether they are urgent or not.
And there we go.
Again, the ID is added.
We are ready, then, to build our Flask project upon this data.

# Create The Flask Application
 
## What is it?

A new Flask application

## What does it do?

It will form the basis of our Task Manager App

## How do you use it?

Use the Flask framework to easily and quickly connect database to our HTML based graphical user interfaces (GUIs) for task creation and editing

LESSON:

I've just created a new empty project in Cloud9.
Go and do that now, and pause the video before moving on.
Once you have that done, the first thing we're going to do is install Flask.
So we use sudo pip install flask.
And that sets us up with our Flask functionality ready to be imported.
The second thing we need to do is, because this is a blank application, we need to create a new Python file.
And in this case, we'll call it app.py.
The first thing we need to do is we need to import our Flask functionality in order to set up the application for use.
And then we create an instance of Flask, or a Flask app.
And we store it in the app variable here on line 3.
We do app = Flask(__name__)
And then we'll test.
We'll create a test function with a route in it that will display some text as a proof of concept.
Remember the '/' refers to the default route.
So in the spirit of tradition, we're calling this hello.
So we'll return a meta Hello World message, a variant on the Hello World message.
You've done this already before in Practical Python.
So let's call it Hello World again.
And once this is in place, we will then set up our IP address and our port number so that Cloud9 knows how to run and where to run our application.
In the next video, we'll deploy to Heroku, and we will assign the same values of IP address and port number.
In order to do this, we need the OS.
Now, inside our app.run() function, we set the host.
Again, we use the OS import here, we use the environ object, and then we get the IP.
Don't forget your comma.
And then we set the port.
And we convert the port to an integer.
Again, we'll use os.environ.
And we'll get the port.
Again, don't forget your comma because the last parameter we want to pass in is my debug.
We want to set that to true.
By setting it to true, it allows the changes to be picked up automatically in the browser.
And it'll also produce debug statements in the case of a bug.
So let's run it.
Now you can see that it's running on http://0.0.0.0:8080.
And we'll change those for Heroku later on.
And there we have it, a working Flask application.

# Deploy The Application To Heroku
 
# What is it?

A new Heroku application

# What does it do?

Heroku hosts complex web applications and services

# How do you use it?

Use the Heroku toolbelt that comes with Cloud 9 to easily deploy and maintain your flask application

## Commands used:

heroku git:remote -a task-manager-flask-mongo-1
set git remote heroku to https://git.heroku.com/task-manager-flask-mongo-1.git
dee2018:~/workspace (master) $ git push heroku master
git push heroku master
echo web: python app.py > Procfile 
heroku ps:scale web-1
sudo pip3 freeze --local > requirements.txt


LESSON:

Now let's head over to Heroku and create a corresponding app that we will use to deploy our carradine application.
Let's create an an app name. Remember, the app names must be unique.
And in my case, I'm choosing Europe as the edge server so that the delivery will be that bit quicker.
Our app is in place.
Next thing we do is we're going to log on.
And these are the sets of commands that are provided to help you on the way.
So let's log in to Heroku.
Again, enter your credentials.
Your email followed by your password.
What we are doing here is we're creating a connection between our Cloud9 application and Heroku that would allow us to push our changes using Git to update the application at any given time.
Check the apps.
You can see task-manager-flask-mongo is there.
Then, we create a new Git repository using git init.
And then what I'm going to do is add our files to the repository.
And then we're going to associate the Heroku application as our master branch, or remote master branch.
And here is a command that will allow us to do that back over in Heroku.
You can see Heroko's interface is quite useful and informative in helping you get set up.
It's set.
And then we want to push to Heroku.
It's failed because we don't have our requirements text file in place.
The requirements text will contain a list of the applications that are required for Heroku to run the application.
So in order to do that, we will create a requirements.txt file.
So our command is pseudo pip3 freeze --local > requirements.txt.
The > means add the requirements to a file called requirements.txt.
That's done.
Then we add our requirements file to Git.
Why? Well, to save it to a repository, but also to push it over to Heroku.
Don't forget your commit message.
Always have a meaningful commit message.
We're going to push to Heroku master.
We have "Warning: Your application is missing a Procfile".
You can see that message appears there as part of the push message.
And the Procfile is an instruction to Heroku as to which file is used as our entry point at the application, which file we use to call the application to get it up and running.
So we'll specify that now using echo web Python.
We're specifying that it's a Python file.
And the name of it is app.py, which matches the name of the Python file that we manually created.
And we'll send that information into a file called Procfile.
Remember, there's no extension on Procfile.
Then we'll add the Procfile to GitHub.
Again, add a new message that reflects as accurately as you can the reason for that commit.
Pushing to master.
Now you can see that the Python app was detected.
It's pushing the contents over.
That looks like a healthy push.
And the next thing we want to do is we want to run our application.
So this is a command over to the Heroku app to tell it to get up and running.
You can see scaling Dinos done.
You see our interface here. We're going to go to settings.
And we need to specify our IP and our port.
You remember we set those in the last video.
We need to set those on Heroku so that the server instance on Heroku will know how to run our Flask application.
So our IP address is 0.0.0.0
And our port is 5000.
Open the app.
And there we go.
We're good to go.
Successfully deployed.

# Connect Flask To MongoDB
 
## What is it?

A working connection between your application and your database

## What does it do?

It allows your application to programmatically perform CRUD actions on your database (e.g. so your application can read in your data)

## How do you use it?

## Commands used:

sudo pip3 install flask_pymongo

LESSON:

At this point, we have our basic Flask application in place.
We've also created a corresponding application in Heroku, and we've connected to Heroku.
We created a Git repository, and we're pushing to Heroku.
Now let's wire up our database to our Flask application.
So to do that, we need a password and a username for our link to the Mongo database on mLab.
And in this instance, I'm using admin for the password and the username.
Just a piece of advice: never use a combination of admin admin for username and password.
It is the most hackable username and password combination out there when it comes to databases
Put something more useful and cryptic in place.
To get Flask talking to Mongo, we're going to install a third party library called flask-pymongo.
And it's just slightly different from the pymongo you would have used in an earlier lesson in the sense that it's optimized to work with Flask.
So we've installed.
And now we're going to add some additional imports to reflect that installation.
So we're going to access the library here.
And we're going to import pymongo from flask_pymongo.
And then we want to add some configuration to our Flask application.
So we're going to add the Mongo database name and the URL linking to that database.
So let's add the MONGO_URL.
Let's go and get our Mongo database URL
Paste it in between strings.
And let's grab the database name from the end of that string.
Sometimes it's a good idea just to copy and paste to make sure you don't introduce a typo.
This is failing.
It's because the app itself needs to be created first.
So I was attempting to refer to an app before it had been created.
Now we're going to create an instance of pymongo.
And let's add the app into that with what's called a constructor method.
We need to change the spelling of PyMongo to uppercase M as well for that to work.
Now we're set up to make our connection to the database.
So in order to do that, we create a function with a decorator that includes a route to that function.
Remember, the routing is a string that, when attached to a URL, will redirect to a particular function in a Flask application.
In fact, you can see something very similar in the Django applications that you'll work with later.
So in our case, we're using a string called get_tasks.
And we're creating a function with that decorator, and that decorator is inside app.route.
Our function is called get_tasks.
Now we're going to use some additional functionality from Flask as well.
We're going to use the render_template() function.
We're going to use a redirect.
We're going to access a request object.
And we're going to use the url_for() function.
And we'll see those used throughout the project.
Notice we have two decorators. We have a '/' and a string with get_tasks.
So when the application is run, then the default function that will be called would be get_tasks because of the single '/' decorator that route is in place.
So when get_tasks is called, we will render a template.
In other words, it will redirect to an existing template.
In our case, it is called tasks.html.
And we'll also supply a tasks collection.
That collection will be returned from making a call directly to Mongo.
So we use mongo.db.tasks.
That's our collection.
And we use the find() function to return all tasks in that collection.
So the next thing we need to do is to create a template.
And you'll remember that the templates in a Flask application are placed inside a templates directory.
The spelling is important as well because Flask will look for a directory called templates for the HTML based files.
So we create a file called tasks.html.
And for the moment, we'll create a full HTML document in this file.
Later, we'll refactor this so that it inherits from a parent template.
So in order to access our collection, we need to loop through it.
So we use the jinja for loop looping mechanism to iterate through a collection.
So in our case, it's {% for task in tasks %}.
So tasks is the collection passed back, and task represents each entry, or each record, in that collection, or in our case, each document in that collection.
We can then refer to and access each property, each key/value pair, inside that document.
The first one we access is task name.
So you refer to the object. followed by the key for that value inside the object.
So task name, category name, task description.
Notice also that when you're accessing individual data items in a jinja template, the data is wrapped inside double curly braces, not single.
You use {% %} to represent blocks, if statements, or looping mechanisms.
But when you want to access data directly, individual data items, or variables, you would put place them inside double sets of curly braces.
Let's close our for loop.
We'll re-run the program, and do some testing.
There's a missing slash inside the decorator for get_tasks.
Let's fix that now.
Run again.
That looks better.
And there we have it.
We've successfully connected to a Mongo database, we've brought the data back into a Flask application, and displayed it out onto a template.
So we're good to go!

# Template Inheritance
 
## What is it?

Parent and child HTML templates

## What does it do?

The child template inherits HTML code from the parent template. This follows the philosophy of 'DRY - Don't Repeat Yourself' as templating helps you avoid duplication

## How do you use it?

You use jinja blocks to inject content e.g. 
{% block content %} *Insert content here* {% endblock %}

LESSON:

# Template Inheritance
 
## What is it?

Parent and child HTML templates

## What does it do?

The child template inherits HTML code from the parent template. This follows the philosophy of 'DRY - Don't Repeat Yourself' as templating helps you avoid duplication

## How do you use it?

You use jinja blocks to inject content e.g. 
{% block content %} *Insert content here* {% endblock %}

LESSON:

We now have our Mongo database wired up to the Flask application, and we are in a position now where our documents are displaying on the screen via the template, although we only have one documented at this point.
So let's do a little bit of refractoring.
And what we're going to do is we're going to create a parent template for all of our views, or our templates (i.e. the HTML files).
And to do that, we're creating a new file called base.html.
And that document, or that web page, will contain our references to our JavaScript, our CSS, and our third-party libraries that we'll use across the application.
Now, there will be exceptions to this as well wherever we need to add specific functionality to a child template.
We will add that there as well.
But in general, this acts as a one-stop shop that neatly provides access and visibility to our JavaScript files, our CSS, and our navigation.
The point of the template is that you don't have to repeat yourself.
That is a philosophy within framework development: DRY, don't repeat yourself.
And in order to inject the child content, we create an opening and a block tag.
And the block keyword is required, but in this example, we see the word content, or the string content.
You can use other names for that.
It's a convention to use the word content, but you can use others.
And we'll see how that works in a few moments.
But I've also added a <h1> tag outside, just to prove that we can see material, markup, or functionality outside the child tags and within the parent tag.
So for the child tag to inherit correctly from the parent, we remove the HTML elements, e.g. HTML, the body, the head, and HTML tags themselves.
And we replace that with another jinja block.
So we use the extends keyword followed by the name of the parent template from which we want to inherit and that we want to inject into.
And then we specify the data that will be injected into the parent.
So in order to do that, we repeat the syntax.
Again, this {% block content %}
And then we close it with an end block.
If we don't specify the word content in this case, it won't be displayed because the parent is looking for that.
It's looking for content or data within a block that has that identifier.
So content is just an identifier for that particular block.
We run it, and you can see Outside!
The mark-up has been merged, so the parent template is displaying Outside!, and the child template is displaying the record retrieved from the database.
And this is all achieved using the block tags.
So you have an opening and a closing tag.
Let's change our keyword content to something else.
For example, let's call it stuff.
We change it here.
We run it.
This is to see our content.
So the keyword content, or the identifier, is a convention.
But you must be consistent in the parent and the child elements.
In this case, we changed one back to content and left the other as stuff, and it failed.
So it silently fails there.
Just keep an eye out for those kind of errors.
They won't show up as code failures, but they can be frustrating.
Here we go!
So there we have it.
Our parent child template is in place.

# Materialize Setup
 
## What is it?

Materialize front-end framework

## What does it do?

A modern front-end framework (similar to Bootstrap) that helps you build a stylish and responsive application

## How do you use it?

You reference the relevant Materialize CDNs in your parent template (i.e. base.html)

Important! You will use Materialize version 0.100.2 for these lessons.
Copy and paste the CSS link below into your projects when you need to get set up with Materialize.
 <link rel="stylesheet"  href="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.100.2/css/materialize.min.css">
Please do not install version 1 at this time as it will only cause confusion, break your code, and make you sad.

LESSON:

We now live in a time where people have a visual expectation when interacting with apps.
Not only should something function, it should be beautiful wherever possible, or at least it should be intuitive and effective.
Now intuitive also means first-time learning.
So in order to provide that or promote that form of ease-of-use and intuition, we're going to use a library called Materialize.
Materialize is based on the material design philosophy developed in 2014 by Google.
It was originally based around the card motif, but material design now makes more liberal use of grid-based layouts, responsive animations, transitions, padding, and depth effects, such as lighting and shadows.
Materialize.CSS does a great job of providing you with pre-built functionality that does just that.
So it's a small-ish, very useful library that we're going to use to style our access, our create, read, update, and delete mechanisms, and database access functionality.
Throughout this, we'll also be cutting and pasting, or copying and pasting, chunks of pre-written HTML to help us on our way because the focus really is on accessing MongoDB.
But at the same time, it's always better to present your functionality to a user in the most intuitive way possible that promotes a positive user experience on behalf of the user.
You can see here the text being used, forms, and so on.
The interactions are visually very appealing.
It also makes use of the material icons provided by Google, but you can use other icon sets, such as Font Awesome, if you wish.
We'll be using this nav bar later on in a couple of units time towards the end of the project.
Here's an example of drop downs, the options.
Materialize does depend on jQuery as of this particular iteration, but there is a new version coming out that doesn't depend on jQuery.
And jQuery allows the communication with the document object model, the DOM, which you'll have explored in more depth on the frontend modules of the program.
You can also access the links for these via a Content Delivery Network, CDN.
And we'll place those in our parent template.
Why?
Because by placing these links in the parent template, they can be accessed within the child templates and the functionality within the child elements themselves.
As we just mentioned, Materialize is dependent on jQuery, so we need to grab a jQuery link as well to link to a jQuery Content Delivery Network.
Now, you place the jQuery before the Materialize in the head because jQuery needs to be active before Materialize uses that functionality.
Here are the Materialize icons.
The icon set isn't quite as rich as, say, Font Awesome yet, but it's quite useful for our purposes.
So then we need to take the jQuery and place it at the bottom.
Again, it's just a good practice to put your jQuery at the bottom of the <body> element because that way you can ensure that the HTML elements have been fully rendered before any JavaScript activity or functions target those elements that have been rendered.
We also use a Materialize JavaScript import as well.
And we're good to go!
We're good to start styling.

Links From The Video
Materialize Docs

Materialize CDN for compiled and minified CSS:

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.100.2/css/materialize.min.css">

Materialize CDN for compiled and minified JS:

<script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.100.2/js/materialize.min.js"></script>
View Source Code

# Accordion Setup
 
## What is it?

A Materialize component

## What does it do?

It provides an accordion-style feature which expands and contracts when you click on an element. It is commonly used to show and hide more detailed information about a topic

## How do you use it?

You include the source code for the component named 'Collapsible HTML Structure' in your HTML file

LESSON:

At this point, we have our Materialize imports, our CDN links, our external links, to CSS in place.
We also have our JavaScript, we have our jQuery, and we have our icons in place.
So now let's use one of the components.
And we're going to use what Materialize calls collapsible, which is just a custom name for an accordion.
An accordion expands and contracts when you click on elements of that, so it reveals more detailed information.
And we're using that to display our tasks.

So in the accordion header, or the collapsible header, we'll see the task name and the due date.
And once expanded, we will display the description associated with that task.
As a challenge, you can go further and display more information, such as is if the task is urgent and also the category of that task.
But for now, we're going to keep it simple.
We're going to display the task name, the task due date, and, when expanded, that accordion node will display the task description.
So we copy and paste.
And for now, we will paste it within the block tags.
Remember, if you paste it outside of the block tag, it won't be displayed when the parent and child templates render.
So let's just copy it and paste as is.
And we can see our collapsible elements are in place.
Now, they're not firing yet because they need a bit of JavaScript to initialize it.
So we use the jQuery document.ready() function.
So this function will be called when the document is ready.
That means when all the elements, the HTML elements, have rendered.
So we'll place this in the base.html in the parent template so that any collapsible elements can access this functionality when they're being rendered.
Do a refresh.
And there we go.
So we now have our accordion in place.
What we'll do next is we will dynamically add tasks to those accordion elements.

# Accordion Task Data Binding

## What is it?

Binding data from our database to our accordion feature

## What does it do?

It creates a collapsible header for every task in the database. The collapsible header will display the task name and when a user clicks on it they will be able to view the task description

## How do you use it?

You dynamically generate a list item for every document (i.e. a task) returned from the database

LESSON:

We now have our accordions in place.
And the accordions contain sample data, such as some lorem ipsum and so on.
We're going to replace that with some actual dynamically generated data from the database.
Now in this case, we only have one record, but that will build over time.
So an accordion is really a stylized unordered list with list items.
So what we're going to do is we're going to dynamically generate a list item in a list for every record returned, or every document returned, from the database.
We use a for loop.
Again, for task in tasks.
So we can reuse the jinja functionality that we created earlier.
And we're going to wrap a list item in the for loop.
What we're getting there is a kind of conditional rendering.
You'll get an instance of a list item for every record represented in the database or that's returned based on a particular search.
And for each instance, we will display the task name.
Beside that, we will display the task header.
So these will appear in the collapsible header, or the accordion header.
And when you expand the accordion element, we have a div and a span.
And let's replace the lorem ipsum with the task description.
This conditional rendering is quite common across all templated frameworks.
Angular uses it, React can use it, Vue can use this, Django can use this.
So once you get a sense of one of the frameworks, it's very easy to transition to another framework type.
There we go, Buy Detergent.
Now notice the icon on the site doesn't really suit.
It's a cloud, so we'll create a custom one.
And what we're going to look for is an icon that gives a visual clue to the user that more information is available and that if they expand, they'll see a task description.
So we're going to go to material icons.
And we're going to search for an appropriate icon.
You can see there that the icons are broken into different categories.
As I mentioned in an earlier video, it's not as rich as Font Awesome, but it's still pretty comprehensive.
We're looking for an expand icon.
Notice that these icons are represented in an <i> tag, which used to be italics.
Italics is no longer the preferred way of representing italicized text.
We use em for emphasis now.
So that's why this slightly deprecated tag has become commonly used with icons.
So it's no longer i for italics.
It's i for icon.
We've swapped it in.
The user now is given a visual clue as to the fact that there is more information available if they click on this element.
Last thing we'll do, then, is we'll make it strong so that the task name is more emphasized.
And there we go. We have our task list.

# Add Categories To MongoDB
 
## What is it?

A category is a document that consists of a key : value pair e.g. "category_name" : "work"

## What does it do?

Categories can be used to group similar or related tasks

## How do you use it?

By adding a new document to your database for each new category

LESSON:

Now let's go back to mLab and create some additional categories.
And you can see there that the category really is made up of a key value pair of category name and whatever key we associate with that.
So go into create document.
Change "category_name" from "Home" to "Work".
And when we save it, we see that MongoDB gives us the auto-generated ID.
Again, you can see this as similar to a primary key in a relational database.
Let's add another category.
This time I'll call it music.
Create task and go back.
And we see a list of our categories.
So now we have multiple categories available to us to play around with over in Flask.

# Add Task Form Boilerplate
 
## What is it?

A boilerplate or skeleton form written in HTML

## What does it do?

The completed form will allow application users to add a new task. The boilerplate form is the HTML code required to generate the form

## How do you use it?

By creating a skeleton form in a new file called 'addtask.html'

LESSON:

As a reminder, CRUD stands for Create, Read, Update, and Delete.
They're the primary actions that you'll undertake when interacting with the database.
So in our last video, we used the read functionality where we did a find, and we read back all tasks.
Now we're going to use c for create.
So we're going to create data.
We're going to put the user interface elements in place that will allow us to add a new task.
So the first thing we do is we create a new HTML file called addtask.html.
And as with our earlier video, we will create this as a child template of base.html.
So you can see again, we use the extends keyword followed by the name of the HTML page, which is base.
And we put it into {% block content %}, so we'll inject this into {% block content %} when this view is being rendered.
And we're going to keep it simple for now. All we're adding is a <h3>.
And let's get rid of the old test function that we used at the beginning of the project.
We're going to create a new function.
And this function is going to be called add_task().
It's singular rather than plural. You'll add one task at a time.
In order to do that, we create a decorator with a route called '/add_task'.
And we create a function with the same name.
You don't have to do this.
You can have your routing identifier can be different than the function name if you want to conceal things like that and make them less obvious.
You don't have to do that, but when you're starting off, it's easier to create a function name with the same name as our task.
There we go.
This function works.
It redirected to the addtask.html page.
What we're going to do now is we're going to use a form because when you want to add a task, the easiest way to do this is to create a HTML form that the user can fill in form elements and submit the form to the server.
So we're going to use Materialize form elements.
They're quite elegant, and they conform to good UX as well.
We're going to use a form with icon prefixes.
We'll modify the prefixes to reflect the data that we expect to be filled into these fields in the form.
Again, just like the tasks template, we will copy and paste in a form element as well.
We'll be using text areas in our forms.
We'll also be using a select.
And we use our select for categories.
The categories that we created in MongoDB in the last video will eventually populate the select element with these options.
I'm just showing you here that there are different ways, there are more stylized ways, of representing the selects as well.
So let's grab our sample form.
And we'll paste that into our add_tasks.
Now remember, it must be inside in the {% endblock %}, between the {% block content %} and {% endblock %}.
Now notice here, similar to the Bootstrap you would have used in earlier lessons, Materialize uses the grid system.
So a grid system is based on on 12 columns.
It's a 12 column grid system.
So you can see that in our divs for each element there, we have two fields.
One uses an s6, and the second uses an s6 as well.
One of the input fields takes up six columns, and the second one takes up six columns as well.
You'll play with those to align them in a way that suits you.
We've saved our changes, so we now run our code.
We can see that we are redirected to the add task page.
And we do have two input fields in a form.
Now, we've no way of submitting it yet, and we don't have our actual data in place.
We'll do that next.

# Add Task Form Input Fields
 
## What is it?

Input fields

## What does it do?

Input fields that will ask users for details of the new task

## How do you use it?

You use the input element

LESSON:

At this point, we have a sample form with two fields.
Let's change the column size of each field from six to 12 so that each form field will take up the full width of the page.
There we have it.
Notice our form has got our input text, a label, and an image.
You can see that each one of those elements is wrapped within a div.
And it's the custom class input field, which provides the styling for those.
You'll become more familiar with those as we go through the project.
But let's change the type, type="text", which is given an ID and a name because we want to target these.
We also want to submit these as values of the database, and the easiest way to do that is to match the names for these input fields to the names of the fields in MongoDB.
We'll also change the icons to reflect the kind of information we expect.
So we change the icon to assignment, we change the label to Task Name, and then we move on to the second input field.
We set the name to task_description, again, to match the value of the document property over in MongoDB.
We set the ID to task_description as well.
And we give it some custom classes as provided by Materialize.
Let's change the label for our input field.
We will change it from telephone to Task Description.
The task description is a text area.
Let's change our icon to subject.
Let's see what it looks like.
Refresh.
The text area is off.
We need to use the html5 text area as our element.
Let's close this off and save.
And there we go!
Now you might be wondering what's that green little icon in the bottom right hand corner of the text area.
That's just a grammerly plug-in that I use on Chrome, so don't expect to see that there when you build your own.
Now we're going to split each input field into its own row.
You don't necessarily need to do this because a column width of 12 will occupy the maximum width within a row, and the elements will naturallyk display beneath each other.
But if you do want to add extra elements within that row and play around with the column widths of those elements within the row, then this is a good start.
So we have our task name.
We have our task description.
The next thing we're going to do is we're going to add a checkbox.
Materialize calls them switches, which is a styled checkbox that looks interesting.
It pops a little bit more than a standard checkbox.
So let's pop that in here.
Clean up the formatting in the layout.
Let's take a look at it.
So we've got off and on.
We only want one label.
We only want is urgent.
And we'd like to display it on the right of the checkbox.
So remove the off.
And we change on to is urgent.
And there we go.
By the way, checkboxes will only submit as form data if they're checked.
Let's give it an ID and a name.
The ID is urgent, and we'll give it the name as is urgent as well.
It's common enough to match the name and the IDs of form elements, or form input fields and formats.
Next thing we're going to do is we're going to add a date picker.
And why use the date picker?
Again, to create a good user experience for the users.
A date picker allows the user to choose a date in a way that is formatted in an acceptable way for the database.
If we were to allow free text, if we were to allow the user just to type in dates, well, we could have all different formats.
We could have US, we could have non-US, European date formats, and so on.
Databases really hate poorly formatted date strings.
So by using a date picker, the only interaction that a user can have with the date is to select a date from a calendar item.
So let's add our date picker.
So the info type is text, but the class itself is date picker.
Materialize's CSS file will recognize and target that accordingly.
Let's change the icon to today.
And it just shows a little calendar icon.
Again, change the ID and the names to due_date.
And they'll match the MongoDB fields, the key value pairs.
And then change the label to Due Date.
We will also need a bit of jQuery to fire or to trigger the display of the calendar.
You can settle for the default values here, but you could customize them as you see fit.
So let's copy this jQuery.
And we'll put it in our parent template, in base.
That way, all date pickers that we choose to include can be accessed by this trigger function.
There you have it!
We still need to add a select to display the options for the categories.
We also need to add a submit button to submit the form.
And we need to add the corresponding Python functionality to take that form content and insert our form data as a new document into our Mongo DB database.

# Allow Task Category Selection
 
## What is it?

A select element

## What does it do?

An element which will allow a user to select a category from a list of options

## How do you use it?

You use a combination of a single select element that contains multiple option elements (i.e. one option for each category)

LESSON:

Our form is getting closer and closer to being complete.
What we need to do next is we need to add a select element, which will allow us to choose from the different categories of tasks.
So let's go back to Materialize and choose a select component.
You can see here the different options that Materialize gives you out-of-the-box.
You can have multiple select, and you can have dividers across select categories.
Let's grab a single select option now.
And we're going to drop that into our form as a test.
Before we go any further, let's wrap it in a row, so it will behave and display correctly.
You can see when we copied across the code, it already had a class of input-field, which styles it in that in that Materialize form style, and by default, it has a col setting of s12.
Let's do a refresh here.
We need some jQuery to initialize this.
And here it is.
It must be placed within a document.ready() function.
Now you remember we already have a ready function for the document element in place, so all we really need is the material_select() function.
So let's go back to our base.html and paste it in below our call to the collapsible function.
Save and do a refresh.
And then we'll test again.
Our next step is to wire up the data from our categories collection in MongoDB and dynamically generate an option instance for each category document we have in our collection.
Let's change our icon prefix to pole.
It gives the impression of categories.
You see them in a bar chart there, roughly representing different categories of tasks.
Let's change our label to task category.
And then we'll modify our options.
Now, we keep the first option.
That will be outside our loop because we want a disabled selected element to be displayed.
And in our case, it'll be choose category.
That will be our first option, and it'll always be there, but it won't be selectable, as it's only a visual clue as to what's expected from the user.
You can see there it's commented out, and the rest are displayed.
We're going to dynamically display our options.
So we will need to bind our category data.
But first, let's clean up our select, give it an ID, and give it a name for our form when this eventually is submitted.
Let's then go back to add_task.
Initially, add_task just redirected to the addtask.html.
Now, the naming can be a little bit confusing.
add_task just means display the add task page.
When we want to add a task to the database, we will have a function called insert_task.
These are our categories. We can see that there's home, work, and music.
And we've used Mongo.
You use the find function with MongoDB to fetch our categories.
And we're passing that back in a categories parameter.
So as I mentioned, we only need one option here.
We need one option in addition to the one that's disabled and selected.
But we only need to display one option inside our for loop because, remember, using a for loop in these templated languages allows us to have conditional rendering.
So what that means is the option HTML segment there will be displayed for each instance of a category in the collection itself.
So we have conditional rendering.
If we have four categories, we will have four options. If we have 10 categories, we'll have 10 options, and so on.
We'll use the option value. We'll set the value to the category name.
And we will use the same piece of data to display the category in its listing.
But the value behind the scenes is the data that will be submitted to the form, and not what the user will see.
There we have it.
Home, work and music.
So it's looking good.
We've added a new select, we've bound it using the categories, we've wrapped it inside a for loop, and we are binding the category name to the option value and the display within the option.
Next thing we need to do, then, is add a submit button and the associated insert function over in Flask.
And we will be able to add a new task.

As a reminder, CRUD stands for Create, Read, Update, and Delete. Now we're going to use c for create. So we're going to create data. We're going to put the user interface elements in place that will allow us to add a new task. And we put it into {% block content %}, so we'll inject this into {% block content %} when this view is being rendered. H3 heading 'Add Tasks'. What we're going to do now is we're going to use a form because when you want to add a task, the easiest way to do this is to create a HTML form that the user can fill in form elements and submit the form to the server. Again, just like the tasks template, we will copy and paste in a form element as well. We'll be using text areas in our forms. We'll also be using a select. And we use our select for categories. The categories that we created in MongoDB in the last video will eventually populate the select element with these options. I'm just showing you here that there are different ways, there are more Submit Add Task Form Data

What is it?

# A submit button


## What does it do?

It will allow the user to submit the form (and save the new task to the database)

## How do you use it?

You create a JavaScript event that will run the insert_task() function when the user clicks the submit button

LESSON:

We're nearly at the point where we can submit a new task.
By the way, once we do this we can reuse this approach as a template for editing tasks and also adding and editing categories later.
The last thing we need is a button.
So we go back to Materialize, and we grab some button markup.
You can see here, the button has an associated icon, as well.
Convention has it that the button goes in at the end of the form because you fill in your form elements, you scan them, you view them, and, once you're happy, you submit.
Let's put our button inside here.
Now, the form is clever enough to recognize when the submit button is being clicked.
And its response to that button being clicked is to submit to a location.
In our case, we will specify the name of a function.
Let's just check it here. We can see add task.
We get method not allowed because we haven't specified the function, or the method, that we will use to respond to that form being submitted.
So let's go back to our app.py, and let's create a new function.
This function will be called insert_task.
Now, because we're submitting a form, and we're submitting using POST, we must refer to the HTTP method that will be used to deliver the form data.
In our case, it's POST, so we specify POST here.
The default is GET.
It's only when you use POST as the submission format on your form that you must specify the method as POST in your function.
We go back to Mongo, we get the tasks collection, and then we do a task_insert.
We do insert_one.
What we insert is the request.
Remember, whenever you submit information to a URI or to some web location, it is submitted in the form of a request object.
We grab that request object.
And inside that, we say show me the form.
And we're converting that form, in our case, to a dictionary, so it can easily be understood by Mongo.
Any of the form fields that have data inside them, or are active, will be submitted as part of the form submission, and ultimately, we'll go on to create a new document in our tasks collection.
In reality, you'll probably want to do some validation, both on the HTML side and inside here for required fields.
But for our purposes now, for simplicity, we will just send the entire form.
Once that's done, we redirect to get_tasks, so we can view that new task in our collection.
It's just good practice.
Let's go back over to form and specify our insert_tasks function inside our action attribute as the value for that action attribute.
So url_for.
Remember, that is saying find the URL, or use the URL, for a function called insert_task.
Our insert_task is singular because you want to insert one at a time.
There's our method. It's POST.
That's why we used the POST configuration.
Let's test.
I've got our category, our task name, our description.
Let's choose a due date and specify that this task is urgent.
Click on add task, and this updates the database.
We return to get tasks, and we can see the new task.
So it looks good.
Let's just verify this over in mLab.
We can see that the new task should be there, and there it is.
So we have our core functionality in place, and we will reuse this.

# Adding Static Files
 
## What is it?

A directory called 'static'

## What does it do?

A directory that holds static files i.e. files that don't change that often such as CSS files, custom JavaScript, images and so on

## How do you use it?

You include a route to your static folder and file in your 'base.html' file like so:

<link rel="stylesheet" href="{{url_for('static', filename='css/style.css')}}" type="text/css"/>
Walkthrough
 
LESSON:

Now in addition to importing third-party libraries, JavaScript and CSS libraries, we're going to apply our own custom styles to our buttons.
So in order to do that, we set up a static directory, as is required with Flask, and Django as well by the way.
Again, it follows the same rules as the templates directory.
It must be spelled with a lowercase s.
And inside there, that's where we store what are called our static assets, assets that don't change that often, such as CSS files, custom JavaScript, images, and so on.
So inside there, we create a CSS directory, and a file called style.css.
A little trick that I like to use when checking whether a style is being targeted correctly is to use something, a garish background color for example.
And in this case, we're going to set the background to red.
And if it works, you'll know about it straightaway.
There's no subtlety in having a red background color.
We refer to our stylesheet.
And in our url_for, we refer to the static directory.
And the file itself will be css/style.css.
Save that.
Just make sure that's in place.
Refresh.
There we go, a red background.
We're going to comment that out.
Let's do a refresh.
You see here in this example, it didn't refresh.
Ykou can clear your browsing data, or you can run your code in an incognito view of the browser, and that doesn't cache your styles.
And there we go.
We're ready to go. We're ready to style our custom buttons.

# Adding Edit And Done Task Buttons
 
## What is it?

Edit and Done buttons

## What does it do?

The buttons will provide a link to a form where a user can edit a task or mark it as done

## How do you use it?

You create anchor elements in your HTML and then style those elements as buttons using CSS

LESSON:

We'd like the ability to edit a task or mark a task as complete on our task list, on the accordion of tasks.
Let's do that now.
Currently, we have the accordion expanding elements.
Beside the expand chevron, we'd like to be able to give the user the option to mark a task as complete or mark it for editing.
Let's create a div, and we are going to add some buttons into this.
We're going to use the grid system to allot a certain number of columns for the buttons and a certain number of columns for the description of the task and its due date.
So in the first column grouping, which will be three columns wide, we will add our expand more.
And in the second grouping, we will add the task name and the task due date.
Inside there, we're also going to add some buttons.
Just do a check once you do an edit.
Once you move or play around with your code, just do a check just to make sure that the layout is still as you'd expect.
Then we go back to buttons.
And instead of a submit button, we just use a style button here, which is really a link.
It's an anchor that has been styled.
We're going to grab that styled component, and you use it for submitting a task and also editing a task.
We'll call one edit, and we'll call the other one done.
So task done and edit.
Save our changes and view.
And you can see there, the buttons are quite bulky.
And that's as small as they they come out of the box, unless we apply custom styles.
That's why we created our static directory with our styles in the last video, so we can make them more presentable.
So let's now go to our style.css.
Let's create a class called btn.small.
We'll give it a height of 24px.
We'll give it a width of 60px.
We'll give it a line height, again, of 24px.
And let's give it some margin.
We give it some margin to give it some breathing space.
It's actually to push each button away from each other.
So left, right, top, and bottom will be 5px.
So as a result, there will be a 10px distance between each button.
Let me give it some padding.
Let's get rid of our test style.
Ignore the warning there. It's just advice.
Let's paste in the style name.
Let's see if it works. Do a refresh, and you can see, there it is. It's working.
We'd also like to change the colors, again, to provide as much visual clues as you can to the user.
We can use default colors that are provided by Materialize.
Of course, these can all be overridden and customized in your own styles, but for simplicity, we'll just use blue for edit, and we'll leave green for done, which is the default.
We're also going to provide some custom styling for our task header, which currently contains the task name and the due date.
When it's 5px margin-top, that's to align it with the buttons because it's slightly off.
It's slightly above center with the buttons themselves.
Do a refresh.
That should be better.
You can also see here that because of the use of columns, the 3 and the 9, we get a nice responsive display on a smaller form factor, such as a mobile device.
Finally, let's wrap our content in a container.
And just as with Bootstrap, Materialize uses a container.
If you wrap the outermost div in a container, it makes more presentable.

# Wire Up Task Edit Button
 
## What is it?

A button called Edit task and a function called edit_task()

## What does it do?

When a user clicks the Edit task button, the edit_task() will run. This function will rprovide the user with a form to edit the task

## How do you use it?

You create your edit_task() function in app.py and wire this up to your Edit task button

Important! There is a bug in the video
In this video, a copy of the addtask.html file is used to create the edittask.html page. However, the action attribute of the form isn't updated so it still points to the insert_task view instead of the update_task.
Copy and paste the opening form tag from below into your projects instead of the existing opening form tag in the edittask.html code.
 <form action="{{ url_for('update_task') }}" method="POST" class="col s12">
Walkthrough
 
LESSON: 

Now that we have our done and edit buttons in place, let's wire them up.
We're going to wire up the edit button first.
And we're going to create a corresponding function in our app.py that will react to the edit button being clicked.
When we say that we want to edit a task, what we mean is we want to edit the properties associated with that task.
It might be the task name, we might want to change the due date, a description, it may no longer be urgent, and so on.
So in order to do that, we want to display the task on an editable form.
In order to do that, we need to retrieve that task from the database.
And a guaranteed way of targeting the task we're looking for is to use its ID, which is similar to its primary key in a relational database.
You can see that our edit_task() function receives the task ID as part of its routing parameter.
And in order to work with this parameter and find a match in MongoDB, we must convert that to a BSON data type.
As per usual with Python, there's a library that we can use to import specifically for this purpose.
So we're going to use bson.objectid.
And we'll use that to convert the ID that's been passed across from our template into a readable format that's acceptable by MongoDB.
So let's set up our function.
So what we're doing here is ultimately we're fetching the task that matches this task ID.
And we'll eventually redirect it to an edit task HTML template that I'll put together in a few moments.
So we want to find one particular task from our tasks collection.
And the parameter we'll pass is the ID.
So we're looking for a match for the ID, and you must use "_id" because that's the key in our Mongo document.
And we wrap our task_id that's passed in as a parameter into edit_tasks.
And we wrap that in an object, and we cast that to a format that's acceptable to MongoDB.
The second thing we need is a list of the collections because we're going to use the task that's returned from MongoDB and all the categories in order to populate a form for editing.
And we're going to reuse much of the layout of our add_task form for the editing.
But the difference now is instead of having empty fields such as description task, name, due date, and, for example, is urgent, they'll be pre-populated based on the information returned in the task.
As will the category names be populated based on the collection of categories returned in the all categories cursor.
It has passed the task back and the categories to our edittask.html, which I will create for us in a moment.
Now I've just added an edittask.html page, and I've copied and pasted the contents of add_task into this.
First thing I need to do is change our heading from Add Task to Edit Task.
We can see we reuse the extends and so on.
And then we'll add a link that when clicked, will take us to this new edit task page or template.
As per usual, we use the url_for.
And we're going to target our edit_task() function that we created a few moments ago.
So we have the function name, and we also have the ID.
That will be it's unique identifier.
And Flask is clever enough to remember the task ID for that particular task in the accordion list of tasks.
So that can be submitted and sent across as part of the link.
We have an error here.
So edit_task task_id.
There's a comma missing between edit_task and task_id.
Let's check that.
Save it.
Run it again.
Still another bug.
It's an issue with the quotation marks now I think.
I'm leaving these in because this is what happens in reality, and typos are made.
It'll give you an idea of what to expect.
And particularly when working with HTML and scripting languages, it's very easy to make typos, in particular with commas, quotation marks, and so on.
We can see we have our buttons in place but that they're not firing.
That is because I've wired up the done template, rather than the edit.
No, it's more than that.
Edit task.
Let's first fix that.
Let's apply it to edit.
Still failing because there is a typo.
Edit Task is spelled with an uppercase T.
The name of our file is edit task with a lowercase T.
File names are case sensitive, as you can see in Flask.
We have our categories in place, and we have our templates.
The next thing to do is populate those with actual task values.

# Bind Data To Edit Task Form
 
## What is it?

Input fields

## What does it do?

Input fields that will allow users to update the details of an existing task

## How do you use it?

You use the input element

LESSON:

We're nearly there with our edit task functionality.
What we need to do next is we need to display the task elements in the form for editing when this view is displayed to the user.
All of these need to be filled in.
Let's start with the select.
The first thing we want to do is we want to display by default the category name selected in the original task creation.
We're going to use a for loop, and we're going to use an if statement.
As we loop through the categories, if the category name matches the category name associated with this particular task, then we set that as selected.
And if the category name doesn't match the task category name, then we simply display an option without the selected attribute included.
It's a very simple use of boolean checks.
If we find a match, then we add a selected attribute.
Otherwise, we don't have a selected attribute.
Let's not forget to close our block.
So if it's true that the category name is equal to the task category name, we generate an option value with the category name displayed.
What's unique to that option is that the selected attribute will be included.
Because we're only using a single select, there should only ever be one match.
As a reminder of where this data comes from, let's go back to our app.py and look at the function.
You can see in edittask that task is passed across as well as the categories.
That allows us to match the category that's associated with task with the general list of categories.
There we can see our categories are available to us, and a selected category for that task was displayed by default.
Next, let's bind the rest of our data to the form.
So the task name, for example, the input, we're going to set the value of that task name to the task name associated with the task being passed across from the function.
Refresh.
There it is.
We'll do the same with our description.
Let's pop that in there.
We'll leave the due date unitl last because it requires an extra bit of work.
But let's work on the is urgent display for now.
Similar to what we did when displaying the options in the select, we use an if statement here as well.
If the task is urgent, and that's what's called truthy, it'll either return true or false.
So if it's true that the task is urgent, then use the checked attribute.
And if it's not, then we don't.
And it's as simple as that.
Task is spelled incorrectly there as well.
You see there that if it's urgent, use the checked attribute.
If it's not urgent, then omit the checked attribute.
Lastly, we will work with our due date.
To bind the due date associated with the task to the field, we need to work with a bit of jQuery.
In particular, we do need to reuse our jQuery import down at the level of edit_task.
For some reason it's not binding.
It's a bug.
It's not binding from the parent template, so we just need to include that script in our edit_task.
And we're going to create a bit of JavaScript that will allow us to work with the date picker.
We use the $
Remember, the $ lets you know that you are using jQuery.
And we focus on the document element.
And we're using the ready function.
I suppose it's the ready method, really, if it's associated with an object and a class.
Inside here, we're going to use an anonymous function.
And we're going to target our due date component.
We need to do a bit of formatting first.
We need to parse our date associated with this task into a format that the date picker understands.
So we now have a local variable called due_date.
Don't confuse the variable on line 68 with the ID of the component.
They are separate things.
That's a local variable that just happens to have the same spelling.
The due date we are referring to in here should be the ID of the due date we are referring to in line 69.
It's not the same value as the variable on line 68.
So we're chaining some functions here.
We're saying ID called due date, get the pick date called picker, and set our selected date as the due date we just formatted there online 68.
So it's a key value pair that's selected.
You use the Select keyword to select a particular date, and the due date that we're passing it in is the due that we formatted on line 68.
I'm also specifying the format dd/mm/yyyy
We're also setting an event trigger of change.
So we need this, but why are we doing this?
We're doing this to inject the due date into the form field associated with that date picker.
It's failing.
There's a bug somewhere. Let's see where our bug is.
Let's have a look at the component and look at the ID.
We're missing the #.
The only time that you're allowed to omit either a # or a full stop is if you're targeting a built-in component, such as a paragraph or header.
Due date is not one of those.
That's why you need the #, so we can target the correct ID.
Finally, the last thing we need to do in terms of displaying the data for edit is to change the text of the button from add task to edit task.

# Update Task In The Database
 
## What is it?

Edit task form

## What does it do?

When a user submits an edit task form, they are sending their updated task data to the database

## How do you use it?

By sending a HTTP post request (upon submission of the form) to save the updated task data to the database

LESSON:

We now have the view elements in place, our HTML.
We also have our values, which are bound to our form fields and form elements.
When we click submit, we now want to update the database with one or more values that have been edited.
It could be a case that none of them are edited, which would be a bit pointless, but it's possible.
So we create our route.
We specify the HTTP method as POST because it's coming from our form.
And remember, our form has been more or less cut and paste from the add task view.
So that will use a POST method.
Why use POST?
Well, one of the reasons is the POST method hides the values from the URL bar when they're being sent across.
We pass in the task ID because that's our hook into the primary key.
Well, the primary key if it was a relational database.
So what we do is we access the tasks collection.
Then we call the update function.
We specify the ID.
That's our key to uniqueness.
Once that's in place, we'll then specify the form fields, and we'll match those to the keys on the task collection.
Notice also, just as the documents in our collections have a separate set of curly braces for our object and our key value pairs, we do the same when updating in Python.
So we have curly braces that wrap around the ID.
Then we have a set of curly braces that wrap around each key value pair outside the ID.
So the task_name, category_name, task_description.
Use the request object to access the form and its form values, or form components.
You need to put these inside quotations because they are a form of JSON.
And use colons instead of equals or assignment values.
These are the things that can catch you up.
To an extent, they will always catch you at some point.
But as you become more experienced, you'll recognize these bugs more quickly.
So we have the due date.
Also, don't forget to separate each key value pair with a comma.
Those comma delimiters provide the intelligence to these functions to let them know that one key value pair is complete, and the next key value pair is available for processing.
This kind of comma separation and colon separation is common across nearly every programming language.
So once you get a feel for it in one language, you'll recognize it very quickly if you end up using a different programming language.
We need to run it.
Let's edit the date.
Change fiendly to friendly.
That's just Calendly reminding me to improve my grammar.
Edit task.
And there we see it.
Buy more detergent by the 22nd of January, 2018.
And our edit is complete.

# Delete Task

## What is it?

Delete task button

## What does it do?

It allows a user to delete a task from the database

## How do you use it?

By sending a HTTP post request to the database to delete the specified task

LESSON:

We now have the ability to edit a task.
So we can create a task, and now we can edit a task.
The next thing we want to do is to be able to mark a task as complete.
Now, we're taking a quite simplistic approach to it in that by marking a task as done, we're just simply deleting it from the database.
As a challenge, you could add a new key value property inside the tasks that maybe marks a task as being complete.
Then when you display tasks, you'll only display tasks where complete is equal to false.
But for now, we'll just delete a task once we're finished with it.
So to do that, we will create a new function called delete_task().
We need to know exactly which task we want to delete.
So the pattern is familiar.
We use task_id.
And we'll pass that in as a parameter into our function that just happens to have the same name, delete_task.
If you do accept the challenge and go on to mark a task as complete, then change the name of the function from delete_task to mark as complete.
So we access the tasks collection, and we call remove.
And we pass in the task_id as the parameter, so it's a very simple function.
Again, we use the syntax as we have been using up until now.
Key value pair inside the curly braces.
We use the object ID to format or parse the task ID in a way that's acceptable to Mongo.
Once that's in place, we want to return or redirect.
So we redirect to get tasks.
Why?
Because once that function is complete, we want to see it disappear. We want visual evidence to see that that task is no longer on our list.
So we redirect to the get_tasks function.
It's very straightforward.
Now, you might need to clear your cache here for this to be picked up.
Let's clear the browsing data.
As I said earlier, you can use incognito mode if you wish.
Click done, and that disappears.
So they're marked as complete.
As I mentioned, they're simply just deleted from the database.
In reality, you would come up with a more sophisticated solution than that.
So there we are, task complete.

# Display Categories
 
## What is it?

get_categories() function

## What does it do?

Reads in a list of the categories from the database and displays them to a user on a 'categories.html' page

## How do you use it?

LESSON:

It's always a good idea in coding to reuse patterns or actual code again and again.
It provides consistency to your projects.
So in order to display our categories, we are going to reuse most of the functionality that displays our list of tasks.
As with a task, you can edit and delete a category, as well as add a new category.
So we create a new categories template called categories.html.
We are going to copy the tasks content.
We'll paste it into categories, and we'll modify it.
The main difference here is there won't be any expansion on the accordion because there's no additional information required for the category, just the category name.
Just clean up our code here.
Again, we have a h3 for categories.
We could put that outside the row, but because a header is a block level element, it will automatically occupy the full width of the available space on the browser and force any subsequent content down onto a new line.
And in this case, instead of looping through a list of tasks, we're going to loop through a list of categories.
So we change our for loop to look for the category collection.
We change that from task to category_name.
We don't need a due date anymore.
And we don't need the details, the description.
So we are cheating a little bit here.
We don't necessarily need a collapsible header.
There are cards that we could use from Materialize, but because we have that pattern in place already and the shape looks similar, we're reusing it.
We're repurposing our collapsible accordion in a way that they just don't collapse.
We don't need our chevron because we don't need to expand further.
Let's clean up some white space.
And let's check that our divs are in place.
That's one of the gotchas when removing HTML elements.
Just make sure you don't leave any stray closing tags for elements.
It happens all the time.
And one way of ensuring that is to make sure your indentation is in place.
That will give you a visual idea of determining whether everything is in place or not.
So then we create a get_categories() function.
Its job is to do a find on the categories table.
Again, we'll shortcut this.
So categories.html is the template we're going to render.
And our categories parameter will feed that from a direct call to MongoDB.
So Mongo.db.categories.find.
If you do find yourself coding in other languages later on in your career, you'll really appreciate how succinct and neat and terse Python can be in terms of getting things done.
In other languages, that could take 8 or 9 lines of code.
We have old stray functions, so let's get rid of those.
There we go.
We can see our categories are in place.
Let's do another little bit of cleanup on our HTML, which will take us to delete, edit, and, eventually, add a category.


# Delete Category
 
## What is it?

A button called Delete Category and a function called delete_category()


## What does it do?

When a user clicks the Delete Category button, the delete_category() function will run which will delete the category from the database

## How do you use it?

You create your delete_category() function in app.py and wire this up to your Delete Category button

LESSON:

Our edit category is now in place.
Let's implement the delete category functionality.
So let's grab our href from the edit and reuse that for the delete.
All we need to do is change the function name in the url_for.
So let's call that delete_category.
It will need the ID because you need to know which category to delete.
So let's create the corresponding function with the route containing delete_category.
Pass in the category_id.
Create a function with the same name.
Pass in the category_id as a parameter to be used to locate and remove that category document from the categories collection.
mongo.db.categories.remove
And all we need here is the ID.
Pass that into the formatting object.
Then redirect back to the get_categories() function, which, again, once called, will make a call to the categories collection and return what categories are left in the database.
Let's test our functionality.
Let's delete the homely category.
Hit delete.
Redirect it back.
Category gone.
Perfect!

# Update Category In The Database
 
## What is it?

A button called Edit Category and a function called update_category()

## What does it do?

When a user clicks the Edit Category button on the form, the update_category() function will run. This will edit the Category text in the Database

## How do you use it?

You create your update_category() function in app.py and wire this up to your Edit Category button

LESSON:

Now that weadded the edit and delete buttons to our category list let's wire up the edit
button and in order to do that what we need to do is create a view that when
the button is clicked that view will be displayed and in that view will be a
single form field displaying the category and it allows us to edit that
once we have made a change that edit is written to the database and were
redirected back to the categories listing again the very same pattern as
used for for tasks once you edit our add a new task you are redirected back to
the tasks list so in order to do that we use our URL for to point to the
appropriate function in app dot pi and notice there we changed it from update
to edit edit category would be used to take the viewer to an editable page
update category will be used to carry out the actual update on the database
and what do we need to display that category we need the category ID the
category ID passed into the function
and we'll name our function we give it the same name as the route you don't
have to do that because URL for what URL for points to the name of a function not
the name of the roof but for simplicity sake we will just give the function the
same name as the route
don't forget to pass in the categoryid as a parameter because
we'll use this to search for that document and feed it and pass it over to
our edit category HTML page and how do we get it over there we pass it over as
a parameter called category not categories because it's a single
category for editing and we refer to the categories collection
and the function we use is find one so its job really is to pass us or pass the
user to a new view and while at the same time obtaining the category document
from the database for editing passing the category ID make sure it's in the
format that's acceptable to Mongo let's just do a little bit of Pepe cleaning
here as well I've just added an edit category that HTML view and what we're
going to do is we're going to take the Edit task functionality copy that paste
it into our edit category and trim back the form items that we don't need
similar to what we did with the categories listing when we copied and
pasted it from the tasks listing so all about reuse so let's change at a task to
at a category and really what we're going to do here is we're going to strip
out the unnecessary form fields until we're left with one and we don't need it
we don't use a select for editing we just use a text input field to display
that in order to easily edit
just collapse the the field items here and we are going to delete the select
we're also going to delete all but one of the other input fields we're gonna
keep the button because we need that to trigger the update change the value to
category top category name not task name so we're simply reusing an input field
that was used in the Edit task form let's change the IDs and they name
attributes as well for form submission change the label to category name and
change the prefix to pole because that matches the pole the our Pam it matches
the icon beside they select in our tasks
okay we haven't our end block is missing so let's go down to
back to our template and make sure there's an end block includes in there
okay
we can see there that it's displaying the correct category now what we don't
have in place yet is the ability to wire it off let's change the button name to
add cap edit category
and then we go and wire up the there we go Edda Kateri
and then we go back and wire up the they update the actual update itself ok looks
good so far
now we have edit academy will now create an update category function that will
actually write to the database that said our right decorator and the name of this
route will be update category and the submit button will call this function
from dead category and we need the ID to target the correct document over in the
database look at our function let's call it update category pass in the category
ID as a parameter for use in the update call
okay let's get our categories collection from Mongo using the syntax again
MongoDB dark categories and now we call update and we identify the ID and also
the field that we want to update in our case there is only one field to update
and that's category name
again format the ID don't forget your comma create a second curly brace set
identify the key in the document don't forget semicolon or colon followed
by the form and because this is a post again we specify the method as being
post our Hayes GTV method is being post
then let's pass in the request object drill into the form that's contained
within the request object and refer to
the form item whose name is Katerina
and once that's done we want to return to categories so we'll do a return
render and we will return to the get cut we'll use the get categories function to
redirect us back to the categories section and by doing that we do another
read from the database which will display the newly modified category name
let's do an edit
let's change music to say home again another home alright then we select edit
category and there we see it so our Edit category works

# Add Category
 
## What is it?

A button called Add Category and a function called add_category()

## What does it do?

When a user clicks the Add Category button, the delete_category() function will run. This function will provide the user with a form to save a new category to the database

## How do you use it?

You create your add_category() function in app.py and wire this up to your Add Category button

LESSON:

We now have the edit category wired and the delete category wired. Now let's add a
category. Let's create a new template called add category and what we're going
to do is we're going to take the contents of edit category
copy that and paste it in to the add category template because the
functionality and the layout for both add and edit is very similar. Let's clean up
some extra tabs here and let's change our form action and we'll change it to
insert category. We remove the category ID because we don't yet have one, we are in
the process of creating a new category at this point. Remove the default values
from the edit functionality so that frees up the text input field
to be empty. Change the text on the bottom to add category and then we go
over to our - oh, let's change our heading to add category - and go to app.py. Now
let's create the corresponding function at this point. Add our routing.
Okay it'll be insert_category.
No need for an ID this point remember because the category doesn't yet exist
but we do need to specify our HTTP methods value and as per usual we use
post. Let's access our Mongo database in preparation for the insert. So categories
is equal to mongo.db.categories.
Okay let's use this cursor and we're going to create another variable called
category_doc. We're going to create a new be BSON formatted document which remember is
more or less JSON anyway. Let's get the request form and let's get the form
field which is category name.
Okay then we add the category doc into the categories table (our collection) and
then return a redirect back to
categories which you just say get_categories - that's the function that
we're targeting. So that will ultimately do the insert but we need to have the
function that will direct us and render the view that allows us to add a new
category in the first place so let's do that now.
Add our route - new category - to be consistent we could have called that add
category to be consistent with add tasks. You can change that if you
want to - just make sure if you do that you change it in the appropriate places
where it's being called. Okay new category just simply returns a render
template which is a rendering of a view.
By the way a template is another name for a view. Right let's add
a new HTML file called add category and what we're going to do here is we're
going to take the code - the mark-up - that was used for edit category, copy it, paste
it and modify it. Okay change our heading to add instead of edit, get rid of the
value because there will be no default value placed inside there because the
category is ye to be saved.
Let's change the text on our button and let's change the form action from
update to insert.
We also get rid of the category ID because the category has yet to be
created. It doesn't have an ID because it's not yet in the database. Now we need
to add
a button to our categories list. We're gonna add that button beneath
our categories list so we go back to the categories page or template or view and
we're going to add a button. Now notice this button isn't inside in a form
because we're not submitting a form. We're just clicking on a button and
redirecting to another resource so we use a standard anchor tag here
rather than the button. As a challenge you can also do something similar in the
tasks list which allow you to add a task directly below the task list rather than
using the menu bar.
We need a href - so we need a location for this anchor tag and the URL that we will
use will be new category.
Let's just clean this up a little bit -
change the text on the button to add category. Run it.
Hmm that looks odd - let's go back. Ah it should be playlist add rather than add
playlist. Do a refresh - okay so we now we have the ability to add category beneath
the category list and there we have it add category.

# Adding A Nav Bar

## What is it?

Nav bar

## What does it do?

The Nav Bar provides users with the necessary links to navigate your application and to perform any CRUD operations (e.g. create, edit or delete tasks and categories)

## How do you use it?

You refactor the source code for a Materialize Nav Bar component to include the relevant links to your HTML templates

LESSON:

So we have all of our crud functionality in place - we can create a
task, we can create a category, we can read tasks, we can read categories and we
can update tasks, we can update categories and we can delete tasks and categories. All
we need to do now is to put some top-level navigation elements on our
application and in the spirit of semantic markup we've created a header
element and we then go across to Materialize and grab a navbar and you
can see that it's already encased in nav element as well so let's grab that paste
it into our header. Just clean it up a bit and let's test it. oh yeah, we should
first change the logo to Task Manager and let's see and there we go!
Okay so we have a little bit of work to do to this we want to make it responsive
you can see here that the navigation elements disappear and we need to fix that.
Let's go back to Materialize and we're going to grab another unordered list and
this on ordered list will be displayed in the form of a sliding side navigation
bar that when viewed on a mobile device a side panel will just slide out from
left to right and display our navigation links. Let's do a refresh we need an
additional icon which is like the three line burger-bar menu icon that we need to put
in place and then we need to make that clickable. So let's grab the icon first
and it's a link (it's embedded inside the link) to make it clickable.
Okay let's do a refresh and it appears when viewed on a mobile device. So we
then need to create an event handler for it or add an event handler for it so the
class is called button collapse for that link we just added and we need to add
this into our document ready function. So let's grab that go to our base.html
we see the document or the ready function for our document is in place
and pop that in. Do a refresh and we can see our links are there. Now these are
the default links - you see page not found when we click on them. So what we
need to do there now is to add our actual links to the navbar. So we'll
replace the default href for sass badges and collapsible and we'll replace
those and just as we've been doing throughout we'll use the jinja
templating language format so we'll use url_for and our first one will be get tasks.
We call that home. Again it's good UX to always call your homepage home. And in
our case what do we want to display when a user first arrives on the application?
Well it's the list of tasks. It gives them the ability to add a new task and we'll
give our users the ability to manage categories.
Let's have an uppercase C there for categories. Save our changes and just do a
quick check there. Okay. So we also had need to add these links into our sidebar
when viewed on a mobile device and let's change our task manager the logo should
always bring you to the home page again it's good UX. So if you click on your logo
wherever you are on your application it should always take you home. So there we
can see it all our functionality is there you can add tasks and insert tasks.
We can get tasks.
Okay let's do a refresh. Go home.
New task. Okay it's all there.
Let's test it by adding a new a new task. So it looks good. It's looking
pretty decent. We can add categories and edit categories. Okay we're in good shape
and here's our sidebar. So it looks good on mobile, looks good on desktop - if you
are so inclined you can style it further and personalize it for your needs but
well done on getting this far!


