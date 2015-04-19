#JSON object class 2.1
##By RCDMK - rcdmk@rcdmk.com

###Licence:
MIT license: http://opensource.org/licenses/mit-license.php
The MIT License (MIT)
Copyright (c) 2012 RCDMK - rcdmk@rcdmk.com

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:  

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.  

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.  

###How to use:

<!-- languages: vbscript, vb -->

    ' instantiate the class
	Dim oJSON = New JSON
	
	' add properties
	oJSON.Add "prop1", "someString"
	oJSON.Add "prop2", 12.3
	oJSON.Add "prop3", Array(1, 2, "three")
	
	' change some values
	oJSON.Change "prop1", "someOtherString"
	oJSON.Change "prop4", "thisWillBeCreated" ' this property doen't exists and will be created automagically
	
	' get the values
	Response.Write oJSON.Value("prop1") & "<br>"
	Response.Write oJSON.Value("prop2") & "<br>"
	Response.Write oJSON.Value("prop3") & "<br>"
	Response.Write oJSON.Value("prop4") & "<br>"
	
	' get the JSON formatted output
	Dim jsonSting
	jsonString = oJSON.Serialize() ' this will contain the string representation of the JSON object
	
	oJSON.Write() ' this will write the output to the Response - equivalent to: Response.Write oJSON.Serialize()
	
	
	' load and parse some JSON formatted string
	jsonString = "{ ""strings"" : ""valorTexto"", ""numbers"": 123.456, ""arrays"": [1, ""2"", 3.4, [5, 6, [7, 8]]], ""objects"": { ""prop1"": ""outroTexto"", ""prop2"": [ { ""id"": 1, ""name"": ""item1"" }, { ""id"": 2, ""name"": ""item2"", ""teste"": { ""maisum"": [1, 2, 3] } } ] } }" ' double quotes here because of the VBScript quote scaping
	
	oJSON.Parse jsonString
	
	oJSON.Write()
	
	
If you want to use arrays, I have something for you too

    ' instantiate the class
	Dim oJSONarray = New JSONarray
	
	' add something to the array
	oJSONarray.Push oJSON 	' Can be JSON objects, and even JSON arrays
	oJSONarray.Push 1.25 	' Can be numbers
	oJSONarray.Push "and strings too"
	
	' write to page
	oJSONarray.Write() ' Gess what? This does the same as the Write method from JSON object
	