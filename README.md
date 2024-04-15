data exp2;
set exp1;
format fake_equity_risk_erp $20.;
drop var1;
rand = input(b.random_num,best.);
if rand>=80 then fake_equity_risk_erp = 'high';
else fake_equity_risk_grp = 'low';
where day_key>=20231001;

if exp_grp = 'control' then holdout = 0;
if exp_grp = 'test0' and dpd in (46,51,56) then holdout = 1; else if exp_grp = 'test0' and dpd not in (46,51,56) then holdout = 0;

/**for test1***/
if exp_grp = 'test1' and fake_equity_risk_grp = 'low' and pay_grp = 'high' then do;
	if dpd in (46,48,50,52,54,56,58) then holdout = 1;
	else holdout = 0;
	end;
else if exp_grp = 'test1' and fake_equity_risk_grp = 'low' and pay_grp = 'med' then do;
	if dpd in (47,49,51,53,55) then holdout = 1;
	else holdout = 0;
	end;
else if exp_grp = 'test1' and fake_equity_risk_grp = 'low' and pay_grp = 'low' then do;
	if dpd in (46,48,50,52) then holdout = 1;
	else holdout = 0;
	end;

else if exp_grp = 'test1' and fake_equity_risk_grp = 'high' and pay_grp = 'high' then do;
	if dpd in (47,51,57) then holdout = 1;
	else holdout = 0;
	end;
else if exp_grp = 'test1' and fake_equity_risk_grp = 'high' and pay_grp = 'med' then do;
	if dpd in (46,52) then holdout = 1;
	else holdout = 0;
	end;
else if exp_grp = 'test1' and fake_equity_risk_grp = 'high' and pay_grp = 'low' then do;
	if dpd in (50) then holdout = 1;
	else holdout = 0;
	end;

/**for test2***/
if exp_grp = 'test2' and fake_equity_risk_grp = 'low' and pay_grp = 'high' then do;
	if dpd in (47,49,51,53,56,57) then holdout = 1;
	else holdout = 0;
	end;
else if exp_grp = 'test2' and fake_equity_risk_grp = 'low' and pay_grp = 'med' then do;
	if dpd in (48,50,52,54,56,57) then holdout = 1;
	else holdout = 0;
	end;
else if exp_grp = 'test2' and fake_equity_risk_grp = 'low' and pay_grp = 'low' then do;
	if dpd in (47,49,51,53,56,57,58) then holdout = 1;
	else holdout = 0;
	end;

else if exp_grp = 'test2' and fake_equity_risk_grp = 'high' and pay_grp = 'high' then do;
	if dpd in (50,54) then holdout = 1;
	else holdout = 0;
	end;
else if exp_grp = 'test2' and fake_equity_risk_grp = 'high' and pay_grp = 'med' then do;
	if dpd in (54,55) then holdout = 1;
	else holdout = 0;
	end;
else if exp_grp = 'test2' and fake_equity_risk_grp = 'high' and pay_grp = 'low' then do;
	if dpd in (54,55,56) then holdout = 1;
	else holdout = 0;
	end;

run;
