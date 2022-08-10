# Ganta Kishore HNI Strategy Logic

```
Bullish = Buy  Call 
Not Bullish = Sell Call
Bearish =  Buy Put 
Not Bearish =  Sell Put 
```


Explained Entire Logic Flow Here with slight brushup, 
All Coders are Welcome to Contribute

```
contact email to commit code : xlnckumar@gmail.com
```
****

```
Spot Price = Current Market Price = At The Money
```

```
CE
Out of the Money = OTM = All Strikes whose Strike Price > Spot Price 
In the Money = ATM = All Strikes whose Strike Price < Spot Price
```

```
PE
Out of the Money = OTM = All Strikes whose Strike Price < Spot Price 
In the Money = ATM = All Strikes whose Strike Price > Spot Price
```

```

CMP =759 = Spot Price

Call Strike		
800	OTM
790	OTM
780	OTM
770	OTM
760	ATM (Nearest Strike Price to CMP)
750	ITM
740	ITM
730	ITM
720	ITM
710	ITM
```

```
CMP =759 = Spot Price
PUT  Strike		
810	ITM
800	ITM
790	ITM
780	ITM
770	ITM
760	ATM
750	OTM
740	OTM
730	OTM
720	OTM
```

Every Strike has a Premium and is Calculated via Intrinsic Value and Time Value.
```
Premium = IV + TV
```


```

CALL IV = Spot - Strike

PUT IV = Strike - Spot

```

```
770 PUT IV = Strike - Spot = 770-759 = 11
```

```
770 CALL IV = Spot - Strike =759 -770 = -11 
IV Cannot be Negative, We Consider Negative IV as Zero.
SO, IV of OTM and ATM is Zero
```

```
Only ITM has Intrinsic Value.
```
```
***SO, OTM premium is only Time Value.
```

```

Contracts = Current Month / Next Month / Far Month

Every Contract Expires on the Last Thursday of the Month. 
If Holiday, Prepones to before day.

The index has weekly options and so weekly expiry.

```


```
1 Month = Current Week / Next Week / Final Expiry
1 Week = Friday to Thursday
```



```
If the price goes above and breaks Two Days High, 
It Signals that the Price is Trying to Rally up.
```


```
Price > 2DHH, Buy Call and Sell Put
Price < 2DHH, Buy Put and Sell Call
```

```
In Options, we look at Index Price, not Futures.
```

```
2DHH = Two Days Higher High
2DLL = Two Days Lower Low
```

```
# Logic
Call Buy = 2DHH + 0.15%
Call Sell = 2DLL - 0.15%
Put Buy = 2DLL - 0.15%
Put Sell = 2DHH + 0.15%
```

```
e.g.:

Day 1 High = 21,016
Day 2 High = 21,079

Day 1 Low = 20,771
Day 2 Low = 20,711

# Mark the Highest High and the Lowest Low.
Highest High = 21,079
Lowest Low = 20,771

# Day 3 is the Day we Trade
# Collect the Spot Data

```



```
Highest High = 21,079
Lowest Low = 20,771
```
 
```
# We will add Little Buffer

Highest High *1.0015% Buffer =21,110.6
Lowest Low * 1.0085% Buffer =20,679.95

```


```
#Note: Use Mround(Cell,0.05) for Rounding in Excel
```


 ```

(4) Final Strike Price =>(We take the Nearest)

Call ATM = 21,100   ==> Mround(21079,100)
Put ATM = 20,700    ==> Mround(20679,100)
 ```
 
 
 ```

(5) Collect Data of Final Strike Price

Call ATM 21100
Day 1 High = 211 ,
Day 2 High  =  189, 
HH = Max(D1H,D2H)=211
Day 1 Low  = 169, 
Day 2 Low = 157,  
LL= Min(D1L,D2L)=157


Put ATM 20700
Day 1 High = 242, 
Day 2 High  =  221, 
HH = 242
Day 1 Low  = 179, 
Day 2 Low = 170, 
LL = 170

```







****
