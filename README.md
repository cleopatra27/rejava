# Direct Charge

```java
cardPayment cardPayment = new cardPayment();
cardLoad cardload = new cardLoad cardload();
cardload.setPBFPubKey(PBFPubKey);
cardload.setCardno(cardno);
cardload.setCvv(cvv);
cardload.setExiprymonth(expirymonth);
cardload.setCurrency(currency);
cardload.setCountry(country);
cardload.setAmount(amount);
cardload.setEmail(email);
cardload.setphonenumber(phonenumber);
cardload.setfirstname(firstname);
cardload.setLastname(lastname);
cardload.setMetaname(metaname);
cardload.setMetaValue(metavalue);
cardload.setRedirect_url(redirect_url);
cardload.setDevice_fingerprint(device_fingerprint)
  
String response = cardPayment.doflwcardpayment(cardload);

JSONObject myObject = new JSONObject(response);

if(myObject.optString("suggested_auth").equals("PIN"))
{
  //get PIN fom customer
  cardload.setPin(PIN);
  cardload.setSuggested_auth("PIN");
  String response_one = cardPayment.doflwcardpayment(cardload);
  
JSONObject myObject = new JSONObject(response_one);
JSONObject Object = myObject.optJSONObject("data");
  
String flwRef = Object.optString("flwRef")
  
validateCardCharge validatecardcharge = new validateCardCharge();
validateCardPayload validatecardpayload = new validateCardPayload();
validatecardpayload.setPBFPubKey(PBFPubKey);
validatecardpayload.setTransaction_reference(transaction_reference);
validatecardpayload.setOTP(OTP);
  
response = validatecardcharge.doflwcardvalidate(validatecardpayload);
}
else if(myObject.optString("suggested_auth").equals("NOAUTH_INTERNATIONAL"))
{
  //billing info - billingzip, billingcity, billingaddress, billingstate, billingcountry
  cardload.setBillingaddress(Billingaddress);
  cardload.setBillingcity(Billingcity);
  cardload.setBillingcountry(Billingcountry);
  cardload.setBillingstate(Billingstate);
  cardload.setBillingzip(Billingzip);
  cardload.setSuggested_auth("NOAUTH_INTERNATIONAL");
  String response_one = cardPayment.doflwcardpayment(cardload);
  
JSONObject myObject = new JSONObject(response_one);
JSONObject Object = myObject.optJSONObject("data");
  
String flwRef = Object.optString("flwRef")
  
validateCardCharge validatecardcharge = new validateCardCharge();
validateCardPayload validatecardpayload = new validateCardPayload();
validatecardpayload.setPBFPubKey(PBFPubKey);
validatecardpayload.setTransaction_reference(transaction_reference);
validatecardpayload.setOTP(OTP);
  
response = validatecardcharge.doflwcardvalidate(validatecardpayload);
}
else if(myObject.optString("authurl")!="N/A")
{
  //load the url in an IFRAME
}

validateCardCharge validatecardcharge = new validateCardCharge();
validateCardPayload validatecardpayload = new validateCardPayload();
validatecardpayload.
  
String overresponse = validatecardcharge.doflwcardvalidate(validatecardpayload);
return response;
```

## Mobile Money
```java
mobileMoney mobileMoney = new mobileMoney();
mobilemoneyPayload mobilemoneyPayload = new mobilemoneyPayload();
mobilemoneyPayload.setPBFPubKey(PBFPubKey);
mobilemoneyPayload.setCurrency(currency);
mobilemoneyPayload.setAmount(amount);
mobilemoneyPayload.setPhoneNumber(phonenumber);
mobilemoneyPayload.setEmail(email);
mobilemoneyPayload.setFirstname(firstname);
mobilemoneyPayload.setLastName(lastname);
mobilemoneyPayload.setNarration(narration);
mobilemoneyPayload.setMetaname(metaname);
mobilemoneyPayload.setMetavalue(metavalue);
mobilemoneyPayload.setDevice_fingerprint(device_fingerprint);
mobilemoneyPayload.setPaymane_type(Payment_type);

String response = mobileMoney.domobilemoney(mobilemoneyPayload);

return response; 
```

## QR code
```java
qrPayments qrPayments = new qrPayments();
qrcodePayload qrcodepayload = new qrcodePayload();
qrcodepayload.setPBFPubKey(PBFPubKey);
qrcodepayload.setAmount(amount);
qrcodepayload.setTxref(teRef);
qrcodepayload.setPayment_Type(payment_type);
qrcodepayload.setDevice_fingerprint(Device_fingerprint);
qrcodepayload.setMetaname(metaname);
qrcodepayload.setMetavalue(metavalue);
qrcodepayload.setEmail(email);

String response = qrPayments.doflwqrpayment(qrcodepayload);
```

## Bills

```java
bills bills = new bills();
BillModel billmodel = new BillModel();
billmodel.setCustomerId(CustomerId);
billmodel.setReference(Reference);
billmodel.setAmount(amount);
billmodel.setIsAirtime(IsAirtime);
billmodel.setBillername(billername);

bills.dobillpayment(billmodel);
```

## BVN Validation
```java
bvnValidation bvnvalidation = new bvnValidation();
bvnload bvnload = new bvnload();
bvnload.setBvn(bvn)

String response = bvnvalidation(bvnload);
```

## Payment Plans
```java

paymentplan paymentplan = new paymentplan();
pamentplancreatepayload pamentplancreatepayload = new pamentplancreatepayload();
pamentplancreatepayload.setAmount(amount);
pamentplancreatepayload.setName(name);
pamentplancreatepayload.setIntervale(interval);
pamentplancreatepayload.setDuration(duration);
pamentplancreatepayload.setRef(ref);

String response = paymentplan.docreatepayment(pamentplancreatepayload);

return response;
```

## Virtual Cards
Sample Code to create a virtual card.

```java 
virtualCards virtualCards = new virtualCards();
virtualcardpayload virtualcardpayload = new virtualcardpayload():
virtualcardpayload.setCurrency(currency);
virtualcardpayload.setAmount(amount);
virtualcardpayload.setBilling_name(billing_name);
virtualcardpayload.setBilling_address(billing_Address);
virtualcardpayload.setBilling_city(billing_city);
virtualcardpayload.setBilling_state(billing_state);
virtualcardpayload.setBilling_postal_code(billing_postal_code);
// virtualcardpayload.setSecret_Key(secret_key);

String response = virtualCards.dovirtualcardcreate(virtualcardpayload);
```

Sample Code to get for a virtual card.
```java 
virtualCards virtualCards = new virtualCards();
virtualcardpayload virtualcardpayload = new virtualcardpayload():
virtualcardpayload.setId(id);
// virtualcardpayload.setSecret_Key(secret_key);

String response = virtualCards.dovirtualcardsearch(virtualcardpayload);
```

Sample Code to List virtual cards.
```java
virtualCards virtualCards = new virtualCards();
virtualcardpayload virtualcardpayload = new virtualcardpayload():
virtualcardpayload.setPage(page);
// virtualcardpayload.setSecret_Key(secret_key);

String response = virtualCards.dovirtualcardget(virtualcardpayload);
```

Sample Code to terminate a virtual card.
```java
virtualCards virtualCards = new virtualCards();
virtualcardpayload virtualcardpayload = new virtualcardpayload():
virtualcardpayload.setId(id);
// virtualcardpayload.setSecret_Key(secret_key);

String response = virtualCards.dovirtualcardterminate(virtualcardpayload);
```

Sample Code to fund a virtual card.
```java
virtualCards virtualCards = new virtualCards();
virtualcardpayload virtualcardpayload = new virtualcardpayload():
virtualcardpayload.setId(id);
virtualcardpayload.setAmount(amount);
virtualcardpayload.setDebit_currency(debit_currency);
// virtualcardpayload.setSecret_Key(secret_key);

String response = virtualCards.dovirtualcardfund(virtualcardpayload);
```

Sample Code to get a virtual card transaction.
```java
virtualCards virtualCards = new virtualCards();
virtualcardpayload virtualcardpayload = new virtualcardpayload():
virtualcardpayload.setId(id);
virtualcardpayload.setFromDate(FromDate);
virtualcardpayload.setToDate(ToDate);
virtualcardpayload.setPageIndex(PageIndex);
virtualcardpayload.setPageSize(pagesize);
virtualcardpayload.setCardId(cardid);
// virtualcardpayload.setSecret_Key(secret_key);

String response = virtualCards.dovirtualcardfetchtrans(virtualcardpayload);
```

------
```java
virtualCards virtualCards = new virtualCards();
withdrawcardpayload withdrawcardpayload = new withdrawcardpayload():
virtualcardpayload.setCard_id(card_id);
virtualcardpayload.setAmount(amount);
// virtualcardpayload.setSecret_Key(secret_key);

String response = virtualCards.dovirtualcardfwithdraw(withdrawcardpayload);
```

## Ebills

Sample Code to create Ebills

```java 
ebills ebills = new ebills();
ebillpayload ebillpayload = new ebillpayload();
ebillpayload.setAccountnumber(accountnumber);
ebillpayload.setNarration(narration);
ebillpayload.setNumberofunits(numberofunits);
ebillpayload.setCurrency(currency);
ebillpayload.setAmount(amount);
ebillpayload.setPhonenumber(phonenumber);
ebillpayload.setEmail(email);
ebillpayload.setTxRef(txref);
//ebillpayload.setSeckey(SECKEY);

String response = ebills.doebillscreate(ebillpayload);
```

Sample Code to update Ebills
```java
ebills ebills = new ebills();
ebillpayload ebillpayload = new ebillpayload();
ebillpayload.setReference(reference);
ebillpayload.setCurrency(currency);
ebillpayload.setAmount(amount);
//ebillpayload.setSeckey(SECKEY);

String response = ebills.doebillsupdate(ebillpayload);
```

## Refund

Sample code to refund a transaction

```java
Refund refund = new Refund();
refundPayload refundpayload = new refundPayload();
refundpayload.setRef(ref);
refundpayload.setAmount(amount);
//refundpayload.setSceretKey(seckey);

String response = refund.dorefund(refundpayload);
```

## Tokenized Charge

Sample code for charging tokenised cards

```java
tokenCharge tokencharge = new tokenCharge();
tokenChargePayload tokenchargepayload = new tokenChargePayload():
tokenchargepayload.setCurrency(currency);
tokenchargepayload.setToken(token);
tokenchargepayload.setAmount(amount);
tokenchargepayload.setEmail(email);
tokenchargepayload.setFirstname(firstname);
tokenchargepayload.setLastname(Lastname);
tokenchargepayload.setIP(ip);
tokenchargepayload.setTxref(texref);
//tokenchargepayload.setSeckey(Seckey);

String response = tokencharge.dotokenizedcharge(tokenchargepayload);
```

Sample code to update email for a token

```java
tokenCharge tokencharge = new tokenCharge();
tokenChargePayload tokenchargepayload = new tokenChargePayload():
tokenchargepayload.setEmail(email);
tokenchargepayload.setToken(token);
//tokenchargepayload.setSeckey(Seckey);

String response = tokencharge.dotokenizedcharge(tokenchargepayload);
```
