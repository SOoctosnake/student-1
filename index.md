---
layout: default
title: Student Blog
---

<style>

<style>
body {
      background-color: #171515;
      color: #ffffff;
  }

h2::before {  
  transform: scaleX(0);
  transform-origin: bottom right;
}

h2:hover::before {
  transform: scaleX(1);
  transform-origin: bottom left;
}

h2::before {
  content: " ";
  display: block;
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  inset: 0 0 0 0;
  background: rgb(0, 0, 0);
  z-index: -1;
  transition: transform .3s ease;
}

h2 {
  position: relative;
  color: #39FF14;
  font-size: 1.5rem;
  font-family: Monospace;
}

p {
  font-family: Monospace;
}

html {
  block-size: 100%;
  inline-size: 100%;
}

body {
  min-block-size: 100%;
  min-inline-size: 100%;
  margin: 0;
  box-sizing: border-box;
  display: grid;
  place-content: center;
  font-family: system-ui, sans-serif;
}

.block-container {
    padding-top: 1rem;
    padding-bottom: 0rem;
    padding-left: 5rem;
    padding-right: 5rem;
}



#loader-wrapper {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1001;
}
#loader-wrapper .loader-section {
  position: fixed;
  top: 0;
  width: 51%;
  height: 100%;
  background: #000;
  z-index: 1000;
}
#loader-wrapper .loader-section.section-left {
  left: 0;
}
#loader-wrapper .loader-section.section-right {
  right: 0;
}
#loader {
  display: block;
  position: relative;
  left: 50%;
  top: 50%;
  width: 150px;
  height: 150px;
  margin: -75px 0 0 -75px;
  border-radius: 50%;
  border: 3px solid transparent;
  border-top-color: #1f1137;
  -webkit-animation: spin 2s linear infinite;
          animation: spin 2s linear infinite;
  z-index: 99999;
}
#loader:before {
  content: "";
  position: absolute;
  top: 5px;
  left: 5px;
  right: 5px;
  bottom: 5px;
  border-radius: 50%;
  border: 3px solid transparent;
  border-top-color: #9370DB;
  -webkit-animation: spin 3s linear infinite;
          animation: spin 3s linear infinite;
}
#loader:after {
  content: "";
  position: absolute;
  top: 15px;
  left: 15px;
  right: 15px;
  bottom: 15px;
  border-radius: 50%;
  border: 3px solid transparent;
  border-top-color: #CBC3E3;
  -webkit-animation: spin 1.5s linear infinite;
          animation: spin 1.5s linear infinite;
}
/*
.loaded #loader-wrapper {
  visibility: hidden;
  -webkit-transform: translateY(-100%);
          transform: translateY(-100%);
  -webkit-transition: all 0.3s 1s ease-out;
  transition: all 0.3s 1s ease-out;
}
.loaded #loader-wrapper .loader-section.section-left {
  -webkit-transform: translateX(-100%);
          transform: translateX(-100%);
  -webkit-transition: all 0.7s 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
  transition: all 0.7s 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
}
.loaded #loader-wrapper .loader-section.section-right {
  -webkit-transform: translateX(100%);
          transform: translateX(100%);
  -webkit-transition: all 0.7s 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
  transition: all 0.7s 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
} 
*/
@-webkit-keyframes fadeOut {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

.loaded #loader-wrapper {
  visibility: hidden;
  -webkit-transition: fadeOut 2.0s ease;
  animation: fadeOut 2.0s ease forwards;
}

.loaded #loader-wrapper .loader-section-left {  
  -webkit-transition: fadeOut 2.0s ease;
  animation: fadeOut 2.0s ease forwards;
}

.loaded #loader-wrapper .loader-section-right {  
  -webkit-transition: fadeOut 2.0s ease;
  animation: fadeOut 2.0s ease forwards;
}


/* .loaded #loader-wrapper {
  visbility: none;
} */

/* Apply the animation when the loader is being faded out */

@-webkit-keyframes spin {
  0% {
    -webkit-transform: rotate(0deg);
            transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
            transform: rotate(360deg);
  }
}
@keyframes spin {
  0% {
    -webkit-transform: rotate(0deg);
            transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
            transform: rotate(360deg);
  }
}

.typewriter h1 {
  overflow: hidden; /* Ensures the content is not revealed until the animation */
  font-family: Monospace;
  border-right: .015em solid orange; /* The typwriter cursor */
  white-space: nowrap; /* Keeps the content on a single line */
  margin: 0 auto; /* Gives that scrolling effect as the typing happens */
  letter-spacing: 0.015em; /* Adjust as needed */
  animation: 
    typing 15.0s steps(30, end) infinite,
    blink-caret 1s step-end infinite;
  animation-delay: 2000ms;
  animation-fill-mode: both;
  color: #000000
}

/* The typing effect */
@keyframes typing {
  0%, 50%, 100% {
    width: 0;
  }
  25%, 75% {
    width: 100%;
  }
}
/* The typewriter cursor effect */
@keyframes blink-caret {
  from, to { border-color: transparent }
  50% { border-color: white; }
}

h2 {
    color: #FFFFEE;
}

h1 {
  color: #FFFFFF
}

h1:hover {
  font-size: 32px;
}
</style>

<script>
  document.addEventListener("DOMContentLoaded", function() {
  setTimeout(function() {
      document.querySelector("body").classList.add("loaded");
  }, 2000)
});
</script>

<!-- <script>
document.addEventListener("DOMContentLoaded", function() {
  const words = ["Welcome", "to", "Saathvik", "Blog"];
  let wordIndex = 0;
  
  function updateWord() {
    const titleElement = document.querySelector(".typewriter h1");
    titleElement.textContent = words[wordIndex];
    wordIndex = (wordIndex + 1) % words.length;
  }

  setInterval(updateWord, 1); // Change word every 3.5 seconds
});
</script> -->

<div class="typewriter">
    <h1>Welcome to Saathvik's Blog</h1>
</div>

<div id="loader-wrapper">
  <div id="loader"></div>
  <div class="loader-section section-left"></div>
  <div class="loader-section section-right"></div>
</div>

<br>

## Saathvik's Computer Science Blog
Hi! I'm Saathvik Gampa, an **aspiring computer science developer**! I am **15** years old and go to Del Norte High. I am currently in my **Sophomore** year in high school challenging myself with 3 AP courses. Here are more facts about me:
- **Member** of Del Norte High's robotics team Team Optix 3749
- DECA **Participant**
- Aspiring **Tennis Player**
- **Academically** Driven Student

- 👋 Hi, I’m @SGTech08
- 👀 I’m interested in computer and data science
- 🌱 I’m currently learning Python, HTML, and JavaScript
- 💞️ I’m looking to collaborate on projects on Github.
- 📫 Reach me on Instagram

![pictureAboutMyself](IMG_3876.jpg)


**Social** Media :  
[Github](https://github.com/SGTech08)  
[Instagram](https://instagram.com/saathvikg08)  



### Here is a little mini game :):
<div>
<script>
    var question = 1
        function checkInput() {
            var userInput = document.getElementById("userInput").value;
            if (userInput == "sophomore" && question == 1) {
                document.getElementById("questionLabel").textContent = "What school do I go to?"
                document.getElementById("userInput").value = ""
                question = question + 1
            }
            if (userInput == "DNHS" && question == 2) {
                document.getElementById("questionLabel").textContent = "What do I want to major in?"
                document.getElementById("userInput").value = ""
                question = question + 1
                }
             if (userInput == "computer science" && question == 3) {
                alert("You got everything right!")
                }
        }
    </script>
    <label id = "questionLabel" for="userInput">What grade am I in?</label>
    <input type="text" id="userInput">
    <button onclick="checkInput()">Submit</button>
</div> 

