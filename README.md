data df1;
set df;
format dt real_dt contact_dt date9.;
dt = input(put(day_key,8.),YYMMDD8.);
real_dt = dt + 1;
contact_dt = real_dt + 1;
run;
