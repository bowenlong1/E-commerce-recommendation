data fca3;
    format contact_dt date9. exp_grp $20.;
    set IC.APR4660_ITER2_AUGOCT23
        IC.APR4660_ITER2_NOVJAN24
        IC.APR4660_ITER2_JANAPR24;
    
    contact_dt = dt + 1;
    rand = input(random_num, best.);
    where day_key >= 20231022;

    /* Creating period variable */
    if day_key <= 20240106 then period = 'p1';
    else if day_key <= 20240229 then period = 'p2';
    else period = 'p3';

    /* Logic for exp_grp variable */
    if period = 'p1' then do;
        if 20 <= rand <= 29 then exp_grp = 'test0';
        else if 30 <= rand <= 39 then exp_grp = 'test1';
        else if 40 <= rand <= 49 then exp_grp = 'test2';
        else exp_grp = 'control';
    end;
    else if period = 'p2' then exp_grp = 'none';
    else if period = 'p3' then do;
        if 0 <= rand <= 89 then exp_grp = '3day';
        else exp_grp = 'org';
    end;

run;
