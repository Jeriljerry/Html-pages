<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Form Submission with Timer</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
    }
    #timer {
      font-size: 30px;
      margin-top: 20px;
    }
    #form-container {
      display: none;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>Your form Submission for Purchase/Workorder creation is completed</h1>

  <!-- Google Form Embed -->
  <iframe id="google-form" src="https://docs.google.com/forms/d/e/1XoEuNPpnz9xSS_RubbtiyF2h0aSFChKk7bBHPUVvlf8/viewform?embedded=true" width="640" height="800" frameborder="0" marginheight="0" marginwidth="0">Loading...</iframe>

  <!-- Timer -->
  <div id="timer"></div>

  <!-- Form After Timer -->
  <div id="form-container">
    <h2>Form is now available again.</h2>
    <p>You can now submit the form again.</p>
    <iframe src="https://docs.google.com/forms/d/e/1XoEuNPpnz9xSS_RubbtiyF2h0aSFChKk7bBHPUVvlf8/viewform?embedded=true" width="640" height="800" frameborder="0" marginheight="0" marginwidth="0">Loading...</iframe>
  </div>

  <script>
    var countdown = 60; // Timer for 1 minute
    var timerElement = document.getElementById('timer');
    var formContainer = document.getElementById('form-container');
    var formIframe = document.getElementById('google-form');

    // Function to display the countdown timer
    function startTimer() {
      var interval = setInterval(function() {
        timerElement.textContent = 'Time remaining: ' + countdown + ' seconds';
        countdown--;
        if (countdown < 0) {
          clearInterval(interval);
          timerElement.textContent = 'Purchase/Work Order file created successfully';
          formIframe.style.display = 'none'; // Hide the form during countdown
          formContainer.style.display = 'block'; // Show the re-enabled form after timer
        }
      }, 1000);
    }

    // Start the timer when the page loads
    window.onload = startTimer;
  </script>
</body>
</html>
