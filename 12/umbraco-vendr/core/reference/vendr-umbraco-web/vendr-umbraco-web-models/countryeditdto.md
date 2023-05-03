---
title: CountryEditDto
description: API reference for CountryEditDto in Vendr, the eCommerce solution for Umbraco
---
## CountryEditDto

```csharp
public class CountryEditDto : CountryDto, IHasPath, INotificationModel
```

**Inheritance**

* class [CountryDto](../countrydto/)
* interface [IHasPath](../ihaspath/)

**Namespace**
* [Vendr.Umbraco.Web.Models](../)

### Constructors

#### CountryEditDto

The default constructor.

```csharp
public CountryEditDto()
```


### Properties

#### Notifications

```csharp
public List<BackOfficeNotification> Notifications { get; set; }
```


---

#### Path

```csharp
public List<string> Path { get; set; }
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Umbraco.Web.dll -->