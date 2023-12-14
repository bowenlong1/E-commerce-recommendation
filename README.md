/* Sample Data (replace this with your actual data) */
data SampleData;
  input Value;
  datalines;
  25
  28
  30
  22
  24
  ;
run;

/* Procedure for Z-test */
proc univariate data=SampleData;
  var Value;
  histogram / normal; /* Optional: display histogram and normal curve */
  ods select Moments Tests;
run;
