RmarkdownNguyenFinalProject
================
Grant Nguyen
11/1/2020

## R Markdown

Title & description of the project: CO2 Emissions by Country

Your name & partner’s name: Grant Nguyen

A description of the data required, and how it will be obtained
(e.g. URL/DOI to data source):
<https://datasets.wri.org/dataset/cait-country> Data will be in csv
format and contain metric tons of CO2 emissions by country from start of
data collection till 2012.

3 questions / analysis tasks you will perform on the data; in the spirit
of the assignments we have been doing:

I will be importing my csv in r and I will use dyplr,ggplot, and more
libraries to create new variables like total CO2 emissions by country
and average CO2 rates by country, which includes use of custom R
functions I will also be creating detailed visual representations of my
findings in the form of bar charts and graphs. Essentially I want to see
which country is emitting most and their rate of emission. I will also
create a website to publish my
findings.

``` r
countryGHG <- read.csv("https://raw.githubusercontent.com/espm-157/Nguyen-Grant-Final-Project/master/cait_annex_ghgemissions.csv")
countryGHG
```

    ##                            X  X.1                            Emissions.Totals
    ## 1                    Country Year Total GHG Emissions Excluding LUCF (MtCO2e)
    ## 2                  Australia 1990                                    417.7422
    ## 3                    Austria 1990                                     78.1567
    ## 4                    Belarus 1990                                    139.1512
    ## 5                    Belgium 1990                                    143.0948
    ## 6                   Bulgaria 1990                                    109.5408
    ## 7                     Canada 1990                                    591.0794
    ## 8                    Croatia 1990                                     31.6472
    ## 9                     Cyprus 1990                                      6.0908
    ## 10            Czech Republic 1990                                     196.039
    ## 11                   Denmark 1990                                     70.0877
    ## 12                   Estonia 1990                                     40.5421
    ## 13       European Union (15) 1990                                   4254.5039
    ## 14       European Union (27) 1990                                   5574.4244
    ## 15                   Finland 1990                                     70.4375
    ## 16                    France 1990                                    559.4916
    ## 17                   Germany 1990                                   1250.2636
    ## 18                    Greece 1990                                    104.5866
    ## 19                   Hungary 1990                                     98.9807
    ## 20                   Iceland 1990                                       3.508
    ## 21                   Ireland 1990                                     55.2471
    ## 22                     Italy 1990                                    518.9842
    ## 23                     Japan 1990                                   1266.6713
    ## 24                    Latvia 1990                                     26.3234
    ## 25             Liechtenstein 1990                                      0.2303
    ## 26                 Lithuania 1990                                     48.7539
    ## 27                Luxembourg 1990                                      12.901
    ## 28                     Malta 1990                                      2.0066
    ## 29                    Monaco 1990                                      0.1079
    ## 30               Netherlands 1990                                    211.8493
    ## 31               New Zealand 1990                                     59.6431
    ## 32                    Norway 1990                                     50.3624
    ## 33                    Poland 1990                                    457.0146
    ## 34                  Portugal 1990                                     60.9524
    ## 35                   Romania 1990                                    244.4036
    ## 36        Russian Federation 1990                                    3351.944
    ## 37                  Slovakia 1990                                     71.7818
    ## 38                  Slovenia 1990                                      18.443
    ## 39                     Spain 1990                                    282.7887
    ## 40                    Sweden 1990                                     72.7504
    ## 41               Switzerland 1990                                      52.973
    ## 42                    Turkey 1990                                    188.4342
    ## 43                   Ukraine 1990                                    929.8936
    ## 44            United Kingdom 1990                                    770.7837
    ## 45  United States of America 1990                                   6169.5921
    ## 46                 Australia 1991                                    419.3831
    ## 47                   Austria 1991                                     82.1964
    ## 48                   Belarus 1991                                    131.7234
    ## 49                   Belgium 1991                                    145.0799
    ## 50                  Bulgaria 1991                                     86.7432
    ## 51                    Canada 1991                                    583.3949
    ## 52                   Croatia 1991                                     24.9307
    ## 53                    Cyprus 1991                                      6.3548
    ## 54            Czech Republic 1991                                    182.1466
    ## 55                   Denmark 1991                                     80.5928
    ## 56                   Estonia 1991                                      37.371
    ## 57       European Union (15) 1991                                   4268.7219
    ## 58       European Union (27) 1991                                   5477.4374
    ## 59                   Finland 1991                                     68.2443
    ## 60                    France 1991                                    583.2022
    ## 61                   Germany 1991                                   1203.2507
    ## 62                    Greece 1991                                    104.1804
    ## 63                   Hungary 1991                                     91.5537
    ## 64                   Iceland 1991                                      3.3447
    ## 65                   Ireland 1991                                     56.0286
    ## 66                     Italy 1991                                    520.5135
    ## 67                     Japan 1991                                   1280.9283
    ## 68                    Latvia 1991                                     24.4206
    ## 69             Liechtenstein 1991                                      0.2383
    ## 70                 Lithuania 1991                                     50.1225
    ## 71                Luxembourg 1991                                     13.4467
    ## 72                     Malta 1991                                      2.1828
    ## 73                    Monaco 1991                                      0.1092
    ## 74               Netherlands 1991                                    216.4157
    ## 75               New Zealand 1991                                     60.5968
    ## 76                    Norway 1991                                     48.2652
    ## 77                    Poland 1991                                    447.2457
    ## 78                  Portugal 1991                                     62.8837
    ## 79                   Romania 1991                                    199.5119
    ## 80        Russian Federation 1991                                   3177.8289
    ## 81                  Slovakia 1991                                     63.7461
    ## 82                  Slovenia 1991                                     17.3167
    ## 83                     Spain 1991                                    290.2759
    ## 84                    Sweden 1991                                     72.9249
    ## 85               Switzerland 1991                                      54.656
    ## 86                    Turkey 1991                                     200.654
    ## 87                   Ukraine 1991                                    818.2349
    ## 88            United Kingdom 1991                                    777.4737
    ## 89  United States of America 1991                                   6122.2497
    ## 90                 Australia 1992                                     423.869
    ## 91                   Austria 1992                                     75.4347
    ## 92                   Belarus 1992                                    121.9809
    ## 93                   Belgium 1992                                    143.7962
    ## 94                  Bulgaria 1992                                     80.4927
    ## 95                    Canada 1992                                    600.3317
    ## 96                   Croatia 1992                                     23.2356
    ## 97                    Cyprus 1992                                      6.7822
    ## 98            Czech Republic 1992                                     165.609
    ## 99                   Denmark 1992                                     74.5152
    ## 100                  Estonia 1992                                     27.3483
    ## 101      European Union (15) 1992                                   4180.1446
    ## 102      European Union (27) 1992                                   5277.5542
    ## 103                  Finland 1992                                     66.8278
    ## 104                   France 1992                                    575.6697
    ## 105                  Germany 1992                                    1153.116
    ## 106                   Greece 1992                                    105.6121
    ## 107                  Hungary 1992                                     82.1006
    ## 108                  Iceland 1992                                      3.2505
    ## 109                  Ireland 1992                                     56.0205
    ## 110                    Italy 1992                                     517.693
    ## 111                    Japan 1992                                   1295.3048
    ## 112                   Latvia 1992                                      19.668
    ## 113            Liechtenstein 1992                                      0.2388
    ## 114                Lithuania 1992                                     30.2119
    ## 115               Luxembourg 1992                                     13.2217
    ## 116                    Malta 1992                                       2.293
    ## 117                   Monaco 1992                                      0.1163
    ## 118              Netherlands 1992                                    215.0821
    ## 119              New Zealand 1992                                     61.7994
    ## 120                   Norway 1992                                     46.5175
    ## 121                   Poland 1992                                    433.3798
    ## 122                 Portugal 1992                                     67.2688
    ## 123                  Romania 1992                                    174.0505
    ## 124       Russian Federation 1992                                   2685.4731
    ## 125                 Slovakia 1992                                     58.2714
    ## 126                 Slovenia 1992                                     17.2022
    ## 127                    Spain 1992                                    297.0826
    ## 128                   Sweden 1992                                     72.5178
    ## 129              Switzerland 1992                                     54.3856
    ## 130                   Turkey 1992                                    211.7293
    ## 131                  Ukraine 1992                                    727.4651
    ## 132           United Kingdom 1992                                    754.3634
    ## 133 United States of America 1992                                   6238.8758
    ## 134                Australia 1993                                    425.6383
    ## 135                  Austria 1993                                     75.4798
    ## 136                  Belarus 1993                                    107.6064
    ## 137                  Belgium 1993                                    142.8444
    ## 138                 Bulgaria 1993                                     78.7152
    ## 139                   Canada 1993                                    602.0883
    ## 140                  Croatia 1993                                     23.2859
    ## 141                   Cyprus 1993                                      7.0864
    ## 142           Czech Republic 1993                                    159.4367
    ## 143                  Denmark 1993                                     76.6819
    ## 144                  Estonia 1993                                      21.211
    ## 145      European Union (15) 1993                                   4108.9921
    ## 146      European Union (27) 1993                                   5174.3153
    ## 147                  Finland 1993                                     68.9188
    ## 148                   France 1993                                    546.8761
    ## 149                  Germany 1993                                   1143.8097
    ## 150                   Greece 1993                                    104.6681
    ## 151                  Hungary 1993                                     82.2942
    ## 152                  Iceland 1993                                      3.3127
    ## 153                  Ireland 1993                                     56.3869
    ## 154                    Italy 1993                                    511.1797
    ## 155                    Japan 1993                                   1288.8008
    ## 156                   Latvia 1993                                      15.889
    ## 157            Liechtenstein 1993                                      0.2461
    ## 158                Lithuania 1993                                     24.3302
    ## 159               Luxembourg 1993                                     13.3338
    ## 160                    Malta 1993                                      2.2939
    ## 161                   Monaco 1993                                      0.1162
    ## 162              Netherlands 1993                                      220.01
    ## 163              New Zealand 1993                                     61.4711
    ## 164                   Norway 1993                                       48.45
    ## 165                   Poland 1993                                    433.6576
    ## 166                 Portugal 1993                                     65.8921
    ## 167                  Romania 1993                                    169.3643
    ## 168       Russian Federation 1993                                   2548.9992
    ## 169                 Slovakia 1993                                     53.6053
    ## 170                 Slovenia 1993                                     17.4395
    ## 171                    Spain 1993                                    284.9979
    ## 172                   Sweden 1993                                     72.5147
    ## 173              Switzerland 1993                                     51.5771
    ## 174                   Turkey 1993                                    223.0802
    ## 175                  Ukraine 1993                                    636.0601
    ## 176           United Kingdom 1993                                    733.4297
    ## 177 United States of America 1993                                   6385.0075
    ## 178                Australia 1994                                    426.1486
    ## 179                  Austria 1994                                     76.3381
    ## 180                  Belarus 1994                                     91.7299
    ## 181                  Belgium 1994                                    148.5785
    ## 182                 Bulgaria 1994                                     75.0742
    ## 183                   Canada 1994                                    622.7651
    ## 184                  Croatia 1994                                      22.469
    ## 185                   Cyprus 1994                                       7.564
    ## 186           Czech Republic 1994                                    149.4488
    ## 187                  Denmark 1994                                     80.6152
    ## 188                  Estonia 1994                                     21.8655
    ## 189      European Union (15) 1994                                   4108.7102
    ## 190      European Union (27) 1994                                   5148.9827
    ## 191                  Finland 1994                                     74.3109
    ## 192                   France 1994                                     546.991
    ## 193                  Germany 1994                                   1123.9379
    ## 194                   Greece 1994                                    107.4195
    ## 195                  Hungary 1994                                      81.842
    ## 196                  Iceland 1994                                      3.2455
    ## 197                  Ireland 1994                                     57.8468
    ## 198                    Italy 1994                                     503.475
    ## 199                    Japan 1994                                   1360.0857
    ## 200                   Latvia 1994                                     13.9576
    ## 201            Liechtenstein 1994                                      0.2323
    ## 202                Lithuania 1994                                     22.9087
    ## 203               Luxembourg 1994                                     12.5051
    ## 204                    Malta 1994                                      2.4095
    ## 205                   Monaco 1994                                      0.1184
    ## 206              Netherlands 1994                                    219.9764
    ## 207              New Zealand 1994                                     62.5293
    ## 208                   Norway 1994                                     50.4097
    ## 209                   Poland 1994                                    430.0583
    ## 210                 Portugal 1994                                     67.1008
    ## 211                  Romania 1994                                    166.0943
    ## 212       Russian Federation 1994                                   2281.4601
    ## 213                 Slovakia 1994                                     51.4237
    ## 214                 Slovenia 1994                                      17.626
    ## 215                    Spain 1994                                    301.2245
    ## 216                   Sweden 1994                                     75.0032
    ## 217              Switzerland 1994                                      50.696
    ## 218                   Turkey 1994                                      218.53
    ## 219                  Ukraine 1994                                     557.359
    ## 220           United Kingdom 1994                                    721.4358
    ## 221 United States of America 1994                                   6456.4176
    ## 222                Australia 1995                                    439.1279
    ## 223                  Austria 1995                                      79.729
    ## 224                  Belarus 1995                                     82.8397
    ## 225                  Belgium 1995                                    150.4079
    ## 226                 Bulgaria 1995                                     75.8387
    ## 227                   Canada 1995                                    639.1397
    ## 228                  Croatia 1995                                     23.0607
    ## 229                   Cyprus 1995                                      7.4653
    ## 230           Czech Republic 1995                                    150.6765
    ## 231                  Denmark 1995                                     77.2883
    ## 232                  Estonia 1995                                     20.0382
    ## 233      European Union (15) 1995                                   4146.3161
    ## 234      European Union (27) 1995                                   5194.6361
    ## 235                  Finland 1995                                     70.8846
    ## 236                   France 1995                                    555.1868
    ## 237                  Germany 1995                                   1118.3279
    ## 238                   Greece 1995                                    109.2891
    ## 239                  Hungary 1995                                     80.2957
    ## 240                  Iceland 1995                                      3.2862
    ## 241                  Ireland 1995                                     58.9857
    ## 242                    Italy 1995                                    530.2407
    ## 243                    Japan 1995                                   1337.7263
    ## 244                   Latvia 1995                                     12.5739
    ## 245            Liechtenstein 1995                                      0.2357
    ## 246                Lithuania 1995                                      22.061
    ## 247               Luxembourg 1995                                     10.1775
    ## 248                    Malta 1995                                      2.3784
    ## 249                   Monaco 1995                                      0.1157
    ## 250              Netherlands 1995                                    223.1955
    ## 251              New Zealand 1995                                     63.2149
    ## 252                   Norway 1995                                     50.2203
    ## 253                   Poland 1995                                    432.4604
    ## 254                 Portugal 1995                                      71.604
    ## 255                  Romania 1995                                    172.7906
    ## 256       Russian Federation 1995                                   2199.0245
    ## 257                 Slovakia 1995                                     53.2119
    ## 258                 Slovenia 1995                                     18.5294
    ## 259                    Spain 1995                                    312.6969
    ## 260                   Sweden 1995                                     74.3713
    ## 261              Switzerland 1995                                     51.4658
    ## 262                   Turkey 1995                                    238.8203
    ## 263                  Ukraine 1995                                    498.5663
    ## 264           United Kingdom 1995                                    712.3218
    ## 265 United States of America 1995                                   6541.2267
    ## 266                Australia 1996                                    446.2757
    ## 267                  Austria 1996                                     82.7415
    ## 268                  Belarus 1996                                     84.9079
    ## 269                  Belgium 1996                                    154.4367
    ## 270                 Bulgaria 1996                                     75.7024
    ## 271                   Canada 1996                                    658.1015
    ## 272                  Croatia 1996                                     23.7022
    ## 273                   Cyprus 1996                                       7.877
    ## 274           Czech Republic 1996                                    154.6797
    ## 275                  Denmark 1996                                     90.2337
    ## 276                  Estonia 1996                                     20.7003
    ## 277      European Union (15) 1996                                   4227.3223
    ## 278      European Union (27) 1996                                   5300.4235
    ## 279                  Finland 1996                                     76.6194
    ## 280                   France 1996                                    569.9918
    ## 281                  Germany 1996                                    1137.261
    ## 282                   Greece 1996                                    112.3514
    ## 283                  Hungary 1996                                     82.4181
    ## 284                  Iceland 1996                                      3.3762
    ## 285                  Ireland 1996                                     61.0588
    ## 286                    Italy 1996                                    523.9159
    ## 287                    Japan 1996                                   1351.5544
    ## 288                   Latvia 1996                                     12.6023
    ## 289            Liechtenstein 1996                                      0.2386
    ## 290                Lithuania 1996                                      23.345
    ## 291               Luxembourg 1996                                     10.2386
    ## 292                    Malta 1996                                      2.4286
    ## 293                   Monaco 1996                                      0.1206
    ## 294              Netherlands 1996                                    231.2826
    ## 295              New Zealand 1996                                     65.3703
    ## 296                   Norway 1996                                     53.3526
    ## 297                   Poland 1996                                    445.6555
    ## 298                 Portugal 1996                                     69.3575
    ## 299                  Romania 1996                                    175.4024
    ## 300       Russian Federation 1996                                   2136.5901
    ## 301                 Slovakia 1996                                     53.0872
    ## 302                 Slovenia 1996                                     19.2027
    ## 303                    Spain 1996                                    305.0734
    ## 304                   Sweden 1996                                     78.3355
    ## 305              Switzerland 1996                                     52.0919
    ## 306                   Turkey 1996                                     259.939
    ## 307                  Ukraine 1996                                    450.5285
    ## 308           United Kingdom 1996                                    733.0229
    ## 309 United States of America 1996                                   6747.5408
    ## 310                Australia 1997                                    458.7685
    ## 311                  Austria 1997                                     82.2693
    ## 312                  Belarus 1997                                     86.7301
    ## 313                  Belgium 1997                                     145.862
    ## 314                 Bulgaria 1997                                     72.0743
    ## 315                   Canada 1997                                    671.8429
    ## 316                  Croatia 1997                                     25.1187
    ## 317                   Cyprus 1997                                      7.9423
    ## 318           Czech Republic 1997                                    151.7639
    ## 319                  Denmark 1997                                     80.7183
    ## 320                  Estonia 1997                                     20.3142
    ## 321      European Union (15) 1997                                   4164.4028
    ## 322      European Union (27) 1997                                   5206.5503
    ## 323                  Finland 1997                                     75.2371
    ## 324                   France 1997                                    564.5332
    ## 325                  Germany 1997                                   1101.3522
    ## 326                   Greece 1997                                     117.168
    ## 327                  Hungary 1997                                      80.618
    ## 328                  Iceland 1997                                      3.5305
    ## 329                  Ireland 1997                                     62.5651
    ## 330                    Italy 1997                                    530.2973
    ## 331                    Japan 1997                                   1344.9561
    ## 332                   Latvia 1997                                     12.0405
    ## 333            Liechtenstein 1997                                      0.2509
    ## 334                Lithuania 1997                                      23.037
    ## 335               Luxembourg 1997                                      9.5345
    ## 336                    Malta 1997                                      2.4965
    ## 337                   Monaco 1997                                      0.1206
    ## 338              Netherlands 1997                                    224.6536
    ## 339              New Zealand 1997                                     68.1379
    ## 340                   Norway 1997                                     53.3075
    ## 341                   Poland 1997                                    437.1429
    ## 342                 Portugal 1997                                     72.4379
    ## 343                  Romania 1997                                    161.9684
    ## 344       Russian Federation 1997                                   2031.9748
    ## 345                 Slovakia 1997                                     53.1881
    ## 346                 Slovenia 1997                                     19.5613
    ## 347                    Spain 1997                                    326.6202
    ## 348                   Sweden 1997                                     73.2638
    ## 349              Switzerland 1997                                     51.1694
    ## 350                   Turkey 1997                                    273.1725
    ## 351                  Ukraine 1997                                    428.0423
    ## 352           United Kingdom 1997                                    706.6485
    ## 353 United States of America 1997                                   6810.6028
    ## 354                Australia 1998                                     473.149
    ## 355                  Austria 1998                                     81.6352
    ## 356                  Belarus 1998                                     84.9498
    ## 357                  Belgium 1998                                    151.4338
    ## 358                 Bulgaria 1998                                     67.1272
    ## 359                   Canada 1998                                    679.4556
    ## 360                  Croatia 1998                                     25.2919
    ## 361                   Cyprus 1998                                      8.0316
    ## 362           Czech Republic 1998                                    144.7988
    ## 363                  Denmark 1998                                     76.8825
    ## 364                  Estonia 1998                                     18.7846
    ## 365      European Union (15) 1998                                   4184.7022
    ## 366      European Union (27) 1998                                   5167.4594
    ## 367                  Finland 1998                                     71.6523
    ## 368                   France 1998                                     579.995
    ## 369                  Germany 1998                                   1075.4058
    ## 370                   Greece 1998                                    122.7513
    ## 371                  Hungary 1998                                     80.0602
    ## 372                  Iceland 1998                                      3.6613
    ## 373                  Ireland 1998                                     65.3642
    ## 374                    Italy 1998                                    541.6607
    ## 375                    Japan 1998                                   1302.3905
    ## 376                   Latvia 1998                                     11.5094
    ## 377            Liechtenstein 1998                                      0.2624
    ## 378                Lithuania 1998                                      23.803
    ## 379               Luxembourg 1998                                      8.6446
    ## 380                    Malta 1998                                      2.5074
    ## 381                   Monaco 1998                                      0.1186
    ## 382              Netherlands 1998                                    225.5088
    ## 383              New Zealand 1998                                     65.8199
    ## 384                   Norway 1998                                     53.4724
    ## 385                   Poland 1998                                    408.7846
    ## 386                 Portugal 1998                                     77.3015
    ## 387                  Romania 1998                                    145.4892
    ## 388       Russian Federation 1998                                   1996.3706
    ## 389                 Slovakia 1998                                     52.5433
    ## 390                 Slovenia 1998                                      19.318
    ## 391                    Spain 1998                                    336.6425
    ## 392                   Sweden 1998                                     73.7481
    ## 393              Switzerland 1998                                     52.5101
    ## 394                   Turkey 1998                                    275.3148
    ## 395                  Ukraine 1998                                     419.739
    ## 396           United Kingdom 1998                                     705.196
    ## 397 United States of America 1998                                    6825.173
    ## 398                Australia 1999                                    482.4221
    ## 399                  Austria 1999                                     79.9171
    ## 400                  Belarus 1999                                     81.4761
    ## 401                  Belgium 1999                                    145.2278
    ## 402                 Bulgaria 1999                                     60.3147
    ## 403                   Canada 1999                                    691.6306
    ## 404                  Croatia 1999                                     26.5719
    ## 405                   Cyprus 1999                                      8.3294
    ## 406           Czech Republic 1999                                    136.4314
    ## 407                  Denmark 1999                                     74.1625
    ## 408                  Estonia 1999                                      17.427
    ## 409      European Union (15) 1999                                   4122.5406
    ## 410      European Union (27) 1999                                   5059.3911
    ## 411                  Finland 1999                                     71.1067
    ## 412                   France 1999                                     565.681
    ## 413                  Germany 1999                                   1041.5327
    ## 414                   Greece 1999                                    122.6141
    ## 415                  Hungary 1999                                     80.3223
    ## 416                  Iceland 1999                                      3.8909
    ## 417                  Ireland 1999                                     66.2931
    ## 418                    Italy 1999                                    548.0498
    ## 419                    Japan 1999                                   1323.5416
    ## 420                   Latvia 1999                                      10.714
    ## 421            Liechtenstein 1999                                      0.2613
    ## 422                Lithuania 1999                                     21.2555
    ## 423               Luxembourg 1999                                      9.0625
    ## 424                    Malta 1999                                      2.5938
    ## 425                   Monaco 1999                                      0.1194
    ## 426              Netherlands 1999                                    213.3686
    ## 427              New Zealand 1999                                     67.7859
    ## 428                   Norway 1999                                     54.4853
    ## 429                   Poland 1999                                    398.6422
    ## 430                 Portugal 1999                                     85.4378
    ## 431                  Romania 1999                                    130.7782
    ## 432       Russian Federation 1999                                   2028.6356
    ## 433                 Slovakia 1999                                     51.3778
    ## 434                 Slovenia 1999                                     18.6642
    ## 435                    Spain 1999                                    364.5169
    ## 436                   Sweden 1999                                     70.4079
    ## 437              Switzerland 1999                                     52.6023
    ## 438                   Turkey 1999                                    276.0209
    ## 439                  Ukraine 1999                                    409.5321
    ## 440           United Kingdom 1999                                    674.2471
    ## 441 United States of America 1999                                   6885.2796
    ## 442                Australia 2000                                    493.2718
    ## 443                  Austria 2000                                     80.1981
    ## 444                  Belarus 2000                                     79.1651
    ## 445                  Belgium 2000                                    145.9917
    ## 446                 Bulgaria 2000                                     59.5007
    ## 447                   Canada 2000                                    717.5811
    ## 448                  Croatia 2000                                     26.2902
    ## 449                   Cyprus 2000                                      8.5738
    ## 450           Czech Republic 2000                                     145.886
    ## 451                  Denmark 2000                                     69.6491
    ## 452                  Estonia 2000                                     17.1422
    ## 453      European Union (15) 2000                                   4137.5439
    ## 454      European Union (27) 2000                                   5066.4636
    ## 455                  Finland 2000                                     69.3297
    ## 456                   France 2000                                     562.995
    ## 457                  Germany 2000                                   1040.5958
    ## 458                   Greece 2000                                    126.2244
    ## 459                  Hungary 2000                                       78.44
    ## 460                  Iceland 2000                                      3.8756
    ## 461                  Ireland 2000                                      68.203
    ## 462                    Italy 2000                                    551.3012
    ## 463                    Japan 2000                                   1342.0875
    ## 464                   Latvia 2000                                     10.0626
    ## 465            Liechtenstein 2000                                      0.2549
    ## 466                Lithuania 2000                                     19.6477
    ## 467               Luxembourg 2000                                        9.76
    ## 468                    Malta 2000                                       2.541
    ## 469                   Monaco 2000                                      0.1199
    ## 470              Netherlands 2000                                    213.0057
    ## 471              New Zealand 2000                                     69.4007
    ## 472                   Norway 2000                                     54.0171
    ## 473                   Poland 2000                                    385.3808
    ## 474                 Portugal 2000                                     84.3033
    ## 475                  Romania 2000                                     133.526
    ## 476       Russian Federation 2000                                   2047.0364
    ## 477                 Slovakia 2000                                     49.2986
    ## 478                 Slovenia 2000                                     18.9202
    ## 479                    Spain 2000                                    378.7758
    ## 480                   Sweden 2000                                     68.9017
    ## 481              Switzerland 2000                                     51.7366
    ## 482                   Turkey 2000                                    298.2148
    ## 483                  Ukraine 2000                                    395.7498
    ## 484           United Kingdom 2000                                    677.4889
    ## 485 United States of America 2000                                   7045.3463
    ## 486                Australia 2001                                    504.0331
    ## 487                  Austria 2001                                     84.1842
    ## 488                  Belarus 2001                                     77.2166
    ## 489                  Belgium 2001                                    145.4008
    ## 490                 Bulgaria 2001                                     62.6593
    ## 491                   Canada 2001                                    710.9696
    ## 492                  Croatia 2001                                     27.4548
    ## 493                   Cyprus 2001                                      8.4704
    ## 494           Czech Republic 2001                                    145.6717
    ## 495                  Denmark 2001                                     71.3024
    ## 496                  Estonia 2001                                     17.5306
    ## 497      European Union (15) 2001                                   4176.3352
    ## 498      European Union (27) 2001                                   5115.4507
    ## 499                  Finland 2001                                     74.5584
    ## 500                   France 2001                                    560.9417
    ## 501                  Germany 2001                                   1055.4223
    ## 502                   Greece 2001                                    127.2218
    ## 503                  Hungary 2001                                     80.2514
    ## 504                  Iceland 2001                                      3.8425
    ## 505                  Ireland 2001                                     70.1705
    ## 506                    Italy 2001                                    557.2281
    ## 507                    Japan 2001                                   1317.1245
    ## 508                   Latvia 2001                                      10.691
    ## 509            Liechtenstein 2001                                      0.2547
    ## 510                Lithuania 2001                                     20.7133
    ## 511               Luxembourg 2001                                     10.2597
    ## 512                    Malta 2001                                      2.6659
    ## 513                   Monaco 2001                                      0.1189
    ## 514              Netherlands 2001                                    214.5296
    ## 515              New Zealand 2001                                     72.0407
    ## 516                   Norway 2001                                     55.2573
    ## 517                   Poland 2001                                    382.0645
    ## 518                 Portugal 2001                                     84.1269
    ## 519                  Romania 2001                                    136.2594
    ## 520       Russian Federation 2001                                   2070.1863
    ## 521                 Slovakia 2001                                     52.3551
    ## 522                 Slovenia 2001                                      19.783
    ## 523                    Spain 2001                                    379.2222
    ## 524                   Sweden 2001                                       69.67
    ## 525              Switzerland 2001                                     52.7988
    ## 526                   Turkey 2001                                    279.2458
    ## 527                  Ukraine 2001                                    400.2432
    ## 528           United Kingdom 2001                                    681.3026
    ## 529 United States of America 2001                                   6935.5835
    ## 530                Australia 2002                                    505.4432
    ## 531                  Austria 2002                                     85.8814
    ## 532                  Belarus 2002                                     76.7879
    ## 533                  Belgium 2002                                     144.295
    ## 534                 Bulgaria 2002                                     59.6765
    ## 535                   Canada 2002                                    717.8248
    ## 536                  Croatia 2002                                     28.5576
    ## 537                   Cyprus 2002                                      8.7225
    ## 538           Czech Republic 2002                                    141.5393
    ## 539                  Denmark 2002                                     70.6527
    ## 540                  Estonia 2002                                     16.9354
    ## 541      European Union (15) 2002                                   4152.1903
    ## 542      European Union (27) 2002                                   5070.1975
    ## 543                  Finland 2002                                     76.7263
    ## 544                   France 2002                                    556.2269
    ## 545                  Germany 2002                                   1034.1638
    ## 546                   Greece 2002                                    127.0479
    ## 547                  Hungary 2002                                     78.1435
    ## 548                  Iceland 2002                                      3.8758
    ## 549                  Ireland 2002                                      68.259
    ## 550                    Italy 2002                                    558.4026
    ## 551                    Japan 2002                                   1349.1509
    ## 552                   Latvia 2002                                     10.6457
    ## 553            Liechtenstein 2002                                      0.2603
    ## 554                Lithuania 2002                                     21.2483
    ## 555               Luxembourg 2002                                     11.0372
    ## 556                    Malta 2002                                      2.7002
    ## 557                   Monaco 2002                                      0.1173
    ## 558              Netherlands 2002                                    213.5354
    ## 559              New Zealand 2002                                     72.7061
    ## 560                   Norway 2002                                     54.1036
    ## 561                   Poland 2002                                    369.0364
    ## 562                 Portugal 2002                                     88.3165
    ## 563                  Romania 2002                                     138.217
    ## 564       Russian Federation 2002                                   2072.0981
    ## 565                 Slovakia 2002                                     51.2053
    ## 566                 Slovenia 2002                                     19.9372
    ## 567                    Spain 2002                                    395.6681
    ## 568                   Sweden 2002                                     70.3659
    ## 569              Switzerland 2002                                     51.7282
    ## 570                   Turkey 2002                                    287.2176
    ## 571                  Ukraine 2002                                    403.0984
    ## 572           United Kingdom 2002                                    661.0824
    ## 573 United States of America 2002                                   6979.3405
    ## 574                Australia 2003                                    509.6304
    ## 575                  Austria 2003                                     91.8755
    ## 576                  Belarus 2003                                     78.5616
    ## 577                  Belgium 2003                                    146.2261
    ## 578                 Bulgaria 2003                                     64.4348
    ## 579                   Canada 2003                                    738.0439
    ## 580                  Croatia 2003                                     29.9628
    ## 581                   Cyprus 2003                                      9.0994
    ## 582           Czech Republic 2003                                    144.5824
    ## 583                  Denmark 2003                                     75.5113
    ## 584                  Estonia 2003                                     18.8391
    ## 585      European Union (15) 2003                                   4206.1999
    ## 586      European Union (27) 2003                                   5157.8898
    ## 587                  Finland 2003                                      84.631
    ## 588                   France 2003                                     562.257
    ## 589                  Germany 2003                                   1032.0824
    ## 590                   Greece 2003                                    130.8818
    ## 591                  Hungary 2003                                     81.2348
    ## 592                  Iceland 2003                                      3.8523
    ## 593                  Ireland 2003                                     68.3313
    ## 594                    Italy 2003                                    573.7271
    ## 595                    Japan 2003                                   1352.9039
    ## 596                   Latvia 2003                                     10.8716
    ## 597            Liechtenstein 2003                                      0.2705
    ## 598                Lithuania 2003                                     21.4512
    ## 599               Luxembourg 2003                                     11.4256
    ## 600                    Malta 2003                                      2.8881
    ## 601                   Monaco 2003                                      0.1121
    ## 602              Netherlands 2003                                    214.3149
    ## 603              New Zealand 2003                                     75.1767
    ## 604                   Norway 2003                                      54.843
    ## 605                   Poland 2003                                    382.0139
    ## 606                 Portugal 2003                                     82.9752
    ## 607                  Romania 2003                                    145.0847
    ## 608       Russian Federation 2003                                   2110.3908
    ## 609                 Slovakia 2003                                     51.5442
    ## 610                 Slovenia 2003                                     19.6457
    ## 611                    Spain 2003                                      402.63
    ## 612                   Sweden 2003                                     70.7971
    ## 613              Switzerland 2003                                     52.8523
    ## 614                   Turkey 2003                                    303.7731
    ## 615                  Ukraine 2003                                    416.4905
    ## 616           United Kingdom 2003                                    668.0152
    ## 617 United States of America 2003                                   7019.4714
    ## 618                Australia 2004                                    525.2847
    ## 619                  Austria 2004                                     91.5195
    ## 620                  Belarus 2004                                     82.8959
    ## 621                  Belgium 2004                                    147.1649
    ## 622                 Bulgaria 2004                                     63.6382
    ## 623                   Canada 2004                                    744.3897
    ## 624                  Croatia 2004                                     30.0898
    ## 625                   Cyprus 2004                                      9.3151
    ## 626           Czech Republic 2004                                    145.9495
    ## 627                  Denmark 2004                                     69.7177
    ## 628                  Estonia 2004                                     19.1765
    ## 629      European Union (15) 2004                                   4206.6224
    ## 630      European Union (27) 2004                                   5161.6396
    ## 631                  Finland 2004                                     80.6191
    ## 632                   France 2004                                    560.5527
    ## 633                  Germany 2004                                   1019.5739
    ## 634                   Greece 2004                                    131.3427
    ## 635                  Hungary 2004                                     80.4926
    ## 636                  Iceland 2004                                      3.9049
    ## 637                  Ireland 2004                                     68.2075
    ## 638                    Italy 2004                                    576.9894
    ## 639                    Japan 2004                                   1348.8064
    ## 640                   Latvia 2004                                     11.0094
    ## 641            Liechtenstein 2004                                      0.2713
    ## 642                Lithuania 2004                                     22.2415
    ## 643               Luxembourg 2004                                     12.8426
    ## 644                    Malta 2004                                      2.8978
    ## 645                   Monaco 2004                                       0.106
    ## 646              Netherlands 2004                                    215.5146
    ## 647              New Zealand 2004                                     74.4981
    ## 648                   Norway 2004                                     55.4179
    ## 649                   Poland 2004                                    386.6551
    ## 650                 Portugal 2004                                     85.6804
    ## 651                  Romania 2004                                    142.3008
    ## 652       Russian Federation 2004                                   2145.2182
    ## 653                 Slovakia 2004                                     51.3765
    ## 654                 Slovenia 2004                                     19.9642
    ## 655                    Spain 2004                                    418.5287
    ## 656                   Sweden 2004                                     70.0089
    ## 657              Switzerland 2004                                     53.5304
    ## 658                   Turkey 2004                                    313.2718
    ## 659                  Ukraine 2004                                    417.1392
    ## 660           United Kingdom 2004                                     667.976
    ## 661 United States of America 2004                                   7147.2662
    ## 662                Australia 2005                                    529.3209
    ## 663                  Austria 2005                                     92.8945
    ## 664                  Belarus 2005                                     84.1737
    ## 665                  Belgium 2005                                    143.2689
    ## 666                 Bulgaria 2005                                     63.7492
    ## 667                   Canada 2005                                    737.4568
    ## 668                  Croatia 2005                                     30.4538
    ## 669                   Cyprus 2005                                      9.3111
    ## 670           Czech Republic 2005                                    145.2594
    ## 671                  Denmark 2005                                      65.396
    ## 672                  Estonia 2005                                     18.4776
    ## 673      European Union (15) 2005                                   4172.7762
    ## 674      European Union (27) 2005                                   5129.1563
    ## 675                  Finland 2005                                      68.748
    ## 676                   France 2005                                    563.0652
    ## 677                  Germany 2005                                    997.9294
    ## 678                   Greece 2005                                    134.9207
    ## 679                  Hungary 2005                                     79.4537
    ## 680                  Iceland 2005                                      3.8325
    ## 681                  Ireland 2005                                     69.4506
    ## 682                    Italy 2005                                    574.4334
    ## 683                    Japan 2005                                   1351.4067
    ## 684                   Latvia 2005                                     11.0977
    ## 685            Liechtenstein 2005                                      0.2718
    ## 686                Lithuania 2005                                     23.3433
    ## 687               Luxembourg 2005                                     13.0964
    ## 688                    Malta 2005                                       2.992
    ## 689                   Monaco 2005                                      0.1047
    ## 690              Netherlands 2005                                    209.4743
    ## 691              New Zealand 2005                                     76.6444
    ## 692                   Norway 2005                                     54.2757
    ## 693                   Poland 2005                                    390.2307
    ## 694                 Portugal 2005                                     88.0372
    ## 695                  Romania 2005                                    141.5605
    ## 696       Russian Federation 2005                                   2128.7497
    ## 697                 Slovakia 2005                                     50.5963
    ## 698                 Slovenia 2005                                     20.3085
    ## 699                    Spain 2005                                    432.8344
    ## 700                   Sweden 2005                                     67.2683
    ## 701              Switzerland 2005                                     54.2274
    ## 702                   Turkey 2005                                    330.9824
    ## 703                  Ukraine 2005                                    417.2967
    ## 704           United Kingdom 2005                                    661.9312
    ## 705 United States of America 2005                                   7169.8993
    ## 706                Australia 2006                                    534.2012
    ## 707                  Austria 2006                                     90.0922
    ## 708                  Belarus 2006                                      88.044
    ## 709                  Belgium 2006                                     138.505
    ## 710                 Bulgaria 2006                                     64.5664
    ## 711                   Canada 2006                                     727.196
    ## 712                  Croatia 2006                                     30.8961
    ## 713                   Cyprus 2006                                      9.5583
    ## 714           Czech Republic 2006                                    147.0381
    ## 715                  Denmark 2006                                     73.2591
    ## 716                  Estonia 2006                                     17.9287
    ## 717      European Union (15) 2006                                   4138.4443
    ## 718      European Union (27) 2006                                   5116.8655
    ## 719                  Finland 2006                                     80.0782
    ## 720                   France 2006                                    551.1131
    ## 721                  Germany 2006                                   1000.3877
    ## 722                   Greece 2006                                     131.343
    ## 723                  Hungary 2006                                     78.0485
    ## 724                  Iceland 2006                                      4.3635
    ## 725                  Ireland 2006                                     69.0255
    ## 726                    Italy 2006                                     563.668
    ## 727                    Japan 2006                                   1333.4996
    ## 728                   Latvia 2006                                     11.5924
    ## 729            Liechtenstein 2006                                       0.274
    ## 730                Lithuania 2006                                      23.748
    ## 731               Luxembourg 2006                                     12.9478
    ## 732                    Malta 2006                                       2.992
    ## 733                   Monaco 2006                                      0.0942
    ## 734              Netherlands 2006                                    205.5426
    ## 735              New Zealand 2006                                     76.5171
    ## 736                   Norway 2006                                     54.1007
    ## 737                   Poland 2006                                    406.0115
    ## 738                 Portugal 2006                                     83.0077
    ## 739                  Romania 2006                                    145.8801
    ## 740       Russian Federation 2006                                   2196.0975
    ## 741                 Slovakia 2006                                     50.5029
    ## 742                 Slovenia 2006                                     20.5543
    ## 743                    Spain 2006                                    424.2475
    ## 744                   Sweden 2006                                      67.164
    ## 745              Switzerland 2006                                     53.8814
    ## 746                   Turkey 2006                                    350.7388
    ## 747                  Ukraine 2006                                    433.7123
    ## 748           United Kingdom 2006                                     658.333
    ## 749 United States of America 2006                                   7109.3381
    ## 750                Australia 2007                                    542.5307
    ## 751                  Austria 2007                                     87.2462
    ## 752                  Belarus 2007                                     87.3117
    ## 753                  Belgium 2007                                      133.67
    ## 754                 Bulgaria 2007                                      68.488
    ## 755                   Canada 2007                                      748.84
    ## 756                  Croatia 2007                                     32.4301
    ## 757                   Cyprus 2007                                      9.8081
    ## 758           Czech Republic 2007                                    147.6248
    ## 759                  Denmark 2007                                     68.6783
    ## 760                  Estonia 2007                                      21.047
    ## 761      European Union (15) 2007                                   4074.9038
    ## 762      European Union (27) 2007                                   5059.0337
    ## 763                  Finland 2007                                     78.4169
    ## 764                   France 2007                                    541.0476
    ## 765                  Germany 2007                                    975.9461
    ## 766                   Greece 2007                                    134.1862
    ## 767                  Hungary 2007                                     76.0397
    ## 768                  Iceland 2007                                      4.5917
    ## 769                  Ireland 2007                                     68.4059
    ## 770                    Italy 2007                                    555.3674
    ## 771                    Japan 2007                                   1365.2273
    ## 772                   Latvia 2007                                     12.0854
    ## 773            Liechtenstein 2007                                      0.2442
    ## 774                Lithuania 2007                                     26.1574
    ## 775               Luxembourg 2007                                     12.3589
    ## 776                    Malta 2007                                      3.1056
    ## 777                   Monaco 2007                                      0.0998
    ## 778              Netherlands 2007                                     204.199
    ## 779              New Zealand 2007                                     74.4611
    ## 780                   Norway 2007                                     56.0113
    ## 781                   Poland 2007                                     407.861
    ## 782                 Portugal 2007                                     80.5103
    ## 783                  Romania 2007                                    142.7036
    ## 784       Russian Federation 2007                                    2199.528
    ## 785                 Slovakia 2007                                     48.5197
    ## 786                 Slovenia 2007                                     20.6897
    ## 787                    Spain 2007                                    432.0093
    ## 788                   Sweden 2007                                     65.5056
    ## 789              Switzerland 2007                                     51.9476
    ## 790                   Turkey 2007                                    380.9476
    ## 791                  Ukraine 2007                                    436.3021
    ## 792           United Kingdom 2007                                    648.0357
    ## 793 United States of America 2007                                   7225.9337
    ## 794                Australia 2008                                    550.3388
    ## 795                  Austria 2008                                     86.9624
    ## 796                  Belarus 2008                                     90.5991
    ## 797                  Belgium 2008                                    136.6454
    ## 798                 Bulgaria 2008                                     66.9427
    ## 799                   Canada 2008                                    730.9157
    ## 800                  Croatia 2008                                     31.1667
    ## 801                   Cyprus 2008                                     10.0655
    ## 802           Czech Republic 2008                                    142.1464
    ## 803                  Denmark 2008                                     65.2371
    ## 804                  Estonia 2008                                     19.6177
    ## 805      European Union (15) 2008                                   3989.3106
    ## 806      European Union (27) 2008                                   4952.4118
    ## 807                  Finland 2008                                     70.2103
    ## 808                   France 2008                                     536.318
    ## 809                  Germany 2008                                    974.9927
    ## 810                   Greece 2008                                    130.3339
    ## 811                  Hungary 2008                                     73.5882
    ## 812                  Iceland 2008                                      4.9936
    ## 813                  Ireland 2008                                      67.608
    ## 814                    Italy 2008                                    541.1775
    ## 815                    Japan 2008                                   1281.9526
    ## 816                   Latvia 2008                                     11.5625
    ## 817            Liechtenstein 2008                                      0.2642
    ## 818                Lithuania 2008                                     24.9193
    ## 819               Luxembourg 2008                                     12.1876
    ## 820                    Malta 2008                                      3.0608
    ## 821                   Monaco 2008                                      0.0966
    ## 822              Netherlands 2008                                    203.3131
    ## 823              New Zealand 2008                                     74.0662
    ## 824                   Norway 2008                                     54.3438
    ## 825                   Poland 2008                                     400.214
    ## 826                 Portugal 2008                                     78.4817
    ## 827                  Romania 2008                                    140.4642
    ## 828       Russian Federation 2008                                   2237.4202
    ## 829                 Slovakia 2008                                     49.1138
    ## 830                 Slovenia 2008                                     21.4062
    ## 831                    Spain 2008                                    398.8764
    ## 832                   Sweden 2008                                     63.4072
    ## 833              Switzerland 2008                                     53.6826
    ## 834                   Turkey 2008                                    367.2073
    ## 835                  Ukraine 2008                                     421.261
    ## 836           United Kingdom 2008                                    633.9822
    ## 837 United States of America 2008                                   7021.5689
    ## 838                Australia 2009                                     549.123
    ## 839                  Austria 2009                                      79.956
    ## 840                  Belarus 2009                                     87.8788
    ## 841                  Belgium 2009                                    124.4677
    ## 842                 Bulgaria 2009                                     57.8052
    ## 843                   Canada 2009                                    689.0302
    ## 844                  Croatia 2009                                     29.1587
    ## 845                   Cyprus 2009                                      9.8035
    ## 846           Czech Republic 2009                                    133.4862
    ## 847                  Denmark 2009                                      62.253
    ## 848                  Estonia 2009                                     16.2616
    ## 849      European Union (15) 2009                                   3710.1569
    ## 850      European Union (27) 2009                                   4593.4423
    ## 851                  Finland 2009                                     66.0502
    ## 852                   France 2009                                     513.003
    ## 853                  Germany 2009                                    911.3081
    ## 854                   Greece 2009                                    123.6339
    ## 855                  Hungary 2009                                     67.3807
    ## 856                  Iceland 2009                                      4.7509
    ## 857                  Ireland 2009                                     61.8249
    ## 858                    Italy 2009                                    490.7797
    ## 859                    Japan 2009                                   1206.8479
    ## 860                   Latvia 2009                                     10.8822
    ## 861            Liechtenstein 2009                                       0.248
    ## 862                Lithuania 2009                                     20.4231
    ## 863               Luxembourg 2009                                       11.69
    ## 864                    Malta 2009                                       2.979
    ## 865                   Monaco 2009                                      0.0914
    ## 866              Netherlands 2009                                    197.8655
    ## 867              New Zealand 2009                                     71.4409
    ## 868                   Norway 2009                                     51.7733
    ## 869                   Poland 2009                                    380.5868
    ## 870                 Portugal 2009                                     75.2157
    ## 871                  Romania 2009                                    120.2944
    ## 872       Russian Federation 2009                                   2121.4223
    ## 873                 Slovakia 2009                                     43.9561
    ## 874                 Slovenia 2009                                     19.4267
    ## 875                    Spain 2009                                    362.7132
    ## 876                   Sweden 2009                                     59.3378
    ## 877              Switzerland 2009                                     52.3504
    ## 878                   Turkey 2009                                    370.0121
    ## 879                  Ukraine 2009                                    365.3066
    ## 880           United Kingdom 2009                                     580.382
    ## 881 United States of America 2009                                    6566.198
    ## 882                Australia 2010                                    548.7444
    ## 883                  Austria 2010                                     85.0122
    ## 884                  Belarus 2010                                     89.4463
    ## 885                  Belgium 2010                                    131.7823
    ## 886                 Bulgaria 2010                                     60.3524
    ## 887                   Canada 2010                                    700.8493
    ## 888                  Croatia 2010                                     28.6155
    ## 889                   Cyprus 2010                                      9.4435
    ## 890           Czech Republic 2010                                    137.4226
    ## 891                  Denmark 2010                                     62.7786
    ## 892                  Estonia 2010                                     19.9888
    ## 893      European Union (15) 2010                                   3790.2247
    ## 894      European Union (27) 2010                                   4705.2002
    ## 895                  Finland 2010                                     74.5367
    ## 896                   France 2010                                    519.8894
    ## 897                  Germany 2010                                    943.5184
    ## 898                   Greece 2010                                    117.2781
    ## 899                  Hungary 2010                                     67.9454
    ## 900                  Iceland 2010                                       4.618
    ## 901                  Ireland 2010                                     61.4926
    ## 902                    Italy 2010                                    500.3139
    ## 903                    Japan 2010                                   1257.3806
    ## 904                   Latvia 2010                                     12.0345
    ## 905            Liechtenstein 2010                                      0.2341
    ## 906                Lithuania 2010                                     21.1206
    ## 907               Luxembourg 2010                                     12.2521
    ## 908                    Malta 2010                                      2.9979
    ## 909                   Monaco 2010                                       0.088
    ## 910              Netherlands 2010                                    209.1766
    ## 911              New Zealand 2010                                     71.8478
    ## 912                   Norway 2010                                     54.3173
    ## 913                   Poland 2010                                    401.6704
    ## 914                 Portugal 2010                                     71.3824
    ## 915                  Romania 2010                                    116.6212
    ## 916       Russian Federation 2010                                   2217.2709
    ## 917                 Slovakia 2010                                     45.8964
    ## 918                 Slovenia 2010                                     19.4819
    ## 919                    Spain 2010                                    348.6413
    ## 920                   Sweden 2010                                     65.4874
    ## 921              Switzerland 2010                                     54.0875
    ## 922                   Turkey 2010                                    402.1027
    ## 923                  Ukraine 2010                                    383.2114
    ## 924           United Kingdom 2010                                    597.7793
    ## 925 United States of America 2010                                   6790.6421
    ## 926                Australia 2011                                    552.2864
    ## 927                  Austria 2011                                     82.8416
    ## 928                  Belarus 2011                                     87.3198
    ## 929                  Belgium 2011                                    120.1715
    ## 930                 Bulgaria 2011                                     66.1333
    ## 931                   Canada 2011                                    701.7912
    ## 932                  Croatia 2011                                     28.2564
    ## 933                   Cyprus 2011                                      9.1544
    ## 934           Czech Republic 2011                                    133.4955
    ## 935                  Denmark 2011                                     57.7483
    ## 936                  Estonia 2011                                     20.9556
    ## 937      European Union (15) 2011                                   3630.6572
    ## 938      European Union (27) 2011                                   4550.2122
    ## 939                  Finland 2011                                     67.0189
    ## 940                   France 2011                                    491.4965
    ## 941                  Germany 2011                                    916.4951
    ## 942                   Greece 2011                                     115.045
    ## 943                  Hungary 2011                                     66.1477
    ## 944                  Iceland 2011                                      4.4132
    ## 945                  Ireland 2011                                     57.5125
    ## 946                    Italy 2011                                     488.792
    ## 947                    Japan 2011                                   1307.7284
    ## 948                   Latvia 2011                                     11.4942
    ## 949            Liechtenstein 2011                                       0.222
    ## 950                Lithuania 2011                                     21.6117
    ## 951               Luxembourg 2011                                     12.0979
    ## 952                    Malta 2011                                      3.0212
    ## 953                   Monaco 2011                                      0.0853
    ## 954              Netherlands 2011                                    194.3789
    ## 955              New Zealand 2011                                     72.8349
    ## 956                   Norway 2011                                     53.3642
    ## 957                   Poland 2011                                    399.3895
    ## 958                 Portugal 2011                                     69.9864
    ## 959                  Romania 2011                                    123.3455
    ## 960       Russian Federation 2011                                   2320.8344
    ## 961                 Slovakia 2011                                      45.297
    ## 962                 Slovenia 2011                                     19.5094
    ## 963                    Spain 2011                                    350.4837
    ## 964                   Sweden 2011                                     61.4489
    ## 965              Switzerland 2011                                     50.0097
    ## 966                   Turkey 2011                                    422.4158
    ## 967                  Ukraine 2011                                    401.5763
    ## 968           United Kingdom 2011                                    556.4578
    ## 969 United States of America 2011                                   6665.7009
    ##                                             X.2
    ## 1   Total GHG Emissions Including LUCF (MtCO2e)
    ## 2                                      524.0457
    ## 3                                       68.2302
    ## 4                                      110.5768
    ## 5                                      142.1811
    ## 6                                        95.492
    ## 7                                      529.4513
    ## 8                                        25.236
    ## 9                                        5.9519
    ## 10                                     192.4211
    ## 11                                      75.5609
    ## 12                                      31.6934
    ## 13                                    4117.7021
    ## 14                                    5319.5404
    ## 15                                      55.2755
    ## 16                                     536.6973
    ## 17                                    1214.5056
    ## 18                                     102.0898
    ## 19                                      96.9618
    ## 20                                       4.6794
    ## 21                                      52.5849
    ## 22                                     506.8304
    ## 23                                    1197.1389
    ## 24                                       4.0174
    ## 25                                       0.2209
    ## 26                                      44.4673
    ## 27                                      13.2488
    ## 28                                         1.95
    ## 29                                       0.1079
    ## 30                                      214.849
    ## 31                                      31.5304
    ## 32                                      35.0148
    ## 33                                     440.6854
    ## 34                                      69.4486
    ## 35                                     217.0482
    ## 36                                    3436.4585
    ## 37                                      61.7627
    ## 38                                        9.387
    ## 39                                      263.683
    ## 40                                      35.5659
    ## 41                                      49.8174
    ## 42                                     173.0533
    ## 43                                     860.1565
    ## 44                                     774.8059
    ## 45                                    5388.7456
    ## 46                                     572.7432
    ## 47                                      66.5522
    ## 48                                     101.1362
    ## 49                                     144.4438
    ## 50                                      72.8115
    ## 51                                     547.4653
    ## 52                                      16.8463
    ## 53                                       6.1978
    ## 54                                     173.1093
    ## 55                                      84.5885
    ## 56                                      28.5198
    ## 57                                    4099.7437
    ## 58                                    5180.7513
    ## 59                                      39.3586
    ## 60                                     564.0934
    ## 61                                    1167.4015
    ## 62                                     101.5853
    ## 63                                      89.0897
    ## 64                                       4.5167
    ## 65                                      53.3022
    ## 66                                     494.5987
    ## 67                                    1204.2216
    ## 68                                        1.382
    ## 69                                       0.2288
    ## 70                                      45.9181
    ## 71                                      13.6192
    ## 72                                       2.1263
    ## 73                                       0.1092
    ## 74                                     219.0552
    ## 75                                      31.3479
    ## 76                                      31.8085
    ## 77                                     429.4323
    ## 78                                      71.3584
    ## 79                                     171.5324
    ## 80                                    3265.8522
    ## 81                                      52.6036
    ## 82                                       8.2849
    ## 83                                     271.3587
    ## 84                                      34.7927
    ## 85                                      51.3694
    ## 86                                     183.5934
    ## 87                                     740.4161
    ## 88                                     781.6059
    ## 89                                    5336.2435
    ## 90                                     510.1688
    ## 91                                      64.5889
    ## 92                                       93.198
    ## 93                                     142.8666
    ## 94                                      66.8737
    ## 95                                      516.047
    ## 96                                      14.6611
    ## 97                                        6.622
    ## 98                                     154.8221
    ## 99                                      80.7506
    ## 100                                     18.0594
    ## 101                                   4019.3954
    ## 102                                    4991.596
    ## 103                                     43.4022
    ## 104                                    552.6141
    ## 105                                   1117.4447
    ## 106                                    102.7534
    ## 107                                     78.8059
    ## 108                                      4.4072
    ## 109                                     53.6378
    ## 110                                    493.1744
    ## 111                                   1218.8882
    ## 112                                     -3.4483
    ## 113                                      0.2292
    ## 114                                      26.045
    ## 115                                     13.0259
    ## 116                                      2.2365
    ## 117                                      0.1163
    ## 118                                    218.0017
    ## 119                                     33.8223
    ## 120                                     30.0973
    ## 121                                    425.1914
    ## 122                                     71.5639
    ## 123                                    143.3853
    ## 124                                   2671.3806
    ## 125                                     45.4353
    ## 126                                      8.1725
    ## 127                                    279.3346
    ## 128                                     36.5747
    ## 129                                     51.3627
    ## 130                                    203.5935
    ## 131                                    662.3742
    ## 132                                    757.7179
    ## 133                                   5469.0404
    ## 134                                    443.0788
    ## 135                                     64.1978
    ## 136                                     85.1187
    ## 137                                      141.99
    ## 138                                     65.8624
    ## 139                                     591.211
    ## 140                                     14.7252
    ## 141                                      6.9913
    ## 142                                    150.0038
    ## 143                                     79.4705
    ## 144                                     11.3704
    ## 145                                   3954.3812
    ## 146                                   4894.9948
    ## 147                                     47.6408
    ## 148                                    517.3733
    ## 149                                   1108.0313
    ## 150                                    101.4653
    ## 151                                     77.2289
    ## 152                                      4.4562
    ## 153                                      53.656
    ## 154                                    499.9567
    ## 155                                   1210.0129
    ## 156                                     -5.9233
    ## 157                                      0.2365
    ## 158                                      18.807
    ## 159                                      13.028
    ## 160                                      2.2373
    ## 161                                      0.1162
    ## 162                                    222.7357
    ## 163                                     33.7883
    ## 164                                     30.2592
    ## 165                                    424.5308
    ## 166                                     68.6955
    ## 167                                    139.4218
    ## 168                                   2447.0195
    ## 169                                     41.6721
    ## 170                                       8.411
    ## 171                                    268.0264
    ## 172                                     40.3615
    ## 173                                     47.3364
    ## 174                                    203.9373
    ## 175                                    586.5606
    ## 176                                    735.7564
    ## 177                                   5613.3765
    ## 178                                    441.3747
    ## 179                                     66.1888
    ## 180                                     59.9958
    ## 181                                    147.7014
    ## 182                                     62.4124
    ## 183                                    605.5517
    ## 184                                     13.9743
    ## 185                                      7.4504
    ## 186                                    142.3077
    ## 187                                     85.0094
    ## 188                                     11.5204
    ## 189                                   3947.5967
    ## 190                                   4869.3493
    ## 191                                     59.9101
    ## 192                                    517.0332
    ## 193                                   1088.4912
    ## 194                                    104.5769
    ## 195                                     76.3282
    ## 196                                      4.3759
    ## 197                                     55.4306
    ## 198                                     479.915
    ## 199                                   1279.8183
    ## 200                                     -8.9263
    ## 201                                      0.2227
    ## 202                                      18.553
    ## 203                                     12.3691
    ## 204                                       2.353
    ## 205                                      0.1183
    ## 206                                    222.6757
    ## 207                                     36.1819
    ## 208                                     33.3042
    ## 209                                    423.3662
    ## 210                                     67.6792
    ## 211                                    137.4391
    ## 212                                   2106.4834
    ## 213                                     40.3272
    ## 214                                      8.6213
    ## 215                                      282.22
    ## 216                                     42.8472
    ## 217                                     47.5806
    ## 218                                    198.4008
    ## 219                                    495.1675
    ## 220                                    723.5641
    ## 221                                   5643.4903
    ## 222                                    462.8477
    ## 223                                     68.2292
    ## 224                                     51.6179
    ## 225                                    149.6902
    ## 226                                     62.6611
    ## 227                                    832.9467
    ## 228                                     13.9821
    ## 229                                      7.3165
    ## 230                                    143.4663
    ## 231                                      80.938
    ## 232                                      9.4418
    ## 233                                   3983.6926
    ## 234                                   4917.6724
    ## 235                                     56.7465
    ## 236                                    526.6843
    ## 237                                   1082.9575
    ## 238                                    106.1348
    ## 239                                     74.7204
    ## 240                                       4.395
    ## 241                                     57.1726
    ## 242                                    499.8578
    ## 243                                   1257.1326
    ## 244                                     -9.0445
    ## 245                                      0.2261
    ## 246                                     18.6853
    ## 247                                      9.9394
    ## 248                                      2.3218
    ## 249                                      0.1157
    ## 250                                    226.0463
    ## 251                                     38.8674
    ## 252                                     30.4348
    ## 253                                    426.8208
    ## 254                                      75.808
    ## 255                                    145.5981
    ## 256                                   1979.7034
    ## 257                                     42.4334
    ## 258                                      9.5587
    ## 259                                    293.4403
    ## 260                                     42.7952
    ## 261                                     47.5745
    ## 262                                    218.7468
    ## 263                                    449.8092
    ## 264                                    715.6047
    ## 265                                   5758.8496
    ## 266                                    476.5976
    ## 267                                     74.3476
    ## 268                                     55.6195
    ## 269                                    154.1776
    ## 270                                     64.8933
    ## 271                                    635.7608
    ## 272                                     14.8783
    ## 273                                      7.7252
    ## 274                                    147.0591
    ## 275                                     92.4899
    ## 276                                     10.3038
    ## 277                                   4050.2317
    ## 278                                   5018.8312
    ## 279                                     53.0912
    ## 280                                    540.0953
    ## 281                                   1101.8001
    ## 282                                    109.5741
    ## 283                                     80.7305
    ## 284                                      4.4727
    ## 285                                     59.3651
    ## 286                                     493.575
    ## 287                                   1266.4269
    ## 288                                     -9.4888
    ## 289                                      0.2289
    ## 290                                     25.1681
    ## 291                                       9.828
    ## 292                                      2.3721
    ## 293                                      0.1206
    ## 294                                     233.966
    ## 295                                     41.8518
    ## 296                                     33.9815
    ## 297                                    438.8876
    ## 298                                     70.3917
    ## 299                                    148.2145
    ## 300                                   1844.6498
    ## 301                                      42.472
    ## 302                                     10.2622
    ## 303                                    285.1585
    ## 304                                     45.2999
    ## 305                                      47.267
    ## 306                                    239.8965
    ## 307                                    395.4613
    ## 308                                    735.6111
    ## 309                                    5948.157
    ## 310                                    478.5037
    ## 311                                     65.2116
    ## 312                                     60.3022
    ## 313                                    145.0867
    ## 314                                     61.2311
    ## 315                                    610.0417
    ## 316                                     16.8554
    ## 317                                      7.7935
    ## 318                                    145.1031
    ## 319                                     84.3427
    ## 320                                     10.8463
    ## 321                                   3985.2174
    ## 322                                   4923.7955
    ## 323                                     56.4654
    ## 324                                    530.4849
    ## 325                                   1065.9252
    ## 326                                    114.5317
    ## 327                                     78.6685
    ## 328                                      4.6085
    ## 329                                      60.105
    ## 330                                    508.4693
    ## 331                                   1259.5179
    ## 332                                     -8.1804
    ## 333                                      0.2415
    ## 334                                     23.2442
    ## 335                                      9.0834
    ## 336                                      2.4399
    ## 337                                      0.1206
    ## 338                                     227.611
    ## 339                                     43.9418
    ## 340                                       34.31
    ## 341                                    430.6515
    ## 342                                     74.5404
    ## 343                                    133.3377
    ## 344                                   1645.1788
    ## 345                                     42.7886
    ## 346                                     10.6541
    ## 347                                    305.1371
    ## 348                                     37.8309
    ## 349                                     45.7161
    ## 350                                    252.9628
    ## 351                                     393.222
    ## 352                                    709.0954
    ## 353                                   6033.8629
    ## 354                                     526.865
    ## 355                                     66.4734
    ## 356                                     60.4854
    ## 357                                    150.7658
    ## 358                                     56.3339
    ## 359                                    799.9119
    ## 360                                     17.1265
    ## 361                                      8.0571
    ## 362                                    137.8009
    ## 363                                     79.4064
    ## 364                                     11.1824
    ## 365                                   4011.8126
    ## 366                                   4883.6555
    ## 367                                     55.0442
    ## 368                                    545.5231
    ## 369                                   1040.3113
    ## 370                                    119.8492
    ## 371                                     76.8802
    ## 372                                      4.7184
    ## 373                                     63.0558
    ## 374                                    522.8938
    ## 375                                   1217.1637
    ## 376                                      -7.695
    ## 377                                      0.2532
    ## 378                                     16.1438
    ## 379                                      8.4491
    ## 380                                      2.4509
    ## 381                                      0.1186
    ## 382                                    228.3748
    ## 383                                     40.5672
    ## 384                                     33.5908
    ## 385                                    401.4927
    ## 386                                     80.4714
    ## 387                                    117.1855
    ## 388                                   1609.7655
    ## 389                                     41.5522
    ## 390                                     10.4583
    ## 391                                    314.3052
    ## 392                                     39.2193
    ## 393                                     47.3229
    ## 394                                    252.4145
    ## 395                                    369.1222
    ## 396                                    706.7329
    ## 397                                    6110.564
    ## 398                                    489.0572
    ## 399                                     61.8807
    ## 400                                     50.1076
    ## 401                                    144.5246
    ## 402                                     49.5487
    ## 403                                    709.4167
    ## 404                                     18.0205
    ## 405                                      8.1583
    ## 406                                    129.2764
    ## 407                                     78.2843
    ## 408                                     12.7933
    ## 409                                   3931.8914
    ## 410                                   4760.1826
    ## 411                                     51.3108
    ## 412                                    528.5127
    ## 413                                   1006.5335
    ## 414                                    119.4762
    ## 415                                     78.6922
    ## 416                                      4.9284
    ## 417                                     64.1413
    ## 418                                    520.2215
    ## 419                                   1238.1674
    ## 420                                     -8.6339
    ## 421                                      0.2525
    ## 422                                     13.5556
    ## 423                                      8.7437
    ## 424                                      2.5379
    ## 425                                      0.1194
    ## 426                                    216.2717
    ## 427                                     42.8016
    ## 428                                     39.6233
    ## 429                                     390.133
    ## 430                                     87.5984
    ## 431                                    102.1017
    ## 432                                   1605.5317
    ## 433                                     40.3284
    ## 434                                      9.7997
    ## 435                                    341.7725
    ## 436                                     36.3937
    ## 437                                     49.0542
    ## 438                                    252.8017
    ## 439                                    345.6246
    ## 440                                     675.251
    ## 441                                   6251.2948
    ## 442                                    556.3511
    ## 443                                     65.2623
    ## 444                                     48.2623
    ## 445                                    145.3099
    ## 446                                     50.5825
    ## 447                                    665.3882
    ## 448                                      18.571
    ## 449                                      8.4235
    ## 450                                    138.3618
    ## 451                                     72.8674
    ## 452                                     18.2419
    ## 453                                   3960.1385
    ## 454                                   4786.2109
    ## 455                                     48.8782
    ## 456                                    536.5641
    ## 457                                   1005.7935
    ## 458                                    123.5086
    ## 459                                     77.7572
    ## 460                                      4.8906
    ## 461                                     66.9493
    ## 462                                    525.4666
    ## 463                                   1256.1096
    ## 464                                     -9.1808
    ## 465                                      0.2463
    ## 466                                     10.4077
    ## 467                                      9.3746
    ## 468                                      2.4851
    ## 469                                      0.1199
    ## 470                                    215.9309
    ## 471                                     45.5055
    ## 472                                     39.0214
    ## 473                                    377.0833
    ## 474                                     86.5641
    ## 475                                    104.3064
    ## 476                                   1589.1096
    ## 477                                     38.5848
    ## 478                                      9.0189
    ## 479                                    355.5129
    ## 480                                     33.3603
    ## 481                                     50.5095
    ## 482                                    252.7148
    ## 483                                    344.9096
    ## 484                                    677.9135
    ## 485                                   6394.6623
    ## 486                                     501.338
    ## 487                                       67.36
    ## 488                                     48.2654
    ## 489                                    144.5438
    ## 490                                     53.9037
    ## 491                                    661.7555
    ## 492                                     19.2828
    ## 493                                       8.348
    ## 494                                    137.7938
    ## 495                                      75.855
    ## 496                                     22.1067
    ## 497                                   3971.4716
    ## 498                                   4803.8511
    ## 499                                     50.8528
    ## 500                                    528.7908
    ## 501                                   1014.6764
    ## 502                                    124.5582
    ## 503                                     78.0604
    ## 504                                      4.8433
    ## 505                                     68.7969
    ## 506                                    523.9518
    ## 507                                   1231.0468
    ## 508                                      -8.176
    ## 509                                      0.2464
    ## 510                                      7.9994
    ## 511                                      9.8081
    ## 512                                        2.61
    ## 513                                      0.1189
    ## 514                                    217.1176
    ## 515                                     49.3339
    ## 516                                     36.6211
    ## 517                                    370.7277
    ## 518                                     83.0917
    ## 519                                    107.2429
    ## 520                                   1525.3326
    ## 521                                     41.8474
    ## 522                                      9.9154
    ## 523                                    355.9895
    ## 524                                     34.0007
    ## 525                                     53.0396
    ## 526                                    231.3402
    ## 527                                    360.3817
    ## 528                                    681.2186
    ## 529                                   6220.1573
    ## 530                                    601.9516
    ## 531                                     75.0015
    ## 532                                     51.1558
    ## 533                                    142.9531
    ## 534                                     50.5589
    ## 535                                    818.9288
    ## 536                                     20.1895
    ## 537                                      8.5484
    ## 538                                    133.9068
    ## 539                                     76.6859
    ## 540                                      20.277
    ## 541                                   3988.7408
    ## 542                                   4813.4946
    ## 543                                     52.5049
    ## 544                                    518.1761
    ## 545                                   1040.8865
    ## 546                                    124.0816
    ## 547                                     76.4601
    ## 548                                      4.8599
    ## 549                                     66.8594
    ## 550                                    520.0162
    ## 551                                   1261.9872
    ## 552                                     -6.8495
    ## 553                                      0.2522
    ## 554                                      15.905
    ## 555                                     10.5859
    ## 556                                      2.6443
    ## 557                                      0.1173
    ## 558                                    216.0921
    ## 559                                     53.2755
    ## 560                                     32.9157
    ## 561                                    356.9306
    ## 562                                      87.232
    ## 563                                    115.8486
    ## 564                                   1496.0249
    ## 565                                     40.4401
    ## 566                                     10.0836
    ## 567                                     372.274
    ## 568                                     34.6956
    ## 569                                     51.4201
    ## 570                                    242.4432
    ## 571                                    363.2218
    ## 572                                    660.0964
    ## 573                                   6149.1045
    ## 574                                    745.6208
    ## 575                                     91.0418
    ## 576                                      56.285
    ## 577                                    144.8326
    ## 578                                      55.409
    ## 579                                    787.7535
    ## 580                                     22.0284
    ## 581                                      8.9366
    ## 582                                    138.8398
    ## 583                                     80.2807
    ## 584                                     19.4965
    ## 585                                   4067.2205
    ## 586                                   4923.9052
    ## 587                                     59.8945
    ## 588                                    522.3557
    ## 589                                   1038.8602
    ## 590                                    128.2423
    ## 591                                     77.3922
    ## 592                                      4.8143
    ## 593                                     66.8496
    ## 594                                    542.9553
    ## 595                                   1256.6275
    ## 596                                     -7.2395
    ## 597                                      0.2625
    ## 598                                     11.6955
    ## 599                                     10.9659
    ## 600                                      2.8311
    ## 601                                      0.1121
    ## 602                                     217.225
    ## 603                                     54.2163
    ## 604                                       31.62
    ## 605                                    369.4058
    ## 606                                     88.0963
    ## 607                                     128.687
    ## 608                                   1549.7118
    ## 609                                     41.3069
    ## 610                                      9.9237
    ## 611                                    380.0825
    ## 612                                       38.21
    ## 613                                     49.8676
    ## 614                                    254.9486
    ## 615                                    357.3818
    ## 616                                    666.7384
    ## 617                                     6083.95
    ## 618                                    476.2541
    ## 619                                     85.6274
    ## 620                                     60.0073
    ## 621                                    145.8861
    ## 622                                     54.4464
    ## 623                                    851.4134
    ## 624                                     22.0825
    ## 625                                       9.143
    ## 626                                    139.7666
    ## 627                                     74.1197
    ## 628                                       16.79
    ## 629                                   4049.7646
    ## 630                                    4900.778
    ## 631                                     55.0068
    ## 632                                    519.5985
    ## 633                                   1026.8059
    ## 634                                    128.5035
    ## 635                                     77.6029
    ## 636                                      4.8428
    ## 637                                       65.68
    ## 638                                    540.6265
    ## 639                                   1253.0267
    ## 640                                      -6.743
    ## 641                                      0.2635
    ## 642                                     15.6429
    ## 643                                     12.4281
    ## 644                                      2.8397
    ## 645                                       0.106
    ## 646                                    218.3862
    ## 647                                     52.1981
    ## 648                                     28.6902
    ## 649                                    370.2622
    ## 650                                     86.1892
    ## 651                                    119.3582
    ## 652                                   1603.3226
    ## 653                                     41.7432
    ## 654                                     10.1614
    ## 655                                    394.2627
    ## 656                                     40.6006
    ## 657                                     48.9586
    ## 658                                    264.6825
    ## 659                                    376.7198
    ## 660                                    665.5917
    ## 661                                   6164.4725
    ## 662                                    552.3312
    ## 663                                      85.597
    ## 664                                     57.9637
    ## 665                                    141.9753
    ## 666                                     54.8148
    ## 667                                    800.1423
    ## 668                                     22.3024
    ## 669                                      9.1369
    ## 670                                    138.5739
    ## 671                                      70.092
    ## 672                                     13.4402
    ## 673                                   4013.6453
    ## 674                                   4855.6899
    ## 675                                     38.8085
    ## 676                                    521.0253
    ## 677                                    1005.301
    ## 678                                    132.1489
    ## 679                                     74.3187
    ## 680                                      4.7374
    ## 681                                     66.8783
    ## 682                                    536.1621
    ## 683                                   1262.5789
    ## 684                                     -6.8945
    ## 685                                      0.2641
    ## 686                                     18.5977
    ## 687                                     12.7107
    ## 688                                      2.9349
    ## 689                                      0.1047
    ## 690                                    212.4886
    ## 691                                     54.9955
    ## 692                                     27.4699
    ## 693                                    368.5951
    ## 694                                     92.5587
    ## 695                                    113.4976
    ## 696                                   1588.2172
    ## 697                                     44.4934
    ## 698                                     10.5359
    ## 699                                    408.2894
    ## 700                                     40.1777
    ## 701                                     50.0301
    ## 702                                    285.9742
    ## 703                                    378.8566
    ## 704                                    659.3384
    ## 705                                   6197.4316
    ## 706                                    526.0179
    ## 707                                     88.6072
    ## 708                                     59.6234
    ## 709                                      137.25
    ## 710                                     56.1682
    ## 711                                    799.9218
    ## 712                                     22.8214
    ## 713                                      9.3919
    ## 714                                    143.5734
    ## 715                                      78.922
    ## 716                                     10.9391
    ## 717                                   3958.7416
    ## 718                                    4819.331
    ## 719                                     46.1514
    ## 720                                    504.5395
    ## 721                                   1007.4383
    ## 722                                    128.5111
    ## 723                                     74.8678
    ## 724                                       5.252
    ## 725                                      66.321
    ## 726                                    524.5007
    ## 727                                   1250.3857
    ## 728                                     -8.2256
    ## 729                                      0.2664
    ## 730                                     19.0351
    ## 731                                     12.6723
    ## 732                                      2.9332
    ## 733                                      0.0942
    ## 734                                    208.5596
    ## 735                                     56.8374
    ## 736                                     32.4109
    ## 737                                    380.9757
    ## 738                                     80.4454
    ## 739                                    118.0173
    ## 740                                   1675.7959
    ## 741                                     42.0445
    ## 742                                     10.8688
    ## 743                                    396.8243
    ## 744                                     32.8269
    ## 745                                     50.9893
    ## 746                                    302.1338
    ## 747                                    392.2932
    ## 748                                    655.3519
    ## 749                                   6190.3156
    ## 750                                    650.5524
    ## 751                                     86.8249
    ## 752                                     59.7522
    ## 753                                    132.4371
    ## 754                                     61.4017
    ## 755                                    800.5286
    ## 756                                     24.7058
    ## 757                                      9.7018
    ## 758                                     146.898
    ## 759                                     71.2493
    ## 760                                     12.9348
    ## 761                                   3921.8297
    ## 762                                   4799.3095
    ## 763                                     52.7044
    ## 764                                    493.7949
    ## 765                                     983.492
    ## 766                                    132.4308
    ## 767                                     72.4552
    ## 768                                      5.4632
    ## 769                                     65.0411
    ## 770                                    537.7657
    ## 771                                   1282.9306
    ## 772                                     -6.5105
    ## 773                                      0.2367
    ## 774                                     22.6526
    ## 775                                     12.0858
    ## 776                                      3.0467
    ## 777                                      0.0998
    ## 778                                    207.0643
    ## 779                                     56.5248
    ## 780                                     34.3245
    ## 781                                    386.0277
    ## 782                                      76.222
    ## 783                                    117.4848
    ## 784                                   1649.3479
    ## 785                                     40.4222
    ## 786                                     10.9648
    ## 787                                    402.3582
    ## 788                                     34.2501
    ## 789                                     49.1641
    ## 790                                    346.5134
    ## 791                                    382.3829
    ## 792                                    644.7036
    ## 793                                   6333.9829
    ## 794                                    520.5817
    ## 795                                     87.4437
    ## 796                                     63.4607
    ## 797                                    135.4208
    ## 798                                     58.6615
    ## 799                                    719.8535
    ## 800                                     23.3432
    ## 801                                      9.8927
    ## 802                                    137.3735
    ## 803                                     63.9389
    ## 804                                     11.4924
    ## 805                                   3806.3325
    ## 806                                   4649.5671
    ## 807                                     40.5752
    ## 808                                    488.6332
    ## 809                                     982.752
    ## 810                                    127.4654
    ## 811                                     68.7637
    ## 812                                      5.8525
    ## 813                                     64.9003
    ## 814                                    504.5071
    ## 815                                   1203.8274
    ## 816                                     -8.0981
    ## 817                                      0.2568
    ## 818                                     16.4838
    ## 819                                     11.9153
    ## 820                                       3.002
    ## 821                                      0.0966
    ## 822                                    206.3389
    ## 823                                     50.5021
    ## 824                                       29.85
    ## 825                                    375.9126
    ## 826                                     72.2207
    ## 827                                    116.1522
    ## 828                                   1658.9589
    ## 829                                     41.8951
    ## 830                                     11.7033
    ## 831                                    369.7893
    ## 832                                     30.5809
    ## 833                                     52.0667
    ## 834                                    327.7917
    ## 835                                    410.8437
    ## 836                                    630.1941
    ## 837                                   6146.1588
    ## 838                                    589.4025
    ## 839                                      76.416
    ## 840                                     57.9507
    ## 841                                    123.1469
    ## 842                                     49.4165
    ## 843                                    679.1878
    ## 844                                      21.093
    ## 845                                       9.629
    ## 846                                    126.6231
    ## 847                                     65.1851
    ## 848                                      8.9194
    ## 849                                   3524.4565
    ## 850                                   4279.9654
    ## 851                                     26.7764
    ## 852                                    474.3354
    ## 853                                    919.8181
    ## 854                                    121.0203
    ## 855                                     63.3909
    ## 856                                      5.5855
    ## 857                                     58.8214
    ## 858                                    450.8596
    ## 859                                   1132.7594
    ## 860                                     -8.9826
    ## 861                                      0.2408
    ## 862                                      9.7933
    ## 863                                     11.3936
    ## 864                                      2.9201
    ## 865                                      0.0914
    ## 866                                    200.7085
    ## 867                                     49.6251
    ## 868                                     29.5543
    ## 869                                    355.4869
    ## 870                                     68.9891
    ## 871                                     92.0398
    ## 872                                   1474.8162
    ## 873                                     36.5187
    ## 874                                      9.7539
    ## 875                                    334.2053
    ## 876                                     26.4464
    ## 877                                     50.2573
    ## 878                                    331.0535
    ## 879                                    347.0388
    ## 880                                    576.5662
    ## 881                                   5704.0165
    ## 882                                    587.7977
    ## 883                                     81.4945
    ## 884                                     59.2671
    ## 885                                    130.4251
    ## 886                                     52.2433
    ## 887                                    804.0443
    ## 888                                     20.7438
    ## 889                                       9.278
    ## 890                                    131.9341
    ## 891                                     62.3058
    ## 892                                     14.0471
    ## 893                                   3620.3779
    ## 894                                   4417.2763
    ## 895                                      49.913
    ## 896                                    485.3081
    ## 897                                    952.2392
    ## 898                                    114.6779
    ## 899                                     63.8607
    ## 900                                      5.4138
    ## 901                                     57.3803
    ## 902                                     456.973
    ## 903                                    1181.609
    ## 904                                     -4.3762
    ## 905                                       0.227
    ## 906                                     10.7231
    ## 907                                     11.9568
    ## 908                                      2.9382
    ## 909                                       0.088
    ## 910                                    212.1692
    ## 911                                     54.0334
    ## 912                                     30.7392
    ## 913                                    376.6481
    ## 914                                     67.8972
    ## 915                                     90.7904
    ## 916                                   1566.6581
    ## 917                                     38.9812
    ## 918                                      9.8302
    ## 919                                    319.7458
    ## 920                                     34.7868
    ## 921                                     51.6828
    ## 922                                    361.4995
    ## 923                                    345.2563
    ## 924                                    594.1139
    ## 925                                   5921.5478
    ## 926                                    511.9385
    ## 927                                     79.3503
    ## 928                                     58.0862
    ## 929                                    118.9032
    ## 930                                     58.1539
    ## 931                                    789.0583
    ## 932                                     21.2247
    ## 933                                      9.0779
    ## 934                                    125.5363
    ## 935                                     55.0844
    ## 936                                     16.6928
    ## 937                                   3456.6648
    ## 938                                   4260.1287
    ## 939                                     42.4414
    ## 940                                    446.8698
    ## 941                                    925.8297
    ## 942                                    112.5054
    ## 943                                     62.3603
    ## 944                                      5.1595
    ## 945                                     53.8109
    ## 946                                    458.2019
    ## 947                                   1232.2943
    ## 948                                      -5.685
    ## 949                                       0.215
    ## 950                                     11.1282
    ## 951                                     11.8037
    ## 952                                      2.9615
    ## 953                                      0.0853
    ## 954                                    197.6448
    ## 955                                     59.2947
    ## 956                                     25.7913
    ## 957                                    377.4772
    ## 958                                     64.6667
    ## 959                                     98.0406
    ## 960                                   1692.3995
    ## 961                                     37.8297
    ## 962                                      9.8906
    ## 963                                    321.4125
    ## 964                                     26.2173
    ## 965                                     46.5987
    ## 966                                    378.7756
    ## 967                                    394.2865
    ## 968                                    553.1485
    ## 969                                   5797.2845
    ##                        Emissions.by.Gas                X.3                X.4
    ## 1   Total CO2 (excluding LUCF) (MtCO2e) Total CH4 (MtCO2e) Total N2O (MtCO2e)
    ## 2                              277.9019           116.1267             18.416
    ## 3                               62.0596             8.3041             6.1978
    ## 4                              103.8068            15.2172            20.1272
    ## 5                              119.0944              9.708            10.8767
    ## 6                               80.2317            16.9692            12.3361
    ## 7                               459.313             72.003            49.0651
    ## 8                               23.3387             3.4202             3.9408
    ## 9                                4.9216             0.7194             0.4499
    ## 10                             164.8127            17.8151            13.3335
    ## 11                              54.1458             6.0684             9.8291
    ## 12                               36.635             1.6732              2.234
    ## 13                            3367.1013           435.5722           395.8516
    ## 14                            4406.9633           591.2254            517.039
    ## 15                               56.643             6.3153             7.3643
    ## 16                             399.4039            59.2562            90.7756
    ## 17                            1041.9138           109.9405            86.5479
    ## 18                              82.9093            10.3362            10.2395
    ## 19                              73.1542            12.6531            12.8149
    ## 20                               2.1601             0.4062             0.5209
    ## 21                               32.424            13.6741              9.112
    ## 22                             434.6563            43.7609            37.3963
    ## 23                            1141.1377            32.1311            31.5625
    ## 24                              19.0419             3.4775              3.804
    ## 25                               0.2031             0.0144             0.0129
    ## 26                              35.8155             5.7497             7.1887
    ## 27                              11.9503             0.4615             0.4761
    ## 28                               1.8655             0.0911             0.0499
    ## 29                               0.1054             0.0007             0.0018
    ## 30                             159.2359            25.7124            19.9862
    ## 31                              25.0471            25.6503             8.3006
    ## 32                              34.8333             5.0301             4.9287
    ## 33                             372.2884            47.1664             37.437
    ## 34                              45.1494            10.2605             5.5425
    ## 35                             175.5584            42.8063            23.9231
    ## 36                            2498.5423            593.579           218.5302
    ## 37                              60.7452             4.4142              6.351
    ## 38                               14.792              2.118             1.2653
    ## 39                             226.7128            26.5865            26.1365
    ## 40                               56.954             6.9382             8.3696
    ## 41                              44.5973             4.6741             3.4577
    ## 42                               141.56            34.0536            12.2172
    ## 43                             718.9515           151.6408             59.098
    ## 44                             590.3839            99.1333            67.4494
    ## 45                             5100.694             637.44           341.2537
    ## 46                             279.3231           116.1898            18.5506
    ## 47                              65.6438             8.2676             6.5293
    ## 48                              97.4754            14.4846            19.7635
    ## 49                             121.5522             9.5234            10.7503
    ## 50                              61.4895            15.7168             9.5321
    ## 51                             450.3934            73.5592            47.7833
    ## 52                              17.3525             3.1682             3.7567
    ## 53                               5.1631             0.7427              0.449
    ## 54                             154.3069             16.203            11.5594
    ## 55                              64.8073             6.1352             9.5868
    ## 56                              33.6346             1.5943              2.142
    ## 57                            3391.4899           431.8511           390.6927
    ## 58                            4355.7679           575.2236           488.6952
    ## 59                               55.062             6.2979             6.8018
    ## 60                             423.8054             59.503            89.5454
    ## 61                            1004.5953           104.4096              82.78
    ## 62                              82.6777            10.2908             9.9377
    ## 63                              69.8439            12.3392             9.0344
    ## 64                               2.0902             0.4032             0.5017
    ## 65                              33.2063            13.8469               8.92
    ## 66                             434.1564            45.0705            38.4247
    ## 67                            1150.0715            31.8671            31.0518
    ## 68                              17.4863             3.3928             3.5416
    ## 69                               0.2108             0.0142             0.0132
    ## 70                              37.9068             5.5289             6.6868
    ## 71                              12.4719             0.4719             0.4896
    ## 72                                2.041             0.0914             0.0504
    ## 73                               0.1063             0.0007              0.002
    ## 74                              164.239            26.0899            20.2565
    ## 75                              25.6896            25.8478             8.4185
    ## 76                               33.369             5.0475             4.7676
    ## 77                             370.4797            45.6868            30.9568
    ## 78                              46.8348            10.5301             5.5188
    ## 79                              144.054            35.7539            17.7618
    ## 80                            2352.2128           577.1783           207.8644
    ## 81                               54.092              4.283             5.1041
    ## 82                              13.7803             2.0397              1.184
    ## 83                             234.4515            27.0555            25.6896
    ## 84                              57.2269             6.9261             8.2747
    ## 85                              46.3204             4.6445             3.4603
    ## 86                             148.5457            38.1897            13.1743
    ## 87                             618.2116           144.7757            55.0854
    ## 88                             597.4261            98.3084            67.6278
    ## 89                            5050.5868           638.8548           350.2399
    ## 90                             284.4926           115.4766            18.6402
    ## 91                              60.1383             7.9856              6.134
    ## 92                              90.0602            14.1433            17.7774
    ## 93                             120.0153             9.3796            10.3834
    ## 94                              57.9022            14.5709             8.0153
    ## 95                             464.6517            77.3083            48.4679
    ## 96                              16.7081             2.8617             3.6549
    ## 97                               5.5063              0.782             0.4939
    ## 98                             139.9545            15.2611            10.3165
    ## 99                              59.0665             6.1346             9.2248
    ## 100                             24.1809             1.3246             1.8269
    ## 101                            3315.827           425.1653           383.9076
    ## 102                           4193.8672           556.5457           469.7262
    ## 103                             54.2137             6.2678             6.3003
    ## 104                            415.4632            59.6329            90.7034
    ## 105                            957.4365           100.6857             83.064
    ## 106                             84.3528            10.4019             9.7845
    ## 107                              63.459            10.9743             7.4297
    ## 108                              2.2161             0.4073             0.4705
    ## 109                             33.0742            13.9633              8.912
    ## 110                            433.8676            43.6628            37.8783
    ## 111                           1158.5444            31.6247            31.2157
    ## 112                             14.0076             2.9148             2.7456
    ## 113                              0.2117              0.014             0.0131
    ## 114                             21.2181             4.4542             4.5397
    ## 115                             12.2421             0.4627             0.5034
    ## 116                              2.1455             0.0944             0.0517
    ## 117                              0.1129             0.0008             0.0021
    ## 118                            162.3161            25.6801            20.4527
    ## 119                             27.5935            25.4488             8.3427
    ## 120                             34.1673             5.1288             4.2113
    ## 121                            361.0971             43.418            28.7482
    ## 122                             51.0944            10.6502             5.5242
    ## 123                            125.1283            31.4135            16.1566
    ## 124                           1931.0262           530.2966           190.4057
    ## 125                             49.7498             4.0546             4.2185
    ## 126                              13.691             2.1182             1.2761
    ## 127                            241.3329            27.5701            24.5511
    ## 128                              57.013             6.9996             8.1338
    ## 129                              46.214             4.5101             3.4377
    ## 130                            154.1746             41.641            15.2327
    ## 131                            542.2063           134.1373            50.9988
    ## 132                            580.9831            96.5335            62.8021
    ## 133                           5156.9173           640.3206           355.3688
    ## 134                            288.4969           113.3179            19.2565
    ## 135                             60.5161             7.9341             5.9601
    ## 136                             77.2042            13.4729            16.9293
    ## 137                            119.0181             9.2706             10.676
    ## 138                             58.4473            12.9376             7.3256
    ## 139                            464.0631            79.6426            49.4336
    ## 140                             17.1652             2.9839             3.1258
    ## 141                              5.7662             0.8185             0.5016
    ## 142                            135.8938            14.3304             9.1359
    ## 143                             61.2161             6.2302             9.0404
    ## 144                             18.7704             1.0519             1.3692
    ## 145                           3259.0524           421.3805           370.8422
    ## 146                           4114.4555           546.6891           453.2651
    ## 147                             56.1228             6.2943             6.4715
    ## 148                            391.9752            59.9074            86.4753
    ## 149                             948.543           100.2261            80.4864
    ## 150                             83.6635            10.3844             8.9132
    ## 151                             64.2369            10.4279             7.3504
    ## 152                              2.3393             0.4154             0.4812
    ## 153                             33.2068            13.9749             9.1044
    ## 154                            427.1702            43.4577            38.3816
    ## 155                           1150.8771            31.3656            30.9781
    ## 156                             11.7435             2.1917             1.9537
    ## 157                                0.22             0.0133             0.0127
    ## 158                             16.3871             4.0086             3.9345
    ## 159                             12.3639             0.4667              0.489
    ## 160                              2.1414             0.0981             0.0528
    ## 161                              0.1128             0.0008             0.0024
    ## 162                            166.7125            25.3682            20.7129
    ## 163                             27.1367            25.5633             8.5711
    ## 164                             35.8052             5.1811             4.3997
    ## 165                            361.4104            43.1563            28.9654
    ## 166                              49.777            10.6422             5.4729
    ## 167                             120.473             30.421             17.061
    ## 168                           1834.2461           514.5512             174.78
    ## 169                             46.0788             3.8092             3.5619
    ## 170                             14.0544             2.0574             1.2108
    ## 171                            231.3441            27.7328            22.7515
    ## 172                             56.9045             6.9939             8.1947
    ## 173                             43.6733             4.3749             3.3587
    ## 174                            162.7567            43.9031            15.7353
    ## 175                            464.8136           124.2071            46.9156
    ## 176                            567.3052             93.302            58.1458
    ## 177                           5267.9051           633.2379           396.9501
    ## 178                            293.2451            110.317             19.622
    ## 179                             60.8998             7.7081             6.4407
    ## 180                             64.5062            12.3162            14.9074
    ## 181                            123.4996             9.2419            11.2375
    ## 182                             56.2914            11.5259             7.2521
    ## 183                            478.7482            82.5571            52.9243
    ## 184                             16.4903             2.7771             3.1904
    ## 185                              6.2036              0.836             0.4998
    ## 186                            126.9086            13.4825             8.9815
    ## 187                             65.1698             6.1261             9.0625
    ## 188                              19.639             1.0212             1.1814
    ## 189                           3261.6948           409.8927           374.9128
    ## 190                           4095.3498           532.3244           456.7466
    ## 191                             61.4186             6.2586             6.5957
    ## 192                            392.0935            59.6947            87.8237
    ## 193                            932.3604            96.1833            80.3504
    ## 194                             85.9143            10.5683              8.729
    ## 195                             63.1041             9.9693             8.4432
    ## 196                              2.2869             0.4241             0.4872
    ## 197                             34.4223            13.9023             9.3843
    ## 198                             419.904            43.8487            37.5917
    ## 199                           1210.6604            30.7232             32.178
    ## 200                             10.2319             2.0147             1.7109
    ## 201                              0.2061             0.0135             0.0126
    ## 202                             15.7991              3.715             3.3943
    ## 203                             11.5502              0.461             0.4788
    ## 204                              2.2529             0.1009             0.0543
    ## 205                              0.1148             0.0008             0.0026
    ## 206                             166.673            24.6223            20.0208
    ## 207                             27.2594            26.1129             8.9222
    ## 208                             37.7188             5.2541             4.4823
    ## 209                            357.1307            43.4456            29.3358
    ## 210                             50.4662            11.0999             5.5347
    ## 211                            118.3783              30.44            15.7849
    ## 212                           1622.3608           479.8185           156.4559
    ## 213                             43.5267             3.8305             3.9249
    ## 214                             14.1888             2.0499             1.2707
    ## 215                            243.5128            28.1077            25.2376
    ## 216                             59.3574             6.9163             8.2406
    ## 217                             42.9347             4.2814             3.3174
    ## 218                            161.0139            44.2752            12.6368
    ## 219                            402.9652            112.214            42.0407
    ## 220                            561.2659            85.9431            58.6207
    ## 221                           5354.5879           640.4111           371.2559
    ## 222                            303.8633           112.1869            20.6357
    ## 223                              63.944             7.6178              6.606
    ## 224                             57.5998             11.705            13.5321
    ## 225                            124.4217             9.2736            11.7205
    ## 226                             58.0432            10.9976             6.7905
    ## 227                            491.1162            85.9095            53.7495
    ## 228                             17.2017             2.7439             3.0541
    ## 229                              6.0882             0.8675             0.5096
    ## 230                            128.0379            13.3081             9.2544
    ## 231                              62.006             6.1625              8.794
    ## 232                             17.9815             0.9816             1.0466
    ## 233                           3297.5101           406.6525           375.4316
    ## 234                            4138.591           528.5792           457.7415
    ## 235                             57.9088             6.1047             6.7703
    ## 236                            398.9295            60.1497            89.5716
    ## 237                            930.7811            92.6314            79.3437
    ## 238                             86.3495            10.5948             8.9968
    ## 239                              62.477             9.9861             7.4723
    ## 240                              2.3182             0.4219             0.4774
    ## 241                             35.2325            13.9197             9.6206
    ## 242                            444.9437            44.3357            38.4222
    ## 243                           1223.6873            29.8994            32.6468
    ## 244                              9.0364             2.0012             1.5354
    ## 245                              0.2094             0.0134             0.0125
    ## 246                             15.0535             3.6212             3.3834
    ## 247                              9.2101             0.4696             0.4807
    ## 248                               2.213             0.1047             0.0592
    ## 249                              0.1118             0.0008             0.0027
    ## 250                             170.738            24.3335            19.8806
    ## 251                             27.3846            26.3663             9.1922
    ## 252                             37.7911             5.1995             4.5336
    ## 253                            358.3023            43.4105            30.3783
    ## 254                             54.4857            11.3722             5.6731
    ## 255                            123.9577            30.5682            16.3959
    ## 256                           1572.5973           461.1772           142.5937
    ## 257                             44.8791             4.0372             4.1597
    ## 258                             15.0111             2.0426             1.3247
    ## 259                            253.8922            28.4505            24.7679
    ## 260                             58.8719             6.8275             8.0698
    ## 261                             43.5844             4.2673             3.3228
    ## 262                            174.0871            47.3933            16.8235
    ## 263                            360.3562            98.9633            39.0933
    ## 264                            552.9302            85.2073            57.1554
    ## 265                           5416.1557           632.8681           384.6212
    ## 266                            311.4131           111.3548            21.6319
    ## 267                             67.3837             7.3982             6.2675
    ## 268                             58.5538            11.8724            14.4779
    ## 269                            128.4524             9.0339            12.0727
    ## 270                             58.3962            10.7247             6.5719
    ## 271                            504.4254            89.0398            56.3007
    ## 272                             17.8343             2.7346              3.053
    ## 273                              6.4506             0.8943             0.5224
    ## 274                             132.487            13.1591             8.8507
    ## 275                             75.4168             6.2055             8.2193
    ## 276                              18.688             0.9957             0.9825
    ## 277                           3372.4831           402.2383           381.4252
    ## 278                           4238.7845           523.4401           463.8868
    ## 279                             63.7169             6.0267              6.726
    ## 280                            411.8994             59.575            90.9494
    ## 281                            951.7572            89.7104            80.8959
    ## 282                              88.435            10.8243             9.2244
    ## 283                             63.7865             10.167             8.1091
    ## 284                              2.4074             0.4289             0.4981
    ## 285                             36.8399            14.1772             9.7446
    ## 286                            438.3034            44.9975            38.4439
    ## 287                           1236.5818            29.1425            33.6164
    ## 288                              9.1306             1.9509             1.5197
    ## 289                              0.2116             0.0138             0.0125
    ## 290                             15.7028              3.615             4.0235
    ## 291                              9.2589             0.4732             0.4889
    ## 292                              2.2652              0.107             0.0549
    ## 293                              0.1161             0.0008              0.003
    ## 294                            177.6959            23.6462            19.8143
    ## 295                             28.6705            26.9479             9.2994
    ## 296                             41.0405             5.2289             4.5674
    ## 297                            371.6826            43.4455            30.0704
    ## 298                             51.8581             11.419             5.9851
    ## 299                            127.3347            30.1216            16.0793
    ## 300                           1533.8698           449.0047           133.1037
    ## 301                             44.6991             4.0165             4.3022
    ## 302                             15.6781             2.0044             1.3749
    ## 303                            241.2862             29.773            27.8995
    ## 304                              62.743             6.7916              8.179
    ## 305                             44.2362             4.1933             3.3265
    ## 306                            192.1995              49.85            16.9954
    ## 307                            324.3997            92.0599            33.9453
    ## 308                            574.7509            82.9988            56.9613
    ## 309                           5602.4452           629.9109           397.3955
    ## 310                            319.7272           114.5103            22.5761
    ## 311                               67.18             7.0936             6.2994
    ## 312                              59.868            11.9201            14.9365
    ## 313                            122.8215             8.8988            11.7537
    ## 314                             55.6259            10.1427             6.2936
    ## 315                            517.2543            90.6827            55.0725
    ## 316                             18.8614             2.8094             3.3451
    ## 317                               6.542             0.9005             0.4998
    ## 318                             129.596            12.8943             8.9325
    ## 319                             66.0868              6.046             8.1834
    ## 320                             18.2365             1.0574             0.9809
    ## 321                           3318.0566           391.5406           379.7374
    ## 322                            4155.633           510.8386           461.3492
    ## 323                             62.3686             5.9502             6.6798
    ## 324                             405.396            58.4711            92.3264
    ## 325                            922.9574            85.0884            78.0454
    ## 326                             93.2178            10.7331              9.008
    ## 327                             62.1957             9.9988             7.9706
    ## 328                              2.4957             0.4301             0.4973
    ## 329                             38.2557            14.1968             9.6961
    ## 330                            442.3717            45.5331            39.8419
    ## 331                           1231.4775            28.0929            34.2949
    ## 332                              8.6033             1.9106             1.5241
    ## 333                              0.2239             0.0135             0.0124
    ## 334                             15.1043              3.723             4.2042
    ## 335                              8.5611             0.4683              0.486
    ## 336                              2.2553             0.1104             0.0554
    ## 337                              0.1163             0.0009             0.0032
    ## 338                            171.5462            22.6262            19.5212
    ## 339                              30.925            27.5006             9.4596
    ## 340                             41.1421             5.2329             4.5545
    ## 341                            362.4663            43.8056            30.2815
    ## 342                             54.7026             11.624             5.9798
    ## 343                            116.1487            28.6639            15.2453
    ## 344                           1458.3805           424.1858           126.6338
    ## 345                             44.8115             4.0802             4.2179
    ## 346                             15.9909             2.0105             1.4059
    ## 347                            262.0963            30.4242            26.9773
    ## 348                             57.6526             6.7414             8.1185
    ## 349                             43.4214             4.0863              3.215
    ## 350                            205.3664            51.1355            15.5427
    ## 351                            309.7035            85.2511             32.955
    ## 352                            550.2986            78.4598            57.2714
    ## 353                           5677.6061           621.2222            386.599
    ## 354                            332.9626           114.4992            23.1572
    ## 355                              66.763             6.9431             6.4175
    ## 356                             58.0648            11.8795             14.998
    ## 357                            129.0656             8.7563            11.8849
    ## 358                             52.6357             9.3187             5.1565
    ## 359                            526.3707            92.0677            51.0024
    ## 360                             19.6236             2.6546             2.8829
    ## 361                              6.6239             0.9062             0.5015
    ## 362                            123.2169            12.4625             8.7378
    ## 363                             62.0129             6.0302             8.3576
    ## 364                             16.6575             1.0468             1.0314
    ## 365                           3367.6248           382.2803           360.0808
    ## 366                           4152.5414           496.9768           439.3648
    ## 367                             59.0889             5.7458             6.5159
    ## 368                            427.1711            58.6565            85.0455
    ## 369                            915.0501            79.7616            64.7472
    ## 370                             98.1149            10.9668             8.9532
    ## 371                             61.4181             9.9862             8.1431
    ## 372                               2.505             0.4401             0.4991
    ## 373                             40.2707            14.4186            10.3028
    ## 374                            453.5241            45.4577            39.7885
    ## 375                           1195.8701            27.2972            32.7814
    ## 376                              8.2204             1.8189             1.4665
    ## 377                              0.2352             0.0135             0.0123
    ## 378                             15.9231             3.4996             4.3721
    ## 379                              7.6727             0.4672             0.4827
    ## 380                              2.2586             0.1122             0.0612
    ## 381                              0.1141             0.0008             0.0032
    ## 382                            173.3811            21.8684            18.7938
    ## 383                              29.381            26.7252              9.314
    ## 384                             41.3699             5.0864             4.5938
    ## 385                            335.3268            42.4696            30.3069
    ## 386                              59.227            12.0547             5.8445
    ## 387                            102.5806            26.6931            14.3076
    ## 388                           1432.7442           424.7038           113.6092
    ## 389                             44.3243             4.3369              3.804
    ## 390                             15.7307             2.0458             1.3953
    ## 391                            270.4402            31.1896             28.194
    ## 392                             58.2661             6.5796             8.1393
    ## 393                              44.723             4.0426             3.2105
    ## 394                            204.5025            52.4441            17.1912
    ## 395                            308.6011            81.2595            29.7628
    ## 396                            555.3504            74.2245            57.0683
    ## 397                           5715.7607           608.6128           363.1359
    ## 398                            342.7857           113.2074            24.0969
    ## 399                             65.3449              6.774             6.3926
    ## 400                             55.4041            11.6275            14.4362
    ## 401                            123.5453             8.6231            11.7804
    ## 402                             46.1589             8.6877             5.4474
    ## 403                            541.5721            91.6786            48.7868
    ## 404                             20.5353              2.664             3.2174
    ## 405                              6.8941             0.9119             0.5041
    ## 406                            115.6364             11.875              8.573
    ## 407                             59.4578             5.9173             8.2009
    ## 408                             15.5084             0.9823             0.8777
    ## 409                           3344.2347           373.8485           339.2242
    ## 410                            4087.218           486.3037           416.4991
    ## 411                             58.6695             5.6172             6.4242
    ## 412                            418.7413            58.4158            78.1431
    ## 413                            887.7809            78.2554            61.2975
    ## 414                             97.4082            10.8818              8.864
    ## 415                             61.3841            10.0854             8.1364
    ## 416                              2.7101             0.4451             0.5207
    ## 417                             41.9071            13.9563             9.9425
    ## 418                            458.8248            45.6808            40.5052
    ## 419                           1230.7973            26.7111              26.36
    ## 420                               7.627             1.7014             1.3813
    ## 421                              0.2343             0.0131             0.0121
    ## 422                             13.4557             3.3537             4.4354
    ## 423                              8.0772             0.4752             0.4841
    ## 424                              2.3481             0.1138             0.0565
    ## 425                              0.1148             0.0008             0.0033
    ## 426                            167.8028            20.8366            18.0697
    ## 427                             30.8525            27.1161             9.4778
    ## 428                             42.1196             5.0064             4.8258
    ## 429                            326.0657            42.3141            29.3683
    ## 430                             66.9908            12.2767             5.9366
    ## 431                             89.3659            25.8611            13.7961
    ## 432                           1469.9001           424.9363           108.1166
    ## 433                             43.4346             4.5464             3.3123
    ## 434                             15.1044             2.0224             1.3866
    ## 435                            295.6415             31.323            29.3504
    ## 436                             55.3251             6.4262              7.769
    ## 437                             44.8415             3.9828             3.1829
    ## 438                             203.847            53.6676            17.4746
    ## 439                            302.4492            78.9126            28.0702
    ## 440                            546.4443            69.2299            46.5189
    ## 441                            5788.887           598.0073           361.6895
    ## 442                            349.4191           115.6351            25.5571
    ## 443                             65.9697             6.6229              6.289
    ## 444                             53.3193            11.4218            14.4142
    ## 445                            125.2497               8.29            11.0363
    ## 446                             45.5228             8.5326             5.4205
    ## 447                            564.6425            94.0258            48.6137
    ## 448                             20.0932             2.7291              3.285
    ## 449                              7.1435             0.9272             0.4837
    ## 450                            125.7111            11.0839             8.6779
    ## 451                             55.0706             5.9128             7.9755
    ## 452                             15.1433             1.0249             0.9017
    ## 453                           3372.9611           366.0146           335.6558
    ## 454                           4111.6515           474.6459           413.0494
    ## 455                             56.8596             5.4069              6.495
    ## 456                            415.8268            59.4823            77.6741
    ## 457                            891.4003            75.1001             61.411
    ## 458                            102.5006             10.834              8.537
    ## 459                             59.4679             9.9912             8.3598
    ## 460                              2.7759             0.4403             0.4951
    ## 461                             44.6892            13.4122              9.482
    ## 462                            462.2777            45.8437            39.4832
    ## 463                           1251.4607            26.1337            28.9208
    ## 464                              6.9926             1.6638             1.3998
    ## 465                              0.2276              0.013              0.012
    ## 466                             11.8532              3.158             4.6226
    ## 467                              8.7807             0.4671             0.4814
    ## 468                              2.3452              0.125              0.061
    ## 469                              0.1128             0.0008             0.0034
    ## 470                            169.9208            19.9182             17.399
    ## 471                             31.3503            27.8867             9.8421
    ## 472                             41.7908             5.0576             4.5888
    ## 473                            315.5396             39.361            29.1763
    ## 474                             65.8632             12.113             5.9982
    ## 475                             92.3903            26.3975            13.2824
    ## 476                           1471.3374           434.6278           112.0388
    ## 477                             41.3674             4.2477             3.5818
    ## 478                             15.2135             2.1184              1.426
    ## 479                            307.0232            32.1626            30.5838
    ## 480                             54.1454              6.252             7.6023
    ## 481                             43.9213             3.9144             3.1835
    ## 482                            225.6086            53.8075            17.1423
    ## 483                            293.5417            75.6058             26.488
    ## 484                            555.2486            64.9867            45.6521
    ## 485                           5962.7015           597.4936           347.8851
    ## 486                            355.7284            117.639            26.9786
    ## 487                             69.9994             6.4865             6.1747
    ## 488                              52.347            11.3673            13.4889
    ## 489                            125.2217             7.9539            10.8023
    ## 490                             49.2558             7.8817             5.4859
    ## 491                            559.0915            95.3104            46.8708
    ## 492                              21.034             2.8772             3.3379
    ## 493                              6.9996             0.9315             0.5209
    ## 494                            125.4666              10.79             8.8406
    ## 495                             56.8989             6.0163             7.6742
    ## 496                             15.4978             1.0566             0.8889
    ## 497                           3434.5603           354.6338           326.9186
    ## 498                           4182.6238           461.7586            405.895
    ## 499                             62.1287             5.2775             6.4321
    ## 500                            416.5441            58.7587            75.0305
    ## 501                            907.4432            72.2734            62.4704
    ## 502                            104.8975            10.0417             8.3581
    ## 503                             60.8225             9.7734             8.9415
    ## 504                              2.7733             0.4487             0.4872
    ## 505                             47.0984             13.459             8.9694
    ## 506                             468.284             44.696             39.561
    ## 507                           1236.3205            25.2158            25.5041
    ## 508                              7.4121              1.751             1.5184
    ## 509                              0.2256             0.0136             0.0123
    ## 510                              12.558             3.2827             4.8542
    ## 511                              9.2972             0.4667             0.4588
    ## 512                              2.4648             0.1255             0.0587
    ## 513                              0.1139             0.0008             0.0035
    ## 514                             175.692            19.1397            16.3387
    ## 515                             33.4522            27.9735            10.2075
    ## 516                             43.1596             5.0685             4.5061
    ## 517                            312.0834            38.7423            29.3287
    ## 518                             65.5739            12.3728              5.758
    ## 519                             95.2094            26.4105            13.3782
    ## 520                           1490.3926           439.2679           113.1332
    ## 521                             44.1685             4.2922              3.763
    ## 522                              16.125             2.0873             1.3975
    ## 523                            311.3466            32.9636            28.9262
    ## 524                             55.0779             6.2105             7.4198
    ## 525                             44.8728             3.9286             3.2109
    ## 526                            209.1545            53.2006             15.195
    ## 527                            298.8787            74.3682            26.8732
    ## 528                            566.9372             59.301            42.9877
    ## 529                           5862.8408            595.298           351.3379
    ## 530                            360.0643           114.6247             26.614
    ## 531                              71.714             6.3891             6.1773
    ## 532                             52.5288            11.2919            12.9503
    ## 533                            124.9713             7.5396            10.2998
    ## 534                             46.2603             8.0121             5.3552
    ## 535                            565.8841            95.4105            46.4504
    ## 536                              22.108             2.9488              3.263
    ## 537                              7.1919              0.964             0.5479
    ## 538                            122.1262            10.3977             8.5428
    ## 539                             56.4662              5.932             7.5183
    ## 540                             15.0043             1.0043             0.8389
    ## 541                           3426.6868           344.6756            317.724
    ## 542                            4155.305           452.0794           394.5346
    ## 543                             64.5836             5.0892              6.519
    ## 544                            413.0942            57.5057            72.7223
    ## 545                            890.7509            69.1969            61.1347
    ## 546                            104.6347            10.0602             8.2793
    ## 547                              59.237             9.8343              8.332
    ## 548                              2.8629             0.4466             0.4543
    ## 549                             45.6762            13.3956             8.5977
    ## 550                            470.5309            43.7606            38.8462
    ## 551                           1273.3966            24.2771             24.771
    ## 552                              7.4093             1.7382              1.485
    ## 553                              0.2306             0.0139             0.0123
    ## 554                             12.6761             3.3548             5.1929
    ## 555                             10.0578             0.4674             0.4668
    ## 556                              2.4848             0.1269             0.0582
    ## 557                              0.1118             0.0008             0.0035
    ## 558                             175.991            17.9578             15.496
    ## 559                             33.6305            27.9028            10.5813
    ## 560                             42.2825             4.9374             4.7159
    ## 561                            300.5194            37.7013            28.3924
    ## 562                             69.3314            12.6489             5.8012
    ## 563                             97.0272            27.1911            13.0413
    ## 564                           1491.3411           445.0765            114.044
    ## 565                             42.4054             4.9024             3.7392
    ## 566                             16.2762             2.1768             1.2849
    ## 567                            330.0042            33.2403            27.7357
    ## 568                             55.9928             6.0283             7.3142
    ## 569                             43.8286             3.8752             3.1918
    ## 570                            218.1939            50.8113            15.7976
    ## 571                            302.1034            73.3407            27.5106
    ## 572                            551.0529            56.2246            41.2444
    ## 573                           5903.3928           588.1538           353.9587
    ## 574                            367.4648           111.5509            25.9766
    ## 575                             77.7582             6.3836             6.1034
    ## 576                             52.8913            12.2107            13.4396
    ## 577                            128.1609             7.0763             9.2381
    ## 578                             50.5046             8.8126             5.0508
    ## 579                             582.896            96.1287             48.791
    ## 580                             23.5287             3.0508             3.1075
    ## 581                              7.5839             0.9607             0.5357
    ## 582                            125.5109            10.3165             8.0391
    ## 583                             61.6271             5.9116             7.2062
    ## 584                             16.8324             1.0382             0.8752
    ## 585                           3493.5954           334.7878           312.3291
    ## 586                           4253.8602           443.1555           389.6353
    ## 587                             72.3295             4.9092             6.6645
    ## 588                            422.0373             56.063            69.9805
    ## 589                            892.9318            66.6172            60.0943
    ## 590                            108.7127            10.0866             8.2026
    ## 591                             62.2473             9.8375             8.3018
    ## 592                              2.8546             0.4453              0.444
    ## 593                              45.155            13.9388             8.5111
    ## 594                            486.5597            42.7872            38.3341
    ## 595                            1278.505            23.7818            24.4228
    ## 596                              7.6338             1.6531             1.5645
    ## 597                                0.24              0.014             0.0124
    ## 598                             12.6611             3.4105             5.3436
    ## 599                             10.4614             0.4579             0.4554
    ## 600                              2.6637             0.1268             0.0555
    ## 601                              0.1065             0.0007             0.0033
    ## 602                            179.5829            17.1154            15.2823
    ## 603                             35.3642            28.0977            10.9247
    ## 604                             43.6473              5.015             4.5684
    ## 605                            312.4811            38.0565            28.5589
    ## 606                             64.4411            12.6495             5.2233
    ## 607                            103.2747            27.2813            13.9568
    ## 608                           1521.2887           460.3062             111.27
    ## 609                             42.8365             4.7291             3.7877
    ## 610                             16.0348             2.1449             1.2364
    ## 611                            333.9134            33.4359            29.4109
    ## 612                             56.6076             5.8823             7.2701
    ## 613                             45.0088              3.781             3.1366
    ## 614                            232.8003            52.0121             16.156
    ## 615                            317.8651            72.4299            26.0324
    ## 616                            561.5107            52.2047              40.77
    ## 617                           5951.5129           595.8363           344.6408
    ## 618                            381.1106           112.8677            26.0916
    ## 619                             78.2159             6.2425             5.4085
    ## 620                             56.2585            12.7772             13.836
    ## 621                            128.8641              6.998             9.4315
    ## 622                             49.4331             8.4825             5.6358
    ## 623                            584.6549            97.8432            51.5923
    ## 624                             23.1524             3.1468             3.4774
    ## 625                              7.8048              0.978             0.5127
    ## 626                            126.5096            10.0369             8.7335
    ## 627                             56.1515             5.7548             6.9902
    ## 628                             17.0821              1.072             0.9167
    ## 629                            3502.867           324.5571           313.6305
    ## 630                           4264.5535           430.7143           393.9726
    ## 631                             68.4387             4.7417             6.6738
    ## 632                            423.6173            55.0064            67.9284
    ## 633                            881.0343            62.4045            63.4139
    ## 634                            109.0391            10.1265             8.2107
    ## 635                             60.7147             9.4436               9.22
    ## 636                              2.9264             0.4471             0.4413
    ## 637                             46.0538            13.1552             8.3315
    ## 638                             489.367            41.3852            39.3668
    ## 639                           1277.8836             23.358            24.4379
    ## 640                              7.7991             1.6447              1.542
    ## 641                              0.2402             0.0141             0.0124
    ## 642                             13.2442             3.3617             5.5847
    ## 643                             11.8345             0.4527             0.5014
    ## 644                              2.6186             0.1328             0.0565
    ## 645                                 0.1             0.0007             0.0032
    ## 646                            180.9854            16.6211             15.728
    ## 647                             34.9349            28.0144            10.9899
    ## 648                             44.0572              4.978              4.719
    ## 649                            316.2048            37.8857            28.8831
    ## 650                             66.8075            12.6393             5.4738
    ## 651                            101.1409            26.3778            14.2589
    ## 652                           1523.5331           490.2609           110.8017
    ## 653                             42.7421             4.6038             3.8138
    ## 654                             16.3925             2.1377             1.1844
    ## 655                            351.7693             33.181            27.9661
    ## 656                             55.7684             5.9042             7.2321
    ## 657                             45.6341             3.7638             3.0878
    ## 658                            243.5849              49.75            16.4802
    ## 659                            319.1725            71.3874            26.3278
    ## 660                            563.2584            50.6454            41.3949
    ## 661                           6070.3257           585.8675           356.2727
    ## 662                              384.75           112.8638            25.8823
    ## 663                             79.7237             6.0834             5.4479
    ## 664                             56.6698            13.1165            14.3598
    ## 665                            125.6105             6.7959             9.1604
    ## 666                             50.3046              7.931             5.3932
    ## 667                             578.955            98.0878            50.3081
    ## 668                             23.4852             3.1319             3.4896
    ## 669                              7.8569             0.9598             0.4722
    ## 670                            125.7444            10.4002             8.4246
    ## 671                             52.4953             5.6842             6.3616
    ## 672                             16.4195             1.0439              0.895
    ## 673                           3484.0951            316.737           304.3147
    ## 674                           4245.7385           422.6694           385.0889
    ## 675                             56.5699             4.5296             6.7093
    ## 676                            427.7188            54.1673            67.3216
    ## 677                            864.7162            59.4829            60.9159
    ## 678                            112.8023            10.1631             7.9101
    ## 679                             60.4768             9.2632             8.5902
    ## 680                              2.8529             0.4428             0.4497
    ## 681                             47.7792            12.8096              8.116
    ## 682                             488.078            41.1069            37.6675
    ## 683                           1282.1284            23.0151            23.9462
    ## 684                              7.7898             1.6645             1.6075
    ## 685                              0.2399             0.0146             0.0126
    ## 686                             14.0176              3.373              5.883
    ## 687                             12.1079             0.4518             0.4785
    ## 688                               2.704             0.1399             0.0585
    ## 689                              0.0987             0.0006             0.0031
    ## 690                            175.9133            16.1006            15.4426
    ## 691                             36.3864            28.3579            11.1094
    ## 692                             43.0595             4.7627             4.7888
    ## 693                            318.0195            38.3256             29.272
    ## 694                             69.2652            12.6442             5.2541
    ## 695                              99.392            26.3348             15.215
    ## 696                           1524.7899           473.7563           108.6905
    ## 697                             42.2245             4.3575             3.7718
    ## 698                             16.6937             2.1391             1.1911
    ## 699                             367.312            33.1839            26.3735
    ## 700                             53.2312             5.7752             7.0728
    ## 701                             46.2591               3.77             3.0703
    ## 702                            259.7659            52.8175            14.6735
    ## 703                            320.6026            70.2195            26.0935
    ## 704                            559.4521            48.4614            40.4991
    ## 705                           6100.4031           585.6147           347.6976
    ## 706                             389.441           113.5089            25.9768
    ## 707                             77.0325             5.9618              5.482
    ## 708                             59.1285            13.8042            15.0795
    ## 709                            121.7998             6.7054             8.2068
    ## 710                              51.719             7.8443               4.83
    ## 711                            571.7474            98.0387            48.1243
    ## 712                             23.7165             3.3789             3.4215
    ## 713                               8.127             0.9571             0.4503
    ## 714                            127.1277            10.6765             8.2559
    ## 715                             60.4633             5.6929             6.2106
    ## 716                             15.8426             1.0546             0.8949
    ## 717                           3467.4761           310.6686           292.2309
    ## 718                           4250.2713           416.8761           372.4874
    ## 719                             68.0376             4.5943             6.6128
    ## 720                            418.2414            53.6672            64.9476
    ## 721                            870.7392            56.8926            60.0996
    ## 722                            111.2234            10.2099             7.7013
    ## 723                             59.5725             9.1561             8.3621
    ## 724                              3.0293             0.4644             0.4751
    ## 725                             47.3985            12.8845             7.9827
    ## 726                            483.5426            39.5779            32.3219
    ## 727                           1262.9452             22.662            23.9281
    ## 728                              8.2733             1.6396             1.6097
    ## 729                              0.2416             0.0152             0.0128
    ## 730                             14.4083             3.4047             5.8412
    ## 731                             11.9693             0.4475             0.4683
    ## 732                               2.671             0.1487             0.0599
    ## 733                              0.0893             0.0005             0.0029
    ## 734                            172.3052            15.7271            15.3125
    ## 735                             36.3117            28.4461            10.9864
    ## 736                             43.4637             4.6506             4.4523
    ## 737                            331.5505            38.7231            30.4832
    ## 738                             64.6553             12.355             5.0092
    ## 739                            104.8934            25.9998             14.223
    ## 740                           1581.8654           485.7885           108.8897
    ## 741                             41.7181             4.4436             4.0403
    ## 742                             16.8917             2.1596             1.2057
    ## 743                            357.3071            33.5095            26.8118
    ## 744                             53.1944             5.6988             7.0963
    ## 745                             45.8943             3.7799              3.069
    ## 746                            276.8797             53.763            16.0507
    ## 747                            337.3581            69.1651            26.7329
    ## 748                            558.5261            47.4526            38.3843
    ## 749                           6024.1147           597.0736           352.4606
    ## 750                            396.8467           114.6387            25.3078
    ## 751                             74.2746             5.8512             5.5098
    ## 752                               58.28            14.1764             14.822
    ## 753                            117.4361             6.6877             7.5456
    ## 754                             55.4787             7.8797             4.9162
    ## 755                            594.6095            96.4072            49.3739
    ## 756                             24.9991             3.5311             3.4803
    ## 757                              8.3721             0.9552             0.4552
    ## 758                            127.3463            10.2882             8.2885
    ## 759                             55.7041              5.694             6.3662
    ## 760                             18.8734             1.0628             0.9608
    ## 761                           3408.3789             305.65             290.49
    ## 762                           4195.9952           409.6687           372.0687
    ## 763                             66.3376             4.4671             6.6477
    ## 764                            408.4035            53.6554            64.5527
    ## 765                            847.3969             54.224            61.7648
    ## 766                            113.6914            10.0528             7.8848
    ## 767                             57.9699             9.1072             7.8669
    ## 768                              3.2864             0.4658             0.4934
    ## 769                             47.5789            12.3593             7.7359
    ## 770                            475.4412            39.3127            31.6786
    ## 771                           1296.1527            22.2855            22.7018
    ## 772                              8.6292             1.6862             1.6628
    ## 773                              0.2109             0.0155             0.0129
    ## 774                             15.7697             3.3785             6.8857
    ## 775                             11.3826             0.4423             0.4666
    ## 776                              2.7569             0.1588             0.0593
    ## 777                              0.0921             0.0006             0.0031
    ## 778                             172.409            15.8431            13.5763
    ## 779                               35.63            27.2932             10.554
    ## 780                              45.482             4.7402             4.2798
    ## 781                            332.6128            38.0232            31.3923
    ## 782                             61.9792            12.1155             5.2781
    ## 783                            102.9209            24.9492            13.9105
    ## 784                           1578.9034           490.1701           111.7258
    ## 785                             39.8573             4.3648             3.9708
    ## 786                             17.0293             2.1651             1.2097
    ## 787                            363.8129             33.874            27.3722
    ## 788                             51.9717             5.4712             6.8253
    ## 789                             43.9274             3.7781             3.0897
    ## 790                            308.0702            55.9013            12.8496
    ## 791                            340.5002            67.7919            27.3725
    ## 792                            549.8899            46.3234            37.7077
    ## 793                           6119.3178           604.2689           362.4156
    ## 794                            403.0878            115.357            25.6613
    ## 795                             73.9217             5.7055             5.6951
    ## 796                             60.3287            14.5207            15.7115
    ## 797                            120.5326             6.5329             7.4652
    ## 798                             53.7609              7.729              5.128
    ## 799                             576.528            94.0986            51.8022
    ## 800                             23.7557              3.518             3.4562
    ## 801                              8.6299             0.9657             0.4436
    ## 802                            122.0047            10.3891             8.4156
    ## 803                             52.2519             5.6518             6.4172
    ## 804                             17.3577             1.0538             1.0735
    ## 805                            3331.501           301.7967            282.705
    ## 806                           4101.1966           404.5449           363.1178
    ## 807                             58.0068             4.3621             6.7859
    ## 808                            401.7941            53.9948            65.5043
    ## 809                            845.7613            53.6055            63.1959
    ## 810                            109.9096            10.0087             7.4746
    ## 811                             56.5273             8.8322             7.0007
    ## 812                              3.6051             0.4615             0.5042
    ## 813                             47.0186            12.2282             7.6317
    ## 814                            463.9216            38.1916            29.6152
    ## 815                           1213.8295            21.7502            22.6643
    ## 816                              8.1757             1.6576             1.6463
    ## 817                              0.2299             0.0158              0.013
    ## 818                             15.1039              3.325             6.3345
    ## 819                             11.2091             0.4448             0.4634
    ## 820                              2.7156              0.158             0.0557
    ## 821                              0.0901             0.0006              0.003
    ## 822                            175.1747            16.0849             9.6871
    ## 823                             36.4513            26.4385            10.3151
    ## 824                              44.411             4.6014             3.8013
    ## 825                            326.8471            37.1279            30.9506
    ## 826                             59.9844            12.1895             5.0235
    ## 827                            100.0808            25.0882            14.3733
    ## 828                           1609.3493           492.9113           116.1865
    ## 829                             40.4929             4.3789             3.8521
    ## 830                              17.999             2.0428              1.139
    ## 831                            333.3866              33.26            24.5057
    ## 832                             50.0055             5.2698             6.9563
    ## 833                             45.4478             3.8428             3.1096
    ## 834                            297.2828            54.3581            12.0539
    ## 835                            324.5406             66.337            29.6518
    ## 836                            537.6789            44.9917            36.7093
    ## 837                           5935.1837            610.114            340.821
    ## 838                            405.0492           112.3605            24.9836
    ## 839                             67.3969             5.6247             5.4139
    ## 840                             56.8277            14.9687            16.0478
    ## 841                            108.2537             6.4477              7.671
    ## 842                             45.4539             7.3611             4.6399
    ## 843                            542.0499            90.9432            47.1657
    ## 844                             21.9825             3.5218             3.2101
    ## 845                              8.3518             0.9758             0.4356
    ## 846                            114.4277            10.0841             7.8774
    ## 847                             49.7796             5.5589             6.0463
    ## 848                             14.1579             0.9845             0.9796
    ## 849                           3067.0348           296.0849           272.2006
    ## 850                           3770.4563           395.4634           342.6624
    ## 851                             55.0566              4.286             5.7597
    ## 852                            383.2425            52.7396            61.5567
    ## 853                            783.7343            51.5052            63.2232
    ## 854                            103.5773             9.7392             7.0156
    ## 855                             51.0553             8.6804             6.5414
    ## 856                              3.5718             0.4589             0.4693
    ## 857                             41.7265            11.9298             7.5414
    ## 858                            415.0889             38.013             28.053
    ## 859                           1141.4653            21.1748            22.5371
    ## 860                              7.4337             1.6801             1.6804
    ## 861                              0.2142             0.0155             0.0128
    ## 862                             12.9202             3.2263             4.1068
    ## 863                             10.7047             0.4449             0.4677
    ## 864                              2.6285             0.1672             0.0543
    ## 865                              0.0854             0.0006             0.0029
    ## 866                            169.9059            16.1237             9.4256
    ## 867                             33.5212            26.8536            10.1278
    ## 868                             42.9027             4.5059               3.19
    ## 869                            311.7732            35.9592            27.3025
    ## 870                             57.0498            12.0275             4.7186
    ## 871                             83.3564            24.0573            12.1632
    ## 872                           1526.4242           464.7224           116.8145
    ## 873                              35.802             4.1954             3.5415
    ## 874                             16.0611             2.0072             1.1392
    ## 875                            296.9497             33.495            24.2396
    ## 876                             46.4048             5.1698             6.7788
    ## 877                             44.2386             3.7864             3.0643
    ## 878                            299.2673            54.1057            12.9963
    ## 879                            274.6331            62.9953            27.0359
    ## 880                             487.161            43.6869            34.6943
    ## 881                           5509.6014           598.0765           332.2967
    ## 882                            406.2085           110.5517            24.5745
    ## 883                             72.5908             5.5361             5.1843
    ## 884                             58.3183            15.2219            15.8905
    ## 885                            114.8732             6.5082             8.2681
    ## 886                             47.7705             7.3605             4.8474
    ## 887                            554.0192            90.4008            47.2871
    ## 888                             21.2888              3.566             3.2791
    ## 889                              7.9916             0.9452             0.4504
    ## 890                             118.005            10.2844             7.6197
    ## 891                             50.2788             5.6201             6.0049
    ## 892                             17.8015             1.0168             1.0161
    ## 893                           3155.3084           293.4585           262.7704
    ## 894                           3890.9221           391.9114           332.7802
    ## 895                             63.5841             4.3383             5.4145
    ## 896                            391.5737            52.7203             59.376
    ## 897                            826.0631             50.385            54.6279
    ## 898                             96.5585             9.7841             7.3156
    ## 899                             51.6084             8.6778             6.4643
    ## 900                              3.4318             0.4595             0.4537
    ## 901                             41.3416            11.6971              7.823
    ## 902                            425.4994            37.2902            27.0756
    ## 903                           1191.0683            20.7406            21.9934
    ## 904                               8.529             1.6772             1.7429
    ## 905                              0.1996             0.0151             0.0127
    ## 906                             13.7251             3.1771             4.0224
    ## 907                             11.2553             0.4529             0.4698
    ## 908                              2.6406             0.1754             0.0519
    ## 909                              0.0824             0.0005             0.0027
    ## 910                            181.3804            15.9359             9.2075
    ## 911                             33.4032            26.8757            10.4299
    ## 912                             45.5478              4.522             3.0526
    ## 913                            332.5737            36.4484            26.8606
    ## 914                             52.6406            12.4843             4.6989
    ## 915                             80.9207            22.5844            12.4081
    ## 916                           1598.2109           491.0838           113.7712
    ## 917                             37.9112             4.1077             3.4163
    ## 918                             16.1364              1.998             1.1098
    ## 919                            280.9383            33.3486            25.3777
    ## 920                             52.3024             5.0762             7.0327
    ## 921                              45.903             3.7656             3.1334
    ## 922                            326.5516            57.5869            13.0792
    ## 923                             289.708            63.8592             28.953
    ## 924                            504.1904            42.9917            35.2986
    ## 925                           5727.0386           588.0416           338.2703
    ## 926                            406.6023           112.5692             25.065
    ## 927                             70.4555             5.3618             5.2937
    ## 928                             55.4015             15.276            16.6399
    ## 929                            104.4666             6.3455             7.0681
    ## 930                             53.2434             7.6828             4.7964
    ## 931                             555.614            90.5625            46.2217
    ## 932                             20.8693             3.5091             3.3923
    ## 933                              7.6723             0.8976             0.4579
    ## 934                            114.2965            10.2337              7.771
    ## 935                             45.2987             5.5247              6.063
    ## 936                              18.833             0.9574              1.004
    ## 937                           3002.8154           287.1602           260.4028
    ## 938                           3743.4304           384.0853           331.3906
    ## 939                             56.4928             4.2052             5.2577
    ## 940                            363.3468            51.4446            59.8787
    ## 941                            798.0579            48.8441            56.8712
    ## 942                             94.8136             9.6308             7.0103
    ## 943                               49.74             8.4596             6.7745
    ## 944                              3.3327             0.4443             0.4485
    ## 945                             37.6645            11.6288             7.6191
    ## 946                            414.2392            36.5677            26.8732
    ## 947                           1240.6845             20.299            21.6236
    ## 948                               8.088             1.5804             1.7303
    ## 949                              0.1848             0.0154              0.013
    ## 950                             13.9705             3.0456             4.3709
    ## 951                             11.1256              0.437             0.4604
    ## 952                              2.6631             0.1674             0.0504
    ## 953                              0.0792             0.0005             0.0027
    ## 954                              167.55            15.2613             9.1053
    ## 955                             33.1622            27.0501            10.6897
    ## 956                             44.6511             4.3974             3.0791
    ## 957                            330.3094            35.5379            27.2406
    ## 958                             51.5265            12.4466             4.4789
    ## 959                             87.9493            22.2581            12.6795
    ## 960                           1684.4326           506.6372           117.5688
    ## 961                             37.6719             4.1385             3.0094
    ## 962                             16.1777             1.9662             1.1032
    ## 963                            284.4073            33.1549            23.9343
    ## 964                             48.7257             4.9849             6.6816
    ## 965                              41.856             3.7323             3.0739
    ## 966                            344.6938            58.8114             12.652
    ## 967                            305.4636            63.3299            32.0565
    ## 968                            464.6184            42.0349            34.2178
    ## 969                           5603.8206           573.0632           343.4682
    ##                      X.5 Emissions.by.Sector                           X.6
    ## 1   Total F-Gas (MtCO2e)     Energy (MtCO2e) Industrial Processes (MtCO2e)
    ## 2                 5.2976            289.1548                       24.6697
    ## 3                 1.5952             55.3972                       10.1037
    ## 4                                   102.2428                        3.6147
    ## 5                 3.4158            112.3754                       15.7764
    ## 6                 0.0039             75.5292                        8.8465
    ## 7                10.6983            469.1862                       55.9785
    ## 8                 0.9475             22.7965                        3.7885
    ## 9                                     4.2138                        0.7281
    ## 10                0.0777            156.7649                       19.6028
    ## 11                0.0445             53.4132                        2.2395
    ## 12                                   35.9569                        1.0482
    ## 13               55.9789            3282.202                       353.202
    ## 14               59.1967           4296.8082                      457.6888
    ## 15                 0.115             54.4949                        5.1301
    ## 16               10.0559            385.5033                       59.1473
    ## 17               11.8614           1020.3233                       94.2089
    ## 18                1.1015             77.1709                       10.0729
    ## 19                0.3584             68.2528                       11.5727
    ## 20                0.4208              1.7787                         0.869
    ## 21                0.0369             30.9705                        3.1793
    ## 22                3.1707            417.7361                       38.3899
    ## 23                 61.84           1078.9753                      130.3402
    ## 24                                   19.1363                        0.5989
    ## 25                     0              0.2038                             0
    ## 26                                    32.745                        4.3968
    ## 27                0.0131             10.4299                        1.6215
    ## 28                     0              1.8781                        0.0003
    ## 29                0.0002               0.107                        0.0002
    ## 30                6.9148            153.7739                       22.1925
    ## 31                0.6451             23.4877                        3.3928
    ## 32                5.5702             29.4913                       13.8071
    ## 33                0.1229            374.0693                        22.025
    ## 34                                   41.6349                        4.8337
    ## 35                2.1158            177.7682                       24.8065
    ## 36               41.2925           2714.7111                      257.4314
    ## 37                0.2714             53.8758                        9.5433
    ## 38                0.2677             14.4158                        1.3176
    ## 39                 3.353            210.9281                       25.8126
    ## 40                0.4885             53.6696                        6.3298
    ## 41                0.2439             42.0067                         3.381
    ## 42                0.6034            132.8827                       15.4423
    ## 43                0.2032            735.5564                        79.841
    ## 44               13.8172            610.7557                       54.3951
    ## 45               90.2045           5267.3471                      316.1474
    ## 46                5.3196            291.0128                       23.9477
    ## 47                1.7556             59.2909                       10.1212
    ## 48                                   95.7824                         3.505
    ## 49                 3.254            115.1742                       15.1028
    ## 50                0.0048             57.5232                        6.9477
    ## 51                11.659            460.0637                        57.416
    ## 52                0.6533             17.1025                        2.9136
    ## 53                                    4.4972                        0.6872
    ## 54                0.0773            149.4649                        14.619
    ## 55                0.0635             63.9517                        2.3471
    ## 56                0.0001             32.9678                        1.0268
    ## 57               54.6882           3315.3605                      342.9349
    ## 58               57.7508            4266.203                      424.1711
    ## 59                0.0827              53.057                        4.7355
    ## 60               10.3484            411.4808                        58.906
    ## 61               11.4658             985.042                       90.2985
    ## 62                1.2742             77.0512                        9.9746
    ## 63                0.3362             67.5423                        7.4508
    ## 64                0.3496              1.7422                        0.7622
    ## 65                0.0555             31.8329                        2.8906
    ## 66                2.8617            417.8747                       38.0286
    ## 67                67.938            1086.827                      136.8073
    ## 68                                   17.6643                        0.5361
    ## 69                     0              0.2117                             0
    ## 70                                   34.8838                        4.4342
    ## 71                0.0132             11.0443                        1.5437
    ## 72                     0              2.0544                        0.0005
    ## 73                0.0002               0.108                        0.0002
    ## 74                5.8303            158.8552                       21.1772
    ## 75                0.6408             23.9186                        3.5313
    ## 76                5.0811             28.5715                       12.6578
    ## 77                0.1224             374.594                       19.0553
    ## 78                                    43.208                        4.9077
    ## 79                1.9421            147.4083                       17.5429
    ## 80               40.5735           2589.3165                      224.0694
    ## 81                 0.267             48.6942                        7.7377
    ## 82                0.3127             13.5482                        1.1981
    ## 83                3.0793            219.3994                       24.3909
    ## 84                0.4972              54.225                        6.1622
    ## 85                0.2308             44.0995                        3.0233
    ## 86                0.7443            138.8218                       17.7314
    ## 87                0.1622            642.0785                       66.5111
    ## 88               14.1114            620.3789                       52.5799
    ## 89               82.5683           5228.4711                      297.3741
    ## 90                5.2596            297.0332                       24.5871
    ## 91                1.1768             54.3642                        8.9054
    ## 92                                   88.9079                        3.2928
    ## 93                4.0179            113.6636                       15.3823
    ## 94                0.0043              55.093                          5.72
    ## 95                9.9039            477.7019                       55.2299
    ## 96                0.0109             16.3856                         2.545
    ## 97                                    4.7914                        0.7367
    ## 98                 0.077             133.384                       16.0692
    ## 99                0.0893             58.0815                          2.38
    ## 100                0.016             23.8161                        0.6035
    ## 101              55.2447            3243.702                      333.3126
    ## 102              57.4152                                          410.0003
    ## 103                0.046             52.3367                        4.4434
    ## 104               9.8703            405.2932                       56.6853
    ## 105              11.9298            936.0226                        92.284
    ## 106               1.0729             78.7612                        9.8506
    ## 107               0.2376             61.4634                        5.8538
    ## 108               0.1566              1.8654                        0.5673
    ## 109                0.071             31.7303                          2.82
    ## 110               2.2843             417.157                        37.469
    ## 111                73.92           1094.1925                      142.6878
    ## 112                                  14.4001                        0.2566
    ## 113                    0              0.2128                             0
    ## 114                                  19.6461                        2.5616
    ## 115               0.0135             10.8951                        1.4739
    ## 116               0.0015              2.1598                        0.0016
    ## 117               0.0005              0.1148                        0.0005
    ## 118               6.6333            157.5429                       21.4733
    ## 119               0.4144             25.7899                        3.3627
    ## 120               3.0101             29.4584                       10.0388
    ## 121               0.1166            365.0794                       18.2171
    ## 122                                  47.7799                        4.6233
    ## 123               1.3521             125.769                       18.3342
    ## 124              33.7446           2145.8952                      202.5065
    ## 125               0.2485             44.5789                        7.4004
    ## 126               0.1169             13.5388                        0.9329
    ## 127               3.6284            228.2628                       22.8426
    ## 128               0.3715             54.3067                        5.7028
    ## 129               0.2239             44.1261                        2.8682
    ## 130               0.6811            145.1173                       18.9269
    ## 131               0.1227            560.4445                       65.7688
    ## 132              14.0447            604.1343                       47.1979
    ## 133              86.2691           5331.8491                      302.2604
    ## 134               4.5669            300.3377                       24.3874
    ## 135               1.0695             54.7802                        8.8165
    ## 136                                  76.5396                        2.6392
    ## 137               3.8798            112.7327                       15.4743
    ## 138               0.0046             55.4816                        5.9297
    ## 139                8.949            477.9484                       55.0342
    ## 140                0.011             17.2912                        2.0012
    ## 141                                   4.9807                        0.8079
    ## 142               0.0766            131.9084                        12.923
    ## 143               0.1952             60.2822                        2.4566
    ## 144               0.0195             18.6039                        0.3449
    ## 145               57.717           3190.9999                       325.091
    ## 146              59.9056           4036.7425                      398.2342
    ## 147               0.0302             54.2918                        4.5019
    ## 148               8.5182             382.186                       54.8154
    ## 149              14.5543            928.0201                       92.4569
    ## 150               1.7071             78.3748                       10.1305
    ## 151               0.2789             61.7051                        6.9676
    ## 152               0.0768              1.9434                        0.5382
    ## 153               0.1008              31.957                        2.8106
    ## 154               2.1703            413.7288                       34.2635
    ## 155                75.58           1087.7093                      143.1422
    ## 156                                  12.2974                        0.0837
    ## 157               0.0001              0.2212                        0.0001
    ## 158               0.0001             15.7892                        1.6428
    ## 159               0.0143             11.0426                        1.4525
    ## 160               0.0015              2.1561                        0.0017
    ## 161               0.0002              0.1149                        0.0002
    ## 162               7.2164            162.2844                       22.3272
    ## 163                  0.2             25.2022                        3.2625
    ## 164               3.0639             30.6746                       10.8381
    ## 165               0.1255            367.0912                       18.2066
    ## 166                                   46.531                        4.5468
    ## 167               1.4094            120.8883                       18.1969
    ## 168              25.4219           2065.7231                      168.6487
    ## 169               0.1555             40.7931                        7.2429
    ## 170               0.1169             14.0474                        0.7956
    ## 171               3.1695            218.6646                        21.578
    ## 172               0.4215             54.1243                        5.8389
    ## 173               0.1701             41.8143                        2.5628
    ## 174               0.6852             151.559                       20.9181
    ## 175               0.1238            490.7611                       51.3202
    ## 176              14.6766            588.5876                       43.8876
    ## 177              86.9144           5438.9247                       301.738
    ## 178               2.9645            301.8524                       24.5903
    ## 179               1.2895             54.8149                        9.3101
    ## 180                                  64.2901                        2.0049
    ## 181               4.5994            115.9181                       18.0151
    ## 182               0.0049             52.5305                        7.4569
    ## 183               8.5355            494.6446                        56.955
    ## 184               0.0112             16.3117                        2.2283
    ## 185               0.0247              5.3889                        0.8639
    ## 186               0.0762            121.7452                       13.8557
    ## 187               0.2568              64.275                         2.555
    ## 188               0.0238             19.2254                        0.6334
    ## 189              62.2098           3175.3192                      343.3226
    ## 190              64.5619           3993.3722                      424.7273
    ## 191               0.0381             59.5259                        4.6861
    ## 192               7.3792            380.3121                       55.7636
    ## 193              15.0438            906.4893                       98.7021
    ## 194               2.2079             80.6829                       10.6154
    ## 195               0.3253             59.9043                        8.4193
    ## 196               0.0473              1.8907                        0.5101
    ## 197               0.1379             32.9597                        3.0887
    ## 198               2.1307            407.5707                        32.753
    ## 199               86.524           1143.6892                      156.3242
    ## 200                                  10.7132                        0.1467
    ## 201               0.0001              0.2072                        0.0001
    ## 202               0.0003             14.8499                        1.8275
    ## 203               0.0151              10.325                        1.3613
    ## 204               0.0015              2.2677                         0.002
    ## 205               0.0001              0.1171                        0.0001
    ## 206               8.6603            161.5849                       24.3127
    ## 207               0.2347             25.4557                        3.1786
    ## 208               2.9547             32.2676                       11.1665
    ## 209               0.1462            360.7256                        20.704
    ## 210                                  47.2279                        4.5321
    ## 211                1.491            118.7093                       18.5195
    ## 212              22.8249           1848.7287                      143.9743
    ## 213               0.1415              37.935                         8.023
    ## 214               0.1167             14.0579                        0.9527
    ## 215               4.3664            228.9085                       25.2078
    ## 216               0.4889             56.2343                        6.2857
    ## 217               0.1624             40.9198                        2.7241
    ## 218               0.6042             149.385                       19.2482
    ## 219                0.139            432.1041                       40.3182
    ## 220              15.6062            575.1018                       46.4151
    ## 221              90.1627           5523.8703                       311.819
    ## 222                2.442            313.5726                       24.3621
    ## 223               1.5612             57.6697                        9.8208
    ## 224               0.0028             57.2595                        2.0357
    ## 225               4.9921            116.4614                       19.2232
    ## 226               0.0075             53.0297                        9.4216
    ## 227               8.3646            508.7885                       57.4725
    ## 228                0.061              17.263                        2.0159
    ## 229                                   5.3076                        0.8049
    ## 230               0.0761            123.6524                       13.1882
    ## 231               0.3258             61.2463                         2.726
    ## 232               0.0286             17.5965                        0.6755
    ## 233              66.7218           3206.1526                      350.3305
    ## 234              69.7245           4028.6656                      437.4081
    ## 235               0.1008             56.0635                        4.6991
    ## 236               6.5359            386.8006                       56.3054
    ## 237              15.5716            902.0943                       96.8219
    ## 238                3.348             80.6191                       12.2631
    ## 239               0.3603             59.2272                        7.8768
    ## 240               0.0687              1.9162                        0.5461
    ## 241               0.2129             33.8454                         3.083
    ## 242               2.5391             431.111                       35.9289
    ## 243              51.4928           1156.7523                      121.3608
    ## 244               0.0009              9.5146                        0.1602
    ## 245               0.0004              0.2106                        0.0004
    ## 246               0.0028             13.9035                        2.1115
    ## 247               0.0171              8.3409                        1.0016
    ## 248               0.0015               2.226                        0.0032
    ## 249               0.0003              0.1142                        0.0003
    ## 250               8.2433            165.6636                       23.5662
    ## 251               0.2718             25.5273                        3.3052
    ## 252               2.6961             32.1564                       11.0973
    ## 253               0.3694            361.8679                       21.9415
    ## 254               0.0731             50.7664                        5.2819
    ## 255               1.8688            122.3206                       21.3402
    ## 256              22.6563           1777.9939                      154.3062
    ## 257               0.1359             38.9477                        8.5523
    ## 258                0.151             14.9193                        1.0017
    ## 259               5.5864            239.5347                        26.673
    ## 260               0.6022             55.4635                        6.6441
    ## 261               0.2914             41.7741                        2.6532
    ## 262               0.5164             161.502                       24.2066
    ## 263               0.1535            386.1465                       35.6802
    ## 264              17.0289             567.385                       46.5919
    ## 265             107.5817           5575.9882                       339.357
    ## 266                1.876            320.8683                       24.2616
    ## 267               1.6922             61.4739                         9.668
    ## 268               0.0037             58.2254                         2.137
    ## 269               4.8778            121.2514                       18.8543
    ## 270               0.0096             53.7372                         9.124
    ## 271               8.3356            524.7376                       59.0893
    ## 272               0.0804             17.8233                        2.0894
    ## 273               0.0097              5.6135                        0.8723
    ## 274               0.1829             127.351                       13.8935
    ## 275               0.3922             74.6762                        2.8281
    ## 276               0.0341              18.341                        0.6829
    ## 277              71.1756           3286.0999                      349.9061
    ## 278              74.3122           4136.3667                      436.4186
    ## 279               0.1498             61.7614                        4.9193
    ## 280                7.568            400.9232                       56.0896
    ## 281              14.8974            923.8541                       95.8475
    ## 282               3.8677             82.8066                       12.9097
    ## 283               0.3556             60.9592                        8.0615
    ## 284               0.0418              2.0067                        0.5257
    ## 285               0.2971             35.4332                        3.2308
    ## 286               2.1711            427.2193                       32.7497
    ## 287              52.2136           1168.8989                      123.4178
    ## 288               0.0011              9.5937                        0.1763
    ## 289               0.0007              0.2129                        0.0007
    ## 290               0.0037             14.4079                        2.5258
    ## 291               0.0176              8.4513                        0.9463
    ## 292               0.0015              2.2787                         0.003
    ## 293               0.0007              0.1187                        0.0007
    ## 294              10.1263            173.3418                       24.8313
    ## 295               0.4524             27.0554                        3.4655
    ## 296               2.5158             35.4646                        10.899
    ## 297               0.4569            376.9827                       20.8514
    ## 298               0.0953             48.1196                        5.3908
    ## 299               1.8668            126.4354                       20.7763
    ## 300               20.612           1748.8901                       140.124
    ## 301               0.0693             38.9294                        8.5475
    ## 302               0.1453              15.637                         0.998
    ## 303               6.1148            227.1135                       27.0795
    ## 304               0.6218             59.7218                        6.4351
    ## 305               0.3358             42.6119                        2.5275
    ## 306               0.8941            179.6827                       24.3171
    ## 307               0.1235            350.2373                       33.8073
    ## 308              18.3119            587.0441                         48.44
    ## 309             117.7893           5765.8363                      350.4042
    ## 310               1.9548            331.7911                       24.3928
    ## 311               1.6963             60.5546                       10.2507
    ## 312               0.0056             59.5229                        2.3031
    ## 313                2.388            115.1973                       16.3863
    ## 314               0.0121             51.0715                        8.4405
    ## 315               8.8334             539.054                       58.5233
    ## 316               0.1029             18.7548                        2.3254
    ## 317                                   5.7382                        0.8298
    ## 318               0.3412            123.6064                       14.8471
    ## 319               0.4022             65.1736                        3.0167
    ## 320               0.0394             17.8571                        0.7195
    ## 321              75.0682           3223.2051                      356.1619
    ## 322              78.7296           4043.8771                      441.6952
    ## 323               0.2386             60.1681                        5.2269
    ## 324               8.3397            393.5208                       56.8368
    ## 325               15.261            892.3363                       95.7738
    ## 326               4.2092             87.4418                       13.3063
    ## 327               0.4529             59.7932                        7.6647
    ## 328               0.1074              2.0464                        0.6425
    ## 329               0.4165             36.5748                         3.687
    ## 330               2.5506            431.4585                       33.2974
    ## 331              51.0908           1165.8201                      120.1259
    ## 332               0.0024              9.0313                        0.1831
    ## 333                0.001              0.2253                         0.001
    ## 334               0.0055             13.9637                        2.4844
    ## 335                0.019              7.8671                        0.8391
    ## 336               0.0754              2.2687                        0.0771
    ## 337               0.0003              0.1191                        0.0003
    ## 338                10.96            166.1616                       26.1106
    ## 339               0.2527             29.3336                        3.2028
    ## 340               2.3779             35.3741                       11.0239
    ## 341               0.5895            366.7247                       21.4593
    ## 342               0.1315             50.7429                        5.6682
    ## 343               1.9106            115.8612                       19.0406
    ## 344              22.7747           1657.0373                      139.8056
    ## 345               0.0786             38.8058                        8.7596
    ## 346               0.1539             15.9502                        1.0276
    ## 347               7.1225            247.1814                       29.0729
    ## 348               0.7513             54.5805                        6.4115
    ## 349               0.4467              41.959                        2.4641
    ## 350               1.1279            192.1169                       24.1397
    ## 351               0.1326            329.6008                       37.8572
    ## 352              20.6188            561.4732                       50.6114
    ## 353             125.1755           5838.5109                       354.139
    ## 354               2.5299            345.4185                       25.5702
    ## 355               1.5116             60.5319                        9.7449
    ## 356               0.0074             57.3155                        2.6544
    ## 357               1.7269            121.3714                       15.8983
    ## 358               0.0162             49.6912                        6.1511
    ## 359              10.0148            548.8044                       55.3699
    ## 360               0.1308             19.4072                        2.1049
    ## 361                                    5.865                        0.7847
    ## 362               0.3816            117.0716                       14.8503
    ## 363               0.4818             61.1686                        2.9936
    ## 364               0.0489             16.2053                        0.7541
    ## 365              74.7163           3268.2432                      335.7213
    ## 366              78.5764           4035.1141                      416.7201
    ## 367               0.3017              56.856                        5.2323
    ## 368               9.1218            415.0253                       50.6384
    ## 369              15.8468             882.853                       81.8291
    ## 370               4.7164              92.258                        13.892
    ## 371               0.5128             58.7144                        7.6554
    ## 372               0.2172              2.0292                        0.7748
    ## 373                0.372             38.8221                        3.5311
    ## 374               2.8904            442.9808                       33.7496
    ## 375              46.4418           1135.6052                      108.5803
    ## 376               0.0036              8.6152                        0.1849
    ## 377               0.0014              0.2367                        0.0014
    ## 378               0.0082             14.6766                        2.9103
    ## 379                0.022              7.1402                        0.6829
    ## 380               0.0754              2.2727                        0.0765
    ## 381               0.0005              0.1169                        0.0005
    ## 382              11.4654             168.061                        26.475
    ## 383               0.3997             27.6704                        3.4427
    ## 384               2.4223             35.3822                       11.2749
    ## 385               0.6813            338.9165                       19.7577
    ## 386               0.1753             55.2277                        5.8386
    ## 387               1.9079            101.2508                        17.908
    ## 388              25.3133           1645.7286                       134.107
    ## 389               0.0781             37.9416                        8.9542
    ## 390               0.1462             15.6497                        1.0116
    ## 391               6.8188            254.1502                        29.969
    ## 392                0.763             55.0605                        6.5984
    ## 393                0.534             43.2736                        2.5584
    ## 394               1.1769            191.3388                       24.7505
    ## 395               0.1155            325.7398                       37.9194
    ## 396              18.5528            564.2756                       49.0039
    ## 397             137.6637           5872.3273                      358.3739
    ## 398               2.3321            352.0202                       25.9722
    ## 399               1.4057             59.3009                        9.4894
    ## 400               0.0084             54.5372                        2.7323
    ## 401                1.279            115.5508                       15.5505
    ## 402               0.0208             43.4324                         5.407
    ## 403                9.593            563.8805                       52.0529
    ## 404               0.1552             19.9847                        2.5853
    ## 405               0.0194              6.1288                        0.8118
    ## 406                0.347            111.3707                       12.1029
    ## 407               0.5865             58.6364                        3.2199
    ## 408               0.0587             15.1034                        0.7077
    ## 409              65.2331            3243.233                      305.4327
    ## 410              69.3703           3973.7108                      378.8712
    ## 411               0.3959             56.3163                        5.3901
    ## 412              10.3808            406.1682                       45.6546
    ## 413              14.1989            858.1271                       74.7274
    ## 414               5.4601             91.6531                       14.5834
    ## 415               0.7164             58.9898                        7.3331
    ## 416                0.215              2.0981                        0.9222
    ## 417               0.4873             40.1568                         3.596
    ## 418               3.0389            448.3513                       34.1808
    ## 419              39.6732           1170.9563                       95.2304
    ## 420               0.0043              7.9613                        0.2228
    ## 421               0.0018               0.236                        0.0018
    ## 422               0.0108             12.3319                        2.8561
    ## 423                0.026              7.5085                         0.725
    ## 424               0.0754              2.3634                        0.0758
    ## 425               0.0004              0.1178                        0.0004
    ## 426               6.6595            162.3864                       21.2261
    ## 427               0.3395             29.0823                        3.5797
    ## 428               2.5334             36.2674                       11.4848
    ## 429               0.8942            330.8902                       18.9011
    ## 430               0.2336             62.7131                        6.2408
    ## 431               1.7551             90.0824                        15.114
    ## 432              25.6826           1671.0838                      151.1583
    ## 433               0.0845              36.857                        8.8746
    ## 434               0.1509             14.9666                        1.0317
    ## 435                8.202            278.4171                       32.3556
    ## 436               0.8875             52.0723                        6.6144
    ## 437                0.595               43.37                        2.6614
    ## 438               1.0317            191.2972                       23.9279
    ## 439               0.1001            318.3425                        39.579
    ## 440              12.0541            553.3664                       32.2475
    ## 441             136.6958           5939.6959                      353.8617
    ## 442               2.6604            361.1913                       25.8157
    ## 443               1.3165              59.246                       10.0589
    ## 444               0.0098             52.6841                        2.6047
    ## 445               1.4157            116.9938                       15.6581
    ## 446               0.0248             42.3507                        6.2346
    ## 447              10.2991            589.4738                       52.0543
    ## 448               0.1829             19.4823                        2.8612
    ## 449               0.0193              6.3605                        0.8306
    ## 450               0.4132            119.6034                       13.5611
    ## 451               0.6902             54.2165                          3.39
    ## 452               0.0723              14.771                        0.7059
    ## 453              62.9124           3259.1703                       309.929
    ## 454              67.1168           3980.7597                      390.2382
    ## 455               0.5682             54.4649                         5.583
    ## 456              10.0118            402.4315                       43.9718
    ## 457              12.6844            856.1885                       77.4516
    ## 458               4.3529              96.483                       13.7125
    ## 459               0.6211             56.5975                        8.1594
    ## 460               0.1643              2.0417                        0.9764
    ## 461               0.6196             42.4581                        4.2231
    ## 462               3.6965            449.6866                        36.249
    ## 463              35.5723           1190.8443                       94.3452
    ## 464               0.0064              7.3411                        0.1794
    ## 465               0.0024              0.2295                        0.0024
    ## 466               0.0139             10.8074                         3.019
    ## 467               0.0308              8.1891                        0.7566
    ## 468               0.0098              2.3606                        0.0101
    ## 469               0.0029              0.1158                        0.0029
    ## 470               5.7676            164.6988                       20.2615
    ## 471               0.3216             29.6578                        3.5238
    ## 472               2.5799             35.5903                       11.7768
    ## 473               1.3038            317.7978                       21.4579
    ## 474               0.3288             61.2459                        6.4944
    ## 475               1.4558             92.8944                       16.7945
    ## 476              29.0323           1668.0229                      166.6827
    ## 477               0.1018             35.6466                         8.294
    ## 478               0.1622             15.0584                        1.0628
    ## 479               9.0062            289.2234                       33.8863
    ## 480                0.902             50.5836                        6.8118
    ## 481               0.7174             42.2899                          2.93
    ## 482               1.6564            213.1999                       24.3738
    ## 483               0.1143            305.8783                        42.279
    ## 484              11.6014            560.6706                        31.811
    ## 485             137.2661            6119.612                      352.4332
    ## 486                3.687            367.8348                        26.838
    ## 487               1.5236             63.3651                       10.0271
    ## 488               0.0134             51.7498                         2.565
    ## 489                1.423            117.5108                       14.9337
    ## 490               0.0358             46.0039                        6.1679
    ## 491               9.6968            585.3444                       50.5239
    ## 492               0.2057             20.3994                        2.8829
    ## 493               0.0184              6.2442                         0.802
    ## 494               0.5744            119.9017                       12.8858
    ## 495                0.713              56.085                        3.2991
    ## 496               0.0872             15.1293                        0.7464
    ## 497              60.2226           3324.4042                      299.6671
    ## 498              65.1733           4057.9429                      377.7021
    ## 499               0.7202             59.7569                        5.7268
    ## 500              10.6084             403.007                       43.8771
    ## 501              13.2353            876.3748                       74.4076
    ## 502               3.9245             98.9555                        13.182
    ## 503                0.714             58.3016                        8.0042
    ## 504               0.1333              2.0046                        0.9771
    ## 505               0.6437             44.5696                        4.3306
    ## 506               4.6871            454.5491                       38.3703
    ## 507               30.084            1177.931                       84.3035
    ## 508               0.0096              7.7617                        0.2073
    ## 509               0.0032              0.2274                        0.0032
    ## 510               0.0184             11.4614                        3.2656
    ## 511                0.037               8.769                        0.7049
    ## 512               0.0169              2.4807                        0.0173
    ## 513               0.0007               0.117                        0.0007
    ## 514               3.3592             170.983                       16.7036
    ## 515               0.4076             31.6994                        3.7079
    ## 516               2.5231             37.5084                       11.2537
    ## 517               1.9101            316.4386                       20.1047
    ## 518               0.4222             61.6683                        6.1324
    ## 519               1.2613             95.8104                       15.9303
    ## 520              27.3927           1687.2755                      167.7199
    ## 521               0.1314             38.1328                        8.7701
    ## 522               0.1732             15.8723                        1.1334
    ## 523               5.9859            292.7837                       31.0668
    ## 524               0.9618             51.4604                        6.8096
    ## 525               0.7865             43.2213                        3.0342
    ## 526               1.6958             196.615                       23.3237
    ## 527                0.123            307.3887                       44.6436
    ## 528              12.0766             572.182                       30.5129
    ## 529             126.1068            6036.684                      318.6409
    ## 530               4.1403            371.2769                       27.4297
    ## 531               1.6011             64.4751                       10.6965
    ## 532               0.0169              51.674                        2.8181
    ## 533               1.4843            116.1557                       15.3654
    ## 534               0.0488             43.4823                        5.5783
    ## 535              10.0798            591.1131                       51.8812
    ## 536               0.2377             21.5076                        2.8499
    ## 537               0.0187              6.4086                        0.8309
    ## 538               0.4727            116.2554                       12.5465
    ## 539               0.7361             55.6221                        3.2098
    ## 540                0.088             14.8247                        0.5453
    ## 541              63.1039           3314.1751                      296.8792
    ## 542              68.2786           4027.3731                      372.6189
    ## 543               0.5345             62.3337                        5.4883
    ## 544              12.9047            398.7174                        44.131
    ## 545              13.0813            860.8772                       72.5112
    ## 546               4.0737              98.864                       13.2169
    ## 547               0.7403             56.7903                        7.3206
    ## 548                0.112              2.0797                        0.9539
    ## 549               0.5894             43.3551                        3.7558
    ## 550               5.2649            456.6813                       38.6038
    ## 551              26.7061           1217.6757                       77.9275
    ## 552               0.0132              7.7559                        0.2237
    ## 553               0.0035              0.2324                        0.0035
    ## 554               0.0245             11.5514                         3.445
    ## 555               0.0452                9.53                         0.729
    ## 556               0.0303              2.5008                        0.0306
    ## 557               0.0013              0.1149                        0.0013
    ## 558               4.0905            171.3236                       17.0719
    ## 559               0.5915             31.8822                        3.8645
    ## 560               2.1679             37.1238                       10.5589
    ## 561               2.4232            305.2269                       18.3705
    ## 562                0.535             65.3281                        6.4562
    ## 563               0.9573             96.6173                       16.5479
    ## 564              21.6365           1690.0212                      166.0107
    ## 565               0.1583             35.8542                        9.1524
    ## 566               0.1993             15.9302                         1.148
    ## 567                4.688            310.6985                       30.4599
    ## 568               1.0306             52.2424                        6.9508
    ## 569               0.8326             42.1968                        3.0321
    ## 570               2.4148            204.5851                       25.5473
    ## 571               0.1436            309.2447                       45.2272
    ## 572              12.5606            555.8661                       28.6726
    ## 573             133.8352           6066.6267                      327.8503
    ## 574               4.6381            377.8303                       28.5597
    ## 575               1.6303             70.5892                        10.747
    ## 576               0.0199             51.8525                        3.0585
    ## 577               1.7508            119.3976                       14.7817
    ## 578               0.0668             47.2764                        6.1994
    ## 579              10.2282            606.9967                       53.5865
    ## 580               0.2759             22.9323                        2.8821
    ## 581               0.0191              6.7932                        0.8404
    ## 582               0.7159            118.7578                        13.656
    ## 583               0.7665             60.9316                        3.2293
    ## 584               0.0932             16.5944                        0.6054
    ## 585              65.4875           3372.4203                      305.2041
    ## 586              71.2387           4115.3857                      385.5147
    ## 587               0.7278             69.9184                        5.9802
    ## 588              14.1763            407.6674                       45.1903
    ## 589              12.4391            856.8689                       77.4655
    ## 590               3.8799            102.7624                       13.1437
    ## 591               0.8481             60.1855                        7.2039
    ## 592               0.1083              2.0718                        0.9497
    ## 593               0.7264             43.8907                         3.069
    ## 594               6.0462            471.4877                        40.204
    ## 595              26.1943           1223.3431                        76.598
    ## 596               0.0201              7.9537                        0.2473
    ## 597                0.004               0.242                         0.004
    ## 598               0.0359             11.5448                        3.5287
    ## 599               0.0509             10.0124                        0.6745
    ## 600               0.0422              2.6803                        0.0424
    ## 601               0.0016              0.1093                        0.0016
    ## 602               2.3342            174.8214                       15.5038
    ## 603               0.7901             33.2252                        4.2766
    ## 604               1.6122             38.4665                        9.8933
    ## 605               2.9174            316.1618                       21.2652
    ## 606               0.6612             60.6168                        6.4821
    ## 607               0.5718            102.8502                       16.4735
    ## 608              17.5259           1728.5643                       167.755
    ## 609               0.1909             36.5213                         9.021
    ## 610               0.2296              15.646                        1.2274
    ## 611               5.8698            314.0012                       31.9954
    ## 612               1.0371             53.1794                        6.6788
    ## 613               0.9258             43.3973                         3.079
    ## 614               2.8047             218.561                       26.2974
    ## 615               0.1631             321.604                       49.3417
    ## 616              13.5298            564.1881                       30.5301
    ## 617             127.4815           6118.9422                      315.8305
    ## 618               5.2148            392.1586                       29.8952
    ## 619               1.6527              71.065                       10.1814
    ## 620               0.0242             55.1412                        3.2388
    ## 621               1.8712            119.7865                       15.3587
    ## 622               0.0869             45.9253                        6.2481
    ## 623              10.2992            603.2905                       61.6811
    ## 624               0.3133             22.4002                         3.247
    ## 625               0.0196              6.9517                        0.9032
    ## 626               0.6695            119.1627                       14.2397
    ## 627               0.8213             55.3333                        3.0391
    ## 628               0.1057             16.7222                        0.7647
    ## 629              65.5678            3370.568                      312.7693
    ## 630              72.3992           4109.8506                      399.3861
    ## 631               0.7649             65.7868                        6.2982
    ## 632              14.0006            407.9123                       43.1633
    ## 633              12.7212            839.8626                       82.1055
    ## 634               3.9664            103.0787                       13.2234
    ## 635               1.1142             57.9938                        8.4019
    ## 636               0.0902              2.1218                        0.9547
    ## 637               0.6671              44.034                        3.1742
    ## 638               6.8704            473.5379                       42.7791
    ## 639              23.1268           1223.1349                       73.7655
    ## 640               0.0235              7.9801                        0.3898
    ## 641               0.0046              0.2422                        0.0046
    ## 642               0.0509             12.1641                        3.7241
    ## 643               0.0539             11.3562                        0.7197
    ## 644               0.0899              2.6346                        0.0903
    ## 645               0.0021              0.1026                        0.0021
    ## 646               2.1801            176.1049                       15.9581
    ## 647               0.5589             32.7582                        4.0118
    ## 648               1.6637             38.4032                       10.5913
    ## 649               3.6815            319.3733                       22.9209
    ## 650               0.7599             62.2627                        7.0941
    ## 651               0.5232             98.9594                       17.5317
    ## 652              20.6225           1754.6177                      176.5953
    ## 653               0.2168             35.4399                       10.1313
    ## 654               0.2496             15.9755                         1.271
    ## 655               5.6123            331.4914                       32.1286
    ## 656               1.1042             51.9605                        7.0711
    ## 657               1.0448             43.8284                        3.3472
    ## 658               3.4566            227.9773                       28.5215
    ## 659               0.2515             320.257                        51.593
    ## 660              12.6773            565.0874                       30.9287
    ## 661             134.8004           6227.8734                      327.1292
    ## 662               5.8248             398.269                       29.0976
    ## 663               1.6395             72.1122                        10.637
    ## 664               0.0277             55.3115                        3.4846
    ## 665               1.7021            116.2355                       15.3203
    ## 666               0.1204             46.6244                        6.6368
    ## 667              10.1059            597.3366                       60.4614
    ## 668               0.3471             22.6724                        3.2945
    ## 669               0.0222              6.9948                        0.9152
    ## 670               0.6902            120.0843                       12.9792
    ## 671               0.8548             51.6947                        2.4578
    ## 672               0.1192             16.0207                        0.8071
    ## 673              67.6294           3348.2338                      311.0686
    ## 674              75.6594           4084.1763                      402.7227
    ## 675               0.9392             54.0356                        6.3743
    ## 676              13.8575            411.8244                       42.6577
    ## 677              12.8145            824.2138                       78.7792
    ## 678               4.0452            106.2306                       13.8815
    ## 679               1.1234             56.9634                        8.9367
    ## 680               0.0872              2.0756                        0.9346
    ## 681               0.7458             45.7324                        3.2986
    ## 682               7.5809            471.9017                       42.5919
    ## 683              22.3169           1226.8212                       73.6534
    ## 684               0.0359              8.0793                        0.2862
    ## 685               0.0047              0.2421                        0.0047
    ## 686               0.0697              12.859                        4.0889
    ## 687               0.0582             11.6358                        0.7161
    ## 688               0.0895              2.7224                        0.0899
    ## 689               0.0022              0.1012                        0.0022
    ## 690               2.0178            171.0024                       15.7527
    ## 691               0.7908             34.1531                        4.2911
    ## 692               1.6648              37.694                       10.2458
    ## 693               4.6136            317.2949                       27.9341
    ## 694               0.8738             64.7779                        7.1354
    ## 695               0.6187             96.6021                       18.1999
    ## 696               21.513             1739.31                      178.5397
    ## 697               0.2425             35.5006                         9.407
    ## 698               0.2846             16.1966                         1.373
    ## 699               5.9651             346.158                       33.6086
    ## 700               1.1891              49.604                        6.9758
    ## 701                1.128             44.3454                        3.5198
    ## 702               3.7255            242.3445                       28.7808
    ## 703               0.3811            320.1709                       52.3954
    ## 704              13.5186            559.5669                       31.2958
    ## 705             136.1839           6251.6174                      330.7654
    ## 706               5.2746            402.4797                       29.2835
    ## 707                1.616             68.9298                       11.0285
    ## 708               0.0319             57.6637                        3.7136
    ## 709                1.793            112.4114                       14.5416
    ## 710               0.1732             47.7854                         6.455
    ## 711               9.2857            586.8929                       61.0187
    ## 712               0.3791             22.8454                        3.4461
    ## 713               0.0239              7.2565                        0.9266
    ## 714                0.978            120.7677                       14.1564
    ## 715               0.8923             59.6624                        2.5383
    ## 716               0.1365             15.3854                        0.8715
    ## 717              68.0687           3328.9654                      303.3092
    ## 718              77.2306           4080.0866                      400.2692
    ## 719               0.8334             65.3755                        6.3018
    ## 720              14.2569            402.6547                       41.4597
    ## 721              12.6563            828.8183                        79.554
    ## 722               2.2084            104.8796                       11.6593
    ## 723               0.9578             56.2264                        8.3116
    ## 724               0.3946               2.143                        1.3499
    ## 725               0.7599             45.3556                        3.2986
    ## 726               8.2257            466.8134                       38.1435
    ## 727              23.9643           1208.1872                       75.6973
    ## 728               0.0698              8.4917                        0.3481
    ## 729               0.0045              0.2438                        0.0045
    ## 730               0.0937             13.0492                         4.341
    ## 731               0.0628              11.439                        0.7732
    ## 732               0.1124              2.6891                        0.1128
    ## 733               0.0015              0.0916                        0.0015
    ## 734               2.1978            167.7474                       15.4872
    ## 735               0.7729             34.1631                        4.2803
    ## 736                1.534             38.4769                        9.3701
    ## 737               5.2547            328.9768                       30.4174
    ## 738               0.9882             60.1663                        6.9433
    ## 739               0.7639             99.7092                       19.3346
    ## 740              19.5539           1796.3834                      187.4363
    ## 741               0.3008             34.4324                        10.252
    ## 742               0.2973             16.3513                        1.4329
    ## 743                6.619            335.3868                       34.4408
    ## 744               1.1745             49.6081                        6.9694
    ## 745               1.1382             44.0099                        3.4962
    ## 746               4.0455            259.1519                       30.6952
    ## 747               0.4563            332.5616                       56.4095
    ## 748              13.9701             558.401                       30.6815
    ## 749             135.6893           6178.3494                      335.6976
    ## 750               5.7376            411.9745                       30.9157
    ## 751               1.6106             65.7363                       11.4457
    ## 752               0.0333             56.8353                        3.8538
    ## 753               2.0005            108.1021                       13.9547
    ## 754               0.2134              51.456                        6.8499
    ## 755               8.4494            609.7618                       59.7872
    ## 756               0.4196             24.1676                        3.6293
    ## 757               0.0256              7.5131                        0.9185
    ## 758               1.7019             120.112                       15.2647
    ## 759               0.9139             54.8503                        2.5593
    ## 760                 0.15             18.2705                         1.059
    ## 761              70.3849           3265.3061                      307.8925
    ## 762              81.3011            4014.962                      411.6036
    ## 763               0.9646             63.2868                        6.8298
    ## 764               14.436            392.3025                       41.6187
    ## 765              12.5604            804.8871                       81.6751
    ## 766               2.5571            107.4365                       11.9113
    ## 767               1.0958             54.4224                         8.097
    ## 768               0.3461              2.1995                        1.5002
    ## 769               0.7318             45.5163                        3.3122
    ## 770               8.9349            458.1646                       38.6013
    ## 771              24.0873           1242.2432                       74.2944
    ## 772               0.1073              8.8168                        0.4041
    ## 773               0.0048              0.2132                        0.0048
    ## 774               0.1235             13.2833                        6.1952
    ## 775               0.0675             10.8525                        0.7672
    ## 776               0.1306              2.7759                        0.1309
    ## 777               0.0039              0.0947                        0.0039
    ## 778               2.3706            167.6178                       14.7755
    ## 779               0.9838               33.22                        4.6558
    ## 780               1.5093             40.4056                        9.3498
    ## 781               5.8326            327.6763                       32.7324
    ## 782               1.1375                57.1                        7.5168
    ## 783               0.9231             96.1235                       20.6031
    ## 784              18.7287           1791.7552                      190.7125
    ## 785               0.3268             32.7495                       10.0101
    ## 786               0.2856             16.4566                        1.4463
    ## 787               6.9501             342.147                       34.1868
    ## 788               1.2374             48.2494                        6.9217
    ## 789               1.1524             42.0084                        3.5186
    ## 790               4.1264             289.292                       29.2618
    ## 791               0.6374            329.3157                       62.6732
    ## 792              14.1146            548.1258                       32.3317
    ## 793             139.9315           6266.9031                      347.2313
    ## 794               6.2328            419.0108                       31.3238
    ## 795                 1.64             64.9746                       11.9367
    ## 796               0.0382             58.6595                         3.971
    ## 797               2.1147            111.4176                       13.8887
    ## 798               0.3247             50.6773                        5.9725
    ## 799               8.4869            592.1957                       58.5458
    ## 800               0.4367             22.9026                        3.5924
    ## 801               0.0263              7.7712                        0.9206
    ## 802                1.337             115.471                       14.0854
    ## 803               0.9162             51.6786                        2.2731
    ## 804               0.1327             16.7458                        1.0511
    ## 805              73.3079           3199.6745                      292.4957
    ## 806              83.5525           3936.4435                      388.1263
    ## 807               1.0556             54.7584                        7.1652
    ## 808              15.0249            386.6225                       40.1358
    ## 809                12.43            805.2215                       78.8578
    ## 810                2.941            104.1092                       11.7751
    ## 811               1.2279             53.4049                        6.8412
    ## 812               0.4228              2.0747                        2.0195
    ## 813               0.7295             45.2499                        3.0311
    ## 814               9.4491            449.2023                       35.6684
    ## 815              23.7086           1161.5645                       70.7054
    ## 816                0.083              8.3535                        0.3718
    ## 817               0.0055              0.2323                        0.0055
    ## 818               0.1559             13.1328                        5.5252
    ## 819               0.0703              10.737                         0.706
    ## 820               0.1315              2.7348                        0.1317
    ## 821               0.0029              0.0925                        0.0029
    ## 822               2.3664            171.5062                       10.2434
    ## 823               0.8612             34.3485                         4.294
    ## 824               1.5301              39.007                        9.1806
    ## 825               5.2884            321.4686                         31.57
    ## 826               1.2842             55.5633                        7.3906
    ## 827               0.9219             95.9652                       17.9324
    ## 828              18.9731           1834.1443                      180.3814
    ## 829               0.3898             33.5461                        9.9017
    ## 830               0.2255             17.4977                         1.327
    ## 831               7.7241            314.7865                       31.6875
    ## 832               1.1755             46.4007                        6.8043
    ## 833               1.2824             43.5524                        3.6401
    ## 834               3.5125            278.3333                       29.8299
    ## 835               0.7315            318.7553                       56.1475
    ## 836              14.6023            536.2163                       31.4829
    ## 837             135.4502           6096.2426                      318.7101
    ## 838               6.7296            422.2761                       29.7091
    ## 839               1.5204             60.3562                        9.7552
    ## 840               0.0346             54.8326                        3.9963
    ## 841               2.0955            101.9346                       11.2315
    ## 842               0.3504             44.5934                        3.2101
    ## 843               8.8714            560.4416                       50.8058
    ## 844               0.4443             21.6507                        2.9835
    ## 845               0.0403              7.6653                        0.7626
    ## 846                1.097            110.1638                       11.1533
    ## 847               0.8681             49.5769                        1.7824
    ## 848               0.1396             14.1297                         0.451
    ## 849              74.8366           2971.8344                      254.0563
    ## 850              84.8601           3658.9974                      322.6687
    ## 851                0.948             52.6798                        5.3481
    ## 852              15.4642            370.5601                       37.0148
    ## 853              12.8454            751.5306                        72.113
    ## 854               3.3018             99.5875                       10.1322
    ## 855               1.1036             48.7373                        5.9739
    ## 856               0.2509              2.0212                        1.8606
    ## 857               0.6271             40.7354                        2.1125
    ## 858               9.6248            405.1922                       30.7431
    ## 859              21.6707           1096.9449                       63.5291
    ## 860                0.088              7.6911                        0.3396
    ## 861               0.0055              0.2165                        0.0055
    ## 862               0.1698             11.8612                        2.3672
    ## 863               0.0728             10.2985                        0.6416
    ## 864               0.1289              2.6473                        0.1292
    ## 865               0.0025              0.0876                        0.0025
    ## 866               2.4104             166.638                        9.9577
    ## 867               0.9383             31.5794                        4.2906
    ## 868               1.1746              38.865                        6.9603
    ## 869                5.552            310.7176                       23.6414
    ## 870               1.4198             54.3245                         5.767
    ## 871               0.7175             82.8778                       11.2372
    ## 872              13.4612           1737.2361                      158.1244
    ## 873               0.4172             30.2006                        8.3747
    ## 874               0.2192             15.8777                        0.9722
    ## 875                8.029             283.189                       26.8631
    ## 876               0.9844             44.5079                        4.9856
    ## 877               1.2611             42.4297                        3.5052
    ## 878               3.6427             278.948                        31.687
    ## 879               0.6423            278.4844                       42.0952
    ## 880              14.8399            489.4814                       26.1107
    ## 881             126.2235           5699.1766                      265.3198
    ## 882               7.4097             421.556                        32.067
    ## 883               1.7011             64.6072                       10.8072
    ## 884               0.0155             56.4416                        4.1125
    ## 885               2.1328            108.1557                       12.2197
    ## 886                0.374             46.7416                        3.5631
    ## 887               9.1423            570.1371                       53.2621
    ## 888               0.4816             21.0091                        3.2112
    ## 889               0.0564              7.4405                        0.6419
    ## 890               1.5135            113.3283                       12.0258
    ## 891               0.8748             50.1955                        1.7037
    ## 892               0.1544              17.768                        0.4939
    ## 893              78.6873           3047.5273                      260.5809
    ## 894              89.5865           3763.4016                      334.6486
    ## 895               1.1998             60.5501                        5.7725
    ## 896              16.2194             377.358                       37.8037
    ## 897              12.4424            789.1788                       68.6763
    ## 898               3.6199             92.2931                       10.4962
    ## 899               1.1949             49.0359                        6.4318
    ## 900               0.2731              1.8692                        1.8898
    ## 901               0.6308             40.5305                        1.9299
    ## 902              10.4487            415.2993                       31.8298
    ## 903              23.5784           1144.9623                       65.8493
    ## 904               0.0854              8.4871                        0.6053
    ## 905               0.0067              0.2019                        0.0067
    ## 906                0.196             12.7578                         2.228
    ## 907               0.0741             10.8394                        0.6602
    ## 908                 0.13              2.6596                        0.1302
    ## 909               0.0023              0.0844                        0.0023
    ## 910               2.6528             177.856                       10.4093
    ## 911                1.139             31.3175                        4.7642
    ## 912               1.1949             40.7224                        7.7395
    ## 913               5.7875            330.2754                       25.9505
    ## 914               1.5586             49.6674                        6.0648
    ## 915               0.7081              79.624                       12.3959
    ## 916               14.205           1824.3168                      172.7036
    ## 917               0.4612             31.7897                        8.6212
    ## 918               0.2376             15.9663                          0.98
    ## 919               8.9766            266.2578                       28.2708
    ## 920                1.076             48.8044                        6.8103
    ## 921               1.2856             43.9081                        3.7235
    ## 922               4.8851            285.0656                       53.9441
    ## 923               0.6912            290.8575                       46.4806
    ## 924              15.2985            505.4481                       27.6477
    ## 925             137.2917           5889.1178                      303.4397
    ## 926                 8.05            422.0395                       33.3128
    ## 927               1.7306              61.985                       11.2469
    ## 928               0.0024              53.158                        4.1486
    ## 929               2.2913             97.6983                       11.2831
    ## 930               0.4107             52.2037                        3.9779
    ## 931                9.393            571.6014                       54.2713
    ## 932               0.4858             20.7154                        3.0001
    ## 933               0.1266               7.137                         0.697
    ## 934               1.1944            109.5146                       11.7906
    ## 935               0.8619             44.9723                        1.8727
    ## 936               0.1612             18.6616                        0.6138
    ## 937              80.2789           2897.7285                      253.2341
    ## 938              91.3058           3614.0112                      331.6847
    ## 939               1.0631             53.3849                        5.5859
    ## 940              16.8263            349.4246                       36.4481
    ## 941               12.722            760.5722                       69.3261
    ## 942               3.5903             92.1652                        8.8938
    ## 943               1.1737             47.3641                         6.194
    ## 944               0.1877              1.7698                        1.7984
    ## 945               0.6001             36.9389                        1.7674
    ## 946               11.112            404.4435                       31.6409
    ## 947              25.1212           1194.4799                       67.1637
    ## 948               0.0954               7.857                        0.7277
    ## 949               0.0088              0.1871                        0.0088
    ## 950               0.2248             11.8205                         3.735
    ## 951               0.0749             10.6887                        0.6715
    ## 952               0.1403              2.6817                        0.1406
    ## 953               0.0029              0.0813                        0.0029
    ## 954               2.4623            163.8721                       10.4449
    ## 955               1.9329             31.0033                         5.431
    ## 956               1.2367             39.8308                        7.6471
    ## 957               6.3016            325.2059                       28.7199
    ## 958               1.5344             48.6105                        5.3239
    ## 959               0.4587             86.3205                       12.5915
    ## 960              12.1957           1920.4015                      174.9605
    ## 961               0.4772             31.5334                        8.2482
    ## 962               0.2623             15.9827                        1.0144
    ## 963               8.9872            271.7272                       26.1277
    ## 964               1.0568             45.0147                        6.6606
    ## 965               1.3475             39.8636                        3.7419
    ## 966               6.2585            301.2503                       56.2058
    ## 967               0.7262            305.2254                       48.7837
    ## 968              15.5867            465.9506                         26.47
    ## 969             145.3488            5745.698                      326.4613
    ##                                         X.7                  X.8            X.9
    ## 1    Solvent and Other Product Use (MtCO2e) Agriculture (MtCO2e) Waste (MtCO2e)
    ## 2                                                        86.5067       106.3035
    ## 3                                    0.5118               8.5567        -9.9265
    ## 4                                    0.0744              30.6446       -28.5744
    ## 5                                    0.2134              11.3167        -0.9137
    ## 6                                    0.8978              18.1983       -14.0488
    ## 7                                    0.1787              46.7285       -61.6281
    ## 8                                     0.117               4.3807        -6.4112
    ## 9                                                         0.6789        -0.1389
    ## 10                                   0.7648              16.2333        -3.6179
    ## 11                                   0.1164              12.5856         5.4732
    ## 12                                   0.0264               3.1668        -8.8487
    ## 13                                  13.2122             433.8681      -136.8018
    ## 14                                  16.7384              599.627      -254.8839
    ## 15                                   0.1784               6.6595        -15.162
    ## 16                                   2.0711             100.0828       -22.7942
    ## 17                                   4.5386              87.9626        -35.758
    ## 18                                   0.3083              11.4601        -2.4967
    ## 19                                   0.2262              15.4775        -2.0189
    ## 20                                   0.0091               0.7065         1.1714
    ## 21                                     0.08               19.634        -2.6621
    ## 22                                   2.4546              40.7386       -12.1537
    ## 23                                   0.2871              31.0903       -69.5323
    ## 24                                   0.0507                6.002       -22.3061
    ## 25                                    0.002                0.023        -0.0095
    ## 26                                   0.1975              10.2921        -4.2866
    ## 27                                   0.0239               0.7432         0.3477
    ## 28                                   0.0025               0.0878        -0.0565
    ## 29                                        0                                   0
    ## 30                                   0.5412              22.5574         2.9997
    ## 31                                   0.0415              30.6619       -28.1127
    ## 32                                   0.1912               5.0126       -15.3476
    ## 33                                   0.6292              49.6553       -16.3292
    ## 34                                   0.3296               8.1595         8.4962
    ## 35                                   0.5405              36.7083       -27.3554
    ## 36                                   0.5616             318.1178        84.5145
    ## 37                                   0.1472               7.1243       -10.0191
    ## 38                                   0.0434               2.1341         -9.056
    ## 39                                   1.5158              37.2095       -19.1057
    ## 40                                   0.3325               8.9972       -37.1845
    ## 41                                   0.4701               6.0921        -3.1556
    ## 42                                                       30.3877       -15.3809
    ## 43                                   0.3768             103.6025       -69.7371
    ## 44                                                       58.1526         4.0222
    ## 45                                    4.404             413.8612      -780.8465
    ## 46                                                       87.0464       153.3601
    ## 47                                    0.466               8.7463       -15.6442
    ## 48                                   0.0724              29.7911       -30.5872
    ## 49                                   0.2103              11.1816        -0.6361
    ## 50                                   0.8957              15.8927       -13.9317
    ## 51                                   0.1699              46.3789       -35.9296
    ## 52                                   0.1204               4.2259        -8.0844
    ## 53                                                        0.6799         -0.157
    ## 54                                   0.7281              14.6117        -9.0373
    ## 55                                   0.1327              12.4251         3.9957
    ## 56                                   0.0281               3.0079        -8.8512
    ## 57                                  12.8604             423.5542      -168.9783
    ## 58                                   16.154             565.5151      -296.6861
    ## 59                                   0.1705               6.2692       -28.8857
    ## 60                                   1.9883              97.6422       -19.1088
    ## 61                                   4.3986              79.7692       -35.8492
    ## 62                                   0.3155              11.3001        -2.5951
    ## 63                                   0.1766              12.8637        -2.4639
    ## 64                                   0.0086               0.6822          1.172
    ## 65                                   0.0818              19.7573        -2.7265
    ## 66                                    2.394              41.5219       -25.9147
    ## 67                                   0.3568              31.0201       -76.7068
    ## 68                                   0.0465               5.6288       -23.0386
    ## 69                                   0.0019               0.0231        -0.0095
    ## 70                                   0.1958               9.4647        -4.2044
    ## 71                                    0.023               0.7515         0.1724
    ## 72                                   0.0025               0.0855        -0.0565
    ## 73                                        0                                   0
    ## 74                                   0.4678               22.999         2.6395
    ## 75                                   0.0428              31.0132       -29.2489
    ## 76                                   0.1719               5.0168       -16.4567
    ## 77                                   0.6082              42.0407       -17.8134
    ## 78                                   0.3137               8.2612         8.4748
    ## 79                                   0.4482              29.6016       -27.9794
    ## 80                                   0.5289             304.2594        88.0233
    ## 81                                   0.1266               6.0817       -11.1425
    ## 82                                   0.0372               2.0019        -9.0318
    ## 83                                   1.5814              37.1986       -18.9172
    ## 84                                   0.3202                8.751       -38.1323
    ## 85                                   0.4439               6.0695        -3.2866
    ## 86                                                       30.9675       -17.0606
    ## 87                                   0.3776              98.7499       -77.8188
    ## 88                                                       57.9181         4.1323
    ## 89                                   4.2817             422.9045      -786.0063
    ## 90                                                        85.033        86.2999
    ## 91                                   0.4176               8.2836       -10.8459
    ## 92                                   0.0704              27.1394       -28.7829
    ## 93                                   0.2093               11.103        -0.9295
    ## 94                                   0.8966              13.6721        -13.619
    ## 95                                   0.1418              47.6347       -84.2848
    ## 96                                   0.1016               3.6263        -8.5744
    ## 97                                                        0.7417        -0.1603
    ## 98                                    0.691              12.7313       -10.7869
    ## 99                                   0.1426              12.2002         6.2353
    ## 100                                  0.0217               2.5845         -9.289
    ## 101                                 12.6113             418.0275      -160.7492
    ## 102                                 15.5949              540.949      -285.9583
    ## 103                                  0.1576               5.8627       -23.4256
    ## 104                                  1.9396              98.0558       -23.0557
    ## 105                                  4.2189              77.0189       -35.6713
    ## 106                                  0.3144              11.0638        -2.8587
    ## 107                                  0.1997              11.0275        -3.2947
    ## 108                                   0.008               0.6509         1.1567
    ## 109                                  0.0823              19.8622        -2.3826
    ## 110                                  2.3937              41.0019       -24.5186
    ## 111                                   0.413              30.9801       -76.4166
    ## 112                                  0.0442               4.4234       -23.1164
    ## 113                                  0.0018               0.0226        -0.0095
    ## 114                                  0.1939               6.6519         -4.167
    ## 115                                  0.0219               0.7461        -0.1958
    ## 116                                  0.0025                0.087        -0.0565
    ## 117                                       0                                   0
    ## 118                                  0.4455              22.9376         2.9196
    ## 119                                  0.0431               30.502       -27.9771
    ## 120                                   0.176                5.032       -16.4202
    ## 121                                  0.5586              38.4996        -8.1885
    ## 122                                  0.3242               8.1329         4.2951
    ## 123                                  0.2376              25.2518       -30.6652
    ## 124                                  0.5214             280.1868       -14.0925
    ## 125                                    0.11               5.0721        -12.836
    ## 126                                  0.0279               2.1787        -9.0297
    ## 127                                   1.621              36.2353        -17.748
    ## 128                                  0.3263               8.7154       -35.9432
    ## 129                                  0.4199               5.9788        -3.0229
    ## 130                                                      30.9438        -8.1358
    ## 131                                   0.379              90.4228        -65.091
    ## 132                                                      57.7271         3.3544
    ## 133                                   4.037             430.3249      -769.8353
    ## 134                                                      83.7967        17.4406
    ## 135                                  0.4185               8.0498        -11.282
    ## 136                                  0.0664              25.7929       -22.4877
    ## 137                                  0.2072              11.2032        -0.8544
    ## 138                                  0.8296              11.4681       -12.8528
    ## 139                                  0.1594              49.0632       -10.8773
    ## 140                                  0.1087               3.2985        -8.5607
    ## 141                                                       0.7644        -0.0951
    ## 142                                  0.6505              11.2049        -9.4329
    ## 143                                  0.1264              12.1067         2.7887
    ## 144                                  0.0208               1.9541        -9.8406
    ## 145                                 12.2338             410.1156      -154.6109
    ## 146                                 15.0522             522.5423      -279.3206
    ## 147                                  0.1504               5.9527        -21.278
    ## 148                                  1.8295               93.866       -29.5029
    ## 149                                  4.1361              76.4387       -35.7784
    ## 150                                  0.3129              10.1999        -3.2027
    ## 151                                  0.2038               9.8237        -5.0653
    ## 152                                   0.008                0.658         1.1435
    ## 153                                  0.0826               19.964        -2.7309
    ## 154                                  2.3507              41.2987        -11.223
    ## 155                                  0.4117               30.904       -78.7879
    ## 156                                  0.0413               2.9368       -21.8122
    ## 157                                  0.0017               0.0216        -0.0096
    ## 158                                  0.1915               5.5308        -5.5232
    ## 159                                  0.0208                0.733        -0.3058
    ## 160                                  0.0025               0.0875        -0.0565
    ## 161                                       0                                   0
    ## 162                                  0.4266               22.614         2.7257
    ## 163                                  0.0437              30.8443       -27.6828
    ## 164                                  0.1772               4.9566       -18.1908
    ## 165                                  0.5194              36.7047        -9.1268
    ## 166                                  0.2842               7.9624         2.8034
    ## 167                                  0.2375              25.5639       -29.9425
    ## 168                                  0.5106             260.1791      -101.9797
    ## 169                                  0.1016               4.3486       -11.9332
    ## 170                                  0.0197               2.0393        -9.0285
    ## 171                                  1.5763              34.6889       -16.9715
    ## 172                                  0.3151               8.8783       -32.1532
    ## 173                                  0.3917               5.8774        -4.2407
    ## 174                                                      31.1044       -19.1429
    ## 175                                   0.378               83.262       -49.4995
    ## 176                                                      57.0501         2.3267
    ## 177                                  4.5875             470.0097       -771.631
    ## 178                                                      83.1504        15.2262
    ## 179                                  0.4033               8.5556       -10.1493
    ## 180                                  0.0643               23.279       -31.7341
    ## 181                                  0.2045               11.206        -0.8771
    ## 182                                  0.1267               9.9971       -12.6618
    ## 183                                  0.1754               50.989       -17.2134
    ## 184                                  0.1105               3.2191        -8.4946
    ## 185                                                        0.758        -0.1137
    ## 186                                  0.6161              10.3725        -7.1411
    ## 187                                  0.1475              11.9973         4.3941
    ## 188                                   0.023               1.7024       -10.3451
    ## 189                                 11.6913             409.6544      -161.1134
    ## 190                                 13.7358             517.0328      -279.6334
    ## 191                                  0.1466               5.9852       -14.4008
    ## 192                                  1.8265              94.6357       -29.9578
    ## 193                                  3.6094              73.7356       -35.4468
    ## 194                                  0.3074              10.0155        -2.8426
    ## 195                                  0.1785               9.7113        -5.5138
    ## 196                                  0.0075                0.665         1.1304
    ## 197                                  0.0837              20.0973        -2.4162
    ## 198                                  2.2666              40.7963         -23.56
    ## 199                                   0.438              30.4906       -80.2674
    ## 200                                  0.0405               2.5313       -22.8839
    ## 201                                  0.0017               0.0217        -0.0096
    ## 202                                   0.189               4.8661        -4.3556
    ## 203                                  0.0196               0.7162         -0.136
    ## 204                                  0.0025               0.0868        -0.0565
    ## 205                                       0                                   0
    ## 206                                  0.4209              21.7472         2.6993
    ## 207                                  0.0443              31.8239       -26.3474
    ## 208                                  0.1903               4.9848       -17.1055
    ## 209                                  0.5211              36.9814        -6.6921
    ## 210                                  0.3133                 8.17         0.5784
    ## 211                                  0.2254              24.1308       -28.6551
    ## 212                                  0.5159             236.2126      -174.9767
    ## 213                                   0.103               4.1877       -11.0965
    ## 214                                  0.0188                2.053        -9.0047
    ## 215                                   1.653              36.6793       -19.0045
    ## 216                                  0.2929               8.9477        -32.156
    ## 217                                  0.3742                5.808        -3.1154
    ## 218                                                      29.7681       -20.1292
    ## 219                                  0.3752              74.4904       -62.1915
    ## 220                                                      57.2536         2.1283
    ## 221                                  4.5875             447.3861      -812.9273
    ## 222                                                      84.6435        23.7198
    ## 223                                  0.4225               8.7196       -11.4998
    ## 224                                  0.0623              21.3445       -31.2218
    ## 225                                  0.2002               11.391        -0.7178
    ## 226                                  0.0956                8.209       -13.1776
    ## 227                                  0.2126              52.6697        193.807
    ## 228                                  0.1083               3.0548        -9.0786
    ## 229                                                       0.7791        -0.1488
    ## 230                                  0.5963               10.332        -7.2101
    ## 231                                  0.1373              11.6331         3.6496
    ## 232                                   0.026               1.4837       -10.5965
    ## 233                                 11.7489             412.1561      -162.6235
    ## 234                                 13.7952             516.9752      -276.9638
    ## 235                                  0.1428               6.0682       -14.1381
    ## 236                                  1.8188              95.6557       -28.5025
    ## 237                                  3.6149               75.866       -35.3704
    ## 238                                  0.2998              10.3187        -3.1543
    ## 239                                  0.2051                9.296        -5.5752
    ## 240                                  0.0075               0.6372         1.1088
    ## 241                                  0.0854              20.3143        -1.8132
    ## 242                                  2.2349              40.5205       -30.3829
    ## 243                                  0.4376              29.8605       -80.5937
    ## 244                                  0.0415               2.3318       -21.6185
    ## 245                                  0.0016               0.0216        -0.0096
    ## 246                                  0.1864               4.6808        -3.3757
    ## 247                                  0.0197               0.7347        -0.2381
    ## 248                                  0.0025               0.0938        -0.0565
    ## 249                                       0                                   0
    ## 250                                  0.4399              22.2201         2.8509
    ## 251                                   0.045              32.2793       -24.3476
    ## 252                                  0.1867               5.0157       -19.7855
    ## 253                                  0.5248              37.0778        -5.6396
    ## 254                                  0.3101                8.181         4.2039
    ## 255                                  0.2294              24.1356       -27.1926
    ## 256                                  0.5117             212.8288      -219.3211
    ## 257                                  0.1215               4.3576       -10.7786
    ## 258                                  0.0173               2.0419        -8.9707
    ## 259                                   1.718              35.8372       -19.2566
    ## 260                                  0.3086               8.7216       -31.5761
    ## 261                                  0.3538               5.8193        -3.8914
    ## 262                                                      29.2342       -20.0735
    ## 263                                  0.3721              66.4691       -48.7571
    ## 264                                                      56.8676         3.2829
    ## 265                                  4.5875             459.5012      -782.3771
    ## 266                                                       85.918        30.3219
    ## 267                                  0.4057               8.2453         -8.394
    ## 268                                  0.0603              21.8951       -29.2884
    ## 269                                  0.1994              11.1651        -0.2592
    ## 270                                  0.0915               7.6861       -10.8091
    ## 271                                  0.2166              54.2288       -22.3407
    ## 272                                  0.1222               3.0381        -8.8239
    ## 273                                                       0.7995        -0.1518
    ## 274                                  0.5866               9.9663        -7.6206
    ## 275                                   0.148              11.0877         2.2561
    ## 276                                  0.0276               1.3753       -10.3965
    ## 277                                 11.7903             416.2845      -177.0906
    ## 278                                 13.8667             518.3815      -281.5923
    ## 279                                   0.138               5.9821       -23.5282
    ## 280                                  1.7905              96.5701       -29.8966
    ## 281                                  3.5332              76.0879       -35.4609
    ## 282                                  0.2982              10.4617        -2.7773
    ## 283                                  0.2313               9.4576        -1.6876
    ## 284                                  0.0082               0.6543         1.0965
    ## 285                                  0.0854                20.74        -1.6937
    ## 286                                  2.3209              40.3097       -30.3408
    ## 287                                  0.4209              29.2077       -85.1275
    ## 288                                  0.0436               2.2617       -22.0911
    ## 289                                  0.0015               0.0219        -0.0097
    ## 290                                  0.1838                5.046         1.8232
    ## 291                                  0.0194               0.7441        -0.4106
    ## 292                                  0.0025               0.0909        -0.0565
    ## 293                                       0                                   0
    ## 294                                   0.389              21.7758         2.6834
    ## 295                                  0.0459              32.7196       -23.5185
    ## 296                                  0.1956               5.0659       -19.3711
    ## 297                                    0.55               36.065        -6.7679
    ## 298                                  0.3314               8.4495         1.0342
    ## 299                                  0.2253              23.1532        -27.188
    ## 300                                  0.5106             194.7281      -291.9404
    ## 301                                  0.1155               4.2012       -10.6152
    ## 302                                  0.0187               1.9941        -8.9405
    ## 303                                  1.8234              39.7931       -19.9149
    ## 304                                  0.3118               8.6586       -33.0356
    ## 305                                  0.3308                 5.78        -4.8249
    ## 306                                                      29.6507       -20.0426
    ## 307                                  0.3686              56.3248       -55.0673
    ## 308                                                      57.1152         2.5882
    ## 309                                  4.5875             468.1382      -799.3838
    ## 310                                                      87.5277        19.7352
    ## 311                                  0.4244               8.2228       -17.0576
    ## 312                                  0.0583              22.2224       -26.4279
    ## 313                                  0.1988              11.1208        -0.7753
    ## 314                                  0.0794               7.5103       -10.8432
    ## 315                                  0.2301              54.0534       -61.8012
    ## 316                                  0.1132               3.2787        -8.2633
    ## 317                                                       0.7686        -0.1488
    ## 318                                  0.5848               9.7582        -6.6608
    ## 319                                  0.1351              10.9792         3.6243
    ## 320                                  0.0283               1.3728        -9.4679
    ## 321                                 11.8265              416.241      -179.1854
    ## 322                                  13.856             517.3861      -282.7548
    ## 323                                  0.1357               5.9886       -18.7717
    ## 324                                  1.7846              97.8314       -34.0483
    ## 325                                  3.5079              75.2199       -35.4271
    ## 326                                  0.3002              10.3167        -2.6363
    ## 327                                  0.2247                9.189        -1.9495
    ## 328                                  0.0083               0.6488          1.078
    ## 329                                  0.0859              20.8584        -2.4601
    ## 330                                  2.3314              41.3571        -21.828
    ## 331                                  0.4046               28.573       -85.4382
    ## 332                                  0.0445                 2.25       -20.2209
    ## 333                                  0.0014               0.0215        -0.0094
    ## 334                                  0.1812                5.221         0.2072
    ## 335                                   0.019               0.7317        -0.4511
    ## 336                                  0.0025               0.0928        -0.0565
    ## 337                                       0                                   0
    ## 338                                  0.3471              21.4102         2.9574
    ## 339                                  0.0462              33.4535        -24.196
    ## 340                                    0.19               5.0307       -18.9975
    ## 341                                  0.5486              36.9173        -6.4914
    ## 342                                   0.355               8.3532         2.1025
    ## 343                                   0.219              22.0271       -28.6307
    ## 344                                  0.5082             181.4267       -386.796
    ## 345                                  0.0976               4.0407       -10.3996
    ## 346                                  0.0189               1.9973        -8.9072
    ## 347                                  1.8844              38.7562       -21.4831
    ## 348                                  0.3209               8.7755       -35.4329
    ## 349                                   0.308               5.6057        -5.4533
    ## 350                                                      28.1736       -20.2097
    ## 351                                  0.3654              50.4565       -34.8203
    ## 352                                                       57.221         2.4469
    ## 353                                  4.8795             462.9234      -776.7399
    ## 354                                                      87.7378         53.716
    ## 355                                  0.4063               8.2261       -15.1618
    ## 356                                  0.0695               22.178       -24.4643
    ## 357                                  0.1977              11.1452         -0.668
    ## 358                                  0.0641                6.387       -10.7932
    ## 359                                  0.4014              54.6114       120.4563
    ## 360                                  0.1116               3.0057        -8.1654
    ## 361                                                       0.7659         0.0255
    ## 362                                  0.5804               9.2847         -6.998
    ## 363                                   0.144              11.2259         2.5239
    ## 364                                  0.0303               1.4227        -7.6021
    ## 365                                 11.8411             416.1916      -172.8896
    ## 366                                 13.8685             515.4708      -283.8039
    ## 367                                  0.1363                5.873       -16.6082
    ## 368                                  1.7925              97.7756       -34.4718
    ## 369                                  3.4824               75.243       -35.0945
    ## 370                                  0.3004              10.3305        -2.9021
    ## 371                                  0.2309               9.6579          -3.18
    ## 372                                  0.0086               0.6608         1.0571
    ## 373                                  0.0866              21.5128        -2.3084
    ## 374                                  2.3858              40.6104       -18.7669
    ## 375                                  0.3771              28.1369       -85.2267
    ## 376                                  0.0439               2.1312       -19.2044
    ## 377                                  0.0014               0.0213        -0.0091
    ## 378                                  0.1786               4.8486        -7.6592
    ## 379                                  0.0179                0.726        -0.1955
    ## 380                                  0.0025               0.0954        -0.0565
    ## 381                                       0                                   0
    ## 382                                  0.3507              20.4174          2.866
    ## 383                                  0.0465              32.5635       -25.2527
    ## 384                                  0.1904               5.0452       -19.8816
    ## 385                                  0.5524              37.6753        -7.2919
    ## 386                                  0.2894               8.3255         3.1699
    ## 387                                  0.2219              21.2411       -28.3037
    ## 388                                  0.5173             161.8337       -386.605
    ## 389                                  0.0945               3.7241       -10.9911
    ## 390                                   0.028               2.0454        -8.8597
    ## 391                                  1.9374              40.4452       -22.3374
    ## 392                                  0.3177               8.6485       -34.5288
    ## 393                                  0.2863               5.5779        -5.1872
    ## 394                                                      28.8617       -22.9003
    ## 395                                  0.3621              45.9364       -50.6168
    ## 396                                                      56.6118          1.537
    ## 397                                  4.8795              446.497       -714.609
    ## 398                                                      89.8948         6.6352
    ## 399                                  0.3923               8.1031       -18.0364
    ## 400                                  0.0874              21.1974       -31.3684
    ## 401                                  0.1965              11.2099        -0.7033
    ## 402                                  0.0566               6.7777        -10.766
    ## 403                                  0.4095              55.0201        17.7861
    ## 404                                  0.1062               3.2067        -8.5514
    ## 405                                                       0.7648        -0.1711
    ## 406                                  0.5785               9.3501         -7.155
    ## 407                                  0.1524              10.7853         4.1218
    ## 408                                    0.03               1.1909        -4.6338
    ## 409                                 11.5262             415.6036      -190.6492
    ## 410                                 13.5161             512.4538      -299.2085
    ## 411                                   0.135                 5.79       -19.7959
    ## 412                                    1.77              97.2989       -37.1683
    ## 413                                  3.2269              76.1697       -34.9992
    ## 414                                  0.3087              10.1776        -3.1379
    ## 415                                  0.2085               9.9271          -1.63
    ## 416                                  0.0083               0.6704         1.0375
    ## 417                                  0.0837              21.0181        -2.1518
    ## 418                                  2.3692              41.0004       -27.8283
    ## 419                                  0.3625              27.7285       -85.3742
    ## 420                                   0.045                1.944       -19.3479
    ## 421                                  0.0013               0.0206        -0.0089
    ## 422                                  0.1761               4.7049        -7.6999
    ## 423                                  0.0173               0.7358        -0.3188
    ## 424                                  0.0027               0.0913        -0.0559
    ## 425                                       0                                   0
    ## 426                                  0.3505              20.0061         2.9031
    ## 427                                  0.0468              32.9868       -24.9843
    ## 428                                  0.1883               5.0813       -14.8621
    ## 429                                  0.5472               36.228        -8.5092
    ## 430                                  0.2908               8.4812         2.1606
    ## 431                                  0.2224              20.3804       -28.6765
    ## 432                                  0.5155              149.326      -423.1039
    ## 433                                  0.0905                3.463       -11.0494
    ## 434                                  0.0324               2.0281        -8.8645
    ## 435                                  1.9383              41.3177       -22.7444
    ## 436                                  0.2989               8.4192       -34.0141
    ## 437                                  0.2731               5.5112        -3.5481
    ## 438                                                      29.1166       -23.2191
    ## 439                                  0.3586              41.4789       -63.9074
    ## 440                                                      56.0119         1.0039
    ## 441                                  4.8795             447.9466      -633.9848
    ## 442                                                       92.219        63.0793
    ## 443                                  0.4251               7.9098       -14.9358
    ## 444                                   0.076              20.8447       -30.9028
    ## 445                                  0.2135              10.5291        -0.6818
    ## 446                                  0.0684               6.2373        -8.9182
    ## 447                                  0.4496              55.6504       -52.1929
    ## 448                                  0.1092               3.1302        -7.7192
    ## 449                                                       0.7436        -0.1503
    ## 450                                  0.5686               9.0949        -7.5242
    ## 451                                  0.1538              10.5126         3.2183
    ## 452                                  0.0268               1.2037         1.0997
    ## 453                                 11.2541             413.4464      -177.4054
    ## 454                                 13.3328             505.3181      -280.2527
    ## 455                                  0.1247                5.886       -20.4515
    ## 456                                  1.8357              99.8359       -26.4309
    ## 457                                  2.9712               76.021       -34.8023
    ## 458                                  0.3066               9.9399        -2.7159
    ## 459                                  0.2136               9.5338        -0.6827
    ## 460                                  0.0083               0.6529          1.015
    ## 461                                   0.079              19.9695        -1.2537
    ## 462                                  2.3014              40.1354       -25.8346
    ## 463                                   0.341              27.4649       -85.9779
    ## 464                                  0.0448               1.9508       -19.2434
    ## 465                                  0.0012               0.0201        -0.0086
    ## 466                                  0.1735               4.4573          -9.24
    ## 467                                  0.0158               0.7213        -0.3854
    ## 468                                   0.003               0.1029        -0.0559
    ## 469                                       0                                   0
    ## 470                                  0.3069              18.8493         2.9253
    ## 471                                  0.0471              34.0584       -23.8952
    ## 472                                  0.1817               4.9751       -14.9957
    ## 473                                  0.6279              34.4628        -8.2975
    ## 474                                  0.2978               8.6934         2.2608
    ## 475                                  0.2243              18.4551       -29.2196
    ## 476                                  0.5229             152.9802      -457.9268
    ## 477                                   0.085                3.496       -10.7139
    ## 478                                  0.0427               2.1335        -9.9012
    ## 479                                  1.9492              42.9537       -23.2629
    ## 480                                  0.2775               8.3131       -35.5414
    ## 481                                  0.2586               5.4957        -1.2271
    ## 482                                                      27.8476          -45.5
    ## 483                                  0.3549              37.3725       -50.8401
    ## 484                                                       54.094         0.4246
    ## 485                                  4.8795             432.1768      -650.6839
    ## 486                                                      95.1323        -2.6951
    ## 487                                  0.4248               7.8631       -16.8242
    ## 488                                  0.0834              19.8176       -28.9512
    ## 489                                  0.2134              10.4087         -0.857
    ## 490                                  0.0548               5.9904        -8.7556
    ## 491                                  0.4195               54.865       -49.2141
    ## 492                                  0.1138               3.3219         -8.172
    ## 493                                                       0.8076        -0.1224
    ## 494                                    0.55               9.2209        -7.8779
    ## 495                                   0.141              10.4196         4.5526
    ## 496                                  0.0245               1.1888         4.5762
    ## 497                                 10.8395             404.1478      -204.8636
    ## 498                                  12.919             496.7634      -311.5996
    ## 499                                   0.122               5.8129       -23.7056
    ## 500                                  1.7808              97.4013       -32.1509
    ## 501                                  2.7486              75.3034       -40.7459
    ## 502                                  0.3043               9.8435        -2.6636
    ## 503                                  0.2579               9.7309         -2.191
    ## 504                                  0.0076               0.6508         1.0009
    ## 505                                  0.0779              19.5938        -1.3736
    ## 506                                   2.214              39.2022       -33.2763
    ## 507                                  0.3436              27.1978       -86.0777
    ## 508                                  0.0509               2.0959        -18.867
    ## 509                                  0.0012               0.0213        -0.0083
    ## 510                                  0.1709               4.5991       -12.7139
    ## 511                                  0.0165               0.6944        -0.4516
    ## 512                                  0.0023               0.0988        -0.0559
    ## 513                                       0                                   0
    ## 514                                  0.2685              18.4953          2.588
    ## 515                                  0.0474              34.4456       -22.7068
    ## 516                                  0.1844               4.8742       -18.6362
    ## 517                                  0.6318              34.1392       -11.3368
    ## 518                                  0.2995               8.4192        -1.0353
    ## 519                                  0.2005              19.0968       -29.0165
    ## 520                                  0.5329             154.3182      -544.8537
    ## 521                                  0.0997               3.5416       -10.5077
    ## 522                                  0.0364               2.1056        -9.8676
    ## 523                                  1.9639              42.2204       -23.2326
    ## 524                                  0.2685               8.2601       -35.6694
    ## 525                                   0.245                5.561         0.2408
    ## 526                                                      26.4214       -47.9056
    ## 527                                  0.3515              37.8586       -39.8615
    ## 528                                                      51.1183         -0.084
    ## 529                                  4.8795             443.6511      -715.4262
    ## 530                                                      92.4138        96.5083
    ## 531                                  0.4271                7.761         -10.88
    ## 532                                  0.0807              19.1227       -25.6321
    ## 533                                  0.2129              10.1869        -1.3419
    ## 534                                  0.0574               6.1426        -9.1175
    ## 535                                  0.3855              54.2248        101.104
    ## 536                                  0.1386               3.2922         -8.368
    ## 537                                                       0.8559         -0.174
    ## 538                                  0.5396               8.9559        -7.6325
    ## 539                                  0.1654                10.34         6.0333
    ## 540                                  0.0248               1.1127         3.3416
    ## 541                                 10.4494             397.5795      -163.4494
    ## 542                                  12.521             490.7889      -256.7029
    ## 543                                  0.1111               5.8698       -24.2214
    ## 544                                  1.6789              96.8698       -38.0508
    ## 545                                  2.5461              72.7835         6.7226
    ## 546                                  0.3051               9.8138        -2.9663
    ## 547                                  0.1907               9.8751        -1.6834
    ## 548                                  0.0074               0.6293         0.9841
    ## 549                                  0.0756              19.3775        -1.3996
    ## 550                                  2.2154              38.5012       -38.3864
    ## 551                                  0.3341              26.9562       -87.1637
    ## 552                                  0.0365               2.0595       -17.4953
    ## 553                                  0.0011               0.0215         -0.008
    ## 554                                  0.1682               4.8629        -5.3433
    ## 555                                  0.0168               0.6874        -0.4513
    ## 556                                  0.0026               0.0979        -0.0559
    ## 557                                       0                                   0
    ## 558                                  0.2486              17.4611         2.5567
    ## 559                                  0.0561               34.742       -19.4307
    ## 560                                  0.1872               4.8688       -21.1879
    ## 561                                   0.661              34.0372       -12.1058
    ## 562                                  0.2893               8.3548        -1.0846
    ## 563                                  0.2223              19.5522       -22.3685
    ## 564                                  0.5315             153.5077      -576.0731
    ## 565                                  0.1319               3.4822       -10.7652
    ## 566                                  0.0365               2.1751        -9.8536
    ## 567                                   1.886               41.119       -23.3941
    ## 568                                  0.2756               8.1708       -35.6703
    ## 569                                  0.2333               5.5358         -0.308
    ## 570                                                      24.9448       -44.7744
    ## 571                                  0.3482              38.1062       -39.8766
    ## 572                                                      51.1679        -0.9861
    ## 573                                  4.3871             447.8782       -830.236
    ## 574                                                      89.8145       235.9904
    ## 575                                  0.4184               7.5549        -0.8337
    ## 576                                  0.0793              19.5033       -22.2766
    ## 577                                  0.2127               9.7117        -1.3934
    ## 578                                  0.0604               5.9678        -9.0258
    ## 579                                  0.4455              56.5175        49.7096
    ## 580                                  0.1468               3.2017        -7.9344
    ## 581                                                       0.8281        -0.1628
    ## 582                                  0.5252               8.3149        -5.7427
    ## 583                                  0.1601               9.8782         4.7693
    ## 584                                  0.0247               1.1636         0.6575
    ## 585                                  9.9533             391.8508      -138.9793
    ## 586                                  12.117             483.8854      -233.9846
    ## 587                                  0.1045               5.8802       -24.7365
    ## 588                                  1.5735              93.1138       -39.9013
    ## 589                                  2.3289              71.2754         6.7777
    ## 590                                  0.3059               9.7503        -2.6395
    ## 591                                  0.2605               9.6114        -3.8426
    ## 592                                  0.0072               0.6172          0.962
    ## 593                                  0.0744              19.5093        -1.4817
    ## 594                                  2.1631                38.34       -30.7718
    ## 595                                  0.3208              26.7284       -96.2764
    ## 596                                  0.0294               2.1126       -18.1111
    ## 597                                  0.0011               0.0216        -0.0079
    ## 598                                  0.1656               4.9875        -9.7557
    ## 599                                  0.0151               0.6477        -0.4597
    ## 600                                  0.0024               0.0911         -0.057
    ## 601                                       0                                   0
    ## 602                                   0.227              17.0984         2.9101
    ## 603                                  0.0524              35.5035       -20.9603
    ## 604                                  0.1906               4.9384        -23.223
    ## 605                                   0.645                33.44       -12.6081
    ## 606                                  0.2879               7.6769         5.1211
    ## 607                                  0.2799              20.0732       -16.3977
    ## 608                                  0.5326             149.5305      -560.6789
    ## 609                                  0.1373               3.3626       -10.2373
    ## 610                                  0.0333               2.0817        -9.7219
    ## 611                                   1.794              43.3926       -22.5474
    ## 612                                  0.2924               8.0603       -32.5871
    ## 613                                  0.2245               5.4609        -2.9847
    ## 614                                                      25.7919       -48.8246
    ## 615                                  0.3455              34.9106       -59.1087
    ## 616                                                      50.8059        -1.2768
    ## 617                                  4.3871             442.1081      -935.5214
    ## 618                                                      90.1689       -49.0305
    ## 619                                  0.3742               7.4516        -5.8921
    ## 620                                  0.0809              19.9714       -22.8886
    ## 621                                  0.2127               9.6624        -1.2788
    ## 622                                  0.0489               6.5278        -9.1918
    ## 623                                  0.4074              58.1409       107.0238
    ## 624                                  0.1755               3.4382        -8.0074
    ## 625                                                       0.8025        -0.1721
    ## 626                                  0.5193               8.7505         -6.183
    ## 627                                  0.1645              10.0082         4.4019
    ## 628                                  0.0251               1.1964        -2.3865
    ## 629                                     9.7             391.7806      -156.8578
    ## 630                                 11.9762             484.5012      -260.8617
    ## 631                                  0.1051               5.8177       -25.6123
    ## 632                                  1.5151              93.5283       -40.9542
    ## 633                                  2.2573              72.4145          7.232
    ## 634                                  0.3067               9.8338        -2.8391
    ## 635                                  0.3249                9.769        -2.8897
    ## 636                                  0.0072               0.6055         0.9378
    ## 637                                  0.0739              19.3134        -2.5275
    ## 638                                  2.1278              38.0343       -36.3629
    ## 639                                  0.2975              26.5421       -95.7798
    ## 640                                  0.0359               2.0761       -17.7524
    ## 641                                   0.001               0.0217        -0.0078
    ## 642                                  0.1626               4.9937        -6.5986
    ## 643                                  0.0174               0.6778        -0.4145
    ## 644                                  0.0024               0.0957        -0.0582
    ## 645                                  0.0001                                   0
    ## 646                                  0.2209              17.0781         2.8716
    ## 647                                  0.0484               35.547          -22.3
    ## 648                                  0.1943               4.8838       -26.7277
    ## 649                                  0.6771              33.2754       -16.3929
    ## 650                                  0.3131                7.964         0.5088
    ## 651                                  0.2774              20.0706       -22.9427
    ## 652                                  0.5348             147.3598      -541.8957
    ## 653                                  0.1635               3.1745        -9.6333
    ## 654                                  0.0392               1.9885        -9.8027
    ## 655                                  1.7047              41.8198       -24.2661
    ## 656                                   0.311               8.0945       -29.4083
    ## 657                                  0.2113               5.4474        -4.5718
    ## 658                                                      25.4431       -48.5893
    ## 659                                   0.343              34.4724       -40.4193
    ## 660                                                      50.9305        -2.3844
    ## 661                                  4.3871             453.3087      -982.7937
    ## 662                                                        89.08        23.0103
    ## 663                                  0.3866               7.4141        -7.2975
    ## 664                                  0.0692              20.6881         -26.21
    ## 665                                  0.2124               9.4496        -1.2936
    ## 666                                  0.0507               6.2068        -8.9344
    ## 667                                   0.378              58.1229        62.6855
    ## 668                                  0.1948               3.4777        -8.1514
    ## 669                                                       0.7381        -0.1742
    ## 670                                  0.5138                8.385        -6.6855
    ## 671                                  0.1896                9.894         4.6961
    ## 672                                  0.0262               1.1708        -5.0374
    ## 673                                  9.6665             385.1335      -159.1309
    ## 674                                 11.9929             478.0657      -273.4664
    ## 675                                  0.1064               5.8271       -29.9395
    ## 676                                  1.4799               92.802       -42.0399
    ## 677                                  2.1136              71.4234         7.3716
    ## 678                                  0.3093               9.5414        -2.7719
    ## 679                                  0.3663               9.1959         -5.135
    ## 680                                  0.0069               0.6083         0.9049
    ## 681                                  0.0741              18.8557        -2.5724
    ## 682                                  2.1229              37.3625       -38.2713
    ## 683                                  0.2664              26.3661       -88.8278
    ## 684                                  0.0357               2.1683       -17.9922
    ## 685                                   0.001               0.0221        -0.0077
    ## 686                                  0.1592               5.0628        -4.7456
    ## 687                                  0.0166               0.6578        -0.3857
    ## 688                                  0.0023               0.0936        -0.0571
    ## 689                                  0.0001                                   0
    ## 690                                   0.213              16.9514         3.0143
    ## 691                                  0.0443              35.9863       -21.6489
    ## 692                                   0.184               4.8782       -26.8058
    ## 693                                  0.6877               33.787       -21.6356
    ## 694                                  0.3199               7.7428         4.5214
    ## 695                                  0.2697              20.9496       -28.0629
    ## 696                                  0.5319             141.6809      -540.5325
    ## 697                                  0.1715                3.171        -6.1029
    ## 698                                  0.0433               2.0034        -9.7727
    ## 699                                  1.8243              39.5228        -24.545
    ## 700                                  0.3028               7.9545       -27.0906
    ## 701                                  0.2108               5.4742        -4.1972
    ## 702                                                      26.2801       -45.0082
    ## 703                                  0.3404              33.8091       -38.4401
    ## 704                                                      50.5468        -2.5928
    ## 705                                  4.3871              446.188      -972.4678
    ## 706                                                      89.8218        -8.1833
    ## 707                                   0.415               7.4501         -1.485
    ## 708                                  0.0675              21.4806       -28.4206
    ## 709                                   0.212               9.3252        -1.2551
    ## 710                                  0.0537                6.098        -8.3982
    ## 711                                  0.3294              57.3456        72.7258
    ## 712                                  0.2242               3.4978        -8.0746
    ## 713                                                       0.7121        -0.1664
    ## 714                                  0.5129               8.2498        -3.4647
    ## 715                                  0.1711               9.7007         5.6629
    ## 716                                  0.0263               1.1664        -6.9896
    ## 717                                  9.7328             380.0993      -179.7028
    ## 718                                 12.0301             474.2256      -297.5345
    ## 719                                  0.1002               5.8273       -33.9268
    ## 720                                  1.4193              91.3507       -46.5736
    ## 721                                   2.136              69.8963         7.0506
    ## 722                                  0.3119               9.3748        -2.8319
    ## 723                                  0.3347               9.2101        -3.1807
    ## 724                                  0.0073               0.6387         0.8885
    ## 725                                  0.0751              18.7218        -2.7045
    ## 726                                  2.1257              36.7671       -39.1673
    ## 727                                  0.2423              26.3163       -83.1139
    ## 728                                  0.0552               2.1629       -19.8179
    ## 729                                   0.001                0.023        -0.0076
    ## 730                                  0.1277               5.0863        -4.7129
    ## 731                                  0.0163               0.6495        -0.2756
    ## 732                                   0.002               0.0934        -0.0589
    ## 733                                       0                                   0
    ## 734                                  0.2122              16.9116          3.017
    ## 735                                  0.0403              35.9162       -19.6796
    ## 736                                   0.174               4.7853       -21.6898
    ## 737                                  0.7615              35.3499       -25.0358
    ## 738                                  0.2841               7.5988        -2.5623
    ## 739                                  0.2085              20.8622       -27.8628
    ## 740                                   0.532             140.5745      -520.3016
    ## 741                                  0.1706               3.1153        -8.4584
    ## 742                                  0.0442                 2.02        -9.6855
    ## 743                                  1.9597              40.3064       -27.4231
    ## 744                                   0.299               7.9316       -34.3371
    ## 745                                  0.2052               5.4941        -2.8921
    ## 746                                                      26.9515        -48.605
    ## 747                                  0.3385              33.6624       -41.4192
    ## 748                                                      49.1015        -2.9811
    ## 749                                  4.3871             454.6201      -919.0225
    ## 750                                                      86.7142       108.0217
    ## 751                                  0.3883               7.5165        -0.4213
    ## 752                                  0.0726              21.2097       -27.5595
    ## 753                                  0.2121               9.3968        -1.2329
    ## 754                                  0.0501               6.0149        -7.0863
    ## 755                                  0.3263              57.6418        51.6886
    ## 756                                  0.2468               3.4459        -7.7243
    ## 757                                                       0.7172        -0.1063
    ## 758                                  0.5122                8.403        -0.7268
    ## 759                                  0.1738                9.929          2.571
    ## 760                                  0.0244               1.2093        -8.1122
    ## 761                                  9.3365             379.7812      -153.0741
    ## 762                                 11.5407             474.8653      -259.7242
    ## 763                                  0.0971               5.8273       -25.7125
    ## 764                                  1.2988              91.9723       -47.2527
    ## 765                                  2.0109              68.7524         7.5459
    ## 766                                  0.3134                 9.59        -1.7554
    ## 767                                  0.3661               9.2366        -3.5845
    ## 768                                  0.0078               0.6597         0.8715
    ## 769                                  0.0757              18.2824        -3.3648
    ## 770                                   2.075              37.3798       -17.6017
    ## 771                                    0.16              26.0062       -82.2967
    ## 772                                  0.0633               2.2544       -18.5959
    ## 773                                   0.001               0.0233        -0.0075
    ## 774                                  0.1176               5.4399        -3.5048
    ## 775                                  0.0175               0.6536        -0.2732
    ## 776                                  0.0027               0.0952        -0.0589
    ## 777                                  0.0001                                   0
    ## 778                                  0.2085              16.7302         2.8653
    ## 779                                  0.0434              34.4466       -17.9363
    ## 780                                  0.1751                4.803       -21.6868
    ## 781                                  0.7216              36.1696       -21.8333
    ## 782                                  0.3005               7.7584        -4.2884
    ## 783                                  0.1378              20.2369       -25.2189
    ## 784                                  0.5414             143.2336      -550.1801
    ## 785                                  0.1662               3.2312        -8.0974
    ## 786                                  0.0422               2.0759        -9.7248
    ## 787                                  1.8882              41.1988       -29.6511
    ## 788                                  0.2814               7.8559       -31.2555
    ## 789                                  0.2043               5.5557        -2.7836
    ## 790                                                      26.7584       -34.4342
    ## 791                                  0.3364              33.0764       -53.9191
    ## 792                                                      47.7706         -3.332
    ## 793                                  4.3871             470.9008      -891.9508
    ## 794                                                      86.6764       -29.7571
    ## 795                                  0.3672                7.654         0.4813
    ## 796                                  0.0641              22.2702       -27.1385
    ## 797                                   0.212                9.259        -1.2247
    ## 798                                  0.0511               6.1869        -8.2811
    ## 799                                  0.3416              58.6026       -11.0622
    ## 800                                  0.2393               3.4309        -7.8235
    ## 801                                                       0.7078        -0.1728
    ## 802                                  0.5153               8.5831        -4.7729
    ## 803                                  0.1574               9.9853        -1.2982
    ## 804                                   0.022               1.3299        -8.1253
    ## 805                                  8.7902             379.0233      -182.9781
    ## 806                                  11.048             474.3189      -302.8447
    ## 807                                  0.0866               5.9169       -29.6352
    ## 808                                  1.1906              94.6029       -47.6848
    ## 809                                  1.8742              71.6236         7.7593
    ## 810                                  0.3141               9.2111        -2.8685
    ## 811                                  0.4063               9.1134        -4.8245
    ## 812                                  0.0072               0.6763         0.8589
    ## 813                                  0.0743               18.145        -2.7077
    ## 814                                  1.9537              36.0154       -36.6703
    ## 815                                  0.1291              25.8148       -78.1253
    ## 816                                  0.0436               2.2187       -19.6606
    ## 817                                   0.001               0.0234        -0.0074
    ## 818                                  0.0909               5.0571        -8.4355
    ## 819                                  0.0169               0.6613        -0.2723
    ## 820                                  0.0021               0.0865        -0.0589
    ## 821                                  0.0001                                   0
    ## 822                                  0.2066              16.7696         3.0258
    ## 823                                   0.031              33.3322       -23.5641
    ## 824                                  0.1703               4.7552       -24.4938
    ## 825                                  0.7972              36.1663       -24.3014
    ## 826                                  0.2638               7.6171         -6.261
    ## 827                                  0.1351              20.7535        -24.312
    ## 828                                  0.5437             148.0253      -578.4613
    ## 829                                  0.1666               3.1295        -7.2186
    ## 830                                  0.0276                1.963         -9.703
    ## 831                                  1.7898              37.4914       -29.0871
    ## 832                                  0.2878               7.9149       -32.8263
    ## 833                                   0.201               5.6485        -1.6159
    ## 834                                                       25.473       -39.4155
    ## 835                                  0.3347              35.1765       -10.4173
    ## 836                                                      46.9929        -3.7881
    ## 837                                  4.3871             463.5838      -875.4101
    ## 838                                                      83.8601        40.2796
    ## 839                                  0.2992               7.6341          -3.54
    ## 840                                  0.0641              22.7807        -29.928
    ## 841                                  0.2116               9.3594        -1.3209
    ## 842                                  0.0478               5.9862        -8.3886
    ## 843                                  0.2605              56.1347        -9.8423
    ## 844                                  0.1529               3.3141        -8.0656
    ## 845                                                       0.6982        -0.1745
    ## 846                                  0.5061               8.1343        -6.8631
    ## 847                                  0.1702               9.6392          2.932
    ## 848                                  0.0185               1.2306        -7.3421
    ## 849                                   8.098             370.3868      -185.7004
    ## 850                                 10.2032             462.9672      -313.4769
    ## 851                                  0.0723               5.7636       -39.2738
    ## 852                                  1.0551              91.1691       -38.6676
    ## 853                                  1.6879              69.6179           8.51
    ## 854                                  0.3156               8.9277        -2.6136
    ## 855                                  0.3401               8.5775        -3.9898
    ## 856                                  0.0063               0.6514         0.8346
    ## 857                                  0.0719              17.9305        -3.0034
    ## 858                                  1.8293              34.7769         -39.92
    ## 859                                  0.1205              25.5504       -74.0885
    ## 860                                  0.0265               2.2508       -19.8648
    ## 861                                   0.001               0.0232        -0.0072
    ## 862                                  0.0954                5.009       -10.6298
    ## 863                                  0.0161               0.6706        -0.2964
    ## 864                                  0.0016               0.0833        -0.0589
    ## 865                                  0.0001                                   0
    ## 866                                  0.1978              16.7116         2.8429
    ## 867                                  0.0279              33.5004       -21.8159
    ## 868                                  0.1506               4.5458        -22.219
    ## 869                                  0.7514              35.2096       -25.0999
    ## 870                                  0.2699               7.5131        -6.2266
    ## 871                                  0.1223              20.3538       -28.2546
    ## 872                                  0.5576             147.3247      -646.6061
    ## 873                                  0.1644               3.0524        -7.4375
    ## 874                                   0.031               1.9947        -9.6728
    ## 875                                  1.6363              37.5468        -28.508
    ## 876                                    0.27               7.6828       -32.8914
    ## 877                                  0.2001               5.5935        -2.0931
    ## 878                                                      26.1041       -38.9586
    ## 879                                  0.3334              33.4849       -18.2678
    ## 880                                                      46.2455        -3.8159
    ## 881                                  4.3871             459.1906      -862.1815
    ## 882                                                      81.6325        39.0533
    ## 883                                  0.3271               7.4668        -3.5177
    ## 884                                  0.1224              22.5866       -30.1792
    ## 885                                  0.2112               9.4272        -1.3572
    ## 886                                  0.0458               6.1856         -8.109
    ## 887                                   0.242              55.6128        103.195
    ## 888                                  0.1525               3.1931        -7.8717
    ## 889                                                       0.7221        -0.1655
    ## 890                                  0.4921               7.9646        -5.4885
    ## 891                                  0.1877                9.655        -0.4729
    ## 892                                  0.0174               1.2566        -5.9416
    ## 893                                  8.2054             369.4908      -169.8467
    ## 894                                 10.2623             459.9101      -287.9239
    ## 895                                  0.0736                5.955       -24.6237
    ## 896                                  1.0989              90.3384       -34.5813
    ## 897                                  1.9445              68.3647         8.7207
    ## 898                                  0.3162               9.2707        -2.6002
    ## 899                                  0.2689               8.5313        -4.0847
    ## 900                                  0.0061               0.6428         0.7958
    ## 901                                  0.0717              17.9948        -4.1123
    ## 902                                  1.6767              33.7226       -43.3409
    ## 903                                   0.099              25.5175       -75.7716
    ## 904                                  0.0452               2.3217       -16.4108
    ## 905                                   0.001               0.0227        -0.0071
    ## 906                                  0.0874               4.9847       -10.3975
    ## 907                                  0.0143               0.6779        -0.2953
    ## 908                                  0.0013                0.078        -0.0597
    ## 909                                       0                                   0
    ## 910                                  0.1812              16.6382         2.9926
    ## 911                                   0.031              33.7223       -17.8144
    ## 912                                  0.1709               4.4565        -23.578
    ## 913                                  0.7794              34.5606       -25.0222
    ## 914                                  0.2258               7.5174        -3.4853
    ## 915                                  0.1247              18.7609       -25.8308
    ## 916                                  0.5649             141.8535      -650.6128
    ## 917                                  0.1643               3.0983        -6.9151
    ## 918                                  0.0304               1.9549        -9.6517
    ## 919                                  1.5927               38.744       -28.8955
    ## 920                                  0.2889               7.7856       -30.7006
    ## 921                                  0.1976               5.6472        -2.4047
    ## 922                                                      27.1268       -40.6032
    ## 923                                   0.332              34.5074       -37.9551
    ## 924                                                      46.7254        -3.6654
    ## 925                                  4.3871               462.27      -869.0943
    ## 926                                                      84.1429       -40.3479
    ## 927                                  0.3242               7.5771        -3.4913
    ## 928                                  0.0616              23.4647       -29.2336
    ## 929                                  0.2111               9.3659        -1.2683
    ## 930                                  0.0413               6.1485        -7.9794
    ## 931                                  0.2474               53.925        87.2671
    ## 932                                  0.1442               3.3185        -7.0318
    ## 933                                                       0.7299        -0.0765
    ## 934                                  0.4694               8.0648        -7.9592
    ## 935                                  0.1672               9.7123         -2.664
    ## 936                                  0.0189               1.2705        -4.2628
    ## 937                                  7.9686             369.7847      -173.9925
    ## 938                                 10.0704              461.013      -290.0835
    ## 939                                  0.0698               5.8665       -24.5774
    ## 940                                  1.1252              91.5852       -44.6267
    ## 941                                  1.8559              70.3599         9.3346
    ## 942                                  0.3164               8.9658        -2.5396
    ## 943                                  0.3096               8.7587        -3.7875
    ## 944                                  0.0063               0.6407         0.7463
    ## 945                                  0.0725              17.6912        -3.7016
    ## 946                                  1.6563              33.5304       -30.5901
    ## 947                                  0.0971              25.4023       -75.4341
    ## 948                                  0.0413               2.3155       -17.1792
    ## 949                                   0.001               0.0234         -0.007
    ## 950                                  0.0859                 4.98       -10.4835
    ## 951                                  0.0158               0.6637        -0.2942
    ## 952                                  0.0013               0.0709        -0.0597
    ## 953                                       0                                   0
    ## 954                                  0.1545              16.0284         3.2659
    ## 955                                  0.0279              34.3873       -13.5402
    ## 956                                  0.1805               4.4845       -27.5729
    ## 957                                  0.7887              34.9298       -21.9123
    ## 958                                  0.2667               7.5049        -5.3198
    ## 959                                  0.1256              18.9415       -25.3049
    ## 960                                  0.5709             144.0438      -628.4349
    ## 961                                  0.1705               3.1175        -7.4673
    ## 962                                  0.0493               1.9007        -9.6187
    ## 963                                  1.4491              37.2791       -29.0712
    ## 964                                  0.2889               7.7721       -35.2317
    ## 965                                  0.1994               5.6035        -3.4109
    ## 966                                                      28.8331       -43.6403
    ## 967                                  0.3308              36.1903        -7.2898
    ## 968                                                      46.6746        -3.3094
    ## 969                                  4.3871             461.4969      -868.4164
    ##                                                       X.10
    ## 1   Land Use and Forestry (Net Forest Conversion) (MtCO2e)
    ## 2                                                  17.4111
    ## 3                                                   3.5873
    ## 4                                                   2.5747
    ## 5                                                   3.4129
    ## 6                                                    6.069
    ## 7                                                  19.0074
    ## 8                                                   0.5645
    ## 9                                                     0.47
    ## 10                                                  2.6732
    ## 11                                                  1.7331
    ## 12                                                  0.3437
    ## 13                                                172.0195
    ## 14                                                 203.562
    ## 15                                                  3.9746
    ## 16                                                 12.6871
    ## 17                                                 43.2302
    ## 18                                                  5.5744
    ## 19                                                  3.4515
    ## 20                                                  0.1447
    ## 21                                                  1.3833
    ## 22                                                  19.665
    ## 23                                                 25.9784
    ## 24                                                  0.5355
    ## 25                                                  0.0016
    ## 26                                                  1.1225
    ## 27                                                  0.0825
    ## 28                                                  0.0378
    ## 29                                                  0.0008
    ## 30                                                 12.7843
    ## 31                                                  2.0591
    ## 32                                                  1.8602
    ## 33                                                 10.6358
    ## 34                                                  5.9946
    ## 35                                                  4.5801
    ## 36                                                 61.1221
    ## 37                                                  1.0913
    ## 38                                                   0.532
    ## 39                                                  7.3228
    ## 40                                                  3.4213
    ## 41                                                   1.011
    ## 42                                                  9.7216
    ## 43                                                 10.5168
    ## 44                                                 47.4803
    ## 45                                                167.8324
    ## 46                                                 17.3762
    ## 47                                                  3.5719
    ## 48                                                  2.5725
    ## 49                                                   3.411
    ## 50                                                  5.4839
    ## 51                                                 19.3664
    ## 52                                                  0.5682
    ## 53                                                  0.4905
    ## 54                                                  2.7229
    ## 55                                                  1.7363
    ## 56                                                  0.3404
    ## 57                                                174.0119
    ## 58                                                205.3941
    ## 59                                                  4.0121
    ## 60                                                 13.1848
    ## 61                                                 43.7425
    ## 62                                                  5.5389
    ## 63                                                  3.5202
    ## 64                                                  0.1494
    ## 65                                                   1.466
    ## 66                                                 20.6943
    ## 67                                                 25.9172
    ## 68                                                   0.545
    ## 69                                                  0.0015
    ## 70                                                   1.144
    ## 71                                                  0.0842
    ## 72                                                  0.0399
    ## 73                                                   0.001
    ## 74                                                 12.9164
    ## 75                                                  2.0908
    ## 76                                                  1.8472
    ## 77                                                 10.9475
    ## 78                                                   6.193
    ## 79                                                  4.5109
    ## 80                                                 59.6547
    ## 81                                                  1.1059
    ## 82                                                  0.5313
    ## 83                                                  7.7056
    ## 84                                                  3.4666
    ## 85                                                  1.0075
    ## 86                                                 13.1334
    ## 87                                                 10.5177
    ## 88                                                 46.5967
    ## 89                                                169.2184
    ## 90                                                 17.2157
    ## 91                                                  3.4639
    ## 92                                                  2.5705
    ## 93                                                  3.4381
    ## 94                                                   5.111
    ## 95                                                 19.6235
    ## 96                                                  0.5771
    ## 97                                                  0.5124
    ## 98                                                  2.7335
    ## 99                                                   1.711
    ## 100                                                 0.3226
    ## 101                                               172.4913
    ## 102                                               203.5878
    ## 103                                                 4.0274
    ## 104                                                13.6958
    ## 105                                                43.5716
    ## 106                                                 5.6221
    ## 107                                                 3.5562
    ## 108                                                 0.1589
    ## 109                                                 1.5257
    ## 110                                                19.6714
    ## 111                                                27.0314
    ## 112                                                 0.5437
    ## 113                                                 0.0015
    ## 114                                                 1.1584
    ## 115                                                 0.0846
    ## 116                                                 0.0421
    ## 117                                                  0.001
    ## 118                                                12.6829
    ## 119                                                 2.1017
    ## 120                                                 1.8123
    ## 121                                                11.0251
    ## 122                                                 6.4084
    ## 123                                                 4.4579
    ## 124                                                56.3632
    ## 125                                                   1.11
    ## 126                                                 0.5238
    ## 127                                                 8.1209
    ## 128                                                 3.4667
    ## 129                                                   0.98
    ## 130                                                16.7413
    ## 131                                                  10.45
    ## 132                                                45.3042
    ## 133                                               170.4044
    ## 134                                                17.1165
    ## 135                                                 3.4149
    ## 136                                                 2.5683
    ## 137                                                  3.227
    ## 138                                                 5.0062
    ## 139                                                19.8831
    ## 140                                                 0.5863
    ## 141                                                 0.5334
    ## 142                                                 2.7499
    ## 143                                                   1.71
    ## 144                                                 0.2872
    ## 145                                               170.5518
    ## 146                                               201.7441
    ## 147                                                 4.0219
    ## 148                                                14.1792
    ## 149                                                 42.758
    ## 150                                                   5.65
    ## 151                                                  3.594
    ## 152                                                 0.1652
    ## 153                                                 1.5726
    ## 154                                                 19.538
    ## 155                                                26.6337
    ## 156                                                 0.5297
    ## 157                                                 0.0015
    ## 158                                                 1.1759
    ## 159                                                 0.0849
    ## 160                                                  0.046
    ## 161                                                 0.0011
    ## 162                                                12.3578
    ## 163                                                 2.1184
    ## 164                                                 1.8035
    ## 165                                                11.1356
    ## 166                                                 6.5677
    ## 167                                                 4.4777
    ## 168                                                53.9376
    ## 169                                                  1.119
    ## 170                                                 0.5375
    ## 171                                                 8.4902
    ## 172                                                 3.3581
    ## 173                                                 0.9182
    ## 174                                                19.4987
    ## 175                                                10.3388
    ## 176                                                43.9043
    ## 177                                               169.7476
    ## 178                                                16.5554
    ## 179                                                 3.2542
    ## 180                                                 2.0915
    ## 181                                                 3.2348
    ## 182                                                  4.963
    ## 183                                                20.0011
    ## 184                                                 0.5994
    ## 185                                                 0.5533
    ## 186                                                 2.8593
    ## 187                                                 1.6403
    ## 188                                                 0.2812
    ## 189                                               168.7227
    ## 190                                               200.1146
    ## 191                                                 3.9671
    ## 192                                                14.4531
    ## 193                                                41.4015
    ## 194                                                 5.7983
    ## 195                                                 3.6286
    ## 196                                                 0.1721
    ## 197                                                 1.6175
    ## 198                                                20.0884
    ## 199                                                29.1438
    ## 200                                                 0.5259
    ## 201                                                 0.0016
    ## 202                                                 1.1762
    ## 203                                                 0.0829
    ## 204                                                 0.0505
    ## 205                                                 0.0011
    ## 206                                                11.9107
    ## 207                                                 2.0268
    ## 208                                                 1.8006
    ## 209                                                11.1263
    ## 210                                                 6.8576
    ## 211                                                 4.5092
    ## 212                                                52.0285
    ## 213                                                  1.175
    ## 214                                                 0.5435
    ## 215                                                 8.7758
    ## 216                                                 3.2426
    ## 217                                                 0.8569
    ## 218                                                20.1288
    ## 219                                                10.0711
    ## 220                                                42.6653
    ## 221                                               168.7546
    ## 222                                                16.5498
    ## 223                                                 3.0965
    ## 224                                                 2.1376
    ## 225                                                 3.1322
    ## 226                                                 5.0828
    ## 227                                                19.9964
    ## 228                                                 0.6186
    ## 229                                                 0.5738
    ## 230                                                 2.9076
    ## 231                                                 1.5456
    ## 232                                                 0.2565
    ## 233                                                165.928
    ## 234                                                197.792
    ## 235                                                 3.9111
    ## 236                                                14.6063
    ## 237                                                39.9307
    ## 238                                                 5.7883
    ## 239                                                 3.6906
    ## 240                                                 0.1791
    ## 241                                                 1.6577
    ## 242                                                20.4454
    ## 243                                                29.3152
    ## 244                                                 0.5259
    ## 245                                                 0.0015
    ## 246                                                 1.1789
    ## 247                                                 0.0805
    ## 248                                                 0.0528
    ## 249                                                 0.0011
    ## 250                                                11.3057
    ## 251                                                 2.0582
    ## 252                                                 1.7641
    ## 253                                                11.0483
    ## 254                                                 7.0647
    ## 255                                                 4.7649
    ## 256                                                53.3839
    ## 257                                                 1.2327
    ## 258                                                 0.5493
    ## 259                                                 8.9341
    ## 260                                                 3.2335
    ## 261                                                 0.8525
    ## 262                                                23.8775
    ## 263                                                 9.8984
    ## 264                                                41.4774
    ## 265                                               161.7928
    ## 266                                                15.2279
    ## 267                                                 2.9487
    ## 268                                                   2.59
    ## 269                                                 2.9665
    ## 270                                                 5.0637
    ## 271                                                19.8292
    ## 272                                                 0.6292
    ## 273                                                 0.5916
    ## 274                                                 2.8823
    ## 275                                                 1.4937
    ## 276                                                 0.2735
    ## 277                                               163.2414
    ## 278                                                 195.39
    ## 279                                                 3.8187
    ## 280                                                14.6185
    ## 281                                                37.9382
    ## 282                                                 5.8752
    ## 283                                                 3.7084
    ## 284                                                 0.1814
    ## 285                                                 1.5695
    ## 286                                                21.3163
    ## 287                                                29.6091
    ## 288                                                  0.527
    ## 289                                                 0.0016
    ## 290                                                 1.1814
    ## 291                                                 0.0774
    ## 292                                                 0.0535
    ## 293                                                 0.0011
    ## 294                                                10.9448
    ## 295                                                 2.0839
    ## 296                                                 1.7276
    ## 297                                                11.2064
    ## 298                                                 7.0661
    ## 299                                                 4.8123
    ## 300                                                52.3373
    ## 301                                                 1.2936
    ## 302                                                 0.5549
    ## 303                                                 9.2639
    ## 304                                                 3.2082
    ## 305                                                 0.8284
    ## 306                                                26.2885
    ## 307                                                 9.7905
    ## 308                                                40.4237
    ## 309                                               158.5746
    ## 310                                                15.0569
    ## 311                                                 2.8167
    ## 312                                                 2.6234
    ## 313                                                 2.9588
    ## 314                                                 4.9726
    ## 315                                                19.9821
    ## 316                                                 0.6466
    ## 317                                                 0.6058
    ## 318                                                 2.9674
    ## 319                                                 1.4137
    ## 320                                                 0.3365
    ## 321                                               156.9683
    ## 322                                               189.7358
    ## 323                                                 3.7178
    ## 324                                                14.5596
    ## 325                                                34.5144
    ## 326                                                  5.803
    ## 327                                                 3.7463
    ## 328                                                 0.1844
    ## 329                                                  1.359
    ## 330                                                21.8529
    ## 331                                                30.0326
    ## 332                                                 0.5317
    ## 333                                                 0.0016
    ## 334                                                 1.1867
    ## 335                                                 0.0775
    ## 336                                                 0.0553
    ## 337                                                 0.0012
    ## 338                                                 10.624
    ## 339                                                 2.1018
    ## 340                                                 1.6887
    ## 341                                                 11.493
    ## 342                                                 7.3186
    ## 343                                                 4.8205
    ## 344                                                 53.197
    ## 345                                                 1.4845
    ## 346                                                 0.5673
    ## 347                                                 9.7253
    ## 348                                                 3.1754
    ## 349                                                 0.8191
    ## 350                                                28.7423
    ## 351                                                 9.7624
    ## 352                                                 37.343
    ## 353                                               150.1499
    ## 354                                                14.4224
    ## 355                                                  2.726
    ## 356                                                 2.7325
    ## 357                                                 2.8212
    ## 358                                                 4.8337
    ## 359                                                20.2684
    ## 360                                                 0.6625
    ## 361                                                  0.616
    ## 362                                                 3.0118
    ## 363                                                 1.3504
    ## 364                                                 0.3722
    ## 365                                                152.705
    ## 366                                               186.2859
    ## 367                                                 3.5548
    ## 368                                                14.7632
    ## 369                                                31.9983
    ## 370                                                 5.9704
    ## 371                                                 3.8015
    ## 372                                                 0.1879
    ## 373                                                 1.4115
    ## 374                                                21.9341
    ## 375                                                29.6911
    ## 376                                                 0.5342
    ## 377                                                 0.0016
    ## 378                                                 1.1889
    ## 379                                                 0.0775
    ## 380                                                 0.0602
    ## 381                                                 0.0012
    ## 382                                                10.2047
    ## 383                                                 2.0969
    ## 384                                                 1.5797
    ## 385                                                11.8826
    ## 386                                                 7.6203
    ## 387                                                 4.8673
    ## 388                                                54.1839
    ## 389                                                 1.8288
    ## 390                                                 0.5834
    ## 391                                                10.1408
    ## 392                                                  3.123
    ## 393                                                 0.8003
    ## 394                                                30.3639
    ## 395                                                 9.7813
    ## 396                                                35.3047
    ## 397                                               143.0953
    ## 398                                                14.5349
    ## 399                                                 2.6315
    ## 400                                                 2.9218
    ## 401                                                 2.7202
    ## 402                                                  4.641
    ## 403                                                20.2674
    ## 404                                                 0.6889
    ## 405                                                  0.624
    ## 406                                                 3.0293
    ## 407                                                 1.3685
    ## 408                                                  0.395
    ## 409                                               146.7451
    ## 410                                               180.8392
    ## 411                                                 3.4752
    ## 412                                                14.7894
    ## 413                                                29.2817
    ## 414                                                 5.8913
    ## 415                                                 3.8638
    ## 416                                                 0.1918
    ## 417                                                 1.4385
    ## 418                                                 22.148
    ## 419                                                29.2639
    ## 420                                                  0.541
    ## 421                                                 0.0016
    ## 422                                                 1.1866
    ## 423                                                 0.0759
    ## 424                                                 0.0606
    ## 425                                                 0.0011
    ## 426                                                 9.3994
    ## 427                                                 2.0903
    ## 428                                                 1.4635
    ## 429                                                12.0758
    ## 430                                                 7.7118
    ## 431                                                  4.979
    ## 432                                                 56.552
    ## 433                                                 2.0927
    ## 434                                                 0.6054
    ## 435                                                10.4882
    ## 436                                                 3.0031
    ## 437                                                 0.7728
    ## 438                                                31.6792
    ## 439                                                 9.7731
    ## 440                                                32.6213
    ## 441                                               138.8959
    ## 442                                                14.0459
    ## 443                                                 2.5582
    ## 444                                                 2.9556
    ## 445                                                 2.5973
    ## 446                                                 4.6097
    ## 447                                                 19.953
    ## 448                                                 0.7073
    ## 449                                                 0.6391
    ## 450                                                 3.0581
    ## 451                                                 1.3762
    ## 452                                                 0.4348
    ## 453                                                143.744
    ## 454                                               176.8148
    ## 455                                                 3.2712
    ## 456                                                14.9201
    ## 457                                                27.9634
    ## 458                                                 5.7825
    ## 459                                                 3.9357
    ## 460                                                 0.1962
    ## 461                                                 1.4733
    ## 462                                                22.9289
    ## 463                                                29.0922
    ## 464                                                 0.5465
    ## 465                                                 0.0017
    ## 466                                                 1.1906
    ## 467                                                 0.0772
    ## 468                                                 0.0644
    ## 469                                                 0.0012
    ## 470                                                 8.8892
    ## 471                                                 2.1137
    ## 472                                                 1.4932
    ## 473                                                11.0344
    ## 474                                                 7.5718
    ## 475                                                 5.1577
    ## 476                                                58.8275
    ## 477                                                  1.777
    ## 478                                                 0.6227
    ## 479                                                10.7632
    ## 480                                                 2.9157
    ## 481                                                 0.7483
    ## 482                                                32.7935
    ## 483                                                 9.8652
    ## 484                                                30.9133
    ## 485                                               136.2448
    ## 486                                                 14.228
    ## 487                                                 2.5041
    ## 488                                                 3.0009
    ## 489                                                 2.3341
    ## 490                                                 4.4423
    ## 491                                                19.8168
    ## 492                                                 0.7369
    ## 493                                                 0.6165
    ## 494                                                 3.1133
    ## 495                                                 1.3577
    ## 496                                                 0.4416
    ## 497                                               137.2765
    ## 498                                               170.1233
    ## 499                                                 3.1398
    ## 500                                                14.8754
    ## 501                                                26.5879
    ## 502                                                 4.9365
    ## 503                                                 3.9569
    ## 504                                                 0.2023
    ## 505                                                 1.5985
    ## 506                                                22.8924
    ## 507                                                27.3486
    ## 508                                                 0.5752
    ## 509                                                 0.0016
    ## 510                                                 1.2162
    ## 511                                                 0.0749
    ## 512                                                 0.0668
    ## 513                                                 0.0012
    ## 514                                                 8.0792
    ## 515                                                 2.1403
    ## 516                                                 1.4366
    ## 517                                                10.7502
    ## 518                                                 7.6075
    ## 519                                                 5.2213
    ## 520                                                60.3397
    ## 521                                                 1.8108
    ## 522                                                 0.6354
    ## 523                                                11.1873
    ## 524                                                 2.8713
    ## 525                                                 0.7233
    ## 526                                                32.8857
    ## 527                                                10.0008
    ## 528                                                27.4893
    ## 529                                                131.728
    ## 530                                                14.3228
    ## 531                                                 2.5217
    ## 532                                                 3.0924
    ## 533                                                 2.3741
    ## 534                                                 4.4159
    ## 535                                                20.2202
    ## 536                                                 0.7692
    ## 537                                                 0.6271
    ## 538                                                  3.242
    ## 539                                                 1.3152
    ## 540                                                 0.4278
    ## 541                                                133.107
    ## 542                                               166.8957
    ## 543                                                 2.9234
    ## 544                                                14.8298
    ## 545                                                25.4458
    ## 546                                                 4.8481
    ## 547                                                 3.9668
    ## 548                                                 0.2055
    ## 549                                                 1.6948
    ## 550                                                22.4009
    ## 551                                                26.2574
    ## 552                                                 0.5701
    ## 553                                                 0.0017
    ## 554                                                 1.2207
    ## 555                                                 0.0741
    ## 556                                                 0.0683
    ## 557                                                 0.0012
    ## 558                                                 7.4302
    ## 559                                                 2.1612
    ## 560                                                 1.3649
    ## 561                                                10.7408
    ## 562                                                 7.8881
    ## 563                                                 5.2773
    ## 564                                                62.0268
    ## 565                                                 2.5845
    ## 566                                                 0.6474
    ## 567                                                11.5047
    ## 568                                                 2.7263
    ## 569                                                 0.7161
    ## 570                                                32.1404
    ## 571                                                 10.172
    ## 572                                                25.3759
    ## 573                                               132.5982
    ## 574                                                13.4258
    ## 575                                                  2.566
    ## 576                                                 4.0681
    ## 577                                                 2.1223
    ## 578                                                 4.9308
    ## 579                                                20.4978
    ## 580                                                 0.7999
    ## 581                                                 0.6377
    ## 582                                                 3.3285
    ## 583                                                 1.3122
    ## 584                                                  0.451
    ## 585                                               126.7714
    ## 586                                                160.987
    ## 587                                                 2.7478
    ## 588                                                14.7121
    ## 589                                                24.1437
    ## 590                                                 4.9195
    ## 591                                                 3.9734
    ## 592                                                 0.2065
    ## 593                                                 1.7879
    ## 594                                                21.5324
    ## 595                                                25.9135
    ## 596                                                 0.5287
    ## 597                                                 0.0018
    ## 598                                                 1.2247
    ## 599                                                  0.076
    ## 600                                                 0.0719
    ## 601                                                 0.0012
    ## 602                                                 6.6643
    ## 603                                                  2.119
    ## 604                                                 1.3541
    ## 605                                                 10.502
    ## 606                                                 7.9115
    ## 607                                                 5.4079
    ## 608                                                64.0083
    ## 609                                                 2.5019
    ## 610                                                 0.6572
    ## 611                                                11.4468
    ## 612                                                 2.5861
    ## 613                                                 0.6766
    ## 614                                                33.1229
    ## 615                                                10.2887
    ## 616                                                22.4911
    ## 617                                               138.2035
    ## 618                                                 13.062
    ## 619                                                 2.4472
    ## 620                                                 4.4636
    ## 621                                                 2.1446
    ## 622                                                 4.8881
    ## 623                                                20.8698
    ## 624                                                 0.8289
    ## 625                                                 0.6577
    ## 626                                                 3.2773
    ## 627                                                 1.1726
    ## 628                                                 0.4682
    ## 629                                               121.8045
    ## 630                                               155.9255
    ## 631                                                 2.6113
    ## 632                                                14.4338
    ## 633                                                22.9341
    ## 634                                                    4.9
    ## 635                                                  4.003
    ## 636                                                 0.2157
    ## 637                                                  1.612
    ## 638                                                20.5103
    ## 639                                                25.0663
    ## 640                                                 0.5274
    ## 641                                                 0.0017
    ## 642                                                  1.197
    ## 643                                                 0.0714
    ## 644                                                 0.0749
    ## 645                                                 0.0012
    ## 646                                                 6.1526
    ## 647                                                 2.1328
    ## 648                                                 1.3454
    ## 649                                                10.4085
    ## 650                                                 8.0465
    ## 651                                                 5.4617
    ## 652                                                66.1106
    ## 653                                                 2.4673
    ## 654                                                 0.6899
    ## 655                                                11.3841
    ## 656                                                 2.5718
    ## 657                                                 0.6819
    ## 658                                                31.3298
    ## 659                                                10.4738
    ## 660                                                21.0294
    ## 661                                               134.5678
    ## 662                                                12.8744
    ## 663                                                 2.3447
    ## 664                                                 4.6202
    ## 665                                                 2.0512
    ## 666                                                 4.2305
    ## 667                                                21.1579
    ## 668                                                 0.8144
    ## 669                                                 0.6629
    ## 670                                                  3.297
    ## 671                                                 1.1599
    ## 672                                                 0.4529
    ## 673                                               118.6738
    ## 674                                               152.1987
    ## 675                                                 2.4047
    ## 676                                                14.3013
    ## 677                                                21.3994
    ## 678                                                  4.958
    ## 679                                                 3.9914
    ## 680                                                 0.2072
    ## 681                                                 1.4899
    ## 682                                                20.4544
    ## 683                                                24.2997
    ## 684                                                 0.5283
    ## 685                                                 0.0019
    ## 686                                                 1.1734
    ## 687                                                   0.07
    ## 688                                                 0.0838
    ## 689                                                 0.0012
    ## 690                                                 5.5548
    ## 691                                                 2.1695
    ## 692                                                 1.2738
    ## 693                                                10.5269
    ## 694                                                 8.0612
    ## 695                                                 5.5393
    ## 696                                                68.6872
    ## 697                                                 2.3461
    ## 698                                                 0.6923
    ## 699                                                11.7207
    ## 700                                                 2.4312
    ## 701                                                  0.663
    ## 702                                                33.5771
    ## 703                                                10.5809
    ## 704                                                20.5219
    ## 705                                               136.9413
    ## 706                                                12.6163
    ## 707                                                 2.2688
    ## 708                                                 5.1186
    ## 709                                                 2.0149
    ## 710                                                 4.1742
    ## 711                                                21.6095
    ## 712                                                 0.8826
    ## 713                                                 0.6631
    ## 714                                                 3.3512
    ## 715                                                 1.1866
    ## 716                                                  0.479
    ## 717                                               116.3375
    ## 718                                               150.2539
    ## 719                                                 2.4735
    ## 720                                                14.2288
    ## 721                                                19.9831
    ## 722                                                 5.1174
    ## 723                                                 3.9657
    ## 724                                                 0.2247
    ## 725                                                 1.5743
    ## 726                                                19.8183
    ## 727                                                23.0565
    ## 728                                                 0.5345
    ## 729                                                 0.0018
    ## 730                                                 1.1437
    ## 731                                                 0.0699
    ## 732                                                 0.0948
    ## 733                                                 0.0011
    ## 734                                                 5.1842
    ## 735                                                 2.1172
    ## 736                                                 1.2944
    ## 737                                                10.5059
    ## 738                                                 8.0152
    ## 739                                                 5.7655
    ## 740                                                71.1714
    ## 741                                                 2.5326
    ## 742                                                 0.7059
    ## 743                                                12.1537
    ## 744                                                 2.3559
    ## 745                                                 0.6619
    ## 746                                                33.9402
    ## 747                                                10.7403
    ## 748                                                 20.149
    ## 749                                               136.2839
    ## 750                                                12.9263
    ## 751                                                 2.1593
    ## 752                                                 5.3403
    ## 753                                                 2.0042
    ## 754                                                 4.1171
    ## 755                                                21.3228
    ## 756                                                 0.9406
    ## 757                                                 0.6593
    ## 758                                                 3.3329
    ## 759                                                 1.1659
    ## 760                                                 0.4837
    ## 761                                               112.5875
    ## 762                                                146.062
    ## 763                                                 2.3759
    ## 764                                                13.8553
    ## 765                                                18.6205
    ## 766                                                 4.9349
    ## 767                                                 3.9176
    ## 768                                                 0.2244
    ## 769                                                 1.2194
    ## 770                                                19.1466
    ## 771                                                22.5236
    ## 772                                                 0.5469
    ## 773                                                 0.0019
    ## 774                                                 1.1215
    ## 775                                                 0.0681
    ## 776                                                 0.1008
    ## 777                                                 0.0012
    ## 778                                                  4.867
    ## 779                                                 2.0953
    ## 780                                                 1.2779
    ## 781                                                10.5611
    ## 782                                                 7.8346
    ## 783                                                 5.6024
    ## 784                                                73.2853
    ## 785                                                 2.3626
    ## 786                                                 0.6687
    ## 787                                                12.5884
    ## 788                                                 2.1973
    ## 789                                                 0.6464
    ## 790                                                35.6353
    ## 791                                                10.9003
    ## 792                                                19.8077
    ## 793                                               136.5114
    ## 794                                                13.3277
    ## 795                                                 2.0299
    ## 796                                                 5.6343
    ## 797                                                 1.8681
    ## 798                                                 4.0549
    ## 799                                                21.2299
    ## 800                                                 1.0015
    ## 801                                                 0.6659
    ## 802                                                 3.4917
    ## 803                                                 1.1427
    ## 804                                                  0.469
    ## 805                                               109.3269
    ## 806                                               142.4751
    ## 807                                                 2.2833
    ## 808                                                13.7663
    ## 809                                                17.4156
    ## 810                                                 4.9244
    ## 811                                                 3.8224
    ## 812                                                 0.2159
    ## 813                                                 1.1077
    ## 814                                                18.3377
    ## 815                                                23.7389
    ## 816                                                 0.5748
    ## 817                                                  0.002
    ## 818                                                 1.1132
    ## 819                                                 0.0664
    ## 820                                                 0.1058
    ## 821                                                 0.0011
    ## 822                                                 4.5872
    ## 823                                                 2.0604
    ## 824                                                 1.2307
    ## 825                                                10.2119
    ## 826                                                 7.6469
    ## 827                                                 5.6779
    ## 828                                                74.3255
    ## 829                                                   2.37
    ## 830                                                 0.5909
    ## 831                                                13.1211
    ## 832                                                 1.9996
    ## 833                                                 0.6264
    ## 834                                                33.5711
    ## 835                                                10.8471
    ## 836                                                19.2901
    ## 837                                               138.6453
    ## 838                                                13.2777
    ## 839                                                 1.9113
    ## 840                                                 6.2051
    ## 841                                                 1.7306
    ## 842                                                 3.9676
    ## 843                                                21.3876
    ## 844                                                 1.0574
    ## 845                                                 0.6774
    ## 846                                                 3.5286
    ## 847                                                 1.0844
    ## 848                                                 0.4317
    ## 849                                               105.7814
    ## 850                                               138.6057
    ## 851                                                 2.1865
    ## 852                                                13.2039
    ## 853                                                16.3587
    ## 854                                                 4.6709
    ## 855                                                 3.7518
    ## 856                                                 0.2113
    ## 857                                                 0.9746
    ## 858                                                18.2382
    ## 859                                                20.7029
    ## 860                                                 0.5742
    ## 861                                                 0.0018
    ## 862                                                 1.0904
    ## 863                                                 0.0631
    ## 864                                                 0.1176
    ## 865                                                 0.0012
    ## 866                                                 4.3604
    ## 867                                                 2.0427
    ## 868                                                 1.2516
    ## 869                                                10.2667
    ## 870                                                 7.3411
    ## 871                                                 5.7032
    ## 872                                                78.1794
    ## 873                                                 2.1641
    ## 874                                                 0.5511
    ## 875                                                 13.478
    ## 876                                                 1.8916
    ## 877                                                 0.6077
    ## 878                                                 33.273
    ## 879                                                10.9088
    ## 880                                                18.5445
    ## 881                                               138.1239
    ## 882                                                13.4889
    ## 883                                                  1.804
    ## 884                                                 6.1831
    ## 885                                                 1.7685
    ## 886                                                 3.8163
    ## 887                                                21.5953
    ## 888                                                 1.0495
    ## 889                                                 0.6389
    ## 890                                                 3.6118
    ## 891                                                 1.0368
    ## 892                                                 0.4529
    ## 893                                               104.4202
    ## 894                                               136.9776
    ## 895                                                 2.1855
    ## 896                                                13.2904
    ## 897                                                15.3541
    ## 898                                                  4.902
    ## 899                                                 3.6775
    ## 900                                                 0.2101
    ## 901                                                 0.9657
    ## 902                                                17.7855
    ## 903                                                20.9526
    ## 904                                                 0.5752
    ## 905                                                 0.0018
    ## 906                                                 1.0627
    ## 907                                                 0.0602
    ## 908                                                 0.1287
    ## 909                                                 0.0013
    ## 910                                                 4.0919
    ## 911                                                 2.0128
    ## 912                                                  1.228
    ## 913                                                10.1046
    ## 914                                                 7.9071
    ## 915                                                 5.7156
    ## 916                                                77.8321
    ## 917                                                 2.2228
    ## 918                                                 0.5502
    ## 919                                                 13.776
    ## 920                                                 1.7982
    ## 921                                                 0.5969
    ## 922                                                35.9663
    ## 923                                                11.0339
    ## 924                                                17.9581
    ## 925                                               131.4276
    ## 926                                                12.7911
    ## 927                                                 1.7083
    ## 928                                                  6.487
    ## 929                                                 1.6132
    ## 930                                                 3.7618
    ## 931                                                21.7461
    ## 932                                                 1.0783
    ## 933                                                 0.5904
    ## 934                                                  3.656
    ## 935                                                 1.0238
    ## 936                                                 0.3908
    ## 937                                               101.9414
    ## 938                                               133.4329
    ## 939                                                 2.1117
    ## 940                                                12.9134
    ## 941                                                14.3809
    ## 942                                                 4.7038
    ## 943                                                 3.5214
    ## 944                                                 0.1981
    ## 945                                                 1.0426
    ## 946                                                17.5209
    ## 947                                                20.5854
    ## 948                                                 0.5526
    ## 949                                                 0.0018
    ## 950                                                 0.9903
    ## 951                                                 0.0583
    ## 952                                                 0.1268
    ## 953                                                 0.0012
    ## 954                                                  3.879
    ## 955                                                 1.9854
    ## 956                                                 1.2212
    ## 957                                                 9.7453
    ## 958                                                 8.2804
    ## 959                                                 5.3665
    ## 960                                                80.8577
    ## 961                                                 2.2273
    ## 962                                                 0.5623
    ## 963                                                13.9007
    ## 964                                                 1.7126
    ## 965                                                  0.587
    ## 966                                                36.1266
    ## 967                                                11.0461
    ## 968                                                17.3626
    ## 969                                               127.6574
    ##     Energy.Emissions.by.Sub.Sector
    ## 1       Energy Industries (MtCO2e)
    ## 2                         143.0056
    ## 3                          13.8418
    ## 4                          65.3073
    ## 5                          29.9903
    ## 6                          38.8031
    ## 7                         144.7856
    ## 8                           7.1438
    ## 9                           1.7709
    ## 10                         57.9669
    ## 11                         26.5267
    ## 12                         28.7757
    ## 13                       1166.7552
    ## 14                       1668.1685
    ## 15                         19.1874
    ## 16                         64.4737
    ## 17                         428.073
    ## 18                          43.159
    ## 19                         22.7205
    ## 20                          0.0137
    ## 21                         11.2385
    ## 22                        137.2138
    ## 23                        325.2052
    ## 24                          6.2866
    ## 25                          0.0002
    ## 26                           13.55
    ## 27                          0.0356
    ## 28                          1.3726
    ## 29                          0.0282
    ## 30                         52.6992
    ## 31                          5.9659
    ## 32                          6.9683
    ## 33                        235.8178
    ## 34                         16.3261
    ## 35                         71.1928
    ## 36                       1176.0419
    ## 37                          16.891
    ## 38                          6.2655
    ## 39                         77.6552
    ## 40                         10.1448
    ## 41                          2.5515
    ## 42                          34.143
    ## 43                        272.0493
    ## 44                        237.7914
    ## 45                       1828.5137
    ## 46                        146.2659
    ## 47                         14.6794
    ## 48                          58.764
    ## 49                         29.9299
    ## 50                         30.4573
    ## 51                        143.7215
    ## 52                          4.7795
    ## 53                          1.8332
    ## 54                         57.6582
    ## 55                         35.4184
    ## 56                         26.2649
    ## 57                        1169.408
    ## 58                        1647.152
    ## 59                         18.9585
    ## 60                          76.786
    ## 61                        414.8644
    ## 62                         42.0117
    ## 63                         23.3819
    ## 64                          0.0152
    ## 65                          11.699
    ## 66                         131.265
    ## 67                        327.9733
    ## 68                          5.7696
    ## 69                          0.0008
    ## 70                         14.6205
    ## 71                          0.0363
    ## 72                          1.5177
    ## 73                          0.0277
    ## 74                         53.3085
    ## 75                          6.0799
    ## 76                          7.3441
    ## 77                        229.7506
    ## 78                         16.9492
    ## 79                         65.9167
    ## 80                       1105.3603
    ## 81                         15.2282
    ## 82                          5.3453
    ## 83                         78.4317
    ## 84                         11.1422
    ## 85                          2.8179
    ## 86                         36.7715
    ## 87                        232.4495
    ## 88                        235.5811
    ## 89                       1825.8749
    ## 90                        149.6104
    ## 91                         11.3603
    ## 92                         54.6787
    ## 93                         28.7667
    ## 94                         28.7117
    ## 95                        152.7875
    ## 96                           5.351
    ## 97                          2.1314
    ## 98                         51.5168
    ## 99                         30.4841
    ## 100                         19.875
    ## 101                      1131.4411
    ## 102                       1567.846
    ## 103                        18.7296
    ## 104                        69.3337
    ## 105                       391.6041
    ## 106                        44.3024
    ## 107                        24.3176
    ## 108                         0.0137
    ## 109                        12.3636
    ## 110                       130.9846
    ## 111                       334.6791
    ## 112                         4.9439
    ## 113                         0.0019
    ## 114                         8.6028
    ## 115                         0.0371
    ## 116                         1.6027
    ## 117                         0.0306
    ## 118                        53.2559
    ## 119                         7.5623
    ## 120                         7.9226
    ## 121                       220.5178
    ## 122                        20.0233
    ## 123                        55.0552
    ## 124                      1081.2472
    ## 125                        13.2635
    ## 126                         5.8666
    ## 127                        85.8873
    ## 128                        11.7489
    ## 129                          2.908
    ## 130                        41.9575
    ## 131                       198.8705
    ## 132                       224.3444
    ## 133                      1839.2795
    ## 134                       151.3983
    ## 135                         11.513
    ## 136                        45.7218
    ## 137                        28.2351
    ## 138                        29.0165
    ## 139                       144.2166
    ## 140                         5.9319
    ## 141                          2.252
    ## 142                        53.7717
    ## 143                        32.0758
    ## 144                        15.6428
    ## 145                      1085.0398
    ## 146                      1506.4892
    ## 147                        21.4623
    ## 148                         56.907
    ## 149                       381.2355
    ## 150                        44.2003
    ## 151                         25.486
    ## 152                          0.015
    ## 153                        12.3786
    ## 154                       125.4742
    ## 155                       316.5689
    ## 156                         3.9901
    ## 157                         0.0019
    ## 158                         7.2766
    ## 159                         0.0353
    ## 160                          1.578
    ## 161                         0.0334
    ## 162                        55.4643
    ## 163                         6.6276
    ## 164                         8.1955
    ## 165                       207.6558
    ## 166                        18.0816
    ## 167                        56.9865
    ## 168                       1056.814
    ## 169                         12.148
    ## 170                         5.6454
    ## 171                        79.9409
    ## 172                        11.8877
    ## 173                         2.5628
    ## 174                        40.7217
    ## 175                       171.1002
    ## 176                       207.9144
    ## 177                      1914.9743
    ## 178                        152.293
    ## 179                        11.8092
    ## 180                        39.3758
    ## 181                        30.0165
    ## 182                        26.7152
    ## 183                       146.8954
    ## 184                         4.6812
    ## 185                         2.3837
    ## 186                        53.9554
    ## 187                        36.1236
    ## 188                        15.9078
    ## 189                      1095.5473
    ## 190                      1512.5933
    ## 191                        26.3914
    ## 192                        53.2765
    ## 193                       378.9785
    ## 194                        46.1846
    ## 195                          24.65
    ## 196                         0.0147
    ## 197                        12.7168
    ## 198                        127.955
    ## 199                       357.4037
    ## 200                         3.7494
    ## 201                         0.0018
    ## 202                         7.2309
    ## 203                         0.0345
    ## 204                         1.6751
    ## 205                         0.0362
    ## 206                        58.2568
    ## 207                         5.5217
    ## 208                         8.8823
    ## 209                       206.7796
    ## 210                        17.2623
    ## 211                        57.6225
    ## 212                       965.2844
    ## 213                        11.1212
    ## 214                         5.2553
    ## 215                        80.2834
    ## 216                        12.3925
    ## 217                         2.5998
    ## 218                        47.3586
    ## 219                       148.9028
    ## 220                        205.725
    ## 221                      1939.4715
    ## 222                       158.1487
    ## 223                        12.9708
    ## 224                        33.5697
    ## 225                        29.4224
    ## 226                        27.2246
    ## 227                       151.6063
    ## 228                          5.275
    ## 229                         2.1752
    ## 230                        60.7453
    ## 231                        32.7159
    ## 232                        14.3913
    ## 233                        1104.27
    ## 234                      1513.5697
    ## 235                        24.1198
    ## 236                        56.0009
    ## 237                        368.282
    ## 238                        44.9426
    ## 239                        24.4819
    ## 240                          0.019
    ## 241                        13.4014
    ## 242                       140.5407
    ## 243                       346.3959
    ## 244                          3.434
    ## 245                          0.002
    ## 246                         6.3719
    ## 247                         0.0932
    ## 248                         1.6112
    ## 249                         0.0361
    ## 250                         61.665
    ## 251                         4.7963
    ## 252                          8.742
    ## 253                       191.4957
    ## 254                        19.8911
    ## 255                        60.1025
    ## 256                       912.5808
    ## 257                        11.6395
    ## 258                         5.6265
    ## 259                        86.6375
    ## 260                        11.5434
    ## 261                         2.6372
    ## 262                        47.4934
    ## 263                       132.3969
    ## 264                       203.9337
    ## 265                      1956.2304
    ## 266                       162.8561
    ## 267                        13.8563
    ## 268                        33.7044
    ## 269                        29.2445
    ## 270                        27.0375
    ## 271                       151.6876
    ## 272                         5.1221
    ## 273                         2.2899
    ## 274                        64.7128
    ## 275                        45.0936
    ## 276                        14.9112
    ## 277                      1120.7992
    ## 278                      1545.0463
    ## 279                        29.8297
    ## 280                        61.2009
    ## 281                       375.6062
    ## 282                        44.1182
    ## 283                        25.3406
    ## 284                         0.0118
    ## 285                        14.1206
    ## 286                       135.7194
    ## 287                       346.6153
    ## 288                          3.567
    ## 289                         0.0025
    ## 290                         7.0532
    ## 291                         0.0813
    ## 292                         1.6384
    ## 293                         0.0388
    ## 294                        62.6558
    ## 295                          5.549
    ## 296                         9.7956
    ## 297                        198.129
    ## 298                        15.9222
    ## 299                        62.8067
    ## 300                       910.5752
    ## 301                        11.5239
    ## 302                          5.237
    ## 303                        73.6233
    ## 304                        16.0704
    ## 305                         2.8531
    ## 306                        52.1748
    ## 307                       115.5011
    ## 308                       205.5663
    ## 309                      2029.5181
    ## 310                       169.5387
    ## 311                        13.9248
    ## 312                        35.5277
    ## 313                        28.1095
    ## 314                        29.0642
    ## 315                       160.1265
    ## 316                         5.6068
    ## 317                         2.4215
    ## 318                         60.702
    ## 319                        35.9483
    ## 320                         14.489
    ## 321                      1086.0737
    ## 322                      1495.6651
    ## 323                        27.4384
    ## 324                        57.2878
    ## 325                       354.8701
    ## 326                        47.5682
    ## 327                        25.2777
    ## 328                         0.0083
    ## 329                        14.7823
    ## 330                       137.7084
    ## 331                       343.5823
    ## 332                         3.3245
    ## 333                         0.0025
    ## 334                         6.4949
    ## 335                         0.0824
    ## 336                         1.6305
    ## 337                         0.0435
    ## 338                        63.6848
    ## 339                         7.1479
    ## 340                        10.1664
    ## 341                        192.442
    ## 342                        16.6475
    ## 343                        56.0396
    ## 344                       857.8853
    ## 345                        12.0554
    ## 346                           5.65
    ## 347                        85.9643
    ## 348                        11.1987
    ## 349                         2.8178
    ## 350                        58.4082
    ## 351                        107.818
    ## 352                       192.7434
    ## 353                      2097.0928
    ## 354                       182.1054
    ## 355                        13.0582
    ## 356                        33.4509
    ## 357                        30.8392
    ## 358                        27.8584
    ## 359                        176.054
    ## 360                         6.2868
    ## 361                         2.6547
    ## 362                        58.3583
    ## 363                        32.3318
    ## 364                        12.9155
    ## 365                      1121.7695
    ## 366                      1513.0867
    ## 367                        24.1825
    ## 368                        70.1756
    ## 369                       357.6757
    ## 370                        50.0959
    ## 371                        26.4134
    ## 372                         0.0113
    ## 373                        15.1672
    ## 374                       148.7534
    ## 375                       333.9603
    ## 376                         3.3687
    ## 377                         0.0029
    ## 378                          7.302
    ## 379                         0.1469
    ## 380                         1.6451
    ## 381                         0.0409
    ## 382                        66.0109
    ## 383                         5.5779
    ## 384                         9.8521
    ## 385                       185.5139
    ## 386                        19.2721
    ## 387                        47.3538
    ## 388                       862.4702
    ## 389                         12.048
    ## 390                         5.8853
    ## 391                        85.2958
    ## 392                        12.2791
    ## 393                         3.1442
    ## 394                          64.31
    ## 395                       101.3229
    ## 396                       198.4759
    ## 397                      2186.4742
    ## 398                       189.4411
    ## 399                        12.5808
    ## 400                        32.1042
    ## 401                        27.1284
    ## 402                        24.2289
    ## 403                         184.46
    ## 404                         6.4824
    ## 405                         2.8409
    ## 406                        56.2906
    ## 407                        29.2469
    ## 408                        12.3453
    ## 409                      1101.2812
    ## 410                      1472.8924
    ## 411                         23.663
    ## 412                        63.7518
    ## 413                        345.576
    ## 414                         50.388
    ## 415                        26.1096
    ## 416                         0.0084
    ## 417                        15.8223
    ## 418                       146.5566
    ## 419                       351.4439
    ## 420                         2.9402
    ## 421                         0.0029
    ## 422                         5.9129
    ## 423                         0.1623
    ## 424                         1.7086
    ## 425                         0.0414
    ## 426                        62.0936
    ## 427                         6.7892
    ## 428                         9.8124
    ## 429                       179.9186
    ## 430                        25.3947
    ## 431                        42.3552
    ## 432                       850.5603
    ## 433                         11.766
    ## 434                         5.1945
    ## 435                       101.2313
    ## 436                        10.5104
    ## 437                         3.1817
    ## 438                        69.5927
    ## 439                         104.03
    ## 440                       189.2866
    ## 441                      2199.7964
    ## 442                       192.4727
    ## 443                        12.2754
    ## 444                        30.7512
    ## 445                         28.528
    ## 446                        24.0715
    ## 447                       196.7241
    ## 448                          5.895
    ## 449                         2.9683
    ## 450                        59.5702
    ## 451                        26.2128
    ## 452                        11.9121
    ## 453                       1132.889
    ## 454                      1501.9364
    ## 455                        22.1198
    ## 456                        62.9686
    ## 457                       359.6293
    ## 458                        54.8322
    ## 459                        24.0665
    ## 460                         0.0074
    ## 461                        16.1405
    ## 462                       152.5561
    ## 463                       359.3167
    ## 464                         2.4899
    ## 465                         0.0027
    ## 466                         5.0521
    ## 467                           0.12
    ## 468                         1.6933
    ## 469                         0.0427
    ## 470                        63.9169
    ## 471                         6.4613
    ## 472                        10.7557
    ## 473                       177.4363
    ## 474                        21.6192
    ## 475                         42.761
    ## 476                       863.4636
    ## 477                        11.5282
    ## 478                         5.4979
    ## 479                       105.3688
    ## 480                         8.9749
    ## 481                         3.0927
    ## 482                        77.0419
    ## 483                        97.0416
    ## 484                       199.7057
    ## 485                      2306.9427
    ## 486                       199.7428
    ## 487                        13.8889
    ## 488                        31.1873
    ## 489                        27.0054
    ## 490                        27.9542
    ## 491                       200.9771
    ## 492                          6.395
    ## 493                         2.8502
    ## 494                        61.8495
    ## 495                        27.5811
    ## 496                        11.7282
    ## 497                      1160.5093
    ## 498                      1539.5134
    ## 499                        27.5091
    ## 500                        56.1953
    ## 501                        371.788
    ## 502                         55.355
    ## 503                         23.756
    ## 504                         0.0067
    ## 505                        17.3642
    ## 506                       155.1639
    ## 507                       351.6841
    ## 508                         2.4315
    ## 509                         0.0029
    ## 510                         5.5279
    ## 511                         0.2833
    ## 512                         1.8142
    ## 513                         0.0452
    ## 514                        68.0073
    ## 515                          7.948
    ## 516                        12.0013
    ## 517                        179.064
    ## 518                        22.0919
    ## 519                        42.8994
    ## 520                       861.6002
    ## 521                        12.9263
    ## 522                         6.2027
    ## 523                         99.856
    ## 524                        10.5488
    ## 525                         3.2235
    ## 526                        79.9893
    ## 527                         100.21
    ## 528                       209.7819
    ## 529                      2268.5169
    ## 530                       201.1576
    ## 531                        13.5372
    ## 532                        30.8342
    ## 533                        28.5017
    ## 534                        25.2857
    ## 535                       199.9593
    ## 536                         7.2691
    ## 537                         3.0119
    ## 538                        60.2305
    ## 539                        27.7581
    ## 540                        11.4498
    ## 541                      1192.1211
    ## 542                      1558.1645
    ## 543                        30.2624
    ## 544                        60.4087
    ## 545                       373.5969
    ## 546                        54.7749
    ## 547                          21.91
    ## 548                         0.0087
    ## 549                        16.4538
    ## 550                       162.0882
    ## 551                       383.2419
    ## 552                         2.3272
    ## 553                         0.0025
    ## 554                         5.3444
    ## 555                         1.0296
    ## 556                         1.8303
    ## 557                         0.0405
    ## 558                        67.3876
    ## 559                         7.3302
    ## 560                        12.2483
    ## 561                       172.8834
    ## 562                        25.5175
    ## 563                        42.2289
    ## 564                       870.6371
    ## 565                        13.0895
    ## 566                         6.4518
    ## 567                       113.4811
    ## 568                        11.4963
    ## 569                         3.3143
    ## 570                        74.2925
    ## 571                        99.8844
    ## 572                       207.8259
    ## 573                      2285.1084
    ## 574                       207.9745
    ## 575                        16.3613
    ## 576                        30.6664
    ## 577                        29.6219
    ## 578                        27.1668
    ## 579                       205.4012
    ## 580                         7.9491
    ## 581                         3.2391
    ## 582                        60.1875
    ## 583                        32.4821
    ## 584                        13.2483
    ## 585                      1225.4512
    ## 586                      1609.9909
    ## 587                        37.2348
    ## 588                         63.974
    ## 589                       387.7231
    ## 590                        56.0156
    ## 591                        22.8524
    ## 592                         0.0079
    ## 593                        15.7616
    ## 594                       162.6821
    ## 595                       397.2635
    ## 596                         2.2604
    ## 597                         0.0028
    ## 598                         5.2184
    ## 599                         1.0375
    ## 600                         2.0068
    ## 601                         0.0336
    ## 602                        68.8493
    ## 603                         8.6517
    ## 604                        12.9573
    ## 605                        181.249
    ## 606                        21.0059
    ## 607                        47.9279
    ## 608                       881.0183
    ## 609                        12.9995
    ## 610                         6.1837
    ## 611                       106.6174
    ## 612                        12.6721
    ## 613                          3.347
    ## 614                        74.4258
    ## 615                       105.3619
    ## 616                       215.3552
    ## 617                      2317.8137
    ## 618                       216.3781
    ## 619                        16.4049
    ## 620                        32.6909
    ## 621                         29.778
    ## 622                        26.8622
    ## 623                       199.2595
    ## 624                         6.8437
    ## 625                         3.2944
    ## 626                        60.2193
    ## 627                        26.5918
    ## 628                        13.1724
    ## 629                      1222.2436
    ## 630                      1597.1201
    ## 631                        33.0481
    ## 632                        63.2026
    ## 633                       385.1853
    ## 634                        57.3409
    ## 635                        20.7337
    ## 636                         0.0076
    ## 637                        15.3687
    ## 638                       160.6845
    ## 639                       392.8659
    ## 640                         2.0704
    ## 641                         0.0029
    ## 642                         5.3944
    ## 643                         1.2634
    ## 644                         1.9575
    ## 645                         0.0299
    ## 646                         70.275
    ## 647                         8.2756
    ## 648                        13.0664
    ## 649                       179.2449
    ## 650                        22.4778
    ## 651                        43.2139
    ## 652                       865.8444
    ## 653                        12.3996
    ## 654                         6.3138
    ## 655                        116.311
    ## 656                        11.7377
    ## 657                         3.6671
    ## 658                        76.4215
    ## 659                        98.6642
    ## 660                        214.572
    ## 661                      2352.2289
    ## 662                       219.8421
    ## 663                        16.3627
    ## 664                        32.1213
    ## 665                        29.4275
    ## 666                        27.0436
    ## 667                       194.0144
    ## 668                         6.8016
    ## 669                         3.4831
    ## 670                        61.1585
    ## 671                        23.3355
    ## 672                        12.3946
    ## 673                        1215.16
    ## 674                      1584.7557
    ## 675                        21.9202
    ## 676                        68.3806
    ## 677                       378.8885
    ## 678                        58.1537
    ## 679                        18.3566
    ## 680                         0.0094
    ## 681                        15.7703
    ## 682                       160.5519
    ## 683                       408.1377
    ## 684                         2.0587
    ## 685                         0.0031
    ## 686                         5.6507
    ## 687                         1.2438
    ## 688                         1.9959
    ## 689                           0.03
    ## 690                         67.681
    ## 691                        10.3235
    ## 692                        13.3323
    ## 693                       178.1122
    ## 694                         25.488
    ## 695                         41.342
    ## 696                       868.3768
    ## 697                        11.6748
    ## 698                         6.3252
    ## 699                       126.1329
    ## 700                         10.844
    ## 701                         3.8517
    ## 702                        88.8331
    ## 703                        99.8769
    ## 704                       213.0823
    ## 705                      2418.6007
    ## 706                        224.519
    ## 707                        15.2542
    ## 708                        32.5578
    ## 709                        27.9345
    ## 710                        27.3563
    ## 711                       187.4911
    ## 712                         6.6497
    ## 713                         3.6649
    ## 714                        60.6116
    ## 715                        31.2668
    ## 716                        11.6596
    ## 717                       1218.805
    ## 718                      1595.4798
    ## 719                        32.8734
    ## 720                        65.1616
    ## 721                        381.283
    ## 722                        55.9677
    ## 723                        19.3649
    ## 724                         0.0088
    ## 725                        15.0286
    ## 726                       161.6982
    ## 727                       396.4362
    ## 728                         2.0854
    ## 729                         0.0028
    ## 730                         5.1983
    ## 731                         1.3078
    ## 732                         2.0107
    ## 733                          0.023
    ## 734                        62.7577
    ## 735                        10.2128
    ## 736                        13.3194
    ## 737                       183.3687
    ## 738                        22.5301
    ## 739                          44.06
    ## 740                       899.5941
    ## 741                         10.915
    ## 742                         6.3794
    ## 743                       117.1541
    ## 744                        10.9011
    ## 745                         4.1284
    ## 746                        90.8855
    ## 747                       107.6678
    ## 748                        219.951
    ## 749                      2363.0766
    ## 750                       227.2541
    ## 751                         13.986
    ## 752                        30.5151
    ## 753                        27.4356
    ## 754                         30.679
    ## 755                       194.3628
    ## 756                         7.7607
    ## 757                         3.8137
    ## 758                        64.2277
    ## 759                        26.5723
    ## 760                        13.9045
    ## 761                      1221.4405
    ## 762                      1603.4312
    ## 763                         30.804
    ## 764                        65.5772
    ## 765                       389.5711
    ## 766                        59.4442
    ## 767                        20.1906
    ## 768                         0.0241
    ## 769                        14.5354
    ## 770                       161.4687
    ## 771                       449.4324
    ## 772                         1.9558
    ## 773                         0.0025
    ## 774                         4.7364
    ## 775                          1.184
    ## 776                          2.053
    ## 777                         0.0306
    ## 778                        65.4706
    ## 779                         8.8278
    ## 780                         13.656
    ## 781                       180.0843
    ## 782                        19.8785
    ## 783                         43.465
    ## 784                       886.0966
    ## 785                        10.2842
    ## 786                         6.5964
    ## 787                       123.1352
    ## 788                        10.3023
    ## 789                         3.8788
    ## 790                       106.9316
    ## 791                       107.0549
    ## 792                       214.4565
    ## 793                      2430.0107
    ## 794                       229.9995
    ## 795                        13.7807
    ## 796                        31.5449
    ## 797                        25.4701
    ## 798                        32.2035
    ## 799                       181.6846
    ## 800                         6.7263
    ## 801                         3.9799
    ## 802                        59.0613
    ## 803                        24.4742
    ## 804                        12.6079
    ## 805                      1159.6409
    ## 806                      1529.0126
    ## 807                         24.092
    ## 808                        63.8135
    ## 809                       368.2116
    ## 810                        58.2259
    ## 811                        19.4009
    ## 812                         0.0082
    ## 813                        14.6529
    ## 814                       156.8061
    ## 815                       422.9406
    ## 816                         1.9283
    ## 817                         0.0029
    ## 818                         4.8372
    ## 819                         0.9995
    ## 820                         2.0098
    ## 821                         0.0287
    ## 822                        65.5539
    ## 823                         9.7533
    ## 824                        13.6919
    ## 825                       174.3189
    ## 826                        19.3116
    ## 827                        42.3088
    ## 828                       904.6511
    ## 829                        10.3271
    ## 830                         6.3881
    ## 831                       106.0225
    ## 832                        10.1532
    ## 833                         4.0606
    ## 834                       106.2726
    ## 835                       106.0858
    ## 836                       210.4229
    ## 837                      2378.2085
    ## 838                        237.011
    ## 839                        12.8485
    ## 840                        30.3403
    ## 841                        25.9109
    ## 842                        29.6242
    ## 843                       166.1361
    ## 844                         6.3922
    ## 845                         4.0053
    ## 846                         56.192
    ## 847                         24.338
    ## 848                        10.6911
    ## 849                      1062.0433
    ## 850                      1404.4408
    ## 851                         25.127
    ## 852                        61.7007
    ## 853                       342.0896
    ## 854                        54.6786
    ## 855                        16.2194
    ## 856                          0.009
    ## 857                        13.0777
    ## 858                       131.7964
    ## 859                       387.4572
    ## 860                         1.8769
    ## 861                         0.0029
    ## 862                         4.8131
    ## 863                         1.1951
    ## 864                         1.9032
    ## 865                         0.0265
    ## 866                        64.6021
    ## 867                         7.5481
    ## 868                        14.4566
    ## 869                       166.9015
    ## 870                        19.4927
    ## 871                        35.6607
    ## 872                       867.2449
    ## 873                         8.4228
    ## 874                         6.0873
    ## 875                        89.7953
    ## 876                        10.5671
    ## 877                         3.9758
    ## 878                       102.8192
    ## 879                        96.7802
    ## 880                       187.2283
    ## 881                      2163.6548
    ## 882                        232.993
    ## 883                        14.2352
    ## 884                        31.7734
    ## 885                        26.4353
    ## 886                        31.5469
    ## 887                       166.0385
    ## 888                         5.9047
    ## 889                         3.8803
    ## 890                         58.905
    ## 891                        24.3288
    ## 892                        14.2386
    ## 893                      1071.4744
    ## 894                      1428.4414
    ## 895                        30.4906
    ## 896                        62.2333
    ## 897                       356.4012
    ## 898                        52.2224
    ## 899                        16.6801
    ## 900                         0.0069
    ## 901                        13.3334
    ## 902                       133.1824
    ## 903                       407.3078
    ## 904                         2.2606
    ## 905                         0.0032
    ## 906                         5.3184
    ## 907                         1.2071
    ## 908                         1.8933
    ## 909                         0.0256
    ## 910                        66.6128
    ## 911                         6.7743
    ## 912                        14.8757
    ## 913                       173.4737
    ## 914                        14.5502
    ## 915                        33.1628
    ## 916                       891.7417
    ## 917                         9.3934
    ## 918                         6.2137
    ## 919                        72.5514
    ## 920                        13.0904
    ## 921                         4.1967
    ## 922                       112.9137
    ## 923                       102.6419
    ## 924                       192.9862
    ## 925                      2278.1058
    ## 926                       230.1836
    ## 927                        13.9884
    ## 928                         29.073
    ## 929                        22.0493
    ## 930                        36.3601
    ## 931                       154.8545
    ## 932                         6.2754
    ## 933                          3.722
    ## 934                        58.4239
    ## 935                        20.4175
    ## 936                        14.8756
    ## 937                      1041.1266
    ## 938                      1406.0874
    ## 939                        24.6284
    ## 940                        53.6822
    ## 941                       354.3089
    ## 942                        54.0264
    ## 943                        16.0254
    ## 944                          0.007
    ## 945                        11.9415
    ## 946                       131.2305
    ## 947                       468.6443
    ## 948                         2.0838
    ## 949                          0.003
    ## 950                         4.4465
    ## 951                         0.9947
    ## 952                         1.9377
    ## 953                         0.0278
    ## 954                        62.4256
    ## 955                         6.4687
    ## 956                        14.4684
    ## 957                       174.7709
    ## 958                        16.5251
    ## 959                        36.6219
    ## 960                       899.1465
    ## 961                         9.4343
    ## 962                         6.2586
    ## 963                         86.526
    ## 964                        10.6621
    ## 965                         3.9943
    ## 966                       122.1335
    ## 967                       112.0526
    ## 968                       180.1543
    ## 969                      2176.8977
    ##                                                    X.11                X.12
    ## 1    Manufacturing Industries and Construction (MtCO2e)  Transport (MtCO2e)
    ## 2                                               35.6078             62.0311
    ## 3                                               12.7736             14.0291
    ## 4                                                7.2385              13.074
    ## 5                                               32.7926             20.8152
    ## 6                                               19.6082              6.7939
    ## 7                                               64.2755            146.0118
    ## 8                                                5.8719              4.0954
    ## 9                                                1.0815              1.1753
    ## 10                                              46.7539              7.7559
    ## 11                                               5.5349             10.9821
    ## 12                                               2.4869              2.4605
    ## 13                                             643.2436            696.6285
    ## 14                                             853.9465             774.249
    ## 15                                              13.3566             12.7567
    ## 16                                              88.4223            122.1532
    ## 17                                             177.2594            164.7217
    ## 18                                               9.6186             14.5437
    ## 19                                              11.8047              8.3401
    ## 20                                                0.377              0.6208
    ## 21                                               3.9612              5.1214
    ## 22                                              86.9477            103.1055
    ## 23                                             373.0171             215.557
    ## 24                                               3.7376               2.999
    ## 25                                               0.0353              0.0767
    ## 26                                               5.7566              7.5598
    ## 27                                               6.3047              2.7211
    ## 28                                               0.0595              0.3495
    ## 29                                                                   0.0334
    ## 30                                              33.0982             26.2552
    ## 31                                               4.7242              8.6257
    ## 32                                               3.5748             11.1015
    ## 33                                              42.4208             20.4727
    ## 34                                               9.8543             10.3089
    ## 35                                              55.7194             11.9622
    ## 36                                             217.5303            342.3652
    ## 37                                              18.1552              5.0217
    ## 38                                               3.1188              2.7298
    ## 39                                              46.9705             55.7431
    ## 40                                              12.0593             19.3011
    ## 41                                               6.1189             14.5975
    ## 42                                               37.735             26.2866
    ## 43                                             191.8343             91.1236
    ## 44                                             105.4751            116.2502
    ## 45                                             854.6598           1492.3613
    ## 46                                              35.1684             61.4576
    ## 47                                              13.1702             15.5331
    ## 48                                               7.7458             12.8182
    ## 49                                                 32.7             21.0031
    ## 50                                              15.3843              3.9205
    ## 51                                              60.7307            141.2795
    ## 52                                               4.3662              3.0107
    ## 53                                               1.3064              1.1715
    ## 54                                              49.2984              6.9383
    ## 55                                               6.0816             11.3703
    ## 56                                               2.3459              2.2401
    ## 57                                             624.6919            711.3031
    ## 58                                             809.9379            782.5189
    ## 59                                              12.8344             12.3993
    ## 60                                              89.1698            124.9124
    ## 61                                             155.6946            168.0297
    ## 62                                               9.5221              15.345
    ## 63                                              10.6135              7.4408
    ## 64                                               0.3006              0.6328
    ## 65                                               4.0739              5.3052
    ## 66                                              84.6179            105.7193
    ## 67                                             368.0656            227.1356
    ## 68                                               2.8136              2.8111
    ## 69                                               0.0342                0.09
    ## 70                                               5.8739              7.7356
    ## 71                                               6.1403              3.2316
    ## 72                                               0.0626              0.3699
    ## 73                                                                   0.0382
    ## 74                                              32.8109             26.5509
    ## 75                                                5.209              8.6355
    ## 76                                               3.4064             10.9822
    ## 77                                              39.5502             21.5233
    ## 78                                               9.9695             10.9201
    ## 79                                              38.1581             10.2677
    ## 80                                              210.671            332.3687
    ## 81                                              16.7816              4.2202
    ## 82                                               3.0574              2.5768
    ## 83                                              49.4185             58.8179
    ## 84                                              12.1047             18.8575
    ## 85                                               6.2997             15.0922
    ## 86                                              40.6896             24.9905
    ## 87                                             163.0587             79.6729
    ## 88                                             107.7165            115.4449
    ## 89                                             834.2381           1450.3671
    ## 90                                              34.7399             62.6575
    ## 91                                              12.0425             15.5183
    ## 92                                               7.2045             10.5836
    ## 93                                              31.8928             21.7574
    ## 94                                              14.6475              4.1158
    ## 95                                              59.7663            145.0498
    ## 96                                               3.6983              2.8955
    ## 97                                                1.122               1.318
    ## 98                                               41.217              7.8077
    ## 99                                               5.9119             11.5834
    ## 100                                               1.577              1.1557
    ## 101                                            601.6196            736.1894
    ## 102                                            765.9241            804.4504
    ## 103                                             12.3038             12.3165
    ## 104                                             87.7514            129.6268
    ## 105                                            145.4534            173.4348
    ## 106                                              8.8835             15.7403
    ## 107                                             10.1607              7.2182
    ## 108                                              0.3535              0.6434
    ## 109                                              3.7683              5.7276
    ## 110                                             83.2026            110.0837
    ## 111                                            360.2986            231.6237
    ## 112                                              2.3768              2.5034
    ## 113                                              0.0342              0.0892
    ## 114                                              2.7971              5.2031
    ## 115                                              5.8158              3.5297
    ## 116                                              0.0592              0.3947
    ## 117                                                                  0.0438
    ## 118                                             33.4073             27.8647
    ## 119                                              5.0569              8.9869
    ## 120                                              3.3213             11.2128
    ## 121                                             37.0409             21.9931
    ## 122                                             10.4049             11.8368
    ## 123                                             34.9675             10.0178
    ## 124                                            138.0074            270.5767
    ## 125                                             15.6761               3.882
    ## 126                                              2.6627              2.6515
    ## 127                                             46.5007             62.4415
    ## 128                                             11.0794             19.9915
    ## 129                                              5.9548              15.417
    ## 130                                             39.6392             25.6346
    ## 131                                            138.8162             69.1337
    ## 132                                            104.5476            116.8845
    ## 133                                            865.5971            1515.509
    ## 134                                             35.2259              63.989
    ## 135                                             12.3478             15.6628
    ## 136                                              6.8237              8.5474
    ## 137                                             30.7857             22.2777
    ## 138                                             13.5987              4.7121
    ## 139                                             59.6422            148.7686
    ## 140                                              3.5324              3.0755
    ## 141                                              1.1864              1.3374
    ## 142                                             42.1015              7.7367
    ## 143                                              5.7647             11.6835
    ## 144                                              0.7456              1.2793
    ## 145                                            578.7648            743.5967
    ## 146                                             746.425            809.4292
    ## 147                                             12.4102             11.8503
    ## 148                                             80.1228            129.4888
    ## 149                                            135.0381            178.0993
    ## 150                                              8.5818             15.9502
    ## 151                                              9.0467              7.2136
    ## 152                                               0.382              0.6439
    ## 153                                              3.9862              5.7566
    ## 154                                             83.5999            111.7746
    ## 155                                            359.4321            236.4577
    ## 156                                              2.1092              2.2941
    ## 157                                               0.036               0.087
    ## 158                                              1.7901              4.0698
    ## 159                                              5.9411              3.5744
    ## 160                                              0.0583              0.4161
    ## 161                                                                  0.0411
    ## 162                                             32.6661             28.5041
    ## 163                                              5.3032              9.4537
    ## 164                                              3.5693             11.8655
    ## 165                                             47.5732             21.5291
    ## 166                                             10.4239             12.3496
    ## 167                                              32.102              8.2952
    ## 168                                            117.9721            227.5853
    ## 169                                             14.8452              3.8533
    ## 170                                              2.5032              3.0958
    ## 171                                             44.6068             61.5583
    ## 172                                             11.9275             19.0821
    ## 173                                              5.8702             14.3508
    ## 174                                             41.0239             31.3319
    ## 175                                            118.8858             59.7955
    ## 176                                            101.9877            118.1186
    ## 177                                             864.518           1553.1122
    ## 178                                             36.0506             65.6314
    ## 179                                             13.3407             15.7266
    ## 180                                              6.4595              5.3681
    ## 181                                             32.2038               22.78
    ## 182                                             13.8131              4.3726
    ## 183                                             63.2464             156.055
    ## 184                                              3.7163               3.297
    ## 185                                              1.4095              1.3907
    ## 186                                             32.7031              8.0914
    ## 187                                              5.8547             12.1573
    ## 188                                              1.0491              1.6059
    ## 189                                            590.1368            748.7375
    ## 190                                             745.977            816.1415
    ## 191                                             12.7032             12.1974
    ## 192                                             85.9224            130.6054
    ## 193                                            132.8278            174.3678
    ## 194                                               8.507              16.266
    ## 195                                              8.3738              7.0477
    ## 196                                              0.3595              0.6467
    ## 197                                              4.2422              6.0372
    ## 198                                             84.7129            111.5758
    ## 199                                            367.9582            248.4937
    ## 200                                              1.9099              2.1747
    ## 201                                              0.0342              0.0796
    ## 202                                              1.8155              3.3453
    ## 203                                              5.2208              3.6372
    ## 204                                              0.0576              0.4332
    ## 205                                                                  0.0425
    ## 206                                             31.1779             29.0056
    ## 207                                              5.6345              10.137
    ## 208                                               4.145             11.7345
    ## 209                                             48.3159             22.5968
    ## 210                                             10.7435             13.0355
    ## 211                                             29.6316              8.8001
    ## 212                                             94.6874            200.3937
    ## 213                                             14.0958              4.0979
    ## 214                                              2.6654              3.4476
    ## 215                                             49.8581             64.9633
    ## 216                                             13.0455             19.7197
    ## 217                                              5.8704             14.5386
    ## 218                                             37.2743             29.7903
    ## 219                                            103.0348              51.847
    ## 220                                            101.1599            118.7478
    ## 221                                            873.2486           1599.4744
    ## 222                                              36.935             68.3753
    ## 223                                             13.5961             16.0104
    ## 224                                               6.447               4.841
    ## 225                                             32.6582             22.8936
    ## 226                                              14.664              4.7107
    ## 227                                             65.2588            160.1242
    ## 228                                              3.5568               3.466
    ## 229                                              1.4479              1.4765
    ## 230                                             27.8687              9.8949
    ## 231                                              5.9865             12.3131
    ## 232                                              0.8836               1.575
    ## 233                                            592.0897            758.9638
    ## 234                                            758.1169            829.9044
    ## 235                                             12.1376             11.9938
    ## 236                                             85.2398            132.4626
    ## 237                                            135.4682            178.1451
    ## 238                                              9.2742             16.6175
    ## 239                                              8.4082              7.2655
    ## 240                                              0.3777              0.6284
    ## 241                                              4.3471              6.3044
    ## 242                                             86.5856            114.1006
    ## 243                                             372.848             256.127
    ## 244                                              1.8733              2.0729
    ## 245                                              0.0344              0.0815
    ## 246                                              1.5166              3.8787
    ## 247                                              3.3601              3.4528
    ## 248                                              0.0602              0.4465
    ## 249                                                                  0.0412
    ## 250                                             28.9222             29.5427
    ## 251                                              5.7217             10.7915
    ## 252                                              3.8749             12.1475
    ## 253                                             62.8041             23.3662
    ## 254                                             10.9591             13.7482
    ## 255                                             30.2676              8.0806
    ## 256                                            106.3619             186.111
    ## 257                                             13.6179              4.3489
    ## 258                                              2.6152              3.8243
    ## 259                                             53.6993             65.7047
    ## 260                                             13.6364             19.6342
    ## 261                                              6.0628              14.228
    ## 262                                             42.1963             33.2836
    ## 263                                             91.2831             45.5056
    ## 264                                             97.7686            118.1297
    ## 265                                            876.9045           1634.3804
    ## 266                                             37.0305             70.7721
    ## 267                                             13.8212             17.5693
    ## 268                                              6.7551              4.8158
    ## 269                                             31.9614             23.3429
    ## 270                                             15.1355              4.6401
    ## 271                                             67.3744            164.4099
    ## 272                                              3.5236              3.8188
    ## 273                                              1.5849              1.5273
    ## 274                                             28.1071             11.0206
    ## 275                                              6.1577             12.5655
    ## 276                                              0.9621              1.6399
    ## 277                                            577.8963            776.2903
    ## 278                                            747.6425            854.9273
    ## 279                                             11.9996             11.9803
    ## 280                                             85.4704            134.3385
    ## 281                                             126.404            178.2135
    ## 282                                              9.8296             17.0587
    ## 283                                              8.6996              7.2629
    ## 284                                              0.4181              0.6193
    ## 285                                              4.1822              7.3357
    ## 286                                              84.628            115.6916
    ## 287                                            381.1242            261.8039
    ## 288                                              1.8376              2.0387
    ## 289                                              0.0343              0.0828
    ## 290                                              1.3977              3.9195
    ## 291                                              3.2183              3.5543
    ## 292                                              0.0627              0.4695
    ## 293                                                                  0.0411
    ## 294                                             29.3788             30.2793
    ## 295                                              6.1194             10.9428
    ## 296                                              4.3943             12.7465
    ## 297                                             67.3902             25.8589
    ## 298                                             11.2118             14.4758
    ## 299                                             28.9763              11.394
    ## 300                                            107.2057            178.0441
    ## 301                                             13.1141              4.4031
    ## 302                                              2.4785              4.4625
    ## 303                                             48.6886             70.2603
    ## 304                                             13.6045             19.3728
    ## 305                                               5.839             14.2925
    ## 306                                             52.2784             35.3774
    ## 307                                             81.3916             40.1556
    ## 308                                             98.8531            122.4753
    ## 309                                            913.3106           1679.0061
    ## 310                                              37.162             72.1621
    ## 311                                             15.3605             16.5771
    ## 312                                              6.8022              4.3869
    ## 313                                             31.1548              23.535
    ## 314                                             12.0943              4.5759
    ## 315                                             68.0542            170.6891
    ## 316                                              3.6118              4.1118
    ## 317                                              1.5022              1.5938
    ## 318                                             27.6157             11.7449
    ## 319                                              6.2075             12.7751
    ## 320                                              0.8812               1.747
    ## 321                                            591.6292            786.3196
    ## 322                                            746.8746            868.4705
    ## 323                                              12.275             12.5544
    ## 324                                             86.9443            136.8841
    ## 325                                            129.9854            178.6871
    ## 326                                             10.0363             17.7968
    ## 327                                              7.8808              7.7032
    ## 328                                              0.4904              0.6374
    ## 329                                                4.55              7.7389
    ## 330                                             87.3029            117.6361
    ## 331                                            383.5653            263.8367
    ## 332                                              1.7916              2.0318
    ## 333                                              0.0359              0.0864
    ## 334                                              1.3914              4.2602
    ## 335                                              2.4674              3.7587
    ## 336                                              0.0575               0.481
    ## 337                                                                  0.0393
    ## 338                                             28.3149             30.6754
    ## 339                                              6.5139             11.1717
    ## 340                                              4.2864              12.996
    ## 341                                             63.6164             27.3288
    ## 342                                             12.1953             15.2615
    ## 343                                             23.4947             11.5817
    ## 344                                            106.8788            164.9942
    ## 345                                             12.6998              4.5723
    ## 346                                              2.2196              4.5303
    ## 347                                             55.2229             71.0638
    ## 348                                             13.9172             19.6222
    ## 349                                              5.7348             14.8499
    ## 350                                             57.3066             33.7457
    ## 351                                             75.4515             36.8183
    ## 352                                              97.273            123.9562
    ## 353                                            913.9375           1695.8291
    ## 354                                             37.0765              72.273
    ## 355                                             14.1167             18.7057
    ## 356                                              7.0762               4.085
    ## 357                                             33.6141             24.2234
    ## 358                                             10.8473              5.7841
    ## 359                                             64.3724            173.9776
    ## 360                                              3.7877              4.2989
    ## 361                                              1.3223                1.67
    ## 362                                             24.5095             11.9996
    ## 363                                              6.2408             12.7413
    ## 364                                              0.8267              1.7984
    ## 365                                            581.6826            810.7101
    ## 366                                             718.227            895.9705
    ## 367                                             11.9354             12.7029
    ## 368                                             89.4893              139.13
    ## 369                                            125.4653            181.8051
    ## 370                                             10.0949             19.6363
    ## 371                                               7.069              8.6085
    ## 372                                              0.4678              0.6411
    ## 373                                               4.589              9.1188
    ## 374                                              80.926            121.6449
    ## 375                                            360.1486             262.847
    ## 376                                              1.5706               2.005
    ## 377                                              0.0382              0.0861
    ## 378                                              1.3779              4.3874
    ## 379                                                1.43              3.9215
    ## 380                                              0.0414              0.4884
    ## 381                                                                   0.038
    ## 382                                             28.2701             31.4148
    ## 383                                              6.1714             11.3648
    ## 384                                              4.4363              13.122
    ## 385                                             55.0382             28.7612
    ## 386                                             12.0921             17.0523
    ## 387                                             19.6084             10.9987
    ## 388                                              88.941            193.6968
    ## 389                                             12.0473              4.8544
    ## 390                                              2.2858              3.9046
    ## 391                                             55.6122             77.5706
    ## 392                                             13.2284              19.899
    ## 393                                              5.9175             15.0612
    ## 394                                             55.6842             31.8848
    ## 395                                             72.9468             41.3363
    ## 396                                             96.1879            123.4993
    ## 397                                            875.2609           1731.2572
    ## 398                                             37.8197             73.0972
    ## 399                                             13.3412             18.1653
    ## 400                                              6.9671              3.3648
    ## 401                                             32.1644             24.5747
    ## 402                                              8.8489              6.0128
    ## 403                                             65.2818            178.7833
    ## 404                                              3.5209              4.5811
    ## 405                                              1.3619               1.714
    ## 406                                             22.3184             12.2233
    ## 407                                              6.3314             12.7797
    ## 408                                               0.477               1.679
    ## 409                                             576.068            829.3164
    ## 410                                             696.976            915.2715
    ## 411                                             11.9191             12.9391
    ## 412                                             86.1718            141.5465
    ## 413                                            122.4975            187.0565
    ## 414                                               9.038             19.9767
    ## 415                                              6.4319              9.1097
    ## 416                                              0.4955              0.6718
    ## 417                                              4.8099              9.7313
    ## 418                                             82.7878            123.3827
    ## 419                                            367.4767            265.0025
    ## 420                                               1.422              1.9549
    ## 421                                              0.0376              0.0918
    ## 422                                              1.0609              3.8496
    ## 423                                              1.5405              4.2164
    ## 424                                              0.0546              0.4972
    ## 425                                                                  0.0386
    ## 426                                             27.9111             32.4013
    ## 427                                              5.9964             11.6027
    ## 428                                              4.0058             13.7572
    ## 429                                             47.3205             31.3453
    ## 430                                             12.1839             17.9024
    ## 431                                             17.9166              9.1188
    ## 432                                             97.4476            195.4691
    ## 433                                             11.3984              4.7384
    ## 434                                              2.2967              3.7123
    ## 435                                             58.0453             82.2278
    ## 436                                              12.207             20.1984
    ## 437                                              5.9019             15.6688
    ## 438                                             50.0455              33.804
    ## 439                                             73.1455             35.6164
    ## 440                                             96.6927            124.5135
    ## 441                                            851.0362            1785.937
    ## 442                                             38.8045             75.1308
    ## 443                                             14.0032             18.9655
    ## 444                                              6.7675              3.1326
    ## 445                                             33.3311             24.8685
    ## 446                                              8.4789              5.7394
    ## 447                                              68.785            180.1282
    ## 448                                              3.6319              4.5973
    ## 449                                              1.4004              1.7552
    ## 450                                             27.2853             12.3643
    ## 451                                              6.1434             12.5627
    ## 452                                              0.5754              1.6671
    ## 453                                            580.3127            828.3354
    ## 454                                            706.4371            910.1007
    ## 455                                             11.9392              12.842
    ## 456                                             86.6672            141.1144
    ## 457                                             118.604             183.037
    ## 458                                              9.7847             18.9007
    ## 459                                              6.4163              9.1039
    ## 460                                              0.4495              0.6738
    ## 461                                              5.6417             10.7704
    ## 462                                             83.8108            122.4418
    ## 463                                            379.2492            263.9641
    ## 464                                              1.1606              2.1682
    ## 465                                              0.0343              0.0958
    ## 466                                              0.9907              3.4063
    ## 467                                              1.4504              4.8653
    ## 468                                              0.0575               0.504
    ## 469                                                                  0.0368
    ## 470                                             27.4317             32.7594
    ## 471                                              6.2841             12.1456
    ## 472                                              3.8339             12.9005
    ## 473                                             47.7295               27.55
    ## 474                                             12.7686             19.4595
    ## 475                                             18.7359              9.3963
    ## 476                                             116.059            153.0268
    ## 477                                             11.0252               4.249
    ## 478                                              2.2687              3.8617
    ## 479                                             60.5633             84.5107
    ## 480                                             12.6214             19.8747
    ## 481                                              5.7875             15.9005
    ## 482                                             60.2211             35.5155
    ## 483                                             74.6573             34.7433
    ## 484                                             97.0947            123.7341
    ## 485                                            850.6941           1829.6564
    ## 486                                             38.2427             73.7257
    ## 487                                             13.8578             20.4594
    ## 488                                              6.3093              3.1301
    ## 489                                             32.5116             25.4791
    ## 490                                              8.4559               5.878
    ## 491                                             65.4464            178.2737
    ## 492                                              3.6285              4.6454
    ## 493                                              1.3458              1.8115
    ## 494                                             24.7913             13.2518
    ## 495                                              6.2372             12.5682
    ## 496                                              0.7009              1.9964
    ## 497                                            565.2778            837.7991
    ## 498                                            685.1763            924.5495
    ## 499                                             11.4848             12.9627
    ## 500                                             79.0657            143.8875
    ## 501                                            111.7045            179.1066
    ## 502                                               9.958             19.7908
    ## 503                                              6.9262              9.5758
    ## 504                                              0.4964              0.6848
    ## 505                                              5.5987             11.2965
    ## 506                                             82.1356            124.4774
    ## 507                                             368.883            265.8258
    ## 508                                              1.0734              2.5638
    ## 509                                              0.0346              0.0922
    ## 510                                              0.9679              3.6047
    ## 511                                              1.5885              5.0838
    ## 512                                              0.0494               0.528
    ## 513                                                                   0.037
    ## 514                                             27.1296             33.2523
    ## 515                                              6.6245             12.2256
    ## 516                                              3.9213             13.1987
    ## 517                                             42.6359              27.341
    ## 518                                             11.6119             19.7524
    ## 519                                             19.7261             11.4059
    ## 520                                            117.5307            161.6259
    ## 521                                             11.0153              4.8095
    ## 522                                              2.2105              3.9841
    ## 523                                              64.955             88.2702
    ## 524                                             12.7242             20.0661
    ## 525                                              6.0736             15.6013
    ## 526                                             47.1487             35.5846
    ## 527                                             72.5053             36.2764
    ## 528                                             96.3363            123.7896
    ## 529                                            843.2992           1811.2407
    ## 530                                             39.6913             75.4324
    ## 531                                              14.178             22.3829
    ## 532                                              6.4889              4.1246
    ## 533                                             31.2374             25.7824
    ## 534                                              7.9718              6.1219
    ## 535                                              66.993            180.2448
    ## 536                                               3.451              4.9038
    ## 537                                              1.3401              1.7947
    ## 538                                             23.9554             13.8781
    ## 539                                              5.9432             12.6668
    ## 540                                              0.4853              2.1252
    ## 541                                            551.1125            847.3357
    ## 542                                            665.8567            935.2795
    ## 543                                             11.1714             13.1556
    ## 544                                             79.5764            144.7855
    ## 545                                            110.8306            176.7576
    ## 546                                              9.5049             20.0988
    ## 547                                              6.2552             10.2007
    ## 548                                              0.4976              0.6888
    ## 549                                              5.3224             11.4916
    ## 550                                             78.3264            126.3836
    ## 551                                            375.3945             259.912
    ## 552                                              1.1203              2.6445
    ## 553                                              0.0357              0.0877
    ## 554                                              1.0574              3.7264
    ## 555                                              1.5157              5.2298
    ## 556                                              0.0468              0.5326
    ## 557                                                                  0.0369
    ## 558                                             27.5127             33.9561
    ## 559                                              6.9103             12.7064
    ## 560                                              3.6949              13.034
    ## 561                                             40.0331             26.3956
    ## 562                                             11.0681             20.2576
    ## 563                                             20.2952             11.7233
    ## 564                                            114.3584            167.7818
    ## 565                                                9.94              4.9364
    ## 566                                              2.2438              3.8642
    ## 567                                             66.3783             90.0826
    ## 568                                             12.4946             20.6227
    ## 569                                              5.8134             15.5256
    ## 570                                             58.4072             36.6342
    ## 571                                             71.2195              40.178
    ## 572                                              87.795            126.1452
    ## 573                                            830.1635           1849.5036
    ## 574                                             38.7302             76.9221
    ## 575                                             14.8204             24.2428
    ## 576                                              7.0415              3.9804
    ## 577                                             30.6542             26.3386
    ## 578                                              9.0437              6.7072
    ## 579                                             69.1305            183.4375
    ## 580                                              3.5917               5.293
    ## 581                                              1.3795               1.901
    ## 582                                             23.4386             15.7579
    ## 583                                              5.8891             13.1305
    ## 584                                              0.5552              2.0194
    ## 585                                            563.0384            850.3873
    ## 586                                            677.5457            944.8334
    ## 587                                             11.5376             13.3417
    ## 588                                             82.8982            144.2338
    ## 589                                            107.9981            170.2567
    ## 590                                              9.1888              21.183
    ## 591                                              6.9542             10.6986
    ## 592                                              0.4472              0.7844
    ## 593                                              5.5144             11.6969
    ## 594                                             83.9653            127.2274
    ## 595                                            375.5914            257.0973
    ## 596                                              1.1499               2.794
    ## 597                                              0.0383              0.0873
    ## 598                                              1.0764              3.7746
    ## 599                                              1.4492              5.6676
    ## 600                                              0.0482              0.5339
    ## 601                                                                  0.0365
    ## 602                                             27.8524             34.6181
    ## 603                                              6.2543             13.2497
    ## 604                                              3.9982             13.3971
    ## 605                                             39.0983             28.8577
    ## 606                                             10.6512             20.1411
    ## 607                                             18.8571             12.3518
    ## 608                                            112.9035            176.4219
    ## 609                                             10.7486              5.0466
    ## 610                                              2.1579              4.0035
    ## 611                                             71.1221              94.033
    ## 612                                             12.2191             20.9203
    ## 613                                               5.948             15.6932
    ## 614                                             67.7298             38.4138
    ## 615                                             74.9506             41.1216
    ## 616                                              89.093             125.836
    ## 617                                            828.9392           1836.8673
    ## 618                                             39.8228             80.7589
    ## 619                                             15.2391             24.7528
    ## 620                                              7.8265              4.4288
    ## 621                                             30.6741             27.3337
    ## 622                                              8.3597              7.0069
    ## 623                                             70.0694             188.624
    ## 624                                              3.9958              5.4763
    ## 625                                              1.4095              2.0036
    ## 626                                             23.5913             16.5703
    ## 627                                              5.9386             13.4566
    ## 628                                               0.664              2.0662
    ## 629                                            562.1801            862.2286
    ## 630                                            676.0025             963.866
    ## 631                                             11.6324             13.6912
    ## 632                                             80.4163            144.7112
    ## 633                                            107.0875            169.9722
    ## 634                                              8.5447             21.6199
    ## 635                                              6.0197             11.1873
    ## 636                                              0.4848              0.8379
    ## 637                                              5.9114             12.4188
    ## 638                                             84.7933            129.1413
    ## 639                                            381.1877            256.2372
    ## 640                                              1.1632              2.9349
    ## 641                                              0.0374              0.0861
    ## 642                                              1.1674               4.113
    ## 643                                              1.6212              6.6206
    ## 644                                              0.0593              0.5105
    ## 645                                                                  0.0356
    ## 646                                             27.6934             34.9618
    ## 647                                               5.747              13.557
    ## 648                                              3.7395             13.8773
    ## 649                                             39.8685             32.6334
    ## 650                                             10.9386             20.0957
    ## 651                                             19.1635             13.1534
    ## 652                                            116.9041            183.1822
    ## 653                                             10.0798              5.3045
    ## 654                                              2.2764              4.1535
    ## 655                                             73.5931             97.6135
    ## 656                                             11.8895             21.2563
    ## 657                                              6.0659             15.7688
    ## 658                                             68.6801             41.2279
    ## 659                                             76.0974             44.4295
    ## 660                                             87.9849            127.2678
    ## 661                                            853.1097            1880.413
    ## 662                                             40.8276             80.9254
    ## 663                                             16.5312             25.0426
    ## 664                                              8.1424              4.4882
    ## 665                                             28.8682             26.3536
    ## 666                                              8.0654              7.6971
    ## 667                                             69.0178            192.4707
    ## 668                                              4.0983              5.6812
    ## 669                                              0.9079              2.0432
    ## 670                                             23.3011             17.9442
    ## 671                                              5.6427              13.574
    ## 672                                               0.719              2.1374
    ## 673                                            562.8469            855.1883
    ## 674                                            669.7899            963.3643
    ## 675                                             11.3358             13.7144
    ## 676                                             82.0753            142.9633
    ## 677                                            109.7514            161.7558
    ## 678                                             10.2268             21.6606
    ## 679                                              6.6911             11.8837
    ## 680                                              0.4474              0.8489
    ## 681                                              6.0191             13.1104
    ## 682                                             80.2388            127.4613
    ## 683                                            373.6523            250.5685
    ## 684                                              1.1794              3.0602
    ## 685                                              0.0362              0.0856
    ## 686                                              1.2635              4.3769
    ## 687                                              1.5935               7.016
    ## 688                                              0.0511              0.5665
    ## 689                                                                  0.0341
    ## 690                                             27.4838             34.9573
    ## 691                                              4.9165             13.6176
    ## 692                                              3.4732              13.756
    ## 693                                             33.4946              35.069
    ## 694                                             10.6819             19.8607
    ## 695                                             18.3939             12.7054
    ## 696                                            126.4019            191.8384
    ## 697                                             10.3905              6.2648
    ## 698                                              2.4855              4.4276
    ## 699                                             74.5614             100.848
    ## 700                                             11.3346             21.5069
    ## 701                                              6.1178             15.8294
    ## 702                                             67.7712             41.3066
    ## 703                                             76.0585             44.5679
    ## 704                                             88.4978            128.0557
    ## 705                                            829.8592           1901.4292
    ## 706                                              39.803             81.2855
    ## 707                                             16.2674             23.7379
    ## 708                                              8.3866              5.6822
    ## 709                                             29.0216             25.7714
    ## 710                                              8.1251              8.3203
    ## 711                                             69.7408            191.5854
    ## 712                                              4.1996              5.9921
    ## 713                                              0.8653              2.0319
    ## 714                                             22.6973             18.2801
    ## 715                                              5.7647             13.9606
    ## 716                                              0.7147              2.2962
    ## 717                                            564.4752             855.064
    ## 718                                            670.1704            969.8441
    ## 719                                             11.6148             13.8967
    ## 720                                             84.5162            141.4531
    ## 721                                            113.3534            157.9838
    ## 722                                             10.4394             22.4527
    ## 723                                              5.2822             12.6983
    ## 724                                              0.4325              0.9934
    ## 725                                              5.9103             13.8921
    ## 726                                             79.1868             128.823
    ## 727                                            375.7101            246.9976
    ## 728                                              1.2293              3.3651
    ## 729                                              0.0374              0.0826
    ## 730                                              1.4821              4.6484
    ## 731                                               1.662              6.7061
    ## 732                                               0.046              0.5321
    ## 733                                                                  0.0339
    ## 734                                             27.9513             35.8656
    ## 735                                              4.8708             13.7402
    ## 736                                              3.7923             14.3951
    ## 737                                             33.5235             38.8937
    ## 738                                             10.4734             19.9031
    ## 739                                             17.8756             13.2091
    ## 740                                            127.7197            200.7402
    ## 741                                             11.2605              5.8575
    ## 742                                              2.5935              4.6474
    ## 743                                             72.6183            103.7931
    ## 744                                              11.517             21.3108
    ## 745                                              6.2564             15.9518
    ## 746                                              77.658             44.3941
    ## 747                                             79.5035             45.8744
    ## 748                                             86.1921            128.2287
    ## 749                                            854.7256           1900.5665
    ## 750                                             40.3963             83.3984
    ## 751                                             16.0159             23.8926
    ## 752                                              8.7019              5.6737
    ## 753                                             27.8203             25.6534
    ## 754                                              8.8118              8.1403
    ## 755                                             77.8552             195.067
    ## 756                                              4.2229              6.4182
    ## 757                                              0.8576              2.1696
    ## 758                                             20.4118              19.234
    ## 759                                              5.5688             14.5817
    ## 760                                              1.1837              2.4208
    ## 761                                            558.4767            855.8272
    ## 762                                            663.9425            979.0201
    ## 763                                             11.4333             14.2634
    ## 764                                             82.5188            139.7841
    ## 765                                             118.908            154.5744
    ## 766                                             10.1594             23.1797
    ## 767                                               5.018             13.0893
    ## 768                                              0.4122              1.0283
    ## 769                                              6.1484             14.4818
    ## 770                                             75.9029            128.8363
    ## 771                                            372.7587            241.0471
    ## 772                                              1.2399              3.8055
    ## 773                                              0.0309              0.0867
    ## 774                                              1.4553               5.415
    ## 775                                              1.5502              6.4364
    ## 776                                              0.0515               0.562
    ## 777                                                                  0.0345
    ## 778                                             28.0861             35.5055
    ## 779                                              5.3166             13.8609
    ## 780                                              3.5187             15.2259
    ## 781                                             36.5146             42.9949
    ## 782                                             10.6053             19.4996
    ## 783                                             17.4572             13.6158
    ## 784                                            118.4353            208.4612
    ## 785                                             10.1185               6.517
    ## 786                                               2.346              5.2288
    ## 787                                             69.7193            107.2491
    ## 788                                             10.9584             21.3978
    ## 789                                              6.0899             16.2837
    ## 790                                             80.8223             51.7897
    ## 791                                             82.2388             46.9362
    ## 792                                             85.2219            129.2842
    ## 793                                            850.8128           1908.3971
    ## 794                                             42.4329             85.1369
    ## 795                                             16.1075             22.6041
    ## 796                                              8.7399              6.4009
    ## 797                                             28.3695             27.9753
    ## 798                                              6.3659              8.5248
    ## 799                                             76.4041            193.8602
    ## 800                                              4.2147              6.2618
    ## 801                                              0.8836              2.2604
    ## 802                                             20.6196              19.072
    ## 803                                              5.1234             14.3547
    ## 804                                               1.078              2.3039
    ## 805                                            536.3198            831.3088
    ## 806                                            635.2871            959.3313
    ## 807                                             10.7706             13.5985
    ## 808                                              78.627            133.4684
    ## 809                                            114.5069            154.4474
    ## 810                                              9.4028             22.1249
    ## 811                                              4.9361             12.9874
    ## 812                                              0.3688              0.9729
    ## 813                                              5.6483             13.7445
    ## 814                                             72.4735            123.7761
    ## 815                                             338.047            231.1421
    ## 816                                              1.1271              3.5939
    ## 817                                               0.033              0.0911
    ## 818                                               1.289              5.3946
    ## 819                                              1.4315              6.5709
    ## 820                                              0.0477              0.5603
    ## 821                                                                  0.0329
    ## 822                                             27.6263             35.8056
    ## 823                                               5.359             13.8689
    ## 824                                               3.531             14.6601
    ## 825                                             32.3477             45.2015
    ## 826                                             10.0071             19.2024
    ## 827                                             17.9431             15.2534
    ## 828                                            134.4329            220.3506
    ## 829                                             10.0247              6.7126
    ## 830                                              2.3046              6.1577
    ## 831                                             65.5021            101.7334
    ## 832                                             10.3562             20.8289
    ## 833                                              6.0961             16.6618
    ## 834                                             56.2731             47.8048
    ## 835                                                73.4             46.7158
    ## 836                                             82.4877            123.7382
    ## 837                                            808.1246           1816.3236
    ## 838                                             39.3189             84.6388
    ## 839                                             14.5034             21.7777
    ## 840                                              8.2445              5.3467
    ## 841                                             19.9803             27.2304
    ## 842                                              3.6583              8.1828
    ## 843                                             73.1712            186.3384
    ## 844                                              3.3936              6.2656
    ## 845                                              0.7437              2.2659
    ## 846                                             19.4116             18.4982
    ## 847                                              4.1372             13.5314
    ## 848                                               0.591              2.1264
    ## 849                                            452.8688            810.7054
    ## 850                                             536.786            935.1459
    ## 851                                              8.3947               12.92
    ## 852                                              67.658            131.8817
    ## 853                                            100.7796            153.9521
    ## 854                                               7.461             24.9331
    ## 855                                              3.7259             12.9616
    ## 856                                              0.2642              0.9458
    ## 857                                              4.4297             12.5246
    ## 858                                             55.9029            119.3376
    ## 859                                            321.3964            225.6301
    ## 860                                              0.9028               3.185
    ## 861                                              0.0238               0.085
    ## 862                                              1.0232              4.4214
    ## 863                                              1.3692              6.0151
    ## 864                                              0.0406              0.5744
    ## 865                                                                    0.03
    ## 866                                             25.0275             34.3856
    ## 867                                               5.033             13.6877
    ## 868                                              3.2523             14.4783
    ## 869                                             29.5109             45.6478
    ## 870                                                8.61             19.1522
    ## 871                                             12.8424             15.0791
    ## 872                                            132.3889            199.5274
    ## 873                                              9.5491              6.1725
    ## 874                                              1.9178              5.3254
    ## 875                                             56.6987             96.2744
    ## 876                                              8.6406             20.2203
    ## 877                                              5.7192             16.4731
    ## 878                                             55.4037             47.4397
    ## 879                                             54.6587             40.7095
    ## 880                                              71.435            119.2048
    ## 881                                            728.2231           1749.2494
    ## 882                                              40.914             85.6603
    ## 883                                             15.4597              22.451
    ## 884                                              8.1416              5.2839
    ## 885                                             23.6263             27.1283
    ## 886                                              3.8288              7.9543
    ## 887                                             77.6844            195.5605
    ## 888                                              3.3794              6.0396
    ## 889                                              0.6512              2.3131
    ## 890                                             19.4384             17.4244
    ## 891                                              4.5042             13.4636
    ## 892                                              0.5102              2.2482
    ## 893                                            489.5176            805.3088
    ## 894                                            575.5293            929.8225
    ## 895                                              9.8864             13.4305
    ## 896                                             71.9274            133.6116
    ## 897                                            115.7805            154.9555
    ## 898                                              6.7636             22.0766
    ## 899                                              3.9026             11.8235
    ## 900                                              0.2127              0.9003
    ## 901                                               4.569             11.6028
    ## 902                                             61.3739             118.911
    ## 903                                            345.1189             228.163
    ## 904                                              1.0929              3.2591
    ## 905                                              0.0224              0.0805
    ## 906                                              1.1253              4.5639
    ## 907                                              1.4374              6.3881
    ## 908                                              0.0462              0.5962
    ## 909                                                                  0.0261
    ## 910                                             27.3128             34.9756
    ## 911                                              5.2287             13.8299
    ## 912                                              3.5357             15.1059
    ## 913                                              30.992             48.1137
    ## 914                                              9.2656             18.9296
    ## 915                                              13.208             14.3001
    ## 916                                            138.7353            228.3812
    ## 917                                              9.3164              6.6519
    ## 918                                              1.8996              5.2651
    ## 919                                             59.5663             91.9086
    ## 920                                             10.1548             20.4594
    ## 921                                              5.8732               16.38
    ## 922                                             57.1362             45.1424
    ## 923                                             59.0294             40.0254
    ## 924                                             70.7119            117.6467
    ## 925                                            786.2305           1762.4973
    ## 926                                             40.9202             87.6049
    ## 927                                             14.9976             21.7501
    ## 928                                              8.0576              6.6181
    ## 929                                             23.5649             27.0471
    ## 930                                              3.6686               8.129
    ## 931                                             80.5054              198.58
    ## 932                                              3.1533              5.8887
    ## 933                                              0.5114              2.2498
    ## 934                                             17.9427             17.2554
    ## 935                                              4.5004             13.1113
    ## 936                                              0.7902              2.2599
    ## 937                                            476.5449            795.7342
    ## 938                                            564.0047            920.5533
    ## 939                                              9.6682              13.228
    ## 940                                             68.1725            133.4387
    ## 941                                            115.2913            157.1791
    ## 942                                              5.3126                20.3
    ## 943                                              3.8013             11.3924
    ## 944                                              0.1935              0.8637
    ## 945                                              4.1963             11.2904
    ## 946                                             61.2509            117.8514
    ## 947                                            337.5334            224.7057
    ## 948                                              0.9036              3.1415
    ## 949                                              0.0194              0.0795
    ## 950                                              1.1666              4.4817
    ## 951                                              1.2932               6.849
    ## 952                                               0.073              0.5657
    ## 953                                                                  0.0266
    ## 954                                             25.8251             35.2184
    ## 955                                              5.1014             14.0146
    ## 956                                              3.3442             15.2385
    ## 957                                             31.3007             48.6872
    ## 958                                              8.6072             17.5502
    ## 959                                             15.7612             14.5777
    ## 960                                            145.8986            283.5858
    ## 961                                              9.8362                6.38
    ## 962                                              1.7042              5.6987
    ## 963                                             58.6766             87.3855
    ## 964                                              9.5145             20.0001
    ## 965                                               5.371             16.2058
    ## 966                                             57.5315             47.9458
    ## 967                                             65.4475             36.7369
    ## 968                                             68.7056            116.2258
    ## 969                                            779.1372           1743.6836
    ##                        X.13                     X.14
    ## 1    Other Sectors (MtCO2e)  Energy - Other (MtCO2e)
    ## 2                   15.0561                   1.0652
    ## 3                   14.4062                   0.0359
    ## 4                   14.7921                   0.5909
    ## 5                   27.6718                    0.163
    ## 6                    7.7453                   0.0295
    ## 7                     71.58                   0.1696
    ## 8                    3.7939                         
    ## 9                    0.1841                   0.0011
    ## 10                  33.7024                   1.6275
    ## 11                   9.8718                   0.1286
    ## 12                   2.0084                   0.0444
    ## 13                 656.4187                  22.2545
    ## 14                 817.8742                  28.7362
    ## 15                   7.1756                   1.7878
    ## 16                  100.747                         
    ## 17                 208.0662                  12.1171
    ## 18                   8.5922                         
    ## 19                  22.8946                         
    ## 20                   0.7053                         
    ## 21                   10.518                         
    ## 22                  78.5687                   1.1197
    ## 23                 162.1222                         
    ## 24                   5.7897                         
    ## 25                   0.0889                   0.0024
    ## 26                   5.7282                         
    ## 27                   1.3232                   0.0291
    ## 28                   0.0965                         
    ## 29                   0.0454                         
    ## 30                  38.2907                   0.5766
    ## 31                   2.8953                         
    ## 32                   4.3434                   0.4628
    ## 33                  56.2774                         
    ## 34                   4.6584                   0.1047
    ## 35                   14.728                   2.5142
    ## 36                 264.0559                 282.2682
    ## 37                  10.4902                   2.2328
    ## 38                   1.8105                    0.032
    ## 39                  26.4545                         
    ## 40                  10.9157                   0.8632
    ## 41                  18.0607                   0.2057
    ## 42                  32.5336                         
    ## 43                  95.1062                   0.1069
    ## 44                 110.5585                   5.3371
    ## 45                 564.3225                 202.8689
    ## 46                   15.208                   1.0369
    ## 47                  15.5524                    0.038
    ## 48                  14.7718                   0.5679
    ## 49                  30.5612                   0.1631
    ## 50                   5.5926                   0.0481
    ## 51                  70.9496                   0.1601
    ## 52                   3.1555                         
    ## 53                   0.1841                   0.0009
    ## 54                   26.231                   1.4322
    ## 55                  10.0852                   0.2976
    ## 56                   1.8816                   0.0544
    ## 57                 695.8458                  18.0994
    ## 58                 857.5057                  23.9168
    ## 59                   6.9845                   1.6299
    ## 60                  111.151                         
    ## 61                 208.2197                   8.5906
    ## 62                   8.9004                         
    ## 63                   23.585                         
    ## 64                   0.7229                         
    ## 65                  10.6272                         
    ## 66                  84.3359                   1.2735
    ## 67                 160.8039                         
    ## 68                   5.9569                         
    ## 69                   0.0834                   0.0029
    ## 70                   6.4945                         
    ## 71                   1.5901                   0.0291
    ## 72                   0.1041                         
    ## 73                   0.0421                         
    ## 74                  42.8199                   0.5491
    ## 75                   2.6989                         
    ## 76                   3.9015                   0.4119
    ## 77                  66.5047                         
    ## 78                   4.8738                   0.1137
    ## 79                  13.6049                    2.332
    ## 80                 251.8471                 266.8611
    ## 81                   9.3914                    1.943
    ## 82                   2.1292                   0.0069
    ## 83                   28.766                         
    ## 84                  10.7003                   1.0887
    ## 85                  19.2332                   0.1882
    ## 86                  34.0923                         
    ## 87                  85.0488                   0.9496
    ## 88                  122.052                   4.3341
    ## 89                 579.2475                 215.4354
    ## 90                   15.637                   1.0907
    ## 91                  15.0638                   0.0346
    ## 92                  14.3627                   0.5823
    ## 93                  30.4048                    0.163
    ## 94                   5.3656                   0.0621
    ## 95                  73.1887                   0.1598
    ## 96                   2.6451                         
    ## 97                   0.2179                   0.0009
    ## 98                  23.9713                   1.3422
    ## 99                   9.2353                     0.15
    ## 100                   1.068                   0.0348
    ## 101                664.1964                  15.8211
    ## 102                809.6126                  19.5997
    ## 103                  7.1023                   1.6097
    ## 104                108.9955                         
    ## 105                191.2562                   6.5649
    ## 106                  8.5363                         
    ## 107                 17.4212                         
    ## 108                  0.7865                         
    ## 109                  9.7478                         
    ## 110                 80.8648                     1.36
    ## 111                165.0066                         
    ## 112                  4.2861                         
    ## 113                  0.0842                    0.003
    ## 114                  2.8832                         
    ## 115                  1.4658                   0.0292
    ## 116                  0.1032                         
    ## 117                  0.0404                        0
    ## 118                 39.7035                   0.5638
    ## 119                  2.8752                         
    ## 120                  3.5774                   0.4955
    ## 121                 69.2769                         
    ## 122                  5.0336                   0.0864
    ## 123                  9.9695                   0.6823
    ## 124                235.0792                  33.5534
    ## 125                  8.9646                   1.6548
    ## 126                  1.8886                   0.0014
    ## 127                 29.2796                         
    ## 128                  9.9756                   1.1409
    ## 129                 19.2343                   0.1799
    ## 130                 35.5198                         
    ## 131                 76.0629                   1.5668
    ## 132                118.8745                   4.1266
    ## 133                581.6279                 210.7878
    ## 134                 16.0858                   1.1137
    ## 135                 14.8773                   0.0404
    ## 136                 13.4283                   0.6052
    ## 137                 30.5549                   0.1615
    ## 138                  5.8805                   0.0816
    ## 139                 76.0692                   0.1347
    ## 140                  2.6207                         
    ## 141                  0.2028                   0.0009
    ## 142                 19.6768                    1.297
    ## 143                  9.8765                   0.2466
    ## 144                  0.8719                    0.011
    ## 145                675.4071                  14.4626
    ## 146                818.4802                  17.5492
    ## 147                  6.7122                   1.5169
    ## 148                 106.161                         
    ## 149                199.8622                   5.2387
    ## 150                   8.375                         
    ## 151                 17.5754                         
    ## 152                  0.8165                         
    ## 153                  9.7137                         
    ## 154                 80.6304                   1.5382
    ## 155                 172.858                         
    ## 156                  3.6241                         
    ## 157                  0.0933                   0.0024
    ## 158                  2.4843                         
    ## 159                  1.4479                   0.0256
    ## 160                  0.1036                         
    ## 161                  0.0404                        0
    ## 162                 42.4086                   0.5488
    ## 163                  2.5538                         
    ## 164                   3.534                   0.3723
    ## 165                 74.1037                         
    ## 166                  5.1913                   0.0792
    ## 167                  8.7337                   0.3222
    ## 168                230.2402                  58.4125
    ## 169                  7.4462                   1.3725
    ## 170                  2.3701                   0.0014
    ## 171                 28.4883                         
    ## 172                  9.9422                    0.892
    ## 173                 18.4587                   0.1715
    ## 174                 36.2385                         
    ## 175                 68.3265                   2.0127
    ## 176                122.4207                   4.1816
    ## 177                592.7563                 199.3201
    ## 178                 15.9686                    1.143
    ## 179                 13.5497                   0.0426
    ## 180                 11.1416                   0.6553
    ## 181                 30.1353                   0.1619
    ## 182                  5.4272                   0.0511
    ## 183                 75.7518                   0.1384
    ## 184                  2.7105                         
    ## 185                  0.2031                   0.0006
    ## 186                 18.7249                   1.3061
    ## 187                  9.2444                   0.2609
    ## 188                  0.5753                   0.0112
    ## 189                641.3478                  13.9723
    ## 190                771.6535                  16.6547
    ## 191                  6.2126                    1.775
    ## 192                100.8183                         
    ## 193                189.4183                   4.8074
    ## 194                  8.4247                         
    ## 195                 17.2736                         
    ## 196                   0.799                         
    ## 197                  9.8453                         
    ## 198                 71.4193                   1.5411
    ## 199                167.8027                         
    ## 200                  2.6005                         
    ## 201                  0.0888                   0.0023
    ## 202                  2.2809                         
    ## 203                  1.3902                   0.0239
    ## 204                  0.1018                         
    ## 205                  0.0383                        0
    ## 206                 39.9103                   0.4952
    ## 207                  2.8807                         
    ## 208                  3.6946                   0.5149
    ## 209                 67.1178                         
    ## 210                  5.4422                   0.0853
    ## 211                   7.158                   0.4439
    ## 212                  209.44                  30.2085
    ## 213                  6.5655                   0.8681
    ## 214                  2.2771                   0.0014
    ## 215                  29.515                         
    ## 216                  9.9512                   0.7863
    ## 217                 17.3682                   0.1659
    ## 218                 32.6312                         
    ## 219                 62.0067                   2.3421
    ## 220                117.3484                   3.9988
    ## 221                585.6044                 209.3206
    ## 222                 16.5897                   1.2619
    ## 223                 14.7062                   0.0334
    ## 224                 10.5474                   0.6179
    ## 225                 30.7544                   0.1049
    ## 226                  4.0662                   0.0621
    ## 227                 76.1904                   0.1355
    ## 228                  2.9226                         
    ## 229                   0.206                   0.0007
    ## 230                 17.0863                   1.2109
    ## 231                   9.448                   0.2611
    ## 232                   0.631                   0.0293
    ## 233                652.1637                  12.9967
    ## 234                778.6521                  16.2589
    ## 235                  5.7204                   1.8409
    ## 236                103.4828                         
    ## 237                191.9791                   3.9981
    ## 238                  8.4735                         
    ## 239                 16.4468                         
    ## 240                  0.8081                         
    ## 241                   9.678                         
    ## 242                 78.3004                   1.5113
    ## 243                179.7205                         
    ## 244                  1.8556                   0.0062
    ## 245                  0.0899                   0.0022
    ## 246                  1.9443                         
    ## 247                  1.4024                   0.0114
    ## 248                  0.1082                         
    ## 249                  0.0369                        0
    ## 250                 42.3843                   0.5218
    ## 251                  2.9619                         
    ## 252                  3.6805                   0.4614
    ## 253                 66.7496                         
    ## 254                  5.2976                    0.082
    ## 255                  8.2268                   0.5743
    ## 256                194.4248                  39.3869
    ## 257                  6.7285                   1.3774
    ## 258                  2.4391                   0.0014
    ## 259                 29.4262                         
    ## 260                  9.5548                   0.7141
    ## 261                  18.349                   0.1483
    ## 262                 36.3688                         
    ## 263                 57.4201                    2.617
    ## 264                112.9322                   3.9244
    ## 265                584.6934                 209.7069
    ## 266                 16.9292                   1.3611
    ## 267                 15.8915                   0.0399
    ## 268                 10.8061                   0.8049
    ## 269                 35.9944                    0.089
    ## 270                  4.5738                   0.0798
    ## 271                 81.6249                   0.1374
    ## 272                  3.3475                         
    ## 273                  0.2092                    0.001
    ## 274                 15.6324                   1.1591
    ## 275                 10.1105                   0.1844
    ## 276                  0.7165                   0.0166
    ## 277                716.4248                  11.6981
    ## 278                844.8206                  14.8092
    ## 279                   5.825                    1.889
    ## 280                  111.24                         
    ## 281                 216.929                   3.1188
    ## 282                 10.3865                         
    ## 283                 16.9776                         
    ## 284                  0.8755                         
    ## 285                  9.6844                         
    ## 286                 80.1163                   1.2424
    ## 287                177.7454                         
    ## 288                  1.8824                   0.0033
    ## 289                  0.0903                   0.0023
    ## 290                  1.8381                         
    ## 291                  1.5544                     0.02
    ## 292                  0.1082                         
    ## 293                  0.0388                        0
    ## 294                  47.926                   0.5183
    ## 295                  2.8159                         
    ## 296                  4.4185                    0.412
    ## 297                 68.0249                         
    ## 298                  5.6867                   0.1051
    ## 299                  8.2879                   0.3008
    ## 300                174.6401                  40.8936
    ## 301                  7.0831                   1.5492
    ## 302                  3.0617                   0.0014
    ## 303                 30.5406                         
    ## 304                  9.6508                   0.6556
    ## 305                  19.157                   0.1374
    ## 306                 37.6183                         
    ## 307                  54.905                   2.9209
    ## 308                126.3273                   3.8423
    ## 309                624.2161                 205.8152
    ## 310                 17.1606                   1.3922
    ## 311                 14.3076                    0.038
    ## 312                  10.686                   0.6629
    ## 313                 31.7092                   0.0973
    ## 314                  3.1302                   0.0364
    ## 315                 78.7642                   0.1391
    ## 316                  3.3979                         
    ## 317                  0.2186                   0.0005
    ## 318                 15.7387                   1.2092
    ## 319                  9.2921                   0.1792
    ## 320                  0.6332                   0.0139
    ## 321                668.8134                  11.3141
    ## 322                   793.5                  14.0531
    ## 323                  5.8159                   1.8164
    ## 324                104.2391                         
    ## 325                202.5835                    3.015
    ## 326                 10.6449                         
    ## 327                 16.2872                         
    ## 328                  0.8456                         
    ## 329                  9.3978                         
    ## 330                 77.5224                   1.2948
    ## 331                173.5104                         
    ## 332                  1.6203                   0.0125
    ## 333                  0.0974                   0.0026
    ## 334                  1.6025                         
    ## 335                  1.5107                   0.0243
    ## 336                  0.0997                         
    ## 337                  0.0364                        0
    ## 338                  40.955                   0.4944
    ## 339                  2.8609                         
    ## 340                   3.986                   0.4315
    ## 341                 64.5304                         
    ## 342                  5.6375                   0.1009
    ## 343                 10.9288                   0.0237
    ## 344                168.4398                  38.3292
    ## 345                  6.7642                   1.4414
    ## 346                  3.1327                   0.0014
    ## 347                 30.7441                         
    ## 348                  8.8807                   0.5944
    ## 349                 18.0945                   0.1473
    ## 350                 40.3407                         
    ## 351                 52.9451                   3.1612
    ## 352                117.1271                    3.666
    ## 353                604.0469                 213.0383
    ## 354                 17.2626                   1.2717
    ## 355                 14.2437                   0.0434
    ## 356                  10.614                   0.6895
    ## 357                  32.022                   0.0941
    ## 358                   3.353                   0.0206
    ## 359                  70.938                   0.1061
    ## 360                  3.2517                         
    ## 361                  0.2159                   0.0005
    ## 362                 14.5038                   1.2903
    ## 363                   9.052                   0.2128
    ## 364                  0.5591                   0.0175
    ## 365                669.5054                  10.7646
    ## 366                778.4365                    14.26
    ## 367                  5.8924                   1.9264
    ## 368                108.2178                         
    ## 369                 194.023                   3.0231
    ## 370                 10.9897                         
    ## 371                 14.0072                         
    ## 372                  0.8242                         
    ## 373                  9.8546                         
    ## 374                 80.6059                   1.0951
    ## 375                177.4684                         
    ## 376                   1.425                   0.0033
    ## 377                  0.1059                    0.003
    ## 378                  1.3711                         
    ## 379                  1.5817                   0.0364
    ## 380                  0.0979                         
    ## 381                   0.038                        0
    ## 382                 39.9877                   0.5301
    ## 383                  2.9599                         
    ## 384                  4.0445                    0.368
    ## 385                 53.7377                         
    ## 386                   5.763                   0.1052
    ## 387                 10.2818                   0.7107
    ## 388                159.0344                  14.1966
    ## 389                  6.2152                   1.4497
    ## 390                  3.1634                   0.0027
    ## 391                 31.5009                         
    ## 392                  8.7861                   0.4791
    ## 393                 18.6993                   0.1463
    ## 394                 37.1096                         
    ## 395                 55.1995                   3.6781
    ## 396                118.5606                   3.2256
    ## 397                552.2175                 229.5068
    ## 398                 17.3518                   1.1717
    ## 399                 14.7899                   0.0426
    ## 400                 10.0466                   0.6852
    ## 401                 31.0003                   0.0941
    ## 402                  2.8191                   0.0483
    ## 403                 74.3427                   0.0871
    ## 404                  3.6544                         
    ## 405                  0.2097                   0.0007
    ## 406                 13.4036                   1.2726
    ## 407                   8.908                    0.191
    ## 408                  0.4987                   0.0175
    ## 409                655.7064                    10.27
    ## 410                763.7952                  13.1526
    ## 411                  5.7861                   1.8221
    ## 412                107.2813                         
    ## 413                178.0761                   2.5821
    ## 414                 10.8318                         
    ## 415                 14.8003                         
    ## 416                  0.8095                         
    ## 417                  9.6655                         
    ## 418                 85.4208                   1.1579
    ## 419                185.8666                         
    ## 420                  1.4009                   0.0094
    ## 421                  0.0998                   0.0031
    ## 422                  1.2761                         
    ## 423                  1.5178                    0.047
    ## 424                  0.1029                         
    ## 425                  0.0378                        0
    ## 426                 37.7563                    0.663
    ## 427                  3.0733                         
    ## 428                  4.1397                   0.3982
    ## 429                 55.1677                         
    ## 430                  6.1732                   0.0805
    ## 431                  8.7735                   0.1266
    ## 432                  174.23                  20.9263
    ## 433                  6.2582                   1.4046
    ## 434                  3.3781                   0.0029
    ## 435                 33.0377                         
    ## 436                  8.3489                   0.4159
    ## 437                 18.1811                   0.1321
    ## 438                 35.5836                         
    ## 439                 50.0621                   3.8944
    ## 440                118.6168                   3.1805
    ## 441                574.5705                 236.8617
    ## 442                 17.7575                   1.2052
    ## 443                 13.5848                   0.0418
    ## 444                  9.7106                    0.858
    ## 445                  29.541                   0.0937
    ## 446                  2.3959                   0.0118
    ## 447                 80.6679                   0.1313
    ## 448                  3.5066                         
    ## 449                  0.2344                   0.0006
    ## 450                 13.9551                   1.2622
    ## 451                  8.3713                   0.1184
    ## 452                   0.502                   0.0172
    ## 453                640.3168                   9.4015
    ## 454                739.9229                  12.5051
    ## 455                  5.4326                   1.9479
    ## 456                104.0971                         
    ## 457                171.2951                   2.3085
    ## 458                 11.4554                         
    ## 459                 14.4246                         
    ## 460                  0.7561                         
    ## 461                  9.8201                         
    ## 462                 81.0032                   0.8507
    ## 463                187.2349                         
    ## 464                  1.3015                   0.0001
    ## 465                  0.0928                    0.003
    ## 466                  1.1094                         
    ## 467                  1.7166                   0.0116
    ## 468                  0.1057                         
    ## 469                  0.0363                        0
    ## 470                 38.4742                   0.5952
    ## 471                  3.1577                         
    ## 472                  3.4435                   0.1822
    ## 473                 47.5538                         
    ## 474                  6.4085                   0.0956
    ## 475                  9.0058                   0.2502
    ## 476                182.8292                  11.8991
    ## 477                  5.9651                   1.5585
    ## 478                  3.0528                   0.0031
    ## 479                 34.6707                         
    ## 480                  8.2638                   0.4001
    ## 481                 17.0892                   0.1364
    ## 482                  38.151                         
    ## 483                 45.7686                     3.22
    ## 484                117.7921                   2.9448
    ## 485                607.2711                 230.3328
    ## 486                 18.5701                   1.2194
    ## 487                 14.7271                   0.0424
    ## 488                  8.8276                   0.8238
    ## 489                 31.8115                   0.0958
    ## 490                  2.1987                   0.0156
    ## 491                 77.1243                   0.0817
    ## 492                  3.6987                         
    ## 493                  0.2344                   0.0006
    ## 494                 13.9413                   1.2202
    ## 495                  8.7328                   0.1046
    ## 496                    0.58                   0.0189
    ## 497                688.3975                   8.2484
    ## 498                792.4115                  11.3619
    ## 499                  5.6831                   1.9303
    ## 500                117.2639                         
    ## 501                192.2797                   1.8888
    ## 502                 12.2959                         
    ## 503                 15.6023                         
    ## 504                  0.6711                         
    ## 505                 10.1621                         
    ## 506                 83.8857                   0.3654
    ## 507                190.6673                         
    ## 508                  1.4773                   0.0002
    ## 509                  0.0944                   0.0026
    ## 510                  1.0828                   0.0007
    ## 511                  1.7623                   0.0232
    ## 512                  0.0891                         
    ## 513                  0.0348                        0
    ## 514                 40.7086                   0.4835
    ## 515                    3.22                         
    ## 516                  3.8143                   0.2995
    ## 517                 50.6643                         
    ## 518                  6.7548                   0.0956
    ## 519                  8.3455                   0.4305
    ## 520                190.1197                  13.0784
    ## 521                  6.6729                   1.4236
    ## 522                  3.1254                   0.0033
    ## 523                 35.7736                         
    ## 524                  7.4291                   0.2748
    ## 525                 17.8986                   0.1336
    ## 526                 31.6769                         
    ## 527                 46.4167                   3.0376
    ## 528                120.7606                   2.9506
    ## 529                592.2548                 224.9073
    ## 530                 18.6939                   1.1764
    ## 531                 13.9631                    0.043
    ## 532                  8.1433                   0.5978
    ## 533                 29.9505                   0.0947
    ## 534                  2.6298                   0.0117
    ## 535                 81.0257                   0.0931
    ## 536                  3.7869                         
    ## 537                  0.2598                   0.0006
    ## 538                 12.5153                   1.1659
    ## 539                  8.4185                   0.0964
    ## 540                  0.6618                    0.015
    ## 541                652.3132                   8.3962
    ## 542                753.7479                  11.1111
    ## 543                   5.645                   1.9176
    ## 544                107.7932                         
    ## 545                178.9326                   1.9296
    ## 546                 12.8424                         
    ## 547                 15.9693                         
    ## 548                  0.7352                         
    ## 549                 10.0181                         
    ## 550                 81.2467                    0.322
    ## 551                198.6898                         
    ## 552                  1.4417                   0.0068
    ## 553                   0.103                   0.0028
    ## 554                    1.15                   0.0011
    ## 555                  1.7018                   0.0129
    ## 556                  0.0911                         
    ## 557                  0.0375                        0
    ## 558                 39.6204                   0.5087
    ## 559                  3.3264                         
    ## 560                  3.9992                   0.4581
    ## 561                 49.8568                         
    ## 562                  6.9754                   0.0671
    ## 563                  8.4288                   0.3195
    ## 564                164.1752                  17.0534
    ## 565                  5.4487                   1.1912
    ## 566                  2.9816                   0.0033
    ## 567                 36.7318                         
    ## 568                  6.9055                    0.324
    ## 569                 17.1409                   0.1397
    ## 570                 33.2411                        0
    ## 571                 48.7143                   1.6895
    ## 572                113.2522                   3.0869
    ## 573                 590.171                 222.9164
    ## 574                 19.3266                    1.172
    ## 575                 14.6863                   0.0435
    ## 576                  8.0042                   0.6167
    ## 577                 32.1618                   0.0928
    ## 578                  2.8055                         
    ## 579                 85.1937                   0.0868
    ## 580                  4.0398                         
    ## 581                  0.2717                   0.0005
    ## 582                  13.886                   1.0844
    ## 583                  8.5664                   0.0997
    ## 584                   0.655                   0.0193
    ## 585                664.1425                   8.9559
    ## 586                770.0103                  11.5967
    ## 587                    5.55                   2.0732
    ## 588                110.8577                         
    ## 589                171.2146                   1.9529
    ## 590                 14.7777                         
    ## 591                 17.2089                         
    ## 592                  0.6939                         
    ## 593                 10.2912                         
    ## 594                 88.1529                    0.701
    ## 595                 192.967                         
    ## 596                  1.5647                   0.0064
    ## 597                  0.1093                   0.0035
    ## 598                  1.2044                   0.0035
    ## 599                  1.8143                    0.003
    ## 600                  0.0914                         
    ## 601                  0.0392                        0
    ## 602                 40.7635                   0.4454
    ## 603                  3.5895                         
    ## 604                  4.2867                   0.1743
    ## 605                 49.8677                         
    ## 606                  7.1529                   0.0535
    ## 607                   9.977                   0.4276
    ## 608                 166.617                  21.6173
    ## 609                  5.4328                   1.0958
    ## 610                  2.9026                   0.0033
    ## 611                 38.6423                         
    ## 612                  6.6445                   0.3042
    ## 613                 18.0437                   0.1251
    ## 614                 36.1429                        0
    ## 615                 50.3446                    1.709
    ## 616                114.5346                   3.1934
    ## 617                619.5749                 226.8269
    ## 618                 19.1443                   1.2398
    ## 619                  14.196                   0.0441
    ## 620                  7.9202                   0.6387
    ## 621                 31.3941                   0.0927
    ## 622                  2.3695                   0.0028
    ## 623                 80.9712                   0.0827
    ## 624                  3.9496                         
    ## 625                  0.2433                   0.0005
    ## 626                 13.4397                   1.1317
    ## 627                  8.2338                   0.2492
    ## 628                  0.6777                   0.0283
    ## 629                658.8606                   8.9013
    ## 630                765.5822                  12.3477
    ## 631                   5.428                    1.817
    ## 632                114.1676                         
    ## 633                160.6521                   1.6704
    ## 634                 13.9367                         
    ## 635                 17.7436                         
    ## 636                  0.6666                         
    ## 637                 10.2689                         
    ## 638                 89.8359                   1.1803
    ## 639                 192.436                         
    ## 640                  1.6281                   0.0115
    ## 641                  0.1119                   0.0031
    ## 642                  1.2216                   0.0094
    ## 643                  1.8059                         
    ## 644                  0.1074                         
    ## 645                  0.0371                        0
    ## 646                 40.4764                   0.4493
    ## 647                  3.5366                         
    ## 648                  3.8386                   0.3337
    ## 649                 50.7044                         
    ## 650                  7.3978                   0.0407
    ## 651                 10.7636                   0.7238
    ## 652                161.9739                  24.2171
    ## 653                  4.9849                    1.535
    ## 654                   2.838                   0.0034
    ## 655                  40.051                         
    ## 656                  6.3832                   0.2826
    ## 657                  17.971                   0.1138
    ## 658                  39.871                        0
    ## 659                 51.5177                   1.5853
    ## 660                 116.257                   3.0826
    ## 661                608.1666                 248.7006
    ## 662                 19.4888                   1.2982
    ## 663                 13.7066                   0.0446
    ## 664                  8.3128                   0.6545
    ## 665                 30.9623                   0.0932
    ## 666                  2.3745                         
    ## 667                 78.3594                   0.0899
    ## 668                  3.9791                         
    ## 669                  0.5602                   0.0004
    ## 670                 11.9456                   1.1189
    ## 671                  8.2079                   0.2811
    ## 672                   0.617                   0.0355
    ## 673                652.5683                    8.733
    ## 674                760.6922                  12.6439
    ## 675                  5.1168                   1.7567
    ## 676                113.3573                         
    ## 677                158.0954                   1.7211
    ## 678                 14.5705                         
    ## 679                 17.8262                         
    ## 680                  0.6514                         
    ## 681                 10.7758                         
    ## 682                 94.5329                   1.2914
    ## 683                194.0292                         
    ## 684                  1.6064                   0.0076
    ## 685                  0.1127                   0.0035
    ## 686                  1.2925                   0.0125
    ## 687                  1.7382                         
    ## 688                   0.109                         
    ## 689                  0.0372                        0
    ## 690                 38.0433                   0.3827
    ## 691                  3.5857                         
    ## 692                  3.5104                   0.2922
    ## 693                 53.4075                         
    ## 694                  7.2469                   0.0732
    ## 695                 11.0731                   1.2996
    ## 696                136.8504                  27.9057
    ## 697                  4.7267                   1.4331
    ## 698                  2.5852                   0.0033
    ## 699                 40.6712                         
    ## 700                  5.2753                   0.2264
    ## 701                 18.1871                   0.1236
    ## 702                  42.361                        0
    ## 703                 51.4441                   1.5046
    ## 704                111.9622                   2.8698
    ## 705                 587.296                 233.5425
    ## 706                 19.3542                   1.0902
    ## 707                 13.1679                   0.0451
    ## 708                  8.6906                   0.6781
    ## 709                 29.0367                   0.0933
    ## 710                  2.6256                         
    ## 711                 73.5155                    0.108
    ## 712                  3.7408                         
    ## 713                  0.6817                   0.0128
    ## 714                 13.2545                   1.0981
    ## 715                  7.8626                   0.1375
    ## 716                  0.5638                   0.0322
    ## 717                630.5337                   8.9084
    ## 718                 742.936                  11.7565
    ## 719                  5.0121                   1.8084
    ## 720                106.2449                         
    ## 721                161.3984                   1.5682
    ## 722                 14.4933                         
    ## 723                 16.6605                         
    ## 724                  0.5687                         
    ## 725                 10.4775                         
    ## 726                   88.68                   1.0585
    ## 727                188.5991                         
    ## 728                  1.6574                   0.0089
    ## 729                  0.1162                   0.0037
    ## 730                   1.447                   0.0122
    ## 731                  1.7165                         
    ## 732                  0.1003                         
    ## 733                  0.0347                        0
    ## 734                 38.4257                   0.3885
    ## 735                   3.486                         
    ## 736                   3.512                   0.2806
    ## 737                 55.8949                         
    ## 738                  6.0624                    0.076
    ## 739                 12.7937                   0.6269
    ## 740                139.0267                   30.442
    ## 741                  4.3627                   1.0537
    ## 742                  2.3603                   0.0033
    ## 743                 38.0141                         
    ## 744                  4.6744                    0.245
    ## 745                  17.307                   0.1273
    ## 746                 44.0096                        0
    ## 747                 51.6567                   1.7631
    ## 748                106.9484                   3.4976
    ## 749                535.3394                 232.7871
    ## 750                 19.5622                   1.3926
    ## 751                  11.331                   0.0456
    ## 752                  9.4311                   0.6766
    ## 753                 26.5879                   0.0685
    ## 754                  2.3314                         
    ## 755                 79.3459                   0.1291
    ## 756                  3.3956                         
    ## 757                   0.653                   0.0192
    ## 758                 10.6593                   1.1097
    ## 759                  7.2656                   0.1845
    ## 760                  0.6118                   0.0312
    ## 761                571.8881                    8.816
    ## 762                671.3952                  12.1312
    ## 763                  4.8427                   1.7605
    ## 764                 99.5455                         
    ## 765                128.8976                   1.3041
    ## 766                 13.0835                         
    ## 767                 13.9112                         
    ## 768                  0.5851                         
    ## 769                 10.2907                         
    ## 770                 83.7797                   0.9688
    ## 771                178.5512                         
    ## 772                  1.6661                   0.0028
    ## 773                  0.0886                   0.0034
    ## 774                  1.4026                    0.016
    ## 775                  1.6384                         
    ## 776                  0.1095                         
    ## 777                  0.0296                        0
    ## 778                 35.9443                   0.3782
    ## 779                  3.3795                         
    ## 780                   3.289                   0.2119
    ## 781                 51.6744                         
    ## 782                  5.9066                   0.0733
    ## 783                  10.915                   0.9899
    ## 784                138.4592                  32.9919
    ## 785                  3.6583                    1.143
    ## 786                  1.9146                   0.0035
    ## 787                 38.1777                         
    ## 788                  4.3417                   0.2517
    ## 789                 15.4075                   0.1199
    ## 790                 47.3107                        0
    ## 791                 46.4294                   1.5539
    ## 792                102.0022                   3.7885
    ## 793                 566.134                 218.9718
    ## 794                   19.67                   1.4504
    ## 795                 11.9993                   0.0462
    ## 796                  9.6746                   0.5463
    ## 797                 29.0264                   0.0617
    ## 798                  2.0927                         
    ## 799                 78.1453                   0.1167
    ## 800                  3.5129                         
    ## 801                  0.6057                   0.0415
    ## 802                  11.086                    1.159
    ## 803                  7.0869                   0.1189
    ## 804                  0.6315                    0.011
    ## 805                616.7783                   7.9066
    ## 806                718.5512                   11.309
    ## 807                  4.4293                   1.6791
    ## 808                 105.643                         
    ## 809                155.2207                   1.3238
    ## 810                 12.7967                         
    ## 811                 13.8222                         
    ## 812                  0.5363                         
    ## 813                 11.1526                         
    ## 814                 88.0014                    0.801
    ## 815                168.9885                         
    ## 816                  1.5658                   0.0034
    ## 817                  0.1005                   0.0036
    ## 818                  1.3377                   0.0124
    ## 819                  1.6934                         
    ## 820                   0.117                         
    ## 821                  0.0309                        0
    ## 822                 39.7128                   0.3606
    ## 823                  3.2373                         
    ## 824                  3.1342                   0.2569
    ## 825                 54.1322                         
    ## 826                  5.5106                   0.0857
    ## 827                  9.9991                   0.8638
    ## 828                142.7508                  33.8423
    ## 829                  4.1058                   1.3077
    ## 830                  2.2774                   0.0036
    ## 831                 38.1412                         
    ## 832                   3.901                   0.1543
    ## 833                 16.3849                   0.1146
    ## 834                 65.4194                        0
    ## 835                   46.77                   1.2635
    ## 836                104.0881                   3.2855
    ## 837                576.6577                 218.1098
    ## 838                 19.6741                   1.4214
    ## 839                 10.6811                   0.0467
    ## 840                  8.8201                   0.6032
    ## 841                 28.2406                   0.0564
    ## 842                  1.8376                         
    ## 843                 75.9054                   0.0848
    ## 844                  3.5306                         
    ## 845                  0.6344                    0.016
    ## 846                 10.7706                   1.1432
    ## 847                   7.008                   0.1778
    ## 848                  0.6139                   0.0297
    ## 849                592.3076                   7.8286
    ## 850                693.7448                  10.3307
    ## 851                  4.4537                   1.6243
    ## 852                104.4772                         
    ## 853                142.9638                   1.3534
    ## 854                 10.9623                         
    ## 855                 13.5331                         
    ## 856                  0.6289                         
    ## 857                 10.6678                         
    ## 858                 90.0983                   0.9199
    ## 859                162.0317                         
    ## 860                  1.5819                   0.0053
    ## 861                  0.1002                   0.0037
    ## 862                  1.3229                   0.0114
    ## 863                  1.6769                         
    ## 864                  0.1292                         
    ## 865                  0.0311                        0
    ## 866                 39.8995                   0.3263
    ## 867                  2.9613                         
    ## 868                    3.35                   0.2683
    ## 869                 54.7081                         
    ## 870                   5.324                    0.086
    ## 871                 10.1943                   0.3113
    ## 872                142.5221                  28.1402
    ## 873                  3.9256                   0.9819
    ## 874                  2.1855                   0.0033
    ## 875                 37.1681                         
    ## 876                  3.8105                   0.2441
    ## 877                 15.9141                   0.1163
    ## 878                 70.6693                        0
    ## 879                 43.8595                    0.895
    ## 880                 96.4186                   3.0098
    ## 881                566.1757                 202.6404
    ## 882                 20.0099                   1.5054
    ## 883                 11.9349                   0.0473
    ## 884                  8.8458                   0.6744
    ## 885                  30.369                   0.0481
    ## 886                  2.0129                         
    ## 887                  72.203                   0.0794
    ## 888                  3.5962                         
    ## 889                  0.5799                    0.016
    ## 890                 12.1978                   1.1077
    ## 891                  7.2964                   0.1327
    ## 892                  0.6461                   0.0416
    ## 893                628.0984                   7.4719
    ## 894                741.0658                   9.9149
    ## 895                  4.7937                    1.771
    ## 896                105.1976                         
    ## 897                150.7439                   1.3113
    ## 898                  9.8389                         
    ## 899                 14.2695                         
    ## 900                  0.5561                         
    ## 901                 10.9937                         
    ## 902                 93.6448                   0.6694
    ## 903                163.9636                         
    ## 904                  1.7256                   0.0079
    ## 905                  0.0913                   0.0035
    ## 906                  1.4643                    0.016
    ## 907                  1.7614                         
    ## 908                  0.1239                         
    ## 909                  0.0326                        0
    ## 910                 45.8824                   0.3333
    ## 911                  2.9293                         
    ## 912                  3.6064                   0.2739
    ## 913                 63.0876                         
    ## 914                  5.2292                   0.0863
    ## 915                 10.1922                   0.3131
    ## 916                136.1361                  26.6931
    ## 917                  4.4418                    0.938
    ## 918                  2.2259                   0.0029
    ## 919                 38.9398                         
    ## 920                  3.9223                   0.1761
    ## 921                 17.1101                   0.1209
    ## 922                 67.4109                        0
    ## 923                 45.5874                   1.0037
    ## 924                109.2009                   2.9209
    ## 925                560.8864                 216.9749
    ## 926                  20.451                   1.6011
    ## 927                  10.728                   0.0478
    ## 928                  7.4045                   0.6021
    ## 929                  24.486                   0.0503
    ## 930                  2.2839                         
    ## 931                 77.8865                   0.0691
    ## 932                   3.393                         
    ## 933                  0.6347                   0.0192
    ## 934                 10.5594                    1.116
    ## 935                  6.3595                   0.2166
    ## 936                  0.6406                   0.0202
    ## 937                533.1427                    7.093
    ## 938                635.1066                   9.9126
    ## 939                  4.0472                   1.6547
    ## 940                  90.044                         
    ## 941                 122.726                   1.2157
    ## 942                 11.0896                         
    ## 943                 13.8208                         
    ## 944                  0.5235                         
    ## 945                  9.4829                         
    ## 946                 86.1785                   0.5266
    ## 947                163.1895                         
    ## 948                  1.6254                   0.0072
    ## 949                  0.0802                    0.004
    ## 950                  1.4429                   0.0129
    ## 951                  1.5126                         
    ## 952                  0.1052                         
    ## 953                  0.0268                        0
    ## 954                 37.7293                    0.361
    ## 955                  3.0855                         
    ## 956                  3.2727                   0.2488
    ## 957                 54.9453                         
    ## 958                  4.6969                   0.0776
    ## 959                 10.2031                   0.6035
    ## 960                145.9714                  27.5939
    ## 961                  3.7489                   1.0372
    ## 962                  1.9537                   0.0034
    ## 963                 35.3862                         
    ## 964                  3.6545                   0.1862
    ## 965                 13.9579                   0.1081
    ## 966                  71.136                        0
    ## 967                 47.5328                   1.1763
    ## 968                 86.5632                    2.778
    ## 969                556.5401                   212.44
    ##                                        X.15
    ## 1    Fugitive Emissions from Fuels (MtCO2e)
    ## 2                                    32.389
    ## 3                                    0.3106
    ## 4                                      1.24
    ## 5                                    0.9425
    ## 6                                    2.5492
    ## 7                                   42.3636
    ## 8                                    1.8915
    ## 9                                    0.0009
    ## 10                                   8.9584
    ## 11                                   0.3691
    ## 12                                   0.1811
    ## 13                                  96.9016
    ## 14                                 153.8338
    ## 15                                   0.2308
    ## 16                                   9.7071
    ## 17                                  30.0859
    ## 18                                   1.2573
    ## 19                                   2.4929
    ## 20                                    0.062
    ## 21                                   0.1313
    ## 22                                  10.7806
    ## 23                                   3.0739
    ## 24                                   0.3232
    ## 25                                   0.0003
    ## 26                                   0.1504
    ## 27                                   0.0163
    ## 28                                         
    ## 29                                        0
    ## 30                                   2.8539
    ## 31                                   1.2766
    ## 32                                   3.0404
    ## 33                                  19.0805
    ## 34                                   0.3826
    ## 35                                  21.6516
    ## 36                                 432.4497
    ## 37                                   1.0848
    ## 38                                   0.4591
    ## 39                                   4.1049
    ## 40                                   0.3855
    ## 41                                   0.4724
    ## 42                                   2.1846
    ## 43                                   85.336
    ## 44                                  35.3435
    ## 45                                 324.6209
    ## 46                                   31.876
    ## 47                                   0.3177
    ## 48                                   1.1147
    ## 49                                   0.8169
    ## 50                                   2.1205
    ## 51                                  43.2223
    ## 52                                   1.7906
    ## 53                                   0.0011
    ## 54                                   7.9068
    ## 55                                   0.6986
    ## 56                                   0.1809
    ## 57                                  96.0123
    ## 58                                 145.1717
    ## 59                                   0.2504
    ## 60                                   9.4616
    ## 61                                   29.643
    ## 62                                    1.272
    ## 63                                   2.5211
    ## 64                                   0.0706
    ## 65                                   0.1276
    ## 66                                  10.6631
    ## 67                                   2.8486
    ## 68                                   0.3132
    ## 69                                   0.0004
    ## 70                                   0.1594
    ## 71                                   0.0169
    ## 72                                         
    ## 73                                        0
    ## 74                                   2.8159
    ## 75                                   1.2953
    ## 76                                   2.5255
    ## 77                                   17.265
    ## 78                                   0.3816
    ## 79                                   17.129
    ## 80                                 422.2083
    ## 81                                   1.1298
    ## 82                                   0.4326
    ## 83                                   3.9653
    ## 84                                   0.3316
    ## 85                                   0.4682
    ## 86                                   2.2779
    ## 87                                  80.8991
    ## 88                                  35.2502
    ## 89                                 323.3081
    ## 90                                  33.2978
    ## 91                                   0.3447
    ## 92                                   1.4961
    ## 93                                    0.679
    ## 94                                   2.1903
    ## 95                                  46.7498
    ## 96                                   1.7958
    ## 97                                   0.0011
    ## 98                                   7.5291
    ## 99                                   0.7168
    ## 100                                  0.1057
    ## 101                                 94.4345
    ## 102                                139.9895
    ## 103                                  0.2749
    ## 104                                  9.5858
    ## 105                                 27.7092
    ## 106                                  1.2988
    ## 107                                  2.3458
    ## 108                                  0.0682
    ## 109                                   0.123
    ## 110                                 10.6612
    ## 111                                  2.5845
    ## 112                                    0.29
    ## 113                                  0.0004
    ## 114                                  0.1599
    ## 115                                  0.0176
    ## 116                                        
    ## 117                                       0
    ## 118                                  2.7478
    ## 119                                  1.3086
    ## 120                                  2.9288
    ## 121                                 16.2507
    ## 122                                  0.3949
    ## 123                                 15.0766
    ## 124                                387.4313
    ## 125                                  1.1378
    ## 126                                  0.4681
    ## 127                                  4.1537
    ## 128                                  0.3704
    ## 129                                  0.4321
    ## 130                                  2.3663
    ## 131                                 75.9944
    ## 132                                 35.3568
    ## 133                                319.0477
    ## 134                                 32.5251
    ## 135                                  0.3389
    ## 136                                  1.4133
    ## 137                                  0.7177
    ## 138                                   2.192
    ## 139                                 49.1171
    ## 140                                  2.1306
    ## 141                                  0.0011
    ## 142                                  7.3247
    ## 143                                   0.635
    ## 144                                  0.0534
    ## 145                                 93.7289
    ## 146                                138.3697
    ## 147                                  0.3399
    ## 148                                  9.5064
    ## 149                                 28.5463
    ## 150                                  1.2675
    ## 151                                  2.3835
    ## 152                                   0.086
    ## 153                                  0.1219
    ## 154                                 10.7115
    ## 155                                  2.3926
    ## 156                                    0.28
    ## 157                                  0.0005
    ## 158                                  0.1685
    ## 159                                  0.0183
    ## 160                                        
    ## 161                                       0
    ## 162                                  2.6925
    ## 163                                   1.264
    ## 164                                   3.138
    ## 165                                 16.2295
    ## 166                                  0.4055
    ## 167                                 14.4487
    ## 168                                 374.699
    ## 169                                  1.1278
    ## 170                                  0.4315
    ## 171                                  4.0702
    ## 172                                  0.3928
    ## 173                                  0.4003
    ## 174                                  2.2429
    ## 175                                 70.6404
    ## 176                                 33.9646
    ## 177                                314.2437
    ## 178                                 30.7656
    ## 179                                  0.3462
    ## 180                                  1.2898
    ## 181                                  0.6206
    ## 182                                  2.1514
    ## 183                                 52.5576
    ## 184                                  1.9068
    ## 185                                  0.0013
    ## 186                                  6.9643
    ## 187                                  0.6341
    ## 188                                  0.0762
    ## 189                                 85.5776
    ## 190                                130.3523
    ## 191                                  0.2462
    ## 192                                  9.6894
    ## 193                                 26.0896
    ## 194                                  1.3006
    ## 195                                  2.5592
    ## 196                                  0.0708
    ## 197                                  0.1182
    ## 198                                 10.3667
    ## 199                                  2.0308
    ## 200                                  0.2786
    ## 201                                  0.0005
    ## 202                                  0.1772
    ## 203                                  0.0184
    ## 204                                        
    ## 205                                       0
    ## 206                                  2.7392
    ## 207                                  1.2817
    ## 208                                  3.2962
    ## 209                                 15.9155
    ## 210                                  0.6591
    ## 211                                 15.0532
    ## 212                                348.7147
    ## 213                                  1.1866
    ## 214                                  0.4112
    ## 215                                  4.2887
    ## 216                                  0.3391
    ## 217                                   0.377
    ## 218                                  2.3306
    ## 219                                 63.9707
    ## 220                                 28.1217
    ## 221                                316.7508
    ## 222                                  32.262
    ## 223                                  0.3528
    ## 224                                  1.2366
    ## 225                                  0.6279
    ## 226                                   2.302
    ## 227                                 55.4731
    ## 228                                  2.0427
    ## 229                                  0.0012
    ## 230                                  6.8463
    ## 231                                  0.5217
    ## 232                                  0.0863
    ## 233                                 85.6688
    ## 234                                132.1635
    ## 235                                   0.251
    ## 236                                  9.6145
    ## 237                                 24.2218
    ## 238                                  1.3113
    ## 239                                  2.6247
    ## 240                                   0.083
    ## 241                                  0.1144
    ## 242                                 10.0724
    ## 243                                  1.6609
    ## 244                                  0.2728
    ## 245                                  0.0005
    ## 246                                  0.1919
    ## 247                                   0.021
    ## 248                                        
    ## 249                                       0
    ## 250                                  2.6276
    ## 251                                  1.2558
    ## 252                                  3.2501
    ## 253                                 17.4522
    ## 254                                  0.7885
    ## 255                                 15.0688
    ## 256                                339.1287
    ## 257                                  1.2356
    ## 258                                  0.4128
    ## 259                                   4.067
    ## 260                                  0.3806
    ## 261                                  0.3487
    ## 262                                  2.1598
    ## 263                                 56.9239
    ## 264                                 30.6963
    ## 265                                314.0727
    ## 266                                 31.9194
    ## 267                                  0.2957
    ## 268                                  1.3392
    ## 269                                  0.6193
    ## 270                                  2.2705
    ## 271                                 59.5034
    ## 272                                  2.0113
    ## 273                                  0.0011
    ## 274                                  6.7191
    ## 275                                  0.5645
    ## 276                                  0.0948
    ## 277                                 82.9913
    ## 278                                129.1207
    ## 279                                  0.2376
    ## 280                                  8.6734
    ## 281                                 23.5826
    ## 282                                  1.4136
    ## 283                                  2.6785
    ## 284                                   0.082
    ## 285                                  0.1103
    ## 286                                  9.8215
    ## 287                                    1.61
    ## 288                                  0.2648
    ## 289                                  0.0006
    ## 290                                  0.1993
    ## 291                                   0.023
    ## 292                                        
    ## 293                                       0
    ## 294                                  2.5836
    ## 295                                  1.6283
    ## 296                                  3.6976
    ## 297                                 17.5796
    ## 298                                   0.718
    ## 299                                 14.6696
    ## 300                                337.5314
    ## 301                                   1.256
    ## 302                                  0.3961
    ## 303                                  4.0007
    ## 304                                  0.3677
    ## 305                                  0.3329
    ## 306                                  2.2338
    ## 307                                 55.3631
    ## 308                                 29.9798
    ## 309                                313.9702
    ## 310                                 34.3755
    ## 311                                  0.3466
    ## 312                                  1.4571
    ## 313                                  0.5914
    ## 314                                  2.1705
    ## 315                                 61.2809
    ## 316                                  2.0266
    ## 317                                  0.0015
    ## 318                                  6.5958
    ## 319                                  0.7714
    ## 320                                  0.0927
    ## 321                                 79.0551
    ## 322                                125.3139
    ## 323                                   0.268
    ## 324                                  8.1656
    ## 325                                 23.1951
    ## 326                                  1.3955
    ## 327                                  2.6442
    ## 328                                  0.0647
    ## 329                                  0.1058
    ## 330                                  9.9939
    ## 331                                  1.3254
    ## 332                                  0.2506
    ## 333                                  0.0006
    ## 334                                  0.2148
    ## 335                                  0.0235
    ## 336                                        
    ## 337                                       0
    ## 338                                  2.0371
    ## 339                                  1.6391
    ## 340                                  3.5079
    ## 341                                  18.807
    ## 342                                  0.9001
    ## 343                                 13.7927
    ## 344                                  320.51
    ## 345                                  1.2726
    ## 346                                  0.4162
    ## 347                                  4.1863
    ## 348                                  0.3673
    ## 349                                  0.3145
    ## 350                                  2.3157
    ## 351                                 53.4067
    ## 352                                 26.7074
    ## 353                                314.5664
    ## 354                                 35.4293
    ## 355                                   0.364
    ## 356                                  1.3999
    ## 357                                  0.5786
    ## 358                                  1.8278
    ## 359                                 63.3563
    ## 360                                  1.7822
    ## 361                                  0.0016
    ## 362                                  6.4101
    ## 363                                  0.5898
    ## 364                                   0.088
    ## 365                                  73.811
    ## 366                                115.1335
    ## 367                                  0.2165
    ## 368                                  8.0126
    ## 369                                 20.8608
    ## 370                                  1.4411
    ## 371                                  2.6163
    ## 372                                  0.0848
    ## 373                                  0.0924
    ## 374                                  9.9554
    ## 375                                  1.1808
    ## 376                                  0.2426
    ## 377                                  0.0007
    ## 378                                  0.2382
    ## 379                                  0.0237
    ## 380                                        
    ## 381                                       0
    ## 382                                  1.8475
    ## 383                                  1.5964
    ## 384                                  3.5593
    ## 385                                 15.8656
    ## 386                                  0.9429
    ## 387                                 12.2973
    ## 388                                327.3896
    ## 389                                   1.327
    ## 390                                  0.4079
    ## 391                                  4.1706
    ## 392                                  0.3886
    ## 393                                   0.305
    ## 394                                  2.3502
    ## 395                                 51.2564
    ## 396                                 24.3264
    ## 397                                297.6107
    ## 398                                 33.1386
    ## 399                                  0.3811
    ## 400                                  1.3694
    ## 401                                  0.5889
    ## 402                                  1.4744
    ## 403                                 60.9255
    ## 404                                  1.7459
    ## 405                                  0.0017
    ## 406                                  5.8622
    ## 407                                  1.1795
    ## 408                                  0.0858
    ## 409                                  70.591
    ## 410                                111.6231
    ## 411                                  0.1869
    ## 412                                  7.4169
    ## 413                                 22.3387
    ## 414                                  1.4185
    ## 415                                  2.5383
    ## 416                                  0.1129
    ## 417                                  0.1279
    ## 418                                  9.0454
    ## 419                                  1.1666
    ## 420                                  0.2338
    ## 421                                  0.0007
    ## 422                                  0.2324
    ## 423                                  0.0245
    ## 424                                        
    ## 425                                       0
    ## 426                                  1.5612
    ## 427                                  1.6206
    ## 428                                  4.1541
    ## 429                                 17.1382
    ## 430                                  0.9785
    ## 431                                 11.7916
    ## 432                                332.4505
    ## 433                                  1.2914
    ## 434                                  0.3822
    ## 435                                   3.875
    ## 436                                  0.3917
    ## 437                                  0.3044
    ## 438                                  2.2714
    ## 439                                 51.5941
    ## 440                                 21.0763
    ## 441                                291.4941
    ## 442                                 35.8206
    ## 443                                  0.3752
    ## 444                                  1.4642
    ## 445                                  0.6315
    ## 446                                  1.6532
    ## 447                                 63.0374
    ## 448                                  1.8515
    ## 449                                  0.0017
    ## 450                                  5.1663
    ## 451                                  0.8079
    ## 452                                  0.0972
    ## 453                                 67.9149
    ## 454                                109.8575
    ## 455                                  0.1834
    ## 456                                  7.5843
    ## 457                                 21.3146
    ## 458                                    1.51
    ## 459                                  2.5862
    ## 460                                  0.1549
    ## 461                                  0.0854
    ## 462                                  9.0239
    ## 463                                  1.0793
    ## 464                                  0.2207
    ## 465                                  0.0007
    ## 466                                  0.2489
    ## 467                                  0.0252
    ## 468                                        
    ## 469                                       0
    ## 470                                  1.5214
    ## 471                                  1.6091
    ## 472                                  4.4745
    ## 473                                 17.5282
    ## 474                                  0.8945
    ## 475                                 12.7451
    ## 476                                340.7452
    ## 477                                  1.3207
    ## 478                                  0.3743
    ## 479                                  4.1099
    ## 480                                  0.4487
    ## 481                                  0.2836
    ## 482                                  2.2703
    ## 483                                 50.4475
    ## 484                                 19.3992
    ## 485                                294.7149
    ## 486                                  36.334
    ## 487                                  0.3894
    ## 488                                  1.4717
    ## 489                                  0.6074
    ## 490                                  1.5016
    ## 491                                 63.4413
    ## 492                                  2.0317
    ## 493                                  0.0017
    ## 494                                  4.8477
    ## 495                                   0.861
    ## 496                                   0.105
    ## 497                                 64.1722
    ## 498                                104.9303
    ## 499                                  0.1869
    ## 500                                  6.5946
    ## 501                                 19.6072
    ## 502                                  1.5558
    ## 503                                  2.4412
    ## 504                                  0.1456
    ## 505                                  0.1481
    ## 506                                  8.5211
    ## 507                                  0.8707
    ## 508                                  0.2155
    ## 509                                  0.0008
    ## 510                                  0.2774
    ## 511                                  0.0281
    ## 512                                        
    ## 513                                       0
    ## 514                                  1.4016
    ## 515                                  1.6813
    ## 516                                  4.2733
    ## 517                                 16.7335
    ## 518                                  1.3618
    ## 519                                  13.003
    ## 520                                343.3206
    ## 521                                  1.2852
    ## 522                                  0.3463
    ## 523                                  3.9288
    ## 524                                  0.4175
    ## 525                                  0.2906
    ## 526                                  2.2154
    ## 527                                 48.9426
    ## 528                                  18.563
    ## 529                                296.4651
    ## 530                                 35.1253
    ## 531                                   0.371
    ## 532                                  1.4853
    ## 533                                   0.589
    ## 534                                  1.4613
    ## 535                                 62.7971
    ## 536                                  2.0968
    ## 537                                  0.0016
    ## 538                                  4.5101
    ## 539                                  0.7392
    ## 540                                  0.0876
    ## 541                                 62.8964
    ## 542                                103.2134
    ## 543                                  0.1817
    ## 544                                  6.1535
    ## 545                                 18.8299
    ## 546                                   1.643
    ## 547                                  2.4552
    ## 548                                  0.1494
    ## 549                                  0.0693
    ## 550                                  8.3144
    ## 551                                  0.4375
    ## 552                                  0.2154
    ## 553                                  0.0008
    ## 554                                  0.2721
    ## 555                                  0.0402
    ## 556                                        
    ## 557                                       0
    ## 558                                   2.338
    ## 559                                  1.6089
    ## 560                                  3.6893
    ## 561                                  16.058
    ## 562                                  1.4424
    ## 563                                 13.6217
    ## 564                                356.0153
    ## 565                                  1.2484
    ## 566                                  0.3855
    ## 567                                  4.0247
    ## 568                                  0.3995
    ## 569                                  0.2627
    ## 570                                    2.01
    ## 571                                 47.5591
    ## 572                                 17.7608
    ## 573                                288.7639
    ## 574                                  33.705
    ## 575                                   0.435
    ## 576                                  1.5433
    ## 577                                  0.5284
    ## 578                                  1.5534
    ## 579                                 63.7469
    ## 580                                  2.0587
    ## 581                                  0.0014
    ## 582                                  4.4034
    ## 583                                  0.7638
    ## 584                                  0.0972
    ## 585                                  60.445
    ## 586                                101.4088
    ## 587                                  0.1811
    ## 588                                  5.7036
    ## 589                                 17.7234
    ## 590                                  1.5973
    ## 591                                  2.4714
    ## 592                                  0.1383
    ## 593                                  0.6266
    ## 594                                   8.759
    ## 595                                   0.424
    ## 596                                  0.1784
    ## 597                                  0.0009
    ## 598                                  0.2675
    ## 599                                  0.0407
    ## 600                                        
    ## 601                                       0
    ## 602                                  2.2926
    ## 603                                  1.4799
    ## 604                                   3.653
    ## 605                                 17.0891
    ## 606                                  1.6123
    ## 607                                 13.3088
    ## 608                                369.9863
    ## 609                                  1.1981
    ## 610                                  0.3951
    ## 611                                  3.5864
    ## 612                                  0.4192
    ## 613                                  0.2402
    ## 614                                  1.8487
    ## 615                                 48.1163
    ## 616                                 16.1759
    ## 617                                288.9201
    ## 618                                 34.8148
    ## 619                                  0.4281
    ## 620                                   1.636
    ## 621                                  0.5139
    ## 622                                  1.3241
    ## 623                                 64.2838
    ## 624                                  2.1348
    ## 625                                  0.0004
    ## 626                                  4.2105
    ## 627                                  0.8634
    ## 628                                  0.1137
    ## 629                                 56.1538
    ## 630                                 94.9321
    ## 631                                    0.17
    ## 632                                  5.4145
    ## 633                                 15.2951
    ## 634                                  1.6366
    ## 635                                  2.3095
    ## 636                                  0.1248
    ## 637                                  0.0662
    ## 638                                  7.9026
    ## 639                                  0.4081
    ## 640                                  0.1719
    ## 641                                  0.0009
    ## 642                                  0.2583
    ## 643                                  0.0451
    ## 644                                        
    ## 645                                       0
    ## 646                                  2.2489
    ## 647                                   1.642
    ## 648                                  3.5478
    ## 649                                 16.9222
    ## 650                                  1.3121
    ## 651                                 11.9413
    ## 652                                402.4961
    ## 653                                  1.1361
    ## 654                                  0.3904
    ## 655                                  3.9229
    ## 656                                  0.4112
    ## 657                                   0.242
    ## 658                                  1.7769
    ## 659                                 47.9629
    ## 660                                 15.9231
    ## 661                                285.2545
    ## 662                                 35.8869
    ## 663                                  0.4245
    ## 664                                  1.5923
    ## 665                                  0.5307
    ## 666                                  1.4438
    ## 667                                 63.3843
    ## 668                                  2.1122
    ## 669                                        
    ## 670                                  4.6161
    ## 671                                  0.6535
    ## 672                                  0.1172
    ## 673                                 53.7374
    ## 674                                 92.9302
    ## 675                                  0.1917
    ## 676                                  5.0479
    ## 677                                 14.0016
    ## 678                                   1.619
    ## 679                                  2.2059
    ## 680                                  0.1184
    ## 681                                  0.0569
    ## 682                                  7.8255
    ## 683                                  0.4335
    ## 684                                  0.1668
    ## 685                                   0.001
    ## 686                                  0.2629
    ## 687                                  0.0444
    ## 688                                        
    ## 689                                       0
    ## 690                                  2.4543
    ## 691                                  1.7098
    ## 692                                  3.3298
    ## 693                                 17.2115
    ## 694                                  1.4271
    ## 695                                 11.7881
    ## 696                                387.9368
    ## 697                                  1.0109
    ## 698                                  0.3698
    ## 699                                  3.9445
    ## 700                                  0.4168
    ## 701                                   0.236
    ## 702                                  2.0726
    ## 703                                  46.719
    ## 704                                  15.099
    ## 705                                280.8899
    ## 706                                 36.4278
    ## 707                                  0.4572
    ## 708                                  1.6684
    ## 709                                   0.554
    ## 710                                   1.358
    ## 711                                 64.4521
    ## 712                                  2.2631
    ## 713                                        
    ## 714                                  4.8261
    ## 715                                  0.6701
    ## 716                                  0.1189
    ## 717                                  51.179
    ## 718                                 89.8997
    ## 719                                    0.17
    ## 720                                  5.2789
    ## 721                                 13.2315
    ## 722                                  1.5266
    ## 723                                  2.2206
    ## 724                                  0.1397
    ## 725                                  0.0472
    ## 726                                   7.367
    ## 727                                  0.4443
    ## 728                                  0.1456
    ## 729                                  0.0011
    ## 730                                  0.2611
    ## 731                                  0.0466
    ## 732                                        
    ## 733                                       0
    ## 734                                  2.3586
    ## 735                                  1.8533
    ## 736                                  3.1774
    ## 737                                  17.296
    ## 738                                  1.1213
    ## 739                                  11.144
    ## 740                                398.8606
    ## 741                                   0.983
    ## 742                                  0.3674
    ## 743                                  3.8072
    ## 744                                  0.9597
    ## 745                                  0.2389
    ## 746                                  2.2046
    ## 747                                  46.096
    ## 748                                 13.5832
    ## 749                                291.8542
    ## 750                                 39.9709
    ## 751                                  0.4651
    ## 752                                   1.837
    ## 753                                  0.5364
    ## 754                                  1.4934
    ## 755                                 63.0018
    ## 756                                  2.3701
    ## 757                                        
    ## 758                                  4.4695
    ## 759                                  0.6774
    ## 760                                  0.1186
    ## 761                                 48.8577
    ## 762                                 85.0417
    ## 763                                   0.183
    ## 764                                  4.8769
    ## 765                                 11.6319
    ## 766                                  1.5698
    ## 767                                  2.2133
    ## 768                                  0.1497
    ## 769                                  0.0599
    ## 770                                  7.2082
    ## 771                                  0.4538
    ## 772                                  0.1466
    ## 773                                  0.0011
    ## 774                                  0.2581
    ## 775                                  0.0436
    ## 776                                        
    ## 777                                       0
    ## 778                                   2.233
    ## 779                                  1.8351
    ## 780                                  4.5041
    ## 781                                 16.4082
    ## 782                                  1.1368
    ## 783                                  9.6806
    ## 784                                 407.311
    ## 785                                  1.0284
    ## 786                                  0.3673
    ## 787                                  3.8658
    ## 788                                  0.9975
    ## 789                                  0.2286
    ## 790                                  2.4378
    ## 791                                 45.1026
    ## 792                                 13.3725
    ## 793                                292.5767
    ## 794                                  40.321
    ## 795                                  0.4368
    ## 796                                  1.7529
    ## 797                                  0.5146
    ## 798                                  1.4905
    ## 799                                 61.9849
    ## 800                                  2.1869
    ## 801                                        
    ## 802                                   4.473
    ## 803                                  0.5205
    ## 804                                  0.1135
    ## 805                                 47.7201
    ## 806                                 82.9523
    ## 807                                  0.1889
    ## 808                                  5.0705
    ## 809                                 11.5112
    ## 810                                  1.5589
    ## 811                                  2.2583
    ## 812                                  0.1886
    ## 813                                  0.0516
    ## 814                                  7.3442
    ## 815                                  0.4463
    ## 816                                   0.135
    ## 817                                  0.0011
    ## 818                                   0.262
    ## 819                                  0.0417
    ## 820                                        
    ## 821                                       0
    ## 822                                  2.4471
    ## 823                                  2.1301
    ## 824                                  3.7329
    ## 825                                 15.4683
    ## 826                                  1.4459
    ## 827                                  9.5972
    ## 828                                398.1167
    ## 829                                  1.0681
    ## 830                                  0.3663
    ## 831                                  3.3874
    ## 832                                  1.0071
    ## 833                                  0.2345
    ## 834                                  2.5634
    ## 835                                 44.5202
    ## 836                                 12.1939
    ## 837                                298.8183
    ## 838                                 40.2119
    ## 839                                  0.4988
    ## 840                                  1.4777
    ## 841                                  0.5161
    ## 842                                  1.2906
    ## 843                                 58.8058
    ## 844                                  2.0686
    ## 845                                        
    ## 846                                  4.1483
    ## 847                                  0.3845
    ## 848                                  0.0777
    ## 849                                 46.0807
    ## 850                                 78.5492
    ## 851                                  0.1602
    ## 852                                  4.8426
    ## 853                                 10.3921
    ## 854                                  1.5525
    ## 855                                  2.2972
    ## 856                                  0.1733
    ## 857                                  0.0355
    ## 858                                  7.1372
    ## 859                                  0.4295
    ## 860                                  0.1391
    ## 861                                   0.001
    ## 862                                  0.2692
    ## 863                                  0.0421
    ## 864                                        
    ## 865                                       0
    ## 866                                   2.397
    ## 867                                  2.3492
    ## 868                                  3.0596
    ## 869                                 13.9492
    ## 870                                  1.6594
    ## 871                                    8.79
    ## 872                                367.4127
    ## 873                                  1.1487
    ## 874                                  0.3584
    ## 875                                  3.2525
    ## 876                                  1.0253
    ## 877                                  0.2313
    ## 878                                   2.616
    ## 879                                 41.5814
    ## 880                                 12.1848
    ## 881                                289.2332
    ## 882                                 40.4734
    ## 883                                  0.4791
    ## 884                                  1.7225
    ## 885                                  0.5487
    ## 886                                  1.3987
    ## 887                                 58.5712
    ## 888                                  2.0893
    ## 889                                        
    ## 890                                   4.255
    ## 891                                  0.4698
    ## 892                                  0.0832
    ## 893                                 45.6563
    ## 894                                 78.6276
    ## 895                                  0.1779
    ## 896                                  4.3881
    ## 897                                  9.9863
    ## 898                                  1.3916
    ## 899                                  2.3601
    ## 900                                  0.1931
    ## 901                                  0.0316
    ## 902                                  7.5178
    ## 903                                   0.409
    ## 904                                   0.141
    ## 905                                  0.0011
    ## 906                                  0.2698
    ## 907                                  0.0453
    ## 908                                        
    ## 909                                       0
    ## 910                                   2.739
    ## 911                                  2.5554
    ## 912                                  3.3248
    ## 913                                 14.6084
    ## 914                                  1.6064
    ## 915                                  8.4478
    ## 916                                402.6294
    ## 917                                  1.0482
    ## 918                                  0.3591
    ## 919                                  3.2918
    ## 920                                  1.0014
    ## 921                                  0.2273
    ## 922                                  2.4623
    ## 923                                 42.5697
    ## 924                                 11.9816
    ## 925                                284.4229
    ## 926                                 41.2788
    ## 927                                  0.4731
    ## 928                                  1.4026
    ## 929                                  0.5008
    ## 930                                  1.7621
    ## 931                                 59.7058
    ## 932                                  2.0049
    ## 933                                        
    ## 934                                  4.2172
    ## 935                                   0.367
    ## 936                                  0.0751
    ## 937                                 44.0871
    ## 938                                 78.3466
    ## 939                                  0.1583
    ## 940                                  4.0872
    ## 941                                  9.8513
    ## 942                                  1.4367
    ## 943                                  2.3242
    ## 944                                  0.1821
    ## 945                                  0.0278
    ## 946                                  7.4056
    ## 947                                   0.407
    ## 948                                  0.0954
    ## 949                                   0.001
    ## 950                                  0.2698
    ## 951                                  0.0393
    ## 952                                        
    ## 953                                       0
    ## 954                                  2.3128
    ## 955                                  2.3331
    ## 956                                  3.2583
    ## 957                                 15.5018
    ## 958                                  1.1535
    ## 959                                   8.553
    ## 960                                418.2053
    ## 961                                  1.0967
    ## 962                                  0.3641
    ## 963                                  3.7528
    ## 964                                  0.9974
    ## 965                                  0.2264
    ## 966                                  2.5035
    ## 967                                 42.2793
    ## 968                                 11.5238
    ## 969                                276.9994
