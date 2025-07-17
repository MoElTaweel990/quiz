
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Fun English Quiz!</title>
    <link href="https://fonts.googleapis.com/css2?family=Boogaloo&family=Kalam:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        /* Colors: Sky Blue #A7D7F5, Sunny Yellow #FFD700, Grass Green #8BC34A, Light Pink #FFC0CB */
        body {
            font-family: 'Kalam', cursive; /* Playful font */
            background: linear-gradient(to bottom right, #A7D7F5, #FFC0CB); /* Gradient background */
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
            box-sizing: border-box;
            overflow-x: hidden; /* Prevent horizontal scrollbar */
        }
        .quiz-container {
            background-color: #fff;
            padding: 30px 40px;
            border-radius: 25px; /* More rounded corners */
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2); /* Clearer shadow */
            width: 100%;
            max-width: 800px;
            text-align: center;
            border: 5px solid #FFD700; /* Attractive border color */
            position: relative; /* For absolute positioning of graphics */
        }
        /* ---- ADD YOUR CUSTOM GRAPHICS HERE! ---- */
        /* Example: A star graphic in the top-left corner */
        .quiz-container::before {
            content: '';
            position: absolute;
            top: -20px;
            left: -20px;
            width: 80px;
            height: 80px;
            background-image: url('https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Star_icon_stylized.svg/1200px-Star_icon_stylized.svg.png'); /* Replace with your star image URL */
            background-size: contain;
            background-repeat: no-repeat;
            z-index: 1; /* To appear above the background */
        }
        /* Example: A balloon graphic in the bottom-right corner */
        .quiz-container::after {
            content: '';
            position: absolute;
            bottom: -20px;
            right: -20px;
            width: 100px;
            height: 100px;
            background-image: url('https://www.freeiconspng.com/uploads/balloon-png-image-0.png'); /* Replace with your balloon image URL */
            background-size: contain;
            background-repeat: no-repeat;
            z-index: 1;
        }
        /* ---------------------------------- */

        h1 {
            font-family: 'Boogaloo', cursive; /* Special font for the title */
            color: #E6007A; /* Vibrant pink color */
            margin-bottom: 25px;
            font-size: 3em; /* Large title size */
            text-shadow: 2px 2px #FFD700; /* Shadow for the title */
        }
        .question {
            margin-bottom: 25px;
            text-align: left;
            background-color: #F8F8F8; /* Light background for the question */
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
            border: 2px dashed #8BC34A; /* Green dashed border */
        }
        .question p {
            font-size: 1.5em; /* Larger font size for the question */
            margin-bottom: 15px;
            color: #4A148C; /* Dark purple color */
            font-weight: bold;
            display: flex;
            align-items: center;
        }
        .question p i { /* Icons next to the question */
            margin-right: 10px;
            color: #FFD700; /* Yellow color for icons */
        }
        .options label {
            display: flex; /* To align options and icons */
            align-items: center;
            margin-bottom: 12px;
            cursor: pointer;
            padding: 12px 15px;
            background-color: #E1F5FE; /* Very light blue for options */
            border-radius: 10px;
            transition: background-color 0.2s, transform 0.2s;
            border: 1px solid #A7D7F5;
            font-size: 1.2em; /* Option font size */
            color: #333;
        }
        .options label:hover {
            background-color: #C1E9FE; /* Darker blue on hover */
            transform: translateY(-3px); /* Slight lift on hover */
        }
        .options input[type="radio"] {
            margin-right: 15px;
            transform: scale(1.5); /* Enlarge radio buttons */
        }
        .feedback {
            margin-top: 10px;
            font-weight: bold;
            font-size: 1.3em; /* Feedback font size */
            text-shadow: 1px 1px #fff;
        }
        .correct {
            color: #28A745; /* Bright green */
        }
        .incorrect {
            color: #DC3545; /* Bright red */
        }
        .fill-in-blank input[type="text"] {
            width: 80%;
            padding: 10px;
            margin-top: 5px;
            border: 2px solid #A7D7F5; /* Blue border */
            border-radius: 10px;
            font-size: 1.2em;
            font-family: 'Kalam', cursive;
            outline: none; /* Remove outline on focus */
        }
        .fill-in-blank input[type="text"]:focus {
            border-color: #FFD700; /* Change border color on focus */
            box-shadow: 0 0 8px rgba(255, 215, 0, 0.5);
        }
        button {
            background-color: #E6007A; /* Cheerful button color */
            color: white;
            padding: 15px 35px;
            border: none;
            border-radius: 15px;
            cursor: pointer;
            font-size: 1.5em; /* Large button font size */
            margin-top: 30px;
            transition: background-color 0.3s ease, transform 0.2s;
            font-family: 'Boogaloo', cursive; /* Playful button font */
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
        }
        button:hover {
            background-color: #CC0066; /* Darker color on hover */
            transform: translateY(-3px); /* Slight lift on hover */
        }
        #results {
            margin-top: 30px;
            font-size: 1.8em; /* Large results font size */
            font-weight: bold;
            color: #4A148C; /* Purple for results */
            text-shadow: 1px 1px #FFD700;
        }
        .contact-link {
            margin-top: 30px;
            font-size: 1.2em;
            color: #555;
        }
        .contact-link a {
            color: #25D366; /* WhatsApp green */
            text-decoration: none;
            font-weight: bold;
            transition: color 0.2s;
        }
        .contact-link a:hover {
            text-decoration: underline;
            color: #1DA851;
        }
        .contact-link i { /* WhatsApp icon */
            margin-right: 8px;
            color: #25D366;
        }

        /* Additional character graphic example */
        .cute-character {
            position: absolute;
            top: 50px; /* Adjust position */
            right: -80px; /* Adjust position */
            width: 150px;
            height: 150px;
            background-image: url('https://www.pngwing.com/png/963/279/png-transparent-little-boy-little-boy.png'); /* Replace with your character image URL */
            background-size: contain;
            background-repeat: no-repeat;
            z-index: 2; /* Ensure it appears above everything */
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <div class="cute-character"></div> <h1><i class="fas fa-magic"></i> The Fun English Quiz! <i class="fas fa-star"></i></h1>
        <div id="quiz">
            </div>
        <button id="submitBtn"><i class="fas fa-paper-plane"></i> I'm Done! Show My Score</button>
        <div id="results"></div>
        <div class="contact-link">
            <i class="fab fa-whatsapp"></i> Need help or have questions? Contact us on WhatsApp: <a href="https://wa.me/201117112423" target="_blank">Chat on WhatsApp</a>
        </div>
    </div>

    <script>
        const questions = [
            {
                type: "multiple-choice",
                level: "child",
                question: "What is the opposite of 'big'?",
                options: ["small", "tall", "fast", "happy"],
                answer: "small",
                icon: "fas fa-child" /* Icon for the question */
            },
            {
                type: "fill-in-blank",
                level: "child",
                question: "The sky is ____ (color).",
                answer: "blue",
                icon: "fas fa-cloud"
            },
            {
                type: "true-false",
                level: "child",
                question: "A cat says 'woof'.",
                answer: "false",
                icon: "fas fa-cat"
            },
            {
                type: "multiple-choice",
                level: "adult",
                question: "Choose the grammatically correct sentence:",
                options: [
                    "She go to the store yesterday.",
                    "She went to the store yesterday.",
                    "She goes to the store yesterday.",
                    "She going to the store yesterday."
                ],
                answer: "She went to the store yesterday.",
                icon: "fas fa-brain"
            },
            {
                type: "fill-in-blank",
                level: "adult",
                question: "The passive voice is formed with a form of 'to be' and the past ____ of the main verb.",
                answer: "participle",
                icon: "fas fa-pencil-alt"
            },
            {
                type: "true-false",
                level: "adult",
                question: "'Affect' is typically a verb, while 'effect' is typically a noun.",
                answer: "true",
                icon: "fas fa-lightbulb"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "How many legs does a dog have?",
                options: ["two", "four", "six", "eight"],
                answer: "four",
                icon: "fas fa-dog"
            },
            {
                type: "fill-in-blank",
                level: "child",
                question: "I like to eat ____ (fruit, red and round).",
                answer: "apple",
                icon: "fas fa-apple-alt"
            },
            {
                type: "true-false",
                level: "child",
                question: "Birds can fly.",
                answer: "true",
                icon: "fas fa-dove"
            },
            {
                type: "multiple-choice",
                level: "adult",
                question: "Which of these is a synonym for 'ubiquitous'?",
                options: ["rare", "common", "unique", "scarce"],
                answer: "common",
                icon: "fas fa-language"
            },
            {
                type: "fill-in-blank",
                level: "adult",
                question: "The idiom 'break a ____' means good luck.",
                answer: "leg",
                icon: "fas fa-book"
            },
            {
                type: "true-false",
                level: "adult",
                question: "The word 'literally' can sometimes be used figuratively in informal speech.",
                answer: "true",
                icon: "fas fa-quote-right"
            }
        ];

        const quizDiv = document.getElementById('quiz');
        const submitButton = document.getElementById('submitBtn');
        const resultsDiv = document.getElementById('results');
        let score = 0;
        let answeredQuestions = 0;

        function renderQuestions() {
            quizDiv.innerHTML = ''; // Clear previous questions
            questions.forEach((q, index) => {
                const questionElement = document.createElement('div');
                questionElement.classList.add('question');
                
                // Add icon to the question
                const questionText = `<p><i class="${q.icon}"></i> ${index + 1}. ${q.question} <span style="font-size:0.8em; color:#888;">(${q.level === 'child' ? 'For Kids' : 'For Adults'})</span></p>`;
                questionElement.innerHTML = questionText;

                if (q.type === "multiple-choice") {
                    const optionsDiv = document.createElement('div');
                    optionsDiv.classList.add('options');
                    q.options.forEach(option => {
                        optionsDiv.innerHTML += `
                            <label>
                                <input type="radio" name="question${index}" value="${option}">
                                ${option}
                            </label>
                        `;
                    });
                    questionElement.appendChild(optionsDiv);
                } else if (q.type === "fill-in-blank") {
                    const fillInBlankDiv = document.createElement('div');
                    fillInBlankDiv.classList.add('fill-in-blank');
                    fillInBlankDiv.innerHTML = `<input type="text" id="q${index}" placeholder="Type your answer here">`;
                    questionElement.appendChild(fillInBlankDiv);
                } else if (q.type === "true-false") {
                    const optionsDiv = document.createElement('div');
                    optionsDiv.classList.add('options');
                    optionsDiv.innerHTML += `
                        <label>
                            <input type="radio" name="question${index}" value="true">
                            True
                        </label>
                        <label>
                            <input type="radio" name="question${index}" value="false">
                            False
                        </label>
                    `;
                    questionElement.appendChild(optionsDiv);
                }
                const feedbackElement = document.createElement('div');
                feedbackElement.classList.add('feedback');
                feedbackElement.id = `feedback-${index}`;
                questionElement.appendChild(feedbackElement);
                quizDiv.appendChild(questionElement);
            });
        }

        function checkAnswer(question, userAnswer, index) {
            const feedbackElement = document.getElementById(`feedback-${index}`);
            let isCorrect = false;

            if (question.type === "multiple-choice" || question.type === "true-false") {
                isCorrect = (userAnswer === question.answer);
            } else if (question.type === "fill-in-blank") {
                isCorrect = (userAnswer.toLowerCase().trim() === question.answer.toLowerCase().trim());
            }

            if (isCorrect) {
                feedbackElement.textContent = "Correct! Great job!";
                feedbackElement.classList.remove('incorrect');
                feedbackElement.classList.add('correct');
                return true;
            } else {
                feedbackElement.textContent = `Incorrect. The correct answer was: ${question.answer}`;
                feedbackElement.classList.remove('correct');
                feedbackElement.classList.add('incorrect');
                return false;
            }
        }

        submitButton.addEventListener('click', () => {
            score = 0;
            answeredQuestions = 0;
            questions.forEach((q, index) => {
                let userAnswer = '';
                if (q.type === "multiple-choice" || q.type === "true-false") {
                    const selectedOption = document.querySelector(`input[name="question${index}"]:checked`);
                    if (selectedOption) {
                        userAnswer = selectedOption.value;
                        answeredQuestions++;
                    }
                } else if (q.type === "fill-in-blank") {
                    const inputField = document.getElementById(`q${index}`);
                    if (inputField && inputField.value.trim() !== '') {
                        userAnswer = inputField.value;
                        answeredQuestions++;
                    }
                }

                // Only provide feedback if the user attempted to answer the question
                if (userAnswer) {
                    if (checkAnswer(q, userAnswer, index)) {
                        score++;
                    }
                } else {
                     // Clear any previous feedback if the question wasn't answered
                    const feedbackElement = document.getElementById(`feedback-${index}`);
                    feedbackElement.textContent = "Please answer this question.";
                    feedbackElement.classList.remove('correct', 'incorrect');
                }
            });

            if (answeredQuestions === questions.length) {
                resultsDiv.textContent = `You scored ${score} out of ${questions.length} questions! Awesome!`;
            } else {
                resultsDiv.textContent = `Please answer all questions to see your final score. You have answered ${answeredQuestions} out of ${questions.length} questions so far.`;
            }
        });

        renderQuestions();
    </script>
</body>
</html>
