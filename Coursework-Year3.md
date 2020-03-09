---
layout: coursework-highlights
title: "Coursework - Year 3"
permalink: /coursework3
---

<h1 style="text-align:center;margin-top:20px;">Coursework - Year 3</h1>
<div class="row">

<h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3095">Dissertation - Generation of Islands and Simulating Climate Change using OpenGL</a></h2>
<hr>
</div>

<div class="row">
	<div class="col-xs-6">
		<img class="enlarge" src="/img/coursework/DissertationPoster.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-xs-6">
		<h3>Poster</h3>
		<p>For my 3rd year dissertation I wanted to explore graphics within programming as I had never quite grasped how to implement them.</p>
		<p>Tackling this topic enabled me to explore the belly of the beast, I utilised a codebase provided to us during the graphics module I was doing that year.</p>
		<p>This provided a framework in which to easily set up a window using OpenGL as well as a few other features, however understanding the codebase I had never used before made this slightly more difficult; albeit increasing my confidence in using another programmers complex code.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img class="enlarge" src="/img/coursework/DissGantt.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-xs-6">
		<h3>Planning - Gantt Chart</h3>
		<p>In order to organise my dissertation I used a Gantt chart which changed over time as needed.</p>
		<p>I enjoy games with wide open worlds that can be explored, and naturally wanted to generate random islands to replicate this, this changed after discussion with my tutors.</p>
		<p> The biggest change was to incorperate climate change and rising sea levels, which are returning to the forefront of issues we face once again.</p>
		<p>I made the decision to use heightmaps of the UK rather then randomly generated islands, in hopes of making people aware that these are real issues, not just an interesting graphics demo.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-xs-6">
		<img class="enlarge" src="/img/coursework/DissErosion.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-xs-6">
		<h3>The Result</h3>
		<p>This project was a challenging experience for me, however I managed to achieve what I had set out to do, albeit not as pretty as I would have liked.</p>
		<p>The image shows the erosion and the inundation of water upon the UK after the sea level had risen.</p>
	</div>

</div>

<div class="row">
	<hr>
	<div class="col-xs-6">
		<img class="enlarge" src="/img/coursework/DissertationGraph.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-xs-6">
		<h3>Data Analysis Graph</h3>
		<p>Another aspect of this dissertation I enjoyed was the data analysis of testing performance of the simulation with different detail or tesselation levels, amount of textures being rendered etc.</p>
		<p>This is just one example of the graphs I produced in Excel, this particular graph using the fps, x and y position of the 'camera' to see how much the render times/fps were effected by how much of the model was showing on the screen.</p>
	</div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3221">Programming for Games</a></h2>
</div>
{::options parse_block_html="true" /}
<div class="row">
<hr>
<div class="row">
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/QuadTest.png" style="max-width:90%;max-height=350px">
<img class="enlarge" src="/img/coursework/PolyTest.png" style="max-width:90%;max-height=350px">
</div>
<div class="col-xs-6">
<h3>Assignment 1 - Polynomials and Quadratics</h3>
<p>For this assignment we were to display the co-efficient of a power of x, compute values of a polynomials given a value of x.</p>
<p>Overloading of +, * and - operators as well as IO operators >> and <<. Implemented other operators such as == != += -= *=, Constructors, Destructors, Assignment and Copy constructor; to allow manipulation of polynomials.</p>
<p>STL vector use was forbidden, requiring data to be stored on the heap using an array.</p>
</div>
</div>
<div class="row">
<details><summary markdown="span" style="text-align:right">Show me the code!</summary>
	
```cpp
/*
Polynomial.cpp
Author: Steven Kirby
Student Number: 160275779
Date: 11/7/2018
*/

#include "Polynomial.h"

//class variables
int arraySize;
int* polyArray = nullptr;

//constructors
Polynomial::Polynomial(string poly)
{
	//get the array size by using the highest power and adding 1 for power(0) to make a array on the heap of the correct size
	arraySize = FindHighestPower(poly) + 1;
	polyArray = new int[arraySize];

	//zero the array for missing powers ( short form polynomials )
	FillArrayWithZero(*this);

	//add the coefficients in the right powers in the array
	FindCoefficients(poly);

}

Polynomial::Polynomial()
{

}

//copy constructor
Polynomial::Polynomial(const Polynomial &copy)
{
	arraySize = copy.arraySize;
	polyArray = new int[copy.arraySize];
	for (int i = 0; i < copy.arraySize; i++) {
		polyArray[i] = copy.polyArray[i];
	}
}

//destructor
Polynomial::~Polynomial()
{
	//delete array and null the pointer
	delete [] polyArray; 
	polyArray = nullptr;
}

//method to find the highest power of a polynomial(assuming its ordered) to get a correct size for an array
int Polynomial::FindHighestPower(string poly)
{
	istringstream iss(poly);
	int coeff = 0;
	char x;
	char pow;
	int highestPower = 0;

	//parts of the string stream are fed into the variables
	iss >> coeff >> x >> pow >> highestPower;

	//when the string reads like 5x + 2, + gets taken into pow rather then ^ 
	if (pow == '+') {
		return 1;
	}
	return highestPower;
}

//method to fill the array with zeros
void Polynomial::FillArrayWithZero(Polynomial &poly) {

	for (int i = 0; i < poly.arraySize; i++)
	{
		poly.polyArray[i] = 0;
	}
}

//method to find the coeffecients of a polynomial, using the highest power available out of the string to only fill the correct array values
void Polynomial::FindCoefficients(string poly)
{
	string delim = " + ";


	size_t pos = 0;
	int i;
	do {
		//as with quadratic 
		pos = poly.find(delim);
		char *cstr = &poly[0];

		//this finds the correct place to put the coefficient in the array
		i = FindHighestPower(poly);

		//as with quadratic
		polyArray[i] = atoi(cstr);
		poly.erase(0, pos + delim.length());

	} while (pos != string::npos);



}

//method returns coefficient of specified power
int Polynomial::FindCoefficientOfPower(int power)
{
	return polyArray[power];
}

//method to work out the value of a polynomial given an x value
double Polynomial::ValueOfX(double x)
{
	double z = 0.0f;

	//loops through the array and uses math pow function to calculate this (coefficent * x^i)
	for (int i = 0; i < arraySize; i++) {
		z += polyArray[i] * pow(x, i);
	}
	return z;
}


Polynomial Polynomial::operator+(Polynomial polyRHS)
{
	//same as quadratic except allows for different size arrays with different powers
	Polynomial addedPolys;
	addedPolys = *this;
	
	//ternary operator which chooses the biggest array as this is what will be able to accomodate any sums with + or - 
	int newarraysize = (arraySize > polyRHS.arraySize) ? arraySize : polyRHS.arraySize;

	addedPolys.arraySize = newarraysize;
	addedPolys.polyArray = new int[newarraysize];
	FillArrayWithZero(addedPolys);

	for (int i = 0; i < arraySize; i++) {
		addedPolys.polyArray[i] += this->polyArray[i];
	}
	for (int i = 0; i < polyRHS.arraySize; i++) {
		addedPolys.polyArray[i] += polyRHS.polyArray[i];
	}

	return Polynomial(addedPolys);
}

//same as + operator but - operator
Polynomial Polynomial::operator-(Polynomial polyRHS)
{
	Polynomial subtractedPolys;
	subtractedPolys = *this;
	int newarraysize = (arraySize > polyRHS.arraySize) ? arraySize : polyRHS.arraySize;
	subtractedPolys.arraySize = newarraysize;
	subtractedPolys.polyArray = new int[newarraysize];
	FillArrayWithZero(subtractedPolys);

	//add the left hand side then take away the right hand side
	for (int i = 0; i < arraySize; i++) {
		subtractedPolys.polyArray[i] += this->polyArray[i];
	}
	for (int i = polyRHS.arraySize-1; i >= 0; i--) {
		subtractedPolys.polyArray[i] -= polyRHS.polyArray[i];

		//required to remove any powers that are lost ( see == overload )
		if (subtractedPolys.polyArray[i] == 0 && i == (subtractedPolys.arraySize -1)) {
			subtractedPolys.arraySize--;
		}
	}
	return Polynomial(subtractedPolys);
}

bool operator==(const Polynomial & polyLHS, const Polynomial & polyRHS)
{
	//if the array sizes are different they cant be equal(due to removal of 0 coefficient powers above highest power in subtraction method)
	if (polyLHS.arraySize != polyRHS.arraySize) {
		return false;
	}

	//check each power as with quadratic, if one is not the same return false immediately
	for (int i = 0; i < polyLHS.arraySize; i++)
	{
		if (polyLHS.polyArray[i] == polyRHS.polyArray[i]) {
			continue;
		}
		else {
			return false;
		}
	}
	return true;
}

//reverse of ==
bool operator!=(const Polynomial& polyLHS, const Polynomial& polyRHS)
{

	if (polyLHS.arraySize != polyRHS.arraySize) {
		return true;
	}

	for (int i = 0; i < polyLHS.arraySize; i++)
	{
		if (polyLHS.polyArray[i] == polyRHS.polyArray[i]) {
			continue;
		}
		else {
			return true;
		}
	}
	return false;
}


//calls the + operator
Polynomial& Polynomial::operator+=(Polynomial & polyRHS)
{
	*this = *this + polyRHS;

	return *this;
}

//calls the - operator
Polynomial& Polynomial::operator-=(Polynomial & polyRHS)
{
	*this = *this - polyRHS;

	return *this;
}


ostream & operator<<(ostream & out, const Polynomial &poly)
{
	//start from the highest power
	int i = poly.arraySize - 1;

	//loop through each power adding the string to the out stream
	for (i; i > 0; i--)
	{
		out << "Power(" << i << ") Coefficient: " << poly.polyArray[i] << ", ";
	}
	//if last coefficient dont print a comma
	out << "Power(" << i << ") Coefficient: " << poly.polyArray[i];
	return out;
}

istream &operator>>(istream &in, Polynomial &poly)
{
	//take the whole string in and save in polyString
	string polyString;
	getline(in, polyString);

	//reassign the values of arraySize based on newly input string
	poly.arraySize = poly.FindHighestPower(polyString) + 1;

	//zero array again as new data locations could be being accessed
	poly.FillArrayWithZero(poly);
	poly.FindCoefficients(polyString);

	return in;
}

Polynomial Polynomial::operator=(Polynomial polyRHS)
{
	//assignment of data
	arraySize = polyRHS.arraySize;
	polyArray = new int[polyRHS.arraySize];
	for (int i = 0; i < polyRHS.arraySize; i++) {
		polyArray[i] = polyRHS.polyArray[i];
	}
	return *this;
}

Polynomial Polynomial::operator*(Polynomial polyRHS)
{

	//new polynomial to store the multiplied polynomial values
	Polynomial multipliedPoly;

	//always end up with this size
	int newarraysize = arraySize + polyRHS.arraySize - 1;
	multipliedPoly.arraySize = newarraysize;
	multipliedPoly.polyArray = new int[newarraysize];

	FillArrayWithZero(multipliedPoly);

	//loop through each array of coefficients multiplying one with each other
	for (int i = 0; i < arraySize; i++) {
		for (int j = 0; j < polyRHS.arraySize; j++) {
			// += allows combining of like terms without an additional method 
			multipliedPoly.polyArray[i + j] += polyRHS.polyArray[j] * polyArray[i];
		}
	}


	return Polynomial(multipliedPoly);
}

// calls the * operator
Polynomial & Polynomial::operator*=(Polynomial & polyRHS)
{

	*this = *this * polyRHS;

	return *this;
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
    <img class="enlarge" src="/img/coursework/SpaceChess.png" style="max-width:90%;max-height=350px">
  </div>
  <div class="col-xs-6">
	  <h3>Assignment 2 - Space Chess</h3>
	  <p>The task for this assignment was to create a simulation of a Rook , Bishop, and Queen on a board, these pieces could move any distance by teleportation within the board including non-integer values (unlike chess).</p>
	  <p>I learnt a lot about polymorphism and inheritance as well as collision detection of simple shapes within a 2d space.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3222">Gaming Simulations</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - </h3>
    <p style="color:red">Work in progress.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3223">Graphics for Games</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - </h3>
    <p style="color:red">Work in progress.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 2 -</h3>
	 <p style="color:red">Work in progress.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3224">Computer Games Development</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - </h3>
	<p style="color:red">Work in progress.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3122">Mobile Computer Systems Development</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img src="" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - </h3>
    <p style="color:red">Work in progress.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3123">Web Technologies</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - </h3>
    <p style="color:red">Work in progress.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3124">System and Network Security</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - </h3>
    <p style="color:red">Work in progress.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3123">Web Construction and Management(Server-Side)</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-xs-6">
    <img class="enlarge" src="" style="max-width:90%" max-height="350"><br><br>
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 - </h3>
    <p style="color:red">Work in progress.</p>
  </div>
</div>
