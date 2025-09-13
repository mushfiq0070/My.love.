<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>আমার প্রশ্ন – Prank Version</title>
<style>
  body {
    font-family: 'Arial', sans-serif;
    margin: 0;
    padding: 0;
    overflow: hidden;
    height: 100vh;
    background: linear-gradient(120deg, #fbc2eb, #a6c1ee);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container {
    background-color: #ffffffcc;
    padding: 30px 25px;
    border-radius: 15px;
    text-align: center;
    box-shadow: 0 8px 25px rgba(0,0,0,0.3);
    max-width: 400px;
    width: 90%;
  }

  h1 {
    font-size: 2rem;
    color: #333;
    margin-bottom: 25px;
  }

  .buttons button {
    padding: 12px 25px;
    font-size: 18px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: all 0.2s ease;
    position: relative;
  }

  #yesButton {
    background-color: #4CAF50;
    color: white;
  }
  #yesButton:hover {
    transform: scale(1.1);
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
  }

  #noButton {
    background-color: #f44336;
    color: white;
  }
  #noButton:hover {
    transform: scale(1.1);
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
  }

  #message {
    font-size: 1.5rem;
    margin-top: 20px;
    color: #333;
  }

  #videoContainer {
    margin-top: 20px;
    width: 100%;
    border-radius: 10px;
    overflow: hidden;
  }
  #videoPlayer {
    width: 100%;
    height: 250px;
    border: none;
  }

  @media(min-width:600px){
    #videoPlayer { height: 315px; }
  }
</style>
</head>
<body>

<div class="container" id="container">
  <h1 id="question">তুমি কি আমাকে ভালোবাসো? ❤️</h1>
  <div class="buttons">
    <button id="yesButton">হ্যাঁ</button>
    <button id="noButton">না</button>
  </div>
  <p id="message"></p>
  <div id="videoContainer" style="display:none;">
    <iframe id="videoPlayer" src="" allowfullscreen allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"></iframe>
  </div>
</div>

<script>
const noButton = document.getElementById('noButton');
const yesButton = document.getElementById('yesButton');
const message = document.getElementById('message');
const question = document.getElementById('question');
const videoContainer = document.getElementById('videoContainer');
const videoPlayer = document.getElementById('videoPlayer');
const container = document.getElementById('container');

const noMessages = [
  "না", "আরেকবার ভাবো...", "দয়া করে হ্যাঁ বলো! 🙏",
  "আমার মন ভেঙে যাবে 💔", "শেষ সুযোগ! 🥺", "প্লিজ!",
  "ভালোবাসো না বুঝি? 😔", "আমি রাগ করবো! 😠", "সত্যি করে বলো..."
];

let currentNoIndex = 0;

// No বাটনের প্রাঙ্ক
function moveNoButton() {
  const maxX = window.innerWidth - noButton.offsetWidth - 20;
  const maxY = window.innerHeight - noButton.offsetHeight - 20;
  const newX = Math.random() * maxX;
  const newY = Math.random() * maxY;
  noButton.style.position = 'absolute';
  noButton.style.left = `${newX}px`;
  noButton.style.top = `${newY}px`;
  noButton.textContent = noMessages[currentNoIndex];
  currentNoIndex = (currentNoIndex + 1) % noMessages.length;
}

// Mouse move event দিয়ে নো বাটনকে এড়ানো
noButton.addEventListener('mouseenter', moveNoButton);

yesButton.addEventListener('click', () => {
  question.style.display = 'none';
  yesButton.style.display = 'none';
  noButton.style.display = 'none';
  message.innerHTML = "আমি জানতাম তুমি আমাকে ভালোবাসো! 🥰💖😍";
  videoContainer.style.display = 'block';
  videoPlayer.src = "https://www.youtube.com/embed/gwA1t5jxTbY?autoplay=1";
});

window.onload = () => {
  moveNoButton();
};
</script>

</body>
</html>
