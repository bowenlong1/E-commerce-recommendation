%macro create_pays(num);
    %do i = 1 %to &num;
        if (beg&i>0 and end&i< beg&i+input(put(m&i,8.),yymmdd8.) - input(put(b&i,8.),yymmdd8.)) or (beg&i = 0 and ebal&i<sba&i) then pay&i = 1; else pay&i = 0;
    %end;
%mend;

data your_data;
    set your_dataset;
    %create_pays(12);
run;

