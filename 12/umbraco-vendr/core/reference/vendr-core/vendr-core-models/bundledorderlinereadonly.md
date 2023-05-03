---
title: BundledOrderLineReadOnly
description: API reference for BundledOrderLineReadOnly in Vendr, the eCommerce solution for Umbraco
---
## BundledOrderLineReadOnly

```csharp
public class BundledOrderLineReadOnly : OrderLineReadOnly
```

**Inheritance**

* class [OrderLineReadOnly](../orderlinereadonly/)

**Namespace**
* [Vendr.Core.Models](../)

### Properties

#### ParentBundleId

Gets the bundle ID of the parent order line to this order line

```csharp
public string ParentBundleId { get; }
```


---

#### ParentOrderLineId

Gets the ID of the parent [`OrderLineReadOnly`](../orderlinereadonly/) this entity belongs to

```csharp
public Guid ParentOrderLineId { get; }
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->