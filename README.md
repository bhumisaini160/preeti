<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Friendship Request</title>
    <!-- Google Fonts for stylish text -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Roboto:wght@400&display=swap" rel="stylesheet">
    <style>
        body {
            background-image: url('https://assets.onecompiler.app/42yhaadyw/42ykx7yur/f1.webp'); /* Change to your desired image URL */
            background-size: cover;
            background-position: center;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: Arial, sans-serif;
            overflow: hidden;
            flex-direction: column; /* Stack content vertically */
        }

        /* Styling for the name at the top */
        #name {
            font-family: 'Playfair Display', serif;
            color: white;
            font-size: 3em;
            font-weight: bold;
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.5);
        }

        /* Styling for the big heart */
        #heart {
            position: absolute;
            top: 20px;
            left: 60%; /* Adjust to position the heart beside the text */
            font-size: 5em;
            color: red;
            animation: twinkle 1s ease-in-out infinite, burst 2s ease-out 3s forwards;
            transform-origin: center;
        }

        /* Twinkle effect for the heart */
        @keyframes twinkle {
            0% {
                opacity: 1;
                transform: scale(1);
            }
            50% {
                opacity: 0.7;
                transform: scale(1.1);
            }
            100% {
                opacity: 1;
                transform: scale(1);
            }
        }

        /* Burst effect for the heart */
        @keyframes burst {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.5);
            }
            100% {
                transform: scale(0);
                opacity: 0;
            }
        }

        /* Create smaller hearts that burst */
        .burst-heart {
            position: absolute;
            width: 30px;
            height: 30px;
            background-color: red;
            clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
            animation: mini-heart 0.5s ease-in forwards;
            z-index: 10;
        }

        @keyframes mini-heart {
            0% {
                transform: scale(0.5);
                opacity: 1;
            }
            100% {
                transform: translateY(-150px) scale(1.5);
                opacity: 0;
            }
        }

        #box {
            background: white;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            z-index: 1;
        }

        #question {
            font-size: 1.5em;
            margin-bottom: 20px;
        }

        .button {
            background-color: #ff4d4d;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            font-size: 1em;
            cursor: pointer;
            transition: 0.3s;
        }

        .button:hover {
            background-color: #ff1a1a;
        }

        #story {
            display: none;
            font-size: 1.2em;
            color: #333;
            text-align: left;
            margin-top: 20px;
            line-height: 1.5;
        }
    </style>
</head>
<body>
    <audio autoplay loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mp3">
        Your browser does not support the audio element.
    </audio>
    
    <!-- PREET SHUKLA text at the top -->
    <div id="name">PREET SHUKLA</div>
    
    <!-- Big Red Heart beside PREET SHUKLA -->
    <div id="heart">❤️</div>

    <div id="box">
        <div id="question">Wanna be friends?</div>
        <button id="yes" class="button">Yes</button>
        <button id="no" class="button">No</button>
        <div id="story"></div>
    </div>

    <script>
        const yesButton = document.getElementById("yes");
        const noButton = document.getElementById("no");
        const storyDiv = document.getElementById("story");
        const storyText = [
            "Hey, we were so good friends before.",
            "It’s been around 1.5 years of friendship.",
            "Why has our friendship become like this, where we think before talking?",
            "Meeting face-to-face is rare; even a simple hello feels absent.",
            "You ignore me, and it hurts so much.",
            "I confessed my feelings, and still, you act like this.",
            "Think about a year ago when you used to share everything with me.",
            "You even called me your best friend.",
            "Now, it feels like you are avoiding me and our friendship.",
            "If I did something wrong, talk to me instead of cutting off conversations.",
            "I want our friendship to be like before. Will you be my best friend again?"
        ];
        let currentLine = 0;

        // Handle "Yes" button click
        yesButton.addEventListener("click", () => {
            storyDiv.style.display = "block";
            yesButton.style.display = "none";
            noButton.style.display = "none";

            const interval = setInterval(() => {
                if (currentLine < storyText.length) {
                    storyDiv.innerText = storyText[currentLine];
                    currentLine++;
                } else {
                    clearInterval(interval);
                    storyDiv.innerText = "Will you be my best friend again? 💖";
                }
            }, 5000); // Show each line for 5 seconds
        });

        // Handle "No" button click (moving the button)
        noButton.addEventListener("mouseover", () => {
            const x = Math.random() * 200 - 100;
            const y = Math.random() * 200 - 100;
            noButton.style.transform = `translate(${x}px, ${y}px)`;
        });

        // Burst effect when heart bursts
        function burstHearts() {
            const heartCount = 30; // Number of mini hearts
            for (let i = 0; i < heartCount; i++) {
                const heart = document.createElement("div");
                heart.classList.add("burst-heart");
                heart.style.left = `${window.innerWidth / 2 - 30}px`; // Position the burst at the center
                heart.style.top = `${window.innerHeight / 2 - 30}px`;
                document.body.appendChild(heart);

                // Remove the heart after animation
                setTimeout(() => {
                    heart.remove();
                }, 500);
            }
        }

        // Trigger burst effect when the heart bursts
        document.getElementById('heart').addEventListener('animationend', () => {
            burstHearts();
        });
    </script>
</body>
</html>
