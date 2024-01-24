proc sql;
    create table acct2 as 
    select a.*,
        b1.dpd as dpd1,
        b2.dpd as dpd2,
        b3.dpd as dpd3,
        b4.dpd as dpd4,
        b5.dpd as dpd5,
        b6.dpd as dpd6,
        b7.dpd as dpd7,
        b8.dpd as dpd8,
        b9.dpd as dpd9,
        b10.dpd as dpd10,
        b11.dpd as dpd11,
        b12.dpd as dpd12,
        b13.dpd as dpd13,
        b14.dpd as dpd14,
        b15.dpd as dpd15,
        b16.dpd as dpd16,
        b17.dpd as dpd17,
        b18.dpd as dpd18,
        b19.dpd as dpd19,
        b20.dpd as dpd20,
        b21.dpd as dpd21,
        b22.dpd as dpd22,
        b23.dpd as dpd23,
        b24.dpd as dpd24,
        b25.dpd as dpd25,
        b26.dpd as dpd26,
        b27.dpd as dpd27,
        b28.dpd as dpd28,
        b29.dpd as dpd29,
        b30.dpd as dpd30,
        b31.dpd as dpd31,
        b32.dpd as dpd32,
        b33.dpd as dpd33,
        b34.dpd as dpd34,
        b35.dpd as dpd35,
        b36.dpd as dpd36,
        b37.dpd as dpd37,
        b38.dpd as dpd38,
        b39.dpd as dpd39,
        b40.dpd as dpd40,
        b41.dpd as dpd41,
        b42.dpd as dpd42,
        b43.dpd as dpd43,
        b44.dpd as dpd44,
        b45.dpd as dpd45,
        b46.dpd as dpd46,
        b47.dpd as dpd47,
        b48.dpd as dpd48,
        b49.dpd as dpd49,
        b50.dpd as dpd50,
        b51.dpd as dpd51,
        b52.dpd as dpd52,
        b53.dpd as dpd53,
        b54.dpd as dpd54,
        b55.dpd as dpd55,
        b56.dpd as dpd56,
        b57.dpd as dpd57,
        b58.dpd as dpd58,
        b59.dpd as dpd59,
        b60.dpd as dpd60,
        b61.dpd as dpd61,
        b62.dpd as dpd62,
        b63.dpd as dpd63,
        b64.dpd as dpd64,
        b65.dpd as dpd65,
        b66.dpd as dpd66,
        b67.dpd as dpd67,
        b68.dpd as dpd68,
        b69.dpd as dpd69,
        b70.dpd as dpd70,
        b71.dpd as dpd71,
        b72.dpd as dpd72,
        b73.dpd as dpd73,
        b74.dpd as dpd74,
        b75.dpd as dpd75,
        b76.dpd as dpd76,
        b77.dpd as dpd77,
        b78.dpd as dpd78,
        b79.dpd as dpd79,
        b80.dpd as dpd80,
        b81.dpd as dpd81,
        b82.dpd as dpd82,
        b83.dpd as dpd83,
        b84.dpd as dpd84,
        b85.dpd as dpd85,
        b86.dpd as dpd86,
        b87.dpd as dpd87,
        b88.dpd as dpd88,
        b89.dpd as dpd89,
        b90.dpd as dpd90,
        b91.dpd as dpd91,
        b92.dpd as dpd92,
        b93.dpd as dpd93,
        b94.dpd as dpd94,
        b95.dpd as dpd95,
        b96.dpd as dpd96,
        b97.dpd as dpd97,
        b98.dpd as dpd98,
        b99.dpd as dpd99,
        b100.dpd as dpd100,
        b101.dpd as dpd101,
        b102.dpd as dpd102,
        b103.dpd as dpd103,
        b104.dpd as dpd104,
        b105.dpd as dpd105,
        b106.dpd as dpd106,
        b107.dpd as dpd107,
        b108.dpd as dpd108,
        b109.dpd as dpd109,
        b110.dpd as dpd110,
        b111.dpd as dpd111,
        b112.dpd as dpd112,
        b113.dpd as dpd113,
        b114.dpd as dpd114,
        b115.dpd as dpd115,
        b116.dpd as dpd116,
        b117.dpd as dpd117,
        b118.dpd as dpd118,
        b119.dpd as dpd119,
        b120.dpd as dpd120
    from acct a
    left join all_dpd b1 on a.loan_acct_nbr = b1.loan_acct_nbr and a.dt+1 = b1.dt
    left join all_dpd b2 on a.loan_acct_nbr = b2.loan_acct_nbr and a.dt+2 = b2.dt
    left join all_dpd b3 on a.loan_acct_nbr = b3.loan_acct_nbr and a.dt+3 = b3.dt
    left join all_dpd b4 on a.loan_acct_nbr = b4.loan_acct_nbr and a.dt+4 = b4.dt
    left join all_dpd b5 on a.loan_acct_nbr = b5.loan_acct_nbr and a.dt+5 = b5.dt
    left join all_dpd b6 on a.loan_acct_nbr = b6.loan_acct_nbr and a.dt+6 = b6.dt
    left join all_dpd b7 on a.loan_acct_nbr = b7.loan_acct_nbr and a.dt+7 = b7.dt
    left join all_dpd b8 on a.loan_acct_nbr = b8.loan_acct_nbr and a.dt+8 = b8.dt
    left join all_dpd b9 on a.loan_acct_nbr = b9.loan_acct_nbr and a.dt+9 = b9.dt
    left join all_dpd b10 on a.loan_acct_nbr = b10.loan_acct_nbr and a.dt+10 = b10.dt
    left join all_dpd b11 on a.loan_acct_nbr = b11.loan_acct_nbr and a.dt+11 = b11.dt
    left join all_dpd b12 on a.loan_acct_nbr = b12.loan_acct_nbr and a.dt+12 = b12.dt
    left join all_dpd b13 on a.loan_acct_nbr = b13.loan_acct_nbr and a.dt+13 = b13.dt
    left join all_dpd b14 on a.loan_acct_nbr = b14.loan_acct_nbr and a.dt+14 = b14.dt
    left join all_dpd b15 on a.loan_acct_nbr = b15.loan_acct_nbr and a.dt+15 = b15.dt
    left join all_dpd b16 on a.loan_acct_nbr = b16.loan_acct_nbr and a.dt+16 = b16.dt
    left join all_dpd b17 on a.loan_acct_nbr = b17.loan_acct_nbr and a.dt+17 = b17.dt
    left join all_dpd b18 on a.loan_acct_nbr = b18.loan_acct_nbr and a.dt+18 = b18.dt
    left join all_dpd b19 on a.loan_acct_nbr = b19.loan_acct_nbr and a.dt+19 = b19.dt
    left join all_dpd b20 on a.loan_acct_nbr = b20.loan_acct_nbr and a.dt+20 = b20.dt
    left join all_dpd b21 on a.loan_acct_nbr = b21.loan_acct_nbr and a.dt+21 = b21.dt
    left join all_dpd b22 on a.loan_acct_nbr = b22.loan_acct_nbr and a.dt+22 = b22.dt
    left join all_dpd b23 on a.loan_acct_nbr = b23.loan_acct_nbr and a.dt+23 = b23.dt
    left join all_dpd b24 on a.loan_acct_nbr = b24.loan_acct_nbr and a.dt+24 = b24.dt
    left join all_dpd b25 on a.loan_acct_nbr = b25.loan_acct_nbr and a.dt+25 = b25.dt
    left join all_dpd b26 on a.loan_acct_nbr = b26.loan_acct_nbr and a.dt+26 = b26.dt
    left join all_dpd b27 on a.loan_acct_nbr = b27.loan_acct_nbr and a.dt+27 = b27.dt
    left join all_dpd b28 on a.loan_acct_nbr = b28.loan_acct_nbr and a.dt+28 = b28.dt
    left join all_dpd b29 on a.loan_acct_nbr = b29.loan_acct_nbr and a.dt+29 = b29.dt
    left join all_dpd b30 on a.loan_acct_nbr = b30.loan_acct_nbr and a.dt+30 = b30.dt
    left join all_dpd b31 on a.loan_acct_nbr = b31.loan_acct_nbr and a.dt+31 = b31.dt
    left join all_dpd b32 on a.loan_acct_nbr = b32.loan_acct_nbr and a.dt+32 = b32.dt
    left join all_dpd b33 on a.loan_acct_nbr = b33.loan_acct_nbr and a.dt+33 = b33.dt
    left join all_dpd b34 on a.loan_acct_nbr = b34.loan_acct_nbr and a.dt+34 = b34.dt
    left join all_dpd b35 on a.loan_acct_nbr = b35.loan_acct_nbr and a.dt+35 = b35.dt
    left join all_dpd b36 on a.loan_acct_nbr = b36.loan_acct_nbr and a.dt+36 = b36.dt
    left join all_dpd b37 on a.loan_acct_nbr = b37.loan_acct_nbr and a.dt+37 = b37.dt
    left join all_dpd b38 on a.loan_acct_nbr = b38.loan_acct_nbr and a.dt+38 = b38.dt
    left join all_dpd b39 on a.loan_acct_nbr = b39.loan_acct_nbr and a.dt+39 = b39.dt
    left join all_dpd b40 on a.loan_acct_nbr = b40.loan_acct_nbr and a.dt+40 = b40.dt
    left join all_dpd b41 on a.loan_acct_nbr = b41.loan_acct_nbr and a.dt+41 = b41.dt
    left join all_dpd b42 on a.loan_acct_nbr = b42.loan_acct_nbr and a.dt+42 = b42.dt
    left join all_dpd b43 on a.loan_acct_nbr = b43.loan_acct_nbr and a.dt+43 = b43.dt
    left join all_dpd b44 on a.loan_acct_nbr = b44.loan_acct_nbr and a.dt+44 = b44.dt
    left join all_dpd b45 on a.loan_acct_nbr = b45.loan_acct_nbr and a.dt+45 = b45.dt
    left join all_dpd b46 on a.loan_acct_nbr = b46.loan_acct_nbr and a.dt+46 = b46.dt
    left join all_dpd b47 on a.loan_acct_nbr = b47.loan_acct_nbr and a.dt+47 = b47.dt
    left join all_dpd b48 on a.loan_acct_nbr = b48.loan_acct_nbr and a.dt+48 = b48.dt
    left join all_dpd b49 on a.loan_acct_nbr = b49.loan_acct_nbr and a.dt+49 = b49.dt
    left join all_dpd b50 on a.loan_acct_nbr = b50.loan_acct_nbr and a.dt+50 = b50.dt
    left join all_dpd b51 on a.loan_acct_nbr = b51.loan_acct_nbr and a.dt+51 = b51.dt
    left join all_dpd b52 on a.loan_acct_nbr = b52.loan_acct_nbr and a.dt+52 = b52.dt
    left join all_dpd b53 on a.loan_acct_nbr = b53.loan_acct_nbr and a.dt+53 = b53.dt
    left join all_dpd b54 on a.loan_acct_nbr = b54.loan_acct_nbr and a.dt+54 = b54.dt
    left join all_dpd b55 on a.loan_acct_nbr = b55.loan_acct_nbr and a.dt+55 = b55.dt
    left join all_dpd b56 on a.loan_acct_nbr = b56.

