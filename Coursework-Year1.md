---
layout: coursework-highlights
title: "Coursework - Year 1"
permalink: /coursework1
---

<h1 style="text-align:center;margin-top:20px;">Coursework - Year 1</h1>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1021">Programming I</a></h2>
</div>
{::options parse_block_html="true" /}
<div class="row">
<hr>
<div class="row">
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/TaxChartCoursework.PNG" style="max-width:90%" max-height="350">
</div>
<div class="col-xs-6">
<h3>Assignment 1 - Tax Chart and Calculator</h3>
<p>The first coursework we were tasked with in Java involved creating a Tax Calculator which then displayed a bar chart showing income and amount to pay.</p>
</div>
</div>
<div class="row">
<details><summary markdown="span" style="text-align:right">Show me the code!</summary>
	
```java
/**
* Prints table of data with gross,tax paid and net values
* 
* @param gross gross income before tax
*/
public void printTable(int[]gross){
    int[] net;
    net = new int[gross.length];
	
//for loop prints each of gross income, net income , and tax paid on the gross income.
    for(int row = 0;row<=(gross.length -1);row++){
        net[row] = ((gross[row])-(TaxCalculator.taxPayable(gross[row])));
			
//ensures the net income is never less then 0
	if (net[row]<0){
	    net[row]=0;
	}
		
//prints out the values to the console
	System.out.println("Gross:" +gross[row] + " Tax-Payable:" + (TaxCalculator.taxPayable(gross[row])) + " Net:" + net[row]);
    }
}
```

</details>
<br/>
</div>
</div>
{::options parse_block_html="false" /}

<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="/img/coursework/HotelCoursework2.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 2 - Hotel booking system</h3>
    <p>The second coursework we were tasked with in Java involved creating a hotel booking system using OOP; this did not require a GUI.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1022">Programming II</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="/img/coursework/BrowserCoursework.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Web Browser</h3>
    <p>The coursework we were tasked with in Java in the second semester was to create a browser that would display webpages and required a GUI, we were told to use Swing for this.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1023">The Software Engineering Professional</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Programming Presentation</h3>
    <p>Research and present information on a programming language of our choosing, including a written report of the information.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="/img/coursework/EthicsCoursework.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 2 - Ethics in Software Engineering</h3>
    <p>This coursework involved choosing a computing disaster to discuss, mainly about the ethics behind the disaster, what happened, how it happened and what could have been done to prevent it.</p>
    <p>The topic I decided to choose was 000webhost and their database breach of plain text information; over 13.5 million users details and passwords.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="/img/coursework/usabilityCoursework.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 3 - Usability Analysis (Sprint)</h3>
    <p>Using Nielsen's 10 Usablity Heuristics where appropriate we were tasked with testing out the universities blackboard system.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="/img/coursework/litCoursework.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 4 - Literature Review</h3>
    <p>Using Google Scholar we were to find 3 literature pieces from trusted and reliable sources based on a subject in computing science, I opted to choose AI and Machine Learning; this wasn't a suggested topic however I find this subject interesting.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="/img/coursework/testingCoursework.PNG" style="max-width:90%" max-height="350"><br><br>
    <img class="enlarge" src="/img/coursework/testingCoursework2.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 5 - Debugging PreWritten Code</h3>
    <p>The code we were given had been written specifically for the purpose of testing and debugging, it had issues injected purposefully.</p>
  </div>
</div>

{::options parse_block_html="true" /}
<div class="row">
<hr>
<h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1024">Computer Architecture</a></h2>
</div>
<div class="row">
<hr>
<div class="row">
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/liftCoursework.PNG" style="max-width:90%" max-height="350"><br><br>
</div>
<div class="col-xs-6">
<h3>Assignment 1 - Lift Simulator</h3>
<p>Using assembly language, we were tasked with controlling a lift.</p>
<p>We had a very limited amount of memory to work with.</p>
</div>
</div>
<div class="row">
<details><summary markdown="span" style="text-align:right">Show me the code!</summary>
			
```asm
; ----- LIFT --------------------------
	JMP	Start		; Skip the db's
	db	A8		; Code for Timer Interupt stored in A8
	db	00		; Keyboard Interupt not used
	db 	AA		; Keypad Interupt Code stored in AA

Start:
	STI			; Set the Interupt
	MOV	CL, 4F	;o	; Set Register CL to char o
	MOV	DL, 54	;t	; Set Register DL to char t
	OUT	08		; Display Key Pad
	OUT	06		; Display lift window
	JMP	WaitUpButton	; Jump to check for button pressed

;------------ Display up and start up motor ------------
UP:
	
	IN	06		; Read Lift Status
	AND	AL, 04		; Isolate Near top check bit
	JNZ	WaitDownButton	; If near top go back to wait for buttons
				; else continue
	MOV	BL, 55		; Display "UP"
	MOV	[C0], BL	; |
	MOV	BL, 50		; |
	MOV	[C1], BL	; v
	MOV	BL, 0		; Clear Excess Letters using null
	MOV	[C2], BL	; |
	MOV	[C3], BL	; |	
	MOV	[C4], BL	; |
	MOV	[C5], BL	; v

	OR	AL, 01		; Set UP motor bit
	OUT	06		; Turn on UP motor
;------------ Start checking if near top -----------------
CheckU:	   
	AND	AL, 4		; Isolate near top check bit
	IN	06		; Read lift status
	JZ	CheckU		; If reached top continue else keep checking
	AND	AL, FE		; Turn off up motor
	OUT	06		; Send command to lift - turns off lift motor
	MOV	[C0], DL	; T
	MOV	[C1], CL	; O
	MOV	BL, 50		; set bl to p
	MOV	[C2], BL	; P
	
;------------- Check if any buttons have been pressed -----------
WaitDownButton:
	IN	06		; Read lift status
	AND	AL, 10		; Isolate down button
	JNZ	Down		; Jump to down if pressed else continue
	JMP	WaitDownButton  ; Keep checking
WaitUpButton:
	IN	06		; Read Status again
	AND	AL, 20		; Isolate up button
	JNZ	UP		; Jump to up if Pressed else continue
	JMP	WaitUpButton	; Keep checking till button pressed
;------------ Display Down and start down motor ----------------
Down:
	
	IN	06		; Read lift status
	AND	AL, 08		; Isolate near bottom check bit
	JNZ	WaitUpButton	; If near bottom, go back and wait for buttons
				; Else continue
	MOV	BL, 44		; BL set to D
	MOV	[C0], BL	; D
	MOV	[C1], CL	; O
	MOV	BL, 57		; BL set to W
	MOV	[C2], BL	; W
	MOV	BL, 4E		; BL set to N
	MOV	[C3], BL	; N

	OR	AL, 02		; Set Down motor bit
	OUT	06		; Turn on Down motor
;------------ Start checking if lift is at bottom --------------
CheckD:
	AND	AL, 08		; Isolate near bottom check bit
	IN	06		; Read lift status
	JZ	CheckD		; If near bottom continue else keep checking
	AND	AL, FD		; Turn off down motor
	OUT	06		; Send command to lift - turns off lift motor

	MOV	BL, 42		; Set BL to B
	MOV	[C0], BL	; B
	MOV	[C2], DL	; T miss O as this would already be there from dOwn
	MOV	[C3], DL	; T
	MOV	[C4], CL	; O
	MOV	BL, 4D		; Set Bl to M
	MOV	[C5], BL	; M
	JMP	WaitUpButton	; Go back to wait for buttons again	
	
ORG A8
	iret			; Do nothing, return
ORG AA
	POP 	AL		; POP to prevent code overwriting, done first to prevent
				; quick presses of button affecting code

	IN	08		; Port for the peripheral keypad
	CMP	AL,0D		; Check if enter was pressed on pad
	JZ 	DOWN		; If it was jump to Down
	IN	06		; Read Lift Status
	AND	AL, 1		; Check if up motor was on
	JNZ	CheckU		; If it was check if near top to prevent crash		
	JMP	CheckD		; Else check if near bottom to prevent crash

END
; --------------------------------------------------------------

```

</details>
</div>
</div>

{::options parse_block_html="false" /}

<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1025">Mathematics for Computer Science</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="/img/coursework/Maths.jpg" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Fundamental Maths</h3>
    <p>Some of the topics we covered for this coursework included.</p>
	  <ul>
		  <li>Basics of Set Theory</li>
		  <li>Numbers and their representations</li>
		  <li>Real Valued Functions</li>
		  <li>Vectors and Matrices</li>
		  <li>Combinatorics and Basics of Counting</li>
	  </ul>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 2 - Discrete Maths</h3>
    <p>Some of the topics we covered for this coursework included.</p>
	  <ul>
		  <li>Relations and Functions</li>
		  <li>Proof Techniques</li>
		  <li>Recursive Function Definitions and Proof by Induction</li>
		  <li>Graph Theory</li>
	  </ul>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1026">Website Design and Construction</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="/img/coursework/webCoursework.PNG" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Copy a Website using image</h3>
    <p>Using just an image and some pre-written text, we were tasked with marking up the text so that the page had the same underlying 
structure as a website and then using CSS to make it look like the final result.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
	  <img class="enlarge" src="/img/coursework/TutorialWebsiteCSS.png" style="max-width:90%" max-height="350"><br><br>
	  <img class="enlarge" src="/img/coursework/TutorialWebsite.png" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
	  <h3>Assignment 2 - Develop Tutorial Website</h3>
	  <p>Voice clips and slides from the course are laid out in easy to use sections separating the different topics of the course.</p>
	  <p>The user can utilise what they have learnt from the website and gain feedback immediately by using the live HTML, CSS, Javascript testing area, this function was adapted from some code I found online, the layout changes depending on what section of the tutorial website the user is on (shown in the pictures).</p>
	  <p>This testing area can expand to accommodate more lines as needed.</p>
	  <img class="enlarge" src="/img/coursework/TutorialWebsiteExpand.png" style="max-width:90%" max-height="350">
	  
  </div>
</div>
