<!--
Name: Mustafa Mohd
File: image_gallery.html
Date: April 2nd 2025
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
            border: 2px solid #ddd;
            border-radius: 5px;
            transition: transform 0.2s;
        }
        .gallery img:hover {
            transform: scale(1.1);
        }
        #displayed-image {
            width: 300px;
            margin-top: 20px;
            border: 2px solid #000;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <h1>Image Gallery</h1>

    <!-- Main Displayed Image -->
    <img id="displayed-image" src="images/image1.jpg" alt="Displayed Image">
    
    <!-- Thumbnail Images -->
    <div class="gallery">
        <img src="images/image1.jpg" alt="Image 1">
        <img src="images/image2.jpg" alt="Image 2">
        <img src="images/image3.jpg" alt="Image 3">
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

        // Error handling for broken image links
        displayedImage.onerror = function() {
            displayedImage.src = "images/placeholder.jpg"; // Default placeholder image
            displayedImage.alt = "Image not found";
        };
    </script>
</body>
</html>
