proc sql;
    create table pmt65 as 
    select cat, dpd, 
    
    %do i=1 %to 65;
        ,avg(pm&i.) as avg_pm&i.
    %end
    
    from pmt_track2
    group by 1,2,3;
quit;
