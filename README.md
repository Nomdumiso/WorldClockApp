# WorldClockApp
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>World Time App</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>World Time App</h1>
    <select id="locationSelect">
        <option value="America/New_York">New York</option>
        <option value="Europe/London">London</option>
        <option value="Asia/Tokyo">Tokyo</option>
    </select>
    <div id="timeDisplay"></div>
    <button id="homeButton" style="display:none;">Home</button>
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
}

#timeDisplay {
    margin-top: 20px;
    font-size: 24px;
}

#homeButton {
    margin-top: 20px;
}
document.addEventListener('DOMContentLoaded', () => {
    const locationSelect = document.getElementById('locationSelect');
    const timeDisplay = document.getElementById('timeDisplay');
    const homeButton = document.getElementById('homeButton');

    function updateTime() {
        const location = locationSelect.value;
        const date = new Date().toLocaleString('en-US', { timeZone: location });
        timeDisplay.textContent = `Current time in ${location.replace('_', ' ')}: ${date}`;
    }

    locationSelect.addEventListener('change', () => {
        updateTime();
        homeButton.style.display = 'block';
    });

    homeButton.addEventListener('click', () => {
        timeDisplay.textContent = '';
        homeButton.style.display = 'none';
    });

    // Display the user's current location time
    const userTimeDisplay = document.createElement('div');
    document.body.appendChild(userTimeDisplay);
    const userTime = new Date().toLocaleString();
    userTimeDisplay.textContent = `Your current time: ${userTime}`;

    // Initial time display
    updateTime();
});
