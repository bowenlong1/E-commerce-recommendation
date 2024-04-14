proc sql;
    create table fcall as 
    select loan_acct_nbr, day_key, workload_dt, sum(oc_call) as oc_call
    from (
        select loan_acct_nbr, day_key, workload_dt, oc_call
        from ic.apr46_octjan24
        where day_key <= 20240101 /* Adjust the upper bound of the day_key range for the first dataset */
    ) as dataset1
    union all
    select loan_acct_nbr, day_key, workload_dt, sum(oc_call) as oc_call
    from (
        select loan_acct_nbr, day_key, workload_dt, oc_call
        from ic.apr46_janapr24
        where day_key > 20240101 /* Adjust the lower bound of the day_key range for the second dataset */
    ) as dataset2
    group by 1, 2, 3;
quit;
