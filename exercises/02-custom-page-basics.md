# Exercise 2: Creating Your First Custom Page

## Overview
In this exercise, you'll add your first **custom page** to the model-driven expense tracker app you built in Exercise 1. Custom pages bring canvas app flexibility into your model-driven app, allowing you to create tailored experiences while maintaining enterprise data governance.

## Scenario
We're expanding the expense tracker with a **Trip Dashboard** custom page that provides:
- Visual overview of trip expenses with charts and KPIs
- Quick expense entry form optimized for mobile
- Modern, responsive UI following Fluent UI 2 principles
- Seamless integration with existing model-driven data

## Learning Objectives
- Understand when and why to use custom pages in model-driven apps
- Create a custom page from scratch using Power Apps canvas designer
- Apply Fluent UI 2 principles for modern, accessible interfaces
- Connect custom pages to Dataverse for real-time data
- Navigate between model-driven forms and custom pages
- Design responsive layouts for multiple form factors

## Exercise Structure: Mainquests & Sidequests

> [!TIP]
> **Continued Gaming Approach**: This exercise builds on Exercise 1's mainquest/sidequest structure for optimal pacing.

**🎯 Mainquests** (Required for Everyone):
- Create and configure a custom page
- Build responsive dashboard layout
- Connect to Dataverse data sources
- Implement basic navigation

**⭐ Sidequests** (Optional for Fast Finishers):
- Advanced chart visualizations
- Mobile-optimized input controls
- Custom branding and theming

---

## 🎯 Mainquest Part 1: Understanding Custom Pages

### What Are Custom Pages?

**Custom Pages = Canvas Apps Inside Model-Driven Apps**
- Canvas app-like designer with full control over layout and controls
- Access to all Power Apps controls, connectors, and formulas
- Embedded seamlessly within model-driven app navigation
- Shared security, data, and business logic with the model-driven app

**When to Use Custom Pages:**
✅ **Dashboards & Analytics**: Visual KPIs, charts, and summaries  
✅ **Specialized Data Entry**: Mobile-optimized or wizard-style forms  
✅ **External Integrations**: Connect to systems outside Dataverse  
✅ **Custom User Experiences**: Unique workflows or branded interfaces  

**When to Stick with Model-Driven Forms:**
✅ **Standard CRUD Operations**: Built-in forms are faster to build  
✅ **Enterprise Features**: Business rules, security roles, field-level security  
✅ **Complex Relationships**: Subgrids and related record navigation  
✅ **Accessibility**: Built-in screen reader and keyboard navigation support  

### Step 1: Access Your Existing Solution

1. Navigate to **Power Apps** ([make.powerapps.com](https://make.powerapps.com))
2. Select your environment
3. Select **Solutions** → **Expense Tracker App** (your solution from Exercise 1)

> [!IMPORTANT]
> **Solution Context**: Always create custom pages within your existing solution to maintain proper application lifecycle management and deployment capabilities.

---

## 🎯 Mainquest Part 2: Create Your First Custom Page

### Step 2: Add a Custom Page to Your App

1. In your **Expense Tracker App solution**, select **Apps** 
2. Find your **Expense Tracker** app and select the **ellipsis (...)** → **Edit**

![Edit Model-Driven App](images/02-1-2-edit-app.png)

3. In the modern app designer, select **+ New page** → **Custom page**

![Add Custom Page](images/02-1-2-add-custom-page.png)

4. Configure the custom page:
   - **Name**: `Trip Dashboard`
   - **Description**: `Visual overview and quick entry for trip expenses`

5. Select **Create**

### Step 3: Understand the Custom Page Designer

The custom page designer is essentially the **Power Apps canvas designer** embedded within your model-driven app:

![Custom Page Designer](images/02-1-3-designer-interface.png)

**Key Interface Elements:**
- **Left Panel**: Insert tab with controls, media, charts, and connectors
- **Center Canvas**: Design surface with responsive preview options
- **Right Panel**: Properties for selected controls
- **Top Ribbon**: Save, preview, data sources, and settings
- **Bottom**: Formula bar for Power Apps expressions

> [!TIP]
> **Canvas App Skills Transfer**: If you're familiar with Power Apps canvas apps, you already know this interface! Custom pages use the exact same designer and control library.

---

## 🎯 Mainquest Part 3: Design Your Dashboard Layout

### Step 4: Create the Page Structure

1. **Set Up Responsive Layout**:
   - Select **Settings** (gear icon) → **Display**
   - **Orientation**: `Both` (responsive for desktop and mobile)
   - **Scale to fit**: `On`

2. **Add Container Controls for Structure**:
   - From **Insert** → **Layout** → **Container**
   - Rename it to `HeaderContainer` in the properties panel
   - Position: Top of screen, full width

3. **Add Header Content**:
   - Inside `HeaderContainer`, add a **Label** control
   - **Text**: `"Trip Dashboard"`
   - **Font size**: `24`
   - **Font weight**: `Semibold`
   - **Color**: `RGBA(50, 49, 48, 1)` (Fluent UI dark gray)

![Dashboard Header](images/02-1-4-header-layout.png)

### Step 5: Connect to Dataverse

1. **Add Data Sources**:
   - Select **Data** (cylinder icon) in left panel
   - Search for your Trip table: `[prefix]_Trip` (e.g., `lf_Trip`)
   - Select **Connect**

![Connect Data Source](images/02-1-5-connect-data.png)

2. **Add Expense Data Source**:
   - In Data panel, search for your Expense table: `[prefix]_Expense`
   - Select **Connect**

> [!NOTE]
> **Automatic Connection**: Custom pages automatically inherit the security context and data access of your model-driven app. No additional authentication required!

### Step 6: Create KPI Cards

1. **Add KPI Container**:
   - Add another **Container** below the header
   - Name: `KPIContainer`
   - **Direction**: `Horizontal` (for side-by-side cards)
   - **Wrap**: `Wrap` (responsive behavior)

2. **Create Trip Count Card**:
   - Inside `KPIContainer`, add a **Container**
   - Name: `TripCountCard`
   - **Background color**: `RGBA(243, 242, 241, 1)` (Fluent UI light gray)
   - **Border radius**: `4`
   - **Width**: `200`
   - **Height**: `120`

3. **Add KPI Content**:
   - Inside `TripCountCard`, add a **Label**
   - **Text**: `CountRows(lf_Trip)` (replace `lf` with your prefix)
   - **Font size**: `32`
   - **Font weight**: `Bold`
   - **Align**: `Center`

4. **Add KPI Description**:
   - Add another **Label** below the count
   - **Text**: `"Total Trips"`
   - **Font size**: `14`
   - **Color**: `RGBA(96, 94, 92, 1)` (Fluent UI secondary text)

![KPI Cards](images/02-1-6-kpi-cards.png)

---

## 🎯 Mainquest Part 4: Add Interactive Elements

### Step 7: Create Recent Trips Gallery

1. **Add Gallery Container**:
   - Below KPI section, add a **Container**
   - Name: `RecentTripsContainer`

2. **Add Gallery Control**:
   - Inside the container, add **Gallery** → **Vertical gallery**
   - **Data source**: Your Trip table (e.g., `lf_Trip`)
   - **Items**: `SortByColumns(lf_Trip, "lf_startdate", SortOrder.Descending)` (replace prefix)

3. **Customize Gallery Template**:
   - In the gallery template, keep the default **Title** and **Subtitle** controls
   - **Title Text**: `ThisItem.'lf_tripname'` (replace with your Trip Name column)
   - **Subtitle Text**: `ThisItem.lf_destination` (replace with your Destination column)

4. **Add Date Label**:
   - Add a **Label** to the template
   - **Text**: `Text(ThisItem.lf_startdate, "mmm dd, yyyy")` (replace with your Start Date column)
   - Position on the right side of the template

![Recent Trips Gallery](images/02-1-7-recent-trips.png)

### Step 8: Test Your Custom Page

1. **Save Your Work**: Select **Save** in the top ribbon

2. **Preview the Page**:
   - Select **Preview** → **Preview**
   - Test the responsive behavior by resizing the preview window
   - Verify data is loading from your Dataverse tables

3. **Test in Model-Driven App**:
   - Go back to your model-driven app designer
   - Select **Save and Publish**
   - Select **Play** to test the app
   - Navigate to your **Trip Dashboard** page in the site map

![Custom Page in App](images/02-1-8-page-in-app.png)

> [!TIP]
> **Iteration Workflow**: You can switch between the model-driven app and custom page designer for testing. Changes save automatically, but remember to publish the app for changes to appear in the live app.

---

## ⭐ Sidequest: Mobile-Optimized Quick Entry

> [!NOTE]
> **Mobile First Challenge**: Complete this sidequest to learn responsive design patterns for custom pages!

**Your Mission**: Add a mobile-friendly expense entry form to your dashboard.

**Implementation Steps**:
1. **Add Entry Form Container**:
   - Add a new **Container** below your gallery
   - Name: `QuickEntryContainer`
   - **Visible**: `If(App.ActiveScreen.Size = ScreenSize.Small, true, false)`

2. **Create Input Controls**:
   - Add **Text input** for expense title
   - Add **Number input** for amount
   - Add **Dropdown** connected to your Expense Category choice values
   - Add **Date picker** for expense date

3. **Add Submit Logic**:
   - Add a **Button** with text "Add Expense"
   - **OnSelect**: `SubmitForm(FormControl)` or `Patch()` function to create record

> [!TIP]
> **Sidequest Hints**:
> - 📱 **Responsive Visibility**: Use `App.ActiveScreen.Size` to show/hide controls based on device
> - 🎨 **Fluent UI Colors**: Use `ColorValue("#0078d4")` for primary blue buttons
> - 📝 **Form Controls**: Consider using `Edit form` control for built-in validation and submit logic
> - 🔗 **Navigation**: Use `Navigate()` to return to model-driven views after submission

---

## ⭐ Advanced Sidequest: Chart Visualization

> [!NOTE]
> **Data Visualization Challenge**: Add professional charts to your dashboard!

**Your Mission**: Create a chart showing expenses by category.

**Implementation Steps**:
1. **Add Chart Control**:
   - From Insert → Charts → **Column chart**
   - **Data source**: `AddColumns(GroupBy(lf_Expense, "lf_expensecategory", "CategoryGroup"), "TotalAmount", Sum(CategoryGroup, lf_amount))`

2. **Configure Chart Properties**:
   - **Labels**: `TotalAmount.'lf_expensecategory'`
   - **Values**: `TotalAmount.TotalAmount`
   - **Colors**: Fluent UI color palette

> [!TIP]
> **Advanced Sidequest Hints**:
> - 📊 **Data Aggregation**: Use `GroupBy()` and `AddColumns()` to summarize data
> - 🎨 **Chart Styling**: Explore color palettes and chart types for best data representation  
> - 📈 **Dynamic Data**: Charts update automatically as underlying data changes
> - 🔄 **Refresh**: Use `Refresh(DataSource)` if you need to force data refresh

---

## 🥳 Exercise Complete!

**You've successfully created a custom page that:**
- Brings canvas app flexibility into your model-driven app
- Displays real-time data from Dataverse with responsive design
- Applies Fluent UI 2 principles for professional appearance
- Integrates seamlessly with existing model-driven navigation
- Provides foundation for advanced visualizations and mobile experiences

### Key Concepts Learned

**Hybrid Development Approach:**
- Model-driven apps for enterprise CRUD operations
- Custom pages for specialized experiences and visualizations
- Shared data layer and security context
- Unified navigation and user experience

**Canvas Designer Power:**
- Full control over layout and user experience
- Rich control library including charts and media
- Power Apps formula language for dynamic behavior
- Responsive design capabilities for multiple devices

### What's Next?

In **Exercise 3**, you'll enhance your custom page with JavaScript for advanced interactivity and learn how to navigate between custom pages and model-driven forms programmatically.

---

## Troubleshooting

**Custom page not showing data?**
- Verify your table prefix matches your formulas (e.g., `lf_Trip` vs `js_Trip`)
- Check that tables were properly connected in the Data panel
- Ensure you're using the correct column names in your formulas

**Gallery showing no items?**
- Verify the **Items** property syntax is correct
- Check that your Trip table has sample data from Exercise 1
- Try simple formula first: just `lf_Trip` instead of `SortByColumns()`

**Preview not working?**
- Save your custom page before previewing
- Try **Refresh** in the preview window
- Check for formula errors in controls (red wavy underlines)

**Can't find custom page in model-driven app?**
- Ensure you **Saved and Published** the model-driven app
- Check that the custom page was added to the correct app
- Verify the page appears in the app designer sitemap

**Need Help?** Raise your hand - we're here to help! 🙋‍♀️🙋‍♂️