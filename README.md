		FS All Multicoding

Brief Description
To create a single column containing the combined responses for a set of multicode responses from every Multi or Grid question found in the file 

Overview
DP team use the software QPS to create data tables. Data for Multis or Grids must be in one column, with the answers separated by commas. This macro allows DP to convert Forsta data to QPS importable data

As preconditions:

File must have at least one Multi or Grid question

Multi question tags are: _om, _omos, _al

Grid question tags are:  _aag, _adg, _bvg, _eag, _erg, _fbg, _frg, _ftg, _itg, _jrg, _keyadg, _ndg, _grid (_og), _opg, _pig, _ppg, _prg, _reg, _sbg, _sug

DP must have renamed resp_id column to SERIAL. SERIAL must be the header of the first column in the data file

A. Reusable Requirements | RR 3 :

ID

Acceptance Criteria

Notes

RR-1
Error trap.

Add a general error trap to the macro for edge cases. If triggered, show the following error message “An error has occurred while attempting to run the macro. Please contact a member of the IT Team with the name of the macro and the following information: Error.Number and Error.Description

Progress bar.

Update the status bar to inform the user about the progress of the macro. Show a percentage of completion i.e. “32% progress”. If the process takes too long, show the current process being run by the macro i.e. “32% progress: calculating scores”

Application.ScreenUpdating 

Screen updating refers to the process where Excel visually re-draws the monitor with every change made by a running macro. This causes screen flickering and slows down the execution of the code. For efficiency purposes, Application.ScreenUpdating must be turned OFF right before the macro process starts, and must be turned ON when the macro has finished

 

RR-2
Copy final output

Selecting and copying the final output to ensure the user can paste it after the macro ends i.e. pasting a table that was generated to a power point presentation

 

RR-3
Where macro runs

Macro runs on the currently opened sheet in Excel

 

RR-4
Clear All/Select All
By default selected the option “Clear all” is enable. If the user clicks on it then all selected products should be unselected. And the bottom name will be “Select All“

When the bottom is  “Select all”. If user clicks on it then all remaining product will be selected automatically.  

RR-5
Font type
Pop-up menu for the user to choose the font type 
By default: Trebuchet MS , Regular , 8

RR-6
Colour menu 

Colour- Pop Up for user to choose the colour

RR-7
Adjust the Userform elements to fit on Laptop Screen.

 

RR-8
Sheet name
The new sheet created by the macro should be named the sheet same as the macro name
Example: “Ingredient list“

 

Multiple Run versions
Is enable and for each time the macro should add V#

V1 , V2 , V3

At the end 



Key Features
Feature 1: Multi or Grid answers in one column 
Description: Answer codes are collated into one column

Benefit: Data can be imported to QPS

Feature 2: Original data is untouched
Description: New sheets are created, original data is untouched

Benefit: Original data from Forsta must exist. Allows the user to run comparisons when needed.

Feature 3: Summary of questions processed
Description: A new sheet is created showing which questions were processed by the macro

Benefit: A quick summary to verify the macro worked fine

Feature 4: Open ends in separate sheet
Description: A new sheet with open ends is created

Benefit: Gives flexbility to DP as they need open ends separate from all dat


BPIs
Security: Migrated code to C# to enhance IT security

Simplification: Combined two old macros into one. Old macros were called “All Multicoding” and “New Multicoding”

UI revamped: Old macro had a User Interface that wasn’t useful, we removed 3 user forms and simplified de userform. We are saving clicks from the process every time the macro runs

Support: Macros works for both main and loop data files

Efficiencies leading to time savings:

Old macro forced the user to choose one question at a time. Current macro will process all questions found

Identify question tags supported automatically for both Multi and Grid

Single column added in per question is highlighted with a colour, making it simple to the user to identify the output
Column header named with the question processe



    	A116. Macro path and UI (C)
Data to test
Data to run the test for Binary 

 Knorr Pork Cube P329356 All Multicoding - Before Macro.xlsx   

Old macro data output for Binary - can be used to compare results 

 Knorr Pork Cube P329356 All Multicoding - After Macro.xlsx  

Data to run the test for Scores

 Knorr Pork Cube P329356 New Multicode - Before Macro.xlsx 

Old macro data output for Scores - can be used to compare results 

Knorr Pork Cube P329356 New Multicode - After Macro.xlsx 


User Story Properties
ID

A116

User Story Description

As the user,

I want to run a macro to collate all Multi or Grid questions into single columns

So that DP can use the data to import into QPS


Functionality Description
Preconditions

File must have at least one Multi or Grid question

SERIAL must be the header of the first column in the data file

A. Reusable Requirements | RR 3
 

Path: MMR Group Macros → DP Team → Data → All Multicoding

Acceptance Criteria

I want to access the macro on the {correct path}

I want to {remove UI elements}

I want to {show userform}

I want to {validate serial column}


Domain Logic

Display Logic

correct path

Update the following path on Excel

MMR Group Macros → DP Team → Data → All Multicoding

Put it at the top of the list within “Data”

NOTE: For testing purposes, the macro should be placed on a separate ribbon 

Test QA Macro → All Multicoding

No changes to MMR Group Macros are allowed until the macro is tested and uploaded to Bitbucket. This setup ensures the macro can be installed, tested, and uninstalled without causing issues with live macros.



remove UI elements

The old macro shows 4 UI forms: Form 2, Form 3, Form 4 are no longer needed so remove them all. UI Old (Design)

NOTE: info from the UI forms is still needed to run the macro but we no longer need the interfaces

“Use underscore” - Multis and Grids always have underscore to identify each answer code

“Run split opens/_others macro” - Macro to always create a separate sheet with Open ends

“Initial columns to keep” must be 1

On Form 3 the user always selected “Yes”


Macro should NOT display any user forms at all


show userform

Update the only user form that’s left (see Form 1 from {remove UI elements})

We only need the Instructions AND the Data type selection. Everything else from the old macro can be removed.

Instructions to be: “This macro will create a single column containing the combined responses for a set of multicode responses from every Multi or Grid question found in the file. The first column of the file must be called SERIAL and all columns must have headers.”

Data type selection needs two options, user can choose only one of them

Binary (Multi questions) - Option to be selected by default

Scores (Grid questions)

NOTE on questions tags

For Binary, Multi question tags supported are: _om, _omos, _al 

For Scores, Grid question tags supported are:  _aag, _adg, _bvg, _eag, _erg, _fbg, _frg, _ftg, _itg, _jrg, _keyadg, _ndg, _grid (_og), _opg, _pig, _ppg, _prg, _reg, _sbg, _sug



validate serial column 

SERIAL must be the header of the first column in the data file. If that’s not the case, show error message “SERIAL must be the header of the first column”



Test Cases
Test Case

Actions/Steps

Expected Result

1

Macro path is ok

MMR Group Macros → DP Team → Data → All Multicoding

2

Testing macro path is on separate ribbon

Test QA Macro → All Multicoding

3

Userform shows instructions and two options to choose from

UI revamped

4

SERIAL must be the header of the first column in the data file

Show error if not true



		A122. Multicode


User Story Properties
ID

A122

User Story Description

As the user,

I want to multicode all Multi or Grid questions into one column per question

So that DP can use the data for the QPS software


Functionality Description
Preconditions

File must have at least one Multi or Grid question

SERIAL must be the header of the first column in the data file

Acceptance Criteria

I want to {multicode the multis}

I want to {multicode the grids}

I want to add a {summary of the multicode}




Domain Logic

Display Logic

multicode the multis

Run only if “Binary (Multi questions)” option is chosen at UI

A Multi question from Forsta is split in multiple columns, one per answer code. Example below with Q30_om with answers codes 1 to 8


0 OR nothing means the answer was not selected

1 means the answer was selected - this is the one we care about

We need ONE column per Multi question found in the sheet “Original No Opens”. To do that

Make a copy of the “Original No Opens” and call it “Multicoded”

For each Multi question found

Create a new column right after the question found. Format the new column added in

Background colour to be yellow

Column header to be the question ID followed by “_multicode” i.e. Q30_opg_multicode

To fill in each row for the new column, go through each answer code to find which codes were selected = 1 (highlighted pink in the example)

On the new multicoded column, add the answer codes that were selected, separated by ;


multicode the grids

Run only if “Scores (Grid questions)” option is chosen at UI

A Grid question from Forsta is split in multiple columns, one per answer code.  Example below with Q9_adg with answers codes 1 to 6


We need ONE column per Grid question found in the sheet “Original No Opens”. To do that

Make a copy of the “Original No Opens” and call it “Multicoded”

For each Grid question found

Create a new column right after the question found. Format the new column added in

Background colour to be orange

Column header to be the question ID followed by “_multicode” i.e. Q9_opg_multicode

To fill in each row for the new column, go through each answer code that has a value 

On the new multicoded column, add all the answer codes that were selected, separated by ;

summary of the multicode

Create a new sheet called “Multicode Summary” and add two columns

Column A 

Header “Multicode Question”

Add all the multicoded questions, one per row

Column B

Header “Questions feeding into multicoded”

Add the first answer code from the question i.e. Q30_om_1

From column C onwards, add all answer codes from the question i.e. Q30_om_2 on column C, Q30_om_3 on column D, etc


Test Cases
Test Case

Actions/Steps

Expected Result

1

Multis or Grids are multicoded

Each question added to new single column, multicoded AND sheet is called Multicoded

2

Multicoded summary sheet added

Multicode Summary sheet 

3

Binary works for multi question tags supported: _om, _omos, _al

 

4

Scores works for Grid question tags supported:  _aag, _adg, _bvg, _eag, _erg, _fbg, _frg, _ftg, _itg, _jrg, _keyadg, _ndg, _grid (_og), _opg, _pig, _ppg, _prg, _reg, _sbg, _sug





		A117. Create new sheets

User Story Properties
ID

A117

User Story Description

As the user,

I want to create new sheets 

So that DP can use the data for the QPS software


Functionality Description
Preconditions

File must have at least one Multi or Grid question

SERIAL must be the header of the first column in the data file

Acceptance Criteria

I want to {multicode the multis}

I want to add a {summary of the multicode}




Domain Logic

Display Logic

keep original data

Macro runs on the currently opened sheet in Excel.

Original data sheet must be kept so make a copy of the sheet and call it “Original”

Original data sheet untouched and called “Original”


resolve open ends

Open ended questions require a few modifications. 

Open end tags are _oe, _oem, _other 

Make a copy of the original sheet and call it “Original No Opens” 

Create a new sheet called “Opens”

Copy column SERIAL as the first column

Copy all columns with open end tags  

Remove all columns with open end tags from sheet “Original No Opens” 


Test Cases
Test Case

Actions/Steps

Expected Result

1

Keep origina data sheet

Original data sheet kept and called “Original”

2

Resolve open ends 

Data sheet called “Original No Opens” AND contains no open ends

Data sheet called “Opens” created

