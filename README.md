# haleetisler_hw5TH_csi3150

## Problem Statement
Quiz App Demo is a web application that takes the user through a set of 5 questions about topics in Computer Science. The landing page takes the user to a button where they are allowed to start their quiz. Upon clicking that button, a set of rules pops up explaining how the user can interact with the quiz. Once they are ready, they can start. As they answer the questions, they will be timed and scored on how many they get right. After answering all five questions, you are taken to a final screen that shows you your score and allows you to either retake the quiz or exit.

<img src="https://github.com/halee-t/haleetisler_hw5TH_csi3150/assets/123340415/f28b2acd-8946-487f-b269-6bba6f36a5e3" height="200px">
<img src="https://github.com/halee-t/haleetisler_hw5TH_csi3150/assets/123340415/a83fb4d1-5dcf-40e5-88e7-787595df0141" height="200px">
<img src="https://github.com/halee-t/haleetisler_hw5TH_csi3150/assets/123340415/8f8307cf-de73-4729-bb2a-5ac971710a23" height="200px">
<img src="https://github.com/halee-t/haleetisler_hw5TH_csi3150/assets/123340415/06160ac1-ff88-4dc1-98a4-66c836052c8d" height="200px">

## Functional Features
<ul>
  <li>Start Button that brings up a popup with rules</li>
  <li>On the rules page, users can exit or start the quiz</li>
  <li>In the quiz, users can select from one of four options</li>
  <li>A timer for 15 seconds that resets for each question</li>
  <li>A progress bar that shows how much time is left</li>
  <li>Once an answer is selected, immediate feedback on the correct (and incorrect if chosen) answer must display</li>
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
.gitignore
README.md
```

Your files should fall under 3 main components:
<ul>
  <li>index.html</li>
  <li>css folder</li>
  <li>js folder</li>
</ul>

**Disclaimer:** If you decide to change the directory structure of the files, then you must change the paths for the following pieces of code in index.html as they are all connected through the head of the html file:
```html
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

### index.html
- The head section includes all of the important information such as the meta tags, the title of the application (Quiz App Demo), and the connecting links to other files in the directory. If your fontawesome does not work, then you may need to create an account.
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz App Demo</title>

    <!-- CSS FILE -->
    <link rel="stylesheet" href="css/style.css">
    <!-- This is my personal font awesome kit code. you will have to add your own after you register with email-->
    <script src="https://kit.fontawesome.com/4a4f4b55b0.js" crossorigin="anonymous"></script>

     <!-- Add questions list -->
    <script src="js/questions.js" defer></script>

    <!-- Main logic of the app -->
    <script src="js/quizApp.js" defer></script>
</head>
```
<ul>
  <li>Within the body, the first element is the Start Quiz button you see upon opening.</li>
</ul>

```html
<!-- Quiz START Button -->
    <div class="start_btn"><button>Start Quiz</button></div>
```
<ul>
  <li>The Instruction Box Wrapper is a pop up card that includes the rules of the game. The three main components are the title, the list, and the buttons to quit or to start the quiz.</li>
</ul>

```html
<!-- Instruction box wrapper -->
    <div class="info_box">
        <div class="info-title"><span>Some Rules of this Quiz</span></div>
        <div class="info-list">
            <div class="info">1. You will have only <span>15 seconds</span> per each question.</div>
            <div class="info">2. Once you select your answer, it can't be undone.</div>
            <div class="info">3. You can't select any option once time goes off.</div>
            <div class="info">4. You can't exit from the Quiz while you're playing.</div>
            <div class="info">5. You'll get points on the basis of your correct answers.</div>
        </div>
        <div class="buttons">
            <button class="quit">Exit Quiz</button>
            <button class="restart">Continue</button>
        </div>
    </div>
```

- The Quiz Box includes:
  - Header with the title, timer, and progress bar
  - Main section with the question and the options that will be taken from ./js/questions.js
  - Footer with the question number that the user is on and the button to go to the next question


```html
<!-- Quiz Box -->
    <div class="quiz_box">
        <header>
            <div class="title">Demo Quiz App in JavaScript</div>
            <div class="timer">
                <div class="time_left_txt">Time Left</div>
                <div class="timer_sec">15</div>
            </div>
            <div class="time_line"></div>
        </header>
        <section>
            <div class="que_text">
                <!-- Insert questions from ./js/questions.js -->
            </div>
            <div class="option_list">
                <!-- Insert options to questions from ./js/questions.js -->
            </div>
        </section>

        <!-- footer of Quiz Box -->
        <footer>
            <div class="total_que">
                <!-- insert Question Count Number dynamically from JavaScript App logic -->
            </div>
            <button class="next_btn">Next Que</button>
        </footer>
    </div>
```
- The last section in the body is the Result Box. This is what pops up when you are done with the quiz. It displays:
  - A crown icon
  - A title text saying the user has completed the quiz
  - The score, taken dynamically from quizApp.js
  - Buttons to either replay or quit

 ```html
<!-- Result Box -->
    <div class="result_box">
        <div class="icon">
            <i class="fas fa-crown"></i>
        </div>
        <div class="complete_text">You've completed the Quiz!</div>
        <div class="score_text">
            <!-- insert dynamic user score as Result from JavaScript -->
        </div>
        <div class="buttons">
            <button class="restart">Replay Quiz</button>
            <button class="quit">Quit Quiz</button>
        </div>
    </div>
```

### style.css
A lot of the css file is done to simply make the application look pleasing to the eye. I will cover the sections that may not be as easily recognizable. 

- The Poppins font from google is imported to customize the application
  ```css
  @import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap");
  ```

- When you highlight text on the page, the font color turns white and the highlight turns purple
```css
  ::selection {
  color: #fff;
  background: #a020f0;
}
```

- A z-index is set to allow the boxes to be stacked on top of each other with only the one that needs to be shown on top
```css
.info_box.activeInfo,
.quiz_box.activeQuiz,
.result_box.activeResult {
  opacity: 1;
  z-index: 5;
  pointer-events: auto;
  transform: translate(-50%, -50%) scale(1);
}
```

- The `pointer-events: none;` controls what happens with the mouse controls. It allows no clicks, hovers, or mouse wheel events.
- The `user-select: none;` makes sure that the user cannot select the header or timer.

### questions.js
This file creates an array of objects that each contain the following:
<ul>
  <li>question number</li>
  <li>question</li>
  <li>answer</li>
  <li>the options: note that this is an array within itself</li>
</ul>
If you would like to add more questions/change the existing ones, you would do so here. <br>
❗️❗️ Note: If you change or add to this file, you must follow the same format ❗️❗️

### quizApp.js
- The first 15 lines are dedicated to declaring variables and assigning them to their respective html class
  - ex: `const start_btn = document.querySelector(".start_btn button");`
- If a button is clicked by the user, these lines will execute the action that is needed
  - clicking the start button will show the info box
  - clicking the exit button will hide the info box
  - clicking the continue button will hide the info box, open the quiz box, and call various functions that will show the questions, set the question count, and start the timer and progress line
  ```js
  // if startQuiz button clicked
  start_btn.addEventListener("click", (e) => {
    info_box.classList.add("activeInfo"); //show info box
  });
  
  // if exitQuiz button clicked
  exit_btn.addEventListener("click", (e) => {
    info_box.classList.remove("activeInfo"); //hide info box
  });
  
  // if continueQuiz button clicked
  continue_btn.addEventListener("click", (e) => {
    info_box.classList.remove("activeInfo"); //hide info box
    quiz_box.classList.add("activeQuiz"); //show quiz box
    showQuetions(0); //calling showQestions function
    queCounter(1); //passing 1 parameter to queCounter
    startTimer(15); //calling startTimer function
    startTimerLine(0); //calling startTimerLine function
  });
  ```
- At the end of the quiz, if the user decided to restart it, then the following code executes.
  - The quiz box is shown again as the result box is hidden
  - All variables are reset
  - The showQuestions, queCounter, startTimer, and startTimerLine are called again to go through the quiz
    ```js
    // if restartQuiz button clicked
    restart_quiz.addEventListener("click", (e) => {
      quiz_box.classList.add("activeQuiz"); //show quiz box
      result_box.classList.remove("activeResult"); //hide result box
      timeValue = 15;
      que_count = 0;
      que_numb = 1;
      userScore = 0;
      widthValue = 0;
      showQuetions(que_count); //calling showQestions function
      queCounter(que_numb); //passing que_numb value to queCounter
      clearInterval(counter); //clear counter
      clearInterval(counterLine); //clear counterLine
      startTimer(timeValue); //calling startTimer function
      startTimerLine(widthValue); //calling startTimerLine function
      timeText.textContent = "Time Left"; //change the text of timeText to Time Left
      next_btn.classList.remove("show"); //hide the next button
    });
    ```
- If the next button is clicked during the quiz, one of two things happen
  - if you are not on the last question, the the question count increases, the question number increases, and you recall all necessary quiz functions with the new counts
  - if you just finished the last question, then you need to clear the counter and show the result page
  ```js
  // if Next Question button is clicked
  next_btn.addEventListener("click", (e) => {
    //check if it does not exceed max questions
    if (que_count < questions.length - 1) {
      que_count++; //increment the que_count value
      que_numb++; //increment the que_numb value
      showQuetions(que_count); //calling showQestions function
      queCounter(que_numb); //passing que_numb value to queCounter
      clearInterval(counter); //clear counter
      clearInterval(counterLine); //clear counterLine
      startTimer(timeValue); //calling startTimer function
      startTimerLine(widthValue); //calling startTimerLine function
      timeText.textContent = "Time Left"; //change the timeText to Time Left
      next_btn.classList.remove("show"); //hide the next button
    } else {
      clearInterval(counter); //clear counter
      clearInterval(counterLine); //clear counterLine
      showResult(); //calling showResult function
    }
  });
  ```
  
- the function showQuetions takes all the information from the questions.js array and sends it to a respective html element to display
  - the let sections assign all of the html elements
  - the lines with .innerHTML is what sends it to index.html to be displayed
  - all answer options are filled in with the for loop

  ```js
  // getting questions and options from array
  // If you have lesser or more number of options you need to change this code
  function showQuetions(index) {
    const que_text = document.querySelector(".que_text");
  
    //creating a new span and div tag for question and option and passing the value using array index
    // self exercise: re-write the following using backtick syntax for string in JS instead of concatenation operator
    let que_tag =
      "<span>" +
      questions[index].numb +
      ". " +
      questions[index].question +
      "</span>";
    let option_tag =
      '<div class="option"><span>' +
      questions[index].options[0] +
      "</span></div>" +
      '<div class="option"><span>' +
      questions[index].options[1] +
      "</span></div>" +
      '<div class="option"><span>' +
      questions[index].options[2] +
      "</span></div>" +
      '<div class="option"><span>' +
      questions[index].options[3] +
      "</span></div>";
    que_text.innerHTML = que_tag; //adding new (child) span tag inside que_tag
    option_list.innerHTML = option_tag; //adding new (child) div tag inside option_tag
  
    const option = option_list.querySelectorAll(".option");
  
    // set onclick attribute to all available options
    for (i = 0; i < option.length; i++) {
      option[i].setAttribute("onclick", "optionSelected(this)");
    }
  }
  ```

- The optionSelected function deals with what should happen when the user selects an answer
  - The timer and progress bar should be reset with clearInterval()
  - You then need to set variables for the selected option, the correct answer, and all options
  - If the user got it right, increase their score, and add the appropriate designs to indicate that they got it right
  - If the user got it wrong, add the appropriate designs to indicate they got it wrong, find the correct answer, and style that option as well
  - All options must now be disabled
  - The next button must be shown

  ```js
  //if user clicked on option
  function optionSelected(answer) {
    clearInterval(counter); //clear counter
    clearInterval(counterLine); //clear counterLine
    let userAns = answer.textContent; //getting user selected option
    let correcAns = questions[que_count].answer; //getting correct answer from array
    const allOptions = option_list.children.length; //getting all option items
  
    //if user selected option is equal to array's correct answer
    if (userAns == correcAns) {
      userScore += 1; //update total score value increment by 1
      answer.classList.add("correct"); //add green color to correct selected option
      answer.insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to correct selected option
      console.log("Correct Answer");
      console.log("Your correct answers = " + userScore);
    } else {
      answer.classList.add("incorrect"); //add red color to correct selected option
      answer.insertAdjacentHTML("beforeend", crossIconTag); //add cross icon to correct selected option
      console.log("Wrong Answer");
  
      for (i = 0; i < allOptions; i++) {
        if (option_list.children[i].textContent == correcAns) {
          //if there is an option which is matched to an array answer
          option_list.children[i].setAttribute("class", "option correct"); //add green color to matched option
          option_list.children[i].insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to matched option
          console.log("Auto selected correct answer.");
        }
      }
    }
    for (i = 0; i < allOptions; i++) {
      option_list.children[i].classList.add("disabled"); //once user select an option, disable all options
    }
    next_btn.classList.add("show"); //show the next button if user selected any option
  }
  ```

- The showResult() function is called when the user finishes the quiz and the result page should show
  - The info box and quiz box must be hidden, and the result box must be shown. (.remove and .add)
  - A customized text is created with the userScore and the amount of questions. The text is customized based on how many questions they got right. This is added dynamically to index.html to be displayed
 
  ```js
  // display for result box based on user performance
  function showResult() {
    info_box.classList.remove("activeInfo"); //hide info box
    quiz_box.classList.remove("activeQuiz"); //hide quiz box
    result_box.classList.add("activeResult"); //show result box
    const scoreText = result_box.querySelector(".score_text");
    if (userScore > 3) {
      // if user scored more than 3
      //create a new span tag and pass the user score number and total question number
      let scoreTag =
        "<span>and congrats! , You got <p>" +
        userScore +
        "</p> out of <p>" +
        questions.length +
        "</p></span>";
      scoreText.innerHTML = scoreTag; //add new span tag inside score_Text
    } else if (userScore > 1) {
      // if user scored more than 1
      let scoreTag =
        "<span>and nice , You got <p>" +
        userScore +
        "</p> out of <p>" +
        questions.length +
        "</p></span>";
      scoreText.innerHTML = scoreTag;
    } else {
      // if user scored less than 1
      let scoreTag =
        "<span>and sorry , You got only <p>" +
        userScore +
        "</p> out of <p>" +
        questions.length +
        "</p></span>";
      scoreText.innerHTML = scoreTag;
    }
  }
  ```

- The remaining functions startTimer(), timer(), startTimerLine(), and queCounter() all deal with the functionality of the respective elements
  - startTime() sets an interval of 1 second to time out the timer and then calls timer()
  - timer() displays the time, decrease the time by 1 each time its called, styles the time to add a 0 in front for consistency, and if the time runs out then the correct answer should be shown and the user should be allowed to move to the next question
  - startTimeLine() increases the pixels of the time_line div to make it appear as if it is a progress bar
  - queCounter() lets the user know which question they are on

  ```js
  // control the timer and actions associated to it
  function startTimer(time) {
    counter = setInterval(timer, 1000);
    function timer() {
      timeCount.textContent = time; //change the value of timeCount with time value
      time--; //decrement the time value
      if (time < 9) {
        //if timer is less than 9
        let addZero = timeCount.textContent;
        timeCount.textContent = "0" + addZero; //add a 0 before time value
      }
      if (time < 0) {
        //if timer is less than 0
        clearInterval(counter); //clear counter
        timeText.textContent = "Time Off"; //change the time text to time off
        const allOptions = option_list.children.length; //get all option items
        let correcAns = questions[que_count].answer; //get correct answer from array
        for (i = 0; i < allOptions; i++) {
          if (option_list.children[i].textContent == correcAns) {
            //if there is an option which is matched to an array answer
            option_list.children[i].setAttribute("class", "option correct"); //add green color to matched option
            option_list.children[i].insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to matched option
            console.log("Time Off: Auto selected correct answer.");
          }
        }
        for (i = 0; i < allOptions; i++) {
          option_list.children[i].classList.add("disabled"); //once user select an option then disabled all options
        }
        next_btn.classList.add("show"); //show the next button if user selected any option
      }
    }
  }
  
  // Shows a progress bar mirroring timer value left
  function startTimerLine(time) {
    counterLine = setInterval(timer, 29);
    function timer() {
      time += 1; //upgrading time value with 1
      time_line.style.width = time + "px"; //increasing width of time_line with px by time value
      if (time > 549) {
        //if time value is greater than 549
        clearInterval(counterLine); //clear counterLine
      }
    }
  }
  
  function queCounter(index) {
    //creating a new span tag and passing the question number and total question
    let totalQueCounTag =
      "<span><p>" +
      index +
      "</p> of <p>" +
      questions.length +
      "</p> Questions</span>";
    bottom_ques_counter.innerHTML = totalQueCounTag; //adding new span tag inside bottom_ques_counter
  }
  ```
