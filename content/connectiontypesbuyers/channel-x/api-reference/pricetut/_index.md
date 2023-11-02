+++
title = "Price Use Cases"
pagetitle = "Price Calculation"
description = "Some examples on how to operate prices"
weight = 3
icon="fa-money"
alwaysopen = false
isDirectory = false
+++
Three price charging types are allowed: *price per Room*, *price per Pax* and *price per Occupancy*. When more than one price is charged for the same day, the newest price will be returned as available price.

**1. [Price per Room](#price-per-room)**\
When a price is charged per Room means that all occupancies allowed in the room will have the same price. If an `AdditionalGuestAmount` are charged for occupancies over the standard occupancy, they will be applied.

**2. [Price per Pax/Guest (Standard Occupancy)](#price-per-pax/guest)**\
When a price is charged per Pax means that the price is for the number of guests specified.

If `NumberOfGuests` is equal or under the standard occupancy, the price returned will have to be the same as the price charged. If `NumberOfGuests` is over the Standard Occupancy, the price is calculated from the Standard Occupancy price and the `AdditionalGuestAmount` charged.

**3. [Price per Occupancy](#price-per-occupancy)**\
When a price is charged per Occupancy means that this price will only be available for the specified occupancy. **No** `AdditionalGuestAmount` are applied.

**Notes**

-   Children and babies are not allowed in BaseByGuestAmts. Children and
    babies are always defined in AdditionalGuestAmounts.
-   The possible Type values in the AdditionalGuestAmount tag are
    Exclusive and not specified.
   > If there is no value specified, then the price is a relative and it is added to the price of the current pax.\
    If the value is "Exclusive", then the price is absolute and will represent the total price of the current pax.

-   If the price is per Room, then all AdditionalGuestAmount must be
    relative.

- If the price is per Occupancy then *@Type* should be **14** and *@Code* should
be specified. 

- An Occupancy is defined by *AdultNumber-ChildNumber-InfantNumber*. E.g.: *@Code* for an occupancy of 2 adults, 1 child and 0 babies would be "2-1-0"


</br>


### Price per Pax/Guest

**Case 1:**\
*Standard occupancy* = 2\
*Room uses:*\
`1-0-0`\
`2-0-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>  
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 2\*(100/2) = 100          |


</br>


**Case 2:**\
*Standard occupancy* = 2\
*Room uses:*\
`1-0-0`\
`2-0-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "1" AmountAfterTax="100.00"/>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="130.00"/>
    </BaseByGuestAmts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | 100              			|
| 2-0-0         | 2\*(130/2) = 130          |


</br>


**Case 3:**\
*Standard occupancy* = 2\
*Room uses:*\
`1-0-0`\
`2-0-0`\
`3-0-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "10"/>
    </AdditionalGuestAmounts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 2\*(100/2) = 100          |
| 3-0-0         | (100/2) + (100/2) + ((100/2) + (40) = 190 |


</br>

**Case 4:**\
*Standard occupancy* = 2\
*Room uses:*\
`1-0-0`\
`2-0-0`\
`3-0-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "10" Type="Exclusive"/>
    </AdditionalGuestAmounts>
``` 
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 2*(100/2) = 100           |
| 3-0-0         | (100/2) + (100/2) + 40 = 140 |


</br>

**Case 5:**\
*Standard occupancy* = 2\
*Room uses:*\
`1-0-0`\
`2-0-0`\
`1-1-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "8" />
    </AdditionalGuestAmounts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 2*(100/2) = 100           |
| 1-1-0         | 2*(100/2) = 100           |

</br>

**Case 5.1:**\
*Standard occupancy* = 2\
*Room uses:*\
`1-0-0`\
`2-0-0`\
`1-0-1`

> NOTE: The same samples with children are valid for babies specifying
AgeQualifyingCode = "7".

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "7" />
    </AdditionalGuestAmounts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 2*(100/2) = 100           |
| 1-1-0         | 2*(100/2) = 100           |


</br>


**Case 6:**\
*Standard occupancy* = 2\
*Room uses:*\
`1-0-0`\
`2-0-0`\
`2-1-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "-40.00" AgeQualifyingCode = "8" />
    </AdditionalGuestAmounts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 2*(100/2) = 100           |
| 2-1-0         | 2*(100/2) + ((100/2) -40) = 60 |


</br>

**Case 7:**\
*Standard occupancy* = 2\
*Room uses:*\
`1-0-0`\
`2-0-0`\
`3-0-0`\
`4-0-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "10.00" AgeQualifyingCode = "10" />
        <AdditionalGuestAmount MaxAdditionalGuests = "2" Amount = "-15.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 2*(100/2) = 100           |
| 3-0-0         | (100/2) + (100/2) + ((100/2) + 10) = 160 |
| 4-0-0         | (100/2) + (100/2) + ((100/2) + 10) + ((100/2) - 15) = 195 |


</br>


**Case 8:**\
*Standard occupancy* = 2\
*Room uses:*\
`1-0-0`\
`2-0-0`\
`3-0-0`\
`4-0-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "-10.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 2*(100/2) = 100           |
| 3-0-0         | (100/2) + (100/2) + ((100/2) -10) = 140 |
| 4-0-0         | (100/2) + (100/2) + ((100/2) -10) + ((100/2) - 10) = 180 |


</br>


**Case 9:**\
*Standard occupancy* = 3\
*Room uses:*\
`1-0-0`\
`2-0-0`\
`3-0-0`\
`4-0-0`\
`5-0-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "3" AmountAfterTax="150.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "-10.00" AgeQualifyingCode = "10" />
        <AdditionalGuestAmount MaxAdditionalGuests = "2" Amount = "15.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 2*(100/2) = 100           |
| 3-0-0         | 3\*(150/3) = 150 |
| 4-0-0         | (150/3) + (150/3) + (150/3) + ((150/3) - 10) = 190 |
| 5-0-0         | (150/3) + (150/3) + (150/3) + ((150/3) - 10) + ((150/3) + 15) = 255|



</br>


### Price per Room

**Case 1:**\
*Standard occupancy* = 2\
*Room uses*\
`1-0-0`\
`2-0-0`\
`1-1-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "25" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | 100              			|
| 2-0-0         | 100                       |
| 1-1-0         | 100                       |

</br>


**Case 2:**\
*Standard occupancy* = 2\
*Room uses*\
`1-0-0`\
`2-0-0`\
`3-0-0`\
`1-1-0`\
`3-1-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "25" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "20.00" AgeQualifyingCode = "10" />
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "10.00" AgeQualifyingCode = "8" />
    </AdditionalGuestAmounts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | 100              			|
| 2-0-0         | 100                       |
| 3-0-0         | 100 + (100/2 + 20) = 170  |
| 1-1-0         | 100                       |
| 3-1-0         | 100 + (100/2 + 20) + (100/2 + 10) = 230 |


</br>


**Case 3:**\
*Standard occupancy* = 3\
*Room uses*\
`1-0-0`\
`2-0-0`\
`3-0-0`\
`4-0-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "25" AmountAfterTax="120.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "20.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | 120              			|
| 2-0-0         | 120                       |
| 3-0-0         | 120                       |
| 4-0-0         | 120 + (120/3 + 20) = 180  |


</br>


### Price per Occupancy

**Case 1:**\
*Room uses*\
`1-0-0`\
`2-0-0`\
`3-0-0`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "14" AmountAfterTax="100.00" Code = "2-0-0"/>
    </BaseByGuestAmts> 
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 1-0-0         | -              			|
| 2-0-0         | 100                       |
| 3-0-0         | -                         |


</br>


**Case 2:**\
*Room uses*\
`2-1-0`\
`2-0-1`

Message:
```xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "14" AmountAfterTax="95.00" Code = "2-1-0"/>
        <BaseByGuestAmt Type = "14" AmountAfterTax="80.00" Code = "2-0-1"/>
    </BaseByGuestAmts>  
```
| **Occupancy** | **Price**			        |
| ------------- | ------------------------- |
| 2-1-0         | 95             			|
| 2-0-1         | 80                        |

{{%custom-children%}}

