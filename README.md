<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>SmartSolve AI Demo</title>
<style>
  body {
    font-family: Arial, sans-serif;
    max-width: 600px;
    margin: 40px auto;
    padding: 20px;
    background: #f7f7f7;
  }
  h1 {
    text-align: center;
    color: #333;
  }
  #chatbox {
    border: 1px solid #ccc;
    background: #fff;
    height: 400px;
    overflow-y: auto;
    padding: 10px;
    margin-bottom: 10px;
  }
  .message {
    margin: 10px 0;
  }
  .user {
    text-align: right;
    color: blue;
  }
  .bot {
    text-align: left;
    color: green;
  }
  #userInput {
    width: 100%;
    padding: 10px;
    font-size: 16px;
  }
  #sendBtn {
    padding: 10px 20px;
    font-size: 16px;
    margin-top: 5px;
    cursor: pointer;
  }
</style>
</head>
<body>

<h1>SmartSolve AI Demo</h1>
<div id="chatbox"></div>
<input type="text" id="userInput" placeholder="আপনার প্রশ্ন লিখুন..." />
<button id="sendBtn">Send</button>

<script>
  const chatbox = document.getElementById('chatbox');
  const userInput = document.getElementById('userInput');
  const sendBtn = document.getElementById('sendBtn');

  function appendMessage(text, className) {
    const div = document.createElement('div');
    div.className = 'message ' + className;
    div.textContent = text;
    chatbox.appendChild(div);
    chatbox.scrollTop = chatbox.scrollHeight;
  }

  function getBotResponse(userText) {
    // সিমুলেটেড বা ফিক্সড উত্তর, পরে চাইলে উন্নত করা যাবে
    const lower = userText.toLowerCase();
    if (lower.includes('hello')) return 'Hello! How can I help you today?';
    if (lower.includes('problem')) return 'Please describe your problem in detail.';
    if (lower.includes('thanks')) return 'You’re welcome!';
    return "Sorry, I don't understand. Can you ask something else?";
  }

  sendBtn.addEventListener('click', () => {
    const text = userInput.value.trim();
    if (!text) return;
    appendMessage('You: ' + text, 'user');
    const botReply = getBotResponse(text);
    setTimeout(() => appendMessage('SmartSolve AI: ' + botReply, 'bot'), 500);
    userInput.value = '';
    userInput.focus();
  });

  userInput.addEventListener('keypress', (e) => {
    if (e.key === 'Enter') sendBtn.click();
  });
</script>

</body>
</html>
