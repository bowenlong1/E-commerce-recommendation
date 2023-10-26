
data d0;
format contact_dt date9.;
infile "/opt/SAS/SAS_data/projects/DATASCIENCE/RPT/dev/Custom_Data/AAA_Data Science Projects/Collections/Data/4660 dialer file/GMF_Consumer_APR_CHLNGR_&key0..dat" dlm='|' dsd truncover firstobs= 2;
length project $120. acct_nbr $120.
custm_key1 $12. ;
input project acct_nbr custm_key1;
day_key = &key0.;
contact_dt = input(put(&key0.,8.),YYMMDD8.) + 1;
loan_acct_nbr = input(substr(acct_nbr,length(acct_nbr)-11,12),12.);
run;
