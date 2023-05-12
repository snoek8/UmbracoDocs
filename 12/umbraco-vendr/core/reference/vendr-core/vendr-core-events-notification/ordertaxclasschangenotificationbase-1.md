---
title: OrderTaxClassChangeNotificationBase<TEntity>
description: API reference for OrderTaxClassChangeNotificationBase<TEntity> in Vendr, the eCommerce solution for Umbraco
---
## OrderTaxClassChangeNotificationBase&lt;TEntity&gt;

```csharp
public abstract class OrderTaxClassChangeNotificationBase<TEntity> : 
    OrderNotificationEventBase<TEntity>
    where TEntity : OrderReadOnly
```

**Inheritance**

* class [OrderNotificationEventBase&lt;TOrder&gt;](../ordernotificationeventbase-1/)

**Namespace**
* [Vendr.Core.Events.Notification](../)

### Constructors

#### OrderTaxClassChangeNotificationBase&lt;TEntity&gt;

```csharp
public OrderTaxClassChangeNotificationBase(TEntity order, ChangingValue<Guid?> taxClassId)
```


### Properties

#### TaxClassId

```csharp
public ChangingValue<Guid?> TaxClassId { get; }
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->