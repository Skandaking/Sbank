# Umbraco 17 Tutorial: Creating Document Types and Block Lists

This tutorial is based on the official Umbraco 17 documentation and will guide you through creating document types, element types, and block lists for your navigation and hero section.

## Table of Contents
1. [Understanding Document Types in Umbraco 17](#understanding-document-types)
2. [Creating Element Types](#creating-element-types)
3. [Creating Document Types](#creating-document-types)
4. [Setting Up Block Lists](#setting-up-block-lists)
5. [Adding Properties with Property Groups](#adding-properties)

---

## Understanding Document Types in Umbraco 17

In Umbraco 17, there are four main types of document types:

### 1. **Document Type** (without template)
- Defines content structure and fields
- Used for structured, reusable content
- Examples: metadata schemas, settings, components

### 2. **Document Type with Template**
- Combines content structure with a visual presentation
- Used for pages that render directly on the website
- Examples: blog posts, landing pages, service pages

### 3. **Element Type**
- Document Type without a template
- Designed for reusable, repeatable properties
- Used in Block List Editor or Block Grid Editor
- **Cannot be created in the Content tree**
- Automatically has "Is an Element Type" flag set to True

### 4. **Folder**
- Organizational container in Settings section only
- No impact on Content section or site functionality

---

## Creating Element Types

Element Types are the building blocks for Block Lists. They define the schema for each block item.

### Step-by-Step: Create "Navigation Item" Element Type

1. **Navigate to Settings**
   - Go to the **Settings** section in Umbraco backoffice
   - Expand **Document Types** by clicking the arrow

2. **Create Element Type**
   - Click the menu icon (•••) next to **Document Types**
   - Select **Element Type** from the context menu

3. **Name the Element Type**
   - Enter name: **"Navigation Item"**
   - The alias will auto-generate as `navigationItem`
   - You can unlock and change the alias if needed (must be camelCase)

4. **Add Property Group**
   - Click **"Add group"** button
   - Name it: **"Content"**
   - This is required in Umbraco 17 - all properties must belong to a group

5. **Add Properties to the Group**
   
   **Property 1: Link Text**
   - Click **"Add property"** in the Content group
   - **Name**: `Link Text`
   - **Alias**: `linkText` (auto-generated)
   - **Property Group**: Select "Content"
   - **Select Editor**: Choose **Textstring**
   - **Description**: "Display text for the navigation link"
   - **Mandatory**: Toggle ON
   - Click **Submit**

   **Property 2: Link**
   - Click **"Add property"** again
   - **Name**: `Link`
   - **Alias**: `link` (auto-generated)
   - **Property Group**: Select "Content"
   - **Select Editor**: Choose **Multi URL Picker**
   - **Description**: "Target page or URL"
   - **Mandatory**: Toggle ON
   - Click **Submit**

   **Property 3: Is Active** (Optional)
   - Click **"Add property"** again
   - **Name**: `Is Active`
   - **Alias**: `isActive` (auto-generated)
   - **Property Group**: Select "Content"
   - **Select Editor**: Choose **True/False**
   - **Description**: "Highlight this item as active"
   - **Mandatory**: Toggle OFF
   - Click **Submit**

6. **Save the Element Type**
   - Click **Save** in the bottom right corner

### Step-by-Step: Create "CTA Navigation Item" Element Type

Follow the same steps as above, but:
- Name: **"CTA Navigation Item"**
- Alias: `ctaNavigationItem`
- Properties:
  - **Link Text** (Textstring, Required)
  - **Link** (Multi URL Picker, Required)

### Step-by-Step: Create "Hero Promotional Block" Element Type

1. **Create Element Type**
   - Settings → Document Types → ••• → **Element Type**
   - Name: **"Hero Promotional Block"**
   - Alias: `heroPromotionalBlock`

2. **Create Property Groups**
   - **Group 1**: "Content"
   - **Group 2**: "Styling" (optional, for background color)

3. **Add Properties**

   **In "Content" Group:**
   - **Image** (Media Picker, Required)
     - Name: `Image`
     - Alias: `image`
     - Editor: **Media Picker**
     - Allowed Types: Image only
   
   - **Title** (Textstring, Required)
     - Name: `Title`
     - Alias: `title`
     - Editor: **Textstring**
   
   - **Description** (Textarea, Optional)
     - Name: `Description`
     - Alias: `description`
     - Editor: **Textarea** (or Rich Text Editor if formatting needed)
   
   - **Call to Action Text** (Textstring, Required)
     - Name: `Call to Action Text`
     - Alias: `ctaText`
     - Editor: **Textstring**
   
   - **Call to Action Link** (Multi URL Picker, Required)
     - Name: `Call to Action Link`
     - Alias: `ctaLink`
     - Editor: **Multi URL Picker**

   **In "Styling" Group** (Optional):
   - **Background Color** (Textstring, Optional)
     - Name: `Background Color`
     - Alias: `backgroundColor`
     - Editor: **Textstring** (for hex codes like #424242)

4. **Save the Element Type**

---

## Creating Document Types

### Step-by-Step: Create "Site Settings" Document Type

1. **Navigate to Settings**
   - Go to **Settings** → **Document Types**

2. **Create Document Type**
   - Click ••• next to **Document Types**
   - Select **Document Type** (without template, since this is for settings)

3. **Name and Configure**
   - Name: **"Site Settings"**
   - Alias: `siteSettings`

4. **Set Permissions**
   - Go to **Structure** tab
   - Toggle **"Allow as root"** ON
   - This allows it to be created at the root of the Content tree

5. **Add Property Group**
   - Click **"Add group"**
   - Name: **"Navigation"**

6. **Add Properties**

   **Logo** (Media Picker)
   - Name: `Logo`
   - Alias: `siteLogo`
   - Property Group: **Navigation**
   - Editor: **Media Picker**
   - Allowed Types: Image

   **Primary Navigation Items** (Block List)
   - Name: `Primary Navigation Items`
   - Alias: `primaryNavigation`
   - Property Group: **Navigation**
   - Editor: **Block List** (see [Setting Up Block Lists](#setting-up-block-lists) below)

   **Utility Navigation Items** (Block List)
   - Name: `Utility Navigation Items`
   - Alias: `utilityNavigation`
   - Property Group: **Navigation**
   - Editor: **Block List**

   **Secondary CTA Bar Items** (Block List)
   - Name: `Secondary CTA Bar Items`
   - Alias: `secondaryCtaBar`
   - Property Group: **Navigation**
   - Editor: **Block List**

7. **Save the Document Type**

### Step-by-Step: Create "Home Page" Document Type

1. **Create Document Type with Template**
   - Settings → Document Types → ••• → **Document Type with Template**
   - This creates both the Document Type and a template

2. **Name and Configure**
   - Name: **"Home Page"**
   - Alias: `homePage`

3. **Set Permissions**
   - Go to **Structure** tab
   - Toggle **"Allow as root"** ON

4. **Add Property Group**
   - Click **"Add group"**
   - Name: **"Hero Section"**

5. **Add Hero Promotional Blocks Property**
   - Name: `Hero Promotional Blocks`
   - Alias: `heroPromotionalBlocks`
   - Property Group: **Hero Section**
   - Editor: **Block List** (configured to use "Hero Promotional Block" element type)

6. **Save the Document Type**

---

## Setting Up Block Lists

Block Lists require a **Data Type** configuration before you can use them as properties.

### Step-by-Step: Create Block List Data Type for Navigation

1. **Navigate to Data Types**
   - Go to **Settings** → **Data Types**

2. **Create New Data Type**
   - Click ••• next to **Data Types**
   - Select **Data Type**

3. **Configure the Data Type**
   - **Name**: `Navigation Block List`
   - **Alias**: `navigationBlockList`
   - **Select Editor**: Choose **Block List**

4. **Configure Block List Settings**

   **Available Blocks:**
   - Click **"Add"** to add a block type
   - Select **"Navigation Item"** element type
   - Configure block appearance (optional):
     - **Label**: `{{linkText}}` (uses Umbraco Flavored Markdown)
     - **Background color**: `#424242` (optional)
     - **Icon color**: `#ffffff` (optional)

   **Amount:**
   - **Minimum**: 0
   - **Maximum**: Leave empty (unlimited) or set a specific number

   **Other Settings:**
   - **Single block mode**: OFF (we want multiple items)
   - **Live editing mode**: OFF (default mode)
   - **Inline editing mode**: OFF (default overlay mode)

5. **Save the Data Type**

### Step-by-Step: Create Block List Data Type for Hero Blocks

1. **Create Data Type**
   - Settings → Data Types → ••• → **Data Type**
   - Name: `Hero Promotional Blocks`
   - Alias: `heroPromotionalBlocks`
   - Editor: **Block List**

2. **Configure Block List**
   - **Add Block**: Select **"Hero Promotional Block"** element type
   - **Label**: `{{title}}` (shows the title in the editor)
   - **Amount**:
     - Minimum: 0
     - Maximum: 3 (or leave empty for unlimited)

3. **Save the Data Type**

### Step-by-Step: Create Block List Data Type for CTA Bar

1. **Create Data Type**
   - Name: `CTA Navigation Block List`
   - Alias: `ctaNavigationBlockList`
   - Editor: **Block List**

2. **Configure**
   - **Add Block**: Select **"CTA Navigation Item"** element type
   - **Label**: `{{linkText}}`
   - **Amount**: Minimum 0, Maximum unlimited

3. **Save the Data Type**

---

## Adding Properties with Property Groups

### Important: Property Groups are Mandatory in Umbraco 17

When adding any property to a Document Type or Element Type:

1. **You MUST select or create a Property Group**
   - When creating a property, you'll see a dropdown for "Property Group"
   - You can select an existing group or type a new name to create one
   - Groups appear as tabs in the backoffice editor

2. **Best Practices for Property Groups:**
   - Use descriptive names: "Content", "Navigation", "Hero Section", "Styling"
   - Group related properties together
   - You can reuse group names across different document types
   - Groups help organize properties for content editors

### Example: Adding a Property

1. Click **"Add property"** in a group
2. Fill in:
   - **Name**: The display name
   - **Alias**: Auto-generated (can be unlocked and changed)
   - **Property Group**: Select from dropdown or create new
   - **Select Editor**: Choose the property editor type
   - **Description**: Helpful text for editors
   - **Mandatory**: Toggle if required
3. Click **Submit**
4. **Save** the Document Type

---

## Complete Setup Checklist

### Element Types to Create:
- [ ] Navigation Item (Content group: linkText, link, isActive)
- [ ] CTA Navigation Item (Content group: linkText, link)
- [ ] Hero Promotional Block (Content group: image, title, description, ctaText, ctaLink; Styling group: backgroundColor)

### Data Types to Create:
- [ ] Navigation Block List (uses Navigation Item)
- [ ] CTA Navigation Block List (uses CTA Navigation Item)
- [ ] Hero Promotional Blocks (uses Hero Promotional Block)

### Document Types to Create:
- [ ] Site Settings (Navigation group: siteLogo, primaryNavigation, utilityNavigation, secondaryCtaBar)
- [ ] Home Page (Hero Section group: heroPromotionalBlocks)

### Content to Create:
- [ ] Create a Site Settings content node in Content section
- [ ] Create a Home Page content node in Content section
- [ ] Add navigation items to Site Settings
- [ ] Add hero blocks to Home Page

---

## Key Points to Remember

1. **Property Groups are Required**: Every property must belong to a group in Umbraco 17
2. **Element Types**: Cannot be created in Content tree, only used in Block Lists/Grids
3. **Block Lists Need Data Types**: Create the Data Type first, then use it as a property editor
4. **Aliases Matter**: Use camelCase for aliases (e.g., `heroPromotionalBlocks`)
5. **Save Frequently**: Always save Document Types after making changes

---

## Next Steps

After creating these document types:

1. **Create Content Nodes**: Add content in the Content section using your new Document Types
2. **Create Views**: Build Razor views/partials to render the content
   - Block List partials go in: `Views/Partials/BlockList/Components/`
   - Named by Element Type alias (e.g., `NavigationItem.cshtml`)
3. **Style with CSS**: Add styling to match your design

---

## References

- [Umbraco 17 Documentation - Defining Content](https://docs.umbraco.com/umbraco-cms/fundamentals/data/defining-content)
- [Umbraco 17 Documentation - Block List Editor](https://docs.umbraco.com/umbraco-cms/fundamentals/backoffice/property-editors/built-in-umbraco-property-editors/block-editor/block-list-editor)
- [Umbraco 17 Documentation - Default Document Types](https://docs.umbraco.com/umbraco-cms/fundamentals/data/defining-content/default-document-types)
