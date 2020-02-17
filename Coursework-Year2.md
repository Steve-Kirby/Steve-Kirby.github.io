---
layout: coursework2
title: "Coursework - Year 2"
permalink: /coursework2
---

<h1 style="text-align:center;margin-top:20px;">Coursework - Year 2</h1>
<div class="row bodydark">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2021">Software Engineering</a></h2>
</div>
{::options parse_block_html="true" /}
<div class="row bodydark">
<hr>
<div class="row bodydark">
<div class="col-xs-6">
<img class="enlarge" src="TaxChartCoursework.PNG" style="max-width:90%" max-height="350">
</div>
<div class="col-xs-6 bodydark">
<h3>Assignment 1 - Tax Chart and Calculator</h3>
<p>The First coursework we were tasked with in Java involved creating a Tax Calculator which then displayed a bar chart showing income and amount to pay.</p>
</div>
</div>
<div class="row bodydark">
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
    <img class="enlarge" src="HotelCoursework2.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 2 - Hotel booking system</h3>
    <p>The Second coursework we were tasked with in Java involved creating a Hotel using OOP to allow a booking system, this did not require a GUI.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2022">Software Engineering Team Project</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="BrowserCoursework.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Web Browser</h3>
    <p>The coursework we were tasked with in Java in the second semester was to create a browser that would display webpages and required a GUI, we were told to use Swing for this.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2023">Algorithm Design and Analysis</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Programming Presentation</h3>
    <p>Research and present information on a programming language of our choice, including a written report of the information also</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="EthicsCoursework.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 2 - Ethics in Software Engineering</h3>
    <p>This coursework involved choosing a computing disaster to discuss about, mainly the ethics behind the disaster and what happend,how it happened and what could of been done to prevent this.</p>
    <p>The topic I decided to choose was 000webhost and their database breach of plain text information of over 13.5 million users details and passwords.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="usabilityCoursework.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 3 - Usability Analysis(Sprint)</h3>
    <p>Using Nielsen's 10 Usablity Heuristics where appropriate we were tasked with testing out the universities blackboard system</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="litCoursework.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 4 - Literature Review</h3>
    <p>Using Google Scholar we were to find 3 literature pieces from trusted and reliable sources based on a subject in computing science, I opted to choose AI and Machine Learning, this wasnt a suggested topic however I find this subject interesting.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="testingCoursework.PNG" style="max-width:90%" max-height="350"><br><br>
    <img class="enlarge" src="testingCoursework2.PNG" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 5 - Debugging PreWritten Code</h3>
    <p>The Code we were given had been written specifically for the purpose of testing and debugging with injected issues.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2024">Database Technology</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="liftCoursework.PNG" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Lift Simulator</h3>
    <p>Using assembly language, we were tasked with controlling a lift.</p>
    <p>We had a very limited amount of memory to work with.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2025">Operating Systems</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Maths</h3>
    <p>Generic maths</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2026">Computer Networks</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="webCoursework.PNG" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Copy a Website using image</h3>
    <p>Using just an image and some pre written text we were tasked with marking up the text so that the page had the same underlying 
structure as a website and then using css to make it look like the final result</p>
  </div>
</div>
