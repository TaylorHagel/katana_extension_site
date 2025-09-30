---
layout: page
title: User Guide
permalink: /instructions/
---

# Katana Chrome Extension - User Guide

**Welcome!** This guide will help you use the Katana Master Extension to streamline your workflow. No technical experience required - just follow the steps below.

> **💡 First time with Katana?** This extension works alongside your Katana MRP account at https://factory.katanamrp.com to make common tasks faster and easier.

## Getting Help

1. **Check the History box** - Keeps a log of what actions have been performed by the tool.
2. **Watch progress bars** - they show real-time status and completion details
3. **Look at downloaded results files** - they show specific issues with each row
4. **Try the operation on a smaller test file first**
5. **Report issues on GitHub** - Use the repository issue tracker for bug reports
6. **Contact support** with specific error messages from the Memory box

**Debug Information:**

- Click the debug panel toggle in the extension footer for technical details
- Error messages are now cleaner and more focused on actual issues
- This information helps with troubleshooting complex issues

## Table of Contents

- [Getting Started](#getting-started)
- [Basic Tools](#basic-tools)
- [Customer Management](#customer-management)
- [Supplier Management](#supplier-management)
- [Service Management](#service-management)
- [Price List Management](#price-list-management)
- [Multiple Email Tool](#multiple-email-tool)
- [Data Export Tools](#data-export-tools)
- [Troubleshooting](#troubleshooting)

---

## Getting Started

### Installing the Extension

1. **Install from Chrome Web Store** (when available)
   - Search for "Katana Master Extension"
   - Click "Add to Chrome"
   - Pin the extension to your toolbar

2. **Open Katana in your browser**
   - Go to https://factory.katanamrp.com
   - Log into your Katana account
   - Click on the pinned extension
   - You should see a side panel appear on the right

### Setting Up Your API Key

**What's an API Key?** Think of it as a secure password that lets the extension talk to your Katana account.

1. **Find your API key in Katana:**
   - In Katana, go to Settings → Integrations → API
   - Copy your API key (long string of letters and numbers)
   - SAVE THIS CODE SECURELY. API KEY IS STORED PER SESSION AND WILL NEED TO BE RE-ENTERED OCCASIONALLY!

2. **Enter it in the extension:**
   - Look for the API key prompt in the side panel
   - Paste your API key and click "Save"
   - The extension will remember this securely

### Understanding the Side Panel

The side panel appears on the right side of your Katana pages and shows different tools based on what page you're viewing:

- **Customer pages** → Customer management tools
- **Supplier pages** → Supplier management tools  
- **Service pages** → Service management tools
- **Price list pages** → Price list tools
- **Settings page** → Tool Display Settings

The **History box** at the top keeps a log of everything you do - think of it as your activity history.

---

## Basic Tools

### Managing Tool Visibility

**What this does:** Control which tools appear on each page type.

1. **Find the "Tool Display Settings" section** (appears on Katana Settings page)
2. **Click to expand it**
3. **Check/uncheck tools** you want to see
4. **Changes save automatically** - no need to refresh

**Tip:** If the side panel feels cluttered, turn off tools you don't use frequently.

### Using Keyboard Shortcuts

**Quick access to common actions:**

- **Ctrl+Shift+K** → Opens Katana admin panel in new tab
- **Insert key** → Clicks "Add New Row" buttons (after setup)

**To set up the Insert key:**

1. Go to any page with data tables
2. Find "Keyboard Shortcuts Tool" in the side panel
3. Click "Enable Insert Key"
4. Now pressing Insert will click "Add New Row" buttons automatically

### Understanding the History Box

**What it is:** A permanent log of your extension activities that stays visible as you navigate.

**To clear it:** Click the trash can icon when it gets too full.

---

## Customer Management

### Downloading Customer Data

**When to use:** Get all your customer information in Excel format.

1. **Go to Contacts → Customers** in Katana
2. **Find "Customer Data Management" in the side panel**
3. **Click "Download Customer Data"**
4. **Wait for the download** - you'll see progress in the side panel
5. **Open the Excel file** to view all customer information

### Importing New Customers

**When to use:** Add multiple customers at once from a spreadsheet.

1. **Download the template first:**
   - Click "Download Import Template"
   - Open the Excel file

2. **Fill in customer information:**
   - **Required:** Display Name, Email
   - **Optional:** Address, phone, company details
   - One customer per row

3. **Import your customers:**
   - Click "Import Customers"
   - Select your filled-out Excel file
   - Watch the progress - successful imports show in green

4. **Check results:**
   - Click the download link in the results to see what happened
   - Any errors will be clearly marked

### Editing Existing Customers

**When to use:** Update customer information in bulk.

1. **Download existing data:**
   - Click "Download Customer Data"
   - This includes special "hash" columns - don't delete these!

2. **Make your changes:**
   - Edit any customer information you want to update
   - Add new customers to the bottom of the file
   - Don't change data in the hidden Customer ID or hash columns
   - Save the file

3. **Re-import the changes:**
   - Click "Import Customers"
   - Select your edited file
   - The extension only updates rows you actually changed

4. **Review what happened:**
   - Download the results file to see which customers were updated
   - The History box shows a summary

---

## Supplier Management

### Downloading Supplier Data

**When to use:** Export all supplier information to Excel.

1. **Go to Contacts → Suppliers** in Katana
2. **Click "Download Supplier Data"** in the side panel
3. **Wait for download completion**
4. **Open Excel file** to view supplier data

### Importing New Suppliers

**When to use:** Add multiple suppliers from a spreadsheet.

1. **Get the template:**
   - Click "Download Import Template"
   - Open the Excel template

2. **Add supplier information:**
   - Fill in supplier names, contact info, addresses
   - One supplier per row

3. **Import suppliers:**
   - Click "Import Suppliers"
   - Choose your completed file
   - Monitor progress in the side panel

### Editing Existing Suppliers

**Same process as customers:**

1. Download existing supplier data
2. Make changes or create new (don't touch ID or hash columns)
3. Re-import the file
4. Review results

---

## Service Management

### Checking Service Orders

**When to use:** See all open sales orders for a specific service item.

1. **Go to any service item page** (Services → click on a service)
2. **Click "View Open Orders"** in the side panel
3. **Results appear in the Memory box** with clickable order numbers
4. **Click order numbers** to open them in new tabs

**Note:** Each time you check a service, results are added to Memory (not replaced).

### Managing Service Items

**Import/Export service items in bulk:**

1. **Download template or existing services:**
   - "Download Services Template" → Empty template for new services
   - "Download Services" → All existing services for editing

2. **Edit your spreadsheet:**
   - Add new services or modify existing ones
   - Service ID determines if it's new (blank) or update (filled)

3. **Import services:**
   - Click "Import Service Items"
   - Select your file
   - Progress shows in real-time

---

## Price List Management

### Adding Customers to Price Lists

**When to use:** Assign multiple customers to a price list at once.

1. **Go to Price Lists** in Katana
2. **In the side panel, click "Download Customer Template"**
3. **Fill in the Excel template:**
   - Column D - "Price List Name" is populated with a dropdown of your current price lists (Active & Inactive)
   - Select the appropriate price list per customer
   - Save the edited file

4. **Import the customer list:**
   - Click "Import Customer Price List"
   - Select your file
   - Customers already on the price list are skipped

5. **Check results:**
   - History box shows how many were added/skipped
   - Download results file for details

---

## Multiple Email Tool

### Setting Up Multiple Emails for Purchase Orders

**What this does:** Allows purchase orders to be sent to multiple supplier email addresses automatically, bypassing Katana's single-email limitation.

**⚠️ IMPORTANT: Read all warnings before using this feature!**

#### Step 1: Update Supplier Email Information

1. **Go to Contacts → Suppliers** in Katana
2. **Use the Supplier Edit Tool:**
   - Click "Download Supplier Data" to get the edit file
   - Open the Excel file and find the supplier you want to update
   - In the "Email" column, enter multiple email addresses separated by ", " (comma and space)
   - **Format example:** `primary@supplier.com, accounting@supplier.com, orders@supplier.com`
   - **Maximum:** 3 email addresses per supplier
3. **Re-import the file:**
   - Click "Import Suppliers" and select your edited file
   - The extension will update the supplier with multiple emails

### Using the Multiple Email Feature

**How it works:** The tool runs automatically in the background - no manual activation needed.

1. **Go to any Purchase Order page** (the tool activates automatically)
2. **Click the Email button** as you normally would
3. **The tool automatically:**
   - Detects if the supplier has multiple emails configured
   - Processes any email validation errors
   - Extracts and enters all email addresses individually
   - Handles the email sending process seamlessly

**What you'll see:** The email dialog will populate with all configured email addresses as separate entries.

### Important Warnings and Limitations

#### ⚠️ Critical Warnings

**QuickBooks Online Integration Issues:**
- Multiple emails **WILL cause QBO sync problems**
- Email is the primary field used to match suppliers between Katana and QBO
- Suppliers with multiple emails may not sync properly

**Supplier Management Limitations:**
- Suppliers with multiple emails will show **validation errors** on their supplier cards
- **In-app supplier editing will not work** for these suppliers
- All future updates must be done through the **Admin Panel** or the Supplier Edit Tool
- The supplier card will display as having data errors

**Technical Considerations:**
- This tool bypasses Katana's standard email validation
- Multiple emails are not officially supported by Katana
- Use only when the benefits outweigh the integration risks

#### ✅ Best Practices

1. **Test first:** Try with one non-critical supplier before widespread use
2. **Document changes:** Keep a record of which suppliers have multiple emails
3. **QBO users:** Consider if email-based supplier sync is critical for your workflow
4. **Backup plan:** Ensure you can manage supplier updates through Admin Panel

#### 🔧 Technical Details

- **Email limit:** Maximum 3 email addresses per supplier
- **Format requirement:** Must be separated by ", " (comma and space)
- **Automatic activation:** No setup required - works on all purchase order pages
- **Error handling:** Gracefully processes validation errors and extracts valid emails

---

## Data Export Tools

### Exporting Custom Field Data

**When to use:** Get, add or edit product, material, or inventory data with custom field values.

**NOTE:** Custom field collections must be created in Katana first.

1. **Go to the relevant page:**
   - Products page
   - Materials page 
   - Inventory page

2. **Click the export button** for your data type
3. **Wait for processing** - larger datasets take longer
4. **Download Excel file** with all data and custom field values
5. **Edit File Accordingly** add/edit custom field collection and values

**What you get:** Complete data export including all custom field values in Excel format and the ability to edit custom fields in bulk.

---

## Troubleshooting

### Common Issues

**"Tools not loading"**
- Make sure you're logged into Katana
- Try refreshing the page
- Check that the extension is enabled

**"API key errors"**
- Verify your API key is correct (Settings → Integrations → API in Katana)
- Re-enter the API key in the extension
- Make sure your Katana account has API access

**"Import failures"**
- Check that required fields are filled (marked with * in templates)
- Make sure email addresses are valid
- Don't modify ID or hash columns in edit files

**"Extension disappeared"**
- Pin the extension to your Chrome toolbar
- The side panel only appears on Katana pages
- Try closing and reopening Chrome

### Getting Help

1. **Check the History box** - error messages often explain what went wrong
2. **Look at downloaded results files** - they show specific issues with each row
3. **Try the operation on a smaller test file first**
4. **Contact support** - taylor.hagel@katanamrp.com 

**Debug Information:**
- Click the debug panel toggle in the extension footer for technical details
- This information helps with troubleshooting complex issues

---

## Tips for Success

1. **Start small** - test imports with just a few rows first
2. **Use templates** - they have the right format and required fields
3. **Don't edit ID columns** - let the extension manage these
4. **Watch progress bars** - modern progress tracking shows real-time operation status
5. **Check the History box** - it shows summaries and results from all operations
6. **Download results files (Where Applicable)** - they explain exactly what happened with each row
7. **Keep the side panel open** - tools update automatically as you navigate

---

**Need more technical details?** Check out the [Technical Documentation]({{ site.baseurl }}/readme/) for complete documentation, API architecture, and development information.