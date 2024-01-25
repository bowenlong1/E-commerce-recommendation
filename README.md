/* Assuming your dataset is named 'acct' */
proc surveyselect data=acct out=random_accounts method=urs n=1000 seed=12345;
run;
