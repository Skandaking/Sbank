# Backend Setup: Bank Cards Section

## Step 1: Add Properties to Home Page Document Type

1. **Go to Umbraco Backoffice**
   - Navigate to **Settings** → **Document Types**
   - Find and click on **"Home Page"** document type

2. **Add a New Property Group**
   - Click **"Add group"** button
   - Name it: **"Bank Cards Section"**

3. **Add Properties to the Group**

   **Property 1: Bank Card Images**
   - Click **"Add property"** in the "Bank Cards Section" group
   - **Name**: `Bank Card Images`
   - **Alias**: `bankCardImages` (auto-generated)
   - **Property Group**: Select "Bank Cards Section"
   - **Select Editor**: Choose **Media Picker**
   - **Configuration**: 
     - **Multiple**: Toggle ON (to allow multiple images)
     - **Allowed Types**: Image only
   - **Description**: "Upload 2 bank card images (stacked)"
   - **Mandatory**: Toggle OFF (optional)
   - Click **Submit**

   **Property 2: Section Title**
   - Click **"Add property"** again
   - **Name**: `Section Title`
   - **Alias**: `sectionTitle` (auto-generated)
   - **Property Group**: Select "Bank Cards Section"
   - **Select Editor**: Choose **Textstring**
   - **Description**: "Main heading for the bank cards section"
   - **Mandatory**: Toggle OFF
   - Click **Submit**

   **Property 3: Section Description**
   - Click **"Add property"** again
   - **Name**: `Section Description`
   - **Alias**: `sectionDescription` (auto-generated)
   - **Property Group**: Select "Bank Cards Section"
   - **Select Editor**: Choose **Textarea** (or **Rich Text Editor** if you need formatting)
   - **Description**: "Description text for the bank cards section"
   - **Mandatory**: Toggle OFF
   - Click **Submit**

   **Property 4: Button Text**
   - Click **"Add property"** again
   - **Name**: `Button Text`
   - **Alias**: `buttonText` (auto-generated)
   - **Property Group**: Select "Bank Cards Section"
   - **Select Editor**: Choose **Textstring**
   - **Description**: "Text for the call-to-action button"
   - **Mandatory**: Toggle OFF
   - Click **Submit**

   **Property 5: Button Link**
   - Click **"Add property"** again
   - **Name**: `Button Link`
   - **Alias**: `buttonLink` (auto-generated)
   - **Property Group**: Select "Bank Cards Section"
   - **Select Editor**: Choose **Multi URL Picker**
   - **Description**: "Link destination for the button"
   - **Mandatory**: Toggle OFF
   - Click **Submit**

4. **Save the Document Type**
   - Click **Save** in the bottom right corner

---

## Step 2: Add Content in Umbraco Backoffice

1. **Go to Content Section**
   - Navigate to **Content** in Umbraco backoffice
   - Click on your **Home Page** content node

2. **Fill in the Bank Cards Section**
   - Scroll to the **"Bank Cards Section"** tab/group
   - **Bank Card Images**: Click to upload 2 bank card images
   - **Section Title**: Enter your title (e.g., "Choose Your Perfect Card")
   - **Section Description**: Enter your description text
   - **Button Text**: Enter button text (e.g., "Apply Now" or "Learn More")
   - **Button Link**: Select a page or enter a URL

3. **Save and Publish**
   - Click **Save and Publish**

---

## Step 3: Create the View (Frontend)

I'll create the Razor view to render this section. The view will:
- Display the 2 bank card images stacked on one side
- Show the text content and button on the other side
- Use Tailwind CSS for styling
- Be responsive (stacks on mobile, side-by-side on desktop)

---

## Property Aliases Summary

After setup, you'll have these property aliases:
- `bankCardImages` - Media Picker (multiple images)
- `sectionTitle` - Textstring
- `sectionDescription` - Textarea
- `buttonText` - Textstring
- `buttonLink` - Multi URL Picker

---

## Alternative: Using Block List (More Flexible)

If you want more flexibility (e.g., multiple sections, reordering), you could:

1. Create an Element Type called "Bank Cards Section"
2. Add the same properties to that Element Type
3. Add a Block List property to Home Page called "Content Sections"
4. Add the "Bank Cards Section" as an available block type

This approach allows you to add multiple sections and reorder them easily.

Let me know which approach you prefer, and I'll create the corresponding view!
