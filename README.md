proc sql;
create table chk2_dtl as
select exp_grp, 
       count(*) as vol,
       sum(adj_market_price_condition) as sum_price,
       sum(loan_bal_amt) as sum_balance_amt,
       sum(adj_market_price_condition) - sum(loan_bal_amt) as equity,
       sum(adj_market_price_condition) / sum(loan_bal_amt) as equity_ratio,
       (sum(adj_market_price_condition) / sum(loan_bal_amt)) - 0.06 as equity_ratio_adj,
       ((sum(adj_market_price_condition) / sum(loan_bal_amt)) - 0.06) * sum(loan_bal_amt) - sum(loan_bal_amt) as equity_adj
from rt2_dtl
group by exp_grp;
quit;

