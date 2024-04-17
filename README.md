data exp3;
    set exp2;
    format equity_risk_grp $20.;
    drop var1;
    rand = input(random_num, best.);
    
    /* Determine equity_risk_grp */
    if equity < -10000 then equity_risk_grp = 'F2: High';
    else equity_risk_grp = 'F1: Low';

    /* Determine new_pay_grp */
    if pay < 0.2049 then new_pay_grp = 'P1: Low';
    else if pay <= 0.3482 then new_pay_grp = 'P2: Med';
    else new_pay_grp = 'P3: High';
    
    /* Filter based on day_key */
    where day_key >= 20231001;

    /* Initialize holdout variables */
    contrl_call = 1;
    test0_call = 1;
    test1_call = 1;
    test2_call = 1;

    /* Calculate holdout values */
    if dpd in (46, 51, 56) then test0_call = 0;

    if equity_risk_grp = 'F1: Low' then do;
        if new_pay_grp = 'P1: Low' then do;
            if dpd in (46, 48, 50, 52, 54, 56, 58) then test1_call = 0;
        end;
        else if new_pay_grp = 'P2: Med' then do;
            if dpd in (47, 49, 51, 53, 55) then test1_call = 0;
        end;
        else if new_pay_grp = 'P3: High' then do;
            if dpd in (46, 48, 50, 52) then test1_call = 0;
        end;
    end;
    else if equity_risk_grp = 'F2: High' then do;
        if new_pay_grp = 'P1: Low' then do;
            if dpd in (47, 51, 57) then test1_call = 0;
        end;
        else if new_pay_grp = 'P2: Med' then do;
            if dpd in (46, 52) then test1_call = 0;
        end;
        else if new_pay_grp = 'P3: High' then do;
            if dpd in (50) then test1_call = 0;
        end;
    end;

    if equity_risk_grp = 'F1: Low' then do;
        if new_pay_grp = 'P1: Low' then do;
            if dpd in (47, 49, 51, 53, 56, 57) then test2_call = 0;
        end;
        else if new_pay_grp = 'P2: Med' then do;
            if dpd in (48, 50, 52, 54, 56, 57) then test2_call = 0;
        end;
        else if new_pay_grp = 'P3: High' then do;
            if dpd in (47, 49, 51, 53, 56, 57, 58) then test2_call = 0;
        end;
    end;
    else if equity_risk_grp = 'F2: High' then do;
        if new_pay_grp = 'P1: Low' then do;
            if dpd in (50, 54) then test2_call = 0;
        end;
        else if new_pay_grp = 'P2: Med' then do;
            if dpd in (54, 55) then test2_call = 0;
        end;
        else if new_pay_grp = 'P3: High' then do;
            if dpd in (54, 55, 56) then test2_call = 0;
        end;
    end;

run;
