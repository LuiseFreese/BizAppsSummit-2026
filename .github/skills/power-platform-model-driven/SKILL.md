---
name: power-platform-model-driven
description: 'Build Microsoft Power Platform model-driven apps with proper data modeling, table relationships, and enterprise patterns. USE FOR: creating Dataverse tables, designing forms/views, building model-driven apps, Power Platform best practices, global choice sets, solution management, publisher creation, table relationships, accessibility compliance. DO NOT USE FOR: Canvas apps (different framework), Power Automate flows, general Microsoft 365 development.'
argument-hint: 'Describe your model-driven app requirements (tables, relationships, business logic)'
---

# Power Platform Model-Driven Apps Development

## When to Use This Skill

**Trigger phrases:**
- "Create a model-driven app"
- "Build Dataverse tables"
- "Power Platform solution" 
- "Table relationships"
- "Global choice sets"
- "Model-driven forms/views"
- "Power Apps maker portal"
- "Solution lifecycle management"
- "Publisher and prefix"

**Use for:**
- ✅ Complete model-driven app development workflows
- ✅ Table design with proper data types and relationships
- ✅ Form and view customization following UX best practices
- ✅ Solution and publisher management for ALM
- ✅ Global choice sets with reusable values
- ✅ Accessibility compliance (descriptions → tooltips)
- ✅ Enterprise naming conventions and prefixes

**Don't use for:**
- ❌ Canvas apps (different development paradigm)
- ❌ Power Automate/Logic Apps
- ❌ SharePoint customization
- ❌ Azure development

## Core Development Workflow

### 1. Solution Foundation Setup

**Always start with proper solution architecture:**

1. **Publisher Creation** (use participant initials for workshops):
   - Display name: `[Initials]` (e.g., "LF")
   - Name: `[initials]` (auto-populated, e.g., "lf")
   - Prefix: `[initials]` (2-4 characters, e.g., "lf")

2. **Solution Creation**:
   - Use descriptive names (e.g., "Expense Tracker App")
   - Select your custom publisher (never use "Common Data Services Default Publisher")
   - Version: `1.0.0.0` (semantic versioning)
   - Description: Clear business purpose

3. **Work Within Solution Context**:
   - **All components must be created within the solution**
   - Ensures proper ALM, deployment, and version control
   - Organized component structure for team collaboration

### 2. Table Design Patterns

**Table Naming Standards:**
- Display name: Singular, business-friendly (e.g., "Trip")
- Plural display name: Auto-populated (e.g., "Trips")
- Name: `[prefix]_[TableName]` (e.g., "lf_Trip")

**Primary Column Configuration:**
- Rename from generic "Name" to meaningful field name
- Examples: "Trip Name", "Expense Title", "Project Name"
- This becomes the primary identifier users see

**Data Type Selection Best Practices:**

| Business Need | Data Type | Format | Notes |
|---------------|-----------|--------|-------|
| Single line text | Single Line of Text | Text | Default for names, titles |
| Multi-line text | Text | Text area | Descriptions, justifications |
| Dates only | Date and time | Date only | **Two-step process: type → format** |
| Currency amounts | Currency | Currency | Uses environment currency |
| Dropdown lists | Choice | N/A | Always sync with global choices |
| True/False | Choice | Yes/No | **Not standalone Yes/No type** |
| Related records | Lookup | N/A | Creates relationships |

**System vs Business Status Understanding:**
- Every table has automatic "Status" column (Active/Inactive)
- Create separate business status fields (e.g., "Trip Status", "Project Status")
- Differentiate system state from business workflow state

### 3. Global Choice Sets Strategy

**Naming Convention:**
- Always use `[Purpose] Values` format
- Examples: "Trip Purpose Values", "Payment Method Values"
- The "Values" suffix indicates reusable global choice set

**Implementation Process:**
1. When creating Choice columns, select **"Sync with global choice"**
2. Create new global choice set with proper naming
3. Add all business values with clear labels
4. Set appropriate defaults where needed

**Reusability Benefits:**
- Consistent spellings across tables and environments
- Easier maintenance (update once, applies everywhere)
- Environment migration maintains choice consistency
- Future tables can reuse existing choice sets

### 4. Accessibility and UX Compliance

**Description Field Strategy:**
- **Every column needs meaningful description**
- Descriptions become tooltips in model-driven apps
- Critical for accessibility and user guidance
- Write clear, action-oriented descriptions

**Examples of Good Descriptions:**
- "City, country, or location where the trip is taking place"
- "Expected total cost for this trip including all expenses"
- "Indicates if you have a receipt or proof of purchase"

### 5. Relationship Design

**1:N (One-to-Many) Relationships:**
- Implemented via Lookup column on "many" side
- Example: Trip (1) → Expense Reports (N)
- Lookup field on Expense Report table pointing to Trip
- Always mark lookup as "Required" for data integrity

**Relationship Navigation:**
- Creates automatic subgrids on parent records
- Enables drill-down from parent to child records
- Maintains referential integrity in Dataverse

### 6. Form Customization Standards

**Header Section:**
- Primary identifier field (Trip Name, Expense Title)
- Key status field (Trip Status, Approval Status)
- Keep header minimal and impactful

**General Section Layout:**
- Use two-column layout for optimal screen utilization
- Group related fields logically
- Left column: Primary business fields
- Right column: Secondary/supporting fields

**Related Records Subgrids:**
- Add subgrids for related child records
- Position at bottom of form
- Shows 1:N relationship data inline
- Enables quick creation of related records

### 7. View Configuration

**Column Selection Priority:**
1. Primary identifier (Name/Title field)
2. Key business fields for quick scanning
3. Status indicators
4. Related record identifiers (via lookup)
5. Dates (sorted descending for recency)

**View Sorting Best Practices:**
- Default to most recent first (dates descending)
- Status-based sorting for workflow views
- Alphabetical for reference/lookup scenarios

### 8. Model-Driven App Assembly

**Page Structure:**
- Use "Table based view and form" for standard tables
- Automatically includes both list and detail views
- Maintain consistent navigation hierarchy

**Navigation Organization:**
- Primary entities first (e.g., Trips)
- Related entities second (e.g., Expense Reports)
- Reference data last (e.g., Categories, Locations)

### 9. Built-in Features Leverage

**CRUD Operations (Available automatically):**
- ✅ Create: + New buttons with proper forms
- ✅ Read: List views with drill-down capability
- ✅ Update: Edit forms with validation
- ✅ Delete: Command bar delete with confirmations

**Additional Built-in Features:**
- Search and filtering in all views
- Responsive design (desktop/tablet/mobile)
- Role-based security (when configured)
- Audit trail capability (when enabled)
- Advanced find for complex queries

## Common Patterns and Solutions

### Multi-Entity Business Processes
For processes spanning multiple tables (like expense approval):
1. Use status fields to track workflow stages
2. Implement business rules for field requirements
3. Consider Power Automate for complex approval routing
4. Use calculated fields for automatic totals/summaries

### Reference Data Management
For lookup/dropdown values (categories, types, etc.):
1. Create dedicated reference tables for complex lookups
2. Use global choice sets for simple dropdown lists
3. Maintain consistent naming across similar concepts
4. Plan for easy maintenance and updates

### Data Validation Strategies
- Required fields: Set "Business Required" appropriately
- Data type validation: Automatic based on column types
- Business rules: For conditional logic and validation
- Calculated fields: For automatic computations

## Anti-Patterns to Avoid

❌ **Using default publisher**: Always create custom publisher with meaningful prefix

❌ **Creating outside solutions**: All components must be solution-aware

❌ **Local choice sets**: Always create global choice sets for reusability

❌ **Generic field names**: Make primary columns descriptive and business-friendly

❌ **Missing descriptions**: Every field needs clear, helpful description

❌ **Ignoring relationship direction**: Always implement lookups on the "many" side

❌ **Overcomplicating forms**: Keep layouts clean and logical

❌ **Default sorting**: Configure views with business-appropriate sorting

## Troubleshooting Common Issues

**Tables not visible in app designer:**
- Refresh browser and try again
- Ensure tables are saved and published
- Verify you're working within correct solution

**Lookup fields not showing names:**
- Check primary field configuration on target table
- Verify relationship was created correctly
- Ensure target records exist and are active

**App won't load or errors on launch:**
- Confirm sufficient environment permissions
- Re-publish the app
- Check for required field validation issues

**Forms showing wrong layout:**
- Verify you're editing the correct form (usually "Information" main form)
- Ensure changes are saved and published
- Clear browser cache if needed

---

This skill encapsulates enterprise-grade Power Platform development patterns focused on maintainable, scalable, and user-friendly model-driven applications.