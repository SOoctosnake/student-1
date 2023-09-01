---
layout: post
title: Chat GPT AI BOT
description: Talk with Chat Gpt :)
toc: True
comments: True
categories: ['5.A', 'C4.1']
courses: {'csse': {'week': 1}, 'csp': {'week': 2, 'categories': ['6.B']}, 'csa': {'week': 1}}
type: tangibles
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chatbot Example</title>
  <style>
    body {
      font-family: Arial, sans-serif;
    }
    #chat-container {
      max-width: 600px;
      margin: 0 auto;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 5px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    #chat-messages {
      margin-bottom: 10px;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
      background-color: #f9f9f9;
      max-height: 300px;
      overflow-y: auto;
    }
    #user-input {
      width: 100%;
      padding: 5px;
    }
    #send-button {
      margin-top: 10px;
      padding: 5px 10px;
      background-color: #007bff;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div id="chat-container">
    <h2>Chatbot Example</h2>
    <div id="chat-messages"></div>
    <input type="text" id="user-input" placeholder="Type a message...">
    <button id="send-button">Send</button>
  </div>

  <script>
    document.addEventListener("DOMContentLoaded", () => {
      const chatMessages = document.getElementById("chat-messages");
      const userInput = document.getElementById("user-input");
      const sendButton = document.getElementById("send-button");

      function appendMessage(sender, message) {
        const messageDiv = document.createElement("div");
        messageDiv.className = "message";
        messageDiv.innerHTML = `<strong>${sender}:</strong> ${message}`;
        chatMessages.appendChild(messageDiv);
        chatMessages.scrollTop = chatMessages.scrollHeight;
      }

      function getChatbotResponse(input) {
        const apiKey = "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"; // Replace with your actual API key
        const url = "https://api.openai.com/v1/engines/davinci-codex/completions";

        fetch(url, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            "Authorization": `Bearer ${apiKey}`
          },
          body: JSON.stringify({
            prompt: input,
            max_tokens: 50
          })
        })
        .then(response => response.json())
        .then(data => {
          const botResponse = data.choices[0].text.trim();
          appendMessage("Chatbot", botResponse);
        })
        .catch(error => {
          console.error("Error:", error);
        });
      }

      sendButton.addEventListener("click", () => {
        const userMessage = userInput.value.trim();
        if (userMessage !== "") {
          appendMessage("You", userMessage);
          userInput.value = "";
          getChatbotResponse(userMessage);
        }
      });

      userInput.addEventListener("keydown", event => {
        if (event.key === "Enter") {
          event.preventDefault();
          sendButton.click();
        }
      });
    });
  </script>
</body>
</html>
