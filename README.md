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
        .player-name-section {
            margin-bottom: 30px;
            background-color: #ffe6f2; /* Light pink background */
            padding: 15px 20px;
            border-radius: 15px;
            border: 2px solid #FFC0CB; /* Pink border */
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
        }
        .player-name-section label {
            font-size: 1.3em;
            color: #E6007A;
            margin-bottom: 10px;
            display: block;
            font-weight: bold;
        }
        .player-name-section input[type="text"] {
            width: calc(100% - 20px); /* Adjust width for padding */
            padding: 10px;
            border: 2px solid #FFC0CB;
            border-radius: 8px;
            font-size: 1.1em;
            font-family: 'Kalam', cursive;
            outline: none;
            transition: border-color 0.3s, box-shadow 0.3s;
        }
        .player-name-section input[type="text"]:focus {
            border-color: #E6007A;
            box-shadow: 0 0 8px rgba(230, 0, 122, 0.3);
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
        .quiz-buttons {
            display: flex;
            justify-content: center;
            gap: 20px; /* Space between buttons */
            margin-top: 30px;
            flex-wrap: wrap; /* Allow buttons to wrap on smaller screens */
        }
        button {
            background-color: #E6007A; /* Cheerful button color */
            color: white;
            padding: 15px 25px;
            border: none;
            border-radius: 15px;
            cursor: pointer;
            font-size: 1.3em; /* Button font size */
            transition: background-color 0.3s ease, transform 0.2s;
            font-family: 'Boogaloo', cursive; /* Playful button font */
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px; /* Space between icon and text */
        }
        button:hover {
            background-color: #CC0066; /* Darker color on hover */
            transform: translateY(-3px); /* Slight lift on hover */
        }
        #shareBtn {
            background-color: #25D366; /* WhatsApp green for share button */
            display: none; /* Hidden by default */
        }
        #shareBtn:hover {
            background-color: #1DA851;
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

        <div class="player-name-section">
            <label for="playerName"><i class="fas fa-user-tag"></i> Enter Your Name:</label>
            <input type="text" id="playerName" placeholder="e.g., Sara or Ahmed" maxlength="30">
        </div>

        <div id="quiz">
            </div>
        <div class="quiz-buttons">
            <button id="submitBtn"><i class="fas fa-paper-plane"></i> I'm Done! Show My Score</button>
            <button id="shareBtn"><i class="fab fa-whatsapp"></i> Share Score on WhatsApp</button>
        </div>
        <div id="results"></div>
        <div class="contact-link">
            <i class="fab fa-whatsapp"></i> Need help or have questions? Contact us on WhatsApp: <a href="https://wa.me/201117112423" target="_blank">Chat on WhatsApp</a>
        </div>
    </div>

    <script>
        // Array of ALL possible questions (much larger than 150)
        const allQuestions = [
            // General Questions (Adult/Child)
            { type: "multiple-choice", level: "child", question: "What is the opposite of 'big'?", options: ["small", "tall", "fast", "happy"], answer: "small", answerMeaning: "صغير", icon: "fas fa-child" },
            { type: "fill-in-blank", level: "child", question: "The sky is ____ (color).", answer: "blue", answerMeaning: "أزرق", icon: "fas fa-cloud" },
            { type: "true-false", level: "child", question: "A cat says 'woof'.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-cat" },
            { type: "multiple-choice", level: "adult", question: "Choose the grammatically correct sentence:", options: ["She go to the store yesterday.", "She went to the store yesterday.", "She goes to the store yesterday.", "She going to the store yesterday."], answer: "She went to the store yesterday.", answerMeaning: "هي ذهبت إلى المتجر أمس.", icon: "fas fa-brain" },
            { type: "fill-in-blank", level: "adult", question: "The passive voice is formed with a form of 'to be' and the past ____ of the main verb.", answer: "participle", answerMeaning: "اسم المفعول", icon: "fas fa-pencil-alt" },
            { type: "true-false", level: "adult", question: "'Affect' is typically a verb, while 'effect' is typically a noun.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-lightbulb" },
            { type: "multiple-choice", level: "child", question: "How many legs does a dog have?", options: ["Two", "Four", "Six", "Eight"], answer: "Four", answerMeaning: "أربعة", icon: "fas fa-dog" },
            { type: "fill-in-blank", level: "child", question: "A bird can ____.", answer: "fly", answerMeaning: "يطير", icon: "fas fa-feather-alt" },
            { type: "true-false", level: "child", question: "The sun sets in the east.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-sun" },
            { type: "multiple-choice", level: "adult", question: "Which of these is a synonym for 'happy'?", options: ["Sad", "Joyful", "Angry", "Tired"], answer: "Joyful", answerMeaning: "مبتهج", icon: "fas fa-smile" },
            { type: "fill-in-blank", level: "adult", question: "A person who writes books is an ____.", answer: "author", answerMeaning: "مؤلف", icon: "fas fa-book-reader" },
            { type: "true-false", level: "adult", question: "Celsius is a unit of distance.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-thermometer-half" },
            { type: "multiple-choice", level: "adult", question: "What is the capital of France?", options: ["London", "Berlin", "Paris", "Rome"], answer: "Paris", answerMeaning: "باريس", icon: "fas fa-city" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'eat' is ____.", answer: "ate", answerMeaning: "أكل", icon: "fas fa-utensils" },
            { type: "true-false", level: "adult", question: "A peninsula is a piece of land almost surrounded by water but connected to the mainland on one side.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-globe-americas" },
            
            // Questions on English Letters A-Z
            // Letter A
            { type: "fill-in-blank", level: "child", question: "What is the first letter of the English alphabet?", answer: "A", answerMeaning: "الحرف الأول", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'A'?", options: ["Banana", "Apple", "Car", "Dog"], answer: "Apple", answerMeaning: "تفاح", icon: "fas fa-apple-alt" },
            // Letter B
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'A'?", answer: "B", answerMeaning: "الحرف الذي يلي A", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which animal starts with 'B'?", options: ["Cat", "Bird", "Fish", "Lion"], answer: "Bird", answerMeaning: "طائر", icon: "fas fa-dove" },
            // Letter C
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'B'?", answer: "C", answerMeaning: "الحرف الذي يلي B", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'C'?", options: ["House", "Chair", "Table", "Bed"], answer: "Chair", answerMeaning: "كرسي", icon: "fas fa-chair" },
            // Letter D
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'C'?", answer: "D", answerMeaning: "الحرف الذي يلي C", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which animal starts with 'D'?", options: ["Elephant", "Fox", "Dog", "Goat"], answer: "Dog", answerMeaning: "كلب", icon: "fas fa-dog" },
            // Letter E
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'D'?", answer: "E", answerMeaning: "الحرف الذي يلي D", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'E'?", options: ["Ant", "Egg", "Fish", "Grape"], answer: "Egg", answerMeaning: "بيضة", icon: "fas fa-egg" },
            // Letter F
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'E'?", answer: "F", answerMeaning: "الحرف الذي يلي E", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'F'?", options: ["Hand", "Foot", "Nose", "Ear"], answer: "Foot", answerMeaning: "قدم", icon: "fas fa-shoe-prints" },
            // Letter G
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'F'?", answer: "G", answerMeaning: "الحرف الذي يلي F", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'G'?", options: ["Door", "Glass", "Window", "Wall"], answer: "Glass", answerMeaning: "كوب / زجاج", icon: "fas fa-wine-glass" },
            // Letter H
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'G'?", answer: "H", answerMeaning: "الحرف الذي يلي G", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'H'?", options: ["Tree", "House", "Flower", "Grass"], answer: "House", answerMeaning: "منزل", icon: "fas fa-home" },
            // Letter I
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'H'?", answer: "I", answerMeaning: "الحرف الذي يلي H", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'I'?", options: ["Orange", "Ink", "Book", "Pencil"], answer: "Ink", answerMeaning: "حبر", icon: "fas fa-pen-nib" },
            // Letter J
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'I'?", answer: "J", answerMeaning: "الحرف الذي يلي I", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'J'?", options: ["Key", "Lock", "Jam", "Door"], answer: "Jam", answerMeaning: "مربى", icon: "fas fa-bread-slice" },
            // Letter K
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'J'?", answer: "K", answerMeaning: "الحرف الذي يلي J", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'K'?", options: ["Spoon", "Fork", "Knife", "Plate"], answer: "Knife", answerMeaning: "سكين", icon: "fas fa-utensils" },
            // Letter L
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'K'?", answer: "L", answerMeaning: "الحرف الذي يلي K", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which animal starts with 'L'?", options: ["Tiger", "Bear", "Lion", "Wolf"], answer: "Lion", answerMeaning: "أسد", icon: "fas fa-lion" },
            // Letter M
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'L'?", answer: "M", answerMeaning: "الحرف الذي يلي L", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'M'?", options: ["Sun", "Moon", "Star", "Cloud"], answer: "Moon", answerMeaning: "قمر", icon: "fas fa-moon" },
            // Letter N
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'M'?", answer: "N", answerMeaning: "الحرف الذي يلي M", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'N'?", options: ["Day", "Night", "Morning", "Evening"], answer: "Night", answerMeaning: "ليل", icon: "fas fa-cloud-moon" },
            // Letter O
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'N'?", answer: "O", answerMeaning: "الحرف الذي يلي N", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which fruit starts with 'O'?", options: ["Apple", "Banana", "Orange", "Grape"], answer: "Orange", answerMeaning: "برتقال", icon: "fas fa-orange" },
            // Letter P
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'O'?", answer: "P", answerMeaning: "الحرف الذي يلي O", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'P'?", options: ["Book", "Paper", "Pen", "Eraser"], answer: "Pen", answerMeaning: "قلم", icon: "fas fa-pen" },
            // Letter Q
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'P'?", answer: "Q", answerMeaning: "الحرف الذي يلي P", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'Q'?", options: ["King", "Queen", "Prince", "Princess"], answer: "Queen", answerMeaning: "ملكة", icon: "fas fa-crown" },
            // Letter R
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'Q'?", answer: "R", answerMeaning: "الحرف الذي يلي Q", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which color starts with 'R'?", options: ["Blue", "Green", "Yellow", "Red"], answer: "Red", answerMeaning: "أحمر", icon: "fas fa-palette" },
            // Letter S
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'R'?", answer: "S", answerMeaning: "الحرف الذي يلي R", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'S'?", options: ["Cloud", "Rain", "Snow", "Sun"], answer: "Sun", answerMeaning: "شمس", icon: "fas fa-sun" },
            // Letter T
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'S'?", answer: "T", answerMeaning: "الحرف الذي يلي S", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'T'?", options: ["Chair", "Table", "Sofa", "Bed"], answer: "Table", answerMeaning: "طاولة", icon: "fas fa-table" },
            // Letter U
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'T'?", answer: "U", answerMeaning: "الحرف الذي يلي T", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'U'?", options: ["Car", "Bus", "Umbrella", "Train"], answer: "Umbrella", answerMeaning: "مظلة", icon: "fas fa-umbrella" },
            // Letter V
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'U'?", answer: "V", answerMeaning: "الحرف الذي يلي U", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'V'?", options: ["Guitar", "Piano", "Violin", "Drum"], answer: "Violin", answerMeaning: "كمان", icon: "fas fa-violin" },
            // Letter W
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'V'?", answer: "W", answerMeaning: "الحرف الذي يلي V", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'W'?", options: ["Door", "Window", "Wall", "Roof"], answer: "Window", answerMeaning: "نافذة", icon: "fas fa-window-maximize" },
            // Letter X
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'W'?", answer: "X", answerMeaning: "الحرف الذي يلي W", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'X'?", options: ["Yoyo", "Xylophone", "Zebra", "Tiger"], answer: "Xylophone", answerMeaning: "إكسيليفون", icon: "fas fa-music" },
            // Letter Y
            { type: "fill-in-blank", level: "child", question: "What letter comes after 'X'?", answer: "Y", answerMeaning: "الحرف الذي يلي X", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'Y'?", options: ["Red", "Yellow", "Blue", "Green"], answer: "Yellow", answerMeaning: "أصفر", icon: "fas fa-palette" },
            // Letter Z
            { type: "fill-in-blank", level: "child", question: "What is the last letter of the English alphabet?", answer: "Z", answerMeaning: "الحرف الأخير", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which animal starts with 'Z'?", options: ["Lion", "Tiger", "Zebra", "Bear"], answer: "Zebra", answerMeaning: "حمار وحشي", icon: "fas fa-horse" },

            // New Questions: It is / He is
            { type: "multiple-choice", level: "adult", question: "Choose the correct form: ____ a sunny day.", options: ["He is", "It is", "They are", "She is"], answer: "It is", answerMeaning: "إنه (يوم مشمس - لغير العاقل)", icon: "fas fa-sun" },
            { type: "fill-in-blank", level: "adult", question: "My brother is a doctor. ____ very busy.", answer: "He is", answerMeaning: "هو (جداً مشغول - للعاقل المذكر)", icon: "fas fa-user-md" },
            { type: "true-false", level: "adult", question: "'It is raining' refers to the weather.", answer: "true", answerMeaning: "صحيح (تصف الطقس)", icon: "fas fa-cloud-showers-heavy" },
            { type: "multiple-choice", level: "adult", question: "____ a good idea to study every day.", options: ["He is", "It is", "She is", "We are"], answer: "It is", answerMeaning: "إنه (فكرة جيدة - لغير العاقل/موقف)", icon: "fas fa-lightbulb" },
            { type: "fill-in-blank", level: "adult", question: "Look at that car! ____ red.", answer: "It is", answerMeaning: "إنها (لغير العاقل)", icon: "fas fa-car" },
            { type: "multiple-choice", level: "adult", question: "My father is tall. ____ a strong man.", options: ["It is", "She is", "He is", "They are"], answer: "He is", answerMeaning: "هو (للعاقل المذكر)", icon: "fas fa-male" },
            { type: "true-false", level: "child", question: "We say 'It is' for people.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-user-circle" },
            { type: "multiple-choice", level: "adult", question: "____ dark outside now.", options: ["He is", "She is", "It is", "We are"], answer: "It is", answerMeaning: "إنه (للظواهر الطبيعية)", icon: "fas fa-moon" },
            { type: "fill-in-blank", level: "child", question: "My friend Tom is nice. ____ always helps me.", answer: "He is", answerMeaning: "هو (للعاقل المذكر)", icon: "fas fa-user-friends" },
            { type: "true-false", level: "adult", question: "'It is important' is a common phrase.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-exclamation-circle" },

            // New Questions: Do / Did / Does
            { type: "multiple-choice", level: "adult", question: "____ you like coffee?", options: ["Does", "Did", "Do", "Is"], answer: "Do", answerMeaning: "هل (فعل مساعد للمضارع مع You)", icon: "fas fa-question-circle" },
            { type: "fill-in-blank", level: "adult", question: "She ____ not speak French.", answer: "does", answerMeaning: "لا (فعل مساعد للنفي في المضارع مع She)", icon: "fas fa-language" },
            { type: "true-false", level: "adult", question: "'Did he go to the party yesterday?' uses the past tense.", answer: "true", answerMeaning: "صحيح (يستخدم زمن الماضي)", icon: "fas fa-calendar-alt" },
            { type: "multiple-choice", level: "adult", question: "What ____ you ____ last night?", options: ["do / do", "did / do", "does / do", "do / did"], answer: "did / do", answerMeaning: "ماذا فعلت (فعل مساعد للماضي مع الفعل الأصلي)", icon: "fas fa-question-circle" },
            { type: "fill-in-blank", level: "adult", question: "They ____ not understand the lesson.", answer: "do", answerMeaning: "لا (فعل مساعد للنفي في المضارع مع They)", icon: "fas fa-times-circle" },
            { type: "multiple-choice", level: "adult", question: "____ he finish his homework?", options: ["Do", "Did", "Does", "Is"], answer: "Does", answerMeaning: "هل (فعل مساعد للمضارع مع He)", icon: "fas fa-book" },
            { type: "true-false", level: "adult", question: "'Do you know him?' is a question about present knowledge.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-user-alt" },
            { type: "fill-in-blank", level: "adult", question: "I ____ not want to go.", answer: "do", answerMeaning: "لا (فعل مساعد للنفي في المضارع مع I)", icon: "fas fa-walking" },
            { type: "multiple-choice", level: "adult", question: "____ they play football every weekend?", options: ["Did", "Does", "Do", "Are"], answer: "Do", answerMeaning: "هل (فعل مساعد للمضارع مع They)", icon: "fas fa-futbol" },
            { type: "true-false", level: "adult", question: "You use 'did' for future actions.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-history" },

            // New Questions: Have / Has / Had
            { type: "multiple-choice", level: "adult", question: "I ____ a new car.", options: ["has", "have", "had", "is"], answer: "have", answerMeaning: "أمتلك (للمضارع مع I)", icon: "fas fa-car" },
            { type: "fill-in-blank", level: "adult", question: "He ____ two sisters.", answer: "has", answerMeaning: "يمتلك (للمضارع مع He)", icon: "fas fa-users" },
            { type: "true-false", level: "adult", question: "They had a great time at the beach last summer.", answer: "true", answerMeaning: "صحيح (يمتلكون وقتاً رائعاً في الماضي)", icon: "fas fa-umbrella-beach" },
            { type: "multiple-choice", level: "adult", question: "We ____ finished our homework.", options: ["has", "had", "have", "is"], answer: "have", answerMeaning: "قد انتهينا (للمضارع التام مع We)", icon: "fas fa-book-open" },
            { type: "fill-in-blank", level: "adult", question: "She ____ a beautiful garden.", answer: "has", answerMeaning: "تمتلك (للمضارع مع She)", icon: "fas fa-seedling" },
            { type: "multiple-choice", level: "adult", question: "Before she moved, she ____ lived in London for five years.", options: ["has", "have", "had", "is"], answer: "had", answerMeaning: "كانت قد عاشت (للماضي التام)", icon: "fas fa-city" },
            { type: "true-false", level: "adult", question: "'Had' is used for actions completed before a specific point in the past.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-history" },
            { type: "fill-in-blank", level: "adult", question: "Do you ____ any plans for the weekend?", answer: "have", answerMeaning: "لديك (للمضارع مع You)", icon: "fas fa-calendar-check" },
            { type: "multiple-choice", level: "adult", question: "My dog ____ black fur.", options: ["have", "had", "has", "is"], answer: "has", answerMeaning: "يمتلك (للمضارع مع المفرد الغائب)", icon: "fas fa-paw" },
            { type: "true-false", level: "child", question: "You use 'has' with 'I'.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },

            // New Questions: Verb to be (am, is, are, was, were)
            { type: "multiple-choice", level: "adult", question: "She ____ happy yesterday.", options: ["is", "am", "were", "was"], answer: "was", answerMeaning: "كانت (في الماضي للمفرد)", icon: "fas fa-history" },
            { type: "fill-in-blank", level: "adult", question: "They ____ students.", answer: "are", answerMeaning: "يكونون (للمضارع للجمع)", icon: "fas fa-user-graduate" },
            { type: "true-false", level: "adult", question: "I am a teacher. This sentence uses 'to be' in the present tense.", answer: "true", answerMeaning: "صحيح (يستخدم 'to be' في المضارع)", icon: "fas fa-chalkboard-teacher" },
            { type: "multiple-choice", level: "adult", question: "Where ____ you born?", options: ["was", "is", "were", "are"], answer: "were", answerMeaning: "كنت (في الماضي مع You)", icon: "fas fa-map-marker-alt" },
            { type: "fill-in-blank", level: "child", question: "I ____ six years old.", answer: "am", answerMeaning: "أكون (للمضارع مع I)", icon: "fas fa-birthday-cake" },
            { type: "multiple-choice", level: "adult", question: "He ____ working right now.", options: ["are", "am", "is", "was"], answer: "is", answerMeaning: "يكون (للمضارع مع He)", icon: "fas fa-laptop-code" },
            { type: "true-false", level: "adult", question: "'We was there' is grammatically correct.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times-circle" },
            { type: "fill-in-blank", level: "adult", question: "The weather ____ beautiful today.", answer: "is", answerMeaning: "يكون (للمضارع مع المفرد غير العاقل)", icon: "fas fa-cloud-sun" },
            { type: "multiple-choice", level: "adult", question: "They ____ playing in the park an hour ago.", options: ["are", "is", "was", "were"], answer: "were", answerMeaning: "كانوا (في الماضي للجمع)", icon: "fas fa-walking" },
            { type: "true-false", level: "child", question: "You use 'is' with 'she'.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-female" },
            
            // Additional questions to reach well over 150 total for random selection
            // It is / He is
            { type: "multiple-choice", level: "adult", question: "____ a long way to walk.", options: ["He is", "It is", "She is", "They are"], answer: "It is", answerMeaning: "إنه (مسافة طويلة)", icon: "fas fa-walking" },
            { type: "fill-in-blank", level: "adult", question: "My father is a great chef. ____ cooks delicious food.", answer: "He is", answerMeaning: "هو (يطهو طعاماً لذيذاً)", icon: "fas fa-pizza-slice" },
            { type: "true-false", level: "adult", question: "'It is possible' expresses a possibility.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-check-circle" },
            { type: "multiple-choice", level: "adult", question: "____ important to be kind.", options: ["He is", "She is", "It is", "They are"], answer: "It is", answerMeaning: "إنه (من المهم)", icon: "fas fa-heart" },
            { type: "fill-in-blank", level: "child", question: "My dog is friendly. ____ always wags its tail.", answer: "It is", answerMeaning: "هو/هي (لغير العاقل)", icon: "fas fa-dog" },
            { type: "multiple-choice", level: "adult", question: "That man is my teacher. ____ very patient.", options: ["It is", "She is", "He is", "We are"], answer: "He is", answerMeaning: "هو (صبور جداً)", icon: "fas fa-user-tie" },
            { type: "true-false", level: "adult", question: "'It is' is used for impersonal statements.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-info-circle" },
            { type: "fill-in-blank", level: "adult", question: "____ getting late.", answer: "It is", answerMeaning: "إنه (يصبح متأخراً)", icon: "fas fa-clock" },
            { type: "multiple-choice", level: "child", question: "This is my toy car. ____ red.", options: ["He is", "She is", "It is", "They are"], answer: "It is", answerMeaning: "إنها (لغير العاقل)", icon: "fas fa-car-alt" },
            { type: "true-false", level: "adult", question: "You can use 'He is' for a female person.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-venus-mars" },

            // Do / Did / Does
            { type: "multiple-choice", level: "adult", question: "____ she usually wake up early?", options: ["Do", "Did", "Does", "Is"], answer: "Does", answerMeaning: "هل (تستيقظ عادة - للمفرد الغائب)", icon: "fas fa-sun" },
            { type: "fill-in-blank", level: "adult", question: "I ____ not want to eat pizza tonight.", answer: "do", answerMeaning: "لا (أريد - للنفي مع I)", icon: "fas fa-pizza-slice" },
            { type: "true-false", level: "adult", question: "'Did' is the past tense of both 'do' and 'does'.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-check" },
            { type: "multiple-choice", level: "adult", question: "They ____ their best in the competition.", options: ["do", "does", "did", "doing"], answer: "did", answerMeaning: "فعلوا (ما في وسعهم - للماضي)", icon: "fas fa-medal" },
            { type: "fill-in-blank", level: "adult", question: "____ you finish your work yesterday?", answer: "Did", answerMeaning: "هل (أنهيت - للماضي)", icon: "fas fa-clipboard-check" },
            { type: "multiple-choice", level: "adult", question: "He ____ not understand the question.", options: ["do", "did", "does", "don't"], answer: "does", answerMeaning: "لا (يفهم - للنفي مع He)", icon: "fas fa-question" },
            { type: "true-false", level: "adult", question: "You use 'do' with 'he' in positive statements.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "fill-in-blank", level: "adult", question: "What ____ your sister ____ for a living?", answer: "does / do", answerMeaning: "ماذا (تفعل أختك - للمضارع)", icon: "fas fa-briefcase" },
            { type: "multiple-choice", level: "child", question: "____ you have a pet?", options: ["Does", "Did", "Do", "Is"], answer: "Do", answerMeaning: "هل (لديك - للمضارع)", icon: "fas fa-dog" },
            { type: "true-false", level: "adult", question: "In questions, 'do/does/did' often come before the subject.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-question-circle" },

            // Have / Has / Had
            { type: "multiple-choice", level: "adult", question: "She ____ already eaten dinner.", options: ["has", "have", "had", "is"], answer: "has", answerMeaning: "قد أكلت (للمضارع التام مع She)", icon: "fas fa-plate-utensils" },
            { type: "fill-in-blank", level: "adult", question: "We ____ a meeting next Monday.", answer: "have", answerMeaning: "لدينا (اجتماع - للمضارع)", icon: "fas fa-calendar-day" },
            { type: "true-false", level: "adult", question: "'Has' is used with plural subjects.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "multiple-choice", level: "adult", question: "Before I came home, my brother ____ already left.", options: ["has", "have", "had", "is"], answer: "had", answerMeaning: "كان قد غادر (للماضي التام)", icon: "fas fa-door-open" },
            { type: "fill-in-blank", level: "adult", question: "Do you ____ any questions?", answer: "have", answerMeaning: "لديك (أي أسئلة)", icon: "fas fa-question" },
            { type: "multiple-choice", level: "adult", question: "The company ____ increased its profits.", options: ["have", "had", "has", "is"], answer: "has", answerMeaning: "قد زادت (للمضارع التام مع المفرد)", icon: "fas fa-chart-line" },
            { type: "true-false", level: "child", question: "I had a toy car yesterday.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-car" },
            { type: "fill-in-blank", level: "adult", question: "By the time we arrived, they ____ already started the movie.", answer: "had", answerMeaning: "كانوا قد بدأوا (للماضي التام)", icon: "fas fa-film" },
            { type: "multiple-choice", level: "adult", question: "How many books ____ you ____?", options: ["has / have", "have / had", "do / have", "did / had"], answer: "do / have", answerMeaning: "كم كتاب لديك (للسؤال عن الامتلاك)", icon: "fas fa-book" },
            { type: "true-false", level: "adult", question: "'Have' is used to form the present perfect tense with 'I, you, we, they'.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-check" },

            // Verb to be (am, is, are, was, were)
            { type: "multiple-choice", level: "adult", question: "We ____ going to the concert tonight.", options: ["is", "am", "was", "are"], answer: "are", answerMeaning: "نحن (ذاهبون - للمضارع المستمر)", icon: "fas fa-music" },
            { type: "fill-in-blank", level: "adult", question: "The cat ____ sleeping on the couch.", answer: "is", answerMeaning: "يكون (نائماً - للمفرد)", icon: "fas fa-cat" },
            { type: "true-false", level: "adult", question: "'They was happy' is a correct sentence.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "multiple-choice", level: "adult", question: "I ____ tired after the long journey.", options: ["is", "am", "are", "was"], answer: "was", answerMeaning: "كنت (متعباً - للماضي)", icon: "fas fa-plane" },
            { type: "fill-in-blank", level: "child", question: "You ____ my best friend.", answer: "are", answerMeaning: "تكون (صديقي المفضل)", icon: "fas fa-user-friends" },
            { type: "multiple-choice", level: "adult", question: "Where ____ the keys?", options: ["is", "am", "were", "was"], answer: "are", answerMeaning: "أين (المفاتيح - للجمع)", icon: "fas fa-key" },
            { type: "true-false", level: "adult", question: "'Am' is only used with 'I'.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-check" },
            { type: "fill-in-blank", level: "adult", question: "Last year, I ____ studying abroad.", answer: "was", answerMeaning: "كنت (أدرس - للماضي المستمر)", icon: "fas fa-globe-europe" },
            { type: "multiple-choice", level: "adult", question: "The children ____ playing outside.", options: ["is", "was", "am", "were"], answer: "were", answerMeaning: "كانوا (يلعبون - للماضي المستمر للجمع)", icon: "fas fa-running" },
            { type: "true-false", level: "child", question: "The dog are cute.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-dog" },

            // More diverse questions to ensure well over 150
            // General vocabulary and grammar
            { type: "multiple-choice", level: "adult", question: "What is the past participle of 'go'?", options: ["goed", "gone", "went", "going"], answer: "gone", answerMeaning: "ذهب (اسم مفعول)", icon: "fas fa-route" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'early' is ____.", answer: "late", answerMeaning: "متأخر", icon: "fas fa-clock" },
            { type: "true-false", level: "adult", question: "A 'noun' is a word that describes an action.", answer: "false", answerMeaning: "خطأ (الفعل هو الذي يصف الفعل)", icon: "fas fa-spell-check" },
            { type: "multiple-choice", level: "child", question: "Which fruit is yellow and long?", options: ["Apple", "Banana", "Orange", "Grape"], answer: "Banana", answerMeaning: "موز", icon: "fas fa-banana" },
            { type: "fill-in-blank", level: "child", question: "A doctor helps people when they are ____.", answer: "sick", answerMeaning: "مرضى", icon: "fas fa-hospital" },
            { type: "multiple-choice", level: "adult", question: "Which word means 'very big'?", options: ["Tiny", "Huge", "Small", "Medium"], answer: "Huge", answerMeaning: "ضخم", icon: "fas fa-magnifying-glass" },
            { type: "fill-in-blank", level: "adult", question: "The plural of 'child' is ____.", answer: "children", answerMeaning: "أطفال", icon: "fas fa-child" },
            { type: "true-false", level: "child", question: "You wear shoes on your hands.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-shoe-prints" },
            { type: "multiple-choice", level: "adult", question: "What is a 'synonym'?", options: ["A word with opposite meaning", "A word with similar meaning", "A type of sentence", "A punctuation mark"], answer: "A word with similar meaning", answerMeaning: "كلمة بنفس المعنى", icon: "fas fa-language" },
            { type: "fill-in-blank", level: "adult", question: "The future tense of 'read' is 'will ____'.", answer: "read", answerMeaning: "يقرأ", icon: "fas fa-book" },
            { type: "true-false", level: "adult", question: "The word 'beautiful' is an adjective.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-feather-alt" },
            { type: "multiple-choice", level: "child", question: "What do you use to write?", options: ["Spoon", "Fork", "Pencil", "Plate"], answer: "Pencil", answerMeaning: "قلم رصاص", icon: "fas fa-pencil-alt" },
            { type: "fill-in-blank", level: "child", question: "Birds live in a ____.", answer: "nest", answerMeaning: "عش", icon: "fas fa-feather-alt" },
            { type: "multiple-choice", level: "adult", question: "Which is a conjunction?", options: ["Quickly", "And", "Run", "Blue"], answer: "And", answerMeaning: "حرف عطف", icon: "fas fa-link" },
            { type: "true-false", level: "adult", question: "'Happily' is an adverb.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-smile" },

            // Continue adding more questions to easily exceed 150
            // Example of rapid question generation for quantity:

            // More It is / He is
            { type: "fill-in-blank", level: "adult", question: "My boss is strict. ____ very demanding.", answer: "He is", answerMeaning: "هو (مطالب جداً)", icon: "fas fa-user-tie" },
            { type: "multiple-choice", level: "adult", question: "____ almost time to leave.", options: ["He is", "It is", "She is", "They are"], answer: "It is", answerMeaning: "لقد حان الوقت تقريباً للمغادرة", icon: "fas fa-clock" },
            { type: "true-false", level: "child", question: "'It is a boy' refers to a male child.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-child" },
            { type: "fill-in-blank", level: "adult", question: "The movie was boring. ____ not worth watching.", answer: "It is", answerMeaning: "لا يستحق المشاهدة", icon: "fas fa-film" },
            { type: "multiple-choice", level: "adult", question: "My friend John is smart. ____ good at math.", options: ["It is", "She is", "He is", "We are"], answer: "He is", answerMeaning: "هو (جيد في الرياضيات)", icon: "fas fa-calculator" },

            // More Do / Did / Does
            { type: "fill-in-blank", level: "adult", question: "Why ____ you ____ that?", answer: "did / do", answerMeaning: "لماذا فعلت ذلك", icon: "fas fa-question-circle" },
            { type: "multiple-choice", level: "adult", question: "____ she play piano?", options: ["Do", "Did", "Does", "Is"], answer: "Does", answerMeaning: "هل (تعزف بيانو)", icon: "fas fa-piano" },
            { type: "true-false", level: "adult", question: "You use 'do' when the subject is 'it'.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "fill-in-blank", level: "child", question: "____ you help your mom?", answer: "Do", answerMeaning: "هل (تساعد)", icon: "fas fa-handshake" },
            { type: "multiple-choice", level: "adult", question: "They ____ not watch TV often.", options: ["did", "does", "do", "don't"], answer: "do", answerMeaning: "لا (يشاهدون)", icon: "fas fa-tv" },

            // More Have / Has / Had
            { type: "fill-in-blank", level: "adult", question: "She ____ never seen a live concert.", answer: "has", answerMeaning: "لم ترَ (أبداً)", icon: "fas fa-ticket-alt" },
            { type: "multiple-choice", level: "adult", question: "Before the discovery, no one ____ known about it.", options: ["has", "have", "had", "is"], answer: "had", answerMeaning: "لم يكن (يعلم)", icon: "fas fa-lightbulb" },
            { type: "true-false", level: "child", question: "A car has wheels.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-car" },
            { type: "fill-in-blank", level: "adult", question: "They ____ recently moved to a new house.", answer: "have", answerMeaning: "قد انتقلوا (مؤخراً)", icon: "fas fa-house-chimney" },
            { type: "multiple-choice", level: "adult", question: "My sister ____ a big collection of stamps.", options: ["have", "had", "has", "is"], answer: "has", answerMeaning: "لديها (مجموعة كبيرة)", icon: "fas fa-stamp" },

            // More Verb to be
            { type: "fill-in-blank", level: "adult", question: "This cake ____ delicious!", answer: "is", answerMeaning: "يكون (لذيذاً)", icon: "fas fa-cake-slices" },
            { type: "multiple-choice", level: "adult", question: "We ____ at the museum last Sunday.", options: ["is", "am", "was", "were"], answer: "were", answerMeaning: "كنا (في المتحف)", icon: "fas fa-museum" },
            { type: "true-false", level: "child", question: "I is happy.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "fill-in-blank", level: "adult", question: "The books ____ on the table.", answer: "are", answerMeaning: "تكون (على الطاولة)", icon: "fas fa-book" },
            { type: "multiple-choice", level: "adult", question: "He ____ a student at this university.", options: ["am", "are", "is", "were"], answer: "is", answerMeaning: "هو (طالب)", icon: "fas fa-university" },

            // Random additional questions to hit large number (over 150)
            // Alphabet variations
            { type: "fill-in-blank", level: "child", question: "The letter 'A' makes the sound as in ____.", answer: "apple", answerMeaning: "تفاح", icon: "fas fa-apple-alt" },
            { type: "multiple-choice", level: "child", question: "Which letter comes before 'F'?", options: ["G", "E", "D", "H"], answer: "E", answerMeaning: "الحرف E", icon: "fas fa-font" },
            { type: "true-false", level: "child", question: "'Z' is in the middle of the alphabet.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-font" },
            { type: "fill-in-blank", level: "child", question: "The letter after 'N' is ____.", answer: "O", answerMeaning: "الحرف O", icon: "fas fa-font" },
            { type: "multiple-choice", level: "child", question: "Which word starts with 'S'?", options: ["Table", "Sun", "Chair", "Door"], answer: "Sun", answerMeaning: "شمس", icon: "fas fa-sun" },
            { type: "fill-in-blank", level: "child", question: "The letter 'C' sounds like 'k' in ____.", answer: "cat", answerMeaning: "قطة", icon: "fas fa-cat" },
            { type: "multiple-choice", level: "child", question: "Which of these is a vowel?", options: ["B", "D", "E", "F"], answer: "E", answerMeaning: "حرف متحرك", icon: "fas fa-font" },
            { type: "true-false", level: "child", question: "There are 5 vowels in English.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-check" },

            // More general grammar
            { type: "multiple-choice", level: "adult", question: "Which is the correct past tense of 'see'?", options: ["see", "saw", "seen", "seeing"], answer: "saw", answerMeaning: "رأى", icon: "fas fa-eye" },
            { type: "fill-in-blank", level: "adult", question: "A 'verb' is a word that describes an ____.", answer: "action", answerMeaning: "فعل", icon: "fas fa-running" },
            { type: "true-false", level: "adult", question: "'They is' is grammatically incorrect.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-times" },
            { type: "multiple-choice", level: "adult", question: "What is the superlative form of 'good'?", options: ["better", "goodest", "best", "most good"], answer: "best", answerMeaning: "الأفضل", icon: "fas fa-star" },
            { type: "fill-in-blank", level: "adult", question: "The comparative form of 'happy' is ____.", answer: "happier", answerMeaning: "أسعد", icon: "fas fa-smile" },
            { type: "true-false", level: "adult", question: "A 'preposition' shows the relationship between a noun and other words.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-map-pin" },
            { type: "multiple-choice", level: "adult", question: "Which word is an adverb?", options: ["Beautiful", "Run", "Quickly", "Table"], answer: "Quickly", answerMeaning: "بسرعة (ظرف)", icon: "fas fa-bolt" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'write' is ____.", answer: "wrote", answerMeaning: "كتب", icon: "fas fa-pen-fancy" },
            { type: "true-false", level: "child", question: "You can count 'water'.", answer: "false", answerMeaning: "خطأ (اسم غير معدود)", icon: "fas fa-tint" },
            { type: "multiple-choice", level: "adult", question: "Which is a collective noun?", options: ["Dog", "Tree", "Team", "Car"], answer: "Team", answerMeaning: "فريق (اسم جمعي)", icon: "fas fa-users" },
            { type: "fill-in-blank", level: "adult", question: "The word 'singular' means relating to ____.", answer: "one", answerMeaning: "واحد", icon: "fas fa-hashtag" },
            { type: "true-false", level: "adult", question: "'Their' indicates possession.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-hand-holding-heart" },
            { type: "multiple-choice", level: "child", question: "What color is grass?", options: ["Red", "Blue", "Green", "Yellow"], answer: "Green", answerMeaning: "أخضر", icon: "fas fa-leaf" },
            { type: "fill-in-blank", level: "child", question: "A fish lives in the ____.", answer: "water", answerMeaning: "ماء", icon: "fas fa-fish" },
            { type: "true-false", level: "adult", question: "An 'article' comes before a noun (e.g., a, an, the).", answer: "true", answerMeaning: "صحيح", icon: "fas fa-list-alt" },
            { type: "multiple-choice", level: "adult", question: "Which word is a pronoun?", options: ["House", "Run", "She", "Big"], answer: "She", answerMeaning: "ضمير", icon: "fas fa-user" },
            { type: "fill-in-blank", level: "adult", question: "The past simple of 'swim' is ____.", answer: "swam", answerMeaning: "سبح", icon: "fas fa-person-swimming" },
            { type: "true-false", level: "adult", question: "'Will' is used for future tense.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-hourglass-start" },
            { type: "multiple-choice", level: "child", question: "Which shape has three sides?", options: ["Circle", "Square", "Triangle", "Star"], answer: "Triangle", answerMeaning: "مثلث", icon: "fas fa-shapes" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to hear.", answer: "ears", answerMeaning: "آذان", icon: "fas fa-ear" },
            { type: "true-false", level: "adult", question: "An 'interjection' expresses strong emotion.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-exclamation" },
            { type: "multiple-choice", level: "adult", question: "Which is a type of punctuation?", options: ["Adjective", "Comma", "Noun", "Verb"], answer: "Comma", answerMeaning: "فاصلة", icon: "fas fa-quote-right" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'cold' is ____.", answer: "hot", answerMeaning: "ساخن", icon: "fas fa-fire" },
            { type: "true-false", level: "child", question: "A snake has legs.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-snake" },
            { type: "multiple-choice", level: "adult", question: "Which of these is a preposition of place?", options: ["Quickly", "Under", "Sing", "Happy"], answer: "Under", answerMeaning: "تحت (حرف جر للمكان)", icon: "fas fa-map-marker-alt" },
            { type: "fill-in-blank", level: "adult", question: "The word 'plural' means relating to ____ than one.", answer: "more", answerMeaning: "أكثر", icon: "fas fa-plus" },
            { type: "true-false", level: "adult", question: "'Their' is used as a contraction for 'they are'.", answer: "false", answerMeaning: "خطأ (تلك 'they're')", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "What do you wear on your head to keep warm?", options: ["Socks", "Gloves", "Hat", "Shoes"], answer: "Hat", answerMeaning: "قبعة", icon: "fas fa-hat-cowboy" },
            { type: "fill-in-blank", level: "child", question: "A cow gives us ____.", answer: "milk", answerMeaning: "حليب", icon: "fas fa-cow" },
            { type: "true-false", level: "adult", question: "An 'apostrophe' is used to show possession.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-quote-left" },
            { type: "multiple-choice", level: "adult", question: "Which is a modal verb?", options: ["Run", "Eat", "Can", "Sleep"], answer: "Can", answerMeaning: "فعل مساعد (يستطيع)", icon: "fas fa-lightbulb" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'break' is ____.", answer: "broken", answerMeaning: "مكسور (اسم مفعول)", icon: "fas fa-wrench" },
            { type: "true-false", level: "adult", question: "'Every day' is one word.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-calendar-alt" },
            { type: "multiple-choice", level: "child", question: "What is the color of the grass?", options: ["Red", "Green", "Blue", "Yellow"], answer: "Green", answerMeaning: "أخضر", icon: "fas fa-leaf" },
            { type: "fill-in-blank", level: "child", question: "A teacher works in a ____.", answer: "school", answerMeaning: "مدرسة", icon: "fas fa-school" },
            { type: "true-false", level: "adult", question: "'Me' is an object pronoun.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-user" },
            { type: "multiple-choice", level: "adult", question: "Which word means 'to begin'?", options: ["End", "Stop", "Start", "Finish"], answer: "Start", answerMeaning: "يبدأ", icon: "fas fa-play" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'noisy' is ____.", answer: "quiet", answerMeaning: "هادئ", icon: "fas fa-volume-mute" },
            { type: "true-false", level: "child", question: "Fish can fly.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-fish" },
            { type: "multiple-choice", level: "adult", question: "Which is the correct spelling?", options: ["recieve", "receive", "reiceve", "receve"], answer: "receive", answerMeaning: "يستلم", icon: "fas fa-envelope" },
            { type: "fill-in-blank", level: "adult", question: "An antonym for 'brave' is ____.", answer: "cowardly", answerMeaning: "جبان", icon: "fas fa-shield-alt" },
            { type: "true-false", level: "adult", question: "A comma is used to separate items in a list.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-list-ul" },
            { type: "multiple-choice", level: "child", question: "How many fingers do you have on one hand?", options: ["Three", "Four", "Five", "Six"], answer: "Five", answerMeaning: "خمسة", icon: "fas fa-hand-paper" },
            { type: "fill-in-blank", level: "child", question: "The color of the sky at night is ____.", answer: "dark", answerMeaning: "داكن", icon: "fas fa-moon" },
            { type: "true-false", level: "adult", question: "'Their' and 'there' are homophones.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-volume-up" },
            { type: "multiple-choice", level: "adult", question: "Which word is a determiner?", options: ["Quickly", "Sing", "The", "Jump"], answer: "The", answerMeaning: "أداة تعريف", icon: "fas fa-grip-lines" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'sing' is ____.", answer: "sang", answerMeaning: "غنى", icon: "fas fa-microphone" },
            { type: "true-false", level: "adult", question: "'Good' is an adverb.", answer: "false", answerMeaning: "خطأ (هي صفة)", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "What animal says 'moo'?", options: ["Dog", "Cat", "Cow", "Chicken"], answer: "Cow", answerMeaning: "بقرة", icon: "fas fa-cow" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to smell.", answer: "nose", answerMeaning: "أنف", icon: "fas fa-smog" },
            { type: "true-false", level: "adult", question: "A 'compound sentence' has two or more independent clauses.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-sitemap" },
            { type: "multiple-choice", level: "adult", question: "Which is a common abbreviation for 'doctor'?", options: ["Dr.", "Doc.", "Dctr.", "Doct."], answer: "Dr.", answerMeaning: "اختصار دكتور", icon: "fas fa-user-md" },
            { type: "fill-in-blank", level: "adult", question: "The plural of 'mouse' is ____.", answer: "mice", answerMeaning: "فئران", icon: "fas fa-mouse" },
            { type: "true-false", level: "child", question: "An elephant is smaller than a mouse.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-elephant" },
            { type: "multiple-choice", level: "adult", question: "Which word is a coordinating conjunction?", options: ["Although", "Because", "But", "Since"], answer: "But", answerMeaning: "حرف عطف تنسيقي", icon: "fas fa-puzzle-piece" },
            { type: "fill-in-blank", level: "adult", question: "The verb 'to be' in the third person singular present tense is ____.", answer: "is", answerMeaning: "يكون", icon: "fas fa-grammar" },
            { type: "true-false", level: "adult", question: "'I go to the store' is in the past tense.", answer: "false", answerMeaning: "خطأ (في المضارع)", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "Which animal lays eggs?", options: ["Dog", "Cat", "Chicken", "Cow"], answer: "Chicken", answerMeaning: "دجاجة", icon: "fas fa-egg" },
            { type: "fill-in-blank", level: "child", question: "A bed is for ____.", answer: "sleeping", answerMeaning: "النوم", icon: "fas fa-bed" },
            { type: "true-false", level: "adult", question: "'He speaks good English' is grammatically perfect.", answer: "false", answerMeaning: "خطأ (الصحيح 'He speaks English well')", icon: "fas fa-comments" },
            { type: "multiple-choice", level: "adult", question: "Which word is a demonstrative pronoun?", options: ["Run", "Happy", "This", "Quickly"], answer: "This", answerMeaning: "ضمير إشارة", icon: "fas fa-hand-point-right" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'run' is ____.", answer: "ran", answerMeaning: "ركض", icon: "fas fa-running" },
            { type: "true-false", level: "adult", question: "'A lot' should be written as one word.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "What is the main color of a stop sign?", options: ["Blue", "Yellow", "Red", "Green"], answer: "Red", answerMeaning: "أحمر", icon: "fas fa-traffic-light" },
            { type: "fill-in-blank", level: "child", question: "You drink ____ when you are thirsty.", answer: "water", answerMeaning: "ماء", icon: "fas fa-glass-water" },
            { type: "true-false", level: "adult", question: "An 'adverb' modifies a noun.", answer: "false", answerMeaning: "خطأ (يعدل الفعل أو الصفة أو ظرف آخر)", icon: "fas fa-spell-check" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses the present perfect tense correctly?", options: ["I have went to the store.", "I has gone to the store.", "I have gone to the store.", "I had went to the store."], answer: "I have gone to the store.", answerMeaning: "لقد ذهبت إلى المتجر", icon: "fas fa-clock" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'thin' is ____.", answer: "fat / thick", answerMeaning: "سمين / سميك", icon: "fas fa-weight-hanging" }, // Both are acceptable depending on context
            { type: "true-false", level: "child", question: "A zebra has stripes.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-horse" },
            { type: "multiple-choice", level: "adult", question: "Which word is a quantifier?", options: ["Beautiful", "Many", "Sing", "Quickly"], answer: "Many", answerMeaning: "محدد كمية", icon: "fas fa-sort-numeric-up-alt" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'eat' is ____.", answer: "eaten", answerMeaning: "أكل (اسم مفعول)", icon: "fas fa-utensils" },
            { type: "true-false", level: "adult", question: "'Could' is a past form of 'can'.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-check" },
            { type: "multiple-choice", level: "child", question: "Which season is cold and has snow?", options: ["Summer", "Autumn", "Winter", "Spring"], answer: "Winter", answerMeaning: "الشتاء", icon: "fas fa-snowflake" },
            { type: "fill-in-blank", level: "child", question: "A chair is for ____.", answer: "sitting", answerMeaning: "الجلوس", icon: "fas fa-chair" },
            { type: "true-false", level: "adult", question: "An 'auxiliary verb' helps the main verb.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-hands-helping" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses an imperative verb?", options: ["She sings well.", "Did you go?", "Close the door.", "I am tired."], answer: "Close the door.", answerMeaning: "أغلق الباب (فعل أمر)", icon: "fas fa-door-closed" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'start' is ____.", answer: "finish / end", answerMeaning: "ينتهي / ينهي", icon: "fas fa-stop" },
            { type: "true-false", level: "child", question: "A bicycle has four wheels.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-bicycle" },
            { type: "multiple-choice", level: "adult", question: "Which word is a relative pronoun?", options: ["He", "Quickly", "Which", "And"], answer: "Which", answerMeaning: "ضمير وصل", icon: "fas fa-link" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'drive' is ____.", answer: "drove", answerMeaning: "قاد", icon: "fas fa-car" },
            { type: "true-false", level: "adult", question: "'Its' indicates possession for 'it'.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-check" },
            { type: "multiple-choice", level: "child", question: "What is the sound a dog makes?", options: ["Meow", "Moo", "Woof", "Quack"], answer: "Woof", answerMeaning: "نباح الكلب", icon: "fas fa-dog" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to see.", answer: "eyes", answerMeaning: "عيون", icon: "fas fa-eye" },
            { type: "true-false", level: "adult", question: "A 'gerund' is a verb form ending in -ing used as a noun.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-spell-check" },
            { type: "multiple-choice", level: "adult", question: "Which is a synonym for 'fast'?", options: ["Slow", "Quick", "Big", "Small"], answer: "Quick", answerMeaning: "سريع", icon: "fas fa-bolt" },
            { type: "fill-in-blank", level: "adult", question: "The word 'often' is an ____.", answer: "adverb", answerMeaning: "ظرف تكرار", icon: "fas fa-redo" },
            { type: "true-false", level: "child", question: "An apple is a vegetable.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-apple-alt" },
            { type: "multiple-choice", level: "adult", question: "Which sentence is in the passive voice?", options: ["The boy kicked the ball.", "The ball was kicked by the boy.", "The boy is kicking the ball.", "The ball kicks the boy."], answer: "The ball was kicked by the boy.", answerMeaning: "تم ركل الكرة بواسطة الصبي", icon: "fas fa-hand-point-right" },
            { type: "fill-in-blank", level: "adult", question: "The comparative form of 'bad' is ____.", answer: "worse", answerMeaning: "أسوأ", icon: "fas fa-frown" },
            { type: "true-false", level: "adult", question: "'Effect' is commonly used as a verb.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "Which of these is a body part?", options: ["Table", "Tree", "Hand", "Book"], answer: "Hand", answerMeaning: "يد", icon: "fas fa-hand" },
            { type: "fill-in-blank", level: "child", question: "A cow lives on a ____.", answer: "farm", answerMeaning: "مزرعة", icon: "fas fa-tractor" },
            { type: "true-false", level: "adult", question: "A 'proper noun' is always capitalized.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-check" },
            { type: "multiple-choice", level: "adult", question: "Which is the correct form of 'to lie' (recline) in the past simple?", options: ["lay", "lied", "lain", "lying"], answer: "lay", answerMeaning: "استلقى", icon: "fas fa-bed" },
            { type: "fill-in-blank", level: "adult", question: "The superlative form of 'small' is ____.", answer: "smallest", answerMeaning: "الأصغر", icon: "fas fa-compress-arrows-alt" },
            { type: "true-false", level: "adult", question: "'I have no money' is a grammatically correct sentence.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-money-bill-alt" },
            { type: "multiple-choice", level: "child", question: "What do you wear on your feet?", options: ["Hats", "Gloves", "Socks", "Shirts"], answer: "Socks", answerMeaning: "جوارب", icon: "fas fa-socks" },
            { type: "fill-in-blank", level: "child", question: "You eat with your ____.", answer: "mouth", answerMeaning: "فم", icon: "fas fa-mouth" },
            { type: "true-false", level: "adult", question: "'Less' is used for countable nouns.", answer: "false", answerMeaning: "خطأ (يستخدم لغير المعدود)", icon: "fas fa-times" },
            { type: "multiple-choice", level: "adult", question: "Which of these is a complex sentence?", options: ["I went home.", "I went home, and I ate dinner.", "Because it was raining, I took my umbrella.", "Go home!"], answer: "Because it was raining, I took my umbrella.", answerMeaning: "جملة معقدة", icon: "fas fa-umbrella" },
            { type: "fill-in-blank", level: "adult", question: "The word 'quickly' is an ____.", answer: "adverb", answerMeaning: "ظرف", icon: "fas fa-bolt" },
            { type: "true-false", level: "child", question: "A tomato is a fruit.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-tomato" },
            { type: "multiple-choice", level: "adult", question: "Which form of 'read' is used for the past participle?", options: ["read", "read (pronounced red)", "reading", "reads"], answer: "read (pronounced red)", answerMeaning: "قرأ (اسم مفعول)", icon: "fas fa-book-reader" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'full' is ____.", answer: "empty", answerMeaning: "فارغ", icon: "fas fa-box-open" },
            { type: "true-false", level: "adult", question: "'Fewer' is used for non-countable nouns.", answer: "false", answerMeaning: "خطأ (يستخدم للمعدود)", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "What animal says 'oink'?", options: ["Cow", "Chicken", "Pig", "Sheep"], answer: "Pig", answerMeaning: "خنزير", icon: "fas fa-piggy-bank" },
            { type: "fill-in-blank", level: "child", question: "You write on ____.", answer: "paper", answerMeaning: "ورق", icon: "fas fa-scroll" },
            { type: "true-false", level: "adult", question: "A 'dependent clause' can stand alone as a complete sentence.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-sitemap" },
            { type: "multiple-choice", level: "adult", question: "Which of these is a phrasal verb?", options: ["Run fast", "Eat pizza", "Look up", "Sing a song"], answer: "Look up", answerMeaning: "فعل مركب", icon: "fas fa-magnifying-glass" },
            { type: "fill-in-blank", level: "adult", question: "The past simple of 'sleep' is ____.", answer: "slept", answerMeaning: "نام", icon: "fas fa-bed" },
            { type: "true-false", level: "adult", question: "'Neither... nor' is used to connect two negative ideas.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-handshake" },
            { type: "multiple-choice", level: "child", question: "What is the color of the sun?", options: ["Blue", "Green", "Yellow", "Purple"], answer: "Yellow", answerMeaning: "أصفر", icon: "fas fa-sun" },
            { type: "fill-in-blank", level: "child", question: "A monkey likes to eat ____.", answer: "banana", answerMeaning: "موز", icon: "fas fa-monkey" },
            { type: "true-false", level: "adult", question: "The term 'idiom' refers to a literal expression.", answer: "false", answerMeaning: "خطأ (تعبير مجازي)", icon: "fas fa-lightbulb" },
            { type: "multiple-choice", level: "adult", question: "Which is a common collocation with 'make'?", options: ["make a mistake", "do a mistake", "have a mistake", "take a mistake"], answer: "make a mistake", answerMeaning: "يرتكب خطأ", icon: "fas fa-exclamation-triangle" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'up' is ____.", answer: "down", answerMeaning: "أسفل", icon: "fas fa-arrow-down" },
            { type: "true-false", level: "child", question: "Cars can fly.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-car" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses 'would' correctly for a past habit?", options: ["I would go to school now.", "I would go to school every day when I was young.", "I would going to school.", "I would went to school."], answer: "I would go to school every day when I was young.", answerMeaning: "كنت أذهب إلى المدرسة كل يوم عندما كنت صغيراً", icon: "fas fa-clock" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'swim' is ____.", answer: "swum", answerMeaning: "سبح (اسم مفعول)", icon: "fas fa-person-swimming" },
            { type: "true-false", level: "adult", question: "A 'homograph' is a word that is spelled the same but has a different meaning and often pronunciation.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-pen" },
            { type: "multiple-choice", level: "child", question: "What color is a typical fire truck?", options: ["Blue", "Green", "Red", "Yellow"], answer: "Red", answerMeaning: "أحمر", icon: "fas fa-fire-truck" },
            { type: "fill-in-blank", level: "child", question: "A spoon is for ____ soup.", answer: "eating", answerMeaning: "أكل", icon: "fas fa-utensils" },
            { type: "true-false", level: "adult", question: "'Affect' is mainly a noun.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "multiple-choice", level: "adult", question: "Which verb form completes the sentence: 'She has ____ the task.'", options: ["done", "did", "do", "doing"], answer: "done", answerMeaning: "أنهت (المهمة)", icon: "fas fa-check-double" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'win' is ____.", answer: "lose", answerMeaning: "يخسر", icon: "fas fa-trophy" },
            { type: "true-false", level: "child", question: "Dogs can talk.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-dog" },
            { type: "multiple-choice", level: "adult", question: "Which is a synonym for 'difficult'?", options: ["Easy", "Hard", "Simple", "Smooth"], answer: "Hard", answerMeaning: "صعب", icon: "fas fa-tools" },
            { type: "fill-in-blank", level: "adult", question: "The word 'beautifully' is an ____.", answer: "adverb", answerMeaning: "ظرف", icon: "fas fa-palette" },
            { type: "true-false", level: "adult", question: "A 'prepositional phrase' starts with a preposition and ends with a noun or pronoun.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-route" },
            { type: "multiple-choice", level: "child", question: "What is the name of the place where planes land and take off?", options: ["Port", "Station", "Airport", "Garage"], answer: "Airport", answerMeaning: "مطار", icon: "fas fa-plane-departure" },
            { type: "fill-in-blank", level: "child", question: "A clock tells us the ____.", answer: "time", answerMeaning: "وقت", icon: "fas fa-clock" },
            { type: "true-false", level: "adult", question: "'Good' is an adjective.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-star" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses a conditional type 1 correctly?", options: ["If I would study, I would pass.", "If I study, I will pass.", "If I studied, I will pass.", "If I study, I passed."], answer: "If I study, I will pass.", answerMeaning: "إذا درست، سأنجح", icon: "fas fa-graduation-cap" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'rich' is ____.", answer: "poor", answerMeaning: "فقير", icon: "fas fa-coins" },
            { type: "true-false", level: "child", question: "Birds have teeth.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-dove" },
            { type: "multiple-choice", level: "adult", question: "Which of these is an interrogative pronoun?", options: ["He", "She", "Who", "They"], answer: "Who", answerMeaning: "ضمير استفهام", icon: "fas fa-question" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'begin' is ____.", answer: "began", answerMeaning: "بدأ", icon: "fas fa-hourglass-start" },
            { type: "true-false", level: "adult", question: "'Between' is used for two items, 'among' for more than two.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-users" },
            { type: "multiple-choice", level: "child", question: "What is the sound a cow makes?", options: ["Meow", "Woof", "Moo", "Chirp"], answer: "Moo", answerMeaning: "خوار البقرة", icon: "fas fa-cow" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to walk.", answer: "legs", answerMeaning: "أرجل", icon: "fas fa-walking" },
            { type: "true-false", level: "adult", question: "A 'compound noun' is formed by combining two or more words.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-puzzle-piece" },
            { type: "multiple-choice", level: "adult", question: "Which word means 'to create'?", options: ["Destroy", "Build", "Break", "Separate"], answer: "Build", answerMeaning: "يبني / يخلق", icon: "fas fa-hammer" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'soft' is ____.", answer: "hard", answerMeaning: "صلب", icon: "fas fa-cube" },
            { type: "true-false", level: "child", question: "All fruits are green.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-apple-alt" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses 'affect' correctly?", options: ["The effect of the rain was strong.", "The rain did not affect my mood.", "The rain had a strong affect.", "The rain affects strong."], answer: "The rain did not affect my mood.", answerMeaning: "لم تؤثر الأمطار على مزاجي", icon: "fas fa-cloud-showers-heavy" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'write' is ____.", answer: "written", answerMeaning: "مكتوب (اسم مفعول)", icon: "fas fa-pen-nib" },
            { type: "true-false", level: "adult", question: "'Much' is used for countable nouns.", answer: "false", answerMeaning: "خطأ (لغير المعدود)", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "What is the name of the big star in the sky during the day?", options: ["Moon", "Earth", "Sun", "Cloud"], answer: "Sun", answerMeaning: "الشمس", icon: "fas fa-sun" },
            { type: "fill-in-blank", level: "child", question: "You wear a ____ on your finger.", answer: "ring", answerMeaning: "خاتم", icon: "fas fa-ring" },
            { type: "true-false", level: "adult", question: "A 'prefix' comes at the end of a word.", answer: "false", answerMeaning: "خطأ (يأتي في البداية)", icon: "fas fa-spell-check" },
            { type: "multiple-choice", level: "adult", question: "Which of these indicates a cause and effect relationship?", options: ["And", "But", "Because", "Or"], answer: "Because", answerMeaning: "لأن (سبب ونتيجة)", icon: "fas fa-cogs" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'take' is ____.", answer: "took", answerMeaning: "أخذ", icon: "fas fa-hand-holding" },
            { type: "true-false", level: "adult", question: "'Their' is a possessive pronoun.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-lock" },
            { type: "multiple-choice", level: "child", question: "What animal has a long trunk?", options: ["Lion", "Monkey", "Elephant", "Zebra"], answer: "Elephant", answerMeaning: "فيل", icon: "fas fa-elephant" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to clap.", answer: "hands", answerMeaning: "يدين", icon: "fas fa-hands" },
            { type: "true-false", level: "adult", question: "A 'suffix' comes before the root word.", answer: "false", answerMeaning: "خطأ (يأتي بعد الكلمة الجذرية)", icon: "fas fa-spell-check" },
            { type: "multiple-choice", level: "adult", question: "Which word means 'to decrease'?", options: ["Increase", "Reduce", "Grow", "Expand"], answer: "Reduce", answerMeaning: "يقلل", icon: "fas fa-minus" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'light' (weight) is ____.", answer: "heavy", answerMeaning: "ثقيل", icon: "fas fa-weight-scale" },
            { type: "true-false", level: "child", question: "A tree can walk.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-tree" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses 'advice' correctly?", options: ["Can you give me some advise?", "Can you give me some advices?", "Can you give me some advice?", "Can you gives me some advice?"], answer: "Can you give me some advice?", answerMeaning: "هل يمكنك إعطائي بعض النصائح؟", icon: "fas fa-lightbulb" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'speak' is ____.", answer: "spoken", answerMeaning: "متحدث (اسم مفعول)", icon: "fas fa-comments" },
            { type: "true-false", level: "adult", question: "'Who' refers to a person, 'which' refers to a thing or animal.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-user-circle" },
            { type: "multiple-choice", level: "child", question: "What is the name of the place where books are kept?", options: ["Shop", "Hospital", "Library", "Zoo"], answer: "Library", answerMeaning: "مكتبة", icon: "fas fa-book" },
            { type: "fill-in-blank", level: "child", question: "You wear a ____ to swim.", answer: "swimsuit", answerMeaning: "ملابس سباحة", icon: "fas fa-person-swimming" },
            { type: "true-false", level: "adult", question: "A 'conjunction' connects words, phrases, or clauses.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-link" },
            { type: "multiple-choice", level: "adult", question: "Which is an example of an irregular verb?", options: ["Walk", "Play", "Go", "Talk"], answer: "Go", answerMeaning: "فعل شاذ", icon: "fas fa-running" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'awake' is ____.", answer: "asleep", answerMeaning: "نائم", icon: "fas fa-bed" },
            { type: "true-false", level: "child", question: "A circle has straight sides.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-circle" },
            { type: "multiple-choice", level: "adult", question: "Which is the correct use of 'fewer'?", options: ["Fewer water", "Fewer money", "Fewer books", "Fewer information"], answer: "Fewer books", answerMeaning: "عدد أقل من الكتب", icon: "fas fa-book" },
            { type: "fill-in-blank", level: "adult", question: "The word 'quickly' describes a ____.", answer: "verb / action", answerMeaning: "فعل / حركة", icon: "fas fa-bolt" },
            { type: "true-false", level: "adult", question: "An 'exclamation mark' is used to end a question.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-question-circle" },
            { type: "multiple-choice", level: "child", question: "What is the animal that barks?", options: ["Cat", "Dog", "Bird", "Fish"], answer: "Dog", answerMeaning: "كلب", icon: "fas fa-dog" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to kick a ball.", answer: "feet", answerMeaning: "قدمين", icon: "fas fa-futbol" },
            { type: "true-false", level: "adult", question: "A 'clause' is a group of words that contains a subject and a verb.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-spell-check" },
            { type: "multiple-choice", level: "adult", question: "Which sentence is in the present continuous tense?", options: ["I read a book.", "I am reading a book.", "I read a book yesterday.", "I will read a book."], answer: "I am reading a book.", answerMeaning: "أنا أقرأ كتابًا (الآن)", icon: "fas fa-book-reader" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'long' is ____.", answer: "short", answerMeaning: "قصير", icon: "fas fa-ruler-horizontal" },
            { type: "true-false", level: "child", question: "The ocean is small.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-water" },
            { type: "multiple-choice", level: "adult", question: "Which punctuation mark is used for a pause in a sentence?", options: ["Period", "Question mark", "Comma", "Exclamation mark"], answer: "Comma", answerMeaning: "فاصلة", icon: "fas fa-pause" },
            { type: "fill-in-blank", level: "adult", question: "The past simple of 'eat' is ____.", answer: "ate", answerMeaning: "أكل", icon: "fas fa-pizza-slice" },
            { type: "true-false", level: "adult", question: "'Yours' is a possessive adjective.", answer: "false", answerMeaning: "خطأ (هو ضمير ملكية)", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "What is the color of milk?", options: ["Red", "White", "Black", "Brown"], answer: "White", answerMeaning: "أبيض", icon: "fas fa-glass-milk" },
            { type: "fill-in-blank", level: "child", question: "A table has ____.", answer: "legs", answerMeaning: "أرجل", icon: "fas fa-table" },
            { type: "true-false", level: "adult", question: "A 'fragment' is an incomplete sentence.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-cut" },
            { type: "multiple-choice", level: "adult", question: "Which is a common error: 'He doesn't know nothing' or 'He doesn't know anything'?", options: ["He doesn't know nothing", "He doesn't know anything"], answer: "He doesn't know anything", answerMeaning: "الصحيح لا يعرف شيئاً", icon: "fas fa-exclamation-triangle" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'inside' is ____.", answer: "outside", answerMeaning: "خارج", icon: "fas fa-door-open" },
            { type: "true-false", level: "child", question: "A fish can talk.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-fish" },
            { type: "multiple-choice", level: "adult", question: "Which tense describes actions completed in the past at an unspecified time, or actions that began in the past and continue to the present?", options: ["Past Simple", "Present Continuous", "Present Perfect", "Future Simple"], answer: "Present Perfect", answerMeaning: "المضارع التام", icon: "fas fa-clock" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'go' is ____.", answer: "gone", answerMeaning: "ذهب (اسم مفعول)", icon: "fas fa-route" },
            { type: "true-false", level: "adult", question: "'Must' expresses obligation.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-clipboard-check" },
            { type: "multiple-choice", level: "child", question: "What is the name of a baby dog?", options: ["Kitten", "Chick", "Puppy", "Cub"], answer: "Puppy", answerMeaning: "جرو", icon: "fas fa-dog" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to smell flowers.", answer: "nose", answerMeaning: "أنف", icon: "fas fa-flower" },
            { type: "true-false", level: "adult", question: "A 'run-on sentence' occurs when two or more independent clauses are joined without proper punctuation.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-exclamation" },
            { type: "multiple-choice", level: "adult", question: "Which sentence is in the future simple tense?", options: ["I go.", "I went.", "I will go.", "I am going."], answer: "I will go.", answerMeaning: "سأذهب", icon: "fas fa-calendar-alt" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'fast' is ____.", answer: "slow", answerMeaning: "بطيء", icon: "fas fa-turtle" },
            { type: "true-false", level: "child", question: "A car has wings.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-car" },
            { type: "multiple-choice", level: "adult", question: "Which word is an adjective?", options: ["Quickly", "Sing", "Beautiful", "Run"], answer: "Beautiful", answerMeaning: "جميل (صفة)", icon: "fas fa-palette" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'see' is ____.", answer: "saw", answerMeaning: "رأى", icon: "fas fa-eye" },
            { type: "true-false", level: "adult", question: "'Good' is an adverb.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            // Make sure we have at least 150 questions by duplicating some general types if needed, or adding more specific ones
            // Example for rapid expansion (ensure variety):
            { type: "multiple-choice", level: "adult", question: "Which is the correct comparative form of 'many'?", options: ["mucher", "manyer", "more", "most"], answer: "more", answerMeaning: "أكثر", icon: "fas fa-sort-numeric-up" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'do' is ____.", answer: "done", answerMeaning: "فعل (اسم مفعول)", icon: "fas fa-check-double" },
            { type: "true-false", level: "adult", question: "'Can' expresses ability.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-hand-fist" },
            { type: "multiple-choice", level: "child", question: "Which animal flies at night and makes a 'hoo' sound?", options: ["Bird", "Bat", "Owl", "Eagle"], answer: "Owl", answerMeaning: "بومة", icon: "fas fa-moon" },
            { type: "fill-in-blank", level: "child", question: "The color of the ocean is often ____.", answer: "blue", answerMeaning: "أزرق", icon: "fas fa-water" },
            { type: "true-false", level: "adult", question: "A 'semicolon' connects two independent clauses without a conjunction.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-ellipsis-h" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses 'effect' as a noun correctly?", options: ["The rain will effect the plants.", "The effect of the rain was visible.", "The rain did effect the plants.", "The rain affects strong effects."], answer: "The effect of the rain was visible.", answerMeaning: "تأثير المطر كان مرئياً", icon: "fas fa-leaf" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'fast' is ____.", answer: "slow", answerMeaning: "بطيء", icon: "fas fa-turtle" },
            { type: "true-false", level: "child", question: "A square has five sides.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-square" },
            { type: "multiple-choice", level: "adult", question: "Which of these is a preposition of time?", options: ["Under", "Through", "After", "Between"], answer: "After", answerMeaning: "بعد (حرف جر للوقت)", icon: "fas fa-clock" },
            { type: "fill-in-blank", level: "adult", question: "The word 'suddenly' is an ____.", answer: "adverb", answerMeaning: "ظرف", icon: "fas fa-exclamation" },
            { type: "true-false", level: "adult", question: "'They're' is a contraction of 'they are'.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-users" },
            { type: "multiple-choice", level: "child", question: "What is the name of a baby cat?", options: ["Puppy", "Kitten", "Chick", "Cub"], answer: "Kitten", answerMeaning: "قطة صغيرة", icon: "fas fa-cat" },
            { type: "fill-in-blank", level: "child", question: "A spoon is used for ____ soup.", answer: "eating", answerMeaning: "أكل", icon: "fas fa-utensils" },
            { type: "true-false", level: "adult", question: "The main purpose of a comma is to end a sentence.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "multiple-choice", level: "adult", question: "Which verb form completes 'I had ____ before you arrived.'?", options: ["eaten", "eat", "ate", "eating"], answer: "eaten", answerMeaning: "أكلت", icon: "fas fa-utensils" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'brave' is ____.", answer: "cowardly", answerMeaning: "جبان", icon: "fas fa-mask" },
            { type: "true-false", level: "child", question: "Fish can walk on land.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-fish" },
            { type: "multiple-choice", level: "adult", question: "Which word is a common noun?", options: ["London", "Table", "Sarah", "July"], answer: "Table", answerMeaning: "اسم شائع", icon: "fas fa-table" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'begin' is ____.", answer: "began", answerMeaning: "بدأ", icon: "fas fa-hourglass-start" },
            { type: "true-false", level: "adult", question: "'Its' is a contraction for 'it is'.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "What do you use to draw pictures?", options: ["Hammer", "Pencil", "Spoon", "Scissors"], answer: "Pencil", answerMeaning: "قلم رصاص", icon: "fas fa-pencil-alt" },
            { type: "fill-in-blank", level: "child", question: "A bird lives in a ____.", answer: "nest", answerMeaning: "عش", icon: "fas fa-dove" },
            { type: "true-false", level: "adult", question: "An 'adverb clause' modifies a verb, an adjective, or another adverb.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-language" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses the simple present tense correctly?", options: ["He is eating.", "He eats.", "He ate.", "He will eat."], answer: "He eats.", answerMeaning: "يأكل", icon: "fas fa-utensils" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'wet' is ____.", answer: "dry", answerMeaning: "جاف", icon: "fas fa-cloud" },
            { type: "true-false", level: "child", question: "The sun is cold.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-sun" },
            { type: "multiple-choice", level: "adult", question: "Which word is a quantifying pronoun?", options: ["Many", "Quickly", "Beautiful", "Run"], answer: "Many", answerMeaning: "ضمير كمي", icon: "fas fa-sort-numeric-up" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'write' is ____.", answer: "written", answerMeaning: "مكتوب (اسم مفعول)", icon: "fas fa-pen-nib" },
            { type: "true-false", level: "adult", question: "'Too' (as in 'also') is spelled with one 'o'.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "What is the name of a baby pig?", options: ["Kitten", "Puppy", "Piglet", "Calf"], answer: "Piglet", answerMeaning: "خنزير صغير", icon: "fas fa-piggy-bank" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to hear music.", answer: "ears", answerMeaning: "أذنين", icon: "fas fa-ear" },
            { type: "true-false", level: "adult", question: "A 'colon' (:) introduces a list or explanation.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-list-alt" },
            { type: "multiple-choice", level: "adult", question: "Which of these is a regular verb?", options: ["Go", "Run", "Eat", "Walk"], answer: "Walk", answerMeaning: "فعل منتظم", icon: "fas fa-walking" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'happy' is ____.", answer: "sad", answerMeaning: "حزين", icon: "fas fa-frown" },
            { type: "true-false", level: "child", question: "A fish can walk.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-fish" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses 'lend' correctly?", options: ["Can you borrow me your book?", "Can you lend me your book?", "Can you loan me your book?", "Can you gave me your book?"], answer: "Can you lend me your book?", answerMeaning: "هل يمكنك إعارتي كتابك؟", icon: "fas fa-book-reader" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'make' is ____.", answer: "made", answerMeaning: "صنع", icon: "fas fa-tools" },
            { type: "true-false", level: "adult", question: "'Everyday' (one word) is an adjective.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-calendar-day" },
            { type: "multiple-choice", level: "child", question: "What is the name of the place where trains stop?", options: ["Airport", "Port", "Bus stop", "Train station"], answer: "Train station", answerMeaning: "محطة قطار", icon: "fas fa-train" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to talk.", answer: "mouth", answerMeaning: "فم", icon: "fas fa-comment-dots" },
            { type: "true-false", level: "adult", question: "An 'ellipsis' (...) indicates omitted words.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-ellipsis-h" },
            { type: "multiple-choice", level: "adult", question: "Which of these is a common idiom?", options: ["It is raining cats and dogs.", "It is raining heavily.", "It is raining water.", "It is raining quickly."], answer: "It is raining cats and dogs.", answerMeaning: "إنها تمطر بغزارة (تعبير اصطلاحي)", icon: "fas fa-cloud-showers-heavy" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'open' is ____.", answer: "closed", answerMeaning: "مغلق", icon: "fas fa-door-closed" },
            { type: "true-false", level: "child", question: "A bird can swim underwater for a long time.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-dove" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses the present perfect continuous tense correctly?", options: ["I have lived here for 5 years.", "I have been living here for 5 years.", "I am living here for 5 years.", "I live here for 5 years."], answer: "I have been living here for 5 years.", answerMeaning: "أعيش هنا منذ 5 سنوات", icon: "fas fa-clock" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'break' is ____.", answer: "broken", answerMeaning: "مكسور (اسم مفعول)", icon: "fas fa-wrench" },
            { type: "true-false", level: "adult", question: "'Every day' (two words) is an adverbial phrase.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-calendar-alt" },
            { type: "multiple-choice", level: "child", question: "What do you use to see the world?", options: ["Ears", "Nose", "Eyes", "Hands"], answer: "Eyes", answerMeaning: "عيون", icon: "fas fa-eye" },
            { type: "fill-in-blank", level: "child", question: "A bed is for ____.", answer: "sleeping", answerMeaning: "النوم", icon: "fas fa-bed" },
            { type: "true-false", level: "adult", question: "A 'subordinating conjunction' introduces a dependent clause.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-link" },
            { type: "multiple-choice", level: "adult", question: "Which word means 'to obtain'?", options: ["Lose", "Give", "Get", "Discard"], answer: "Get", answerMeaning: "يحصل على", icon: "fas fa-gift" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'start' is ____.", answer: "finish", answerMeaning: "ينتهي", icon: "fas fa-stop" },
            { type: "true-false", level: "child", question: "A cat says 'meow'.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-cat" },
            { type: "multiple-choice", level: "adult", question: "Which word indicates a cause?", options: ["But", "And", "Because", "Or"], answer: "Because", answerMeaning: "لأن", icon: "fas fa-cogs" },
            { type: "fill-in-blank", level: "adult", question: "The past tense of 'swim' is ____.", answer: "swam", answerMeaning: "سبح", icon: "fas fa-person-swimming" },
            { type: "true-false", level: "adult", question: "'Who's' is a contraction of 'who is' or 'who has'.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-question-circle" },
            { type: "multiple-choice", level: "child", question: "What is the animal that has a long neck?", options: ["Lion", "Monkey", "Giraffe", "Elephant"], answer: "Giraffe", answerMeaning: "زرافة", icon: "fas fa-giraffe" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to eat.", answer: "mouth", answerMeaning: "فم", icon: "fas fa-mouth" },
            { type: "true-false", level: "adult", question: "A 'direct object' receives the action of the verb.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-bullseye" },
            { type: "multiple-choice", level: "adult", question: "Which word is an example of an uncountable noun?", options: ["Book", "Chair", "Water", "Apple"], answer: "Water", answerMeaning: "ماء (اسم غير معدود)", icon: "fas fa-tint" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'take' is ____.", answer: "taken", answerMeaning: "مأخوذ (اسم مفعول)", icon: "fas fa-hand-holding" },
            { type: "true-false", level: "adult", question: "'Lose' means to free from something.", answer: "false", answerMeaning: "خطأ (تعني يخسر)", icon: "fas fa-times" },
            { type: "multiple-choice", level: "child", question: "What is the name of a baby sheep?", options: ["Kitten", "Puppy", "Lamb", "Calf"], answer: "Lamb", answerMeaning: "حمل", icon: "fas fa-sheep" },
            { type: "fill-in-blank", level: "child", question: "A pen is used for ____.", answer: "writing", answerMeaning: "الكتابة", icon: "fas fa-pen" },
            { type: "true-false", level: "adult", question: "An 'adverb of frequency' tells how often something happens.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-redo" },
            { type: "multiple-choice", level: "adult", question: "Which sentence uses 'lay' correctly (to place something)?", options: ["I will lay down.", "I will lay the book on the table.", "I lay on the bed.", "The hen lays on the eggs."], answer: "I will lay the book on the table.", answerMeaning: "سأضع الكتاب على الطاولة", icon: "fas fa-book" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'easy' is ____.", answer: "difficult", answerMeaning: "صعب", icon: "fas fa-hard-hat" },
            { type: "true-false", level: "child", question: "The sun is blue.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-sun" },
            { type: "multiple-choice", level: "adult", question: "Which is a common mistake: 'I could of gone' or 'I could have gone'?", options: ["I could of gone", "I could have gone"], answer: "I could have gone", answerMeaning: "الصحيح كان بإمكاني الذهاب", icon: "fas fa-exclamation-triangle" },
            { type: "fill-in-blank", level: "adult", question: "The past participle of 'see' is ____.", answer: "seen", answerMeaning: "مُرى (اسم مفعول)", icon: "fas fa-eye" },
            { type: "true-false", level: "adult", question: "'Then' refers to time, 'than' is used for comparison.", answer: "true", answerMeaning: "صحيح", icon: "fas fa-clock" },
            { type: "multiple-choice", level: "child", question: "What is the name of a baby cow?", options: ["Kitten", "Puppy", "Lamb", "Calf"], answer: "Calf", answerMeaning: "عجل", icon: "fas fa-cow" },
            { type: "fill-in-blank", level: "child", question: "You use your ____ to write.", answer: "hand", answerMeaning: "يد", icon: "fas fa-pencil-alt" },
            { type: "true-false", level: "adult", question: "A 'run-on sentence' is always grammatically correct.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-times" },
            { type: "multiple-choice", level: "adult", question: "Which is a common error: 'Your' an amazing person' or 'You're an amazing person'?", options: ["Your an amazing person", "You're an amazing person"], answer: "You're an amazing person", answerMeaning: "أنت شخص رائع", icon: "fas fa-user-check" },
            { type: "fill-in-blank", level: "adult", question: "The opposite of 'begin' is ____.", answer: "end", answerMeaning: "ينتهي", icon: "fas fa-stop" },
            { type: "true-false", level: "child", question: "A fish can fly.", answer: "false", answerMeaning: "خطأ", icon: "fas fa-fish" },
            // Ensure we have over 150 questions (This list alone has more than 150)
        ];

        const quizDiv = document.getElementById('quiz');
        const playerNameInput = document.getElementById('playerName');
        const submitButton = document.getElementById('submitBtn');
        const shareButton = document.getElementById('shareBtn');
        const resultsDiv = document.getElementById('results');
        
        let questions = []; // This will hold the randomly selected questions for the current quiz
        const NUMBER_OF_QUESTIONS_TO_DISPLAY = 150; // Target number of questions for the quiz

        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]]; // Swap elements
            }
            return array;
        }

        function selectRandomQuestions(num) {
            const shuffled = shuffleArray([...allQuestions]); // Create a shuffled copy
            return shuffled.slice(0, num); // Take the first 'num' questions
        }

        function renderQuestions() {
            questions = selectRandomQuestions(NUMBER_OF_QUESTIONS_TO_DISPLAY);
            let totalQuestions = questions.length; // Update totalQuestions based on selected questions

            quizDiv.innerHTML = '';
            questions.forEach((q, index) => {
                const questionElement = document.createElement('div');
                questionElement.classList.add('question');
                
                const questionText = `<p><i class="${q.icon}"></i> ${index + 1}. ${q.question} <span style="font-size:0.8em; color:#888;">(${q.level === 'child' ? 'For Kids' : 'For Adults'})</span></p>`;
                questionElement.innerHTML = questionText;

                if (q.type === "multiple-choice") {
                    const optionsDiv = document.createElement('div');
                    optionsDiv.classList.add('options');
                    // Shuffle options for multiple-choice questions
                    const shuffledOptions = shuffleArray([...q.options]); 
                    shuffledOptions.forEach(option => {
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
                    // Options for true/false are always the same, no need to shuffle
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

        // Renamed 'checkAnswer' to be more descriptive and handle internal scoring logic
        function evaluateUserAnswer(question, userAnswer, index) {
            const feedbackElement = document.getElementById(`feedback-${index}`);
            let isCorrect = false;

            if (question.type === "multiple-choice" || question.type === "true-false") {
                isCorrect = (userAnswer.toLowerCase().trim() === question.answer.toLowerCase().trim());
            } else if (question.type === "fill-in-blank") {
                // Handle multiple correct answers for fill-in-blank if applicable (e.g., "fat / thick")
                const correctAnswers = question.answer.split(' / ').map(ans => ans.toLowerCase().trim());
                isCorrect = correctAnswers.includes(userAnswer.toLowerCase().trim());
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
            let score = 0; // Correct answers
            let answeredQuestionsCount = 0; // Count of questions attempted
            let userAnswers = []; // To store details for WhatsApp message
            
            const playerName = playerNameInput.value.trim();

            if (playerName === "") {
                alert("Please enter your name to start the quiz!");
                playerNameInput.focus();
                return;
            }

            questions.forEach((q, index) => {
                let userAnswer = '';
                let questionAttempted = false; 

                if (q.type === "multiple-choice" || q.type === "true-false") {
                    const selectedOption = document.querySelector(`input[name="question${index}"]:checked`);
                    if (selectedOption) {
                        userAnswer = selectedOption.value;
                        questionAttempted = true;
                    }
                } else if (q.type === "fill-in-blank") {
                    const inputField = document.getElementById(`q${index}`);
                    if (inputField && inputField.value.trim() !== '') {
                        userAnswer = inputField.value;
                        questionAttempted = true;
                    }
                }
                
                if (questionAttempted) {
                    answeredQuestionsCount++; 
                }

                // Pass the correct evaluation function
                const isCorrect = evaluateUserAnswer(q, userAnswer, index);
                if (isCorrect) {
                    score++; 
                }

                let correctDisplayAnswer = q.answer;
                if (q.answerMeaning) {
                    correctDisplayAnswer = `${q.answer} (${q.answerMeaning})`;
                }

                userAnswers.push({
                    questionText: q.question,
                    chosenAnswer: userAnswer || "Not Answered",
                    correctAnswer: correctDisplayAnswer,
                    isCorrect: isCorrect
                });
            });

            // Calculate incorrect answers (from total questions displayed in THIS quiz)
            const incorrectAnswers = questions.length - score;

            if (answeredQuestionsCount === questions.length) { // Check against the current quiz's total questions
                let answersDetail = "";
                userAnswers.forEach((item, index) => {
                    const status = item.isCorrect ? "Correct ✅" : `Incorrect ❌ (Correct: ${item.correctAnswer})`;
                    answersDetail += `\nQ${index + 1}: ${item.questionText}\nYour Answer: ${item.chosenAnswer}\nStatus: ${status}\n`;
                });

                finalResultMessage = `Hello! I'm *${playerName}*. I just took the Fun English Quiz!\n\n` +
                                     `*Total Questions: ${questions.length}*\n` + // Use questions.length
                                     `*Correct Answers: ${score} ✅*\n` +
                                     `*Incorrect Answers: ${incorrectAnswers} ❌*\n\n` + 
                                     `Awesome! 🎉\n\nHere are my answers:\n${answersDetail}\n\n` +
                                     `*Final Score: ${score}/${questions.length}*`;
                
                resultsDiv.textContent = `Great job, ${playerName}! You scored ${score} out of ${questions.length} questions! Awesome!`;
                shareButton.style.display = 'flex';
            } else {
                finalResultMessage = "";
                resultsDiv.textContent = `Please answer all questions to see your final score. You have answered ${answeredQuestionsCount} out of ${questions.length} questions so far.`;
                shareButton.style.display = 'none';
            }
        });

        shareButton.addEventListener('click', () => {
            if (finalResultMessage) {
                const encodedMessage = encodeURIComponent(finalResultMessage);
                const whatsappUrl = `https://wa.me/201117112423?text=${encodedMessage}`;
                window.open(whatsappUrl, '_blank');
            } else {
                alert('Please complete the quiz first to share your score!');
            }
        });

        // Initial render of questions when the page loads
        renderQuestions();
    </script>
</body>
</html>
