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
{::options parse_block_html="false" /}
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
    <img class="enlarge" src="" style="max-width:90%" max-height="350">
  </div>
  <div class="col-xs-6">
    <h3>Assignment 1 -</h3>
    <p style="color:red">Work in progress.</p>
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
    <h3>Assignment 1 -</h3>
  <p style="color:red">Work in progress.</p>
  </div>
</div>
<div class="row">
  <hr>
  <h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2024">Database Technology</a></h2>
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
<h2><a href="https://www.ncl.ac.uk/module-catalogue/module.php?code=CSC2025">Operating Systems</a></h2>
</div>
{::options parse_block_html="true" /}	
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

/***************************************************************************/
/***** ARRAYLIB.H IMPLEMENTATIONS ******************************************/
/***************************************************************************/

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
        
/***************************************************************************/
/***** THE FOLLOWING FUNCTIONS ARE IMPLEMENTED FOR YOU - DO NOT CHANGE *****/
/***************************************************************************/

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

/***************************************************************************/
```

</details>
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
