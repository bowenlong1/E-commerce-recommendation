data exp2;
    set exp1;
    format fake_equity_risk_grp $20.;
    drop var1;
    rand = input(random_num, best.);
    
    /* Determine fake_equity_risk_grp */
    if rand >= 80 then fake_equity_risk_grp = 'F2: High';
    else fake_equity_risk_grp = 'F1: Low';
	if pay_grp = 'high' then pay_grp2 = 'P1: High'; 
	else if pay_grp = 'med' then pay_grp2 = 'P2: Med';
	else pay_grp2 = 'P3: Low';
    
    /* Filter based on day_key */
    where day_key >= 20231001;

  
    contrl_holdout = 0;

    /***holdout for test0***/
        if dpd in (46, 51, 56) then test0_holdout = 1;
        else test0_holdout = 0;

	/***holdout for test1***/
        if fake_equity_risk_grp = 'F1: Low' then do;
            if pay_grp2 = 'P1: High' then do;
                if dpd in (46, 48, 50, 52, 54, 56, 58) then test1_holdout = 1;
                else test1_holdout = 0;
            end;
            else if pay_grp2 = 'P2: Med' then do;
                if dpd in (47, 49, 51, 53, 55) then holdout = 1;
                else holdout = 0;
            end;
            else if pay_grp2 = 'P3: Low' then do;
                if dpd in (46, 48, 50, 52) then holdout = 1;
                else holdout = 0;
            end;
        end;
        else if fake_equity_risk_grp = 'F2: High' then do;
            if pay_grp2 = 'P1: High' then do;
                if dpd in (47, 51, 57) then holdout = 1;
                else holdout = 0;
            end;
            else if pay_grp2 = 'P2: Med' then do;
                if dpd in (46, 52) then holdout = 1;
                else holdout = 0;
            end;
            else if pay_grp2 = 'P3: Low' then do;
                if dpd in (50) then holdout = 1;
                else holdout = 0;
            end;
        end;
    end;


	/***holdout for test2***/
        if fake_equity_risk_grp = 'F1: Low' then do;
            if pay_grp2 = 'P1: High' then do;
                if dpd in (47, 49, 51, 53, 56, 57) then test2_holdout = 1;
                else holdout = 0;
            end;
            else if pay_grp2 = 'P2: Med' then do;
                if dpd in (48, 50, 52, 54, 56, 57) then holdout = 1;
                else holdout = 0;
            end;
            else if pay_grp2 = 'P3: Low' then do;
                if dpd in (47, 49, 51, 53, 56, 57, 58) then holdout = 1;
                else holdout = 0;
            end;
        end;
        else if fake_equity_risk_grp = 'F2: High' then do;
            if pay_grp2 = 'P1: High' then do;
                if dpd in (50, 54) then holdout = 1;
                else holdout = 0;
            end;
            else if pay_grp2 = 'P2: Med' then do;
                if dpd in (54, 55) then holdout = 1;
                else holdout = 0;
            end;
            else if pay_grp2 = 'P3: Low' then do;
                if dpd in (54, 55, 56) then holdout = 1;
                else holdout = 0;
            end;
        end;
    end;
run;
