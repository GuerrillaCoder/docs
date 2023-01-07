---
title: Blazor Tailwind Components
---

<script setup>
import { Icon } from "@iconify/vue"
</script>

ServiceStack.Blazor high-productivity components enable the rapid development of CRUD UIs in Blazor Server and WASM Apps:

<div class="my-8 flex justify-center">
    <iframe class="video-hd" src="https://www.youtube.com/embed/iKpQI2233nY" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>


<div id="blazor-component-gallery" class="mt-16 relative bg-white py-4">
  <div class="mx-auto max-w-md px-4 text-center sm:max-w-3xl sm:px-6 lg:max-w-7xl lg:px-8">
    <p class="mt-2 text-3xl font-extrabold tracking-tight text-gray-900 sm:text-4xl">Blazor Gallery</p>
    <p class="mx-auto mt-5 max-w-prose text-xl text-gray-500">
      Discover ServiceStack.Blazor Rich UI Components and Integrated Features
    </p>
  </div>
</div>

[![](/images/blazor/gallery-splash.png)](https://blazor-gallery.servicestack.net)

As our components support both hosting models we're maintaining identical Gallery sites running on both **Blazor Server** and **WASM**:

<div class="mb-16 mx-auto mt-5 max-w-md sm:flex sm:justify-center md:mt-8">
  <div class="rounded-md shadow">
    <a href="https://blazor-gallery.servicestack.net" class="flex w-full items-center justify-center rounded-md border border-transparent bg-indigo-600 px-8 py-3 text-base font-medium text-white hover:bg-indigo-700 md:py-4 md:px-10 md:text-lg hover:no-underline">
      Blazor Server
    </a>
  </div>
  <div class="mt-3 rounded-md shadow sm:mt-0 sm:ml-3">
    <a href="https://blazor-gallery.jamstacks.net" class="flex w-full items-center justify-center rounded-md border border-transparent bg-white px-8 py-3 text-base font-medium text-indigo-600 hover:bg-gray-50 md:py-4 md:px-10 md:text-lg hover:no-underline">
      Blazor WASM
    </a>
  </div>
</div>

For a closer look at ServiceStack.Blazor Components in action, download & run them to see how good they'll run in your Environment:

<div class="flex flex-col">
  <a href="https://github.com/NetCoreApps/BlazorGallery" class="text-xl text-gray-800">
    <Icon icon="simple-icons:github" class="w-6 h-6 mr-2 align-text-bottom" />
    <span>NetCoreApps/BlazorGallery</span>
  </a>
  <a href="https://github.com/NetCoreApps/BlazorGalleryWasm" class="mt-2 text-xl text-gray-800">
    <Icon icon="simple-icons:github" class="w-6 h-6 mr-2 align-text-bottom" />
    <span>NetCoreApps/BlazorGalleryWasm</span>
  </a>
</div>



<div class="pt-8 my-8 ml-20 flex flex-col items-center">
    <div>
        <Icon icon="ic:outline-dark-mode" class="w-40 h-40 text-gray-800 mr-8" />
    </div>
    <h2 id="darkmode" class="border-none text-4xl sm:text-5xl md:text-6xl tracking-tight font-extrabold">
        <span class="text-gray-800 mr-6">Dark Mode</span>
    </h2>
</div>

All ServiceStack.Blazor components take advantage of Tailwind DarkMode support to include full support for Dark Mode.

![](/images/blazor/dark-and-light-mode.png)

[Tailwind](https://tailwindcss.com) has revolutionized how we style our Web Apps with its [mobile first](https://tailwindcss.com/#mobile-first) design system that's dramatically simplified creating maintainable responsive Web Apps. It also excels at adding support for [Dark Mode](https://tailwindcss.com/#dark-mode) with its first-class **dark:** modifier allowing the use of standard tailwind classes to specify what elements should look like when viewed in **Dark Mode**, e.g:

<div class="not-prose relative bg-slate-50 rounded-xl overflow-hidden dark:bg-slate-800/25"><div style="background-position:10px 10px" class="absolute inset-0 bg-grid-slate-100 [mask-image:linear-gradient(0deg,#fff,rgba(255,255,255,0.6))] dark:bg-grid-slate-700/25 dark:[mask-image:linear-gradient(0deg,rgba(255,255,255,0.1),rgba(255,255,255,0.5))]"></div><div class="relative rounded-xl overflow-auto">
  <div class="grid grid-cols-1 sm:grid-cols-2">
    <div class="p-8 pt-7">
      <p class="mb-2 text-sm font-medium text-slate-500">Light mode</p>
      <div class="bg-white rounded-lg px-6 py-8 ring-1 ring-slate-900/5 shadow-xl">
        <div>
          <span class="inline-flex items-center justify-center p-2 bg-indigo-500 rounded-md shadow-lg">
            <svg class="h-6 w-6 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"></path></svg>
          </span>
        </div>
        <h3 class="mt-5 text-base font-medium text-slate-900 tracking-tight">Writes Upside-Down</h3>
        <p class="mt-2 text-sm text-slate-500">
          The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.
        </p>
      </div>
    </div>
    <div class="bg-slate-900 p-8 pt-7">
      <p class="mb-2 text-sm font-medium text-slate-400">Dark mode</p>
      <div class="bg-slate-800 rounded-lg px-6 py-8 ring-1 ring-slate-900/5 shadow-xl">
        <div>
          <span class="inline-flex items-center justify-center p-2 bg-indigo-500 rounded-md shadow-lg">
            <svg class="h-6 w-6 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"></path></svg>
          </span>
        </div>
        <h3 class="mt-5 text-base font-medium text-white tracking-tight">Writes Upside-Down</h3>
        <p class="mt-2 text-sm text-slate-400">
          The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.
        </p>
      </div>
    </div>
  </div>
</div><div class="absolute inset-0 pointer-events-none border border-black/5 rounded-xl dark:border-white/5"></div></div>

```html
<div class="bg-white dark:bg-slate-800 rounded-lg px-6 py-8 ring-1 ring-slate-900/5 shadow-xl">
  <div>
    <span class="inline-flex items-center justify-center p-2 bg-indigo-500 rounded-md shadow-lg">
      <svg class="h-6 w-6 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true"><!-- ... --></svg>
    </span>
  </div>
  <h3 class="text-slate-900 dark:text-white mt-5 text-base font-medium tracking-tight">Writes Upside-Down</h3>
  <p class="text-slate-500 dark:text-slate-400 mt-2 text-sm">
    The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.
  </p>
</div>
```

### View ServiceStack.Blazor in Dark Mode

We're happy to announce that Dark Mode support is included in **all ServiceStack.Blazor components** and all Blazor Tailwind project templates where you'll be able to toggle on/off Dark Mode with the new `<DarkModeToggle>` component. Checkout this video to see how beautiful Dark Mode looks like in the latest ServiceStack.Blazor Components and Tailwind project templates:

<div class="my-8 flex justify-center">
    <iframe class="video-hd" src="https://www.youtube.com/embed/8nwpC_B4AC4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

For a more interactive view, use the right Dark Mode toggle to turn on/off Dark Mode in the embedded [Blazor Gallery Contacts Page](https://blazor-gallery.jamstacks.net/grid/contacts-meta):

<iframe src="https://blazor-gallery.jamstacks.net/grid/contacts-meta/embed" class="w-full border-none h-[970px] w-[1330px] -ml-40"></iframe>

Dark Mode is all implemented with CSS, controlled by toggling the **dark** class on the `<html class="dark">` element, `<DarkModeToggle>` also saves this user preference in `localStorage` where it's preserved across browser restarts.

### View in Dark Mode

The Blazor Tailwind templates also include the ability to override the users color scheme preference and open a page in dark or light mode with the 
`?dark` and `?light` query params:

<div class="not-prose relative">
  <div class="grid grid-cols-1 sm:grid-cols-2 text-center">
    <div>
        <a class="flex flex-col" href="https://blazor-server.jamstacks.net/?light">
            <div class="py-4">blazor-server.jamstacks.net/?light</div>
            <img class="rounded-xl overflow-hidden" src="/images/blazor/blazor-gallery-light.png">
        </a>
    </div>
    <div>
        <a class="flex flex-col" href="https://blazor-server.jamstacks.net/?dark">
            <div class="py-4">blazor-server.jamstacks.net/?dark</div>
            <img class="rounded-xl overflow-hidden" src="/images/blazor/blazor-gallery-dark.png">
        </a>
    </div>
  </div>
</div>

### Force Dark Mode

If your App is best viewed in Dark Mode you can force it to use Dark Mode with `JS.init()` when initializing ServiceStack.Blazor's JS library in Blazor Server's **_Layout.cshtml** or Blazor WASM's **index.html**, e.g:

```html
<script src="_framework/blazor.server.js"></script>
<script src="/js/servicestack-blazor.js"></script>
<script>JS.init({ colorScheme:'dark' })</script>
```

<p class="hide-h2"></p>

## Blazor Tailwind Components

<div id="blazor-components" class="mt-16 mb-8 ml-20 flex flex-col items-center">
    <div>
        <Icon icon="simple-icons:blazor" class="w-40 h-40 text-purple-600 mr-8" />
        <Icon icon="logos:tailwindcss-icon" class="w-44 h-44" />
    </div>
    <h2 class="border-none text-4xl sm:text-5xl md:text-6xl tracking-tight font-extrabold">
        <span class="text-purple-600 mr-6">Blazor</span>
        <span class="mr-6" style="color:#44A8B3">Tailwind</span>
        <span class="text-gray-800">Components</span>
    </h2>
</div>

We encourage you to explore to the Blazor Gallery websites for the full preview, but we'll look at some of the Components here to give you some idea of the functionality available.

### DataGrid

`DataGrid` is a versatile Component we expect to be heavily used for rendering any typed collection:

```cshtml
<DataGrid Model="Track" Items=@Track.Results />
```

Which by default renders results in a striped Tailwind Table:

![](/images/blazor/datagrid-tracks.png)

Whose appearance can be styled to support many of the [Tailwind Table Styles](https://tailwindui.com/components/application-ui/lists/tables) with the `TableStyles` Flag enum, e.g:

```cshtml
<DataGrid Model="Track" Items=@Track.Results TableStyle="TableStyle.VerticalLines" />

<DataGrid Model="Track" Items=@Track.Results TableStyle="TableStyle.WhiteBackground" />

<DataGrid Model="Track" Items=@Track.Results TableStyle="TableStyle.FullWidth" />

<DataGrid Model="Track" Items=@Track.Results 
          TableStyle="TableStyle.UppercaseHeadings | TableStyle.FullWidth | TableStyle.VerticalLines" />
```

![](/images/blazor/datagrid-table-styles.png)

It's a highly versatile component where you'll be able to control which columns are displayed and how they're formatted using `<Column>` definitions, e.g. here's how we can customize the table to look like Blazor's [FetchData.cshtml](https://github.com/SteveSanderson/Blazor/blob/master/samples/ClientServerApp/ClientServerApp.Client/FetchData.cshtml) tabular results:

```cshtml
<DataGrid Items=@forecasts class="max-w-screen-md" TableStyle="TableStyle.StripedRows | TableStyle.UppercaseHeadings">
    <Column Field="(WeatherForecast x) => x.Date" Format="dd/MM/yyyy" />
    <Column Title="Temp. (C)" Field="(WeatherForecast x) => x.TemperatureC" />
    <Column Title="Temp. (F)" Field="(WeatherForecast x) => x.TemperatureF" />
    <Column Field="(WeatherForecast x) => x.Summary" />
</DataGrid>

@code {
    List<WeatherForecast> forecasts = new();

    protected override async Task OnInitializedAsync()
    {
        forecasts = await Http.GetFromJsonAsync<List<WeatherForecast>>("data/weather.json") ?? new();
    }
}
```

[![](/images/blazor/datagrid-weather.png)](https://blazor-gallery.servicestack.net/fetchdata)


Here's a more advanced example showing how to implement a responsive DataGrid by utilizing custom Header and Table Cell templates to define what columns and Headers are visible at different responsive breakpoints and how to enable different features like **Row Selection** and **Filtering** and examples of handling the Row and Header selected events App's can use for executing custom logic:

```cshtml
<DataGrid Model="Booking" Items=@Items AllowSelection="true" AllowFiltering="true"
          HeaderSelected="HandleSelectedHeader" RowSelected="HandleSelectedRow">
    <Column Field="(Booking x) => x.Id" class="text-gray-900" />
    <Column Field="(Booking x) => x.Name" VisibleFrom="Breakpoint.ExtraLarge" />
    <Column Field="(Booking x) => x.RoomType">
        <Header>
            <span class="hidden lg:inline">Room </span>Type
        </Header>
    </Column>
    <Column Field="(Booking x) => x.RoomNumber">
        <Header>
            <span class="hidden lg:inline">Room </span>No
        </Header>
    </Column>
    <Column Field="(Booking x) => x.Cost" Format="C" />
    <Column Field="(Booking x) => x.BookingStartDate" Formatter="FormatDate" VisibleFrom="Breakpoint.Small">
        <Header>
            Start<span class="hidden lg:inline"> Date</span>
        </Header>
    </Column>
    <Column Field="(Booking x) => x.BookingEndDate" Formatter="FormatDate" VisibleFrom="Breakpoint.ExtraLarge">
        <Header>
            End<span class="hidden lg:inline"> Date</span>
        </Header>
        <Template>@{ var booking = context as Booking; }@booking.BookingEndDate?.ToString("D")
        </Template>
    </Column>
    <Column Title="Employee" Field="(Booking x) => x.CreatedBy" VisibleFrom="Breakpoint.Medium" />
</DataGrid>

@code {
    public List<Booking> Items { get; set; } = new() {
        Create.Booking("First Booking!",  RoomType.Queen,  10, 100, "employee@email.com", "BOOK10"),
        Create.Booking("Booking 2",       RoomType.Double, 12, 120, "manager@email.com",  "BOOK25"),
        Create.Booking("Booking the 3rd", RoomType.Suite,  13, 130, "employee@email.com", "BOOK50"),
    };

    string FormatDate(object o) => o is DateTime d ? d.ToShortDateString() : "";

    public async Task HandleSelectedHeader(Column<Booking> item)
    {
        await JS.Log(item.Name);
    }

    public async Task HandleSelectedRow(Booking x)
    {
        await JS.Log(x);
    }
}
```

:::tip
Resize webpage to preview its responsive appearance and different resolution breakpoints
:::

<iframe class="w-full border-none" style="height:385px" src="https://blazor-gallery.jamstacks.net/gallery/datagrid/responsive"></iframe>

### AutoQueryGrid

The functionality and extensibility in `DataGrid` lays the foundation for higher-level components like `AutoQueryGrid` which makes use of it to enable its Auto UI around [AutoQuery CRUD](/autoquery-crud) Services. 

### AutoQueryGrid Read Only

At a minimum AutoQueryGrid requires the AutoQuery APIs it should call to implement its functionality, so you can implement a **read-only** grid by only
specifying the AutoQuery API to query a data model, e.g:

```csharp
<AutoQueryGrid Model="Booking" Apis="Apis.AutoQuery<QueryBookings>()" />
```

This one AutoQuery API is enough to power a functional read-only UI enabling multi flexible querying capabilities, paging, custom column selection and the ability to export the desired filtered resultset to .csv which can be open in Excel or copy the API URL Apps can use to consume the JSON API results:

<iframe class="w-full border-none" style="height:430px" src="https://blazor-gallery.jamstacks.net/gallery/autoquerygrid/readonly"></iframe>

### AutoQueryGrid CRUD

Full CRUD functionality can be enabled by specifying the AutoQuery CRUD APIs for a specified data model, e.g:

```csharp
<AutoQueryGrid Model="Booking" Apis="Apis.AutoQuery<QueryBookings,CreateBooking,UpdateBooking,DeleteBooking>()" />
```

[![](/images/blazor/autoquerygrid-crud.png)](https://blazor-gallery.jamstacks.net/gallery/autoquerygrid/crud)

### Customizable Columns

As `AutoQueryGrid` builds on `DataGrid` it also inherits its customizable option allowing for [customizable responsive columns](https://blazor-gallery.servicestack.net/gallery/autoquerygrid), e.g:

```cshtml
<AutoQueryGrid Model="Booking" Apis="Apis.AutoQuery<QueryBookings,CreateBooking,UpdateBooking,DeleteBooking>()"
               AllowSelection="true" AllowFiltering="true"
               HeaderSelected="OnSelectedHeader" RowSelected="OnSelectedRow">
    <Columns>
        <!-- Custom class -->
        <Column Field="(Booking x) => x.Id" class="text-gray-900" />
        <!-- Only show from Tailwind's xl responsive Breakpoint -->
        <Column Field="(Booking x) => x.Name" VisibleFrom="Breakpoint.ExtraLarge" />
        <!-- Custom Header collapsing 'Room' below 'lg' responsive breakpoint -->
        <Column Field="(Booking x) => x.RoomType">
            <Header>
                <span class="hidden lg:inline">Room </span>Type
            </Header>
        </Column>
        <!-- Custom Header collapsing 'Room' below 'lg' responsive breakpoint -->
        <Column Field="(Booking x) => x.RoomNumber">
            <Header>
                <span class="hidden lg:inline">Room </span>No
            </Header>
        </Column>
        <!-- Custom string Format -->
        <Column Field="(Booking x) => x.Cost" Format="C" />
        <!-- Custom C# Formatter -->
        <Column Field="(Booking x) => x.BookingStartDate" Formatter="FormatDate" VisibleFrom="Breakpoint.Small">
            <Header>
                Start<span class="hidden lg:inline"> Date</span>
            </Header>
        </Column>
        <!-- Custom Header and Cell Value -->
        <Column Field="(Booking x) => x.BookingEndDate" VisibleFrom="Breakpoint.ExtraLarge2x">
            <Header>
                End<span class="hidden lg:inline"> Date</span>
            </Header>
            <Template>
                @context.BookingEndDate?.ToString("D")
            </Template>
        </Column>
        <!-- Custom Title and Complex Type Cell with Reference Link -->
        <Column Title="Voucher" Field="(Booking x) => x.Discount" VisibleFrom="Breakpoint.ExtraLarge">
            <Template>
@if (context.Discount != null)
{
    <TextLink class="flex items-end" href=@($"/gallery/autoquerygrid/coupons?Id={context.Discount.Id}")>
        <PreviewFormat Value=@context.Discount />
    </TextLink>
}          </Template>
        </Column>
    </Columns>
</AutoQueryGrid>
```

Customizing how and when columns are rendered at different breakpoints using different formatting options and custom table header and cell templates:

[![](/images/blazor/autoquerygrid-responsive.png)](https://blazor-gallery.jamstacks.net/gallery/autoquerygrid/responsive)

### Declarative Customizations

The columns can also be customized declaratively using the `[Format]` Metadata Attribute on the Model type:

```csharp
public class Contact : AuditBase
{
    [AutoIncrement]
    public int Id { get; set; }

    [Format(FormatMethods.IconRounded)]
    public string ProfileUrl { get; set; }

    public string FirstName { get; set; }
    public string LastName { get; set; }

    [Format(FormatMethods.Currency)]
    public int? SalaryExpectation { get; set; }

    [Format(FormatMethods.LinkEmail, Options = 
        @"{target:'_self',subject:'New Job Opportunity',
           body:'We have an exciting new opportunity...', cls:'text-green-600'}")]
    public string Email { get; set; }

    [Format(FormatMethods.LinkPhone)]
    public string Phone { get; set; }
}
```

Which can change how results are formatted in the data grid results:

[![](/images/blazor/autoquerygrid-metadata.png)](https://blazor-gallery.jamstacks.net/grid/contacts-meta)

Whilst the `[Input]` and `[FieldCss]` attributes on the AutoQuery CRUD DTOs:

```csharp
public class UpdateContact : IPatchDb<Contact>, IReturn<Contact>
{
    public int Id { get; set; }

    [ValidateNotEmpty]
    public string? FirstName { get; set; }

    [ValidateNotEmpty]
    public string? LastName { get; set; }

    [Input(Type = "file"), UploadTo("profiles")]
    public string? ProfileUrl { get; set; }
    
    public int? SalaryExpectation { get; set; }

    [ValidateNotEmpty]
    public string? JobType { get; set; }

    public int? AvailabilityWeeks { get; set; }
    public EmploymentType? PreferredWorkType { get; set; }
    public string? PreferredLocation { get; set; }

    [ValidateNotEmpty]
    public string? Email { get; set; }
    public string? Phone { get; set; }
 
    [Input(Type="textarea")]
    [FieldCss(Field="col-span-12 text-center", Input="h-48", Label="text-xl text-indigo-700")]
    public string? About { get; set; }
}
```

Can customize how forms are rendered, e.g:

[![](/images/blazor/autoquerygrid-metadata-form.png)](https://blazor-gallery.jamstacks.net/grid/contacts-meta)


### ToolbarButtons

The `<ToolbarButtons>` element can be used to customize the AutoQueryGrid to add your own custom Toolbar buttons, e.g:

```razor
<AutoQueryGrid>
  <ToolbarButtons>
    <div class="pl-2"><button>1</button></div>
    <div class="pl-2"><button>2</button></div>
  </ToolbarButtons>
</AutoQueryGrid>
```

 Enabling complete control over the Toolbar as all existing toolbar buttons can be removed with [AutoQueryGrid parameters](https://reference.servicestack.net/api/ServiceStack.Blazor.Components.Tailwind/AutoQueryGrid%60Model%60).

### Custom Edit and Create Forms

The `<CreateForm>` and `<EditForm>` elements can be used to replace the default [Auto Forms](https://blazor-gallery.jamstacks.net/gallery/autoform) used in creating and editing rows when more advanced or customized functionality is needed.

With this feature we can create a Custom AutoQueryGrid component that uses Custom Edit & Create Forms when selecting and adding new records and also customize the Grid results displayed with the new `ConfigureQuery` parameter to ensure results are filtered to the selected Tenant records:

```razor
<AutoQueryGrid @ref=@grid Model="Item" Apis="Apis.AutoQuery<QueryItems,NewItem,EditItem>()" ConfigureQuery="Configure">
    <CreateForm>
        <div class="relative z-10">
            <div class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10 sm:pl-16">
                <CustomCreateItem OnClose="grid!.OnEditDone" />
            </div>
        </div>
    </CreateForm>
    <EditForm>
        <div class="relative z-10">
            <div class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10 sm:pl-16">
                <CustomEditItem Item="context" OnClose="grid!.OnEditDone" />
            </div>
        </div>
    </EditForm>
</AutoQueryGrid>

@code {
    AutoQueryGrid<Creative>? grid;
    [Parameter, SupplyParameterFromQuery] public int? TenantId { get; set; }

    void Configure(QueryBase query)
    {
        query.AddQueryParam("TenantId", TenantId);
    }
}
```

### Managing Filters & Preferences

By default the AutoQueryGrid displays the user's selected columns and query limit preferences which are persisted in localStorage. 
They can be overridden with the new **Prefs** attribute which has different ergonomic methods for configuration within an attribute:

To limit the Query Results Limit:

```razor
<AutoQueryGrid @ref=@grid Model="Contact" Apis="Apis.AutoQuery<QueryContacts,CreateContact,UpdateContact>()"
               Prefs="ApiPrefs.Create(take:10)" />
```

To limit which columns are displayed in the Query Results:

```razor
<AutoQueryGrid @ref=@grid Model="Contact" Apis="Apis.AutoQuery<QueryContacts,CreateContact,UpdateContact>()"
               Prefs="ApiPrefs.Columns(nameof(Contact.Id), nameof(Contact.LastName))" />
```

```razor
<AutoQueryGrid @ref=@grid Model="Contact" Apis="Apis.AutoQuery<QueryContacts,CreateContact,UpdateContact>()"
               Prefs="ApiPrefs.Columns<Contact>(x => new { x.Id, x.LastName, x.Email })" />
```

To configure both Query Limit and Selected Columns:

```razor
<AutoQueryGrid @ref=@grid Model="Contact" Apis="Apis.AutoQuery<QueryContacts,CreateContact,UpdateContact>()"
               Prefs="ApiPrefs.Create(take:10, columns:new(){ nameof(Contact.Id), nameof(Contact.LastName) })" />
```

```razor
<AutoQueryGrid @ref=@grid Model="Contact" Apis="Apis.AutoQuery<QueryContacts,CreateContact,UpdateContact>()"
               Prefs="ApiPrefs.Configure(x => { x.Take = 5; x.SelectedColumns=new() { nameof(Contact.LastName) }; })"/>
```

In addition the new methods below can be used to clear any user-defined query filters and column preferences:

| Method | Description |
|--|--|
| grid.ClearFiltersAsync()     | Remove user-defined Filters |
| grid.ResetPreferencesAsync() | Remove user-defined Filters and Column Preferences |


### Disable Column Filtering

By default Filtering and Sorting are disabled for complex type columns, they can also be explicitly disabled per column with `AllowFiltering`, e.g:

```razor
<AutoQueryGrid>
    <Column Field="(Contact x) => x.Phone" AllowFiltering="false" />
<AutoQueryGrid>
```

### Changing AutoQueryGrid Defaults

A lot of AutoQueryGrid's UI is customizable allowing you to easily toggle on/off UI features as needed, if you have a consistent style you wish to enforce you can 
change the defaults of every AutoQueryGrid component with [BlazorConfig](#blazor-config), e.g. you can remove **Copy URL** button and change the default Table style to use Uppercase Headings with:

```csharp
BlazorConfig.Set(new() {
    //...
    AutoQueryGridDefaults = new() {
        TableStyle = TableStyle.StripedRows | TableStyle.UppercaseHeadings,
        ShowCopyApiUrl = false,
    }
});
```

Which will change the appearance of every `AutoQueryGrid` Component used in the App unless overridden.

### AutoQueryGrid Gallery

As AutoQueryGrid is a core component for the rapid development of Apps we're maintaining a dedicated section showcasing their different features at [blazor-gallery.servicestack.net/grid](https://blazor-gallery.servicestack.net/grid):

[![](/images/blazor/autoquerygrid-more.png)](https://blazor-gallery.servicestack.net/grid)

## Modal Lookups

To provide an optimal UX for relational fields `AutoQueryGrid` utilizes Modal Lookups for searching and selecting referential data that's automatically inferred from your OrmLite data model relationships, e.g:

```csharp
public class JobApplication : AuditBase
{
    [AutoIncrement]
    public int Id { get; set; }

    [References(typeof(Job))]
    public int JobId { get; set; }
    
    [References(typeof(Contact))]
    public int ContactId { get; set; }
    //...
}
```

Where it will display an enhanced [LookupInput](https://reference.servicestack.net/api/ServiceStack.Blazor.Components.Tailwind/LookupInput) instead of a plain Text Input for the relational `JobId` and `ContactId` fields:

[![](/images/blazor/modalLookup-input.png)](https://blazor-gallery.servicestack.net/grid/job-applications?edit=1)

Which users can use to quickly search for the related record instead of manually inserting Foreign Key Ids:

[![](/images/blazor/modalLookup-dialog.png)](https://blazor-gallery.servicestack.net/grid/job-applications?edit=1)

## File Uploads

Another feature showcased in the above screenshots is support for [Managed File Uploads](/locode/files) which can be declaratively added with the `[Input(Type="file")]` to render the [FileInput](https://reference.servicestack.net/api/ServiceStack.Blazor.Components.Tailwind/FileInput) Component and `[UploadTo]` attribute to specify which File [Upload location](/locode/files#basic-file-upload-example) it should use:

```csharp
public class UpdateJobApplication : IPatchDb<JobApplication>, IReturn<JobApplication>
{
    public int Id { get; set; }
    public int? JobId { get; set; }
    public int? ContactId { get; set; }
    public DateTime? AppliedDate { get; set; }
    public JobApplicationStatus? ApplicationStatus { get; set; }

    [Input(Type = "file"), UploadTo("applications")]
    public List<JobApplicationAttachment>? Attachments { get; set; }
}
```

For a quick primer on using Managed File Uploads to [Upload files from Blazor](/locode/files-blazor) checkout:

<div class="my-16 px-4 sm:px-6">
    <div class="text-center">
      <h1 class="text-4xl tracking-tight font-extrabold text-gray-900 sm:text-5xl">
        <a href="/locode/files-blazor" class="block xl:inline">File Blazor</a>
      </h1>
    </div>
    <div class="my-8">
        <iframe class="video-hd" src="https://www.youtube.com/embed/5sd00MzHpaU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>
</div>

## Auto Forms

The Auto Form components are other high productivity components which can be used to create an automated form based from a Request DTO definition:

```csharp
<AutoCreateForm Model="Booking" ApiType="typeof(CreateBooking)" />
```

[![](/images/blazor/AutoCreateForm.png)](https://blazor-gallery.servicestack.net/gallery/autoform)

### AutoEditForm

Whilst `AutoEditForm` can be used to render an automated form based to update and delete an [AutoQuery CRUD](/autoquery-crud) API:

```csharp
<AutoEditForm Model="Booking" Edit="Model" ApiType="typeof(UpdateBooking)" DeleteApiType="typeof(DeleteBooking)" />

@code {
    Booking Model = Create.Booking("First Booking!", RoomType.Queen, 10, 100, "employee@email.com");
}
```

[![](/images/blazor/AutoEditForm.png)](https://blazor-gallery.servicestack.net/gallery/autoform)

The forms behavior and appearance is further customizable with the [API annotation](/locode/declarative#annotate-apis), declarative [validation](/locode/declarative#type-validation-attributes) and the custom [Field and Input](/locode/declarative#custom-fields-and-inputs) attributes, e.g:

```csharp
[Description("Update an existing Booking")]
[Notes("Find out how to quickly create a <a class='svg-external' target='_blank' href='https://youtu.be/rSFiikDjGos'>C# Bookings App from Scratch</a>")]
[Route("/booking/{Id}", "PATCH")]
[ValidateHasRole("Employee")]
[AutoApply(Behavior.AuditModify)]
public class UpdateBooking : IPatchDb<Booking>, IReturn<IdResponse>
{
    public int Id { get; set; }
    public string? Name { get; set; }
    public RoomType? RoomType { get; set; }
    [ValidateGreaterThan(0)]
    public int? RoomNumber { get; set; }
    [ValidateGreaterThan(0)]
    public decimal? Cost { get; set; }
    public DateTime? BookingStartDate { get; set; }
    public DateTime? BookingEndDate { get; set; }
    [Input(Type = "textarea")]
    public string? Notes { get; set; }
    public bool? Cancelled { get; set; }
}
```


Both AutoForm components will render the Forms UI in a Slide Over dialog and includes built-in support for calling the API to update or edit the record with integrated contextual validation, reporting any field validation errors alongside their Input controls.

### AutoFormFields

If more advanced customization of a Forms appearance and behavior is required, you can use `AutoFormFields` to just render the Form's fields (including Validation binding) that can be used to populate a Request DTO that your App can handle sending, e.g:

[![](/images/blazor/AutoFormFields.png)](https://blazor-gallery.servicestack.net/gallery/autoform)

```csharp
<form @onsubmit="submit" @onsubmit:preventDefault>
    <div class="shadow sm:overflow-hidden sm:rounded-md max-w-screen-lg">
        <div class="space-y-6 bg-white py-6 px-4 sm:p-6">
            <div>
                <h3 class="text-lg font-medium leading-6 text-gray-900">@(ApiType.GetDescription())</h3>
                <p class="notes mt-1 text-sm text-gray-500">
                    @((MarkupString)ApiType.GetNotes())
                </p>
            </div>

            <AutoFormFields Type="typeof(Booking)" Api="Api" FormLayout="FormLayout" ModelDictionary="ModelDictionary"/>

        </div>
        <div class="bg-gray-50 px-4 py-3 text-right sm:px-12">
            <PrimaryButton type="submit" onclick="submit">Save</PrimaryButton>
        </div>
    </div>
</form>

@code {
    [Inject] public JsonApiClient? Client { get; set; }
    IHasErrorStatus? Api { get; set; }
    Type ApiType = typeof(UpdateBooking);
    List<InputInfo>? FormLayout { get; set; }
    Dictionary<string, object> ModelDictionary { get; set; } = new();
    MetadataType MetadataType => ApiType.ToMetadataType();

    Booking Edit = Create.Booking("First Booking!", RoomType.Queen, 10, 100, "employee@email.com");

    protected override async Task OnParametersSetAsync()
    {
        await base.OnParametersSetAsync();
        Api = null;

        ModelDictionary = Edit.ToModelDictionary();
        FormLayout ??= MetadataType.CreateFormLayout<Booking>();
    }

    async Task submit()
    {
        var request = ModelDictionary.FromModelDictionary<UpdateBooking>();
        Api = await Client!.ApiAsync(request);
    }
}
```

## Autocomplete

The `<Autocomplete>` component provides a user friendly Input for being able to search and quickly select items, that includes support for rich templated content, custom matching and infinite scrolling that avoids pre-loading the entire bound list of items. 

Instead of being populated with a fixed List of strings or Key Value Pairs the Autocomplete component can bind directly to a list of POCOs to render its templated content where you'll be able to specify a custom `Match` filter to control which filtered items are displayed, that it can fuzzy match on single or multiple POCO properties.

### Single Contact

Here's a simple Autocomplete example that binds to a **simple** `Contact` from a `List<Contact>` in **allContacts**:

```razor
<Autocomplete T="Contact" Options="allContacts" @bind-Value="simple" Label="Single Contact"
    Match="(x, value) => x!.DisplayName.Contains(value, StringComparison.OrdinalIgnoreCase)"
    placeholder="Select Contact">
    <Item>
        <span class="block truncate">@context!.DisplayName</span>
    </Item>
</Autocomplete>
```

### Single Contact with Icon

The item content is templated allowing for rich content which can be used to display a Contact's profile picture and name:

```razor
<Autocomplete T="Contact" Options="allContacts" @bind-Value="contact" Label="Single Contact with Icon"
    Match="(x, value) => x!.DisplayName.Contains(value, StringComparison.OrdinalIgnoreCase)"
    placeholder="Select Contact">
    <Item>
        <div class="flex items-center">
            <Icon class="h-6 w-6 flex-shrink-0 rounded-full" Src=@context.ProfileUrl />
            <span class="ml-3 truncate">@context!.DisplayName</span>
        </div>
    </Item>
</Autocomplete>
```

### Multiple Contacts with Icon

It also supports multiple selection by using `@bind-Values` to bind to the `List<Contact>` in **contacts** instead, e.g:

```razor
<Autocomplete Options="allContacts" @bind-Values="contacts" Label="Multiple Contacts with Icon"
    Match="(x, value) => x!.DisplayName.Contains(value, StringComparison.OrdinalIgnoreCase)"
    placeholder="Select Contacts">
    <Item>
        <div class="flex items-center">
            <Icon class="h-6 w-6 flex-shrink-0 rounded-full" Src=@context.ProfileUrl />
            <span class="ml-3 truncate">@context!.DisplayName</span>
        </div>
    </Item>
</Autocomplete>
```

and here's a working example of what they look like together in the same form ([example source code](https://blazor-gallery.jamstacks.net/gallery/inputs)):

<div class="pt-12 flex justify-center">
    <iframe src="https://blazor-gallery.jamstacks.net/gallery/inputs/autocomplete" class="w-[500px] border-none h-[560px]"></iframe>
</div>

## TagInput

The TagInput component is useful for when you want to manage a list of strings like words or tags - an input that's notably lacking in HTML Forms.
Best of all `<TagInput>` functions like any other input where it can be included and customized in declarative forms. 

For example this Update AutoQuery Request DTO:

```csharp
// Customize Edit Forms with [Input] and [FieldCss] attributes 
public class UpdateContact : IPatchDb<Contact>, IReturn<Contact>
{
    public int Id { get; set; }

    [ValidateNotEmpty]
    public string? FirstName { get; set; }

    [ValidateNotEmpty]
    public string? LastName { get; set; }

    [Input(Type = "file"), UploadTo("profiles")]
    public string? ProfileUrl { get; set; }
    
    public int? SalaryExpectation { get; set; }

    [ValidateNotEmpty]
    public string? JobType { get; set; }

    public int? AvailabilityWeeks { get; set; }
    public EmploymentType? PreferredWorkType { get; set; }
    public string? PreferredLocation { get; set; }

    [ValidateNotEmpty]
    public string? Email { get; set; }
    public string? Phone { get; set; }
    
    [Input(Type = "tag"), FieldCss(Field = "col-span-12")]
    public List<string>? Skills { get; set; }}
 
    [Input(Type="textarea")]
    [FieldCss(Field="col-span-12 text-center", Input="h-48", Label="text-xl text-indigo-700")]
    public string? About { get; set; }
}
```

is all that's needed to render an instantly working API-enabled Form with validation binding using 
[Auto Form components](https://blazor-gallery.jamstacks.net/gallery/autoform):

```razor
<AutoEditForm class=@Class Model="Contact" ApiType="typeof(UpdateContact)" Edit=@contact />
```

Which by default renders the form in a SlideOver dialog as seen when editing a row in the [Contacts AutoQueryGrid](https://blazor-gallery.jamstacks.net/grid/contacts-meta?edit=1) component:

<iframe src="https://blazor-gallery.jamstacks.net/grid/contacts-meta/embed?edit=1" class="mt-8 w-full border-none h-[970px] w-[1330px] -ml-40"></iframe>

Alternatively it can be rendered in a traditional **"card"** form layout with the new `FormStyle.Card` option:

```razor
<AutoEditForm class=@Class FormStyle="FormStyle.Card" Model="Contact" ApiType="typeof(UpdateContact)" Edit=@contact />
```

<iframe src="https://blazor-gallery.jamstacks.net/gallery/inputs/tag?layout=ExampleLayout&class=max-w-screen-md+mx-auto" class="mt-8 w-full border-none h-[1570px] w-[1330px] -ml-40"></iframe>

Where it functions the same as other Input components where it can be bound directly to a `List<string>` Request DTO property:

```razor
<form @onsubmit="submit" @onsubmit:preventDefault class=@Class>
<CascadingValue Value=@apiQuery.Error>
    <div class="shadow sm:rounded-md bg-white dark:bg-black">
        <div class="relative px-4 py-5 sm:p-6">
            <fieldset>
                <ErrorSummary Except=@VisibleFields />

                <div class="grid grid-cols-12 gap-6">
                    <div class="col-span-6">
                        <TextInput @bind-Value="request.FirstName" />
                    </div>

                    <div class="col-span-6">
                        <TextInput @bind-Value="request.LastName" />
                    </div>

                    <div class="col-span-12">
                        <TagInput @bind-Value="request.Skills" />
                    </div>
                </div>
            </fieldset>
        </div>
    </div>
</CascadingValue>
</form>
```

### NavList

The NavList component encapsulates Tailwind's beautiful List component which is used extensively in [Blazor Gallery's Navigation](https://blazor-gallery.jamstacks.net/grid):

```razor
<div class="max-w-screen-sm">
    <NavList Title="Explore Blazor Components">
        <NavListItem Title="DataGrid" href="/gallery/datagrid" IconSvg=@Icons.DataGrid>
            DataGrid Component Examples for rendering tabular data
        </NavListItem>
        <NavListItem Title="AutoQuery Grid" href="/gallery/autoquerygrid" IconSvg=@Icons.AutoQueryGrid>
            Instant customizable UIs for calling AutoQuery CRUD APIs
        </NavListItem>
    </NavList>

    <h2 class="mt-8 text-base font-semibold text-gray-500 dark:text-gray-400 flex">
        <span title="Requires Auth"><Icon class="h-6 w-6 mr-2" Svg=@Icons.Padlock /></span>
        Booking APIs
    </h2>
    <NavList>
        <NavListItem Title="Bookings" href="/grid/bookings" Icon=@typeof(Booking).GetIcon()>
            Create and manage Bookings
        </NavListItem>
        <NavListItem Title="Coupons" href="/grid/coupons" Icon=@typeof(Coupon).GetIcon()>
            Create and manage discount Coupons
        </NavListItem>
    </NavList>
</div>
```

Where it will render a list of navigation links with descriptions and icons:

<div class="my-8 flex justify-center">
    <iframe src="https://blazor-gallery.jamstacks.net/gallery/navigation/navlist" class="my-8 w-full h-[510px] border-none"></iframe>
</div>

### Colored Buttons

The `ButtonStyle` on PrimaryButton component can be used to render buttons into Tailwind's different primary colors:

```csharp
<div class="grid gap-4 grid-cols-3">
    <PrimaryButton>Default</PrimaryButton>
    <PrimaryButton Style="ButtonStyle.Blue">Blue</PrimaryButton>
    <PrimaryButton Style="ButtonStyle.Purple">Purple</PrimaryButton>
    <PrimaryButton Style="ButtonStyle.Red">Red</PrimaryButton>
    <PrimaryButton Style="ButtonStyle.Green">Green</PrimaryButton>
    <PrimaryButton Style="ButtonStyle.Sky">Sky</PrimaryButton>
    <PrimaryButton Style="ButtonStyle.Cyan">Cyan</PrimaryButton>
</div>
```

<div class="my-8 flex justify-center">
    <iframe src="https://blazor-gallery.jamstacks.net/gallery/navigation/buttons/styles" class="my-8 w-full h-[160px] border-none"></iframe>
</div>

### Select Input

The `<SelectInput>` `Values` and `Entries` parameters can be used to populate options from an array of string's or KeyValuePair's, it also includes declarative features enabling more capable declarative forms which are typically restricted by the compile-time constant expression limitation of .NET attributes. 

The `EvalAllowableValues` and `EvalAllowableEntries` attribute properties overcomes this limitation by letting you define the Select options with a [#Script](https://sharpscript.net) Expression whose great [.NET scriptability](https://sharpscript.net/docs/script-net) lets you reference your App's .NET instances from a string expression. This feature can then be used to populate declarative Select options from a .NET Instance, e.g:

```csharp
public class CreateModifier : ICreateDb<Modifier>, IReturn<Modifier>
{
    [ValidateNotEmpty]
    public string Name { get; set; }

    [ValidateNotEmpty]
    [Input(Type="select", EvalAllowableValues = "AppData.Categories")]
    public string Category { get; set; }
 
    public string? Description { get; set; }
}
```

That we register as a global variable in our AppHost's `ScriptContext` which we can populate from a dynamic source like a DB Table, e.g:

```csharp
using var db = container.Resolve<IDbConnectionFactory>().Open();
ScriptContext.Args[nameof(AppData)] = new AppData
{
    Categories = db.Column<string>(db.From<Category>().Select(x => x.Name))
};
```

Where it will populate the Select input in all `CreateModifier` Auto Form components:

<div class="mt-8 flex justify-center">
    <img src="/images/blazor/diffusion-CreateModifier.png" class="max-w-screen-md" style="border:1px solid #CACACA">
</div>

## PreviewFormat

The `<PreviewFormat>` component is useful for rendering Table Cell data into different customizable formats, e.g:

```cshtml
<PreviewFormat Value="50" Format=Formats.Currency />

<PreviewFormat Value="1000000" Format=Formats.Bytes />

<PreviewFormat Value=@Url Format=Formats.Icon IconClass="w-40 h-40" />

<PreviewFormat Value=@Url Format=Formats.Icon IconClass="w-40 h-40 rounded-full" />

<PreviewFormat Value=@Url Format=Formats.Attachment />

<PreviewFormat Value=@Path Format=Formats.Attachment />

<PreviewFormat Value=@Url Format=Formats.Link />

<PreviewFormat Value=@Email Format=Formats.LinkEmail />

<PreviewFormat Value=@Phone Format=Formats.LinkPhone />
```

[![](/images/blazor/PreviewFormat.png)](https://blazor-gallery.servicestack.net/gallery/formats)

## HtmlFormat

Whilst the versatile `<HtmlFormat>` component can be used to render any Serializable object into a human-friendly HTML Format, e.g:

### Single Model

```cshtml
<div class="max-w-screen-sm">
    <HtmlFormat Value=@Track.Results[0] />
</div>
```

[![](/images/blazor/HtmlFormat-single.png)](https://blazor-gallery.servicestack.net/gallery/formats)

### Item Collections

```cshtml
<div class="max-w-screen-sm">
    <HtmlFormat Value=@Track.Results />
</div>
```

[![](/images/blazor/HtmlFormat-collection.png)](https://blazor-gallery.servicestack.net/gallery/formats)

### Nested Complex Types

```cshtml
<HtmlFormat Value=@Create.Players />
```

[![](/images/blazor/HtmlFormat-complex.png)](https://blazor-gallery.servicestack.net/gallery/formats)

For more info about the Blazor Components available checkout the [Component Gallery](https://blazor-gallery.servicestack.net/gallery):

[![](/images/blazor/component-gallery.png)](https://blazor-gallery.servicestack.net/gallery)

## Blazor Config

A lot of the default conventions used by the Blazor Components are overridable with [BlazorConfig](https://reference.servicestack.net/api/ServiceStack.Blazor/BlazorConfig) initialized in `Program.cs`, where Blazor WASM projects configured with something like:

```csharp
BlazorConfig.Set(new BlazorConfig
{
    IsWasm = true,
    Services = app.Services,
    FallbackAssetsBasePath = apiBaseUrl,
    EnableLogging = true,
    EnableVerboseLogging = builder.HostEnvironment.IsDevelopment(),
});
```

### Asset and Fallback Paths

Where `FallbackAssetsBasePath` allows you to specify a fallback path for Images which is useful when there's a delay for syncing uploaded assets to the CDN that the Blazor WASM client is deployed to, as it can fallback to referencing the asset from the .NET App Server that handled the file upload. 

Alternatively `AssetsBasePath` can be used for specifying a different primary CDN location that's different from the Blazor WASM App CDN or `AssetsPathResolver` and `FallbackPathResolver` can be used when more a advanced custom strategy is required.