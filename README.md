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

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
            "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
	<title>Scripto Post Body Demo</title>
	<meta http-equiv="content-type" content="text/html; charset=utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"/>
	<meta name="apple-mobile-web-app-capable" content="yes"/>
	<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
	<meta http-equiv="refresh" content="3600">

</head>
<body>
<div id="wrapper">
<div id="header">
<h1>Scripto Post Body Demo</h1>
</div>
<p>
Username:<input type="text" id="username" /><br />
Password:<input type="password" id="password"  /><br /><br />
Enter some valid JSON (validate it <a href="http://jsonlint.com/" alt="jsonlint">here</a> if you're not sure): <br /><textarea id="jsoninput" rows=10 cols=20></textarea><br />
Enter arbitrary Text: <br /><textarea id="textinput" rows=10 cols=20></textarea>
<input type="submit" value="Go" id="submitbtn"  onclick="poststuff();"/>
</p>
<div id="response"></div>
</div>
		<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>
		<script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8.16/jquery-ui.min.js"></script>

  <script type="text/javascript">  
    	var poststuff= function(){
			var data = {}
			var temp
			if ($("#jsoninput").val() != ""){
				try {
					temp = $.parseJSON($("#jsoninput").val())
				}
				catch (e){
					temp = ""
				}
				if (temp && temp != ""){
					data = JSON.stringify(temp)
				}
			}
			else if ($("#textinput").val() != ""){
				data.text = $("#textinput").val()
				data = JSON.stringify(data)
			}
			else data = {"testing":"hello"}
			if ($("#username").val() != "" && $("#password").val() != ""){
				// you need contentType in order for the POST to succeed
				var promise = $.ajax({
					type:"POST",
					url: "http://dev6.axeda.com/services/v1/rest/Scripto/execute/TestPostBody?username=" + $("#username").val() + "&password=" + $("#password").val(),
					data: data,
					contentType:"application/json; charset=utf-8",
					dataType:"text"

				})
				$.when(promise).then(function(json){
					$("#response").html("<p>" + JSON.stringify(json) + "</p><br />Check your console for the object.<br />")
					console.log($.parseJSON(json))
					$("#jsoninput").val("")
					$("#textinput").val("")
				})
			}
		}
</script>
</body>
</html>
