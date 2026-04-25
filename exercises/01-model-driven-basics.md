# Exercise 1: Building Your First Model-Driven App

## Overview
In this exercise, you'll build a complete **Expenses Tracker** model-driven app from scratch. You'll learn how to create tables, establish relationships, customize forms and views, and see how model-driven apps provide built-in CRUD operations automatically.

## Scenario
We're building an expense tracking system where:
- **Trips** contain multiple **Expense Reports** 
- Each trip can have several invoices/expenses that need to be tracked and approved
- Users can easily manage all their travel expenses in one organized system

## Learning Objectives
- Create and configure Dataverse tables
- Establish table relationships using lookups
- Customize main forms and views
- Build a model-driven app with minimal configuration
- Understand built-in CRUD operations

---

## Part 1: Create the Tables

### Step 1: Create the Trip Table

1. Navigate to **Power Apps** ([make.powerapps.com](https://make.powerapps.com))
2. Select your environment
3. Click **Tables** in the left navigation
4. Click **+ New table** → **Add columns and data**
5. Name your table: `Trip`
6. Add the following columns:

| Column Name | Data Type | Required | Description |
|-------------|-----------|----------|-------------|
| Trip Name | Text | Yes | Name/description of the trip |
| Destination | Text | Yes | Where the trip is going |
| Start Date | Date Only | Yes | Trip start date |
| End Date | Date Only | Yes | Trip end date |
| Trip Purpose | Choice | No | Business, Training, Conference, etc. |
| Estimated Budget | Currency | No | Planned budget for the trip |
| Trip Status | Choice | Yes | Planning, In Progress, Completed, Cancelled |

7. For **Trip Purpose**, add these choices:
   - Business Meeting
   - Training
   - Conference
   - Customer Visit
   - Other

8. For **Trip Status**, add these choices:
   - Planning (Default)
   - In Progress  
   - Completed
   - Cancelled

9. Click **Save and exit**

### Step 2: Create the Expense Report Table

1. Click **+ New table** → **Add columns and data**
2. Name your table: `Expense Report`
3. Add the following columns:

| Column Name | Data Type | Required | Description |
|-------------|-----------|----------|-------------|
| Expense Title | Text | Yes | Description of the expense |
| Expense Date | Date Only | Yes | When the expense occurred |
| Amount | Currency | Yes | Cost of the expense |
| Expense Category | Choice | Yes | Meals, Transport, Accommodation, etc. |
| Payment Method | Choice | Yes | Company Card, Personal, Cash |
| Receipt Attached | Yes/No | No | Whether receipt is available |
| Business Justification | Text | No | Why this expense was necessary |
| Trip | Lookup | Yes | Related trip (we'll configure this) |

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

---

## Part 2: Create the Relationship

### Step 3: Add the Trip Lookup to Expense Report

1. While still in the Expense Report table editor, find the **Trip** column
2. Click on the **Trip** column to configure it
3. Set the following properties:
   - **Data type**: Lookup
   - **Related table**: Trip
   - **Required**: Yes
4. Click **Save** to save the relationship
5. Click **Save and exit** to finish the Expense Report table

### Understanding the Relationship
You've just created a **1:N (one-to-many)** relationship where:
- One Trip can have many Expense Reports
- Each Expense Report belongs to exactly one Trip
- This is accomplished through a lookup column on the Expense Report table

---

## Part 3: Customize Forms and Views

### Step 4: Customize the Trip Main Form

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

### Step 5: Customize the Trip Main View

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

### Step 6: Customize the Expense Report Main Form

1. Navigate to your **Expense Report** table
2. Click **Forms** tab → edit the **Information** form
3. Organize the form:
   - **Header**: Expense Title and Amount
   - **General section**:
     - Left column: Trip, Expense Date, Expense Category
     - Right column: Payment Method, Receipt Attached
   - **Details section**: Business Justification

4. Click **Save and publish**

### Step 7: Customize the Expense Report Main View  

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

## Part 4: Create the Model-Driven App

### Step 8: Build the App

1. From the Power Apps home page, click **+ Create**
2. Select **Blank app** → **Model-driven app**
3. Give your app a name: `Expense Tracker`
4. Click **Create**

5. In the app designer:
   - Click **+ Add page** → **Table based view and form**
   - Select **Trip** table
   - This automatically adds both the view and form pages for trips
   - Click **Add**

6. Repeat for Expense Reports:
   - Click **+ Add page** → **Table based view and form** 
   - Select **Expense Report** table
   - Click **Add**

7. **Organize Navigation**:
   - In the navigation area, arrange items:
     - Trips (first)
     - Expense Reports (second)

8. Click **Save** then **Publish**

### Step 9: Test Your App

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

## Part 5: Understanding What You Built

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