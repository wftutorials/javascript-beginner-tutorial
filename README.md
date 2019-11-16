# A vanilla Javascript Tutorial for beginners and programmers

Javascript is a popular scripting language that was initalized used primarily for the web. Now it does everything.
Using vanilla javascript which means no frameworks and libraries lets see what we can do.
You can learn more about javascript [here](https://developer.mozilla.org/en-US/docs/Web/javascript).

# Installation

This is not required as it is available on most recent broswers unless it has been disabled.

Lets create a sample template to work with. Create a file called it `index.html` and add the code below.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>

</body>
<script>

</script>
</html>
```

This is the basic template we will be using throughout this tutorial.

# Hello World

Lets add a `p` element and give it an `id`. We will use the `id` to reference the element in javascript.

```html
<p id="message"></p>
```

Now we can add text to our element.

```javascript
var el = document.getElementById('message');
el.innerHTML = "Hello World";
```

We use `document.getElementById` to get a reference to our `p` element. Then we use
`innerHTML` to set the content of the element.

[js_hello_world.png]

View the full code here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<p id="message"></p>
</body>
<script>
var el = document.getElementById('message');
el.innerHTML = "Hello World";
</script>
</html>
```

# Creating a list

Lets create a list. We need an array of element and we need to display them in the webpage.

First we create or `html` template.

```html
<ul id="list">
</ul>
```

Now we have a `ul` element with an **id** for `list`.

In the javascript we create the array we need. We also get the `list` element.

```javascript
var items = ['blue','red','black','brown'];
var el = document.getElementById('list');
```

We use a `for` loop to iterate through our `items` array. 
Learn more about loops [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for).

```javascript
for(var i =0; i< items.length; i++){
 
}
```

Within the `for` loop we add our list items.

```javascript
var listItem = document.createElement("li");
listItem.innerHTML = items[i];
el.appendChild(listItem);
```

We create a `listItem` using `document.createElement()` function and then we then set
the `innerHTML` to the current `items` instance. We finally use `appendChild` to add it to our
`list`.

[js_list.png]

You can view the full code here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<ul id="list">
</ul>
</body>
<script>
var items = ['blue','red','black','brown'];
var el = document.getElementById('list');
for(var i =0; i< items.length; i++){
    var listItem = document.createElement("li");
    listItem.innerHTML = items[i];
    el.appendChild(listItem);
}
</script>
</html>
```

# Click events

We can capture events in javascript lets see how. Lets add our `html` element first.

```html
<p>We are are going to click a button</p>
<button id="button">Click Me</button>
```

Take note of our button. With `id` button. We are going to attach an event here.
First we get the element by id.

```javascript
var el = document.getElementById('button');
```

Then we attach the event using the `addEventListener` function. Learn more about it [here](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener).

```javascript
var el = document.getElementById('button');
el.addEventListener('click', function(){
    alert("button was clicked");
})
```

The result is show below

[js_click_event.gif]

The full code can be show here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<p>We are are going to click a button</p>
<button id="button">Click Me</button>
</body>
<script>
var el = document.getElementById('button');
el.addEventListener('click', function(){
    alert("button was clicked");
})
</script>
</html>
```

# Two way binding

We can mimic this in javascript in a simple way using the following.

Lets setup our `html` views.

```html
<p id="messageOutput">We are are going to click a button</p>
<input id="message" type="text" />
<button id="button">Click Me</button>
```

We get all our elements by id

```javascript
var el = document.getElementById('button');
var msg = document.getElementById('message');
var output = document.getElementById('messageOutput');
```

Then we add a event listener to the `msg` element. The event is `keypress`

```javascript
msg.addEventListener('keypress',function(e){
    output.innerHTML = msg.value;
});
```

This will to a degree simulate two way binding. The results is show below

[js_two_way_binding.gif]

> This is probably a bad example, but you can see how we can update our views based on user input.

You can view the full code here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<p id="messageOutput">We are are going to click a button</p>
<input id="message" type="text" />
<button id="button">Click Me</button>
</body>
<script>
var el = document.getElementById('button');
var msg = document.getElementById('message');
var output = document.getElementById('messageOutput');
msg.addEventListener('keypress',function(e){
    output.innerHTML = msg.value;
});
el.addEventListener('click', function(){
    alert(msg.value);
})
</script>
</html>
```

# Css Styling

We can change the text styling by using `el.style.cssText` object reference lets see how.
Our `html` is show below

```html
<p id="messageOutput">We are are going to click a button</p>
<button id="button">Click Me</button>
```

In our javascript we create a variable to track the css changes called `textColor`.

```javascript
var textColor = "black";
```

Then in our event listener we update the text color based on its current state.

```javascript
el.addEventListener('click', function(){
    if(textColor == "black"){
        output.style.cssText = "color: red;";
        textColor = "red";
    }else{
        output.style.cssText = "color: black;";
        textColor = "black";
    }
})
```

This gives out a little toggle feature where we can change the text color from black to red.

[js_styling.gif]

You can view the full code here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<p id="messageOutput">We are are going to click a button</p>
<button id="button">Click Me</button>
</body>
<script>
    var textColor = "black";
    var el = document.getElementById('button');
    var output = document.getElementById('messageOutput');
    el.addEventListener('click', function(){
        if(textColor == "black"){
            output.style.cssText = "color: red;";
            textColor = "red";
        }else{
            output.style.cssText = "color: black;";
            textColor = "black";
        }
    })
</script>
</html>
```

## Multiple Styles

We can add multiple styles using the `el.style.cssText` feature. Lets see how.

In our event listener function we add additional styles to our logic seperated by a comma

```javascript
el.addEventListener('click', function(){
    if(textColor == "black"){
        output.style.cssText = "color: red; font-size:20px;";
        textColor = "red";
    }else{
        output.style.cssText = "color: black; font-size:12px";
        textColor = "black";
    }
})
```

Now we can see the results. The color and font size changes as we press the button.

[js_multiple_styles.gif]

## Class Styling

We can change the `class` of an element in javascript. Lets add the `html` template.

```html
<p id="messageOutput" class="big">We are are going to click a button</p>
```

The element above has a class of `big`. In the head we have a style tag.

```html
<style>
    .big {
        font-size: 20px;
    }
    .small {
        font-size: 12px;
    }
</style>
```

So we have two styles `big` and `small`. We can now change the `p` element using javascript.

```javascript
var el = document.getElementById('button');
var output = document.getElementById('messageOutput');
el.addEventListener('click', function(){
    if(output.className == "big"){
        output.className = "small";
    }else{
        output.className = "big";
    }
})
```

Above we use the `el.className` property to manipulate the element style. We toggle between `big` and `small`.
The results is show below. You can see the `class` tag being changed in the `dom`.

[js_class_name.gif]

You can view the code here -> 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<style>
    .big {
        font-size: 20px;
    }
    .small {
        font-size: 12px;
    }
</style>
<body>
<p id="messageOutput" class="big">We are are going to click a button</p>
<button id="button">Click Me</button>
</body>
<script>
    var el = document.getElementById('button');
    var output = document.getElementById('messageOutput');
    el.addEventListener('click', function(){
        if(output.className == "big"){
            output.className = "small";
        }else{
            output.className = "big";
        }
    })
</script>
</html>
```

# Conditionally Rendering HTML templates

We can hide and show elements using javascript. Lets see how.
First we add our `html` template

```html
<div style="width: 100px; height: 100px; background: #ddd; padding: 5px;">
    <p id="messageOutput" style="display: block;">We are are going to click a button</p>
</div>
```

We are going to hide the `messageOutput` using javascript when we click the button.

```javascript
var el = document.getElementById('button');
var output = document.getElementById('messageOutput');
el.addEventListener('click', function(){
    if(output.style.display == "block"){
        output.style.display = "none";
    }else{
        output.style.display = "block";
    }
})
```

Above we use `el.style.display` to change the visibility of the `messageOutput` from block which shows it to none which 
hides it.

We can also use the `hidden` property. Learn more [here](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/hidden).

Update or `html`. We are removing the **style** `display:block`.

```html
<div style="width: 100px; height: 100px; background: #ddd; padding: 5px;">
    <p id="messageOutput" >We are are going to click a button</p>
</div>
```

Now in javascript we change the `eventListener` code.

```javascript
var el = document.getElementById('button');
var output = document.getElementById('messageOutput');
el.addEventListener('click', function(){
    if(output.hidden == true){
        output.hidden = false;
    }else{
        output.hidden = true;
    }
})
```

This produces a similar result as before.

[js_conditionally_rendering.gif]

You can view the code here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<div style="width: 100px; height: 100px; background: #ddd; padding: 5px;">
    <p id="messageOutput" >We are are going to click a button</p>
</div>
<button id="button">Click Me</button>
</body>
<script>
    var el = document.getElementById('button');
    var output = document.getElementById('messageOutput');
    el.addEventListener('click', function(){
        if(output.hidden == true){
            output.hidden = false;
        }else{
            output.hidden = true;
        }
    })
</script>
</html>
```

# Forms

Lets see how we can work with forms elements in javascript. First lets add our `html` template.

```html
<p>This is a form tutorial</p>
<form>

</form>
```

## Text Input

Lets try the text input. The `html` is simple enough

```html
<input id="username" type="text" name="firstname" value="John"/>
```

In the javascript we can do.

```javascript
var button = document.getElementById('button');
var el = document.getElementById('username')
button.addEventListener('click', function(){
    alert(el.value);
})
```

The `el.value` property allows use to get the current text from the `input`.

The result is show below.

[js_form_textinput.gif]

## Text Area Element

The textarea is the same as the text input.

```html
<textarea id="message">Hello</textarea>
```

In the javascript you can do

```javascript
document.getElementById('message').value; // output hello
```

## The Select Input

The `html` for the `select` is show below

```html
<select id="cars">
    <option value="nissan">Nissan</option>
    <option value="toyota">Toyota</option>
    <option value="bmw">BMW</option>
    <option value="kia">Kia</option>
</select>
```

Whatever option you choose you can use the `value` property to get the value.

```javascript
var cars = document.getElementById('cars').value;
```

You can see this below.

[js_form_select.gif]

## The checkbox

The check box html is just like the others

```html
<input id="rememberme" type="checkbox" />
```

Now in the javascript we have do see if its checked or not if we want to take action

```javascript
var remMe = document.getElementById('rememberme');
button.addEventListener('click', function(){
    if(remMe.checked == true){
        alert("checked");
    }else{
        alert("not checked");
    }
});
```

We can see the results below.

[js_checkbox_input.gif]


## Form submission

How can we submit a form in javascript. Lets see how.
We can use `FormData` class to deal with forms in javascript. Learn more [here](https://developer.mozilla.org/en-US/docs/Web/API/FormData/FormData).

In javascript we first get a reference to our form by `id`

```javascript
var form = document.getElementById('my-form');
```

Next we pass the reference to the `FormData` class.

```javascript
var formData = new FormData(form);
```

If we want to see the values we collected from the form we can using

```javascript
for (var value of formData.values()) {
    console.log(value);
}
```

If we want to add more data to `formData` we can use the `append` function.

```javascript
formData.append('rememberme', isRememberme);
```

The results is show below.

# Comment - About the check box

We kept track of the checkbox value

```javascript
var remMe = document.getElementById('rememberme');
var isRememberme = (remMe.checked==true) ? 'yes' : 'no';
```

We then added it to the formData.

```javascript
 formData.append('rememberme', isRememberme);
```

This is one way to deal with checboxes.

# End comment

[js_form_submission.gif]

To actually submit the form you can do

```javascript
var request = new XMLHttpRequest();
request.open("POST", "submitform.php");
request.send(formData);
```

Where `submitform.php` is a server side script.

The full code can be found here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<p>This is a form tutorial</p>
<form id="my-form">
    <input id="username" type="text" name="firstname" value="John"/><br>
    <textarea id="message" name="message">Hello</textarea><br>
    <select id="cars" name="cars">
        <option value="nissan">Nissan</option>
        <option value="toyota">Toyota</option>
        <option value="bmw">BMW</option>
        <option value="kia">Kia</option>
    </select><br>
    Remember me? <input id="rememberme" type="checkbox" />
</form>
<button id="button">Click Me</button>
</body>
<script>
    var button = document.getElementById('button');
    var remMe = document.getElementById('rememberme');
    var form = document.getElementById('my-form');
    button.addEventListener('click', function(){
        var isRememberme = (remMe.checked==true) ? 'yes' : 'no';
        var formData = new FormData(form);
        formData.append('rememberme', isRememberme);
        for (var value of formData.values()) {
            console.log(value);
        }
    });
</script>
</html>
```

# Pulling data from an API

Lets use an api to display data on our webpage.
We will be using the `url` [https://jsonplaceholder.typicode.com/users/](https://jsonplaceholder.typicode.com/users/).

Lets add our `html` template.

```html
<p>Getting data from an api</p>
<ul id="list">

</ul>
<button id="button">Click Me</button>
```

We have a `button` and a empty `ul` list. Lets get our data.

First we create a request.

```javascript
const request = new Request('https://jsonplaceholder.typicode.com/users/');
```

Then on the `button` click we using the `fetch` function

```javascript
fetch(request)
    .then(response => {
        if (response.status === 200) {
            return response.json();
        } else {
            throw new Error('Something went wrong on api server!');
        }
    })
    .then(response => {
        console.log(response); // show the response
        // run the ui code here
    }).catch(error => {
    console.error(error);
});
```

In the second `then` function - learn more [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then) 
- is where we place the `ui` code to display the elements.
Learn more about the `fetch` function [here](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch).

The `ui` code is similar to how we created `li` elements earlier except we are using a `foreach` function to iterate through
our results.

```javascript
response.forEach(user=>{
    var listItem = document.createElement("li");
    listItem.innerHTML = user.name +  ' | ' + user.email;
    el.appendChild(listItem);
})
```

The result is show below.

[js_pull_from_api.gif]

You can view the full code here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<p>Getting data from an api</p>
<ul id="list">

</ul>
<button id="button">Click Me</button>
</body>
<script>
    const request = new Request('https://jsonplaceholder.typicode.com/users/');
    var button = document.getElementById('button');
    var el = document.getElementById('list');
    button.addEventListener('click', function(){
        fetch(request)
            .then(response => {
                if (response.status === 200) {
                    return response.json();
                } else {
                    throw new Error('Something went wrong on api server!');
                }
            })
            .then(response => {
                console.log(response);
                response.forEach(user=>{
                    var listItem = document.createElement("li");
                    listItem.innerHTML = user.name +  ' | ' + user.email;
                    el.appendChild(listItem);
                })
            }).catch(error => {
            console.error(error);
        });
    });
</script>
</html>
```

# Creating a table from an api

So lets create a table view using the api we used in the last example. After we do this we will
filter the table in real time.

Lets create the `html` table. The `el` we will be referencing is the `tbody`.

```html
<table>
<thead>
    <tr>
        <td>User Name</td>
        <td>Email</td>
        <td>Website</td>
    </tr>
</thead>
<tbody id="list">

</tbody>
</table>
```

We need to add some styling to make the table look good.

```html
<style>
    table, th, td {
        border: 1px solid black;
        border-collapse: collapse;
    }
</style>
```

In the javascript in the `then` function we render out layout. We are using the same `fetch` function as before and the same
`forEach` on the `response` array.

```javascript
response.forEach(user=>{
    var layout = '<tr>';
    layout += '<td>' + user.name + '</td>';
    layout += '<td>' + user.email + '</td>';
    layout += '<td>' + user.website + '</td>';
    layout += '</tr>';
    el.innerHTML += layout;
})
```

We are creating the `tr` elements and `td` elements and adding it to the `el.innerHTML`.
The `+=` is used to concatenate so we don't overwrite the html we added before.

We can look at the results below.

[js_table_api.gif]

We can view the full script here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<style>
    table, th, td {
        border: 1px solid black;
        border-collapse: collapse;
    }
</style>
<p>Getting data from an api</p>
<table style="border: 1px solid #ccc;">
    <thead>
        <tr>
            <td>User Name</td>
            <td>Email</td>
            <td>Website</td>
        </tr>
    </thead>
    <tbody id="list">

    </tbody>
</table>
<button id="button">Load Table</button>
</body>
<script>
    const request = new Request('https://jsonplaceholder.typicode.com/users/');
    var button = document.getElementById('button');
    var el = document.getElementById('list');
    button.addEventListener('click', function(){
        fetch(request)
            .then(response => {
                if (response.status === 200) {
                    return response.json();
                } else {
                    throw new Error('Something went wrong on api server!');
                }
            })
            .then(response => {
                console.log(response);
                response.forEach(user=>{
                    var layout = '<tr>';
                    layout += '<td>' + user.name + '</td>';
                    layout += '<td>' + user.email + '</td>';
                    layout += '<td>' + user.website + '</td>';
                    layout += '</tr>';
                    el.innerHTML += layout;
                })
            }).catch(error => {
            console.error(error);
        });
    });
</script>
</html>
```

# Filtering a table from an api

We can filter the `data` we received from the api in the table. Lets see how.

Lets add the `html` template. We have our `text input` and a `table`.

```html
Search <input id="query" type="text"/><br><br>
<table style="border: 1px solid #ccc;">
    <thead>
        <tr>
            <td>User Name</td>
            <td>Email</td>
            <td>Website</td>
        </tr>
    </thead>
    <tbody id="list">

    </tbody>
</table>
```

Now the javascript we create some functions to order everything. But first we intialize our global variables.

```javascript
const request = new Request('https://jsonplaceholder.typicode.com/users/');
var query = document.getElementById('query');
var el = document.getElementById('list');
var allUsers = null;
```

Of note is `allUsers`. We will keep a reference to the api data in this variable. Our `query` is the text input element.

Lets look at the different functions and what they do.

## The renderTable function

The first one we look at is the `renderTable` function

````javascript
function renderTable(users){
    el.innerText = "";
    users.forEach(user=>{
        var layout = '<tr>';
        layout += '<td>' + user.name + '</td>';
        layout += '<td>' + user.email + '</td>';
        layout += '<td>' + user.website + '</td>';
        layout += '</tr>';
        el.innerHTML += layout;
    })
}
````

We use this function to update our table based on an array of `users`. We use `forEach` to loop and display the content.
We update the `el` using `el.innerHTML`. **Also note** we first clear the `el` at the top of the function.

## The searchTable function

The `searchTable` function is what we use to search the array of `users` with the `query` from the user.

```javascript
function searchTable(query){
    var filteredUsers = allUsers.filter((u) => {
        return u.name.toLowerCase().includes(query) || u.website.toLowerCase().includes(query)
    });
    if(query != "" && filteredUsers.length > 0){
        renderTable(filteredUsers);
    }else{
        renderTable(allUsers);
    }
}
```

On the `allUsers` we call the `filter` 
function (learn more [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)).

The return results will be sent to the `renderTable` function. Otherwise we send `allUsers` to the `renderTable`.

The `loadData` function is the same except that we load the `allUsers` with the `response`.

```javascript
then(response => {
    allUsers = response;
    renderTable(response);
})
```

At the end of the script we call the `loadData` function first. To get every started.

You can view the results first.

[js_table_filter.gif]

You can view the full code here ->

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vanilla Javascript Tutorial</title>
</head>
<body>
<style>
    table, th, td {
        border: 1px solid black;
        border-collapse: collapse;
    }
</style>
<p>Getting data from an api</p>
Search <input id="query" type="text"/><br><br>
<table style="border: 1px solid #ccc;">
    <thead>
        <tr>
            <td>User Name</td>
            <td>Email</td>
            <td>Website</td>
        </tr>
    </thead>
    <tbody id="list">

    </tbody>
</table>
</body>
<script>
    const request = new Request('https://jsonplaceholder.typicode.com/users/');
    var query = document.getElementById('query');
    var el = document.getElementById('list');
    var allUsers = null;

    query.addEventListener('keypress',function(e){
        searchTable(query.value.toLowerCase());
    });

    function loadData(){
        fetch(request)
            .then(response => {
                if (response.status === 200) {
                    return response.json();
                } else {
                    throw new Error('Something went wrong on api server!');
                }
            })
            .then(response => {
                console.log(response);
                allUsers = response;
                renderTable(response);
            }).catch(error => {
            console.error(error);
        });
    }

    function searchTable(query){
        var filteredUsers = allUsers.filter((u) => {
            return u.name.toLowerCase().includes(query) || u.website.toLowerCase().includes(query)
        });
        if(query != "" && filteredUsers.length > 0){
            renderTable(filteredUsers);
        }else{
            renderTable(allUsers);
        }
    }

    function renderTable(users){
        el.innerText = "";
        users.forEach(user=>{
            var layout = '<tr>';
            layout += '<td>' + user.name + '</td>';
            layout += '<td>' + user.email + '</td>';
            layout += '<td>' + user.website + '</td>';
            layout += '</tr>';
            el.innerHTML += layout;
        })
    }

    loadData();
</script>
</html>
```

# Conclusion

Thats our beginner introduction to `Javascript`. You can do alot with it. Its available on all browsers. Try out the
examples here to get started. Check the references for more information.