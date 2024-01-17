data push;
infile "&idata2./EXP42_46_60_DPD_Push_Logs_&pullkey&i...txt" dlm='|' dsd truncover firstobs= 2;
length 
'Profile ID'n $120.
'Account Number'n $120. 
/*Address $120.*/
'Control population'n $1.
'Mobile App Label'n $120.
'Label'n $120. Status $12. ;
informat 'Event date'n DATETIME18.;
format 'Event date'n DATETIME18.;
input  'Profile ID'n 'Account Number'n 'Event date'n : ?? ANYDTDTM19. 'Control population'n 'Mobile App Label'n  Status 'Label'n ;
run;
