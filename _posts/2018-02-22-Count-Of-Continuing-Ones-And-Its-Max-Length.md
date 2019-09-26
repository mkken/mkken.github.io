---
layout: post
title: "Count Of Continuing Ones And Its Max Length"
date: 2018-02-22
tags: java programTricks
---

A short snippet of code to identify Count of Continuing Ones and its Max Length.



	package javaConcepts;
 
	import java.util.Arrays;
	import java.util.Collections;
	import java.util.LinkedList;
 
	public class ContinuingOnes {
 
	public static void main(String[] args) {
	String oz = "10000111011001111110011100";
 
	LinkedList<String> list = new LinkedList<String>(Arrays.asList(oz.split("0+")));
	System.out.println(list);
	Collections.sort(list);
	int maxLength = list.getLast().length();
 
	System.out.println("max length: " +maxLength);
 
	}
	}


    


**OUTPUT**

```
[1, 111, 11, 111111, 111]
max length: 6
```