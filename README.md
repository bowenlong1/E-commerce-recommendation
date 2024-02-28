proc sql;
create table chk2_dtl as
select exp_grp, count(*) as vol,
sum(adj_market_price_condition) as sum_price,
sum(loan_bal_amt) as sum_balance_amt,
calculated sum_price - calculated sum_balance_amt as equity,
calculated sum_price/calculated sum_balance_amt as equity_ratio,
(calculated sum_price/calculated sum_balance_amt) - .06 as equity_ratio_adj,
(calculated equity_ratio_adj*calculated sum_balance_amt) - calculated sum_balance_amt as equity_adj
from rt2_dtl
group by 1,2;
quit;
