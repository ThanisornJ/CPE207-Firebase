# JQuery
>**jQuery** is a fast, small, and feature-rich JavaScript library. It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JavaScript. <jquery.com>

### Basic JQuery

Select HTML Element using JQuery

``` html
<!-- index.html --->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>Hello</h1>
    <h1>world</h1>
    <h3 class="text">good morning</h3>
    <h3 id="title">good afternoon</h3>
    <input type="text" id="name">

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
</body>
</html>
```
Open `Console` tab and try code below

``` javascript
$('h3')
// output
$('h3')[0]
// output
$('.text')
// output
$('#title')
// output

// Try to access value of element
$('#title').text()

$('#name').val()
```

### AJAX
ajax is build-in JQuery perform an asynchronous HTTP (Ajax) request.

``` javascript
$.ajax({
    url: 'https://api.github.com/users',
    method: 'GET',
    success: data => console.log(data),
    error: err => console.log(err)
})
```
Simple GET method using ajax. common method `GET`, `POST`, `PUT`, `DELETE`.
To use `POST` method and send data to api endpoint see the code below.

``` javascript
$.ajax({
    url: 'https://jsonplaceholder.typicode.com/posts',
    method: 'POST',
    data: {
        text: 'Hello world',
        name: 'John Doe',
    },
    success: data => console.log(data),
    error: err => console.log(err)
})
```

# Firebase 🔥
https://console.firebase.google.com/

Create Project and Getting Started.
Setting permission Rule

Starting template

```html
<!doctype html>
<html lang="en">

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css"
        integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

    <title>GPA Calculator</title>
</head>

<body style="padding: 1em">
    <div class="container-fluid">
        <div class="row">
            <div class="col-md-6">
                <div class="card border-info mb-3">
                    <div class="card-header">
                        <h3 class="card-title">GPA Calculator</h3>
                    </div>
                    <div class="card-body">
                        <form action="">
                            <div class="form-group">
                                <label for="">Subject</label>
                                <input type="text" id="subject" class="form-control" placeholder="Subject...">
                            </div>
                            <div class="form-group">
                                <label for="">Grade</label>
                                <select id="grade" class="form-control" id="">
                                    <option value="4">A</option>
                                    <option value="3">B</option>
                                    <option value="2">C</option>
                                    <option value="1">D</option>
                                    <option value="0">F</option>
                                </select>
                            </div>
                        </form>
                        <button class="btn btn-primary btn-flat">Submit</button>
                    </div>
                </div>
            </div>
            <div class="col-md-6">
                <div class="card text-white bg-dark mb-3">
                    <div class="card-header">
                        <h3 class="card-title">Result</h3>
                    </div>
                    <div class="card-body">
                        <table class="table text-white">
                            <thead>
                                <tr>
                                    <th>Subject</th>
                                    <th>Grade</th>
                                </tr>
                            </thead>
                            <tbody>
                                
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.4.1.slim.min.js"
        integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous">
    </script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
        integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous">
    </script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js"
        integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous">
    </script>

    <!-- The core Firebase JS SDK is always required and must be listed first -->
    <script src="https://www.gstatic.com/firebasejs/7.7.0/firebase-app.js"></script>

    <!-- TODO: Add SDKs for Firebase products that you want to use
     https://firebase.google.com/docs/web/setup#available-libraries -->
    <script src="https://www.gstatic.com/firebasejs/7.7.0/firebase-firestore.js"></script>
    <script src="js/index.js"></script>
</body>

</html>
```

```javascript
// index.js

let firebaseConfig = {
    apiKey: "#API-KEY",
    authDomain: "localhost",
    projectId: "#ProjectID",
};
// Initialize Firebase
firebase.initializeApp(firebaseConfig);
let db = firebase.firestore();
```

### Firebase Data Model

![alt Firebase](https://firebase.google.com/docs/firestore/images/structure-data.png)

#### Documents
In Cloud Firestore, the unit of storage is the document. A document is a lightweight record that contains fields, which map to values. Each document is identified by a name.

A document representing a user alovelace might look like this:

```javascript
first : "Ada"
last : "Lovelace"
born : 1815
```

#### Collections

Documents live in collections, which are simply containers for documents. For example, you could have a users collection to contain your various users, each represented by a document

Read more: [Firebase Cloud Firestore](https://firebase.google.com/docs/firestore/data-model)