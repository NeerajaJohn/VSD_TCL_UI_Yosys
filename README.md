# VSD_TCL_UI_Yosys

## 5 Day workshop by VSD : TCL beginner to advanced training  
This repo is created as part of 5 day workshop on TCL beginner to advanced training, provided by **VSD**(VLSI System Design) by **Kunal Ghosh**. Workshop focussed on creation of a TCL tool box(a user interface) to accept a .csv file as input and return the reprt of the design using Yosys and Opentimer.

The workshop proceeds by following daily subtasks to create the User Interface tool step by step. The works are done in a Virtual Box which came with Open source tools **Yosys Synthesis Suite** and **OpenTimer STA** Tool

<details>
<summary><strong>Day 1: Introduction and VSDSYNTH Toolbox Usage</strong></summary>
  
  The overall function requirement of the tool we are designing was discussed in this day's workshop. We build a TCL tool box which takes a csv file as an input and gives a timing result  output after running through synthesis and timing tools. The tasks followed for this purpose are given below. 
  
  - ##### Task 1: Create a command (for example, vsdsynth) and pass .csv files from UNIX shell to TCL script  
  - ##### Task 2:Converting all inputs to format [1]and SDC format, then passing them to the synthesis tool Yosys
  - ##### Task 3:Convert format [1] and SDC to format [2] and pass them to the timing tool 'Opentimer'.
  - ##### Task 4:Generate an output report with the timing results
  These tasks are covered in the workshop dats by sub tasks. I have linked the specific subtasks done throughout the workshop.
  ##### Task 1 Subtasks:
   
 - <details>
   <summary><strong>Create Command (vsdsynth) and pass csv file from UNIC shell to Tcl script</strong></summary>

    Steps :
     - Created a UNIX script named "tcl_synth" by typing the following in a terminal in vsdsynth folder 
  
       ```bash
       vim tcl_synth
       ```
       > Let the system know that its a UNIX script
 
       ```bash
       #!/bin/tcsh -f
       ```
       <img width="1357" height="757" alt="image" src="https://github.com/user-attachments/assets/9b0bdfe5-525f-45cd-a2c8-6989316919c3" />
       

     - Create Logo for the tool(The file tcl_synth is going to be a tcl tool for synthesis and analysing using the commands to be written in the file tcl_synth created now.

       ```bash
       echo                    "TTTTTTT   CCCCC    L               SSSSSS   Y       Y   N     N  TTTTTTT  H     H"
       echo                    "   T     C     C   L              S          Y     Y    NN    N     T     H     H"
       echo                    "   T     C         L              S           Y   Y     N N   N     T     H     H"
       echo                    "   T     C         L       ====    SSSSS       YYY      N  N  N     T     HHHHHHH"
       echo                    "   T     C         L                    S       Y       N   N N     T     H     H"
       echo                    "   T     C     C   L                    S       Y       N    NN     T     H     H"
       echo                    "   T      CCCCC    LLLLLLL         SSSSS        Y       N     N     T     H     H"
       echo
       echo
       echo                    " A TCL tool created by Neeraja John following VSD TCL Beginner to Advanced Workshop"
      
       ````
      

    - Add execute permission using following line

     ```bash
     chmod +x tcl_synth
     ```
    
     <img width="1361" height="768" alt="image" src="https://github.com/user-attachments/assets/cd284f92-689a-454d-823d-220f9b1432ac" />

    - Next create a variable named "my_work_dir" and assign to it the absolute path of the current working directory. The pwd command returns the full path of the directory where the Tcl script is currently executing
  
      ```bash
      set my_work_dir [pwd]
      ```
    - Next add a line to accept the csv file as input arguement. The below command executes a Tcl script named "tcl_synth.tcl" using the Tcl shell interpreter (tclsh) and passes the first command-line argument to the script.
     ```bash
     tclsh tcl_synth.tcl  $argv[1]
     ```
    - Next to make the tool user friendly, we can give several error scenarios like the following:
      - No csv file given
      - .csv file doesnot exist in working folder
      - User types -help
      To address these issues, we can check conditions using if statements and print out messages to guide the user.
     ```bash
      if ($#argv != 1) then
	      echo "Info : Please Provide the csv file"
	      exit 1
      endif
      if (! -f $argv[1] || $argv[1] == "-help") then
	      if ($argv[1] == "-help") then
		      echo USAGE: ./tcl_synth \<csv file\>
      		echo
      		echo 		where \<csv file\> consists of 2 columns
      		echo
      		echo           	\<Design Name\> is the name of top level module 
      		echo
      		echo            \<Output Directory\> is the name of Output Directory where you want to dump synthesis script, synthesized netlist and timing reports
      		echo 
      		echo             \<Early Libary Path\> is the file path of the early cell libary to be used for STA
      		echo
          echo             \<Late Libary Path\> is the file path of the late cell libary to be used for STA
		      echo
          echo             \<Constraints file\> is the file path of constraints to be used for STA
	      else 
		      echo "ERROR: Cannot find the CSV file $argv[1]. Exiting"
	     endif
     else
          tclsh tcl_synth.tcl  $argv[1]
     endif
     ```
  

</details>




<details>
  <summary><strong>Day 2: Variable Creation and Processing Constraints from CSV</strong></summary
                                                                                          
  - ##### Variable Creation and Processing Constraints from CSV 
  Task 1
</details>


<details>
  <summary><strong>Day 3: Processing clock and input constraints</strong></summary>

  Task 1
</details>




<details>
  <summary><strong>Day 4: Complete Scripting and Yosys Synthesis Introduction</strong></summary>

  Task 1
</details>


<details>
  <summary><strong>Day 5: Advanced Scripting Techniques and Quality of Results Generation</strong></summary>

  Task 1
</details>
