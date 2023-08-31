---
layout: post
title: Movie Quiz
description: A Quiz about Movies
toc: True
comments: True
categories: ['5.A', 'C4.1']
courses: {'csse': {'week': 1}, 'csp': {'week': 2, 'categories': ['6.B']}, 'csa': {'week': 1}}
type: tangibles
---

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Childhood Movies Quiz</title>
<style>
  body {
    font-family: Arial, sans-serif;
  }
  #quiz-container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  h2 {
    margin-top: 0;
  }
  label {
    display: block;
    margin-bottom: 10px;
    font-weight: bold;
  }
  input[type="radio"] {
    margin-right: 5px;
  }
  #submit-button {
    margin-top: 15px;
  }
</style>
</head>
<body>
<div id="quiz-container">
  <h2>Childhood Movies Quiz</h2>
  <form id="quiz-form">
    <div class="question">
      <p>1. Which animated movie features a young lion named Simba?</p>
      <label><input type="radio" name="q1" value="a"> Aladdin</label>
      <label><input type="radio" name="q1" value="b"> The Lion King</label>
      <label><input type="radio" name="q1" value="c"> Toy Story</label>
    </div>
    <div class="question">
      <p>2. Who is the main character in the movie "Finding Nemo"?</p>
      <label><input type="radio" name="q2" value="a"> Dory</label>
      <label><input type="radio" name="q2" value="b"> Nemo</label>
      <label><input type="radio" name="q2" value="c"> Marlin</label>
    </div>
    <!-- Add more questions here... -->
    <div id="submit-button">
      <button type="button" onclick="submitQuiz()">Submit Answers</button>
    </div>
  </form>
  <div id="results"></div>
</div>

<script>
function submitQuiz() {
  const answers = {
    q1: document.querySelector('input[name="q1"]:checked'),
    q2: document.querySelector('input[name="q2"]:checked'),
    // Add more answers here...
  };

  const correctAnswers = {
    q1: 'b',
    q2: 'b',
    // Add more correct answers here...
  };

  let score = 0;

  for (const question in answers) {
    if (answers[question] && answers[question].value === correctAnswers[question]) {
      score++;
    }
  }

  const resultsContainer = document.getElementById('results');
  resultsContainer.innerHTML = `You scored ${score} out of ${Object.keys(correctAnswers).length}!`;
}
</script>
</body>
</html>
