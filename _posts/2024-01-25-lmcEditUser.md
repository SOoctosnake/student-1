---
comments: True
layout: post
title: Edit User
description: cooking
courses: { csp: {week: 20} }
type: hacks
permalink: /lmc-editUser
---
<style>

</style>``
<!-- 
A simple HTML login form with a Login action when button is pressed.  

The form triggers the login_user function defined in the JavaScript below when the Login button is pressed.
-->
<link rel="stylesheet" href="/lmc-frontend/LMC/JS/SCSS/lmcLogin.css">
<div id="titleContainer">
</div>

<div class="background">

</div>

<div class="container">
    <form id="username" action="javascript:login_user()">
        <p><label>
            User Name:
            <input class="userInput" type="text" name="name" id="name" required>
        </label></p>
        <p><label>
            Date of Birth:
            <input class="userInput" type="text" id="dob" required>
        </label></p>
        <p>
            <button onclick="login_user()">Submit</button>
        </p>
    </form>
</div>


<!-- 
Below JavaScript code is designed to handle user authentication in a web application. It's written to work with a backend server that uses JWT (JSON Web Tokens) for authentication.

The script defines a function when the page loads. This function is triggered when the Login button in the HTML form above is pressed. 
 -->
<script type="module">
    // uri variable and options object are obtained from config.js
    import { uri, options } from '{{site.baseurl}}/assets/js/api/config.js';
    
    function login_user(){
        // Set Authenticate endpoint
        const url = uri + '/api/users/';

        // Set the body of the request to include login data from the DOM
        const body = {
            name: document.getElementById("name").value,
            dob: document.getElementById("dob").value,
        };

        // Change options according to Authentication requirements
        const authOptions = {
            ...options, // This will copy all properties from options
            method: 'PUT', // Override the method property
            cache: 'no-cache', // Set the cache property
            headers: {
                'Content-Type': 'application/json', // Example header
                'uid': localStorage.getItem('uid') // Set the uid as a header
            },
            body: JSON.stringify(body),
        };

        console.log(url);
        console.log(authOptions);
        console.log(body);
        // Fetch JWT
        fetch(url, authOptions)
        .then(response => {
            // handle error response from Web API
            if (!response.ok) {
                const errorMsg = 'Login error: ' + response.status;
                console.log(errorMsg);
                return;
            }
            window.location.href = "{{site.baseurl}}/data/database";
        })
        // catch fetch errors (ie ACCESS to server blocked)
        .catch(err => {
            console.error(err);
        });
    }

    // Attach login_user to the window object, allowing access to form action
    window.login_user = login_user;
</script>