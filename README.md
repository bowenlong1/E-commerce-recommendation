/** Corrected logic for move46_m1 - move46_m12 **/
%do i = 1 %to 12;
    min&i = max&i - ((beg&i + input(put(m&i,8.),yymmdd8.) - input(put(b&i,8.),yymmdd8.)) - end&i - 1);
    
    if beg&i<46 and max&i>=46 then move46_m&i = 1;
    else if beg&i>=46 and min&i<46 and end&i>=46 then move46_m&i = 1;
    else move46_m&i = 0;
%end;
