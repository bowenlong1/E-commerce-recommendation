data exp1_filtered;
    set exp1;
    where day_key >= 20231001;
run;

proc univariate data=exp1_filtered noprint;
    var pay;
    output out=quantiles
        pctlpre=pct
        pctlpts=33 66;
run;

data exp1;
    set exp1;
    if pay < pct33 then new_pay_grp = 'P1: Low';
    else if pay <= pct66 then new_pay_grp = 'P2: Med';
    else new_pay_grp = 'P3: High';
run;

proc print data=exp1;
run;

