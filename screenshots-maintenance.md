# Screenshots Maintenance Document - Exercise 1

## Overview
This document lists all screenshots needed for Exercise 1: Building Your First Model-Driven App. Screenshots should be taken in the order listed and use the naming convention provided.

## Screenshot Naming Convention
`01-<partnumber>-<stepnumber>-<title>`

## Part 1: Create Solution and Publisher

### Step 1: Create a Publisher
- **01-1-1-solutions-page** - Power Apps solutions page with "+ New solution" button highlighted
- **01-1-1-new-publisher-dialog** - "New publisher" dialog/link highlighted from the new solution screen
- **01-1-1-publisher-form-filled** - Completed publisher form showing initials-based naming (e.g., "LF BizApps Summit", prefix "lf")
- **01-1-1-publisher-created** - Success confirmation or publisher in dropdown list

### Step 2: Create the Solution
- **01-1-2-new-solution-dialog** - New solution dialog with all fields filled out
- **01-1-2-solution-created** - Inside the new solution showing empty state with "+ New" options

### Step 3: Work Within Your Solution
- **01-1-3-solution-overview** - Clean solution workspace showing organizational structure

---

## Part 2: Create the Tables

### Step 4: Create the Trip Table
- **01-2-4-new-table-menu** - Solution "+ New" menu with "Table" → "Table (advanced properties)" option highlighted (not just "Tables")
- **01-2-4-table-creation-dialog** - New table dialog for Trip table
- **01-2-4-primary-column-config** - Primary column configuration showing rename from "Name" to "Trip Name"
- **01-2-4-table-designer-empty** - Empty table designer after creating Trip table with system Status column visible
- **01-2-4-add-column-dialog** - "New column" dialog showing data type selection options

- **01-2-4-global-choice-creation** - Choice field showing "Sync with global choice" option and "+ New choice" dialog
- **01-2-4-create-global-choice** - Creating the actual global choice set with name and values configuration
- **01-2-4-sync-with-global-choice** - Choice column configuration showing how to sync with the newly created global choice
- **01-2-4-trip-purpose-values** - Creating "Trip Purpose Values" global choice set with all options

- **01-2-4-trip-table-complete** - Trip table with all columns added, showing detailed data types and formats

### Step 5: Create the Expense Report Table
- **01-2-5-expense-report-creation** - Creating second table from solution using "+ New" → "Table" → "Table (advanced properties)"
- **01-2-5-primary-column-config** - Primary column configuration showing rename from "Name" to "Expense Title"

- **01-2-5-expense-table-designer** - Expense Report table in designer with multiple columns showing data types and formats
- **01-2-5-text-area-format** - Text field configuration showing "Text" data type with "Text area" format for Business Justification
- **01-2-5-yesno-choice-format** - Choice field configuration showing Choice data type with "Yes/No" format for Receipt Attached
- **01-2-5-expense-category-choice** - Creating "Expense Category Values" global choice set
- **01-2-5-payment-method-choice** - Creating "Payment Method Values" global choice set
- **01-2-5-lookup-field-config** - Trip lookup field configuration showing related table selection

---

## Part 3: Create the Relationship

### Step 6: Add the Trip Lookup to Expense Report
- **01-3-6-lookup-configuration** - Lookup field properties panel showing relationship settings
- **01-3-6-relationship-created** - Confirmation of relationship creation or tables view showing relationship
- **01-3-6-solution-with-tables** - Solution overview showing both tables created

---

## Part 4: Customize Forms and Views

### Step 7: Customize the Trip Main Form
- **01-4-7-table-forms-tab** - Trip table with Forms tab selected showing available forms
- **01-4-7-form-designer** - Form designer showing Trip form layout
- **01-4-7-header-customization** - Form header section being customized with fields
- **01-4-7-two-column-layout** - General section with two-column field layout
- **01-4-7-add-subgrid** - Process of adding Related Expense Reports subgrid
- **01-4-7-completed-trip-form** - Final Trip form with all customizations

### Step 8: Customize the Trip Main View
- **01-4-8-views-tab** - Trip table Views tab showing available views
- **01-4-8-view-designer** - View designer showing column configuration
- **01-4-8-view-columns-configured** - View with proper columns in correct order
- **01-4-8-sort-configuration** - Sort settings configuration

### Step 9: Customize the Expense Report Main Form
- **01-4-9-expense-form-designer** - Expense Report form in designer
- **01-4-9-expense-form-layout** - Organized form with header and sections
- **01-4-9-completed-expense-form** - Final customized Expense Report form

### Step 10: Customize the Expense Report Main View  
- **01-4-10-expense-view-designer** - Expense Report view designer
- **01-4-10-expense-view-columns** - Expense view with configured columns including Trip lookup
- **01-4-10-completed-expense-view** - Final Expense Report view

---

## Part 5: Create the Model-Driven App

### Step 11: Build the App
- **01-5-11-new-app-menu** - Solution "+ New" menu with "App" > "Model-driven app" highlighted
- **01-5-11-app-creation-dialog** - New model-driven app creation dialog
- **01-5-11-modern-app-designer** - Modern app designer interface (empty state)
- **01-5-11-add-page-menu** - "+ Add page" menu with "Table based view and form" option
- **01-5-11-table-selection** - Table selection dialog showing prefixed table names
- **01-5-11-trip-pages-added** - App designer with Trip pages added
- **01-5-11-expense-pages-added** - App designer with both Trip and Expense Report pages
- **01-5-11-navigation-configured** - Navigation panel showing organized menu structure
- **01-5-11-app-save-publish** - Save and Publish buttons in app designer

### Step 12: Test Your App
- **01-5-12-play-button** - "Play" button to launch the app
- **01-5-12-running-app** - Live app showing navigation and main interface
- **01-5-12-trips-list-view** - Trips list view with sample data
- **01-5-12-new-trip-button** - "+ New" button in command bar highlighted
- **01-5-12-trip-form-create** - New trip creation form
- **01-5-12-trip-detail-view** - Trip detail form showing related expense reports subgrid
- **01-5-12-new-expense-from-subgrid** - Creating new expense from subgrid with Trip auto-populated
- **01-5-12-expense-form-filled** - Completed expense report form
- **01-5-12-relationship-navigation** - Showing relationship between trips and expenses in action

---

## Part 6: Understanding What You Built

### Visual Summary Screenshots
- **01-6-final-solution-components** - Solution showing all created components (tables, app)
- **01-6-final-app-navigation** - Complete app with both navigation items working
- **01-6-crud-operations-demo** - Montage showing Create, Read, Update, Delete operations
- **01-6-relationship-demonstration** - Visual showing one Trip with multiple Expense Reports

---

## Technical Notes for Screenshot Taking

### Image Requirements
- **Resolution**: Minimum 1920x1080 for clarity
- **Format**: PNG for UI screenshots, JPG acceptable for demonstration shots
- **Naming**: Exactly as specified above, lowercase with hyphens
- **Annotations**: Use red arrows/boxes for highlighting, consistent styling

### Content Guidelines
- **Sample Data**: Use realistic but generic company/trip names
- **User Information**: Blur/hide any personal email addresses or sensitive data
- **Consistency**: Use the same browser/window size throughout
- **Error States**: If showing errors, ensure they're instructional not confusing

### Special Considerations
- **Prefixes**: Show examples with realistic initials (e.g., "lf_Trip" not "xx_Trip")
- **Environment**: Use clean demo environment without unrelated tables/apps
- **Timing**: Some screens may need multiple attempts due to auto-save behaviors
- **Responsive**: Consider mobile-friendly cropping for key UI elements
- **Data Type/Format Combinations**: Clearly show the two-step process:
  - First select data type (e.g., "Date and time")
  - Then select format (e.g., "Date only")
- **Global Choice Sets**: Always demonstrate "Sync with global choice" selection and show the naming convention with "Values" suffix
- **Status Column Awareness**: Show that system Status column exists, separate from custom status fields
- **Format Examples**: 
  - Text fields: "Text" format (single line) vs "Text area" format (multi-line)
  - Date fields: "Date and time" data type → "Date only" format
  - Yes/No fields: "Choice" data type → "Yes/No" format (not standalone Yes/No data type)
- **Column Descriptions**: Always show meaningful, user-friendly descriptions in screenshots since these become tooltips in the model-driven app for usability and accessibility

## Review Status
- [ ] Screenshot list reviewed and approved
- [ ] Naming convention confirmed
- [ ] Technical requirements understood
- [ ] Ready to proceed with placeholder insertion