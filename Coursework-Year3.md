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
	<div class="col-sm-6">
		<img class="enlarge" src="/img/coursework/DissertationPoster.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Poster</h3>
		<p>For my 3rd year dissertation I wanted to explore graphics within programming as I had never quite grasped how to implement them.</p>
		<p>Tackling this topic enabled me to explore the belly of the beast, I utilised a codebase provided to us during the graphics module I was doing that year.</p>
		<p>This provided a framework in which to easily set up a window using OpenGL as well as a few other features, however understanding the codebase I had never used before made this slightly more difficult; albeit increasing my confidence in using another programmers complex code.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/coursework/DissGantt.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Planning - Gantt Chart</h3>
		<p>In order to organise my dissertation I used a Gantt chart which changed over time as needed.</p>
		<p>I enjoy games with wide open worlds that can be explored, and naturally wanted to generate random islands to replicate this, this changed after discussion with my tutors.</p>
		<p> The biggest change was to incorperate climate change and rising sea levels, which are returning to the forefront of issues we face once again.</p>
		<p>I made the decision to use heightmaps of the UK rather then randomly generated islands, in hopes of making people aware that these are real issues, not just an interesting graphics demo.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/coursework/DissErosion.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>The Result</h3>
		<p>This project was a challenging experience for me, however I managed to achieve what I had set out to do, albeit not as pretty as I would have liked.</p>
		<p>The image shows the erosion and the inundation of water upon the UK after the sea level had risen.</p>
	</div>

</div>

<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/coursework/DissertationGraph.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
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
<div class="col-sm-6">
<img class="enlarge" src="/img/coursework/QuadTest.png" style="max-width:90%;max-height=350px">
<img class="enlarge" src="/img/coursework/PolyTest.png" style="max-width:90%;max-height=350px">
</div>
<div class="col-sm-6">
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
  <div class="col-sm-6">
    <img class="enlarge" src="/img/coursework/SpaceChess.png" style="max-width:90%;max-height=350px">
  </div>
  <div class="col-sm-6">
	  <h3>Assignment 2 - Space Chess</h3>
	  <p>The task for this assignment was to create a simulation of a Rook , Bishop, and Queen on a board, these pieces could move any distance by teleportation within the board including non-integer values (unlike chess).</p>
	  <p>I learnt a lot about polymorphism and inheritance as well as collision detection of simple shapes within a 2d space.</p>
  </div>
</div>
{::options parse_block_html="true" /}
<div class="row">
<details><summary markdown="span" style="text-align:right">Show me the code! (Game.cpp)</summary>

```cpp

/**
Space Chess, Game.cpp
Purpose: Test Space Chess

@author Steven Kirby
@date 07/12/18
*/

#include "Piece.h"
#include "Queen.h"
#include "Bishop.h"
#include "Rook.h"
#include <time.h>
#include <iostream>
#include <vector>
#include <string>


using namespace std;

int main() {

	const int MAX_TURNS = 1000;
	const int PIECE_QUANTITY = 5;

	//counter for how many turns has been had
	int turns = 0;

	//total scores{Rook, Bishop, Queen}
	int piecesScore[] = {0,0,0};

	vector<Piece*> pieces;

	//random seed
	srand(time(NULL));
	
	// For loop creates PIECE_QUANTITY of each piece and places the pointer to the piece in the vector pieces 
	for (int i = 0; i < PIECE_QUANTITY; i++) {
		Piece* p1 = new Rook;
		Piece* p2 = new Queen;
		Piece* p3 = new Bishop;

		pieces.emplace_back(p1);
		pieces.emplace_back(p2);
		pieces.emplace_back(p3);
	}

	// Runs whilst there is more then 1 piece and we havent exceeded MAX_TURNS
	while (pieces.size() > 1 && turns < MAX_TURNS) {

		// Move each piece in turn
		for (int i = 0; i < pieces.size(); i++) {
			pieces[i]->Move();

			// Check if this piece has collided with all other pieces, if it has add to total score for this piece type, and call deconstructor for other piece that was "captured" and remove from vector
			for (int j = 0; j < pieces.size(); j++) {
				if (pieces[i]->CheckCollision(pieces[j]) == true) {
					pieces[i]->AddScore(piecesScore);
					pieces[j]->~Piece();
					pieces.erase(pieces.begin() + j);

					// Move onto next piece as shouldnt capture more then 1 piece each turn
					break;
				}
			}	
			
		}
		turns++;
	}


	// Print totals information
	cout << endl << "Turns taken by each piece:" << turns << endl;
	cout << "The Rook Pieces took " << piecesScore[0] << " in Total." << endl;
	cout << "The Bishop Pieces took " << piecesScore[1] << " in Total." << endl;
	cout << "The Queen Pieces took " << piecesScore[2] << " in Total." << endl;

	// Stop program from ending automatically, and allow user to exit
	cout << endl << "Press enter to exit: ";
	cin.ignore();
}


```
	
</details>
<details><summary markdown="span" style="text-align:right">Show me the code! (Piece.cpp)</summary>

```cpp

/**
Space Chess, Piece.cpp
Purpose: Abstract Chess Piece type

@author Steven Kirby
@date 07/12/18
*/

#include <string>
#include "Piece.h"
#include <iostream>
#include <algorithm>



//Limit the shapes
enum class shape { circle, square };

//Shorten main body of code when printing information using a info function with limited options
enum class info { p_position, p_symbol, e_collision, p_score };


/**
	Piece constructor, assigns shape based on symbol it recieves and assigns a random x,y position within the grid
	@param sym takes in a representative symbol of a piece type
*/
Piece::Piece(char sym)
{

	this->symbol = sym;
	
	//if its a rook, its a square shape, else its a circle shape
	this->shape = (this->symbol == 'R' ? square : circle);

	this->xpos = (float(rand()) / (float(RAND_MAX)) * GRID_X) ;
	this->ypos = (float(rand()) /  (float(RAND_MAX)) * GRID_Y) ;
}

/**
	Destructor frees memory taken by this piece when it is captured
*/
Piece::~Piece()
{
	free(this);
}

/**
	Clamp implementation, keep value between these params
	@param n value being tested
	@param lower the lower bound
	@param upper the upper bound
*/
float Piece::Clamp(float n, float lower, float upper) {
	return std::max(lower, std::min(n, upper));
}

/**
	Function that takes in a enum value and either 1 or 2 pieces to display information about
	@param req Request information
	@param piece Chess piece
	@param other Required for e_collison, 2nd Chess Piece

*/
string Piece::Info(Piece::info req, Piece* piece, Piece* other) {
	//p for position, e for event, i for information
	string str;

	switch (req) {
	case Piece::info::p_position:
		str = "(" + to_string(piece->xpos) + "," + to_string(piece->ypos) + ")";
		return str;
	case Piece::info::p_symbol:
		str = piece->symbol;
		return str;
	case Piece::info::e_collision:
		str = Info(Piece::p_symbol, piece) + " at position " + Info(Piece::p_position, piece) + " collided with " + Info(Piece::p_symbol, other) + " at position " + Info(Piece::p_position, other);
		return str;
	case Piece::info::p_score:
		str = "This piece has taken " + to_string(piece->takes) + " pieces";
		return str;
	default:
		return "ERROR";
	};
}



/**
	Method to check whether this piece collides with another
	@param other The other piece to check
*/
bool Piece::CheckCollision(Piece * other)
{
	//cout << "checking" << endl;
	if (this == other) {
		return false;
	}

	/*	Switch case checks what shape is colliding with what, it has the form
	circle(this)
	|  |
	|  ---circle(other)
	|  |
	|  ---square(other)
	|  |
	|  ---default;
	|
	square(this)
	|  |
	|  ---circle(other)
	|  |
	|  ---square(other)
	|  |
	|  ---default;
	|
	default;
	*/
	switch (this->shape) {
	case circle: {
		switch (other->shape) {
		case circle: {
			//SOHCAHTOA ( a^2 + b^2 = c^2)
			//Difference of x positions squared + Difference of y positions squared < Radius1 + Radius2 (same for these) squared
			if (fabs(((this->xpos - other->xpos) * (this->xpos - other->xpos)) + ((this->ypos - other->ypos) * (this->ypos - other->ypos))) < ((this->RADIUS + other->RADIUS) * (this->RADIUS + other->RADIUS))) {
				cout << Info(e_collision, this, other) << endl;
				return true;
			}
			return false;
			break;
		}
		case square: {

			//Clamp returns the max value between (other->xpos) and (minimum between other->xpos + side length or this->xpos)  
			float deltaX = this->xpos - Clamp(this->xpos, other->xpos, other->xpos + SIDE);
			float deltaY = this->ypos - Clamp(this->ypos, other->ypos, other->ypos + SIDE);

			//SOHCAHTOA again
			if (((deltaX * deltaX) + (deltaY*deltaY)) < (this->RADIUS * this->RADIUS)) {
				cout << Info(e_collision, this, other) << endl;
				return true;
			}
			return false;
			break;
		}
		default: {
			return false;
			break;
		}
		}
		return false;
		break;
	} // end of this == circle case

	case square: {
		switch (other->shape) {
		case circle: {
			//as above
			float deltaX = other->xpos - Clamp(other->xpos, this->xpos, this->xpos + SIDE);
			float deltaY = other->ypos - Clamp(other->ypos, this->ypos, this->ypos + SIDE);

			if (((deltaX * deltaX) + (deltaY*deltaY)) < (other->RADIUS * other->RADIUS)) {
				cout << Info(e_collision, this, other) << endl;
				return true;
			}
			return false;
			break;
		}
		case square: {

			//find the minimum and maximum x and y values
			float x1Min = this->xpos - (SIDE / 2);
			float y1Min = this->ypos - (SIDE / 2);
			float x1Max = this->xpos + (SIDE / 2);
			float y1Max = this->ypos + (SIDE / 2);
			float x2Min = other->xpos - (SIDE / 2);
			float y2Min = other->ypos - (SIDE / 2);
			float x2Max = other->xpos + (SIDE / 2);
			float y2Max = other->ypos + (SIDE / 2);

			//if one rectangle is to the left of the other completely then they haven't collided
			if (x1Min > x2Max || x1Max < x2Min) {
				return false;
			}
			//if one rectangle is above the other completely then they haven't collided
			else if (y1Min > y2Max || y1Max < y2Min) {
				return false;
			}
			//Must of collided so return true;
			else {
				cout << Info(e_collision, this, other) << endl;
				return true;
			}
			return false;
			break;
		}
		}
		return false;
		break;
	} // end of this == square case

	default: {
		return false;
		break;
	}
	} // end of switch
	
	
}

/**
	Adds a score to individual piece takes and displays how many pieces this piece has taken
	@param pieceScore Needs to be passed for derivitives to take in the array
*/
void Piece::AddScore(int pieceScore[])
{
	this->takes += 1;
	cout << Info(p_score, this) << endl;
}

```
	
</details>
<details><summary markdown="span" style="text-align:right">Show me the code! (Queen.cpp)</summary>

```cpp

/**
Space Chess, Queen.cpp
Purpose: A Queen Chess Piece type

@author Steven Kirby
@date 07/12/18
*/

#include "Queen.h"

/**
Calls Piece constructor with 'Q' symbol
*/
Queen::Queen() : Piece('Q')
{
	
}


Queen::~Queen()
{

}

/**
	Adds to total score of Queen pieces (hard coded) and adds to each pieces individual takes
	@param pieceScore array of total scores for pieces
*/
void Queen::AddScore(int pieceScore[]) {
	Piece::AddScore(pieceScore);
	pieceScore[2] += 1;
}

/**
	Queen can randomly move diagonally in either of 4 directions with equal distance moved x and y (direction can vary)like a bishop or like
	a rook can also randomly move horizontally or vertically in any of 4 directions 
*/
void Queen::Move()
{
	//Random whether going to be like a rook or like a bishop this move
	bool diagOrStr = rand() % 2;

	if (diagOrStr) {

		//see Bishop Move()
		float dis;
		int dir;
		dis = (float(rand()) / float(RAND_MAX)) * MAX_DISTANCE;
		dis = (dis == 0.0f) ? 0.1f : dis;
			
		do {	
			dir = (rand() % 2);
			dir = (dir == 0) ? -1 : 1;
		} while ((dir == 1) ? (dis + xpos) > GRID_X : (-dis + xpos) < 0);
			xpos = Clamp((dis * dir) + xpos, 0.0f, GRID_X);
		do {
			dir = (rand() % 2);
			dir = (dir == 0) ? -1 : 1;
		} while ((dir == 1) ? (dis + ypos) > GRID_Y : (-dis + ypos) < 0);
			ypos = Clamp((dis * dir) + ypos, 0.0f, GRID_Y);
		
	}
	else {

		//see Rook Move()
		float dis;
		bool dir = rand() % 2;
		do {	
			dis = ((float(rand()) / float(RAND_MAX)) * (MAX_DISTANCE + MAX_DISTANCE)) - MAX_DISTANCE;
			dis = (dis == 0.0f) ? 0.1f : dis;
		} while ((dir) ? (dis + xpos) < 0 || (dis + xpos) > GRID_X : (dis + ypos) < 0 || (dis + ypos) > GRID_Y);

		if (dir) {
			xpos = Clamp(dis + xpos, 0.0f, GRID_X);
		}
		else {
			ypos = Clamp(dis + ypos, 0.0f, GRID_Y);
		}
	}
	
}

```
	
</details>
{::options parse_block_html="false" /}
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3222">Gaming Simulations</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-sm-6">
    <img class="enlarge" src="/img/coursework/PhysicsCW.png" style="max-width:90%;max-height=350px">
  </div>
  <div class="col-sm-6">
    <h3>Part 1 - Newtonian Dynamics, Collision Detection and Resolution</h3>
	  <p>The game and framework was provided to us unfinished without any physics or AI, this is what we had to implement.</p>
	  <p>This part of the coursework involved detecting whether a collision had occured between AABB boxes and Spheres or a combination of. This was then to be improved using broad phase and narrow phase, I managed to implement a way of narrowing down the amount of collison calculations but would not class it as broad and narrow phase exactly; this is shown by the white squares in the image to the left.</p>
	  <p>The movement of player and enemy entities used newtonian dynamics with velocity, elasticity and mass affecting how impulses were resolved in the case of a collision. I implemented this quite well however shooting of the laser didnt work as well as i had hoped and was colliding in odd ways, leading to a very slow laser facing in odd directions, eventually I had to abandon this in order to work on other aspects of the coursework.</p> 
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-sm-6">
    <img class="enlarge" src="" style="max-width:90%;max-height=350px">
  </div>
  <div class="col-sm-6">
    <h3>Part 2 - AI(State/Decisions), Flocking, Pathfinding, Entity Lifetime and Gameplay Rules</h3>  		<p>For this section, I implemented a basic boids flocking system , where the red, pink and green robots(non enemies) once close enough would flock together and stay together moving as a group without moving as one block.</p>
	  <p>I also implemented some basic State system for AI, where in the enemy robots chased the player if the player was close by, and stopped when they were not and moved randomly instead, I also had other states such as guarding and shooting half completed however ran out of time for this coursework due to other deadlines.</p>
	  <p>I was also was unable to implement A* pathfinding into the codebase, however I would like to learn this so will try to create a demo of my own in the future.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3223">Graphics for Games</a></h2>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/coursework/GraphicsCW.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Assignment 1 - Space Scene</h3>
		<p>Using OpenGL to create a space scene which needed to incorporate the sun, stars, a planet and a spaceship (user controlled).</p>
		<p>I also added in a moving comet which randomly starts at a location in the distance and flys towards the player, when leaving the screen it starts somewhere randomly in the distance again.</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<img class="enlarge" src="/img/coursework/GraphicsCW2.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Assignment 2 - Shaders</h3>
		<p>Using OpenGL and GLSL I was to create four requested effects on cubes, and come up with two of my own.</p>
		<p>The two that I came up with on my own were the shattering cube and the twisting smiley cube.</p>
	</div>
	
</div>
<div class="row">
	<hr>
	<h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3224">Computer Games Development</a></h2>
	<p><a href="https://steve-kirby.github.io/game/TheEmpyreanTreasure.html">This link</a> takes you to a 'playable in browser' version of this prototype game.</p>
<hr>
</div>
<div class="row">
	<div class="col-sm-6">
		<img class="enlarge" src="/img/coursework/GameDevelopment.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Assignment 1 & 2 - Make a game</h3>
		<p>The screenshot shows the game in action, it isn't perfect and was extremely ambitious for the time I had, alongside looming deadlines for other modules and my dissertation. More importantly I learned a lot about Godot and game development in general whilst making this prototype game.</p>
		<p>We could use any language and/or game engine we wanted to create the game, I chose Godot due to it being free and had heard good things about it when researching a game engine to use.</p>
	</div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3122">Mobile Computer Systems Development</a></h2>
</div>
<div class="row">
	<div class ="col-sm-6">
		<br /><br />
		<img class="enlarge" src="/img/coursework/AppLog.png" style="max-width:90%;max-height:350px">
	</div>
	<div class="col-sm-6">
		<h3>Assignment 1 - Moodboard, Fontboard, Storyboard and Business Case</h3>
		<p>This stage was designing and developing ideas for the app, once I had started the storyboard I had a pretty good idea of what I wanted the app to look like.</p>
		<p>I also kept track of any ideas or problems I came across for the app in a spreadsheet</p>
	</div>
</div>
<div class="row">
	<hr>
	<div class="col-sm-6">
		<iframe width="90%" height="350" src="https://www.youtube.com/embed/wm44R9TGu7s"> </iframe>
	</div>
	<div class="col-sm-6">
		<h3>Assignment 2 - Coding the App</h3>
		<p>In this stage I programmed my app using Android Studio, I used Java for this rather then Kotlin.</p>
		<p>The embedded <a href="https://www.youtube.com/watch?v=wm44R9TGu7s">Youtube video shows the app in action</a> with voice over explaining what I am doing on the app.</p>
		<p>I then wrote a reflective essay on my experience designing and programming the app, highlighting what went right and what went wrong, as well as what I had learnt from this assignment.</p>
	</div>
	
	
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3123">Web Technologies</a></h2>
</div>

<div class="row">
  <hr>
  <div class="col-sm-6">
	  <img class="enlarge" src="/img/coursework/FontboardMoodboard.png" style="max-width:90%;max-height=350px"><br><br>
    <img class="enlarge" src="/img/coursework/WebTechSitemap.png" style="max-width:90%;max-height=350px"><br><br>
	<img class="enlarge" src="/img/coursework/WebTechStoryboard.gif" style="max-width:90%;max-height=350px"><br><br>
  </div>
  <div class="col-sm-6">
    <h3>Assignment 1 - Moodboard, Fontboard, Storyboard and Sitemap</h3>
    <p>For this assignment I was given a specification of a website in which would be used for keeping track of Keys that have been issued to users. These were physical keys on physical hooks in cupboards, controlled by an admin.</p>
	  <p>The gif shows the website storyboard in a powerpoint with links for moving around the website storyboard.</p>
  </div>
</div>

<div class="row">
  <hr>
  <div class="col-sm-6">
	  <img class="enlarge" src="/img/coursework/SearchKeys.png" style="max-width:90%;max-height=350px"><br><br>
	  <img class="enlarge" src="/img/coursework/LostKeys.png" style="max-width:90%;max-height=350px"><br><br>
	  <img class="enlarge" src="/img/coursework/SearchPerson.png" style="max-width:90%;max-height=350px"><br><br>
  </div>
  <div class="col-sm-6">
    <h3>Assignment 2 - Redbean, Twig, Sass, Bootstrap</h3>
	<p>Using a provided framework, I built upon this to create the website using Redbean and Twig primarily.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3124">System and Network Security</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-sm-6">
    <img class="enlarge" src="" style="max-width:90%;max-height=350px"><br><br>
  </div>
  <div class="col-sm-6">
    <h3>Assignment 1 - Capture the Flags</h3>
    <p>This coursework involved 10 tasks of differing security issues faced in computing including decompiling .jar files, cryptography, XSS, SQLi, exploiting buffer overflows, packet sniffing on a network and other variations upon these.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-sm-6">
    <img class="enlarge" src="" style="max-width:90%;max-height=350px"><br><br>
  </div>
  <div class="col-sm-6">
    <h3>Assignment 2 - Security Analysis</h3>
    <p>As a group of 4 students, we were to take a scenario, in this case a hospital providing a smartphone to all of the medical staff using a tracking system (Pozyx) as well as other uses. We then had to identify, assess and suggest risk control mechanisms for two different attacks that could occur against the hospital.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC3422">Web Construction and Management(Server-Side)</a></h2>
</div>
<div class="row">
  <hr>
  <div class="col-sm-6">
    <img class="enlarge" src="/img/coursework/WebServerReview.png" style="max-width:90%;max-height=350px"><br><br>
  </div>
  <div class="col-sm-6">
    <h3>Assignment 1 - Review of Web Server Technologies (Apache HTTPD)</h3>
    <p>This coursework I was tasked with choosing a Web Server technology to discuss and compare features/performance with other options available to use as a Web Servers backbone.</p>
  </div>
</div>
<div class="row">
  <hr>
  <div class="col-sm-6">
    <img class="enlarge" src="" style="max-width:90%;max-height=350px"><br><br>
  </div>
  <div class="col-sm-6">
    <h3>Assignment 2 - Deploy Apache Web Server</h3>
    <p>I deployed a fully functional server using a LAMP stack involving CentOS7, Apache, PHP5 and MySQL.</p>
	  <p>On top of this, Wordpress was used as a content management system in order to generate content. The website was customised with a theme and plugins installed to support an e-commerce store</p>
	  <p>I was also tasked with configuring the Web Server for use of URL rewrites, HTTPS, Custom Error Pages (e.g 404), Authentication and Access Control through htpasswd and an IP filter.</p>
	  <p>I touched on CGI, Reverse Proxies, and Jetty JVM, but had a few issues with these.</p> 
  </div>
</div>
