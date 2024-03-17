# haleetisler_hw5TH_csi3150

## Problem Statement
Quiz App Demo is a web application that takes the user through a set of 5 questions about topics in Computer Science. The landing page takes the user to a button where they are allowed to start their quiz. Upon clicking that button, a set of rules pops up explaining how the user can interact with the quiz. Once they are ready, they can start. As they answer the questions, they will be timed and scored on how many they get right. After answering all five questions, you are taken to a final screen that shows you your score and allows you to either retake the quiz or exit.

## Functional Features
<ul>
  <li>Start Button that brings up a popup with rules</li>
  <li>On the rules page, users can exit or start the quiz</li>
  <li>In the quiz, users can select from one of four options</li>
  <li>A timer for 15 seconds that resets for each question</li>
  <li>A progress bar that shows how much time is left</li>
  <li>Once an answer is selected, the correct (and incorrect, if chosen) answer pops up</li>
  <li>A final screen shows with how many questions the user got right</li>
  <li>At the end, the user can exit or try again</li>
</ul>

## Directory Structure
```
📂 css
  | style.css
📂 js
  | questions.js
  | quizApp.js
index.html
```

Your files should fall under 3 main components:
<ul>
  <li>index.html</li>
  <li>css folder</li>
  <li>js folder</li>
</ul>

**Disclaimer:** If you decide to change the directory structure of the files, then you must change the paths for the following pieces of code in index.html as they are all connected through the head of the html file:
```
<!--line 9-->
<link rel="stylesheet" href="css/style.css">

<!--line 11-->
<script src="https://kit.fontawesome.com/4a4f4b55b0.js" crossorigin="anonymous"></script>

<!--line 14-->
<script src="js/questions.js" defer></script>

<!--line 17-->
<script src="js/quizApp.js" defer></script>
```


## Code Explanation
