# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  
**html**

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JavaScript Playground</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Interactive JavaScript Playground</h1>

    <!-- Event Handling Section -->
    <button id="clickButton">Click Me</button><br><br>

    <button id="hoverButton">Hover Over Me</button><br><br>

    <input type="text" id="keyPressInput" placeholder="Press any key" /><br><br>

    <button id="doubleClickButton">Double-click or Long Press Me</button><br><br>

    <!-- Interactive Elements Section -->
    <button id="changeTextButton">Click to Change Text</button><br><br>

    <img id="galleryImage" src="image1.jpg" alt="Gallery Image" width="300"><br><br>
    <button id="nextButton">Next Image</button><br><br>

    <div class="tabs">
        <div class="tab">Tab 1</div>
        <div class="tab">Tab 2</div>
        <div class="tab">Tab 3</div>
    </div><br><br>

    <!-- Form Validation Section -->
    <form id="myForm">
        <input type="text" id="requiredField" placeholder="Required Field"><br><br>
        <input type="email" id="email" placeholder="Enter your email"><br><br>
        <input type="password" id="password" placeholder="Password"><br><br>
        <span id="passwordFeedback"></span><br><br>
        <input type="submit" value="Submit">
    </form>

    <script src="script.js"></script>
</body>
</html>

**style.css**

/* Style for tab */
.tab {
  display: inline-block;
  padding: 10px;
  background-color: lightgray;
  margin: 5px;
  cursor: pointer;
}

.tab.active {
  background-color: #4CAF50;
  color: white;
}

/* Style for buttons */
button {
  padding: 10px 20px;
  margin: 5px;
  cursor: pointer;
}

/* Hover effect */
button:hover {
  background-color: #ddd;
}

/* Styling for image gallery */
#galleryImage {
  transition: all 0.3s ease;
}

#galleryImage:hover {
  transform: scale(1.1);
}
**script.js**
// 1. Event Handling

// Button Click
const button = document.getElementById("clickButton");
button.addEventListener("click", () => {
  alert("Button clicked!");
});

// Hover Effects
const hoverButton = document.getElementById("hoverButton");
hoverButton.addEventListener("mouseover", () => {
  hoverButton.style.backgroundColor = "blue";
});
hoverButton.addEventListener("mouseout", () => {
  hoverButton.style.backgroundColor = "";
});

// Keypress Detection
const keyPressInput = document.getElementById("keyPressInput");
keyPressInput.addEventListener("keydown", (event) => {
  console.log(`Key pressed: ${event.key}`);
});

// Bonus: Double-click or Long Press
let pressTimer;
const doubleClickButton = document.getElementById("doubleClickButton");

doubleClickButton.addEventListener("mousedown", () => {
  pressTimer = setTimeout(() => {
    alert("Long press detected!");
  }, 1000); // Long press detected after 1 second
});

doubleClickButton.addEventListener("mouseup", () => {
  clearTimeout(pressTimer); // Cancels the long press action if mouse is released early
});

doubleClickButton.addEventListener("dblclick", () => {
  alert("Double-click detected!");
});

// 2. Interactive Elements

// Button that changes text or color
const changeTextButton = document.getElementById("changeTextButton");
changeTextButton.addEventListener("click", () => {
  changeTextButton.textContent = "You clicked me!";
  changeTextButton.style.backgroundColor = "green";
});

// Image Gallery or Slideshow
let currentImage = 0;
const images = ["image1.jpg", "image2.jpg", "image3.jpg"];
const imgElement = document.getElementById("galleryImage");

document.getElementById("nextButton").addEventListener("click", () => {
  currentImage = (currentImage + 1) % images.length;
  imgElement.src = images[currentImage];
});

// Tabs
const tabs = document.querySelectorAll(".tab");
tabs.forEach(tab => {
  tab.addEventListener("click", () => {
    tabs.forEach(t => t.classList.remove("active"));
    tab.classList.add("active");
  });
});

// 3. Form Validation

// Required Field Check
const form = document.getElementById("myForm");
form.addEventListener("submit", (event) => {
  const requiredField = document.getElementById("requiredField");
  if (!requiredField.value) {
    alert("This field is required!");
    event.preventDefault(); // Prevent form submission
  }
});

// Email Format Validation
const emailInput = document.getElementById("email");
emailInput.addEventListener("input", () => {
  const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (!emailPattern.test(emailInput.value)) {
    emailInput.setCustomValidity("Invalid email format");
  } else {
    emailInput.setCustomValidity("");
  }
});

// Password Rules (min 8 characters)
const passwordInput = document.getElementById("password");
passwordInput.addEventListener("input", () => {
  if (passwordInput.value.length < 8) {
    passwordInput.setCustomValidity("Password must be at least 8 characters");
  } else {
    passwordInput.setCustomValidity("");
  }
});

// Real-time Feedback for Password
const passwordFeedback = document.getElementById("passwordFeedback");
passwordInput.addEventListener("input", () => {
  if (passwordInput.value.length < 8) {
    passwordFeedback.textContent = "Password is too short.";
  } else {
    passwordFeedback.textContent = "Password is long enough.";
  }
});

