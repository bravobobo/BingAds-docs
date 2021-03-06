---
title: SearchUserInvitations Service Operation - Customer Management
ms.service: bing-ads-customer-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Searches for user invitations that match a specified criteria.
dev_langs: 
  - csharp
  - java
  - php
  - python
---
# SearchUserInvitations Service Operation - Customer Management
Searches for user invitations that match a specified criteria.

This operation returns all pending invitations, whether or not they have expired. Accepted invitations are not included in the response.  

## <a name="request"></a>Request Elements
The *SearchUserInvitationsRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

> [!NOTE]
> Unless otherwise noted below, all request elements are required.

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="predicates"></a>Predicates|Determines the request conditions. This operation's response will include user invitations that match all of the specified predicates.<br/><br/>Although the data type calls for a list of predicates, you can only set one predicate.<br/><br/>For a list of supported *Field* and *Operator* elements of a [Predicate](predicate.md) object for this service operation, see [Predicate Remarks](predicate.md#remarks).|[Predicate](predicate.md) array|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *SearchUserInvitationsResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="userinvitations"></a>UserInvitations|A list of user invitations that meet the specified criteria.|[UserInvitation](userinvitation.md) array|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
This template was generated by a tool to show the [order](../guides/services-protocol.md#element-order) of the [body](#request-body) and [header](#request-header) elements for the SOAP request. For supported types that you can use with this service operation, see the [Request Body Elements](#request-header) reference above.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v12">
    <Action mustUnderstand="1">SearchUserInvitations</Action>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
  </s:Header>
  <s:Body>
    <SearchUserInvitationsRequest xmlns="https://bingads.microsoft.com/Customer/v12">
      <Predicates xmlns:e278="https://bingads.microsoft.com/Customer/v12/Entities" i:nil="false">
        <e278:Predicate>
          <e278:Field i:nil="false">ValueHere</e278:Field>
          <e278:Operator>ValueHere</e278:Operator>
          <e278:Value i:nil="false">ValueHere</e278:Value>
        </e278:Predicate>
      </Predicates>
    </SearchUserInvitationsRequest>
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
    <SearchUserInvitationsResponse xmlns="https://bingads.microsoft.com/Customer/v12">
      <UserInvitations xmlns:e279="https://bingads.microsoft.com/Customer/v12/Entities" d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">
        <e279:UserInvitation>
          <e279:Id>ValueHere</e279:Id>
          <e279:FirstName d4p1:nil="false">ValueHere</e279:FirstName>
          <e279:LastName d4p1:nil="false">ValueHere</e279:LastName>
          <e279:Email d4p1:nil="false">ValueHere</e279:Email>
          <e279:CustomerId>ValueHere</e279:CustomerId>
          <e279:RoleId>ValueHere</e279:RoleId>
          <e279:AccountIds d4p1:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long>ValueHere</a1:long>
          </e279:AccountIds>
          <e279:ExpirationDate>ValueHere</e279:ExpirationDate>
          <e279:Lcid>ValueHere</e279:Lcid>
        </e279:UserInvitation>
      </UserInvitations>
    </SearchUserInvitationsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](../guides/client-libraries.md). See [Bing Ads Code Examples](../guides/code-examples.md) for more examples.
```csharp
public async Task<SearchUserInvitationsResponse> SearchUserInvitationsAsync(
	IList<Predicate> predicates)
{
	var request = new SearchUserInvitationsRequest
	{
		Predicates = predicates
	};

	return (await CustomerManagementService.CallAsync((s, r) => s.SearchUserInvitationsAsync(r), request));
}
```
```java
static SearchUserInvitationsResponse searchUserInvitations(
	ArrayOfPredicate predicates) throws RemoteException, Exception
{
	SearchUserInvitationsRequest request = new SearchUserInvitationsRequest();

	request.setPredicates(predicates);

	return CustomerManagementService.getService().searchUserInvitations(request);
}
```
```php
static function SearchUserInvitations(
	$predicates)
{

	$GLOBALS['Proxy'] = $GLOBALS['CustomerManagementProxy'];

	$request = new SearchUserInvitationsRequest();

	$request->Predicates = $predicates;

	return $GLOBALS['CustomerManagementProxy']->GetService()->SearchUserInvitations($request);
}
```
```python
response=customermanagement_service.SearchUserInvitations(
	Predicates=Predicates)
```

## Requirements
Service: [CustomerManagementService.svc v12](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v12/CustomerManagementService.svc)  
Namespace: https\://bingads.microsoft.com/Customer/v12  

