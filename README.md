<!DOCTYPE html>
<html>
<head>
<title>Advanced Quiz Game</title>
<style>
body{
    font-family:Arial;
    text-align:center;
    background:#f0f8ff;
}
.container{
    width:400px;
    margin:auto;
    margin-top:50px;
    padding:20px;
    background:white;
    border-radius:10px;
    box-shadow:0 0 10px gray;
}
button{
    width:100%;
    padding:10px;
    margin:10px 0;
    font-size:16px;
}
#timer{
    color:red;
    font-size:20px;
}
</style>
</head>
<body>
   <audio id="correctSound" src="https://www.soundjay.com/buttons/sounds/button-3.mp3"></audio>
<audio id="wrongSound" src="https://www.soundjay.com/buttons/sounds/button-10.mp3"></audio>

<div class="container">
    <h1>Quiz Game</h1>
    <p id="timer">Time: 10</p>
    <p id="question"></p>
    <button onclick="checkAnswer(0)" id="btn0"></button>
    <button onclick="checkAnswer(1)" id="btn1"></button>
    <button onclick="checkAnswer(2)" id="btn2"></button>
    <p id="score">Score: 0</p>
</div>

<script>
let questions=[

{
q:"Capital of India?",
options:["Delhi","Mumbai","Lucknow"],
answer:0
},
{
q:"2 + 2 = ?",
options:["3","4","5"],
answer:1
},
{
q:"HTML stands for?",
options:["Hyper Text Markup Language","High Text Machine Language","Hyper Tool Multi Language"],
answer:0
},
{
q:"CSS ka use kisliye hota hai?",
options:["Styling","Database","Compiler"],
answer:0
},
{
q:"JavaScript kisliye use hoti hai?",
options:["Styling","Programming","Storage"],
answer:1
},
{
q:"Computer ka brain kya hota hai?",
options:["CPU","Mouse","Keyboard"],
answer:0
},
{
q:"1 byte = ?",
options:["4 bits","8 bits","16 bits"],
answer:1
},
{
q:"India ka national animal?",
options:["Tiger","Lion","Elephant"],
answer:0
},
{
q:"Sun kis direction me rise hota hai?",
options:["West","East","North"],
answer:1
},
{
q:"RAM ka full form?",
options:["Random Access Memory","Read Access Memory","Run Access Memory"],
answer:0
},
{
q:"Keyboard me kitne function keys hoti hain?",
options:["10","12","14"],
answer:1
},
{
q:"Which is not a programming language?",
options:["Python","Java","Monitor"],
answer:2
},
{
q:"WWW ka full form?",
options:["World Wide Web","Wide World Web","Web World Wide"],
answer:0
},
{
q:"भारत का राष्ट्रीय पक्षी?",
options:["तोता","मोर","कबूतर"],
answer:1
},
{
q:"5 x 6 = ?",
options:["30","35","25"],
answer:0
},
{
q:"Mouse ek ___ device hai",
options:["Input","Output","Storage"],
answer:0
},
{
q:"Which planet is called Red Planet?",
options:["Mars","Earth","Venus"],
answer:0
},
{
q:"C language kis type ki language hai?",
options:["Low level","High level","Machine only"],
answer:1
},
{
q:"Monitor kya karta hai?",
options:["Input","Display","Print"],
answer:1
},
{
q:"India independence year?",
options:["1947","1950","1942"],
answer:0

},
{
   q:"india's present PM?",
   option:["Adityanath Yogi","Narendra Modi","Javahar lal nehru"],
   answer:2
}
];



let current=0;
let score=0;
let time=10;
let timer;

function loadQuestion(){
    clearInterval(timer);
    time=10;
    document.getElementById("timer").innerHTML="Time: "+time;

    timer=setInterval(()=>{
        time--;
        document.getElementById("timer").innerHTML="Time: "+time;

        if(time==0){
            current++;
            if(current<questions.length){
                loadQuestion();
            }else{
                endGame();
            }
        }
    },1000);

    document.getElementById("question").innerHTML=questions[current].q;
    document.getElementById("btn0").innerHTML=questions[current].options[0];
    document.getElementById("btn1").innerHTML=questions[current].options[1];
    document.getElementById("btn2").innerHTML=questions[current].options[2];
    document.getElementById("score").innerHTML="Score: "+score;
}

function checkAnswer(option){
    if(option==questions[current].answer){
        score++;
    }

    current++;

    if(current<questions.length){
        loadQuestion();
    }else{
        endGame();
    }
}

function endGame(){
    clearInterval(timer);
    document.querySelector(".container").innerHTML=
    "<h2>Game Over 🎉</h2><p>Your Score: "+score+"</p><button onclick='location.reload()'>Restart</button>";
}

loadQuestion();
</script>

</body>
</html>
