* Automates billing of CDBL by taking custom input and feeding that to URL parameter to get numerous CDS invoices.
* Splits the following pdfs based on spreadsheet data:  
 	- susp (suspension) invoice,  
 	- susp list,  
 	- attachment 1  
 	- attachment 2  
* What required 500+ repetitions of a step amongst other steps now requires only one step.

**Total CDS Billing solutions**

Files that are needed for input:  attach1.xlsx |  attach2.xlsx | susp.xlsx | dpinfo.xlsx | attach1.pdf | attach2.pdf | susp.pdf | susplist.pdf  

* The xlsx files specify how the pdf files are split and feeds parameter to URL for generating invoices. The URL is http://10.64.15.2:8889/reports/rwservlet?report=D:\\\\Accounts\_10g\\\\party\_ledger10g\\\\invoice\_printing\_susp\_dup\_email.rdf\&desformat=PDF\&destype=CACHE\&userid=billing/billing@cdblldb
* For example, if you have in dpinfo.xlsx entered 10100, 10200, 10300 and so on, running the workflow sequence will -  
 	- display a custom html input requiring 'bill date' and 'for month'  
 	- if 'bill date' and 'for month' values are given and 'generate' is clicked,  
 	- the RPA fetches [URL]\&mnyr=**for\_month**\&bill\_date=**bill\_date**\&dp\_from=**10100,** and downloads the pdf. The pdf is saved in the respective folder.  
 	- the cycle is repeated for the next entries 10200, 10300 and so on and the "*\&dp\_from="* parameter changes accordingly.  
 	- So as there are usually 500 entries, 500 pdfs will be downloaded automatically, eliminating strenous repetitive manual work and reducing overall completion time significantly.  

* Other xlsx files specify how the pdf files should split. Only the number of sub-entries for each entry can be retrieved from CDS (depository system), eg. only the number of BO accounts for each DP can be known. Each page of a DP pdf has 36 entries of BO accounts so if number of BO accounts is divided by 36, number of pages for every DP can be determined.
* For example, if the xlsx says  10100 - 10, 10200 - 50, 10300 - 75 and so on, then the RPA splits the pdf from page 1 to 10 and names it 10100\_[remaining identifier].pdf, splits the pdf from page 11 to 50 and names it 10200\_<remaining identifier>.pdf and so on.

* How the xlsx files are structured (eg. susp.xlsx):  
 	- the first column (A) is the DPID.  
 	- the second column (B) is the number of BOs of each DPID.  
 	- the third column (C) is B/36.  
 	- the fourth column (D) is INT(C).  
 	- the fifth column(E) is D+1, which is the no of pages for each DPID.  

**AAMF RPA**

This is just a simple pdf splitter which is also a part of *Total CDS Billing solutions.* Just the same like before, the xlsx specifies how the pdf should split and saves the splits into respective folder.

