# Exercise 1: Building Your First Model-Driven App

## Overview
In this exercise, you'll build a complete **Expenses Tracker** model-driven app from scratch. You'll learn how to create tables, establish relationships, customize forms and views, and see how model-driven apps provide built-in CRUD operations automatically.

## Scenario
We're building an expense tracking system where:
- **Trips** contain multiple **Expense Reports** 
- Each trip can have several invoices/expenses that need to be tracked and approved
- Users can easily manage all their travel expenses in one organized system

## Learning Objectives
- Create a solution and publisher for proper application lifecycle management
- Create and configure Dataverse tables
- Establish table relationships using lookups
- Customize main forms and views
- Build a model-driven app with minimal configuration
- Understand built-in CRUD operations

---

## Part 1: Create Solution and Publisher

### Step 1: Create a Publisher

1. Navigate to **Power Apps** ([make.powerapps.com](https://make.powerapps.com))
2. Select your environment
3. Click **Solutions** in the left navigation

![Solutions Page](exercises/images/01-1-1-solutions-page.png)

4. Click **+ New solution**
5. Before we create the solution, we need a publisher. Click **+ New publisher**
6. Fill in the publisher details using **your initials**:
   - **Display name**: `[Your Initials]` (e.g., "LF")
   - **Name**: `[yourinitials]` (e.g., "lf" - this will auto-populate)
   - **Prefix**: `[your initials]` (e.g., "lf" - keep it short, 2-4 characters)
   - **Option value prefix**: `10000` (leave default or use provided number)
   - **Contact details**: Add your email

![Publisher Form Filled](exercises/images/01-1-1-publisher-form-filled.png)

7. Click **Save**

> 💡 **Why use your initials?** This ensures each participant has a unique publisher prefix, avoiding conflicts when working in shared environments.

### Step 2: Create the Solution

1. Now back in the **New solution** dialog:
   - **Display name**: `Expense Tracker App`
   - **Name**: `ExpenseTrackerApp` (auto-populated)
   - **Publisher**: Select **[Your Initials]** (the publisher you just created)
   - **Version**: `1.0.0.0` (default)
   - **Description**: `Complete expense tracking solution for business trips`

2. Click **Create**

![Solution Created](exercises/images/01-1-2-solution-created.png)

### Step 3: Work Within Your Solution

From now on, **all components will be created within this solution**. This ensures:
- ✅ Proper component organization
- ✅ Easy deployment between environments  
- ✅ Clean application lifecycle management
- ✅ Simplified backup and version control

---

## Part 2: Create the Tables


### Step 4: Create the Trip Table

1. You should now be **inside your Expense Tracker App solution**
2. Click **+ New** → **Table** → **Table**

![New Table Menu](exercises/images/01-2-4-new-table-menu.png)

3. In the **New table** panel:
   - **Display name**: `Trip`
   - **Plural display name**: `Trips` (auto-populated)
   - **Name**: `[prefix]_Trip` (e.g., `lf_Trip` - note your initials prefix)

![Table Creation Dialog](exercises/images/01-2-4-table-creation-dialog.png)

4. Click **Save**

![Table Designer Empty](exercises/images/01-2-4-table-designer-empty.png)

5. You're now in the table designer. Add the following columns by clicking **+ New column**:

![Add Column Dialog](exercises/images/01-2-4-add-column-dialog.png)

| Column Name      | Data Type | Required | Description                                 |
| ---------------- | --------- | -------- | ------------------------------------------- |
| Trip Name        | Text      | Yes      | Name/description of the trip                |
| Destination      | Text      | Yes      | Where the trip is going                     |
| Start Date       | Date Only | Yes      | Trip start date                             |
| End Date         | Date Only | Yes      | Trip end date                               |
| Trip Purpose     | Choice    | No       | Business, Training, Conference, etc.        |
| Estimated Budget | Currency  | No       | Planned budget for the trip                 |
| Trip Status      | Choice    | Yes      | Planning, In Progress, Completed, Cancelled |

7. For **Trip Purpose**, add these choices:
   - Business Meeting
   - Training
   - Conference
   - Customer Visit
   - Other

![Choice Field Config](exercises/images/01-2-4-choice-field-config.png)

8. For **Trip Status**, add these choices:
   - Planning (Default)
   - In Progress  
   - Completed
   - Cancelled

9. Click **Save** (this saves the table to your solution)

![Trip Table Complete](exercises/images/01-2-4-trip-table-complete.png)

### Step 5: Create the Expense Report Table

1. From your solution, click **+ New** → **Table** → **Table**

![Expense Report Creation](exercises/images/01-2-5-expense-report-creation.png)

2. In the **New table** panel:
   - **Display name**: `Expense Report`
   - **Plural display name**: `Expense Reports` (auto-populated) 
   - **Name**: `[prefix]_ExpenseReport` (e.g., `lf_ExpenseReport` - note your prefix)
3. Click **Save**
4. Add the following columns by clicking **+ New column**:

![Expense Table Designer](exercises/images/01-2-5-expense-table-designer.png)

| Column Name            | Data Type | Required | Description                           |
| ---------------------- | --------- | -------- | ------------------------------------- |
| Expense Title          | Text      | Yes      | Description of the expense            |
| Expense Date           | Date Only | Yes      | When the expense occurred             |
| Amount                 | Currency  | Yes      | Cost of the expense                   |
| Expense Category       | Choice    | Yes      | Meals, Transport, Accommodation, etc. |
| Payment Method         | Choice    | Yes      | Company Card, Personal, Cash          |
| Receipt Attached       | Yes/No    | No       | Whether receipt is available          |
| Business Justification | Text      | No       | Why this expense was necessary        |
| Trip                   | Lookup    | Yes      | Related trip (we'll configure this)   |

4. For **Expense Category**, add these choices:
   - Meals & Entertainment
   - Transportation
   - Accommodation
   - Fuel
   - Parking
   - Other

5. For **Payment Method**, add these choices:
   - Company Credit Card
   - Personal Reimbursement
   - Cash Advance

6. **Don't save yet** - we need to add the lookup relationship first

![Lookup Field Config](exercises/images/01-2-5-lookup-field-config.png)

---

## Part 3: Create the Relationship

### Step 6: Add the Trip Lookup to Expense Report

1. While still in the Expense Report table editor, find the **Trip** column
2. Click on the **Trip** column to configure it
3. Set the following properties:
   - **Data type**: Lookup
   - **Related table**: Trip
   - **Required**: Yes

![Lookup Configuration](exercises/images/01-3-6-lookup-configuration.png)

4. Click **Save** to save the relationship

![Relationship Created](exercises/images/01-3-6-relationship-created.png)

5. Click **Save and exit** to finish the Expense Report table

![Solution With Tables](exercises/images/01-3-6-solution-with-tables.png)

### Understanding the Relationship
You've just created a **1:N (one-to-many)** relationship where:
- One Trip can have many Expense Reports
- Each Expense Report belongs to exactly one Trip
- This is accomplished through a lookup column on the Expense Report table

---

## Part 4: Customize Forms and Views

### Step 7: Customize the Trip Main Form

1. Go back to **Tables** and select your **Trip** table
2. Click **Forms** tab
3. Find the **Information** form (Main form type) and click to edit it
4. Customize the form layout:
   - **Header section**: Add Trip Name and Trip Status
   - **General section**: Organize fields in two columns:
     - Left column: Destination, Start Date, Trip Purpose  
     - Right column: Estimated Budget, End Date
   - Add a new **Details** section below with: Business Justification (if you added this field)

5. **Add a Related Records subgrid**:
   - From the **Table columns** panel, drag **Related** → **Expense Reports** onto the form
   - This will show all expense reports related to this trip
   - Position it at the bottom of the form

6. Click **Save and publish**

### Step 8: Customize the Trip Main View

1. Still in the Trip table, click **Views** tab
2. Find the **Active Trips** view and click to edit it
3. Configure the view columns (in this order):
   - Trip Name
   - Destination  
   - Start Date
   - End Date
   - Trip Status
   - Estimated Budget

4. Set **Sort by**: Start Date (Descending) so newest trips appear first
5. Click **Save and publish**

### Step 9: Customize the Expense Report Main Form

1. Navigate to your **Expense Report** table
2. Click **Forms** tab → edit the **Information** form
3. Organize the form:
   - **Header**: Expense Title and Amount
   - **General section**:
     - Left column: Trip, Expense Date, Expense Category
     - Right column: Payment Method, Receipt Attached
   - **Details section**: Business Justification

4. Click **Save and publish**

### Step 10: Customize the Expense Report Main View  

1. In Expense Report table, click **Views** tab
2. Edit the **Active Expense Reports** view
3. Configure columns:
   - Expense Title
   - Trip (this will show the related trip name)
   - Expense Date
   - Amount
   - Expense Category
   - Payment Method

4. Set **Sort by**: Expense Date (Descending)
5. Click **Save and publish**

---

## Part 5: Create the Model-Driven App

### Step 11: Build the App

1. From within your **Expense Tracker App solution**, click **+ New** → **App** → **Model-driven app**
2. In the app designer:
   - **Name**: `Expense Tracker`
   - **Description**: `Track business trip expenses and manage approvals`
3. Click **Create**

4. In the modern app designer:
   - Click **+ Add page** → **Table based view and form**
   - Select **Trip** table (it will show with your prefix, e.g., `lf_Trip`)
   - This automatically adds both the view and form pages for trips
   - Click **Add**

5. Repeat for Expense Reports:
   - Click **+ Add page** → **Table based view and form** 
   - Select **Expense Report** table (it will show with your prefix, e.g., `lf_ExpenseReport`)
   - Click **Add**

6. **Organize Navigation**:
   - In the navigation area, arrange items:
     - Trips (first)
     - Expense Reports (second)

7. Click **Save** then **Publish**

> 💡 **Solution Benefits**: Notice how all your components (tables, app) are now organized within your solution. This makes deployment to other environments much easier!

### Step 12: Test Your App

1. Click **Play** to launch your app
2. **Test the built-in CRUD operations**:

   **Create**: 
   - Click **Trips** in navigation
   - Click **+ New** in command bar
   - Fill out a sample trip and save
   
   **Read**: 
   - View the trip in the list
   - Click on a trip to open the detailed form
   - Notice the Related Expense Reports section
   
   **Update**: 
   - Edit any field in the trip
   - Click **Save** 
   
   **Delete**: 
   - Select a trip from the list
   - Click **Delete** in command bar (be careful!)

3. **Test the Relationship**:
   - Open a trip record
   - In the **Expense Reports** subgrid, click **+ New Expense Report**
   - Notice the Trip field is automatically populated
   - Fill out the expense details and save
   - See how it appears in both the subgrid and the Expense Reports main area

---

## Part 6: Understanding What You Built

### Built-in Features You Get "For Free"

✅ **Complete CRUD Operations**: Create, Read, Update, Delete - no coding required

✅ **Data Validation**: Required fields, data type validation automatically enforced

✅ **Relationship Navigation**: Click from trips to expenses and back seamlessly  

✅ **Search and Filtering**: Use the search box and filter options in views

✅ **Responsive Design**: Works on desktop, tablet, and mobile devices

✅ **Security**: Built-in role-based security (when configured)

✅ **Audit Trail**: Tracks who created/modified records and when (when enabled)

### The Power of Model-Driven Apps

**What made this so easy?**
- **Metadata-driven**: The platform uses your table and relationship definitions to automatically generate the UI
- **Convention over configuration**: Sensible defaults for forms, views, and navigation
- **Built-in business logic**: Standard operations work immediately without custom development

**When would you customize the command bar?**
While most standard operations are built-in, you might add custom buttons for:
- Triggering Power Automate flows
- Complex business processes (e.g., "Submit for Approval")
- Integration with external systems
- Custom calculations or reports

> 💡 **Pro Tip**: The component library approach mentioned in the overview is the easiest way to add custom command bar buttons, but for most business apps, the standard commands are sufficient.

---

## 🎯 Challenge Exercise

If you finish early, try these enhancements:

1. **Add a Status Reason**: Create a status reason field on Expense Report with values like "Draft", "Submitted", "Approved", "Rejected"

2. **Create a Business Rule**: Make the "Business Justification" field required when the expense amount is over $100

3. **Add a Calculated Field**: Create a calculated field on Trip that shows the total of all related expense reports

4. **Create a Custom View**: Build a view that shows only expenses over $50 from the last 30 days

---

## ✅ Exercise Complete!

**You've successfully built a complete business application with:**
- ✅ Two related tables with proper data structure
- ✅ Customized forms for optimal user experience  
- ✅ Tailored views for efficient data management
- ✅ A model-driven app with full CRUD functionality
- ✅ Understanding of built-in vs. custom functionality

**Next Steps**: In Exercise 2, you'll learn how to create custom pages that bring canvas app flexibility into your model-driven app while maintaining the enterprise structure you just built.

---

## Troubleshooting

**Can't see your tables in app designer?** 
- Refresh the browser and try again
- Make sure tables are saved and published

**Lookup field not showing Trip names?**
- Verify the Trip table has a "Name" or primary field configured
- Check that the relationship was created correctly

**App won't load?**
- Ensure you have sufficient permissions in the environment
- Try publishing the app again

**Need Help?** Raise your hand - we're here to help! 🙋‍♀️🙋‍♂️