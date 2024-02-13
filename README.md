/* Create quantile buckets for dpd_3week, since_last_pmt_day, and days_to_next_pmt */
proc rank data=port2 groups=3 out=port2_ranked;
   var dpd_3week since_last_pmt_day days_to_next_pmt;
   ranks dpd_3week_rank since_last_pmt_day_rank days_to_next_pmt_rank;
run;

/* Create f1_group column with quantile combinations */
data port2_ranked;
   set port2_ranked;
   f1_group = cats('dpd', dpd_3week_rank, '-last', since_last_pmt_day_rank, '-next', days_to_next_pmt_rank);
run;

/* Create f1 column with 3 values */
data port2_ranked;
   set port2_ranked;
   if f1_group in ('dpd3-last3-next3', 'dpd2-last1-next3', 'dpd3-last1-next3', 'dpd3-last1-next2', 'dpd3-last2-next2', 'dpd3-last1-next1', 'dpd3-last3-next2', 'dpd3-last2-next3') then f1 = 'F1';
   else if f1_group in ('dpd1-last3-next3', 'dpd1-last3-next2', 'dpd2-last3-next2', 'dpd2-last1-next2', 'dpd2-last3-next1', 'dpd1-last1-next2', 'dpd3-last3-next1', 'dpd1-last1-next3', 'dpd2-last2-next2', 'dpd1-last2-next2', 'dpd1-last2-next3') then f1 = 'F2';
   else if f1_group in ('dpd1-last1-next1', 'dpd2-last1-next1', 'dpd2-last2-next1', 'dpd1-last3-next1', 'dpd1-last2-next1', 'dpd3-last2-next1', 'dpd2-last3-next3', 'dpd2-last2-next3') then f1 = 'F3';
run;

