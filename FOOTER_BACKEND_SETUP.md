# Footer Backend Setup Guide - Step by Step

This guide will walk you through creating all the necessary Document Types, Element Types, and Data Types needed for a comprehensive footer in Umbraco 17.

## Overview

The footer will be managed through your existing **Site Settings** document type. We'll add footer properties that allow content editors to manage:
- Disclaimer text
- App store download badges
- Social media links
- Multiple columns of footer links (Useful Tools, Our sites, Who we are, Support, Legal)
- Legal/regulatory information

---

## Step 1: Create Element Types

Element Types are reusable components that will be used in Block Lists. We need to create several Element Types for the footer.

### 1.1 Create "Footer Link Item" Element Type

**Purpose**: Individual link items for footer columns (Useful Tools, Our sites, etc.)

1. **Navigate to Settings**
   - Go to **Settings** → **Document Types**

2. **Create Element Type**
   - Click the menu icon (•••) next to **Document Types**
   - Select **Element Type**

3. **Name the Element Type**
   - Name: **"Footer Link Item"**
   - Alias: `footerLinkItem` (auto-generated, verify it's correct)

4. **Add Property Group**
   - Click **"Add group"**
   - Name: **"Content"**

5. **Add Properties** (in the "Content" group):

   **Link Text** (Textstring, Required)
   - Name: `Link Text`
   - Alias: `linkText`
   - Property Group: **Content**
   - Editor: **Textstring**
   - Mandatory: ✅ Yes

   **Link** (Multi URL Picker, Required)
   - Name: `Link`
   - Alias: `link`
   - Property Group: **Content**
   - Editor: **Multi URL Picker**
   - Mandatory: ✅ Yes

6. **Save the Element Type**

---

### 1.2 Create "App Store Badge" Element Type

**Purpose**: App store download badges (App Store, Google Play, AppGallery)

1. **Create Element Type**
   - Settings → Document Types → ••• → **Element Type**
   - Name: **"App Store Badge"**
   - Alias: `appStoreBadge`

2. **Add Property Group**
   - Name: **"Content"**

3. **Add Properties** (in the "Content" group):

   **Store Name** (Dropdown, Required)
   - Name: `Store Name`
   - Alias: `storeName`
   - Property Group: **Content**
   - Editor: **Dropdown**
   - Prevalues: 
     - `App Store`
     - `Google Play`
     - `AppGallery`
   - Mandatory: ✅ Yes

   **Badge Image** (Media Picker, Required)
   - Name: `Badge Image`
   - Alias: `badgeImage`
   - Property Group: **Content**
   - Editor: **Media Picker**
   - Allowed Types: Image only
   - Mandatory: ✅ Yes

   **Download Link** (Multi URL Picker, Required)
   - Name: `Download Link`
   - Alias: `downloadLink`
   - Property Group: **Content**
   - Editor: **Multi URL Picker**
   - Mandatory: ✅ Yes

4. **Save the Element Type**

---

### 1.3 Create "Social Media Link" Element Type

**Purpose**: Social media icons and links (Twitter/X, Facebook, Instagram)

1. **Create Element Type**
   - Settings → Document Types → ••• → **Element Type**
   - Name: **"Social Media Link"**
   - Alias: `socialMediaLink`

2. **Add Property Group**
   - Name: **"Content"**

3. **Add Properties** (in the "Content" group):

   **Platform Name** (Dropdown, Required)
   - Name: `Platform Name`
   - Alias: `platformName`
   - Property Group: **Content**
   - Editor: **Dropdown**
   - Prevalues:
     - `Twitter/X`
     - `Facebook`
     - `Instagram`
     - `LinkedIn` (optional, for future use)
   - Mandatory: ✅ Yes

   **Social Media Link** (Multi URL Picker, Required)
   - Name: `Social Media Link`
   - Alias: `socialLink`
   - Property Group: **Content**
   - Editor: **Multi URL Picker**
   - Mandatory: ✅ Yes

   **Icon Image** (Media Picker, Optional)
   - Name: `Icon Image`
   - Alias: `iconImage`
   - Property Group: **Content**
   - Editor: **Media Picker**
   - Allowed Types: Image only
   - Mandatory: ❌ No (can use CSS classes instead)

4. **Save the Element Type**

---

## Step 2: Create Data Types (Block Lists)

Before we can use Block Lists in Document Types, we need to create Data Type configurations.

### 2.1 Create "Footer Links Block List" Data Type

**Purpose**: Block List for footer link columns

1. **Navigate to Data Types**
   - Go to **Settings** → **Data Types**

2. **Create New Data Type**
   - Click ••• next to **Data Types**
   - Select **Data Type**

3. **Configure Data Type**
   - Name: **"Footer Links Block List"**
   - Editor: **Block List**

4. **Configure Block List Settings**
   - Click **"Add"** in the "Available Blocks" section
   - Select **"Footer Link Item"** (the Element Type we created)
   - Set as **Default** block (optional, but recommended)
   - Click **Submit**

5. **Save the Data Type**

---

### 2.2 Create "App Store Badges Block List" Data Type

**Purpose**: Block List for app store badges

1. **Create New Data Type**
   - Settings → Data Types → ••• → **Data Type**
   - Name: **"App Store Badges Block List"**
   - Editor: **Block List**

2. **Configure Block List Settings**
   - Click **"Add"** in the "Available Blocks" section
   - Select **"App Store Badge"** Element Type
   - Set as **Default** block
   - Click **Submit**

3. **Save the Data Type**

---

### 2.3 Create "Social Media Links Block List" Data Type

**Purpose**: Block List for social media links

1. **Create New Data Type**
   - Settings → Data Types → ••• → **Data Type**
   - Name: **"Social Media Links Block List"**
   - Editor: **Block List**

2. **Configure Block List Settings**
   - Click **"Add"** in the "Available Blocks" section
   - Select **"Social Media Link"** Element Type
   - Set as **Default** block
   - Click **Submit**

3. **Save the Data Type**

---

## Step 3: Add Footer Properties to Site Settings

Now we'll add footer properties to your existing **Site Settings** document type.

### 3.1 Open Site Settings Document Type

1. **Navigate to Settings**
   - Go to **Settings** → **Document Types**

2. **Find Site Settings**
   - Locate **"Site Settings"** in the list
   - Click on it to open

---

### 3.2 Add Footer Property Group

1. **Add Property Group**
   - Click **"Add group"**
   - Name: **"Footer"**

---

### 3.3 Add Footer Properties

Add the following properties to the **"Footer"** group:

#### Property 1: Disclaimer Text

- **Name**: `Disclaimer Text`
- **Alias**: `footerDisclaimerText`
- **Property Group**: **Footer**
- **Editor**: **Textarea** (or **Rich Text Editor** if formatting needed)
- **Mandatory**: ❌ No
- **Description**: "Privacy policy disclaimer shown at the top of the footer"

#### Property 2: App Store Badges

- **Name**: `App Store Badges`
- **Alias**: `footerAppStoreBadges`
- **Property Group**: **Footer**
- **Editor**: **Block List**
- **Data Type**: Select **"App Store Badges Block List"** (the Data Type we created)
- **Mandatory**: ❌ No
- **Description**: "App store download badges (App Store, Google Play, AppGallery)"

#### Property 3: Social Media Links

- **Name**: `Social Media Links`
- **Alias**: `footerSocialMediaLinks`
- **Property Group**: **Footer**
- **Editor**: **Block List**
- **Data Type**: Select **"Social Media Links Block List"**
- **Mandatory**: ❌ No
- **Description**: "Social media icons and links"

#### Property 4: Useful Tools Links

- **Name**: `Useful Tools Links`
- **Alias**: `footerUsefulToolsLinks`
- **Property Group**: **Footer**
- **Editor**: **Block List**
- **Data Type**: Select **"Footer Links Block List"**
- **Mandatory**: ❌ No
- **Description**: "Links for useful tools section (e.g., Find a branch, Rates and fees, Calculators)"

#### Property 5: Our Sites Links

- **Name**: `Our Sites Links`
- **Alias**: `footerOurSitesLinks`
- **Property Group**: **Footer**
- **Editor**: **Block List**
- **Data Type**: Select **"Footer Links Block List"**
- **Mandatory**: ❌ No
- **Description**: "Links for our sites section (e.g., Personal Banking, Business Banking)"

#### Property 6: Who We Are Links

- **Name**: `Who We Are Links`
- **Alias**: `footerWhoWeAreLinks`
- **Property Group**: **Footer**
- **Editor**: **Block List**
- **Data Type**: Select **"Footer Links Block List"**
- **Mandatory**: ❌ No
- **Description**: "Links for who we are section (e.g., About Us, Careers, Sustainability)"

#### Property 7: Support Links

- **Name**: `Support Links`
- **Alias**: `footerSupportLinks`
- **Property Group**: **Footer**
- **Editor**: **Block List**
- **Data Type**: Select **"Footer Links Block List"**
- **Mandatory**: ❌ No
- **Description**: "Links for support section (e.g., Talk to us, Give us feedback, Security centre)"

#### Property 8: Legal Links

- **Name**: `Legal Links`
- **Alias**: `footerLegalLinks`
- **Property Group**: **Footer**
- **Editor**: **Block List**
- **Data Type**: Select **"Footer Links Block List"**
- **Mandatory**: ❌ No
- **Description**: "Links for legal section (e.g., Data privacy statement, Cookie policy)"

#### Property 9: Legal/Regulatory Text

- **Name**: `Legal Regulatory Text`
- **Alias**: `footerLegalRegulatoryText`
- **Property Group**: **Footer**
- **Editor**: **Textarea** (or **Rich Text Editor**)
- **Mandatory**: ❌ No
- **Description**: "Legal and regulatory information shown at the bottom of the footer"

---

### 3.4 Save Site Settings Document Type

1. **Click "Save"** at the top right
2. Verify all properties are saved correctly

---

## Step 4: Create Content in Umbraco Backoffice

Now that the Document Type is set up, you need to add the footer content.

### 4.1 Open Site Settings Content Node

1. **Navigate to Content**
   - Go to **Content** section in Umbraco backoffice

2. **Find Site Settings**
   - Locate your **Site Settings** content node (usually at the root)
   - Click on it to open

3. **Navigate to Footer Tab**
   - You should now see a **"Footer"** tab in the editor
   - Click on it

---

### 4.2 Add Footer Content

Fill in the footer properties:

#### Add Disclaimer Text
- Enter the disclaimer text in the **"Disclaimer Text"** field
- Example: "Please note: To provide our products and services, we collaborate with other companies..."

#### Add App Store Badges
1. Click **"Create new"** in the **"App Store Badges"** field
2. Add 3 badges (one for each store):
   - **Badge 1**: 
     - Store Name: `App Store`
     - Badge Image: Upload App Store badge image
     - Download Link: Add App Store URL
   - **Badge 2**:
     - Store Name: `Google Play`
     - Badge Image: Upload Google Play badge image
     - Download Link: Add Google Play URL
   - **Badge 3**:
     - Store Name: `AppGallery`
     - Badge Image: Upload AppGallery badge image
     - Download Link: Add AppGallery URL

#### Add Social Media Links
1. Click **"Create new"** in the **"Social Media Links"** field
2. Add social media links:
   - **Twitter/X**: Platform Name: `Twitter/X`, Social Media Link: [your Twitter URL]
   - **Facebook**: Platform Name: `Facebook`, Social Media Link: [your Facebook URL]
   - **Instagram**: Platform Name: `Instagram`, Social Media Link: [your Instagram URL]

#### Add Footer Link Columns

For each link column (Useful Tools, Our Sites, Who We Are, Support, Legal):

1. Click **"Create new"** in the respective field
2. Add individual link items:
   - **Link Text**: The display text (e.g., "Find a branch/agent outlet")
   - **Link**: The URL (using Multi URL Picker)

**Example for Useful Tools Links:**
- Find a branch/agent outlet
- Branch codes
- Rates and fees
- Personal loan calculator
- Home loan calculator
- Find a home
- Our partners and offers

**Example for Our Sites Links:**
- Personal Banking
- Islamic Banking
- Business Banking
- Corporate Banking
- App, online and other banking

**Example for Who We Are Links:**
- About Absa Bank Kenya PLC
- About Absa Group
- Careers
- Citizenship
- Sustainability
- Investor relations
- Media centre

**Example for Support Links:**
- Talk to us
- Give us feedback
- Security centre
- Let us know what you think

**Example for Legal Links:**
- Data privacy statement
- Cookie policy
- Product terms and conditions

#### Add Legal/Regulatory Text
- Enter the legal text in the **"Legal Regulatory Text"** field
- Example: "Absa Bank Kenya PLC. Registered in Kenya. Registered office: Absa Head Quarters, Waiyaki Way, PO Box 30120, 00100 GPO, Nairobi, Kenya. Absa Bank Kenya PLC is regulated by the Central Bank of Kenya."

---

### 4.3 Save and Publish

1. Click **"Save"** to save your changes
2. Click **"Save and Publish"** to publish the footer content

---

## Step 5: Summary Checklist

Use this checklist to verify everything is set up correctly:

### Element Types Created:
- [ ] Footer Link Item (Content group: linkText, link)
- [ ] App Store Badge (Content group: storeName, badgeImage, downloadLink)
- [ ] Social Media Link (Content group: platformName, socialLink, iconImage)

### Data Types Created:
- [ ] Footer Links Block List (uses Footer Link Item)
- [ ] App Store Badges Block List (uses App Store Badge)
- [ ] Social Media Links Block List (uses Social Media Link)

### Site Settings Properties Added:
- [ ] Disclaimer Text (Textarea)
- [ ] App Store Badges (Block List)
- [ ] Social Media Links (Block List)
- [ ] Useful Tools Links (Block List)
- [ ] Our Sites Links (Block List)
- [ ] Who We Are Links (Block List)
- [ ] Support Links (Block List)
- [ ] Legal Links (Block List)
- [ ] Legal Regulatory Text (Textarea)

### Content Added:
- [ ] Disclaimer text entered in Site Settings
- [ ] App store badges added (3 badges)
- [ ] Social media links added (3+ links)
- [ ] Footer link columns populated with links
- [ ] Legal/regulatory text entered
- [ ] Site Settings saved and published

---

## Next Steps

After completing the backend setup:

1. **Create Footer Partial View**: Create `Views/Partials/Footer.cshtml` that reads from Site Settings
2. **Add Footer to Layout**: Include the footer partial in `Views/_Layout.cshtml`
3. **Style the Footer**: Add CSS styling to match your design
4. **Create Partial Views for Block Lists**: Create partial views for rendering the Block List items

---

## Important Notes

- **Property Groups are Required**: Every property must belong to a group in Umbraco 17
- **Aliases Matter**: Use camelCase for aliases (e.g., `footerAppStoreBadges`)
- **Save Frequently**: Always save Document Types after making changes
- **Element Types**: Cannot be created in Content tree, only used in Block Lists/Grids
- **Block Lists Need Data Types**: Create the Data Type first, then use it as a property editor

---

## Troubleshooting

**Problem**: Can't find "Block List" editor option
- **Solution**: Make sure you've created the Data Type first. The Block List editor appears when you select a Block List Data Type.

**Problem**: Element Type not showing in Block List configuration
- **Solution**: Make sure the Element Type is saved. Refresh the Data Type configuration page.

**Problem**: Footer tab not showing in Site Settings
- **Solution**: Make sure you saved the Site Settings Document Type after adding the Footer property group and properties.

---

## References

- [Umbraco 17 Documentation - Defining Content](https://docs.umbraco.com/umbraco-cms/fundamentals/data/defining-content)
- [Umbraco 17 Documentation - Block List Editor](https://docs.umbraco.com/umbraco-cms/fundamentals/backoffice/property-editors/built-in-umbraco-property-editors/block-editor/block-list-editor)
