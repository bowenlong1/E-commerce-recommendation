proc sql;
   create table track2 as 
   select 
      a.acct_nbr,
      a.dt15,
      b1.days_past_due as dpd62,
      b2.days_past_due as dpd63,
      b3.days_past_due as dpd64,
      b4.days_past_due as dpd65,
      b5.days_past_due as dpd66,
      b6.days_past_due as dpd67,
      b7.days_past_due as dpd68,
      b8.days_past_due as dpd69,
      b9.days_past_due as dpd70,
      b10.days_past_due as dpd71,
      b11.days_past_due as dpd72,
      b12.days_past_due as dpd73,
      b13.days_past_due as dpd74,
      b14.days_past_due as dpd75,
      b15.days_past_due as dpd76,
      b16.days_past_due as dpd77,
      b17.days_past_due as dpd78,
      b18.days_past_due as dpd79,
      b19.days_past_due as dpd80,
      b20.days_past_due as dpd81,
      b21.days_past_due as dpd82,
      b22.days_past_due as dpd83,
      b23.days_past_due as dpd84,
      b24.days_past_due as dpd85,
      b25.days_past_due as dpd86,
      b26.days_past_due as dpd87,
      b27.days_past_due as dpd88,
      b28.days_past_due as dpd89,
      b29.days_past_due as dpd90,
      b30.days_past_due as dpd91,
      b31.days_past_due as dpd92,
      b32.days_past_due as dpd93,
      b33.days_past_due as dpd94,
      b34.days_past_due as dpd95,
      b35.days_past_due as dpd96,
      b36.days_past_due as dpd97,
      b37.days_past_due as dpd98,
      b38.days_past_due as dpd99,
      b39.days_past_due as dpd100,
      b40.days_past_due as dpd101,
      b41.days_past_due as dpd102,
      b42.days_past_due as dpd103,
      b43.days_past_due as dpd104,
      b44.days_past_due as dpd105,
      b45.days_past_due as dpd106,
      b46.days_past_due as dpd107,
      b47.days_past_due as dpd108,
      b48.days_past_due as dpd109,
      b49.days_past_due as dpd110,
      b50.days_past_due as dpd111,
      b51.days_past_due as dpd112,
      b52.days_past_due as dpd113,
      b53.days_past_due as dpd114,
      b54.days_past_due as dpd115,
      b55.days_past_due as dpd116,
      b56.days_past_due as dpd117,
      b57.days_past_due as dpd118,
      b58.days_past_due as dpd119,
      b59.days_past_due as dpd120,
      b60.days_past_due as dpd121
   from 
      track a 
   left join 
      dpd as b1
   on 
      a.acct_nbr = b1.acct_nbr 
      and a.dt15 + 1 = b1.dt
   left join 
      dpd as b2
   on 
      a.acct_nbr = b2.acct_nbr 
      and a.dt15 + 2 = b2.dt
   left join 
      dpd as b3
   on 
      a.acct_nbr = b3.acct_nbr 
      and a.dt15 + 3 = b3.dt
   left join 
      dpd as b4
   on 
      a.acct_nbr = b4.acct_nbr 
      and a.dt15 + 4 = b4.dt
   left join 
      dpd as b5
   on 
      a.acct_nbr = b5.acct_nbr 
      and a.dt15 + 5 = b5.dt
   left join 
      dpd as b6
   on 
      a.acct_nbr = b6.acct_nbr 
      and a.dt15 + 6 = b6.dt
   left join 
      dpd as b7
   on 
      a.acct_nbr = b7.acct_nbr 
      and a.dt15 + 7 = b7.dt
   left join 
      dpd as b8
   on 
      a.acct_nbr = b8.acct_nbr 
      and a.dt15 + 8 = b8.dt
   left join 
      dpd as b9
   on 
      a.acct_nbr = b9.acct_nbr 
      and a.dt15 + 9 = b9.dt
   left join 
      dpd as b10
   on 
      a.acct_nbr = b10.acct_nbr 
      and a.dt15 + 10 = b10.dt
   left join 
      dpd as b11
   on 
      a.acct_nbr = b11.acct_nbr 
      and a.dt15 + 11 = b11.dt
   left join 
      dpd as b12
   on 
      a.acct_nbr = b12.acct_nbr 
      and a.dt15 + 12 = b12.dt
   left join 
      dpd as b13
   on 
      a.acct_nbr = b13.acct_nbr 
      and a.dt15 + 13 = b13.dt
   left join 
      dpd as b14
   on 
      a.acct_nbr = b14.acct_nbr 
      and a.dt15 + 14 = b14.dt
   left join 
      dpd as b15
   on 
      a.acct_nbr = b15.acct_nbr 
      and a.dt15 + 15 = b15.dt
   left join 
      dpd as b16
   on 
      a.acct_nbr = b16.acct_nbr 
      and a.dt15 + 16 = b16.dt
   left join 
      dpd as b17
   on 
      a.acct_nbr = b17.acct_nbr 
      and a.dt15 + 17 = b17.dt
   left join 
      dpd as b18
   on 
      a.acct_nbr = b18.acct_nbr 
      and a.dt15 + 18 = b18.dt
   left join 
      dpd as b19
   on 
      a.acct_nbr = b19.acct_nbr 
      and a.dt15 + 19 = b19.dt
   left join 
      dpd as b20
   on 
      a.acct_nbr = b20.acct_nbr 
      and a.dt15 + 20 = b20.dt
   left join 
      dpd as b21
   on 
      a.acct_nbr = b21.acct_nbr 
      and a.dt15 + 21 = b21.dt
   left join 
      dpd as b22
   on 
      a.acct_nbr = b22.acct_nbr 
      and a.dt15 + 22 = b22.dt
   left join 
      dpd as b23
   on 
      a.acct_nbr = b23.acct_nbr 
      and a.dt15 + 23 = b23.dt
   left join 
      dpd as b24
   on 
      a.acct_nbr = b24.acct_nbr 
      and a.dt15 + 24 = b24.dt
   left join 
      dpd as b25
   on 
      a.acct_nbr = b25.acct_nbr 
      and a.dt15 + 25 = b25.dt
   left join 
      dpd as b26
   on 
      a.acct_nbr = b26.acct_nbr 
      and a.dt15 + 26 = b26.dt
   left join 
      dpd as b27
   on 
      a.acct_nbr = b27.acct_nbr 
      and a.dt15 + 27 = b27.dt
   left join 
      dpd as b28
   on 
      a.acct_nbr = b28.acct_nbr 
      and a.dt15 + 28 = b28.dt
   left join 
      dpd as b29
   on 
      a.acct_nbr = b29.acct_nbr 
      and a.dt15 + 29 = b29.dt
   left join 
      dpd as b30
   on 
      a.acct_nbr = b30.acct_nbr 
      and a.dt15 + 30 = b30.dt
   left join 
      dpd as b31
   on 
      a.acct_nbr = b31.acct_nbr 
      and a.dt15 + 31 = b31.dt
   left join 
      dpd as b32
   on 
      a.acct_nbr = b32.acct_nbr 
      and a.dt15 + 32 = b32.dt
   left join 
      dpd as b33
   on 
      a.acct_nbr = b33.acct_nbr 
      and a.dt15 + 33 = b33.dt
   left join 
      dpd as b34
   on 
      a.acct_nbr = b34.acct_nbr 
      and a.dt15 + 34 = b34.dt
   left join 
      dpd as b35
   on 
      a.acct_nbr = b35.acct_nbr 
      and a.dt15 + 35 = b35.dt
   left join 
      dpd as b36
   on 
      a.acct_nbr = b36.acct_nbr 
      and a.dt15 + 36 = b36.dt
   left join 
      dpd as b37
   on 
      a.acct_nbr = b37.acct_nbr 
      and a.dt15 + 37 = b37.dt
   left join 
      dpd as b38
   on 
      a.acct_nbr = b38.acct_nbr 
      and a.dt15 + 38 = b38.dt
   left join 
      dpd as b39
   on 
      a.acct_nbr = b39.acct_nbr 
      and a.dt15 + 39 = b39.dt
   left join 
      dpd as b40
   on 
      a.acct_nbr = b40.acct_nbr 
      and a.dt15 + 40 = b40.dt
   left join 
      dpd as b41
   on 
      a.acct_nbr = b41.acct_nbr 
      and a.dt15 + 41 = b41.dt
   left join 
      dpd as b42
   on 
      a.acct_nbr = b42.acct_nbr 
      and a.dt15 + 42 = b42.dt
   left join 
      dpd as b43
   on 
      a.acct_nbr = b43.acct_nbr 
      and a.dt15 + 43 = b43.dt
   left join 
      dpd as b44
   on 
      a.acct_nbr = b44.acct_nbr 
      and a.dt15 + 44 = b44.dt
   left join 
      dpd as b45
   on 
      a.acct_nbr = b45.acct_nbr 
      and a.dt15 + 45 = b45.dt
   left join 
      dpd as b46
   on 
      a.acct_nbr = b46.acct_nbr 
      and a.dt15 + 46 = b46.dt
   left join 
      dpd as b47
   on 
      a.acct_nbr = b47.acct_nbr 
      and a.dt15 + 47 = b47.dt
   left join 
      dpd as b48
   on 
      a.acct_nbr = b48.acct_nbr 
      and a.dt15 + 48 = b48.dt
   left join 
      dpd as b49
   on 
      a.acct_nbr = b49.acct_nbr 
      and a.dt15 + 49 = b49.dt
   left join 
      dpd as b50
   on 
      a.acct_nbr = b50.acct_nbr 
      and a.dt15 + 50 = b50.dt
   left join 
      dpd as b51
   on 
      a.acct_nbr = b51.acct_nbr 
      and a.dt15 + 51 = b51.dt
   left join 
      dpd as b52
   on 
      a.acct_nbr = b52.acct_nbr 
      and a.dt15 + 52 = b52.dt
   left join 
      dpd as b53
   on 
      a.acct_nbr = b53.acct_nbr 
      and a.dt15 + 53 = b53.dt
   left join 
      dpd as b54
   on 
      a.acct_nbr = b54.acct_nbr 
      and a.dt15 + 54 = b54.dt
   left join 
      dpd as b55
   on 
      a.acct_nbr = b55.acct_nbr 
      and a.dt15 + 55 = b55.dt
   left join 
      dpd as b56
   on 
      a.acct_nbr = b56.acct_nbr 
      and a.dt15 + 56 = b56.dt
   left join 
      dpd as b57
   on 
      a.acct_nbr = b57.acct_nbr 
      and a.dt15 + 57 = b57.dt
   left join 
      dpd as b58
   on 
      a.acct_nbr = b58.acct_nbr 
      and a.dt15 + 58 = b58.dt
   left join 
      dpd as b59
   on 
      a.acct_nbr = b59.acct_nbr 
      and a.dt15 + 59 = b59.dt
   left join 
      dpd as b60
   on 
      a.acct_nbr = b60.acct_nbr 
      and a.dt15 + 60 = b60.dt
   left join 
      dpd as b61
   on 
      a.acct_nbr = b61.acct_nbr 
      and a.dt15 + 61 = b61.dt
   left join 
      dpd as b62
   on 
      a.acct_nbr = b62.acct_nbr 
      and a.dt15 + 62 = b62.dt
   left join 
      dpd as b63
   on 
      a.acct_nbr = b63.acct_nbr 
      and a.dt15 + 63 = b63.dt
   left join 
      dpd as b64
   on 
      a.acct_nbr = b64.acct_nbr 
      and a.dt15 + 64 = b64.dt
   left join 
      dpd as b65
   on 
      a.acct_nbr = b65.acct_nbr 
      and a.dt15 + 65 = b65.dt
   left join 
      dpd as b66
   on 
      a.acct_nbr = b66.acct_nbr 
      and a.dt15 + 66 = b66.dt
   left join 
      dpd as b67
   on 
      a.acct_nbr = b67.acct_nbr 
      and a.dt15 + 67 = b67.dt
   left join 
      dpd as b68
   on 
      a.acct_nbr = b68.acct_nbr 
      and a.dt15 + 68 = b68.dt
   left join 
      dpd as b69
   on 
      a.acct_nbr = b69.acct_nbr 
      and a.dt15 + 69 = b69.dt
   left join 
      dpd as b70
   on 
      a.acct_nbr = b70.acct_nbr 
      and a.dt15 + 70 = b70.dt
   left join 
      dpd as b71
   on 
      a.acct_nbr = b71.acct_nbr 
      and a.dt15 + 71 = b71.dt
   left join 
      dpd as b72
   on 
      a.acct_nbr = b72.acct_nbr 
      and a.dt15 + 72 = b72.dt
   left join 
      dpd as b73
   on 
      a.acct_nbr = b73.acct_nbr 
      and a.dt15 + 73 = b73.dt
   left join 
      dpd as b74
   on 
      a.acct_nbr = b74.acct_nbr 
      and a.dt15 + 74 = b74.dt
   left join 
      dpd as b75
   on 
      a.acct_nbr = b75.acct_nbr 
      and a.dt15 + 75 = b75.dt
   left join 
      dpd as b76
   on 
      a.acct_nbr = b76.acct_nbr 
      and a.dt15 + 76 = b76.dt
   left join 
      dpd as b77
   on 
      a.acct_nbr = b77.acct_nbr 
      and a.dt15 + 77 = b77.dt
   left join 
      dpd as b78
   on 
      a.acct_nbr = b78.acct_nbr 
      and a.dt15 + 78 = b78.dt
   left join 
      dpd as b79
   on 
      a.acct_nbr = b79.acct_nbr 
      and a.dt15 + 79 = b79.dt
   left join 
      dpd as b80
   on 
      a.acct_nbr = b80.acct_nbr 
      and a.dt15 + 80 = b80.dt
   left join 
      dpd as b81
   on 
      a.acct_nbr = b81.acct_nbr 
      and a.dt15 + 81 = b81.dt
   left join 
      dpd as b82
   on 
      a.acct_nbr = b82.acct_nbr 
      and a.dt15 + 82 = b82.dt
   left join 
      dpd as b83
   on 
      a.acct_nbr = b83.acct_nbr 
      and a.dt15 + 83 = b83.dt
   left join 
      dpd as b84
   on 
      a.acct_nbr = b84.acct_nbr 
      and a.dt15 + 84 = b84.dt
   left join 
      dpd as b85
   on 
      a.acct_nbr = b85.acct_nbr 
      and a.dt15 + 85 = b85.dt
   left join 
      dpd as b86
   on 
      a.acct_nbr = b86.acct_nbr 
      and a.dt15 + 86 = b86.dt
   left join 
      dpd as b87
   on 
      a.acct_nbr = b87.acct_nbr 
      and a.dt15 + 87 = b87.dt
   left join 
      dpd as b88
   on 
      a.acct_nbr = b88.acct_nbr 
      and a.dt15 + 88 = b88.dt
   left join 
      dpd as b89
   on 
      a.acct_nbr = b89.acct_nbr 
      and a.dt15 + 89 = b89.dt
   left join 
      dpd as b90
   on 
      a.acct_nbr = b90.acct_nbr 
      and a.dt15 + 90 = b90.dt
   left join 
      dpd as b91
   on 
      a.acct_nbr = b91.acct_nbr 
      and a.dt15 + 91 = b91.dt
   left join 
      dpd as b92
   on 
      a.acct_nbr = b92.acct_nbr 
      and a.dt15 + 92 = b92.dt
   left join 
      dpd as b93
   on 
      a.acct_nbr = b93.acct_nbr 
      and a.dt15 + 93 = b93.dt
   left join 
      dpd as b94
   on 
      a.acct_nbr = b94.acct_nbr 
      and a.dt15 + 94 = b94.dt
   left join 
      dpd as b95
   on 
      a.acct_nbr = b95.acct_nbr 
      and a.dt15 + 95 = b95.dt
   left join 
      dpd as b96
   on 
      a.acct_nbr = b96.acct_nbr 
      and a.dt15 + 96 = b96.dt
   left join 
      dpd as b97
   on 
      a.acct_nbr = b97.acct_nbr 
      and a.dt15 + 97 = b97.dt
   left join 
      dpd as b98
   on 
      a.acct_nbr = b98.acct_nbr 
      and a.dt15 + 98 = b98.dt
   left join 
      dpd as b99
   on 
      a.acct_nbr = b99.acct_nbr 
      and a.dt15 + 99 = b99.dt
   left join 
      dpd as b100
   on 
      a.acct_nbr = b100.acct_nbr
