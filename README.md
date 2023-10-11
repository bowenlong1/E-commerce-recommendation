proc sql;
    create table pmt65 as
    select cat, dpd,
        %do i=1 %to 65;
            avg(pm&i.) as avg_pm&i.
            %if i<65 %then %do;, %end;
        %end;
    from pmt_track2
    group by 1, 2;
quit;

28         proc sql;
29             create table pmt65 as
30             select cat, dpd,
31                 %do i=1 %to 65;
ERROR: The %DO statement is not valid in open code.
32                     avg(pm&i.) as avg_pm&i.
                                _
                                22
