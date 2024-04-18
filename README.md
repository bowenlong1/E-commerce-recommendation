28         data rep3;
29         set dpd2;
30         %create_pays(12);
31         payct = pay1+pay2+pay3+pay4+pay5+pay6+pay7+pay8+pay9+pay10+pay11+pay12;
32         e46_ct = sum(max1>=46, max2>=46, max3>=46, max4>=46, max5>=46, max6>=46, max7>=46,max8>=46, max9>=46, max10>=46,
32       ! max11>=46, max12>=46);
33         
34         /**correct this part**/
35         %do i = 1 %to 12;
ERROR: The %DO statement is not valid in open code.
36             min&i = max&i - ((beg&i + input(put(m&i,8.),yymmdd8.) - input(put(b&i,8.),yymmdd8.)) - end&i - 1);
               ___
               180
WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
37             if beg&i<46 and max&i>=46 then move46_m&i = 1;
                                              ________
                                              180
WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
38             else if beg&i>=46 and min&i<46 and end&i>=46 then move46_m&i = 1;
                                                                 ________
                                                                 180
WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
2                                                          The SAS System                             15:28 Thursday, April 18, 2024

WARNING: Apparent symbolic reference I not resolved.
WARNING: Apparent symbolic reference I not resolved.
ERROR 180-322: Statement is not valid or it is used out of proper order.

39             else move46_m&i = 0;
WARNING: Apparent symbolic reference I not resolved.
39             else move46_m&i = 0;
                    ________
                    180
ERROR 180-322: Statement is not valid or it is used out of proper order.

WARNING: Apparent symbolic reference I not resolved.
40         %end;
ERROR: The %END statement is not valid in open code.
41         /****/
42         if dpd7<53 then payd7 = 1; else payd7 = 0;
43         if dpd15<61 then payd15 = 1; else payd15 = 0;
44         if dpd24<70 then payd24 = 1; else payd24 = 0;
45         if dpd30<76 then payd30 = 1; else payd30 = 0;
46         run;
