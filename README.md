%macro create_pmt65_table;
proc sql;
    create table pmt65 as
    select cat, dpd,
	count(*) as vin,
        %do i=1 %to 65;
            avg(pm&i.) as avg_pm&i.,
			sum(pmt&i.) as sum_pmt&i.,
			sum(pmt&i.)/sum(acct_payoff_amt) as perc_pmt&i.
            %if &i < 65 %then %do;, %end;
        %end;
    from pmt_track2
    group by 1, 2;
quit;
%mend;

%create_pmt65_table;
