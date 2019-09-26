---
layout: post
title: "Numpy Cheatsheet"
date: 2018-10-10
tags: python numpy
---

*Import this to start*

	
	import numpy as np

**Importing And Exporting**

	np.loadtxt('file.txt') 			#From a text file
	np.genfromtxt('file.csv',delimiter=',') #From a CSV file



**Creating Arrays**

	np.array([(1,2,3),(4,5,6)]) 		# Two dimensional array
	np.zeros(3) 				# 3x1 array with all values 0
	np.ones((3,4)) 				# 3x4 array with all values 1
	np.eye(5) 				# 5x5 array of 0 with 1 on diagonal
	np.linspace(0,100,6) 	# Array of 6 evenly dividedvalues from 0 to 100
	np.arange(0,10,3)  # Array of values from 0 to< than 10 with step 3 (eg [0,3,6,9])
	np.full((2,3),8)			# 2x3 array with all values 8

**Properties Check**

	arr.size 				# Returns number of elements in arr
	arr.shape 			# Returns dimensions of arr (rows, columns)
	arr.dtype 			# Returns type of elements in arr
	arr.astype(dtype) 		# Convert arr elements to type dtype
	arr.tolist() 			# Convert arr to a Python list

**Copying , Sorting And Reshaping**

	np.copy(arr) 		# Copies arr to new memory
	arr.view(dtype) 	# Creates view of arr elements with type dtype
	arr.sort() 		# Sorts array
	arr.sort(axis=0) 	# Sorts specific axis of arr
	two_d_arr.flatten() 	# Flattens 2D array two_d_arr to 1D
	arr.T 		# Transposes arr (rows become columns and vice versa)
	arr.reshape(3,4) # Reshapes arr to 3 rows, 4 columns without changing data
	arr.resize((5,6)) # Changes arr shape to 5x6 and fills new values with 0

**Adding And Removing Element**

	np.mean(arr,axis=0)		# Returns mean along specific axis
	arr.sum() 			# Returns sum of arr
	arr.min() 			# Returns minimum value of arr
	arr.max(axis=0) 		# Returns maximum value of specific axis
	np.var(arr)			# Returns the variance of array
	arr.corrcoef() 			# Returns correlation coefficientof array
	np.std(arr,axis=1)	# Returns the standard deviation of specific axis


**Slicing, Subsetting ANd Indexing**

	arr[5] 			# Returns the element at index 5
	arr[2,5] 		# Returns the 2D array element on Index [2][5]
	arr[1]=4 		# Assigns array element on index 1 the value 4
	arr[1,3]=10 	   # Assigns array element on index [1][3] the value 10
	arr[0:3] 		# Returns the elements at indices 0,1,2 
	arr[0:3,4] 		# Returns the elements on rows 0,1,2 at column 4
	arr[:2] 		# Returns the elements at indices 0,1 
	arr[:,1] 		# Returns the elements at index 1 on all rows
	arr<5 			# Returns an array with boolean values	
	(arr1<3) & (arr2>5) # Returns an array with boolean values
	~arr 			# Inverts a boolean array
	arr[arr<5] 		# Returns array elements smaller than 5