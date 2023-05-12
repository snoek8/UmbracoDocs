---
title: PipelineTaskCollectionBuilder<TCollection,TItem>
description: API reference for PipelineTaskCollectionBuilder<TCollection,TItem> in Vendr, the eCommerce solution for Umbraco
---
## PipelineTaskCollectionBuilder&lt;TCollection,TItem&gt;

```csharp
public class PipelineTaskCollectionBuilder<TCollection, TItem> : 
    OrderedComposedCollectionBuilderBase<PipelineTaskCollectionBuilder<TCollection, TItem>, TCollection, IPipelineTask<TItem>>
    where TCollection : class, IPipelineTaskCollection<TItem>
```

**Inheritance**

* class [OrderedComposedCollectionBuilderBase&lt;!0,!1,!2&gt;](../../../vendr-common/vendr-common-composing/orderedcomposedcollectionbuilderbase-3/)

**Namespace**
* [Vendr.Core.Composing](../)

### Constructors

#### PipelineTaskCollectionBuilder&lt;TCollection,TItem&gt;

The default constructor.

```csharp
public PipelineTaskCollectionBuilder()
```


### Methods

#### CreateCollection

```csharp
public override TCollection CreateCollection(IServiceProvider factory)
```


---

#### OnFail&lt;T&gt;

```csharp
public PipelineTaskCollectionBuilder<TCollection, TItem> OnFail<T>()
    where T : IPipelineAction<TItem>
```


---

#### RegisterWith

```csharp
public override void RegisterWith(IServiceCollection services)
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->