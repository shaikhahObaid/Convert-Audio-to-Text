# Convert-Audio-to-Text
## The code 
<html>
<head>
<title>Live Update</title>
<meta charset="UTF-8">
<script type="text/javascript" src="autoUpdate.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
</head>
<body>
<p id="demo" style="display:none;"></p>
<script>


	function stt(){
		        // get output div reference
		        var output = document.getElementById("output");
		        // get action element reference
		        var action = document.getElementById("action");
                // new speech recognition object
                var SpeechRecognition = SpeechRecognition || webkitSpeechRecognition;
                var recognition = new SpeechRecognition();
            
                // This runs when the speech recognition service starts
                recognition.onstart = function() {
                    action.innerHTML = "<small>listening, please speak...</small>";
                };
                
                recognition.onspeechend = function() {
                    action.innerHTML = "<small>stopped listening</small>";
                    recognition.stop();
                }
              
                // This runs when the speech recognition service returns result
                recognition.onresult = function(event) {
                    var transcript = event.results[0][0].transcript;
                    var confidence = event.results[0][0].confidence;
                    output.innerHTML = transcript ;
                    output.classList.remove("hide");
                };
              
                 // start recognition
                 recognition.start();
	
	}

</script>
<div align="right">
<br>
<button class="button-71" role="button" onclick="stt()">

  "click to start"
</button>
<br>
<p>
<span id="action"></span>
</p>
<div id="output" class="hide"></div>
</div>
</body>
</html>
