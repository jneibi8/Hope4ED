# Hope4ED
<!DOCTYPE html>
<html>
<head>
	<title>Psychometric Test</title>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<style>
		body {
			font-family: Arial, sans-serif;
			background-color: #f0f0f0;
		}

		.container {
			max-width: 800px;
			margin: 0 auto;
			padding: 20px;
			background-color: #fff;
			box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
		}

		h1 {
			text-align: center;
			margin-bottom: 20px;
		}

		h2 {
			margin-top: 40px;
			margin-bottom: 20px;
		}

		.question {
			margin-bottom: 10px;
			font-size: 18px;
			font-weight: bold;
		}

		.answer {
			margin-bottom: 10px;
			font-size: 16px;
		}

		button {
			display: block;
			margin: 0 auto;
			margin-top: 20px;
			padding: 10px 20px;
			font-size: 18px;
			font-weight: bold;
			color: #fff;
			background-color: #007bff;
			border: none;
			border-radius: 5px;
			cursor: pointer;
		}

		.result {
			margin-top: 40px;
			font-size: 24px;
			font-weight: bold;
			text-align: center;
		}

		.definition {
			margin-top: 20px;
			font-size: 18px;
			text-align: justify;
		}
	</style>
</head>
<body>
	<div class="container">
		<h1>Psychometric Test</h1>

		<div id="questions">
			<!-- Questions will be added dynamically with JavaScript -->
		</div>

		<button onclick="calculateScore()">Submit</button>

		<div id="results" style="display: none;">
			<h2>Results</h2>
			<p>Your final score is <span id="score"></span>.</p>
			<p>Your personality type is <span id="personality"></span>.</p>
			<div class="definition" id="definition">
				<!-- Personality type definition will be added dynamically with JavaScript -->
			</div>
		</div>
	</div>

	<script>
		// Questions
		var questions = [
			"I enjoy spending time alone.",
			"I am usually the life of the party.",
			"I am very organized.",
			"I often feel anxious or worried.",
			"I am a good listener.",
			"I like to take charge in group situations.",
			"I enjoy trying new things.",
			"I am detail-oriented.",
			"I am sensitive to other people's feelings.",
			"I have a hard time saying no to people.",
			"I prefer routines and structure.",
			"I am very self-motivated.",
			"I like to plan things out in advance.",
			"I am a creative person.",
			"I am comfortable with taking risks.",
			"I can be impulsive at times.",
			"I have a strong sense of empathy.",
			"I am very competitive.",
			"I am easily stressed.",
			"I am a natural leader.",
			"I am a patient person.",
			"I enjoy helping others.",
			"I am easily distracted.",
      "I am a good problem solver.",
      "I am a positive and optimistic person."
       ];
       	// Score ranges for each personality type
	var scoreRanges = [
		{
			type: "Type A",
			minScore: 0,
			maxScore: 25,
			definition: "Type A individuals are ambitious, competitive, and always striving to achieve more. They are often impatient and have a high level of stress."
		},
		{
			type: "Type B",
			minScore: 26,
			maxScore: 50,
			definition: "Type B individuals are laid-back and relaxed. They are not as competitive as Type A individuals and are more likely to enjoy the journey than the destination."
		},
		{
			type: "Type C",
			minScore: 51,
			maxScore: 75,
			definition: "Type C individuals are detail-oriented and conscientious. They are often introverted and prefer to work independently. They may have a tendency to worry and be pessimistic."
		},
		{
			type: "Type D",
			minScore: 76,
			maxScore: 100,
			definition: "Type D individuals are characterized by their negative emotions, such as anxiety, stress, and depression. They may be introverted and have difficulty expressing their emotions to others."
		}
	];

	// Dynamically create questions
	var questionsHtml = "";
	for (var i = 0; i < questions.length; i++) {
		questionsHtml += '<div class="question">' + questions[i] + '</div>';
		questionsHtml += '<div class="answer">';
		questionsHtml += '<input type="radio" name="question' + i + '" value="0" required> Strongly disagree';
		questionsHtml += '<br>';
		questionsHtml += '<input type="radio" name="question' + i + '" value="1"> Disagree';
		questionsHtml += '<br>';
		questionsHtml += '<input type="radio" name="question' + i + '" value="2"> Neutral';
		questionsHtml += '<br>';
		questionsHtml += '<input type="radio" name="question' + i + '" value="3"> Agree';
		questionsHtml += '<br>';
		questionsHtml += '<input type="radio" name="question' + i + '" value="4"> Strongly agree';
		questionsHtml += '</div>';
	}
	document.getElementById("questions").innerHTML = questionsHtml;

	// Calculate score and display results
	function calculateScore() {
		var score = 0;
		for (var i = 0; i < questions.length; i++) {
			score += parseInt(document.querySelector('input[name="question' + i + '"]:checked').value);
		}
		document.getElementById("score").innerHTML = score;

		// Determine personality type based on score
		var personalityType = "";
		for (var i = 0; i < scoreRanges.length; i++) {
			if (score >= scoreRanges[i].minScore && score <= scoreRanges[i].maxScore) {
				personalityType = scoreRanges[i].type;
				document.getElementById("definition").innerHTML = scoreRanges[i].definition;
				break;
			}
		}
		document.getElementById("personality").innerHTML = personalityType;

		// Show results section
		document.getElementById("results").style.display = "block";
	}
</script>
</ body>
</ html>
