# boardpen.github.io
GitHub Web Portfolio test

<!DOCTYPE html><html lang="en"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>URL Fetcher</title>
    <script>
        async function fetchURL() {
            const urlInput = document.getElementById('urlInput').value;
            try {
                const response = await fetch(urlInput);
                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }
                const html = await response.text();
                // 여기에 가져온 HTML을 처리하는 로직을 추가할 수 있습니다.
                console.log(html); // 가져온 HTML을 콘솔에 출력합니다.
                alert("HTML fetched successfully! Check the console for the output.");
            } catch (error) {
                console.error('Error fetching the URL:', error);
                alert('Failed to fetch the URL.');
            }
        }
    </script></head><body>
    <h1>URL Fetcher</h1>
    <input type="text" id="urlInput" placeholder="Enter URL here" style="width: 300px;">
    <button onclick="fetchURL()">Fetch URL</button></body></html>
