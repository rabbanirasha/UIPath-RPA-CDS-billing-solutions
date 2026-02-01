Files that should be kept in this folder (rpa_input\) -
----------------------------------------------------

1. attach1.xlsx
2. attach2.xlsx
3. susp.xlsx
4. dpinfo.xlsx

5. attach1.pdf
6. attach2.pdf
7. susp.pdf
8. susplist.pdf


How do I start
---------------

1. Rename the files from the .NET app to the ones mentioned above.
2. Remove the header at the bottom row from all files.
3. In the susp.xlsx file, 
	-the first column (A) is the DPID.
	-the second column (B) is the number of BOs of each DPID.
	-the third column (C) is B/36.
	-the fourth column (D) is INT(C).
	-the fifth column(E) is D+1. 
	-E is the no of pages of susplist for each DPID.
	