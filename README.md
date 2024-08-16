<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Website HTML Fetcher</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        #container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        input[type="text"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 4px;
            border: 1px solid #ccc;
        }
        button {
            padding: 10px 15px;
            background-color: #007bff;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        pre {
            background-color: #f4f4f4;
            padding: 15px;
            border-radius: 4px;
            border: 1px solid #ddd;
            overflow-x: auto;
        }
    </style>
</head>
<body>
    <div id="container">
        <h1>Website HTML Fetcher</h1>
        <input type="text" id="url" placeholder="Enter the website URL">
        <button onclick="fetchHTML()">Fetch HTML</button>
        <h3>HTML Output:</h3>
        <pre id="output"></pre>
    </div>
    <script>
        function fetchHTML() {
            const url = document.getElementById('url').value;
            fetch(`/get-html?url=${encodeURIComponent(url)}`)
                .then(response => response.text())
                .then(data => {
                    document.getElementById('output').textContent = data;
                })
                .catch(error => {
                    document.getElementById('output').textContent = 'An error occurred: ' + error;
                });
        }
    </script>
</body>
</html>
