<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>100x100 Grid of Random Colours</title>
<style>
    body {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
        background-color: black; /* Set background color to black */
    }

    .pixel {
        width: 7px; /* Each pixel is 7x7 pixels (5px for the pixel + 1px border on each side) */
        height: 7px; /* Each pixel is 7x7 pixels (5px for the pixel + 1px border on each side) */
        display: inline-block;
        margin: 0;
        font-size: 12px;
    }
</style>
</head>
<body>
    <script>
        // Create a 100x100 grid of pixels with random colors
        let canvas = document.createElement('canvas');
        canvas.width = 700; // 100 * 7 (pixel size)
        canvas.height = 700; // 100 * 7 (pixel size)
        let ctx = canvas.getContext('2d');

        // Set canvas background color to black
        ctx.fillStyle = "black";
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        for (let i = 0; i < 100; i++) {
            for (let j = 0; j < 100; j++) {
                // Generate a random color
                let randomColor = '#' + Math.floor(Math.random() * 16777215).toString(16);
                // Set the pixel color
                ctx.fillStyle = randomColor;
                // Draw the pixel
                ctx.fillRect(j * 7 + 1, i * 7 + 1, 5, 5);
            }
        }

        // Convert canvas to base64-encoded PNG
        let imageDataURL = canvas.toDataURL('image/png');

        // Set the generated PNG as the body background
        document.body.style.backgroundImage = `url(${imageDataURL})`;
    </script>
</body>
</html>
