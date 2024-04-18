%macro create_pays(num);
    %do i = 1 %to &num;
        if (beg&i>0 and end&i< beg&i+input(put(m&i,8.),yymmdd8.) - input(put(b&i,8.),yymmdd8.)) or (beg&i = 0 and ebal&i<sba&i) then pay&i = 1; else pay&i = 0;
    %end;
%mend;

data rep3;
set dpd2;
%create_pays(12);
payct = pay1+pay2+pay3+pay4+pay5+pay6+pay7+pay8+pay9+pay10+pay11+pay12;
e46_ct = sum(max1>=46, max2>=46, max3>=46, max4>=46, max5>=46, max6>=46, max7>=46,max8>=46, max9>=46, max10>=46, max11>=46, max12>=46);

/**correct this part**/
min1 = max1 - ((beg1 + input(put(m1,8.),yymmdd8.) - input(put(b1,8.),yymmdd8.) - end1 - 1)
if beg1<46 and max1>=46 then move46_m1 = 1 or if beg1>=46 and min1<46 and end1>=46 then move46_m1 = 1
else: move46_m1 = 0

/****/

if dpd7<53 then payd7 = 1; else payd7 = 0;
if dpd15<61 then payd15 = 1; else payd15 = 0;
if dpd24<70 then payd24 = 1; else payd24 = 0;
if dpd30<76 then payd30 = 1; else payd30 = 0;
run;
