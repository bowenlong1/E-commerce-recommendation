proc sql;
    create table accts_p1 as 
    select a.*,
        b1.dpd as dpd1,
        b2.dpd as dpd2,
        b3.dpd as dpd3,
        b4.dpd as dpd4,
        b5.dpd as dpd5,
        b6.dpd as dpd6,
        b7.dpd as dpd7,
        b8.dpd as dpd8,
        b9.dpd as dpd9,
        b10.dpd as dpd10,
        b11.dpd as dpd11,
        b12.dpd as dpd12,
        b13.dpd as dpd13,
        b14.dpd as dpd14,
        b15.dpd as dpd15,
        b16.dpd as dpd16,
        b17.dpd as dpd17,
        b18.dpd as dpd18,
        b19.dpd as dpd19,
        b20.dpd as dpd20
    from acct a
    left join all_dpd b1 on a.loan_acct_nbr = b1.loan_acct_nbr and a.dt+1 = b1.dt
    left join all_dpd b2 on a.loan_acct_nbr = b2.loan_acct_nbr and a.dt+2 = b2.dt
    left join all_dpd b3 on a.loan_acct_nbr = b3.loan_acct_nbr and a.dt+3 = b3.dt
    left join all_dpd b4 on a.loan_acct_nbr = b4.loan_acct_nbr and a.dt+4 = b4.dt
    left join all_dpd b5 on a.loan_acct_nbr = b5.loan_acct_nbr and a.dt+5 = b5.dt
    left join all_dpd b6 on a.loan_acct_nbr = b6.loan_acct_nbr and a.dt+6 = b6.dt
    left join all_dpd b7 on a.loan_acct_nbr = b7.loan_acct_nbr and a.dt+7 = b7.dt
    left join all_dpd b8 on a.loan_acct_nbr = b8.loan_acct_nbr and a.dt+8 = b8.dt
    left join all_dpd b9 on a.loan_acct_nbr = b9.loan_acct_nbr and a.dt+9 = b9.dt
    left join all_dpd b10 on a.loan_acct_nbr = b10.loan_acct_nbr and a.dt+10 = b10.dt
    left join all_dpd b11 on a.loan_acct_nbr = b11.loan_acct_nbr and a.dt+11 = b11.dt
    left join all_dpd b12 on a.loan_acct_nbr = b12.loan_acct_nbr and a.dt+12 = b12.dt
    left join all_dpd b13 on a.loan_acct_nbr = b13.loan_acct_nbr and a.dt+13 = b13.dt
    left join all_dpd b14 on a.loan_acct_nbr = b14.loan_acct_nbr and a.dt+14 = b14.dt
    left join all_dpd b15 on a.loan_acct_nbr = b15.loan_acct_nbr and a.dt+15 = b15.dt
    left join all_dpd b16 on a.loan_acct_nbr = b16.loan_acct_nbr and a.dt+16 = b16.dt
    left join all_dpd b17 on a.loan_acct_nbr = b17.loan_acct_nbr and a.dt+17 = b17.dt
    left join all_dpd b18 on a.loan_acct_nbr = b18.loan_acct_nbr and a.dt+18 = b18.dt
    left join all_dpd b19 on a.loan_acct_nbr = b19.loan_acct_nbr and a.dt+19 = b19.dt
    left join all_dpd b20 on a.loan_acct_nbr = b20.loan_acct_nbr and a.dt+20 = b20.dt;
quit;
