---
title: ValidateDefaultShippingMethodBelongsToCountryStore
description: API reference for ValidateDefaultShippingMethodBelongsToCountryStore in Vendr, the eCommerce solution for Umbraco
---
## ValidateDefaultShippingMethodBelongsToCountryStore

```csharp
public class ValidateDefaultShippingMethodBelongsToCountryStore : 
    ValidationEventHandlerBase<ValidateCountryDefaultShippingMethodChange>
```

**Inheritance**

* class [ValidationEventHandlerBase&lt;!0&gt;](../../../vendr-common/vendr-common-events/validationeventhandlerbase-1/)

**Namespace**
* [Vendr.Core.Events.Validation.Handlers.Country](../)

### Constructors

#### ValidateDefaultShippingMethodBelongsToCountryStore

```csharp
public ValidateDefaultShippingMethodBelongsToCountryStore(
    IShippingMethodService shippingMethodService)
```


### Methods

#### Validate

```csharp
public override void Validate(ValidateCountryDefaultShippingMethodChange evt)
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->