<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Refresh Grid</title>
<link rel="icon" href="https://ipfs.io/ipfs/QmcXRu9ZWwH3chUSJipNpwQXQPRcfPzTPPyk7pdDy49kEn" type="image/x-icon">
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
        font-size: 30px; /* Reduced font size by half */
        font-family: "Pixelify Sans", sans-serif; /* Apply custom font to pixels */
    }

    .refresh-button {
        font-size: 50px; /* Reduced font size by half */
        font-weight: bold;
        padding: 37.5px 75px; /* Reduced padding for smaller button */
        background-color: #4CAF50; /* Green color */
        color: white;
        border: 2px solid black; /* Set black border */
        border-radius: 37.5px; /* Rounded corners */
        cursor: pointer;
        text-decoration: none;
        position: relative; /* Required for absolute positioning of pseudo-elements */
        overflow: hidden; /* Ensure pseudo-elements stay within button boundaries */
        transition: background-color 0.3s, box-shadow 0.3s, border-color 0.3s; /* Smooth transition on hover */
        font-family: "Pixelify Sans", sans-serif; /* Apply custom font to button */
    }

    .refresh-button::before,
    .refresh-button::after {
        content: "";
        position: absolute;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
        z-index: -1; /* Behind the button content */
    }

    .refresh-button::before {
        border: 5px solid white; /* Set white border with increased thickness */
        border-radius: 37.5px; /* Match button's border radius */
    }

    .refresh-button:hover {
        background-color: #45a049; /* Darker green color on hover */
        box-shadow: 0px 30px 60px rgba(0, 0, 0, 0.2); /* Increase shadow on hover */
        border-color: #45a049; /* Darker green color on hover */
    }
</style>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Pixelify+Sans:wght@400..700&display=swap" rel="stylesheet">
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
    <button class="refresh-button" onclick="window.location.reload();">Refresh</button>
</body>
</html>
s
