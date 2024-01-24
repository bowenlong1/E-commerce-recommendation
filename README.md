%macro create_acct_table(piece_start, piece_end, output_table);
    proc sql;
    create table &output_table as 
    select a.*,
    %do i = &piece_start %to &piece_end;
        b&i..dpd as dpd&i.
    %end;
    from acct a
    %do i = &piece_start %to &piece_end;
        left join all_dpd b&i.
        on a.loan_acct_nbr = b&i..loan_acct_nbr
        and a.dt + &i. = b&i..dt
    %end;
    ;
    quit;
%mend;

%create_acct_table(1, 20, acct_p1)
%create_acct_table(21, 40, acct_p2)
%create_acct_table(41, 60, acct_p3)
%create_acct_table(61, 80, acct_p4)
%create_acct_table(81, 100, acct_p5)
%create_acct_table(101, 120, acct_p6)
