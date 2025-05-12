# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Interactive Animations</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <button id="animateBtn">Click Me!</button>
  <img id="animatedImg" src="https://via.placeholder.com/150" alt="Sample Image" />
  <script src="script.js"></script>
</body>
</html>


/* styles.css */
button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #2196f3;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

button:hover {
  background-color: #0b7dda;
  transform: scale(1.05);
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

img {
  display: block;
  margin: 20px auto;
  width: 150px;
  height: 150px;
  opacity: 0;
  animation: fadeIn 2s forwards;
}


// script.js

// Function to save user preferences to localStorage
function saveUserPreferences(preferences) {
  localStorage.setItem('userPreferences', JSON.stringify(preferences));
}

// Function to retrieve user preferences from localStorage
function getUserPreferences() {
  const preferences = localStorage.getItem('userPreferences');
  return preferences ? JSON.parse(preferences) : {};
}

// Function to apply saved preferences
function applyPreferences() {
  const preferences = getUserPreferences();
  const button = document.getElementById('animateBtn');
  if (preferences.buttonColor) {
    button.style.backgroundColor = preferences.buttonColor;
  }
}

// Function to trigger animation on the image
function triggerImageAnimation() {
  const image = document.getElementById('animatedImg');
  image.style.animation = 'none'; // Reset animation
  void image.offsetWidth; // Trigger reflow
  image.style.animation = 'fadeIn 2s forwards';
}

// Event listener for button click
document.addEventListener('DOMContentLoaded', () => {
  const button = document.getElementById('animateBtn');

  // Apply saved preferences on load
  applyPreferences();

  button.addEventListener('click', () => {
    // Change button color
    button.style.backgroundColor = '#4caf50';

    // Save preference
    saveUserPreferences({ buttonColor: '#4caf50' });

    // Trigger image animation
    triggerImageAnimation();
  });
});
