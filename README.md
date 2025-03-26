# Assignment-4
part 1
<!--
Name: Your Name
File: silly_story_generator.html
Date: March 2025
A JavaScript-based story generator that creates a silly random story based on user input.
-->

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Silly Story Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
        }
        button {
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <h1>Silly Story Generator</h1>
    <label for="customName">Enter a name:</label>
    <input type="text" id="customName" placeholder="Enter a name">
    <br>
    <button id="generate">Generate Story</button>
    <p id="story"></p>

    <script>
        document.getElementById('generate').addEventListener('click', generateStory);

        function generateStory() {
            const nameInput = document.getElementById('customName').value;
            const story = document.getElementById('story');
            
            let randomName = nameInput || 'Bob';
            let randomPlace = ["the park", "the zoo", "a castle"][Math.floor(Math.random() * 3)];
            let randomAction = ["danced joyfully", "sang loudly", "jumped in the air"][Math.floor(Math.random() * 3)];
            let randomTemp = ["hot", "cold", "rainy"][Math.floor(Math.random() * 3)];
            
            let storyText = `One day, ${randomName} went to ${randomPlace}. It was a ${randomTemp} day. ${randomName} ${randomAction} and made everyone laugh.`;
            
            story.textContent = storyText;
        }
    </script>
</body>
</html>part 2
<!--
Name: Your Name
File: image_gallery.html
Date: March 2025
A JavaScript-based image gallery that allows users to change images by clicking on thumbnails.
-->

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Gallery</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .gallery {
            display: flex;
            justify-content: center;
            gap: 10px;
        }
        .gallery img {
            width: 100px;
            cursor: pointer;
        }
        #displayed-image {
            width: 300px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Image Gallery</h1>
    <img id="displayed-image" src="image1.jpg" alt="Displayed Image">
    <div class="gallery">
        <img src="image1.jpg" alt="Image 1">
        <img src="image2.jpg" alt="Image 2">
        <img src="image3.jpg" alt="Image 3">
    </div>

    <script>
        const displayedImage = document.getElementById('displayed-image');
        const thumbnails = document.querySelectorAll('.gallery img');

        thumbnails.forEach(thumbnail => {
            thumbnail.addEventListener('click', function() {
                displayedImage.src = this.src;
                displayedImage.alt = this.alt;
            });
        });
    </script>
</body>
</html>
part 3
<!--
Name: Your Name
File: object_building_practice.html
Date: March 2025
A JavaScript practice file for creating and manipulating objects.
-->

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Object Building Practice</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
    </style>
</head>
<body>
    <h1>Object Building Practice</h1>
    <button id="showInfo">Show Person Info</button>
    <p id="output"></p>

    <script>
        const person = {
            name: "Alice",
            age: 25,
            job: "Developer",
            describe() {
                return `${this.name} is ${this.age} years old and works as a ${this.job}.`;
            }
        };

        document.getElementById('showInfo').addEventListener('click', function() {
            document.getElementById('output').textContent = person.describe();
        });
    </script>
</body>
</html>
part 4
<!--
Name: Your Name
File: bouncing_balls.html
Date: March 2025
A JavaScript-based animation that creates bouncing balls with dynamic movement.
-->

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bouncing Balls</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: black;
        }
        canvas {
            display: block;
        }
    </style>
</head>
<body>
    <canvas id="ballCanvas"></canvas>
    <script>
        const canvas = document.getElementById('ballCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        class Ball {
            constructor(x, y, velX, velY, color, size) {
                this.x = x;
                this.y = y;
                this.velX = velX;
                this.velY = velY;
                this.color = color;
                this.size = size;
            }
            draw() {
                ctx.beginPath();
                ctx.fillStyle = this.color;
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
            update() {
                if ((this.x + this.size) >= canvas.width || (this.x - this.size) <= 0) {
                    this.velX = -this.velX;
                }
                if ((this.y + this.size) >= canvas.height || (this.y - this.size) <= 0) {
                    this.velY = -this.velY;
                }
                this.x += this.velX;
                this.y += this.velY;
            }
        }

        const balls = [];
        for (let i = 0; i < 10; i++) {
            let size = Math.random() * 20 + 10;
            let ball = new Ball(
                Math.random() * (canvas.width - size * 2) + size,
                Math.random() * (canvas.height - size * 2) + size,
                Math.random() * 4 - 2,
                Math.random() * 4 - 2,
                `rgb(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255})`,
                size
            );
            balls.push(ball);
        }

        function loop() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.25)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            for (const ball of balls) {
                ball.draw();
                ball.update();
            }
            requestAnimationFrame(loop);
        }

        loop();
    </script>
</body>
</html>
