+++
title = "Messages"
pagetitle = "Messages"
description = "Notif messages"
weight = 1
icon="fa-file-code-o"
alwaysopen = false
isDirectory = false
+++

# Global Details

In this section, you will find some details to take into account to develop ChannelX successfully and the specification of the methods to be developed.

* [Protocol and headers](#protocol-and-Headers)
* [Timeout and responses](#timeout-and-responses)
* [Error Handling](#error-handling)
* [Requests](#requests)


## Protocol and headers

All requests are expected to be standard HTTP POST requests in which the POST body is the request XML in a SOAP envelope like the [following](#soap-envelope-example) and the **Content-Type** header is set to ``"text/xml;charset=UTF-8"``.

By default, the requests are not compressed, but you can choose the following compression `gzip`, `deflate` and `br`, let us know if you want to receive the requests compressed.


### SOAPAction header

All requests come with a **SOAPAction** header corresponding to the transmitted message. The possible SOAP actions are:

 * http://schemas.xmltravelgate.com/hubpush/provider/2012/10/IProviderGen/HotelAvailNotif 
 * http://schemas.xmltravelgate.com/hubpush/provider/2012/10/IProviderGen/HotelRatePlanNotif
 * http://schemas.xmltravelgate.com/hubpush/provider/2012/10/IProviderGen/HotelRatePlanInventoryNotif 


### SOAP Envelope example

```xml
<s:Envelope xmlns:s = "http://schemas.xmlsoap.org/soap/envelope/" xmlns:u = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
    <s:Header>
    <o:Security s:mustUnderstand = "1" xmlns:o = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
        <o:UsernameToken u:Id = "uuid-d740d5c0-ebc5-45c7-bd74-62b20c963d85-7">
            <o:Username> username  </o:Username>
            <o:Password Type = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0#PasswordText"> password </o:Password>
        </o:UsernameToken>
    </o:Security>
    </s:Header>
    <s:Body xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd = "http://www.w3.org/2001/XMLSchema">
        The content request
    </s:Body>
</s:Envelope>
```

### Authentication

Requests come with a *Base-64* encoded authentication. Credentials may be found in **Authorization** header tag, with value **Basic (encoded credentials)** as follows:

`Authorization: Basic aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj1RWWg2bVlJSkcyWQ==`

The user and password to be set and the endpoint that receives the requests have to be informed to us in order to configure your ChannelX.  


## Timeout and responses

ChannelX waits for **5000ms** an HTTP 200 OK and a non-null response with a *Success* element in the response, or if you have a controlled error you can send us an error response.


### Response messages

Each request should provide a response for the same type of element that has been sent. For example, if a *HotelRatePlanNotif* request is received, a *HotelRatePlanNotif* response should be sent and so on. [Here](#requests) you have the specification of the possible requests.

| **Possible combination Elements regarding Request** |
| :---------------------------- |
| HotelAvailNotifResponse / HotelAvailNotifResult  |
| HotelRatePlanNotifResponse / HotelRatePlanNotifResult  |
| HotelRatePlanInventoryNotifResponse / HotelRatePlanInventoryNotifResult  |

<br/>

**Success**

For all successful requests, a *Success* element is expected to be returned in the response. For a *HotelAvailNotif* request it should be like the following:

```xml
<HotelAvailNotifResponse xmlns = "http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
    <HotelAvailNotifResult>
        <Success xmlns = "http://www.opentravel.org/OTA/2003/05"/>
    </HotelAvailNotifResult>
</HotelAvailNotifResponse>
```

<br/>

**Error**

On the other hand, when request provides any error, the response should be like:

```xml
<HotelAvailNotifResponse xmlns = "http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
    <HotelAvailNotifResult>
        <Errors xmlns = "http://www.opentravel.org/OTA/2003/05">
            <Error ShortText = "AvailStatusMessages not found" Code = "2"/>
        </Errors>
    </HotelAvailNotifResult>
</HotelAvailNotifResponse>
```

| **Element**	                  | **Rel** | **Type** | **Description**					                                             |
| :---------------------------- | :-----: | :------: | --------------------------------------------------------------------- |
| Errors | 1 | | |
| Error | 1..n | | Displays error information that has occurred in the system |
| @ShortText | 1 | String | Brief description of the error |
| @Code | 1 | Integer | Check [General Details > Error Table](https://docs.travelgatex.com/connectiontypesbuyers/channel-x/api-reference/codelists/) |


## Error Handling

First of all, if your system does not respond to us on time or it returns an error response, in order to get closer to real-time, we do not retry the messages again.

Based on this real-time principle, we recommend that your system processes our requests within 100ms on average.


## Requests

The requests from ChannelX have a **5MB maximum size**, without including the headers and the SOAP envelope. In this section, you have the specification of these requests.


### Acronyms

On the the following specification you can find the following acronyms:

BR = Only used for: 'Basic Rates'\
DV = Only used for: 'Derived Rates'\
OF = Only used for: 'Offers'\
N = Names allowed for a specific element


### HotelRatePlanInventoryNotif

The ``HotelRatePlanInventoryNotif`` message contains information about the inventory setup information that should be followed by the structure: Hotel > Rate > Room.

```xml
<HotelRatePlanInventoryNotif xmlns = "http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
    <request PrimaryLangID = "ES" Version = "0">
        <RatePlans HotelCode = "1" HotelStatusType = "Active" xmlns = "http://www.opentravel.org/OTA/2003/05">
            <RatePlan Duration = "0" CurrencyCode = "EUR" RatePlanCode = "BAR" FreeChild = "true" FreeBaby = "false" RatePlanStatusType = "Active" RatePlanNotifType = "New" YieldableIndicator="true" RatePlanType = "0">
                <Commission Percent="10"/>
                <BookingRules>
                    <BookingRule>
                        <CancelPenalties>
                            <CancelPenalty>
                                <Deadline OffsetTimeUnit = "Day" OffsetUnitMultiplier = "20" OffsetDropTime = "BeforeArrival"/>
                                <AmountPercent NmbrOfNights = "3"/>
                            </CancelPenalty>
                            <CancelPenalty Start = "2018-03-01" End = "2018-03-06">
                                <Deadline OffsetTimeUnit = "Day" OffsetUnitMultiplier = "10" OffsetDropTime = "BeforeArrival"/>
                                <AmountPercent Amount = "10"/>
                            </CancelPenalty>
                            <CancelPenalty NonRefundable = "true" Start = "2018-03-13" End = "2018-03-15"/>
                        </CancelPenalties>
                    </BookingRule>
                    <BookingRule>
                        <Viewerships>
                            <Viewership>
                                <LocationCodes LocationCodesInclusive = "true">
                                    <LocationCode CountryCode = "ES"/>
                                </LocationCodes>
                            </Viewership>
                            <Viewership>
                                <LocationCodes LocationCodesInclusive = "false"/>
                            </Viewership>
                        </Viewerships>
                    </BookingRule>
                </BookingRules>
                <Rates>
                    <Rate>
                        <AdditionalGuestAmounts>
                            <AdditionalGuestAmount AgeQualifyingCode = "8" MaxAge = "12"/>
                            <AdditionalGuestAmount AgeQualifyingCode = "7" MaxAge = "2"/>
                        </AdditionalGuestAmounts>
                        <PaymentPolicies>
                            <GuaranteePayment PaymentCode = "BookingDatePayment">
                                <AcceptedPayments>
                                    <AcceptedPayment>
                                        <PaymentCard CardCode = "VI"/>
                                    </AcceptedPayment>
                                    <AcceptedPayment>
                                        <PaymentCard CardCode = "AX"/>
                                    </AcceptedPayment>
                                </AcceptedPayments>
                            </GuaranteePayment>
                        </PaymentPolicies>
                        <MealsIncluded MealPlanCodes = "14"/>
                    </Rate>
                </Rates>
                <SellableProducts>
                    <SellableProduct InvCode = "STD" InvType = "ROOM" InvStatusType = "Active" InvNotifType = "New">
                        <GuestRoom>
                            <Quantities StandardNumBeds = "2"/>
                            <Occupancy MinOccupancy = "2" MaxOccupancy = "2" AgeQualifyingCode = "10"/>
                            <Room RoomTypeCode = "STD" RoomID = "1"/>
                            <Description>
                                <Text>Standard</Text>
                            </Description>
                        </GuestRoom>
                    </SellableProduct>
                    <SellableProduct InvCode = "STD" InvType = "ROOM" InvStatusType = "Active" InvNotifType = "New">
                        <GuestRoom>
                            <Quantities StandardNumBeds = "2"/>
                            <Occupancy MinOccupancy = "1" MaxOccupancy = "1" AgeQualifyingCode = "10"/>
                            <Occupancy MinOccupancy = "1" MaxOccupancy = "1" AgeQualifyingCode = "8"/>
                            <Occupancy MinOccupancy = "1" MaxOccupancy = "1" AgeQualifyingCode = "7"/>
                            <Room RoomTypeCode = "STD" RoomID = "1"/>
                            <Description>
                                <Text>Standard</Text>
                            </Description>
                        </GuestRoom>
                    </SellableProduct>
                </SellableProducts>
                <Taxes>
                    <Tax Amount = "20" ChargeFrequency = "true">
                        <TaxDescription>
                            <Text>city</Text>
                        </TaxDescription>
                    </Tax>
                </Taxes>
                <AdditionalDetails>
                    <AdditionalDetail Code = "REP" Type = "39">
                        <DetailDescription>
                            <Text>Repsol</Text>
                        </DetailDescription>
                    </AdditionalDetail>
                </AdditionalDetails>
                <Description>
                    <Text>bb</Text>
                </Description>
            </RatePlan>
        </RatePlans>
        <TPA_Extensions xmlns = "http://www.opentravel.org/OTA/2003/05">
            <Attribute key = "HotelNotifType" value = "New"/>
        </TPA_Extensions>
    </request>
</HotelRatePlanInventoryNotif>
```
<br/>

**Example for Derived RatePlan**
```xml
<HotelRatePlanInventoryNotif xmlns = "http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
    <request PrimaryLangID = "ES" Version = "0"/>
    <RatePlans HotelCode = "1" HotelStatusType = "Active" xmlns = "http://www.opentravel.org/OTA/2003/05">
        <RatePlan BaseRatePlanCode = "BAR" RatePlanStatusType = "Active" RatePlanCode = "DERIVED" RateReturn = "false">
            <RatePlanInclusionsType>
                <RatePlanInclusionDescription>
                    <Name>BaseMealPlanSupplement</Name>
                </RatePlanInclusionDescription>
            </RatePlanInclusionsType>
            <Description>
                <Text>Derived Rate</Text>
            </Description>
        </RatePlan>
    </RatePlans>
</HotelRatePlanInventoryNotif>
```

<br/>

**Example for Offers**
```xml
<HotelRatePlanInventoryNotif xmlns = "http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
    <request PrimaryLangID = "ES" Version = "0"/>
    <RatePlans HotelCode = "1" HotelStatusType = "Active" xmlns = "http://www.opentravel.org/OTA/2003/05">
        <RatePlan BaseRatePlanCode = "BAR" RatePlanStatusType = "Active" RatePlanCode = "DERIVED" RateReturn = "false">
            <Offers>
                <Offer OfferCode = "offer" OfferStatusType = "Active" OfferNotifType = "New">
                    <OfferRules>
                        <OfferRule>
                            <LengthsOfStay ArrivalDateBased = "false">
                                <LengthOfStay Time = "2" MinMaxMessageType = "MinLOS"/>
                                <LengthOfStay Time = "6" MinMaxMessageType = "MaxLOS"/>
                            </LengthsOfStay>
                            <DOW_Restrictions>
                                <AvailableDaysOfWeek Mon = "true" Tue = "true" Weds = "true" Thur = "true" Fri = "true" Sat = "true" Sun = "true"/>
                            </DOW_Restrictions>
                            <Inventories>
                                <Inventory InvCode = "1BDAPT"/>
                            </Inventories>
                        </OfferRule>
                    </OfferRules>
                    <Discount NightsDiscounted = "1" DiscountPattern = "Last"/>
                    <OfferDescription>
                        <Text>Offer Test</Text>
                    </OfferDescription>
                </Offer>
            </Offers>
        </RatePlan>
    </RatePlans>
</HotelRatePlanInventoryNotif>
```

| **Element**	                  | **Rel** | **Type** | **Description**					                                             |
| :---------------------------- | :-----: | :------: | --------------------------------------------------------------------- |
| HotelRatePlanInventoryNotif  	| 1 	    |		       | 						                                                 |
| ../request                 	    | 1 	    |		       |          						                                                 |
| ../RatePlans			   	            | 1   	  |		       |							                                                         |
| @HotelCode				            | 1	      | String	 |                                                                       |
| @HotelStatusType			        | 1	      | String	 | *N*: Active, Deactivated				                                         |
| ../RatePlan  		                | 0..n	  |		       |                        				                                       |
| @FreeChild				          | 1	      | Boolean	 | Indicates if the child is free at that rate. Find here the [price calculation](https://docs.travelgatex.com/inventory/extranet/faq/free-children-baby/)    |
| @FreeBaby				          | 1	      | Boolean	 | Indicates if the baby is free at that rate. Find here the [price calculation](https://docs.travelgatex.com/inventory/extranet/faq/free-children-baby/) |
| @RatePlanCode				          | 1	      | String	 | Rate code						                                                 |
| @BaseRatePlanCode			        | 0..1	  | String	 | *DV*. Rate code of the base RatePlan                                  |
| @RateReturn			              | 0..1	  | String	 | -                                                                     |
| @RatePlanNotifType			      | 0..1	  | String	 | *N*: New, Delta, Remove                                                  |
| @RatePlanStatusType			      | 1		    | String   | *N*: Active, Deactivated				                                         |
| @CurrencyCode				          | 0..1	  | String	 | *BR*. ISO Currency (EUR)	                                             |
| @YieldableIndicator			    | 0..1	 | Boolean  | Used to indicate the rate plan is subject to yield management logic. When false, the rate plan is not yieldable. When true or it's not returned, the rate plan is yieldable.|
| @Start      				          | 0..1 	  | Date	   | Booking Start Date for which the rate will be available.               |
| @End        				          | 0..1	  | Date     | Booking Start Date for which the rate will be available.               |
| @RatePlanType        				  | 0..1	  | String     | Rate rule to apply. 0 - No selected, 7 - Large Family, 8 - Public Servant, 10 - Negotiated, 11 - Package, 34 - Canary Resident, 35 - Balearic Resident, 36 - Honeymoon. If the attribute is not present and it is a base rate, the value is 0, if it is a derived rate, the value is the same as the parent rate.               |
| @PromotionCode        				    | 0..1	 | String     | Promotion code to apply. 0 - NoPromotion, 25 - Senior55  26 - Senior60, 27 - Senior65. If the attribute is not present or its value is 0 there is no promotion|
| RatePlan/Commission            	    | 0..1    |	         |                                                                       |
| @Percent           	                | 1       |Decimal	 | Commission percentage applied                                          |
| RatePlan/BookingRules            	    | 0..1    |	         |                                                                       |
| ../BookingRule		                | 1..n    |	         | 					                                                             |
| @Code       				          | 0..1	  | String   | Empty if there are viewerships conditions                               |
| ../CancelPenalties               | 1       | 	       |                                               	                       |
| ../CancelPenalty                 | 1..n    |	         |              					                                               |
| @NonRefundable			          | 1 	    | Boolean  |                                                 	                     |
| CancelPenalty/Deadline 		                  | 1       |	         |                                                                       |
| @OffsetTimeUnit			          | 1 	    | String   |                                                                       |
| @OffsetUnitMultiplier			    | 1 	    | Integer      |                                          	                           |
| @OffsetDropTime			          | 1 	    | String   |                                                                       |
| CancelPenalty/AmountPercent   | 1       |	         | NmbrOfNights, Percent or Amount tag must be present                       |
| @NmbrOfNights				          | 0..1	  | Integer  | Number of nights that will be charged                                 |
| @Percent    				          | 0..1	  | Decimal  | Percent of the total amount that will be charged in case of cancellation applying the current cancel penalty |
| @Amount     				          | 0..1	  | Decimal   | Amount that will be charged                                          |
| @CurrencyCode				          | 0..1	  | String    | Must be present if the amount tag is present                             |
| ../Viewerships		                | 0..1    |	          |                                          		                         |
| ../Viewership	                  | 1..n	  |	          |							                                                         |
| ../LocationCodes                 | 1       |	          |                                       		                           |
| @LocationCodesInclusive		    | 1 	    | Boolean   | Can or cannot be requested from this countryCode                     |
| /LocationCode                  | 0..1    |           | If it is missing, applies to all countryCodes |
| @CountryCode				          | 1 		  | String    | Country ISO2 code can or cannot be requested from this rate.        |
| RatePlan/Rates		                      | 1	      |		        | 							                                                       |
| ../Rate                          | 1..n	  |		        |							                                                         |
| Rate/AdditionalGuestAmounts		    | 1	      |		        |							                                                         |
| ../AdditionalGuestAmount		      | 1..2	  |		        |							                                                         |
| @AgeQualifyingCode		        | 1	      |	Integer	  |	*N*: 8, 7. Child, Baby			 |
| @MaxAge		                    | 1	      |	Integer	  |	Max age (not inclusive) of the additional guest			   |
| Rate/PaymentPolicies			          | 1     	|	          |                 |
| ../GuaranteePayment	            | 1..n    |	          | Information about an accepted payment            |
| @PaymentCode				          | 1     	|	          | Payment method accepted by the rate. Check *Documentation > Code Lists > Payment Type Codes*|
| ../AcceptedPayments	            | 0..1    |	          | Accepted payments information. Only present if *PaymentCode* is not "MerchantPayment" |
| /AcceptedPayment	              | 1..n    |	          | 	                                                                   |
| ../PaymentCard		                | 1..n    |	          |                                             	                       |
| @CardCode        			        | 1     	| String    | Check *Documentation > Code Lists > Credit Cards*                         |
| Rate/MealsIncluded                 | 0..1	  |	          | Present if board is included within the rate	                       |
| @MealPlanCodes			          | 1 		  | Integer   | Check *Documentation > Code Lists > Meal Plan Codes (OTA MPT)* |
| RatePlan/SellableProducts	            | 0..1    |	          | List of sellable products. When derived rate and not present, it applies to all rooms. In other cases, it informs about the rooms to which it applies |
| ../SellableProduct               | 0..n    |	          | Present if rooms are associated with this rate		                         |
| @InvCode    				          | 1 		  | String    | Sellable Product Code				                                       |
| @InvTypeCode    			        | 0..1 	  | String    | External information about the room (own code, own description, etc.) |
| @InvType    				          | 1 		  | String    | *N*: ROOM		                                   |
| @InvStatusType			          | 1 	 	  | String    | *N*: Active, Deactivated.				                                       |
| @InvNotifType			            | 0..1	  | String	  | *N*: New, Delta, Remove                                                 |
| ../GuestRoom                     | 1..n	  |	          |							                                                         |
| GuestRoom/Quantities                    | 1       |	          |      						                                                     |
| @StandardNumBeds			        | 1 		  | Integer   | Standard occupation of the room 			                                   |
| GuestRoom/Occupancy                     | 1       |	          |     						                                                     |
| @MinOccupancy				          | 1 		  | Integer   | 					                                                           |
| @MaxOccupancy				          | 1 		  | Integer   |                 					                                           |
| @AgeQualifyingCode			      | 1 		  | Integer   | *N*: 10, 8, 7. Adult, Child, Infant.		                                   |
| GuestRoom/Room                          | 1       |           | 			                                                               |
| @RoomTypeCode    				      | 1 		  | String    | Room Code 				                                                   |
| @RoomID    				            | 1 		  | Integer   |         				                                                     |
| GuestRoom/Description                          | 0..1       |     | Room description			                                               |
| Text                          | 1       | String    | 			                                               |
| RatePlan/Taxes                         | 0..1    |	          |	 	                                                                   |
| ../Tax                           | 1..n    |	          | Tax that applies to the room prices of the rate 			                   |
| @Amount/Percent               | 1       | Decimal   | Tax will be applied relative to an amount or a percentage            |
| @ChargeFrequency              | 0..1    | Boolean   | Tax is/isn't applied relative to the Amount of Nights booked         |
| @ChargeUnit                   | 0..1    | Boolean   | Tax is/isn't applied relative to the Amount of Paxes booked          |
| @Type                   | 0..1    | String   | If Inclusive indicates that tax has to be added to the final price. If Type is different than Inclusive or is not present the tax is only informative.         |
| ../TaxDescription                | 1       |	          |  			                                                               |
| ../Text                          | 1       | String	  | Description of tax type 			                                       |
| ../RatePlanInclusionsType        |	0..1    |	          | *DV*                  			                                         |
| ../RatePlanInclusionDescription  |	1       |	          |	*DV* 			                                                           |
| ../Name                          |	1       |	          |	*DV*.	                                                                                                  |         
| RatePlan/Description             |	0..1       |    |	Rate description 			                                             |
| ../Text                          |	1       |	String    |				                                             |
| RatePlan/Offers                  | 0..1    |           |                                                                      |
| ../Offer                         | 1..n    |           | 			                                                               |
| @OfferCode                    | 1       | String    |                                                                      |
| @OfferStatusType              | 1       | String    | *N*: Active, Deactivated                                             |
| @OfferNotifType			          | 0..1	  | String	  | *N*: New, Delta, Remove                                              |
| ../OfferRules                    | 1       |           | 			                                                               |
| ../OfferRule                     | 1       |           |		                                                                   |
| ../LengthsOfStay                 | 1       |           | 			                                                               |
| ../LengthOfStay                  | 1..2    |           |						                                                           |
| @Time 				                | 1	      | Integer	  | It indicates the number of nights for this stay	                       |
| @MinMaxMessageType			      | 1	      | String	  | *N*: MinLOS, MaxLOS. Minimum or Maximum stay for the Offer           |
| ../DOW_Restrictions              | 1       |           | 			                                                               |
| ../AvailableDaysOfWeek           | 1       |           |It indicates whether the Offer data applies to a certain day of the week |
| @Mon  				| 1	     | Boolean	|  |
| @Tue  				| 1	     | Boolean	|  |
| @Weds 				| 1	     | Boolean	|  |
| @Thur 				| 1	     | Boolean	|  |
| @Fri  				| 1	     | Boolean	|  |
| @Sat  				| 1	     | Boolean	|  |
| @Sun  				| 1      | Boolean	|  |
| ../Inventories                   | 0..1    |           | Rooms to which the offer will apply. If no Inventories are sent, the offer will apply to all the rooms in the Rate |
| ../Inventory                     | 1..n    |           | 		                                                                 |
| @InvCode                      | 1       | String    | Room code                                                            |
| ../Discount                       | 1       |           | 			                                                               |
| @NightsDiscounted             | 1       | String    | Nights discounted by the offer from the total stay amount           |
| @DiscountPattern              | 1       | String    | *N*: First, Last, Cheapest. Booking night/s the offer will dicount   |
| ../OfferDescription                          | 0..1       |     | Offer description                         
| ../Text                          | 1       | String    |                                                      |
| RatePlan/AdditionalDetails | 0..1 |  | Rate plan additional details |
| ../AdditionalDetail | 0..n |  | List of additional details |
| @Code | 1 | String | Trading partner code associated with the detail |
| @Type | 1 | String | Define the information. Only allowed "39" (Contract/negotiated booking information)|
| ../DetailDescription | 1 |  | Details Description |
| ../Text | 1 | String | Description. If additional details type is "39", the name of the trading partner for this rate.  |
| ../TPA_Extensions			   	      | 0..1    |		        | Only added when creating or deleting a hotel                 |
| ../TPA_Extensions/Attribute      | 1       |		        |							                                                         |
| @key        			            | 1  		  | String	  | *N*: HotelNotifType						                                       |
| @value      			            | 1  		  | String	  | *N*: New, Remove. To create a hotel or remove all the hotel setup.   |


### HotelRatePlanNotif 

The ``HotelRatePlanNotif`` message contains information about rate prices.

```xml
<HotelRatePlanNotif>
    <request>
        <POS>
            <Source>
                <RequestorID ID = "Provider1"/>
                <BookingChannel>
                    <CompanyName Code = "ClientTravelAgency1"/>
                </BookingChannel>
            </Source>
        </POS>
        <RatePlans HotelCode = "HOT123">
            <RatePlan RatePlanCode = "TAR333" CurrencyCode = "EUR" FreeChild = "true" FreeBaby = "false" RatePlanStatusType = "Deactivated">
                <Rates>
                    <Rate Start = "2013-04-01" End = "2013-12-31">
                        <BaseByGuestAmts>
                            <BaseByGuestAmt Type = "25" AmountAfterTax = "80.00"/>
                        </BaseByGuestAmts>
                    </Rate>
                </Rates>
                <SellableProducts>
                    <SellableProduct InvCode = "43" InvType = "ROOM"/>
                </SellableProducts>
                <Supplements>
                    <Supplement Start = "2013-04-01" End = "2013-12-31" AgeQualifyingCode = "10" Amount = "20.00" InvCode = "1" SupplementType = "Board"/>
                    <Supplement Start = "2013-04-01" End = "2013-12-31" AgeQualifyingCode = "8" Amount = "10.00" InvCode = "1" SupplementType = "Board"/>
                </Supplements>
            </RatePlan>
            <RatePlan RatePlanCode = "TAR333" CurrencyCode = "EUR" RatePlanStatusType = "Deactivated">
                <Rates>
                    <Rate Start = "2013-04-01" End = "2013-12-31">
                        <BaseByGuestAmts>
                            <BaseByGuestAmt Type = "14" Code = "2-0-0" AmountAfterTax = "150.00"/>
                            <BaseByGuestAmt Type = "14" Code = "3-0-0" AmountAfterTax = "-1"/>
                        </BaseByGuestAmts>
                    </Rate>
                </Rates>
                <SellableProducts>
                    <SellableProduct InvCode = "43" InvType = "ROOM"/>
                </SellableProducts>
                <Supplements>
                    <Supplement Start = "2013-04-01" End = "2013-12-31" AgeQualifyingCode = "10" Amount = "20.00" InvCode = "1" SupplementType = "Board"/>
                    <Supplement Start = "2013-04-01" End = "2013-12-31" AgeQualifyingCode = "8" Amount = "10.00" InvCode = "1" SupplementType = "Board"/>
                </Supplements>
            </RatePlan>
        </RatePlans>
    </request>
</HotelRatePlanNotif>
```

<br/>

**Example for Derived RatePlan**
```xml
<HotelRatePlanNotif>
    <request Version = "0">
        <POS>
            <Source>
                <RequestorID ID = "Provider1"></RequestorID>
                <BookingChannel>
                    <CompanyName Code = "ClientTravelAgency1"></CompanyName>
                </BookingChannel>
            </Source>
        </POS>
        <RatePlan RatePlanCode = "DRV" BaseRatePlanCode = "SRATE" RatePlanStatusType = "Active">
            <Rates>
                <Rate Start = "2014-07-01" End = "2014-07-31" AdjustedPercentage = "10" AdjustUpIndicator = "0"></Rate>
            </Rates>
        </RatePlan>
        <RatePlan RatePlanCode = "DRV" BaseRatePlanCode = "SRATE" RatePlanStatusType = "Deactivated">
            <Rates>
                <Rate Start = "2014-08-01" End = "2014-08-31" AdjustedPercentage = "10" AdjustUpIndicator = "0"></Rate>
            </Rates>
        </RatePlan>
    </request>
</HotelRatePlanNotif>
```

| **Element**	                  | **Rel** | **Type** | **Description**					                                             |
| :---------------------------- | :-----: | :------: | --------------------------------------------------------------------- |
| HotelRatePlanNotif		| 1 	    |		       | Root Node						                                                 |
| ../request		| 1 	    |		       | 				                                                 |
| request/RatePlans			   	            | 1   	  |		       |							                                                         |
| @HotelCode				            | 1	      | String	 |                                                                       |
| ../RatePlan			                | 1..n	  |		       |                        				                                       |
| @RatePlanCode				          | 1	      | String	 |          						                                                 |
| @FreeChild				          | 1	      | Boolean	 | Indicates if the child is free at that rate. Find here the [price calculation](https://docs.travelgatex.com/inventory/extranet/faq/free-children-baby/)    |
| @FreeBaby				          | 1	      | Boolean	 | Indicates if the baby is free at that rate. Find here the [price calculation](https://docs.travelgatex.com/inventory/extranet/faq/free-children-baby/) |
| @RatePlanStatusType			      | 0..1	  | String	 | *N*: Active, Deactivated. Informative tag that indicates wheter RatePlan is active or not |
| @BaseRatePlanCode			        | 0..1	  | String	 | *DV*. Rate code of the base RatePlan                                  |
| @CurrencyCode				          | 0..1	  | String	 | *BR*. ISO Currency	                                             |
| RatePlan/Rates	                        | 1	      |		       |							                                                         |
| ../Rate	                        | 1..n	      |		       |							                                                         |
| @Start 				                | 1	      | Date	   | Start date of rate 					                                         |
| @End   				                | 1	      | Date	   | End date of rate 					                                           |
| @AdjustedPercentage			      | 0..1	  | Decimal	 | *DV*. The percentage off the base rate plan amount used to determine the price of the Derived RatePlan |
| @AdjustedAmount			          | 0..1	  | Decimal	 | *DV*. The amount which should be added to the Base RatePlan to determine the price of the Derived RatePlan |
| @AdjustUpIndicator			      | 0..1	  | Boolean	 | *DV*: **true**: the adjusted amount/percentage is added to the amount specified for the Base RatePlan to determine the Derived RateAmount. **false**: the adjusted amount or adjusted percentage is subtracted from the amount specified for the Base RatePlan to determine the Derived RatePlan amount |
| Rate/BaseByGuestAmts               | 0..1 | | Different types of price can come in the same BaseByGuestAmts element.	             |
| ../BaseByGuestAmt                | 1..n |	|					 |                                                                       | 
| @AmountAfterTax			          | 1	      | Decimal	 | Total amount for the @NumberOfGuests indicated per day. This amount doesn't include tax. When value is *-1*, price should be deleted from the system.	|
| @NumberOfGuests			          | 0..1	  | Integer	 | How many adults are indicated per day. If @NumberOfGuests is not informed then @Type must be informed. The maximum @NumberOfGuests is the standard occupancy of the room       |
| @Type  				                | 0..1	  | Integer	 | If amounts are per Room or per Occupancy instead of per Pax. **@Type=25**: price is per Room. **@Type=14**: price is per occupancy, @Code is mandatory, AdditionalGuestAmounts are not allowed |
| @Code  				                | 0..1	  | String   | Mandatory if **@Type=14**.                                  |
| Rate/AdditionalGuestAmounts	      | 0..1 |  | *BR*				                                               |
| ../AdditionalGuestAmount         | 1..n |  | Price and information about the additional pax (children, infants or extra adults|
| @MaxAdditionalGuests			    | 1	      | Integer	 | Number of the additional pax |
| @AgeQualifyingCode			      | 1	      | Integer	 | *N*: 10, 8, 7. Adult, child or baby                            			|
| @Type  				                | 0..1	  | String	 | *N*: Exclusive. If present price is absolute and price tag is @Amount |
| @Amount				                | 0..1	  | Decimal	 | Price for each additional pax			|
| @Percent				              | 0..1	  | Decimal	 | Percent for each additional pax			|
| RatePlan/Supplements			              | 0..1	  | 		     | *BR*. Present if supplements by board exists |
| ../Supplement	                  | 1..n	  |		       |							|
| @Start 				                | 1	      | Date	   | Start date of this supplement			|
| @End   				                | 1	      | Date	   | End date of this supplement				|
| @AgeQualifyingCode			      | 0..1	  | Integer	 | *N*: 10, 8, 7. Adult, child, baby. Not allowed if charging Supplement Board by Occupancy |
| @ChargeTypeCode			          | 0..1	  | String	 | Occupancy Supplement Board. Only allowed if charging Supplement Board by Occupancy.
| @Amount				                | 1	      | Decimal	 | Amount of the supplement					|
| @SupplementType			          | 1	      | String	 | *N*: Board						|
| @InvCode				              | 1	      | String	 | OTA MPT Code if @SupplementType is Board. Check *Documentation > Code Lists > Meal Plan Codes (OTA MPT)*		|
| RatePlan/SellableProducts	            | 0..1	  |		| *BR*. List of sellable products 	|
| ../SellableProduct               | 1..n    |          |							|
| @InvCode				              | 1	      | Integer	 | Sellable Product Code				|
| @InvType				              | 1	      | Integer	 | *N*: ROOM. Sellable product type.				|



### HotelAvailNotif

The ``HotelAvailNotif`` message contains information about rate availability and allotment conditions.

```xml 
<HotelAvailNotif>
    <request>
        <POS>
            <Source>
                <RequestorID ID = "Provider1"></RequestorID>
                <BookingChannel>
                    <CompanyName Code = "ClientTravelAgency1"></CompanyName>
                </BookingChannel>
            </Source>
        </POS>
        <AvailStatusMessages HotelCode = "12">
            <AvailStatusMessage BookingLimit = "9" BookingSold = "1">
                <StatusApplicationControl Start = "2013-12-20" End = "2013-12-25" RatePlanCode = "BAR" InvCode = "APT" InvType = "ROOM"/>
                <LengthsOfStay ArrivalDateBased = "true">
                    <LengthOfStay Time = "2" TimeUnit = "Day" MinMaxMessageType = "MinLOS"/>
                    <LengthOfStay Time = "-1" TimeUnit = "Day" MinMaxMessageType = "MaxLOS"/>
                </LengthsOfStay>
                <RestrictionStatus SellThroughOpenIndicator = "false" MinAdvancedBookingOffset = "5"/>
            </AvailStatusMessage>
            <AvailStatusMessage BookingLimit = "12">
                <StatusApplicationControl Start = "2013-12-20" End = "2013-12-21" RatePlanCode = "LOWCOST" InvCode = "JUN_1" InvType = "ROOM"/>
                <RestrictionStatus Restriction = "Master" Status = "Close"/>
            </AvailStatusMessage>
        </AvailStatusMessages>
    </request>
</HotelAvailNotif>
```
<br/>

**Example for Offers**
```xml
<HotelAvailNotif>
    <request>
        <POS>
            <Source>
                <RequestorID ID = "Provider1"></RequestorID>
                <BookingChannel>
                    <CompanyName Code = "ClientTravelAgency1"></CompanyName>
                </BookingChannel>
            </Source>
        </POS>
        <AvailStatusMessages HotelCode = "12">
            <AvailStatusMessage>
                <StatusApplicationControl Start = "2013-12-20" End = "2013-12-21" RatePlanCode = "LOWCOST" PromotionCode = "OfferCode" Mon = "true" Tue = "true" Weds = "true" Thur = "true" Fri = "true" Sat = "true" Sun = "true"/>
                <RestrictionStatus Restriction = "Master" Status = "Close"/>
            </AvailStatusMessage>
        </AvailStatusMessages>
    </request>
</HotelAvailNotif>
```


| **Element**	                  | **Rel** | **Type** | **Description**					                                             |
| :---------------------------- | :-----: | :------: | --------------------------------------------------------------------- |
| HotelAvailNotif		    | 1  	    |		       | 						                                                 |
| ../request		    | 1  	    |		       | 						                                                 |
| request/AvailStatusMessages			      | 1   	  |		       |							                                                         |
| @HotelCode				            | 1	      | String	 |                                                                       |
| ../AvailStatusMessage            | 1..n	  |		       |							                                                         |
| @BookingLimit				          | 0..1	  | Integer	 | *DV*. Number of available rooms per Room-RatePlan for the indicated dates                                                                  |
| @BookingSold			          | 0..1	  | Integer	 | *DV*. Number of booked rooms per Room-RatePlan for the indicated dates. The available allotment is the difference between BookingLimit and BookingSold                                                                  |
| AvailStatusMessage/StatusApplicationControl      | 1       |	         |						                                                           |
| @Start				                | 1	      | Date	   | Start date						                                               |
| @End  				                | 1	      | Date	   | End date						                                                 |
| @RatePlanCode				          | 1	      | String	 |                                                       |
| @InvCode				              | 0..1	  | String	 | *BR*. Room Code		                             |
| @InvType				              | 0..1	  | String	 | *BR*. *N*: ROOM	                     |
| @PromotionCode				              | 0..1	  | String	 | *OF*. *N*: Offer Code	                     |
| @Mon				              | 0..1	  | Boolean	 | If true or attribute is not present, there is availability on Monday.                     |
| @Tue				              | 0..1	  | Boolean	 | If true or attribute is not present, there is availability on Tuesday.                   |
| @Weds				              | 0..1	  | Boolean	 | If true or attribute is not present, there is availability on Wednesday.                   |
| @Thur				              | 0..1	  | Boolean	 | If true or attribute is not present, there is availability on Thurday.                   |
| @Fri				              | 0..1	  | Boolean	 | If true or attribute is not present, there is availability on Friday.                   |
| @Sat				              | 0..1	  | Boolean	 | If true or attribute is not present, there is availability on Saturday.                   |
| @Sat				              | 0..1	  | Boolean	 | If true or attribute is not present, there is availability on Sunday.                   |
| AvailStatusMessage/LengthsOfStay                 | 0..1    |	         |							                                                         |
| @ArrivalDateBased			        | 0..1	  | Boolean	 | **true**: the Minimum and Maximum Stay is checked ONLY the first day of the availability. **false or null**: the Minimum and Maximum Stay is checked all the availability days. If both values are needed, two AvailStatusMessage will be sent. |
| ../LengthOfStay                  | 1..2    |         |						                                                             |
| @Time 				                | 1	      | Integer	| Indicates the number of @TimeUnit for this stay. When value is *0* or *-1*, condition should be deleted from the system.	                     |
| @TimeUnit				              | 1	      | String	| *N*: Day 						                                                   |
| @MinMaxMessageType			      | 1	      | String	| *N*: MinLOS, MaxLOS. Minimum or maximum stay                           |
| AvailStatusMessage/RestrictionStatus             | 0..1    |         |							                                                           |
| @Status				                | 0..1	  | String	| *N*: Open Close	                                                       |
| @Restriction				          | 0..1	  | String	| *N*: Master, Arrival, Departure.                                       |  
| @MinAdvancedBookingOffset		  | 0..1	  | Integer	| Minimum number of days before the check-in date to be available to be booked. This restriction is usually used to offer discounts on early bookings. When value is *0* or *-1*, condition should be deleted from the system.                             |
| @MaxAdvancedBookingOffset		  | 0..1	  | Integer	| Maximum number of days before the check-in date to be available to be booked. This restriction is usually used to offer last minute discounts on unsold inventory. When value is *-1*, condition should be deleted from the system.               |
| @SellThroughOpenIndicator		  | 0..1	  | Boolean	| *BR*. Room-RatePlan can be sold with no limit if @Status is Open  |

{{%custom-children%}}

