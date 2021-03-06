---
title: SignupCustomer Service Operation - Customer Management
ms.service: bing-ads-customer-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Creates a new customer and account that rolls up to your reseller payment method.
dev_langs: 
  - csharp
  - java
  - php
  - python
---
# SignupCustomer Service Operation - Customer Management
Creates a new customer and account that rolls up to your reseller payment method.

> [!NOTE]
> You must be a reseller with aggregator user permissions to call this operation. For more details see [Management Model for Resellers](../guides/management-model-resellers.md).

Pass both [Customer](customer.md) and [AdvertiserAccount](advertiseraccount.md) objects in the request. The customer object includes the customer's name, the address where the customer is located, the market in which the customer operates, and the industry in which the customer participates. Although it is possible to add multiple customers with the same details, you should use unique customer names so that users can easily distinguish between customers in a user interface.

The account object must specify the name of the account; the type of currency to use to settle the account; and the payment method identifier, which must be set to null. The operation generates an invoice account and sets the payment method identifier to the identifier associated with the reseller's invoice. You are invoiced for all charges incurred by the customers that you manage.

If the operation succeeds, a new managed customer is created outside of the reseller customer and an account is created within the managed customer. 

## <a name="request"></a>Request Elements
The *SignupCustomerRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

> [!NOTE]
> Unless otherwise noted below, all request elements are required.

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="account"></a>Account|An [AdvertiserAccount](advertiseraccount.md) that specifies the details of the customer's primary account.|[AdvertiserAccount](advertiseraccount.md)|
|<a name="customer"></a>Customer|A [Customer](customer.md) that specifies the details of the customer that you are adding.|[Customer](customer.md)|
|<a name="parentcustomerid"></a>ParentCustomerId|The customer identifier of the reseller that will manage this customer.|**long**|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *SignupCustomerResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="accountid"></a>AccountId|A system-generated account identifier corresponding to the new account specified in the request.<br/><br/>Use this identifier with operation requests that require an *AccountId* element and a *CustomerAccountId* SOAP header element.|**long**|
|<a name="accountnumber"></a>AccountNumber|A system-generated account number that is used to identify the account in the Bing Ads web application. The account number has the form, X*nnnnnnn*, where *nnnnnnn* is a series of digits.|**string**|
|<a name="createtime"></a>CreateTime|The date and time that the account was added. The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](https://go.microsoft.com/fwlink/?linkid=859198).|**dateTime**|
|<a name="customerid"></a>CustomerId|A system-generated customer identifier corresponding to the new customer specified in the request.<br/><br/>Use this identifier with operation requests that require a *CustomerId* SOAP header element.|**long**|
|<a name="customernumber"></a>CustomerNumber|A system-generated customer number that is used in the Bing Ads web application. The customer number is of the form, C*nnnnnnn*, where *nnnnnnn* is a series of digits.|**string**|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
This template was generated by a tool to show the [order](../guides/services-protocol.md#element-order) of the [body](#request-body) and [header](#request-header) elements for the SOAP request. For supported types that you can use with this service operation, see the [Request Body Elements](#request-header) reference above.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v12">
    <Action mustUnderstand="1">SignupCustomer</Action>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
  </s:Header>
  <s:Body>
    <SignupCustomerRequest xmlns="https://bingads.microsoft.com/Customer/v12">
      <Customer xmlns:e281="https://bingads.microsoft.com/Customer/v12/Entities" i:nil="false">
        <e281:CustomerFinancialStatus i:nil="false">ValueHere</e281:CustomerFinancialStatus>
        <e281:Id i:nil="false">ValueHere</e281:Id>
        <e281:Industry i:nil="false">ValueHere</e281:Industry>
        <e281:LastModifiedByUserId i:nil="false">ValueHere</e281:LastModifiedByUserId>
        <e281:LastModifiedTime i:nil="false">ValueHere</e281:LastModifiedTime>
        <e281:MarketCountry i:nil="false">ValueHere</e281:MarketCountry>
        <e281:ForwardCompatibilityMap xmlns:e282="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e282:KeyValuePairOfstringstring>
            <e282:key i:nil="false">ValueHere</e282:key>
            <e282:value i:nil="false">ValueHere</e282:value>
          </e282:KeyValuePairOfstringstring>
        </e281:ForwardCompatibilityMap>
        <e281:MarketLanguage i:nil="false">ValueHere</e281:MarketLanguage>
        <e281:Name i:nil="false">ValueHere</e281:Name>
        <e281:ServiceLevel i:nil="false">ValueHere</e281:ServiceLevel>
        <e281:CustomerLifeCycleStatus i:nil="false">ValueHere</e281:CustomerLifeCycleStatus>
        <e281:TimeStamp i:nil="false">ValueHere</e281:TimeStamp>
        <e281:Number i:nil="false">ValueHere</e281:Number>
        <e281:CustomerAddress i:nil="false">
          <e281:City i:nil="false">ValueHere</e281:City>
          <e281:CountryCode i:nil="false">ValueHere</e281:CountryCode>
          <e281:Id i:nil="false">ValueHere</e281:Id>
          <e281:Line1 i:nil="false">ValueHere</e281:Line1>
          <e281:Line2 i:nil="false">ValueHere</e281:Line2>
          <e281:Line3 i:nil="false">ValueHere</e281:Line3>
          <e281:Line4 i:nil="false">ValueHere</e281:Line4>
          <e281:PostalCode i:nil="false">ValueHere</e281:PostalCode>
          <e281:StateOrProvince i:nil="false">ValueHere</e281:StateOrProvince>
          <e281:TimeStamp i:nil="false">ValueHere</e281:TimeStamp>
          <e281:BusinessName i:nil="false">ValueHere</e281:BusinessName>
        </e281:CustomerAddress>
      </Customer>
      <Account xmlns:e283="https://bingads.microsoft.com/Customer/v12/Entities" i:nil="false">
        <e283:BillToCustomerId i:nil="false">ValueHere</e283:BillToCustomerId>
        <e283:CurrencyCode i:nil="false">ValueHere</e283:CurrencyCode>
        <e283:AccountFinancialStatus i:nil="false">ValueHere</e283:AccountFinancialStatus>
        <e283:Id i:nil="false">ValueHere</e283:Id>
        <e283:Language i:nil="false">ValueHere</e283:Language>
        <e283:LastModifiedByUserId i:nil="false">ValueHere</e283:LastModifiedByUserId>
        <e283:LastModifiedTime i:nil="false">ValueHere</e283:LastModifiedTime>
        <e283:Name i:nil="false">ValueHere</e283:Name>
        <e283:Number i:nil="false">ValueHere</e283:Number>
        <e283:ParentCustomerId>ValueHere</e283:ParentCustomerId>
        <e283:PaymentMethodId i:nil="false">ValueHere</e283:PaymentMethodId>
        <e283:PaymentMethodType i:nil="false">ValueHere</e283:PaymentMethodType>
        <e283:PrimaryUserId i:nil="false">ValueHere</e283:PrimaryUserId>
        <e283:AccountLifeCycleStatus i:nil="false">ValueHere</e283:AccountLifeCycleStatus>
        <e283:TimeStamp i:nil="false">ValueHere</e283:TimeStamp>
        <e283:TimeZone i:nil="false">ValueHere</e283:TimeZone>
        <e283:PauseReason i:nil="false">ValueHere</e283:PauseReason>
        <e283:ForwardCompatibilityMap xmlns:e284="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e284:KeyValuePairOfstringstring>
            <e284:key i:nil="false">ValueHere</e284:key>
            <e284:value i:nil="false">ValueHere</e284:value>
          </e284:KeyValuePairOfstringstring>
        </e283:ForwardCompatibilityMap>
        <e283:LinkedAgencies i:nil="false">
          <e283:CustomerInfo>
            <e283:Id i:nil="false">ValueHere</e283:Id>
            <e283:Name i:nil="false">ValueHere</e283:Name>
          </e283:CustomerInfo>
        </e283:LinkedAgencies>
        <e283:SalesHouseCustomerId i:nil="false">ValueHere</e283:SalesHouseCustomerId>
        <e283:TaxInformation xmlns:e285="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e285:KeyValuePairOfstringstring>
            <e285:key i:nil="false">ValueHere</e285:key>
            <e285:value i:nil="false">ValueHere</e285:value>
          </e285:KeyValuePairOfstringstring>
        </e283:TaxInformation>
        <e283:BackUpPaymentInstrumentId i:nil="false">ValueHere</e283:BackUpPaymentInstrumentId>
        <e283:BillingThresholdAmount i:nil="false">ValueHere</e283:BillingThresholdAmount>
        <e283:BusinessAddress i:nil="false">
          <e283:City i:nil="false">ValueHere</e283:City>
          <e283:CountryCode i:nil="false">ValueHere</e283:CountryCode>
          <e283:Id i:nil="false">ValueHere</e283:Id>
          <e283:Line1 i:nil="false">ValueHere</e283:Line1>
          <e283:Line2 i:nil="false">ValueHere</e283:Line2>
          <e283:Line3 i:nil="false">ValueHere</e283:Line3>
          <e283:Line4 i:nil="false">ValueHere</e283:Line4>
          <e283:PostalCode i:nil="false">ValueHere</e283:PostalCode>
          <e283:StateOrProvince i:nil="false">ValueHere</e283:StateOrProvince>
          <e283:TimeStamp i:nil="false">ValueHere</e283:TimeStamp>
          <e283:BusinessName i:nil="false">ValueHere</e283:BusinessName>
        </e283:BusinessAddress>
        <e283:AutoTagType i:nil="false">ValueHere</e283:AutoTagType>
        <e283:SoldToPaymentInstrumentId i:nil="false">ValueHere</e283:SoldToPaymentInstrumentId>
      </Account>
      <ParentCustomerId i:nil="false">ValueHere</ParentCustomerId>
    </SignupCustomerRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
This template was generated by a tool to show the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v12">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <SignupCustomerResponse xmlns="https://bingads.microsoft.com/Customer/v12">
      <CustomerId>ValueHere</CustomerId>
      <CustomerNumber d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</CustomerNumber>
      <AccountId d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</AccountId>
      <AccountNumber d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</AccountNumber>
      <CreateTime>ValueHere</CreateTime>
    </SignupCustomerResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](../guides/client-libraries.md). See [Bing Ads Code Examples](../guides/code-examples.md) for more examples.
```csharp
public async Task<SignupCustomerResponse> SignupCustomerAsync(
	Customer customer,
	AdvertiserAccount account,
	long? parentCustomerId)
{
	var request = new SignupCustomerRequest
	{
		Customer = customer,
		Account = account,
		ParentCustomerId = parentCustomerId
	};

	return (await CustomerManagementService.CallAsync((s, r) => s.SignupCustomerAsync(r), request));
}
```
```java
static SignupCustomerResponse signupCustomer(
	Customer customer,
	AdvertiserAccount account,
	java.lang.Long parentCustomerId) throws RemoteException, Exception
{
	SignupCustomerRequest request = new SignupCustomerRequest();

	request.setCustomer(customer);
	request.setAccount(account);
	request.setParentCustomerId(parentCustomerId);

	return CustomerManagementService.getService().signupCustomer(request);
}
```
```php
static function SignupCustomer(
	$customer,
	$account,
	$parentCustomerId)
{

	$GLOBALS['Proxy'] = $GLOBALS['CustomerManagementProxy'];

	$request = new SignupCustomerRequest();

	$request->Customer = $customer;
	$request->Account = $account;
	$request->ParentCustomerId = $parentCustomerId;

	return $GLOBALS['CustomerManagementProxy']->GetService()->SignupCustomer($request);
}
```
```python
response=customermanagement_service.SignupCustomer(
	Customer=Customer,
	Account=Account,
	ParentCustomerId=ParentCustomerId)
```

## Requirements
Service: [CustomerManagementService.svc v12](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v12/CustomerManagementService.svc)  
Namespace: https\://bingads.microsoft.com/Customer/v12  

