<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YouTube Money Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #121212;
            color: white;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 500px;
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 15px rgba(255, 0, 0, 0.3);
            margin: 50px auto;
        }
        h2 {
            color: #ff0000;
        }
        input, select {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ff0000;
            border-radius: 5px;
            background-color: #333;
            color: white;
        }
        button {
            background-color: #ff0000;
            color: white;
            padding: 12px;
            border: none;
            cursor: pointer;
            width: 100%;
            font-size: 18px;
            border-radius: 5px;
            transition: 0.3s;
        }
        button:hover {
            background-color: #cc0000;
        }
        .result {
            font-size: 22px;
            font-weight: bold;
            margin-top: 15px;
            color: #00ff00;
        }
        .note {
            font-size: 12px;
            color: #bbb;
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>YouTube Money Calculator</h2>
        
        <label for="youtubeLink">Paste YouTube Video Link:</label>
        <input type="text" id="youtubeLink" placeholder="Enter YouTube video URL" oninput="extractVideoID()">
        
        <label for="views">Or Enter Views Manually:</label>
        <input type="number" id="views" placeholder="Enter total views">
        
        <label for="cpm">Select CPM (Cost per 1000 Views):</label>
        <select id="cpm">
            <option value="0.5">$0.5 - Very Low (General Content)</option>
            <option value="1">$1 - Low (Entertainment, Gaming)</option>
            <option value="5">$5 - Medium (Tech, Vlogs)</option>
            <option value="10">$10 - High (Finance, Business)</option>
            <option value="20">$20 - Very High (Real Estate, Insurance)</option>
            <option value="50">$50 - Ultra High (Luxury, Investment)</option>
        </select>

        <button onclick="calculateEarnings()">Calculate Earnings</button>

        <p class="result" id="earnings"></p>
        <p class="note">* This is an estimate. Actual earnings depend on audience location, ads, and engagement.</p>
    </div>

    <script>
        function extractVideoID() {
            let url = document.getElementById("youtubeLink").value;
            let videoID = "";

            // Extract video ID from different YouTube URL formats
            let match = url.match(/(?:youtu\.be\/|youtube\.com\/(?:embed\/|v\/|.*[?&]v=))([^?&]+)/);
            if (match) {
                videoID = match[1];
            }

            // Placeholder for YouTube API (Future Feature)
            if (videoID) {
                console.log("Extracted Video ID: " + videoID);
                // In the future, you can use YouTube API to fetch real views like:
                // fetch(`https://www.googleapis.com/youtube/v3/videos?part=statistics&id=${videoID}&key=YOUR_API_KEY`)
            }
        }

        function calculateEarnings() {
            let views = document.getElementById("views").value;
            let cpm = document.getElementById("cpm").value;

            if (views === "" || views <= 0) {
                document.getElementById("earnings").innerText = "Please enter a valid number of views.";
                return;
            }

            let estimatedEarnings = (views / 1000) * cpm;
            document.getElementById("earnings").innerText = "Estimated Earnings: $" + estimatedEarnings.toFixed(2);
        }
    </script>

</body>
</html>
