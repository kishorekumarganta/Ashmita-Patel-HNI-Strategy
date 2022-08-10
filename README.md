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


```
There is no right or wrong in analysis.
```

```
All Indicators are Lagging Indicators.
```

```
A lot of people trade on Support and Resistance.

Price will not go below Support Point.
Price will not go Above Resistance Point.
```

```
Always trade in Markets with Absolute Clarity.
```

```
we can not predict the markets. No body can.
14-15L Cr a Day Almost our Market Turn Over.
we cannot predict how this 10 L Cr Behavior is in Tomorrow's market.
```

```
One Day Before Prepare for all three Directions 
= > Up, Down, Sideways
I will not trade in Range-Bound Market.
```

```
(6) Calculations

B.O. = Buy Option
S.O. = Sell Option
MSL= Monetary Stop Loss
TSL = Technical Stop Loss
```


```
Call Buy (Long)
Expiry= May 2022 
Strike= 21100
Entry = B.O. =  2DHH + 10% =211*(1+10%)  = 232.1
Our Entry = 
Target = S.O. =  Entry +60% = 232.1*(1+60%)= 371.36
MSL= Entry - 60% = 232.1*(1-60%) = 92.84
TSL = 2DLL- 10% = 157*(1-10%)= 141.3
Stop Loss = S.O. = Max(Msl,Tsl) = 141.3
up==> (Underlying Price = up)  ==> (Premium Price = up)
```

```
Call Sell (Short)
Expiry= May 2022
Strike= 21100
Entry = S.O. = 2DLL-10% = 141.3
Our Entry = 
Target = B.O.  = Entry - 60% = 56.52
MSL= Entry + 60% = 226.08
TSL = 2DHH+10% = 232.10
Stop Loss= B.O.  = Min(Msl,Tsl) = 226.08
No up ==> Underlying Price = Down ==> Premium Price = Down
```

```
Put Buy (Long)
Expiry= May 2022
Strike= 20700
Entry = B.O. =  2DHH + 10% = 266.2
Our Entry = 
Target = S.O. =  Entry +60% = 425.92
MSL= Entry - 60% = 106.48
TSL = 2DLL- 10% = 153
Stop Loss= S.O. = Max(Msl,Tsl) = 153
Down ==> Underlying Price = Down  ==> Premium Price = Down
```

```
Put Sell (Short)
Expiry= May 2022
Strike= 20700
Entry = S.O. = 2DLL-10% = 153
Our Entry = 
Target = B.O.  = Entry - 60% = 61.2
MSL= Entry + 60% = 244.8
TSL = 2DHH+10% = 266.2
Stop Loss= B.O.  = Min(Msl,Tsl) = 244.8
No Down ==> Underlying Price = up ==>  Premium Price = Down
```


****
## Only Bank Nifty POSITIONAL System:

```
DATA:

2 DAYS' HIGHEST HIGH = 23423
2 DAYS LOWEST LOW =  22977
( BUFFER = 0.15% )  TO AVOID A REVERSAL TRAP.

STOP LOSS IS 1.50% i.e. ONE AND HALF PERCENT

MSL =  MONETARY STOP LOSS
TSL =  TECHNICAL STOP LOSS
FSL =  FINAL STOP LOSS

```



```
BUY  SIDE:
2 LOTS BUY AT TRIGGER PRICE 
2 Lot Because we trail one Lot

BUY  ENTRY = 2 DAYS HIGHEST HIGH + 0.15% = 23458.1
For Excel, Use  =high*1.0015

TARGET = ENTRY PRICE + 1.5% =  23809.9
For Excel, Use  =high*1.015

MONETARY STOP LOSS =MSL = ENTRY - 1.5% = 20468.42
For Excel, Use  =ENTRY*0.98

TECHNICAL STOP LOSS=TSL = 2DLL - 0.15% = 19660.47
For Excel, Use  =2DLL*0.9985


FINAL STOP LOSS =FSL
FSL IS HIGHER OF MSL AND TSL i.e. WHICH IS CLOSER TO ENTRY.
For Excel, Use  =MAX(MSL,TSL)
FSL = 20468.42
```



```

SHORT SELL SIDE:

SHORT SELL ENTRY = 2 DAYS LOWEST LOW - 0.15% = 22942.5
For Excel, Use  =LOW * 0.9985

TARGET = ENTRY PRICE - 1.5% =  22598.3
For Excel, Use  =LOW * 0.985

MONETARY STOP LOSS =MSL = ENTRY + 1.5% = 19955.37
For Excel, Use  =ENTRY * 1.015

TECHNICAL STOP LOSS=TSL = 2DHH + 0.15% = 20780.1
For Excel, Use  =2DHH *  1.015

FINAL STOP LOSS =FSL
FSL IS LOWER OF MSL AND TSL i.e. WHICH IS FAR TO ENTRY.
For Excel, Use  =MIN(MSL,TSL)
FSL =  19955.37
```

```
AFTER DECIMAL,UP TO ONE DIGIT I'LL GO.
I ONLY BUY STOCK WHEN IT IS GOING UP.
I ONLY SHORT STOCK WHEN IT IS GOING DOWN.
```
```
Image 1
https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/1.png?raw=true
```


```
Image 2
https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/2.png
```


```
P= Price
TP = Trigger Price
Entry and SL will always come in TP with me.
Target will always come in Price.
```


```
Image 3
https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/3.png

```


```
In step 4, Intraday buffer is 0.10
Historical Data related to Strike get from the NSE site
```


```

Image 4:

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/4.png

```

```

Image 5:

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/5.png

```

```
Image 6:
https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/6.png
```

```
Logic: Whenever 2Days High Crossed, There is a high probability that it goes above. Also, I can say that it will not go below 2 Days Low.

Similarly, whenever 2 Days Low Crossed, There is a high probability that it will go below. Also, I can say that it will not go above 2 Days High.
```



```
Image 7 :

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/7.png
```

```
Image 8:

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/8.png
```


```

We need both Current and Next Week's Data.

we trade sell on Next Week because of more time value.
```


```
Image 9 :

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/9.png
```

```
Image 10 :

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/10.png
```


```
Image 11 :

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/11.png
```


```

For Intraday, Everything will be the current week.

Every Day We place eight orders like the below:
```


```
Image 12 :

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/12.png
```

```
Image 13 :

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/13.png
```

```
Image 14 :

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/13.png
```

```
Image 15 :

https://github.com/kishorekumarganta/Ganta-Kishore-HNI-Strategy/blob/main/15.png

```


```
High Spot with Buffer  we get by =Mround(B3*(1+$C$1),0.05)

Low Spot with Buffer  we get by =Mround(B3*(1-$C$1),0.05)

For Strikes for Nearest Hundred use  =Mround(Spotwithbuffer,100)

```






****


