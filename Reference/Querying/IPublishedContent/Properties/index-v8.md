---
versionFrom: 8.8.0
---

# IPublishedContent Property Access

## Umbraco Properties

Built-in properties, which exists on all content objects by default

Common Examples

```csharp
@* gets the current page Url *@
@Model.Url

@* gets the Creation date, and formats it to a short date *@
@Model.CreateDate.ToString("D")

@* Outputs the name of the parent if it exists *@
@if(Model.Parent != null){
    <h1>@Model.Parent.Name</h1>
}
```

### .Id

Returns the unique Id for the current content item

```csharp
@Model.Id
```

### .Name

Returns the Name of the current content item in the current culture

```csharp
@Model.Name
```

### .Name(string culture = null)

Returns the Name of the current content item in the specified culture, null falls back to the current culture

```csharp
@Model.Name()
```

### .ContentType

Returns a strongly typed 'PublishedContentType' object representing the content type the IPublishedContent item is based on, that gives access to the alias

```csharp
@Model.ContentType
@Model.ContentType.Alias
```

### .GetCultureFromDomains()

Returns a culture from a configured domain in the content tree.

```csharp
@Model.GetCultureFromDomains(Model.Url)
```

### .Parent

Returns the parent content item

```csharp
@Model.Parent
@Model.Parent.Name
```

### .Path

Returns a comma delimited string of Node Ids that represent the path of content items back to root.

```csharp
@Model.Path
```

### .Level

Returns the Level (depth) this content item is in its tree path

```csharp
@Model.Level
```

### .TemplateId

Returns the id of the default Template object used with this content item.

```csharp
@Model.TemplateId
```

There are extension methods to retrieve template alias (Model.GetTemplateAlias())

### .SortOrder

Returns the index the page is on, compared to its siblings

```csharp
@Model.SortOrder
```

### .Url - (Obsolete)

Returns the complete Url to the page in the current culture

```csharp
@Model.Url
```

### .Url(string culture = null, UrlMode mode = UrlMode.Default) - (Extension method)

Returns the Url to the page.

This can be used to get the Url for a specific culture, and for getting the Url in a specific (mode)[https://our.umbraco.com/apidocs/v8/csharp/api/Umbraco.Core.Models.PublishedContent.UrlMode.html].

```csharp
@Model.Url()
```

**Example:** Getting a Danish Url for a site where a Danish language has been set up.

```csharp
@Model.Url("dk")
```

**Example:** Getting an Absolute Danish Url for a site where a Danish language has been set up.

```csharp
@Model.Url("dk", UrlMode.Absolute)
```

### .UrlSegment

Returns the Url encoded name of the page (slug) of the current culture

```csharp
@Model.UrlSegment
```

### .UrlSegment(string culture = null)

Returns the Url encoded name of the page (slug) of the specified culture

```csharp
@Model.UrlSegment()
```

### .WriterId

Returns the id of the Umbraco backoffice user that performed the last update operation on the content item.

```csharp
@Model.WriterId
```

### .WriterName

Returns the name of the Umbraco backoffice user that performed the last update operation on the content item.

_deprecated_ Will be removed in future versions of Umbraco, use WriterName(IUserService) instead

```csharp
@Model.WriterName
```

### .WriterName(IUserService)

Returns the name of the Umbraco backoffice user that initially created the content item.

```csharp
@Model.WriterName(IUserService)
```

### .CreatorId

Returns the id of the Umbraco backoffice user that initially created the content item

```csharp
@Model.CreatorId
```

### .CreatorName

Returns the name of the Umbraco backoffice user that initially created the content item.

_deprecated_ Will be removed in future versions of Umbraco, use CreatorName(IUserService) instead

```csharp
@Model.CreatorName
```

### .CreatorName(IUserService)

Returns the name of the Umbraco backoffice user that initially created the content item.

```csharp
@Model.CreatorName(IUserService)
```

### .CreateDate

Returns the DateTime the page was created

```csharp
@Model.CreateDate
@* gets the Creation date, and formats it to a short date *@
@Model.CreateDate.ToString("D")
```

### .UpdateDate

Returns the DateTime the page was modified

```csharp
@Model.UpdateDate
@* gets the Update/Modified date, and formats it to a short date *@
@Model.UpdateDate.ToString("D")
```

---

## Custom properties

All content and media items contain a reference to all the data defined by their document type.
Custom property access is achieved using variations of the method: `Value`

### Model.Value(string)

Returns the property value for the specified property alias

```csharp
@*Get the property with alias: "siteName" from the current page  *@
@Model.Value("siteName")
```

The type returned of this property value is `object` which is fine in most cases since when using
the above syntax, Razor will automatically execute a `ToString()` on the result value.

See `Model.Value<T>(string)` for how to return a strongly typed object for the property

### Model.Value&lt;T>(string)

Returns the property value for the specified property alias converted to 'T' - the requested output type of the property value.

For example, to return the `string` result of "siteName":

```csharp
@(Model.Value<string>("siteName"))
```
Or to return a collection of `IPublishedContent` for a multiple media picker

```csharp
var mediaItems = Model.Value<IEnumerable<IPublishedContent>>("mediaIds");
```

Another example might be if a property editor stores a JSON value, it might then support converting to a custom
strongly typed model, or at the very least the JSON would be convertible to a `JObject` instance, for example:

```csharp
@(Model.Value<NestedContentModel>("nestedContent"))
```

or

```csharp
@(Model.Value<JObject>("nestedContent"))
```

## Fallbacks

If the current content item doesn't have the requested value, use an alternative 'fallback' value in its place.

### Fallback to Default Value

If a content page has a 'title' property, to fallback to use the 'Name' of the content item if the 'title' is not populated. Set the Fallback type to be Fallback.ToDefaultValue, and set the DefaultValue accordingly:

```csharp
@Model.Value<string>("title", fallback: Fallback.ToDefaultValue, defaultValue: Model.Name);
```

or to a specific value

```csharp
@Model.Value<string>("author", fallback: Fallback.ToDefaultValue, defaultValue: "Team Reporter");
```

### Fallback to Ancestors

Look for a property value on the current page. If it doesn't exist look for the property value on the parent page. Then the parent's parent page and so on. All the way up the content tree - this approach allows the specification of 'global property values' that can then be overridden in different sections or on individual pages.

```csharp
@Model.Value("propertyAlias", fallback: Fallback.ToAncestors)
```

### Fallback to Language

If working with variants - fallback to a different language value - if perhaps the value hasn't been populated yet for the current language:

```csharp
Model.Value("pageTitle", "fr", fallback: Fallback.ToLanguage)
```

### Combining the Fallback options

Use Fallback.To() to 'combine' Fallback options.

The following would first look for a 'title' property on all ancestors, before defaulting to the current page's name:

```csharp
@Model.Value("title", fallback: Fallback.To(Fallback.Ancestors, Fallback.DefaultValue), defaultValue: Model.Name)
```

## Property Methods

**There are a few helpful methods to help check if a property exists, has a value or is null.**

### .HasProperty(string propertyAlias)

Returns a boolean value representing if the IPublishedContent has a property with the specified alias.

### .HasValue(string propertyAlias)

Returns a boolean value representing if the IPublishedContent property has had a value set.

It's possible to use 'Fallbacks' with HasValue:

```csharp
bool hasPageTitleSetSomewhere = Model.HasValue("pageTitle",fallback: Fallback.ToAncestors);
```