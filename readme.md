﻿#Admesh Parser

##Table of Contents

- Description
- You Can't Use This Until You Download More Stuff
- Install
- Include
- admeshParser()
	- admeshDirectory
	- options
	- Returns
- Example

##Description

This module returns a function that takes an STL file and returns a JavaScript object containing information about the file. 

##You Can't Use This Until You Download More Stuff

To use this module, you will need [admesh](https://sites.google.com/a/varlog.com/www/admesh-htm). This module just parses the output, it does not include the binary.

You will also need an STL file to run this on. Two files are included in the 'test' folder.

##Install

	npm install admesh-parser

##Include

	var admeshParser = require('admesh-parser')

##admeshParser(admeshDirectory, options)
- **admeshDirectory** (String) 

	`'C:\\Users\\Me\\Documents\\admesh.exe'`

- **options** (Array or String)  
	The last element must be a string of the input file directory

		var options
		options = [
			"--remove-unconnected",
			"--fill-holes",
			"C:\\Users\\Me\\Documents\\gear.stl"
		]
		//or
		options = ["C:\\Users\\Me\\Documents\\gear.stl"]
		//or
		options =  'C:\\Users\\Me\\Documents\\gear.stl'

	The options argument can be either a string, or an array of strings.

- **Returns**

		{ x: { min: -1.334557, max: 1.370952 },
		  y: { min: -1.377953, max: 1.37723 },
		  z: { min: -1.373225, max: 1.242838 },
		  facets: 
		   { overall: { before: 3656, after: 3656 },
		     disconnected1: { before: 18, after: 0 },
		     disconnected2: { before: 3, after: 0 },
		     disconnected3: { before: 0, after: 0 },
		     disconnected: { before: 21, after: 0 },
		     degenerate: 4,
		     removed: 14,
		     added: 3,
		     reversed: 2 },
		  edges: { fixed: 24, backwards: 0 },
		  volume: 10.889216,
		  parts: 1,
		  normalsFixed: 12,
		  all: 
		   [ -1.334557,
		     1.370952,
		     -1.377953,
		     1.37723,
		     -1.373225,
		     1.242838,
		     3656,
		     3656,
		     1,
		     18,
		     0,
		     2,
		     3,
		     0,
		     3,
		     0,
		     0,	
		     21,
		     0,
		     1,
		     10.889216,
		     4,
		     24,
		     14,
		     3,
		     2,
		     0,
		     12 ] }
    

##Example

	var model = admeshParser(
		"C:\\Program Files\\admesh\\admesh.exe", //Admesh dir
		"C:\\Users\\Me\\Documents\\gear.stl" //Options (model dir)
	)

	console.log("Number of parts: " + model.parts)
	console.log("Min X: " + model.x.min)
	console.log("Max X: " + model.x.max)
	console.log("Num of facets, before: " + model.facets.overall.before)
	console.log("Volume: " + model.volume)
