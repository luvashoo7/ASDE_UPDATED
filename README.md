#Task-4 Bash

Use the attached sample TSV file: sample.tsv
Create a new TSV file (output.tsv) with:
The first column (Item Name) from the original file (sample.tsv)
Add an additional column in the end which has the line number of the item from the original file
Only include items whose name start with 'Xerox'
The rows are sorted by the item name. (ascending, alphabetical)
Once the file output.tsv is created, attach the o/p of the below command along with the generated file:

cat output.tsv | tee >(wc -l) | tee >(sha1sum) | tail -5


Note: You cannot use loops of any kind. Do this with a single line command. You can use the pipe operator.

Sample Output: (The first 3 lines of the output.tsv should look like this)
Xerox 1880	12784
Xerox 1880	12916
Xerox 1880	13334

#Answer:

Step 1: Download the sample TSV file

Step 2: Extract the first column and line numbers for 'Xerox' item with the following command
awk -F'\t' '$1 ~ /^Xerox/ {print $1, FNR}' sample.tsv > output.tsv

Step 3: Sort the rows by item name with the following command
sort -k1 output.tsv -o output.tsv

step 4: run this command & attach the output
cat output.tsv | tee >(wc -l) | tee >(sha1sum) | tail -5
<img width="325" alt="image" src="https://github.com/luvashoo7/ASDE_UPDATED/assets/61554374/395f8c0a-e3a4-4c62-8d4b-8ab8fecb7ef3">





#Task-5 Bash

Write a command to print all the groups of the owner of all the files in the current directory.

Note: You cannot use loops of any kind. Do this with a single line command. You can use the pipe operator.

#Answer:

ls -l | awk '{print $3}' | sort | uniq -d



