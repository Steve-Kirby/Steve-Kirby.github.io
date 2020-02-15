---
layout: page
title: "Coursework - Year 1"
permalink: /coursework1
---
<h1 style="text-align:center;margin-top:20px;">Coursework - Year 1</h1>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1021">Programming I</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="TaxChartCoursework.PNG" style="max-width:90%" height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Tax Chart and Calculator</h3>
    <p>The First coursework we were tasked with in Java involved creating a Tax Calculator which then displayed a bar chart showing income and amount to pay.</p>
	  {::options parse_block_html="true" /}
	  <details><summary markdown="span">Let's see some code!</summary>
		  ```java
		  /**
 * @Author Steven Kirby
 * @Date 13/10/2016
 * @Company The Beurocratic Office Generating Other Financial Fiddles(BOGOFF)
 * @ClassPurpose Calculates tax paid based on income
 */
public class TaxCalculator {

	public static void main(String[] args) {
		
	}
	
	/**
	 * Calculates how much tax to pay given an income
	 * 
	 * @param income gross income before tax
	 * @return tax to be paid(rounded)
	 */
	public static int taxPayable(int income){
		double payable = 0;
		//declaring all the values for each tax band and the thresholds for each one.
		double taxFree = 0.0,taxBand1 = 0.1,taxBand2 = 0.2,taxBand3 = 0.4,taxBand4 = 0.6,taxBand5 = 1.2;
		int threshold1 = 100, threshold2 = 150, threshold3 = 200, threshold4 = 300, threshold5 = 400;
		//this while loop will continue until income has reached 0, the way I have chosen to work out the tax paid is using
		//the idea that starting at the income value, and decrementing by 1 whilst adding to the tax payable value
		//until the income has reached 0.
		while(income>0){
			//it seems most logical to start at the higher threshold as when each for loop finishes it can move straight
			//on to the next for loop.
			for(income=income;(income>threshold5)&&(income>threshold5);income--){
				payable += taxBand5;
			}
			for(income=income;(income<=threshold5)&&(income>threshold4);income--){
				payable += taxBand4;
			}
			for(income=income;(income<=threshold4)&&(income>threshold3);income--){
				payable += taxBand3;
			}
			for(income=income;(income<=threshold3)&&(income>threshold2);income--){
				payable += taxBand2;
			}	
			for(income=income;(income<=threshold2)&&(income>threshold1);income--){
				payable += taxBand1;
			}	
			for(income=income;(income<=threshold1)&&(income>0);income--){
				//this isn't necessary but for completeness I have included it.
				payable += taxFree;
			}
		}
		//rounds the value of tax to be paid to the nearest pound.
		
		return(int)(Math.round(payable));
	}
	
	/**
	 * Works out how much net income will be left after tax
	 * 
	 * @param taxPaid takes the amount of tax paid
	 * @param income takes the income before tax has been paid
	 * @return returns net income
	 */
	public static int incomeRemaining(int income){
		//calculates the income remaining after tax has been deducted.
		int remainingIncome = income - taxPayable(income);
			//prevents net income to be less then 0
			if (remainingIncome < 0){
			remainingIncome = 0;		
			}
		return remainingIncome;
	}
	
}

		  ```
Of course, it has to be Hello World, right?
</details>
<br/>

{::options parse_block_html="false" /}
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="HotelCoursework2.PNG" style="max-width:90%" height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 2 - Hotel booking system</h3>
    <p>The Second coursework we were tasked with in Java involved creating a Hotel using OOP to allow a booking system, this did not require a GUI.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1022">Programming II</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="BrowserCoursework.PNG" style="max-width:90%" height="350">
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
    <img src="" style="max-width:90%" height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Programming Presentation</h3>
    <p>Research and present information on a programming language of our choice, including a written report of the information also</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="EthicsCoursework.PNG" style="max-width:90%" height="350">
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
    <img src="usabilityCoursework.PNG" style="max-width:90%" height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 3 - Usability Analysis(Sprint)</h3>
    <p>Using Nielsen's 10 Usablity Heuristics where appropriate we were tasked with testing out the universities blackboard system</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="litCoursework.PNG" style="max-width:90%" height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 4 - Literature Review</h3>
    <p>Using Google Scholar we were to find 3 literature pieces from trusted and reliable sources based on a subject in computing science, I opted to choose AI and Machine Learning, this wasnt a suggested topic however I find this subject interesting.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="testingCoursework.PNG" style="max-width:90%" height="350"><br><br>
    <img src="testingCoursework2.PNG" style="max-width:90%" height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 5 - Debugging PreWritten Code</h3>
    <p>The Code we were given had been written specifically for the purpose of testing and debugging with injected issues.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1024">Computer Architecture</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="liftCoursework.PNG" style="max-width:90%" height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Lift Simulator</h3>
    <p>Using assembly language, we were tasked with controlling a lift.</p>
    <p>We had a very limited amount of memory to work with.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1025">Mathematics for Computer Science</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="" style="max-width:90%" height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Maths</h3>
    <p>Generic maths</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC1026">Website Design and Construction</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="webCoursework.PNG" style="max-width:90%" height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - Copy a Website using image</h3>
    <p>Using just an image and some pre written text we were tasked with marking up the text so that the page had the same underlying 
structure as a website and then using css to make it look like the final result</p>
  </div>
</div>
