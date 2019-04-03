# Direct Charge

```bash
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
JSONObject Object = myObject.optJSONObject("data");

if(myObject.optString("status").equals("success") && Object.optString("suggested_auth").equals("PIN"))
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
else if(myObject.optString("status").equals("success") && Object.optString("suggested_auth").equals("NOAUTH_INTERNATIONAL"))
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
else if(myObject.optString("status").equals("success") && Object.optString("authurl")!="N/A")
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
```bash
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
