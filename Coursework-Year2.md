---
layout: coursework-highlights
title: "Coursework - Year 2"
permalink: /coursework2
---

<h1 style="text-align:center;margin-top:20px;">Coursework - Year 2</h1>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2021">Software Engineering</a></h2>
</div>
{::options parse_block_html="true" /}
<div class="row">
<hr>
<div class="row">
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/UMLdiagram.png" style="max-width:90%" max-height="350"><br><br>
<img class="enlarge" src="/img/coursework/TDDtests.png" style="max-width:90%" max-height="350">
</div>
<div class="col-xs-6">
<h3>Assignment 1 - Test Driven Development</h3>
<p>This assignment was split into 3 tasks, the first of which being to produce a UML diagram.</p>
<p>The second task was to produce the program using the UML diagram as a base, writing the code first and then the tests, the code could differ from the UML diagram as long as any changes were documented in the code</p>
<p>The third task was to program the same program, however using TDD (Test Driven Development) first, producing tests before doing any programming, we had to show the test failing and then passing once the programming was complete; this was tracked using the framework provided.</p>
</div>
</div>
<div class="row">
<details><summary markdown="span" style="text-align:right">Show me the code!</summary>

```java
package com.example.tddCoursework.Part1And2CodeAndTest;

import java.util.ArrayList;

public class RecordManagerNonTDD {
	String officeName;
	ArrayList<EmployeeNonTDD> employees = new ArrayList<EmployeeNonTDD>();
	
	
	RecordManagerNonTDD(String officeName){
		this.officeName = officeName;
	}
	
	public ArrayList<EmployeeNonTDD> getAllEmployees(){
		return employees;
	}
	
	public void addEmployee(EmployeeNonTDD employee){
		employees.add(employee);
	}
	
	public void addEmployee(String name, String address, String phoneNumber, String department, String dateStarted){
		employees.add(new EmployeeNonTDD(name,address,phoneNumber,department,dateStarted));
	}
	
	public String getAllEmployeeDetails(){
		String str = "";
		for(EmployeeNonTDD emp : employees){
			str += emp.toString();
		}
		
		return str;
		
	}
	
}

import java.util.ArrayList;

public class EmployeeNonTDD {
	final int STAFF_ID;
	public static int id = 0;
	String name;
	String address;
	String phoneNumber;
	String department;
	String dateStarted;
	ArrayList<TrainingRecordNonTDD> trainingRecords = new ArrayList<TrainingRecordNonTDD>();
	
	EmployeeNonTDD(String name, String address, String phoneNumber, String department, String dateStarted){
		
		this.STAFF_ID = id++;
		this.name = name;
		this.address = address;
		this.phoneNumber = phoneNumber;
		this.department = department;
		this.dateStarted = dateStarted;
	}
	
	public String toString(){
		String str = String.format(" %d %s %s %s %s %s Training Records[",this.STAFF_ID,this.name,this.address,this.phoneNumber,this.department,this.dateStarted);
		if (this.trainingRecords.size() < 1){
			str += "n/a";
		} else {
		for(TrainingRecordNonTDD tr : this.trainingRecords){
			str += tr.toString();
			if(tr != this.trainingRecords.get(trainingRecords.size()-1))
				str += ", ";
		}
		}
		str += "];";
		return str;	
	}
}

public class TrainingRecordNonTDD {

	String qualificationName;
	String dateAchieved;
	String levelOfQualification;
	
	TrainingRecordNonTDD(String qualificationName, String levelOfQualification ,String dateAchieved){
		this.qualificationName = qualificationName;
		this.dateAchieved = dateAchieved;
		this.levelOfQualification = levelOfQualification;
	}
	
	public String toString(){
		
		String tr = String.format("%s %s %s", this.qualificationName,this.levelOfQualification,this.dateAchieved);
		
		return tr;
	}
}
```

</details>
<br/>
<details><summary markdown="span" style="text-align:right">Show me the tests!</summary>

```java
package com.example.tddCoursework.Part1And2CodeAndTest;

import static org.junit.Assert.*;

import org.junit.*;

public class RecordManagerTestPart2 {
	
	public RecordManagerNonTDD rm,anotherRm;
	public EmployeeNonTDD testEmployee;
	public EmployeeNonTDD stevenKirby;
	
	@Before
	public void setUp(){
		
		rm = new RecordManagerNonTDD("Test");
		anotherRm = new RecordManagerNonTDD("Another");
		
		stevenKirby = new EmployeeNonTDD("Steven Kirby","17 Exam Lane","07432965778","Sales","15/11/2017");
		testEmployee = new EmployeeNonTDD("Test Man","28 Test Hill","07422945322","IT","12/11/2017");

		rm.addEmployee(stevenKirby);
		rm.addEmployee(testEmployee);
		
		stevenKirby.trainingRecords.add(new TrainingRecordNonTDD("BSC Computer Science","First","10/11/2017"));
		testEmployee.trainingRecords.add(new TrainingRecordNonTDD("BSC Biomedical Studies","Pass","05/02/2016"));

		testEmployee.trainingRecords.add(new TrainingRecordNonTDD("BSC Biomedical Studies 2","First","01/07/2016"));
		testEmployee.trainingRecords.add(new TrainingRecordNonTDD("BSC Biomedical Studies 3","Second","08/04/2017"));
		
		EmployeeNonTDD.id = 0;
	}
	
	
	
	@Test
	public void testRecordManager() {
		assertTrue(rm != null);
		
	}
	
	@Test
	public void testMultipleRecordManagers(){
		assertTrue(rm != null && anotherRm !=null && rm != anotherRm);
	}

	@Test
	public void testGetAllEmployees() {
		assertEquals(rm.employees,rm.getAllEmployees());
		
	}

	@Test
	public void testAddEmployee() {
		assertEquals(stevenKirby,rm.employees.get(0));
	}

	@Test
	public void testGetAllEmployeeDetails(){
		assertEquals(" 0 Steven Kirby 17 Exam Lane 07432965778 Sales 15/11/2017 Training Records[BSC Computer Science First 10/11/2017]; 1 Test Man 28 Test Hill 07422945322 IT 12/11/2017 Training Records[BSC Biomedical Studies Pass 05/02/2016, BSC Biomedical Studies 2 First 01/07/2016, BSC Biomedical Studies 3 Second 08/04/2017];",rm.getAllEmployeeDetails());
	}
	
	@Test
	public void testNoTrainingRecords(){
		
		stevenKirby.trainingRecords.remove(0);
		assertEquals(" 0 Steven Kirby 17 Exam Lane 07432965778 Sales 15/11/2017 Training Records[n/a]; 1 Test Man 28 Test Hill 07422945322 IT 12/11/2017 Training Records[BSC Biomedical Studies Pass 05/02/2016, BSC Biomedical Studies 2 First 01/07/2016, BSC Biomedical Studies 3 Second 08/04/2017];",rm.getAllEmployeeDetails());
	}
}
```
	
</details>
<br/>
</div>
</div>
<div class="row">
<hr>
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/TDDreport.png" style="max-width:90%" max-height="350">
</div>
<div class="col-xs-6">
<h3>Assignment 2 - Report - Test Driven Development</h3>
<p>This assignment required us to write a short report (500 words) based on our experience of producing a same piece of software with both TDD and non-TDD workflows.</p>
</div>
</div>
<div class="row">
<div class="row">
<hr>
<div class="col-xs-6">
<img class="enlarge" src="" style="max-width:90%" max-height="350">
</div>
<div class="col-xs-6">
<h3>Assignment 3 - VDM-SL (Overture) Temperature Monitoring</h3>
<p>Using VDM-SL to check logic and prove properties of a program by modelling its' systems in Overture.</p>
<p style="color:red">Work in progress.</p>
</div>
</div>
<div class="row">
<hr>
<h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2022">Software Engineering Team Project</a></h2>
</div>
<div class="row">
<hr>
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/SeatonValleyDemo.gif" style="max-width:90%;max-height:350px">
</div>
<div class="col-xs-6">
<p>As part of our <em>Software Engineering - Group Project</em> module we were to design and develop an android app, this could be a variety of different options chosen by the university.</p>
<p>We decided as a group to take on the Seaton Valley Council app, which could provide information to residents of the parish.</p>
<p>The gif here shows the app in use, for this part of the team project I was lead programmer along with 2 other programmers and 2 testers, ensuring any code pushed using gitlab was functional and could integrate with previous code.</p>
</div>
<hr>
</div>
<div class="row">
<hr>
<h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2023">Algorithm Design and Analysis</a></h2>
</div>
<div class="row">
<hr>
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/SortingAlgos.png" style="max-width:90%;max-height=350px">
</div>
<div class="col-xs-6">
<h3>Assignment 1 - Implementing and Comparing Sorting Algorithms</h3>
<p>For this coursework I implemented insertion sort, quick sort and was also provided a new sorting algorithm to implement which included elements from both of these sorting methods.</p>
<p>I believe the constructor, reading and displaying methods were provided to me by the course leader, with the module being about the algorithms rather then programming.</p>
</div>
</div>
<div class="row">
<details><summary markdown="span" style="text-align:right">Show me the code! (Sort.java)</summary>

```java

/*****************************************************/
/***     Initial Author: Jason Steggles 20/09/17   ***/
/***     Extended by: Steven Kirby  Date 24/10/17  ***/
/*****************************************************/

import java.io.*;
import java.text.*;
import java.util.*;

public class Sort {

	/** Array of integers to sort **/
	private int[] A;

	/** Size of the array **/
	private int size;

	/** Number of elements actually used in array **/
	private int usedSize;

	/** Global variables for counting sort comparisons **/
	public int compIS;
	/** Global comparison count for Insertion Sort **/
	public int compQS;
	/** Global comparison count for Quicksort **/
	public int compNewS;

	/** Global comparison count for new sort **/

	/*****************/
	/** Constructor **/
	/*****************/
	Sort(int max) {
		/** Initialiase global sort count variables **/
		compIS = 0;
		compQS = 0;
		compNewS = 0;

		/** Initialise size variables **/
		usedSize = 0;
		size = max;

		/** Create Array of Integers **/
		A = new int[size];
	}

	public int getArraySize() {
		return usedSize;
	}

	/*********************************************/
	/*** Read a file of integers into an array ***/
	/*********************************************/
	public void readIn(String file) {
		try {
			/** Initialise loop variable **/
			usedSize = 0;

			/** Set up file for reading **/
			FileReader reader = new FileReader(file);
			Scanner in = new Scanner(reader);

			/** Loop round reading in data while array not full **/
			while (in.hasNextInt() && (usedSize < size)) {
				A[usedSize] = in.nextInt();
				usedSize++;
			}

		} catch (IOException e) {
			System.out.println("Error processing file " + file);
		}
	}

	/**********************/
	/*** Display array ***/
	/**********************/
	public void display(int line, String header) {
		/*** Integer Formatter - three digits ***/
		NumberFormat FI = NumberFormat.getInstance();
		FI.setMinimumIntegerDigits(3);

		/** Print header string **/
		System.out.print("\n" + header);

		/** Display array data **/
		for (int i = 0; i < usedSize; i++) {
			/** Check if new line is needed **/
			if (i % line == 0) {
				System.out.println();
			}

			/** Display an array element **/
			System.out.print(FI.format(A[i]) + " ");
		}
	}

	/** Insertion Sort Algorithm **/
	public void insertion() {
		// Loop through the array, for N - 1
		for (int i = 1; i < A.length; i++) {
			int key = A[i];
			/*
			 * Store an extra pointer as j variable to loop through array
			 * without affecting i variable
			 */
			int j = i;
			// Check to ensure we don't have a out of bounds exception at -1 of
			// array which doesn't exist.
			// also checks to see if the pointer is in the right place by
			// checking if the value to the left in the array is bigger then it.
			while (j > 0 && key < A[j - 1]) {
				// comparison was made so we would increment the counter.
				compIS++;
				// move values up the array as we know the key should be lower
				// then this.
				A[j] = A[j - 1];
				// decrement j to check the next value in the array.
				j -= 1;
			}
			// when we find the right place even though the while loop is false
			// we need to increment the counter.
			compIS++;
			// insert key into the correct place in the array.
			A[j] = key;
		}

	}

	/** QuickSort Algorithm **/
	public void quick(int L, int R) {
		// if pointers haven't crossed during recursion.
		if (R > L) {
			// partition the left side then the right side.
			int p = partition(L, R);
			quick(L, p - 1);
			quick(p + 1, R);
		}
	}

	/**
	 * Method to partition array from left pointer to right pointer in array.
	 **/
	public int partition(int L, int R) {
		int pL = L;
		int pR = R;
		// value always always right value to start (pivot)
		int v = A[R];

		// if pointers haven't crossed yet
		while (pL < pR) {

			// starting from the left pointer, keep moving right in array until
			// a value less then the pivot is found
			while (A[pL] < v) {
				pL += 1;
				compQS++;
			}
			compQS++;
			// then check from the right pointer and move to the left, ensuring
			// we don't move past the original left pointer
			while (A[pR] >= v && pR > L) {
				pR -= 1;
				compQS++;
			}
			compQS++;
			// swap the values of the pointers if left pointer still smaller the
			// right pointer
			if (pL < pR) {
				swap(pL, pR);
			}
		}
		// swap the value with the original pivot.
		swap(pL, R);
		// return the new left pointer.
		return pL;
	}

	/** Method to swap one element in an array with another **/
	public void swap(int L, int R) {
		// Temporarily store value in variable before overwriting it.
		int temp = A[L];
		A[L] = A[R];
		// and finally writing it to the swap counterpart.
		A[R] = temp;
	}

	/** New Sorting Algorithm **/
	public void newsort() {
		// for each position in array starting from index 0
		int pos = 0;
		while (pos < A.length - 1) {
			// find the minimum value in the array that hasn't been sorted yet.
			int min = findMinFrom(pos);

			// check which array index is the minimum value
			for (int i = pos; i < A.length; i++) {
				if (A[i] == min) {
					// swap it into position
					swap(i, pos);
					// increase the position to find the next minimum
					pos += 1;
				}
				compNewS++;
			}
		}
	}

	/**
	 * Method to find and return the next minimum value in the array after a
	 * given position
	 **/
	public int findMinFrom(int pos) {
		int min = A[pos];
		for (int i = pos + 1; i < A.length; i++) {
			// if value is smaller, it becomes the new minimum
			if (A[i] < min) {
				min = A[i];
			}
			compNewS++;
		}
		return min;

	}
} /** End of Sort Class **/

```

</details>
<br/>
<details><summary markdown="span" style="text-align:right">Show me the code! (TestSort.java)</summary>

```java

/*************************************************/
/***    Test class for Sort class    	       ***/
/***                                           ***/
/***    Author: Steven Kirby    24/10/2017     ***/
/*************************************************/

public class TestSort {
	public static void main(String[] args) {

		// tests using each file as required, array size, test file, which
		// algorithms to test(insertion,quick,new)
		test(15, "test1.txt", true, true, false);
		test(15, "test2.txt", true, true, false);
		test(100, "test3.txt", true, true, true);
		test(100, "test4.txt", true, true, true);
		test(100, "test5.txt", true, false, true);

	}

	// method for calling whichever tests are required for each array test file.
	public static void test(int maxArraySize, String testfile, boolean i, boolean q, boolean n) {

		// read in and display array before it is sorted
		Sort beforeSorting = new Sort(maxArraySize);
		beforeSorting.readIn(testfile);
		beforeSorting.display(10, "Array Before Sorting using " + testfile);
		System.out.println("\n");

		// insertion sort test
		if (i) {
			Sort sortTestInsertion = new Sort(maxArraySize);
			sortTestInsertion.readIn(testfile);
			sortTestInsertion.insertion();
			sortTestInsertion.display(10, "Insertion Test using " + testfile);
			System.out.println("\n   Insertion sort comparison counter: " + sortTestInsertion.compIS);
		}
		// quick sort test
		if (q) {
			Sort sortTestQuick = new Sort(maxArraySize);
			sortTestQuick.readIn(testfile);
			sortTestQuick.quick(0, sortTestQuick.getArraySize() - 1);
			sortTestQuick.display(10, "\nQuickSort Test using " + testfile);
			System.out.println("\n   Quicksort comparison counter: " + sortTestQuick.compQS);
		}
		// new sort test
		if (n) {
			Sort sortTestNew = new Sort(maxArraySize);
			sortTestNew.readIn(testfile);
			sortTestNew.newsort();
			sortTestNew.display(10, "\nNewSort Test using " + testfile);
			System.out.println("\n   Newsort comparison counter: " + sortTestNew.compNewS);
		}
		System.out.println("\n------------------------------------------\n");
	}

} /** End of Test class **/

```

</details>
</div>

<div class="row">
<hr>
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/RopeCutting.png" style="max-width:90%;max-height=350px">
</div>
<div class="col-xs-6">
<h3>Assignment 2 - Algorithm Design and Analysis</h3>
<p></p>
</div>
</div>
<div class="row">
<hr>
<h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2024">Database Technology</a></h2>
</div>
<div class="row">
<hr>
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/DatabaseDesign.png" style="max-width:90%;max-height=350px"><br><br>
</div>
<div class="col-xs-6">
<h3>Assignment 1 - Database Design</h3>
<p>I created a database for a bus company, making sure the relationships of the database would cover all the data and their connections.</p>
</div>
</div>
<div class="row">
<hr>
<div class="col-xs-6">
<img class="enlarge" src="/img/coursework/SparkOutput.png" style="max-width:90%;max-height=350px"><br><br>
</div>
<div class="col-xs-6">
<h3>Assignment 2 - Spark (Java) - Movie Rating Database </h3>
<p>Using spark and 3 large .csv files for movies, ratings and genres. I was tasked with producing output similar to the image shown left, I do not have the data files any more so I can not show how these were laid out.</p>
</div>
</div>
<div class="row">
<details><summary markdown="span" style="text-align:right">Show me the code!</summary>
	
```java
package sparkCoursework;

import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Arrays;
import java.util.List;

import org.apache.log4j.Level;
import org.apache.log4j.LogManager;
import org.apache.spark.SparkConf;
import org.apache.spark.api.java.JavaSparkContext;
import org.apache.spark.sql.Dataset;
import org.apache.spark.sql.Row;
import org.apache.spark.sql.SparkSession;
import static org.apache.spark.sql.functions.*;

public class coursework {

	private static String PATH = Messages.getString("Coursework.0"); //$NON-NLS-1$
	private static String MOVIES_DATA = "movies.csv";
	private static String RATINGS     = "ratings.csv";
	private static String MOVIE_GENRE_DATA = "movieGenres.csv";
	
	static SparkConf conf = new SparkConf().setMaster("local").setAppName("My App");
	static JavaSparkContext sc = new JavaSparkContext(conf);
	static SparkSession spark = SparkSession.builder().appName("Java Spark SQL basic example")
			.config("spark.some.config.option", "some-value").getOrCreate();
	
	static boolean headers = false;
	public static void main(String[] args) {
		// TODO Auto-generated method stub

		LogManager.getLogger("org").setLevel(Level.ERROR);
		
		System.out.println("Step 1");
		//Step 1 - load data and print schemas
		Dataset<Row> movies = LoadMoviesData();
		movies.printSchema();
		Dataset<Row> ratings = LoadRatingsData();
		ratings.printSchema();
		
		System.out.println("Step 2 - no info to show");
		//Step 2 - CSV WRITER APPENDS TO FILE SO MAY NEED TO COMMENT THIS OUT IF YOU RUN CODE
		//Takes 5-10 minutes
		//Put data into lists 
		List<Row> movieList = movies.select("movieId").collectAsList();
		List<Row> genresList = movies.select("genres").collectAsList();
		//list to hold individual genres
		List<String> movieGenre;
		//index
		int i = 0;
		for(Row m : movieList ){
		//Split genres and remove [ and ]
			movieGenre = Arrays.asList((genresList.get(i).toString().replace("[","").replace("]","").split("\\|")));
			for(String g : movieGenre){
				//method to output to CSV
				outputToCSV(m.toString().replace("[", "").replace("]", "") + "," + g.toString());
			}
				i++;
		}
		System.out.println("Step 3");
		//Step 3
		
		//load newly created csv file data
		Dataset<Row> movieGenres = LoadMovieGenresData();
		movieGenres.printSchema();
		//show top 50
		movieGenres.orderBy(movieGenres.col("movieId").desc()).show(50);
		
		System.out.println("Step 4");
		//Step 4
		//count after grouping genres together and rename count column
		Dataset<Row> genrePopularity = movieGenres.groupBy(movieGenres.col("genre")).count().withColumnRenamed("count", "moviesCount");
		genrePopularity.printSchema();
		//show top 10 most popular genres
		genrePopularity.orderBy(genrePopularity.col("moviesCount").desc()).show(10);
		
		System.out.println("Step 5");
		//Step 5
		Dataset<Row> topTen = genrePopularity.orderBy(genrePopularity.col("moviesCount").desc()).limit(10);
		//get table of all users that have rated a movie of the top 10 genre
		Dataset<Row> joinedData = ratings.join(movieGenres,"movieId").join(topTen,"genre");
		//group genre and userId to see each count of genre each user has
		Dataset<Row> userGenre = joinedData.groupBy(joinedData.col("genre"),joinedData.col("userId")).count();
		//order by the most then remove any data that has the same genre after this top one is found, could also use max
		Dataset<Row> ugPairs = userGenre.orderBy(userGenre.col("genre"),userGenre.col("count").desc()).dropDuplicates("genre");
		ugPairs.printSchema();
		ugPairs.select(ugPairs.col("genre"),ugPairs.col("userId")).show();
		
		System.out.println("Step 6");
		//Step 6
		//count how many movies user has rated
		Dataset<Row> numMoviesPerUser = ratings.groupBy(ratings.col("userId")).count().withColumnRenamed("count", "ratingsCount");
		//get the top 10 users
		Dataset<Row> top10NumMoviesPerUser = numMoviesPerUser.orderBy(numMoviesPerUser.col("ratingsCount").desc()).limit(10);
		top10NumMoviesPerUser.printSchema();
		top10NumMoviesPerUser.show();
		//see what genre they have most reviewed
		Dataset<Row> top10CommonGenre = ratings.join(movieGenres,"movieId").join(top10NumMoviesPerUser,"userId");
		Dataset<Row> commonGenre = top10CommonGenre.groupBy(top10CommonGenre.col("userId"), top10CommonGenre.col("genre")).count().withColumnRenamed("genre", "mostCommonGenre");
		commonGenre.printSchema();
		//remove any other data for that user after highest genre is found for that user, join numMoviesPerUser again to be able to see their original ratingsCount
		commonGenre.orderBy(commonGenre.col("count").desc()).dropDuplicates("userId").join(numMoviesPerUser, "userId").select("userId","ratingsCount","mostCommonGenre").show();
		
		System.out.println("Step 7");
		//Step 7
		//group data of the same movieId to find the average and variance of the ratings that were left for them, renamed columns
		Dataset<Row> avgRating = ratings.groupBy(ratings.col("movieId")).agg(avg("rating"),variance("rating")).withColumnRenamed("var_samp(rating)", "variance").withColumnRenamed("avg(rating)","averageRating");
		//show the top 10 rated
		avgRating.orderBy(avgRating.col("averageRating").desc()).limit(10).show();
		}


	private static Dataset<Row> LoadRatingsData() {
		return spark.read().option("inferSchema", true).option("header", true).option("multLine", true)
				.option("mode", "DROPMALFORMED").csv(PATH + RATINGS);
	}

	private static Dataset<Row> LoadMoviesData() {
		return spark.read().option("inferSchema", true).option("header", true).option("multLine", true)
				.option("mode", "DROPMALFORMED").csv(PATH + MOVIES_DATA);
	}
	
	private static Dataset<Row> LoadMovieGenresData() {
		return spark.read().option("inferSchema", true).option("header", true).option("multLine", true)
				.option("mode", "DROPMALFORMED").csv(PATH + MOVIE_GENRE_DATA);
	}
	

	public static void outputToCSV(String str) {

		try {
			// new file with append true
			FileWriter w = new FileWriter("src/main/resources/movieGenres.csv", true);
			BufferedWriter b = new BufferedWriter(w);

			// if the headers have not already been written to the file, then
			// write them
			if (!headers) {
				b.write("movieId,genre\n");
				headers = true;
			}
			
			b.write(str + "\n");
			b.flush();
			b.close();

		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}

	}
}
```
	
</details>
</div>

<div class="row">
<hr>
<h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2025">Operating Systems</a></h2>
</div>
<div class="row">
<hr>
<div class="col-xs-6">
<img src="" style="max-width:90%;max-height=350px"><br><br>
</div>
<div class="col-xs-6">
<h3>Assignment 1</h3>
<p>Hard to remember what this was for, however I believe we were changing a function of the minix operating system.</p>
<p>Sadly no output to be shown at the moment.</p>
</div>
<div class="row">
<details><summary markdown="span" style="text-align:right">Show me the code!</summary>

```c
/*
 * Student Name : Steven Kirby
 * Student Number : 16027577
 * Date : 14/11/2017
 */
#include <errno.h>
#include <limits.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#include "arraylib.h"

/* error message format for fatalerror */
static const char *ERR_FMT = "%s:%d - %s, errno %d: %s\n";

array *newarray(int len) {
/* check if array will be of valid length */
	if(len < 1){
		errno = EINVAL;
		return NULL;
	}

/* dynamic allocation of array struct */
	array *struc = (array *) malloc(sizeof(array));

/* allocate array, giving it enough size for len of ints */
	int* newArray = calloc(len,sizeof(int));

/* assign length and pointer to fields of array struct */
	struc->ai = newArray;
	struc->len = len;

/* if allocation of memory failed set errno and release any memory allocation, then return NULL */
	if(!struc || !newArray){
		errno = ENOMEM;	
		delarray(struc);
		return NULL;
	} 
/* if all successful will return pointer to array struct */
	return struc;
}


int get(array *arr, int idx) {

/* check for any errors, set errno and return the minimum value of int if any error */
	if(arr == NULL || arr->ai == NULL|| idx >= arr->len || idx < 0){
		errno = EINVAL;
		return INT_MIN;
	}

/* returns value in ai[x] */
	return arr->ai[idx];
}
                
void set(array *arr, int idx, int value) {
  
/* check for any errors, set errno if any error */
	if(arr == NULL || arr->ai == NULL || idx >= arr->len || idx < 0){
		errno = EINVAL;

/* needs else as doesnt return on error (void method) */
	} else {

/* set value of ai[x] to the value given */
	arr->ai[idx] = value;
	}
}

void foreach(array *arr, applyfunction applyf) { 

/* check to see if all conditions of foreach method specification are met */
	if(arr && arr->ai && applyf && arr->len > 0){	

/* loop iterates through each value in array to apply function to  */
		for (int a = 0;a < arr->len;a++){

/* stores the resulting value of applyf in the array at index a */
			arr->ai[a] = applyf(arr,a);
		}    
	}
}

void print(FILE *stream, array *arr) {

/* string always starts with [ */
	fprintf(stream,"[");

/* check for errors */
	if(arr && arr->ai && arr->len > 0){

/* loop through the array, printing each value out */
		for(int i = 0; i < arr->len; i++){
			fprintf(stream," %i,",arr->ai[i]);
		}	
	}

/* close the string whether errors were found or not*/
	fprintf(stream," ]");
} 
        
THE FOLLOWING FUNCTIONS ARE IMPLEMENTED FOR YOU - DO NOT CHANGE

/* see println comments in arraylib.h */
void println(FILE *stream, array *arr) {
    print(stream, arr);
    fprintf(stream, "\n");
}

/* see delarray comments in arraylib.h */
void delarray(array *arr) {
    if (arr) { 
        if (arr->ai) 
            free(arr->ai);
        free(arr);
    }
}

/* see fatalerror comments in arraylib.h */
void fatalerror(int line, char *msg) {
    fprintf(stderr, ERR_FMT, __FILE__, line, msg, errno, strerror(errno));
    exit(EXIT_FAILURE);
}

/* see newarray_e comments in arraylib.h */
array *newarray_e(int len) {
    array *arr = newarray(len);
    
    if (!arr)
        fatalerror(__LINE__, "array allocation failed");
        
    return arr;
}

/* see get_e comments in arraylib.h */
int get_e(array *arr, int idx) {
    int val = get(arr, idx);
    
    if (val == INT_MIN && errno == EINVAL)
        fatalerror(__LINE__, "null array or index out of bounds");
    
    return val;
}
        
/* see set_e comments in arraylib.h */
void set_e(array *arr, int idx, int value) {
    set(arr, idx, value);
    
    if (errno == EINVAL)
        fatalerror(__LINE__, "null array or index out of bounds");
}
```

</details>
</div>
</div>
{::options parse_block_html="false" /}
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2026">Computer Networks</a></h2>
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
