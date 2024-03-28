data dpd3;
    set dpd2; /* Replace 'your_dataset' with your actual dataset name */

    array beg{12} beg1-beg12;
    array max{12} max1-max12;
	array end{12} end1-end12;
    array move46_m{12} move46_m1-move46_m12;
    array at46_m{12} at46_m1-at46_m12;
    array e46_m{12} e46_m1-e46_m12;
	array pay_m{12} pay_m1-pay_m12;


    do i = 1 to 12;
        /* Compute move46_m */
        if beg{i} < 46 and max{i} >= 46 then move46_m{i} = 1;
        else move46_m{i} = 0;

        /* Compute at46_m */
        if beg{i} >= 46 then at46_m{i} = 1;
        else at46_m{i} = 0;

        /* Compute e46_m */
        if move46_m{i} = 1 or at46_m{i} = 1 then e46_m{i} = 1;
        else e46_m{i} = 0;

        /* Compute pay_m */
        if end{i} < max{i}  then pay_m{i} = 1;
        else pay_m{i} = 0;
    end;

    drop i;
if e46_m1=1 or
e46_m2=1 or
e46_m3=1 or
e46_m4=1 or
e46_m5=1 or
e46_m6=1 or
e46_m7=1 or
e46_m8=1 or
e46_m9=1 or
e46_m10=1 or
e46_m11=1 or
e46_m12=1 then e46 = 1; else e46 = 0;
run;
