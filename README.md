# pentaho-stata-plugin
## Pentaho Stata Plug-in Documentation
The Stata Input and Output transformation steps can read and write Stata v12 files, Stata v13, Stata v14, and Stata v15 file formats.
### Stata Input
Reads Stata v15 and earlier .dta files. The meta-data from the file (data, variable and value labels) can optionally be send to a separate target step.
 
Table 1: Stata Input Options
Option	Description
Step Name	Optionally, you can change the name of this step to fit your needs
File Name	Specifies the location and name of the input Stata file to be read. The file path and/or name can contain variable references of the form ${variablename}, and the value of the variable will be substituted during runtime. Press ctrl-space to get a pop-up list of available variables. Press the ‘Browse’ button to browse the file system and select an input file.
Send Data To	The target step to which the data records from the input file will be sent. The destination step can be selected from a pop-up list of available steps.
Send Meta Data To	The target step to which the meta data records from the input file will be sent. See Table 2 for the meta data format. This hop is optional.
Table 2: Meta data row layout
Field	Format	Values	Description
action	String(3)		Specify the type of metadata record
		lab	Dataset label
		var	Variable label
		def	Value label definition – one record for each value label
		val	Linking a variable to a value label
name	String(32)		The data file name in the case of ‘lab’ records
The variable name in the case of ‘var’ or ‘val’ records
The value label name in the case of ‘def’ records
value	Integer		The value for the value label, values must/will be listed in ascending order
label	String(80)		The dataset label text in the case of ‘lab’ records
The variable label text in the case of ‘var’ records
The value label name in the case of ‘val’ records
The value label text in the case of ‘def’ records
Stata Output
Output data to a Stata v12 (format 115) file. Optionally receives meta data to add variable and value labels to the saved data.
 
Option	Description
Step Name	Optionally, you can change the name of this step to fit your needs
File Name	Specifies the location and name of the input Stata file to be read. The file path and/or name can contain variable references of the form ${variablename}, and the value of the variable will be substituted during runtime. Press ctrl-space to get a pop-up list of available variables. Press the ‘Browse’ button to browse the file system and specify an input file name and location.
Get Meta Data From	Input step from which the meta data is read. This input stream must be in the format specified in Table 1 and field names are case-sensitive. All other steps are treated as input data and must have an identical row layout to each other. Providing meta data is optional.
Installation
Copy the stata.jar file to the folder “data-integration\plugins\steps\StataPlugin”. After re-starting Pentaho Kettle, the Stata steps will be listed in the Input and Output folders of the Spoon Design tab.
