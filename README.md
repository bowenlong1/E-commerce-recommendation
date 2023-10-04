proc sql;
    create table combined as
    select 
        a.loan_acct_nbr, 
        a.dt as start_date,
        MIN(case when b.dt_sent between a.dt and a.dt+65 and rownum=1 then b.dt_sent else . end) as first_dt_sent,
        MIN(case when b.dt_sent between a.dt and a.dt+65 and rownum=2 then b.dt_sent else . end) as second_dt_sent,
        MIN(case when b.dt_sent between a.dt and a.dt+65 and rownum=3 then b.dt_sent else . end) as third_dt_sent
    from 
        dist_acct a
        left join (
            select 
                loan_acct_nbr, 
                dt_sent, 
                rownum
            from 
                (
                    select 
                        loan_acct_nbr, 
                        dt_sent,
                        monotonic() as rownum
                    from 
                        cred_rpt
                    order by loan_acct_nbr, dt_sent
                ) sub
            where rownum <= 3
        ) b
        on a.loan_acct_nbr = b.loan_acct_nbr 
        and b.dt_sent between a.dt and a.dt+65
    group by 
        a.loan_acct_nbr, 
        a.dt
    ;
quit;
