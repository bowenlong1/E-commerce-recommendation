

data fca3;
format contact_dt date9. exp_grp $20.;
set 
IC.APR4660_ITER2_AUGOCT23
IC.APR4660_ITER2_NOVJAN24
IC.APR4660_ITER2_JANAPR24;
contact_dt = dt + 1;
rand = input(random_num,best.);
where day_key>=20231022;
/*if day_key<20240209 then imp = 'prev'; else imp = 'after';*/
if day_key<=20240106 
/***create period***/
if period = p1: 20231022-20240106
p2: 20240107 - 20240229
p3: 20240301 and above
/**logic for exp_grp***/
if period = p1 and  (case when random_num between 20 and 29 then 'test0'
when random_num between 30 and 39 then 'test1'
when random_num between 40 and 49 then 'test2'
else 'control' end as exp_grp)
if period = p2 then exp_grp = 'none';
if period = p3(case when rand between 0 and 89 then '3day'
else 'org' end as exp_grp);

run;
