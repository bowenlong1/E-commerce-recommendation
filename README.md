
Select specific time range:
with cte as (select ssid, count(packet_id) over (partition by ssid, mac_address) as num
from packet_rates
WHERE time_captured >= TIMESTAMP '2022-01-01 00:00:00' AND 
time_captured < TIMESTAMP '2022-01-01 00:10:00')
select ssid, max(num) as max_number_of_packages_sent
from cte
group by 1

specific date range:
where created_at >= DATE '2020-01-01' AND created_at < DATE '2020-01-06'

group by select min/max:
WITH fst AS (
  SELECT year(created_at) AS year, sum(amount-amount_refunded) AS pmt
  FROM annual_payments
  GROUP BY year
  HAVING year = (SELECT MIN(year(created_at)) FROM annual_payments)
)
https://www.interviewquery.com/questions/percentage-of-revenue-by-year
