---
title: OrderCurrencyChangeNotificationBase<TEntity>
description: API reference for OrderCurrencyChangeNotificationBase<TEntity> in Vendr, the eCommerce solution for Umbraco
---
## OrderCurrencyChangeNotificationBase&lt;TEntity&gt;

```csharp
public abstract class OrderCurrencyChangeNotificationBase<TEntity> : 
    OrderNotificationEventBase<TEntity>
    where TEntity : OrderReadOnly
```

**Inheritance**

* class [OrderNotificationEventBase&lt;TOrder&gt;](../ordernotificationeventbase-1/)

**Namespace**
* [Vendr.Core.Events.Notification](../)

### Constructors

#### OrderCurrencyChangeNotificationBase&lt;TEntity&gt;

```csharp
public OrderCurrencyChangeNotificationBase(TEntity order, ChangingValue<Guid?> currencyId)
```


### Properties

#### CurrencyId

```csharp
public ChangingValue<Guid?> CurrencyId { get; }
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->