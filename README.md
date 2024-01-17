%macro combine_datasets(prefix, num);
data combined_&prefix.;
set 
%do i = 0 %to &num;
   &prefix.&i
%end;
;
run;
%mend;

/* Combine push datasets from 0 to 72 */
%combine_datasets(push, 72);

/* Combine email datasets from 0 to 72 */
%combine_datasets(email, 72);
