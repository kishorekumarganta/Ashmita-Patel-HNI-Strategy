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









****
