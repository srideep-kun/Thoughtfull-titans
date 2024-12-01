# Thoughtfull-titans 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thoughtful Titans</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(to bottom, #FF9933, #138808, #ffffff);
            text-align: center;
            margin: 0;
            padding: 0;
            color: #000;
        }

        header {
            background-color: #f1f1f1;
            padding: 20px;
        }

        h1 {
            font-size: 2.5em;
            margin-bottom: 0;
        }

        .video-container {
            margin-top: 40px;
            max-width: 80%;
            margin-left: auto;
            margin-right: auto;
            padding: 20px;
            background-color: #000;
        }

        iframe {
            width: 100%;
            height: 500px;
        }

        .ai-assistant {
            background-color: #fff;
            padding: 20px;
            margin-top: 30px;
            border-radius: 10px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .ai-assistant h3 {
            color: #000;
            margin-bottom: 20px;
        }

        .question-container {
            margin-bottom: 20px;
        }

        .question-container input[type="text"] {
            width: 80%;
            padding: 10px;
            font-size: 16px;
            margin-bottom: 10px;
        }

        .question-container button {
            padding: 10px 20px;
            font-size: 16px;
            background-color: #4CAF50;
            color: #fff;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }

        .question-container button:hover {
            background-color: #45a049;
        }

        .answer-section {
            margin-top: 20px;
            text-align: left;
        }

        .answer-section p {
            font-size: 18px;
            line-height: 1.6;
        }

        .feedback {
            background-color: #fff;
            padding: 20px;
            margin-top: 40px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .feedback textarea {
            width: 100%;
            height: 150px;
            padding: 10px;
            font-size: 16px;
        }

        .feedback button {
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
            font-size: 16px;
            margin-top: 10px;
        }

        .feedback button:hover {
            background-color: #45a049;
        }

        footer {
            background-color: #333;
            color: white;
            padding: 10px;
            text-align: center;
        }

    </style>
</head>
<body>
    <header>
        <h1>Thoughtful Titans</h1>
        <p>By Srideep Subuddhi, Ridit Dash, and Subhalaxmi Mohanty</p>
    </header>

    <div class="video-container">
        <h2>Watch the Video:</h2>
        <!-- Embed the video -->
        <iframe src="https://www.youtube.com/embed/3D3cIS7rucc?si=S48JZvplxv-VI9ws" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>

    <div class="ai-assistant">
        <h3>Ask Bharati (AI Assistant)</h3>
        <div class="question-container">
            <label for="question">Ask a question about the video:</label><br>
            <input type="text" id="question" placeholder="Ask anything...">
            <button onclick="getAnswer()">Ask</button>
        </div>

        <div class="answer-section" id="answer-section">
            <p><strong>Bharati's Answer:</strong></p>
            <p id="answer">Ask a question to get an answer from Bharati!</p>
        </div>
    </div>

    <div class="feedback">
        <h3>Provide Feedback</h3>
        <textarea placeholder="Enter your feedback here..."></textarea>
        <br>
        <button onclick="submitFeedback()">Submit Feedback</button>
    </div>

    <footer>
        <p>&copy; 2024 Thoughtful Titans. All Rights Reserved.</p>
    </footer>

    <script>
        // Predefined responses for demonstration purposes.
        const predefinedAnswers = {
            "who are the authors": "The authors are Srideep Subuddhi, Ridit Dash, and Subhalaxmi Mohanty.",
            "what is the video about": "This video discusses the 'Thoughtful Titans' project, focusing on its concepts and ideas.",
            "what is bharati": "Bharati is an AI assistant developed to answer your questions about the video.",
            "where can i watch the video": "You can watch the video right here on this page or visit the YouTube link provided.",
            "what is the main theme": "The video covers the main theme of innovation, thoughtfulness, and the impact of the 'Thoughtful Titans' project.",
            "who created the video": "The video was created by Srideep Subuddhi, Ridit Dash, and Subhalaxmi Mohanty.",
            "why was this video made": "The video was made to showcase the ideas and discussions around the Thoughtful Titans initiative.",
            "how can i learn more": "You can learn more by visiting the website or by watching the rest of the content shared by the authors.",
            "is the ai real": "Bharati is an AI system that provides answers based on programmed information and cannot interact like a human.",
            "what is the purpose of this project": "The project aims to foster innovative thinking and thoughtful contributions in various fields.",
            "how long is the video": "The video is approximately 10 minutes long.",
            "who are the target audience": "The target audience includes individuals interested in innovation, technology, and creative thought processes.",
            "is the project available globally": "Yes, the project is available to viewers globally through the online platform.",
            "how can i participate in the project": "You can participate by following the instructions provided in the video and visiting the official website.",
            "does the project involve technology": "Yes, the project makes use of technology to foster new ideas and collaborations.",
            "what makes this project unique": "The project's focus on thoughtful, innovative contributions sets it apart from others.",
            "is there a way to contact the creators": "Yes, you can contact the creators through the 'Contact Us' section on the official website.",
            "what challenges did the creators face": "The creators faced challenges in aligning creative thought with practical implementation.",
            "is this a student-led initiative": "Yes, this initiative is led by students who are passionate about making a difference.",
            "where is the project based": "The project is based in India but is open to global collaboration."
        };

        // Function to get the answer based on user input
        function getAnswer() {
            const question = document.getElementById('question').value.toLowerCase().trim();
            const answerElement = document.getElementById('answer');
            
            if (question === "") {
                answerElement.innerText = "Please ask a question about the video.";
                return;
            }

            // Search for a predefined answer
            const answer = predefinedAnswers[question] || "I'm sorry, I don't have an answer for that question right now.";
            
            // Display the answer
            answerElement.innerText = answer;
        }

        // Function to handle feedback submission
        function submitFeedback() {
            alert("Thank you for your feedback!");
        }
    </script>

</body>
</html>
