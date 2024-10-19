<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inclusive Learning</title>
    <style>
        /* Basic Styling for the Website */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #4CAF50;
            color: white;
            padding: 10px 0;
            text-align: center;
        }

        nav ul {
            list-style: none;
            padding: 0;
        }

        nav ul li {
            display: inline;
            margin: 0 10px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
        }

        .banner {
            background-color: #f0f0f0;
            padding: 50px;
            text-align: center;
        }

        /* User Categories Section */
        .user-categories {
            display: flex;
            justify-content: center;
            margin: 20px;
        }

        .category-box {
            border: 2px solid #ccc;
            padding: 20px;
            margin: 10px;
            width: 250px;
            text-align: center;
            transition: 0.3s;
            cursor: pointer;
        }

        .category-box:hover {
            background-color: #4CAF50;
            color: white;
            border: none;
        }

        .accessibility-features {
            margin: 20px;
        }

        label {
            display: block;
            margin-bottom: 10px;
        }

        .courses {
            padding: 20px;
        }

        .course {
            border: 1px solid #ccc;
            padding: 20px;
            margin-bottom: 10px;
        }

        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 10px;
            position: relative;
            bottom: 0;
            width: 100%;
        }

        .contact-us {
            margin: 20px;
        }

        /* High Contrast Mode */
        .high-contrast {
            background-color: black;
            color: yellow;
        }

        /* Dyslexia-Friendly Mode */
        .dyslexia-mode {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            letter-spacing: 0.1em;
        }
    </style>
</head>
<body>

    <!-- Header Section -->
    <header>
        <div class="logo">
            <!-- Placeholder for Logo -->
            <h1>Inclusive Learning</h1>
        </div>
        <nav>
            <ul>
                <li><a href="#">Home</a></li>
                <li><a href="#">About Us</a></li>
                <li><a href="#">Courses</a></li>
                <li><a href="#">Accessibility Features</a></li>
                <li><a href="#">Contact Us</a></li>
            </ul>
        </nav>
    </header>

    <!-- Main Banner -->
    <section class="banner">
        <h2>Empowering Every Learner, Regardless of Ability</h2>
        <button onclick="startLearning()">Get Started</button>
        <button onclick="learnMore()">Learn More</button>
    </section>

    <!-- User Categories: Visually Impaired, Hearing Impaired, Dyslexic -->
    <section class="user-categories">
        <div class="category-box" id="visuallyImpairedBox" onclick="selectCategory('visuallyImpaired')">
            <h3>Visually Impaired</h3>
            <p>Enable text-to-speech and audio descriptions for content.</p>
        </div>
        <div class="category-box" id="hearingImpairedBox" onclick="selectCategory('hearingImpaired')">
            <h3>Hearing Impaired</h3>
            <p>Sign language interpretation and subtitles for videos.</p>
        </div>
        <div class="category-box" id="dyslexicBox" onclick="selectCategory('dyslexic')">
            <h3>Dyslexic</h3>
            <p>Enable dyslexia-friendly fonts and customized reading modes.</p>
        </div>
    </section>

    <!-- Accessibility Customization -->
    <section class="accessibility-features">
        <h3>Accessibility Features</h3>
        <label>
            <input type="checkbox" id="textToSpeech" onclick="toggleTextToSpeech()"> Enable Text-to-Speech
        </label>
        <label>
            <input type="checkbox" id="highContrast" onclick="toggleHighContrast()"> High Contrast Mode
        </label>
        <label>
            <input type="checkbox" id="signLanguage" onclick="toggleSignLanguage()"> Sign Language Interpretation
        </label>
        <label>
            <input type="checkbox" id="dyslexiaMode" onclick="toggleDyslexiaMode()"> Dyslexia-Friendly Mode
        </label>
    </section>

    <!-- Contact Us -->
    <section class="contact-us">
        <h3>Contact Us</h3>
        <form id="contactForm">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
            <label for="message">Message:</label>
            <textarea id="message" name="message" required></textarea>
            <button type="submit">Submit</button>
        </form>
    </section>

    <footer>
        <p>&copy; 2024 Inclusive Learning | All Rights Reserved</p>
    </footer>

    <script>
        // Text-to-Speech Functionality
        function toggleTextToSpeech() {
            const isChecked = document.getElementById('textToSpeech').checked;
            if (isChecked) {
                document.body.addEventListener('click', speakText);
            } else {
                document.body.removeEventListener('click', speakText);
            }
        }

        function speakText(event) {
            if (event.target.tagName === 'P' || event.target.tagName === 'H4') {
                const text = event.target.textContent;
                const utterance = new SpeechSynthesisUtterance(text);
                speechSynthesis.speak(utterance);
            }
        }

        // High Contrast Mode
        function toggleHighContrast() {
            const isChecked = document.getElementById('highContrast').checked;
            if (isChecked) {
                document.body.classList.add('high-contrast');
            } else {
                document.body.classList.remove('high-contrast');
            }
        }

        // Sign Language Interpretation (Mock function for demo)
        function toggleSignLanguage() {
            const isChecked = document.getElementById('signLanguage').checked;
            if (isChecked) {
                alert('Sign Language Interpretation Enabled (Simulation)');
            } else {
                alert('Sign Language Interpretation Disabled (Simulation)');
            }
        }

        // Dyslexia-Friendly Mode
        function toggleDyslexiaMode() {
            const isChecked = document.getElementById('dyslexiaMode').checked;
            if (isChecked) {
                document.body.classList.add('dyslexia-mode');
            } else {
                document.body.classList.remove('dyslexia-mode');
            }
        }

        // Function to Select a Category and Apply Related Features
        function selectCategory(category) {
            switch (category) {
                case 'visuallyImpaired':
                    document.getElementById('textToSpeech').checked = true;
                    toggleTextToSpeech();
                    break;
                case 'hearingImpaired':
                    document.getElementById('signLanguage').checked = true;
                    toggleSignLanguage();
                    break;
                case 'dyslexic':
                    document.getElementById('dyslexiaMode').checked = true;
                    toggleDyslexiaMode();
                    break;
                default:
                    break;
            }
        }

        // Additional Placeholder Functions
        function startLearning() {
            alert("Redirecting to Learning Path...");
        }

        function learnMore() {
            alert("More Information About Inclusive Learning...");
        }
    </script>
</body>
</html>
