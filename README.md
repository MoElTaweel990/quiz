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
            { type: "true-false", level: "adult", question: "A 'preposition' shows the relati
