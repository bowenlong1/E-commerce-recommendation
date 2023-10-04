%macro generate_pm_vars;

    proc sql;
        create table pmt_track as 
        select a.loan_acct_nbr, a.dt
        
        %do i=1 %to 65;
            ,COALESCE(SUM (CASE WHEN b.process_dt < a.dt+&i. THEN b.TOTL_TRANSACT_AMT ELSE 0 END),0) AS pm&i.
        %end;
        
        from dist_acct a
        left join pmt_hist b 
        on a.loan_acct_nbr = b.partial_acct_nbr and a.dt <= b.process_dt 
        group by 1,2;
    quit;

%mend generate_pm_vars;

%generate_pm_vars;
