# Next Steps: Rendering Your Content

You've created your Document Types and properties. Now let's make them visible on your website!

## ✅ What You've Completed

- [x] Created Element Types (Hero Promotional Block, Navigation Item, etc.)
- [x] Created Document Types (Home Page, Site Settings)
- [x] Created Data Types (Block Lists)
- [x] Added properties to Home Page (Site Title, Site SubTitle, Hero Promotional Blocks)

## 🎯 What's Next

### Step 1: Create Content in Umbraco Backoffice

1. **Go to Content Section**
   - Navigate to **Content** in the Umbraco backoffice

2. **Create Home Page Content**
   - Click the menu icon (•••) next to **Content**
   - Select **"Home Page"** document type
   - Fill in:
     - **Site Title**: Your site's main title
     - **Site Sub Title**: Your site's subtitle
     - **Hero Promotional Blocks**: Click "Create new" to add hero blocks
       - Add 3 blocks (or as many as you need)
       - For each block, fill in:
         - Image (upload an image)
         - Title
         - Description (optional)
         - Call to Action Text
         - Call to Action Link
   - Click **Save and Publish**

### Step 2: Verify Your Views Are Set Up

I've created the following files for you:

- ✅ `Views/HomePage.cshtml` - Updated to render your content
- ✅ `Views/_Layout.cshtml` - Basic layout/master page
- ✅ `Views/Partials/blocklist/Components/HeroPromotionalBlock.cshtml` - Partial view for hero blocks
- ✅ `wwwroot/css/site.css` - Basic styling

### Step 3: Check Your Element Type Alias

**IMPORTANT**: The partial view file name must match your Element Type alias exactly!

- If your Element Type alias is: `heroPromotionalBlock`
- The partial view should be: `HeroPromotionalBlock.cshtml` (PascalCase)

**To check your alias:**
1. Go to **Settings** → **Document Types**
2. Find **"Hero Promotional Block"** Element Type
3. Check the alias (it should be `heroPromotionalBlock`)

**If your alias is different**, rename the file:
- Current: `Views/Partials/blocklist/Components/HeroPromotionalBlock.cshtml`
- Rename to match your alias (e.g., if alias is `heroPromoBlock`, rename to `HeroPromoBlock.cshtml`)

### Step 4: Test Your Site

1. **Run your Umbraco site**
2. **Navigate to the homepage**
3. You should see:
   - Your Site Title
   - Your Site Sub Title
   - Your Hero Promotional Blocks rendered

### Step 5: Customize the Styling

The CSS file (`wwwroot/css/site.css`) has basic styling. Customize it to match your design:

- Adjust grid layout for hero blocks
- Change colors, fonts, spacing
- Add responsive breakpoints
- Match the Absa Bank design from your reference image

### Step 6: Create Navigation Views (Next)

Once your hero section is working, you'll want to:

1. **Create Site Settings content node**
   - Content → ••• → **Site Settings**
   - Add your logo
   - Add navigation items

2. **Create Navigation partial views**
   - `Views/Partials/blocklist/Components/NavigationItem.cshtml`
   - `Views/Partials/blocklist/Components/CtaNavigationItem.cshtml`

3. **Add navigation to layout**
   - Update `Views/_Layout.cshtml` to include navigation

## 🔍 Troubleshooting

### Hero blocks not showing?

1. **Check the property alias**
   - In HomePage.cshtml, verify: `heroPromotionalBlocks` matches your property alias
   - If different, update line: `Model.Value<BlockListModel>("yourActualAlias")`

2. **Check the Element Type alias**
   - The partial view filename must match the Element Type alias
   - File location: `Views/Partials/blocklist/Components/[YourAlias].cshtml`

3. **Check content is published**
   - Make sure you clicked **Save and Publish** (not just Save)

4. **Check browser console**
   - Open browser DevTools (F12)
   - Look for any errors

### Property values not displaying?

- Check property aliases match exactly (case-sensitive)
- Use `Model.Value<string>("propertyAlias")` for simple properties
- Use `Model.Value<BlockListModel>("propertyAlias")` for Block Lists

## 📝 Quick Reference

**Property Aliases in HomePage.cshtml:**
- `siteTitle` - Site Title property
- `siteSubTitle` - Site Sub Title property  
- `heroPromotionalBlocks` - Hero Promotional Blocks property

**Block List Component Location:**
- `Views/Partials/blocklist/Components/[ElementTypeAlias].cshtml`

**Rendering Block Lists:**
```csharp
@await Html.GetBlockListHtmlAsync(heroPromotionalBlocks)
```

## 🎨 Next: Navigation

After your hero section is working, we can:
1. Create navigation partial views
2. Add navigation to the layout
3. Style the navigation to match your design

Let me know when your hero section is displaying correctly, and we'll move on to the navigation!
