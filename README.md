# SocialMediaAnalysis
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Social Media Sentiment Analysis</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f0f2f5;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .app {
      background: white;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 20px rgba(0,0,0,0.1);
      width: 90%;
      max-width: 600px;
    }

    h2 {
      text-align: center;
      color: #333;
    }

    textarea {
      width: 100%;
      height: 120px;
      margin-top: 20px;
      padding: 15px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 16px;
      resize: vertical;
    }

    button {
      margin-top: 20px;
      width: 100%;
      background: #3498db;
      color: white;
      font-size: 16px;
      padding: 12px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }

    button:hover {
      background: #2980b9;
    }

    .result {
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
      text-align: center;
      padding: 10px;
      border-radius: 6px;
    }

    .positive {
      color: #27ae60;
    }

    .negative {
      color: #e74c3c;
    }

    .neutral {
      color: #7f8c8d;
    }
  </style>
</head>
<body>
  <div class="app">
    <h2>🧠 Social Media Sentiment Analyzer</h2>
    <textarea id="textInput" placeholder="Paste a social media post here..."></textarea>
    <button onclick="analyzeSentiment()">Analyze Sentiment</button>
    <div id="output" class="result"></div>
  </div>

  <script>
    const positiveWords = ["good", "great", "happy", "love", "awesome", "fantastic", "excellent"];
    const negativeWords = ["bad", "terrible", "sad", "hate", "awful", "worst", "angry"];

    function analyzeSentiment() {
      const text = document.getElementById("textInput").value.toLowerCase();
      let score = 0;

      positiveWords.forEach(word => {
        if (text.includes(word)) score++;
      });

      negativeWords.forEach(word => {
        if (text.includes(word)) score--;
      });

      const output = document.getElementById("output");
      if (score > 0) {
        output.textContent = "Positive Sentiment 😊";
        output.className = "result positive";
      } else if (score < 0) {
        output.textContent = "Negative Sentiment 😠";
        output.className = "result negative";
      } else {
        output.textContent = "Neutral Sentiment 😐";
        output.className = "result neutral";
      }
    }
  </script>
</body>
</html>
