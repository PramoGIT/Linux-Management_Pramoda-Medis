## Linux Management_Pramoda Medis

# Assignment 05

Make a script and add it to cron

Using crontab automation, let the script "print.sh" run every 12 hours, that is, twice a day

Write the script "print.sh", that adds one line to file "diskspace.txt" reporting home directory size and date, example:
        3596 Jan 31 13:26:11 EET 2025

Let the script run minimum 6 times (there are at least 6 lines in file "discspace.txt" now)

Now write a command using awk-tool to find a line containing maximum size from "discspace.txt" and print it. Example output:
        Max=3596, at Jan 31 13:26:11 EET 2025



------------------

## Create the print.sh Script
The script appends the home directory size and current date to diskspace.txt.


### Summary of Commands
1. Script Creation:

    du -s $HOME

![alt text](01.png)

![alt text](02.png)

Next we need to print the date in the format Jan 31 13:26:11 EET 2025,

    date '+%b %d %H:%M:%S %Z %Y'

![alt text](02.1time.png)

%b → Abbreviated month name (e.g., Feb for February).

%d → Day of the month (e.g., 10 for the 10th day).

%H → Hour in 24-hour format (e.g., 14 for 2 PM).

%M → Minutes (e.g., 45).

%S → Seconds (e.g., 30).

%Z → Time zone abbreviation (e.g., UTC, EST).

%Y → Four-digit year (e.g., 2025).

02. Now we need to append this data and save it in the diskspace.txt file

    #!/bin/bash

    ### Get the size of the home directory in KB
    HOME_SIZE=$(du -s $HOME | awk '{print $1}')

    ### Get the current date and time
    CURRENT_DATE=$(date '+%b %d %H:%M:%S %Z %Y')

    ### Append the information to diskspace.txt
    echo "$HOME_SIZE $CURRENT_DATE" >> diskspace.txt

![alt text](03.png)

03. Cron Job:

    crontab -e
        # Add: 0 */12 * * * /path/to/print.sh

![alt text](04.01Contrab.png)

Add the following lines to execute the code in every 12 hours

    0 */12 * * * /home/medis/print.sh

Since I need to test, generated it in every 1 min interval,

Test the results

![alt text](04.png)


04. Now write a command using awk-tool (manual) to find a line containing maximum size from "discspace.txt" and print it. Example output:

Max=3596, at Jan 31 13:26:11 EET 2025

![alt text](05.png)

    awk '{if($1 > max) {max=$1; line=$0}} END {print "Max=" max ", at " substr(line, index(line, $2))}' diskspace.txt



This will check if the $1 is greater than the max value, ($1 is the value of the first field),

If so it assign the $1 value to max, and save the current line in line variable.

Read all lines

    awk '$1 {print $0}' diskspace.txt

Read 1st Field only

    awk '$1 {print $1}' diskspace.txt

![alt text](06ReadFirstFieldOnly.png)

To print at the end of the operation,
    
    awk 'END {print $1}' diskspace.txt

![alt text](07LastLine.png)

To print the max value at the end of the operation,
    
    awk '{if($1>max){max=$1; line=$0}} END {print max}' diskspace.txt

![alt text](08.png)

To print the max value and the line data at the end of the operation,
    
    awk '{if($1>max){max=$1; line=$0}} END {print max, " and the Data is ", line }' diskspace.txt

![alt text](09.png)

Since we need to print only sub set of the line data we use substr and indexing

    substr(line, index(line, $2))

![alt text](10SyntxError.png)

So the final awk command is
    
    awk '{if($1 > max) {max=$1; line=$0}} END {print "Max=" max ", at " substr(line, index(line, $2))}' diskspace.txt

![alt text](13Final.png)

output of command "echo your_name"

    "Pramoda Medis"

![alt text](14.png)




