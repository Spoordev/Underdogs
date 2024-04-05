<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pixel Grid</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Pixelify+Sans:wght@400..700&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #ED1C24;
            margin: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: "Pixelify Sans", sans-serif; /* Apply custom font */
            color: white; /* Set text color */
        }
        h1 {
            font-size: 48px; /* Adjust font size for the title */
            margin-bottom: 20px; /* Add margin to the bottom of the title */
        }
        .pixel {
            width: 20px; /* Change width to make pixels larger */
            height: 20px; /* Change height to make pixels larger */
            background-color: white;
            border: 1px solid black;
            box-sizing: border-box;
            margin: -1px;
        }
        .grid {
            display: grid;
            grid-template-columns: repeat(32, 20px); /* Adjust width based on pixel size */
            grid-template-rows: repeat(32, 20px); /* Adjust height based on pixel size */
            gap: 0; /* No gap between pixels */
        }
    </style>
</head>
<body>
    <h1>ThomASScott</h1> <!-- Title -->

    <div class="grid" id="pixelGrid"></div>

    <script>
        // JavaScript to dynamically generate the 32x32 grid of pixel boxes
        const gridContainer = document.getElementById("pixelGrid");

        // Function to set the color of a pixel
        function setPixelColor(pixel, color) {
            pixel.style.backgroundColor = color;
        }

        // Example: Hex color values for each pixel (replace with your own values)
        const pixelColors = [
            "#FFFFFF", "#000000", "#FF0000", "#00FF00", "#0000FF",
            // Add more colors here if needed...
        ];

        let colorIndex = 0;

        for (let i = 0; i < 32; i++) {
            for (let j = 0; j < 32; j++) {
                const pixel = document.createElement("div");
                pixel.classList.add("pixel");
                gridContainer.appendChild(pixel);

                // Set color for each pixel
                setPixelColor(pixel, pixelColors[colorIndex]);

                // Increment colorIndex and loop back to the beginning if needed
                colorIndex = (colorIndex + 1) % pixelColors.length;
            }
        }
    </script>
</body>
</html>
