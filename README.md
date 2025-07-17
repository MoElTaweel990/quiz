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
        const questions = [
            // General Questions (Adult/Child)
            {
                type: "multiple-choice",
                level: "child",
                question: "What is the opposite of 'big'?",
                options: ["small", "tall", "fast", "happy"],
                answer: "small",
                answerMeaning: "صغير",
                icon: "fas fa-child"
            },
            {
                type: "fill-in-blank",
                level: "child",
                question: "The sky is ____ (color).",
                answer: "blue",
                answerMeaning: "أزرق",
                icon: "fas fa-cloud"
            },
            {
                type: "true-false",
                level: "child",
                question: "A cat says 'woof'.",
                answer: "false",
                answerMeaning: "خطأ",
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
                answerMeaning: "هي ذهبت إلى المتجر أمس.",
                icon: "fas fa-brain"
            },
            {
                type: "fill-in-blank",
                level: "adult",
                question: "The passive voice is formed with a form of 'to be' and the past ____ of the main verb.",
                answer: "participle",
                answerMeaning: "اسم المفعول",
                icon: "fas fa-pencil-alt"
            },
            {
                type: "true-false",
                level: "adult",
                question: "'Affect' is typically a verb, while 'effect' is typically a noun.",
                answer: "true",
                answerMeaning: "صحيح",
                icon: "fas fa-lightbulb"
            },
            // Questions on English Letters A-Z
            // Letter A
            {
                type: "fill-in-blank",
                level: "child",
                question: "What is the first letter of the English alphabet?",
                answer: "A",
                answerMeaning: "الحرف الأول",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'A'?",
                options: ["Banana", "Apple", "Car", "Dog"],
                answer: "Apple",
                answerMeaning: "تفاح",
                icon: "fas fa-apple-alt"
            },
            // Letter B
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'A'?",
                answer: "B",
                answerMeaning: "الحرف الذي يلي A",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which animal starts with 'B'?",
                options: ["Cat", "Bird", "Fish", "Lion"],
                answer: "Bird",
                answerMeaning: "طائر",
                icon: "fas fa-dove"
            },
            // Letter C
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'B'?",
                answer: "C",
                answerMeaning: "الحرف الذي يلي B",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'C'?",
                options: ["House", "Chair", "Table", "Bed"],
                answer: "Chair",
                answerMeaning: "كرسي",
                icon: "fas fa-chair"
            },
            // Letter D
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'C'?",
                answer: "D",
                answerMeaning: "الحرف الذي يلي C",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which animal starts with 'D'?",
                options: ["Elephant", "Fox", "Dog", "Goat"],
                answer: "Dog",
                answerMeaning: "كلب",
                icon: "fas fa-dog"
            },
            // Letter E
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'D'?",
                answer: "E",
                answerMeaning: "الحرف الذي يلي D",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'E'?",
                options: ["Ant", "Egg", "Fish", "Grape"],
                answer: "Egg",
                answerMeaning: "بيضة",
                icon: "fas fa-egg"
            },
            // Letter F
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'E'?",
                answer: "F",
                answerMeaning: "الحرف الذي يلي E",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'F'?",
                options: ["Hand", "Foot", "Nose", "Ear"],
                answer: "Foot",
                answerMeaning: "قدم",
                icon: "fas fa-shoe-prints"
            },
            // Letter G
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'F'?",
                answer: "G",
                answerMeaning: "الحرف الذي يلي F",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'G'?",
                options: ["Door", "Glass", "Window", "Wall"],
                answer: "Glass",
                answerMeaning: "كوب / زجاج",
                icon: "fas fa-wine-glass"
            },
            // Letter H
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'G'?",
                answer: "H",
                answerMeaning: "الحرف الذي يلي G",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'H'?",
                options: ["Tree", "House", "Flower", "Grass"],
                answer: "House",
                answerMeaning: "منزل",
                icon: "fas fa-home"
            },
            // Letter I
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'H'?",
                answer: "I",
                answerMeaning: "الحرف الذي يلي H",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'I'?",
                options: ["Orange", "Ink", "Book", "Pencil"],
                answer: "Ink",
                answerMeaning: "حبر",
                icon: "fas fa-pen-nib"
            },
            // Letter J
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'I'?",
                answer: "J",
                answerMeaning: "الحرف الذي يلي I",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'J'?",
                options: ["Key", "Lock", "Jam", "Door"],
                answer: "Jam",
                answerMeaning: "مربى",
                icon: "fas fa-bread-slice"
            },
            // Letter K
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'J'?",
                answer: "K",
                answerMeaning: "الحرف الذي يلي J",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'K'?",
                options: ["Spoon", "Fork", "Knife", "Plate"],
                answer: "Knife",
                answerMeaning: "سكين",
                icon: "fas fa-utensils"
            },
            // Letter L
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'K'?",
                answer: "L",
                answerMeaning: "الحرف الذي يلي K",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which animal starts with 'L'?",
                options: ["Tiger", "Bear", "Lion", "Wolf"],
                answer: "Lion",
                answerMeaning: "أسد",
                icon: "fas fa-lion"
            },
            // Letter M
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'L'?",
                answer: "M",
                answerMeaning: "الحرف الذي يلي L",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'M'?",
                options: ["Sun", "Moon", "Star", "Cloud"],
                answer: "Moon",
                answerMeaning: "قمر",
                icon: "fas fa-moon"
            },
            // Letter N
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'M'?",
                answer: "N",
                answerMeaning: "الحرف الذي يلي M",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'N'?",
                options: ["Day", "Night", "Morning", "Evening"],
                answer: "Night",
                answerMeaning: "ليل",
                icon: "fas fa-cloud-moon"
            },
            // Letter O
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'N'?",
                answer: "O",
                answerMeaning: "الحرف الذي يلي N",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which fruit starts with 'O'?",
                options: ["Apple", "Banana", "Orange", "Grape"],
                answer: "Orange",
                answerMeaning: "برتقال",
                icon: "fas fa-orange"
            },
            // Letter P
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'O'?",
                answer: "P",
                answerMeaning: "الحرف الذي يلي O",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'P'?",
                options: ["Book", "Paper", "Pen", "Eraser"],
                answer: "Pen",
                answerMeaning: "قلم",
                icon: "fas fa-pen"
            },
            // Letter Q
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'P'?",
                answer: "Q",
                answerMeaning: "الحرف الذي يلي P",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'Q'?",
                options: ["King", "Queen", "Prince", "Princess"],
                answer: "Queen",
                answerMeaning: "ملكة",
                icon: "fas fa-crown"
            },
            // Letter R
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'Q'?",
                answer: "R",
                answerMeaning: "الحرف الذي يلي Q",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which color starts with 'R'?",
                options: ["Blue", "Green", "Yellow", "Red"],
                answer: "Red",
                answerMeaning: "أحمر",
                icon: "fas fa-palette"
            },
            // Letter S
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'R'?",
                answer: "S",
                answerMeaning: "الحرف الذي يلي R",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'S'?",
                options: ["Cloud", "Rain", "Snow", "Sun"],
                answer: "Sun",
                answerMeaning: "شمس",
                icon: "fas fa-sun"
            },
            // Letter T
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'S'?",
                answer: "T",
                answerMeaning: "الحرف الذي يلي S",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'T'?",
                options: ["Chair", "Table", "Sofa", "Bed"],
                answer: "Table",
                answerMeaning: "طاولة",
                icon: "fas fa-table"
            },
            // Letter U
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'T'?",
                answer: "U",
                answerMeaning: "الحرف الذي يلي T",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'U'?",
                options: ["Car", "Bus", "Umbrella", "Train"],
                answer: "Umbrella",
                answerMeaning: "مظلة",
                icon: "fas fa-umbrella"
            },
            // Letter V
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'U'?",
                answer: "V",
                answerMeaning: "الحرف الذي يلي U",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'V'?",
                options: ["Guitar", "Piano", "Violin", "Drum"],
                answer: "Violin",
                answerMeaning: "كمان",
                icon: "fas fa-violin"
            },
            // Letter W
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'V'?",
                answer: "W",
                answerMeaning: "الحرف الذي يلي V",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'W'?",
                options: ["Door", "Window", "Wall", "Roof"],
                answer: "Window",
                answerMeaning: "نافذة",
                icon: "fas fa-window-maximize"
            },
            // Letter X
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'W'?",
                answer: "X",
                answerMeaning: "الحرف الذي يلي W",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'X'?",
                options: ["Yoyo", "Xylophone", "Zebra", "Tiger"],
                answer: "Xylophone",
                answerMeaning: "إكسيليفون",
                icon: "fas fa-music"
            },
            // Letter Y
            {
                type: "fill-in-blank",
                level: "child",
                question: "What letter comes after 'X'?",
                answer: "Y",
                answerMeaning: "الحرف الذي يلي X",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which word starts with 'Y'?",
                options: ["Red", "Yellow", "Blue", "Green"],
                answer: "Yellow",
                answerMeaning: "أصفر",
                icon: "fas fa-palette"
            },
            // Letter Z
            {
                type: "fill-in-blank",
                level: "child",
                question: "What is the last letter of the English alphabet?",
                answer: "Z",
                answerMeaning: "الحرف الأخير",
                icon: "fas fa-font"
            },
            {
                type: "multiple-choice",
                level: "child",
                question: "Which animal starts with 'Z'?",
                options: ["Lion", "Tiger", "Zebra", "Bear"],
                answer: "Zebra",
                answerMeaning: "حمار وحشي",
                icon: "fas fa-horse"
            },
            // New Questions: It is / He is
            {
                type: "multiple-choice",
                level: "adult",
                question: "Choose the correct form: ____ a sunny day.",
                options: ["He is", "It is", "They are", "She is"],
                answer: "It is",
                answerMeaning: "إنه (يوم مشمس - لغير العاقل)",
                icon: "fas fa-sun"
            },
            {
                type: "fill-in-blank",
                level: "adult",
                question: "My brother is a doctor. ____ very busy.",
                answer: "He is",
                answerMeaning: "هو (جداً مشغول - للعاقل المذكر)",
                icon: "fas fa-user-md"
            },
            {
                type: "true-false",
                level: "adult",
                question: "'It is raining' refers to the weather.",
                answer: "true",
                answerMeaning: "صحيح (تصف الطقس)",
                icon: "fas fa-cloud-showers-heavy"
            },
            {
                type: "multiple-choice",
                level: "adult",
                question: "____ a good idea to study every day.",
                options: ["He is", "It is", "She is", "We are"],
                answer: "It is",
                answerMeaning: "إنه (فكرة جيدة - لغير العاقل/موقف)",
                icon: "fas fa-lightbulb"
            },
            // New Questions: Do / Did / Does
            {
                type: "multiple-choice",
                level: "adult",
                question: "____ you like coffee?",
                options: ["Does", "Did", "Do", "Is"],
                answer: "Do",
                answerMeaning: "هل (فعل مساعد للمضارع مع You)",
                icon: "fas fa-question-circle"
            },
            {
                type: "fill-in-blank",
                level: "adult",
                question: "She ____ not speak French.",
                answer: "does",
                answerMeaning: "لا (فعل مساعد للنفي في المضارع مع She)",
                icon: "fas fa-language"
            },
            {
                type: "true-false",
                level: "adult",
                question: "'Did he go to the party yesterday?' uses the past tense.",
                answer: "true",
                answerMeaning: "صحيح (يستخدم زمن الماضي)",
                icon: "fas fa-calendar-alt"
            },
            {
                type: "multiple-choice",
                level: "adult",
                question: "What ____ you ____ last night?",
                options: ["do / do", "did / do", "does / do", "do / did"],
                answer: "did / do",
                answerMeaning: "ماذا فعلت (فعل مساعد للماضي مع الفعل الأصلي)",
                icon: "fas fa-question-circle"
            },
            // New Questions: Have / Has / Had
            {
                type: "multiple-choice",
                level: "adult",
                question: "I ____ a new car.",
                options: ["has", "have", "had", "is"],
                answer: "have",
                answerMeaning: "أمتلك (للمضارع مع I)",
                icon: "fas fa-car"
            },
            {
                type: "fill-in-blank",
                level: "adult",
                question: "He ____ two sisters.",
                answer: "has",
                answerMeaning: "يمتلك (للمضارع مع He)",
                icon: "fas fa-users"
            },
            {
                type: "true-false",
                level: "adult",
                question: "They had a great time at the beach last summer.",
                answer: "true",
                answerMeaning: "صحيح (يمتلكون وقتاً رائعاً في الماضي)",
                icon: "fas fa-umbrella-beach"
            },
            {
                type: "multiple-choice",
                level: "adult",
                question: "We ____ finished our homework.",
                options: ["has", "had", "have", "is"],
                answer: "have",
                answerMeaning: "قد انتهينا (للمضارع التام مع We)",
                icon: "fas fa-book-open"
            },
            // New Questions: Verb to be (am, is, are, was, were)
            {
                type: "multiple-choice",
                level: "adult",
                question: "She ____ happy yesterday.",
                options: ["is", "am", "were", "was"],
                answer: "was",
                answerMeaning: "كانت (في الماضي للمفرد)",
                icon: "fas fa-history"
            },
            {
                type: "fill-in-blank",
                level: "adult",
                question: "They ____ students.",
                answer: "are",
                answerMeaning: "يكونون (للمضارع للجمع)",
                icon: "fas fa-user-graduate"
            },
            {
                type: "true-false",
                level: "adult",
                question: "I am a teacher. This sentence uses 'to be' in the present tense.",
                answer: "true",
                answerMeaning: "صحيح (يستخدم 'to be' في المضارع)",
                icon: "fas fa-chalkboard-teacher"
            },
            {
                type: "multiple-choice",
                level: "adult",
                question: "Where ____ you born?",
                options: ["was", "is", "were", "are"],
                answer: "were",
                answerMeaning: "كنت (في الماضي مع You)",
                icon: "fas fa-map-marker-alt"
            }
        ];

        const quizDiv = document.getElementById('quiz');
        const playerNameInput = document.getElementById('playerName');
        const submitButton = document.getElementById('submitBtn');
        const shareButton = document.getElementById('shareBtn');
        const resultsDiv = document.getElementById('results');
        let score = 0;
        let totalQuestions = questions.length;
        let answeredQuestions = 0;
        let finalResultMessage = "";
        let userAnswers = [];

        function renderQuestions() {
            quizDiv.innerHTML = '';
            questions.forEach((q, index) => {
                const questionElement = document.createElement('div');
                questionElement.classList.add('question');
                
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
                isCorrect = (userAnswer.toLowerCase().trim() === question.answer.toLowerCase().trim());
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
            userAnswers = [];
            
            const playerName = playerNameInput.value.trim();

            if (playerName === "") {
                alert("Please enter your name to start the quiz!");
                playerNameInput.focus();
                return;
            }

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

                const isCorrect = checkAnswer(q, userAnswer, index);

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

            if (answeredQuestions === totalQuestions) {
                let answersDetail = "";
                userAnswers.forEach((item, index) => {
                    const status = item.isCorrect ? "Correct ✅" : `Incorrect ❌ (Correct: ${item.correctAnswer})`;
                    answersDetail += `\nQ${index + 1}: ${item.questionText}\nYour Answer: ${item.chosenAnswer}\nStatus: ${status}\n`;
                });

                finalResultMessage = `Hello! I'm *${playerName}*. I just took the Fun English Quiz and scored *${score} out of ${totalQuestions}* questions! Awesome! 🎉\n\nHere are my answers:\n${answersDetail}\n\n*Final Score: ${score}/${totalQuestions}*`;
                resultsDiv.textContent = `Great job, ${playerName}! You scored ${score} out of ${totalQuestions} questions! Awesome!`;
                shareButton.style.display = 'flex';
            } else {
                finalResultMessage = "";
                resultsDiv.textContent = `Please answer all questions to see your final score. You have answered ${answeredQuestions} out of ${totalQuestions} questions so far.`;
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

        renderQuestions();
    </script>
</body>
</html>
