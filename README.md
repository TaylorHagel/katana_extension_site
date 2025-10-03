# Katana Chrome Extension

> **👋 New User?** Check out [**instructions.md**](instructions.md) for simple, step-by-step guides on using each tool.
>
> **🔧 Developer/Technical User?** You're in the right place! This README contains complete technical documentation.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
  - [API Key Entry and Storage](#api-key-entry-and-storage)
  - [Navigation and Tool Loading](#navigation-and-tool-loading)
  - [Global History Info Box](#global-History-info-box)
  - [Keyboard Shortcuts](#keyboard-shortcuts)
- [Current Tools](#current-tools)
  - [1. Price List Customer Template & Import Tool](#1-price-list-customer-template--import-tool)
  - [2. Service Item Open Orders Tool](#2-service-item-open-orders-tool)
  - [3. Customers Tool (with Edit Functionality)](#3-customers-tool-with-edit-functionality)
  - [4. Suppliers Tool (with Edit Functionality)](#4-suppliers-tool-with-edit-functionality)
  - [5. Data Table Component](#5-data-table-component)
  - [6. Custom Field Tools (Unified)](#6-custom-field-tools-unified)
  - [7. Service Items Management Tool](#7-service-items-management-tool)
  - [8. Keyboard Shortcuts Tool](#8-keyboard-shortcuts-tool)
  - [9. Tool Visibility Management](#9-tool-visibility-management)
  - [10. Multiple Email Tool (Purchase Orders)](#10-multiple-email-tool-purchase-orders)
  - [11. Historical Sales Orders Import Tool](#11-historical-sales-orders-import-tool)
- [API Architecture](#api-architecture)
  - [Centralized API Layer](#centralized-api-layer--completed)
  - [API Modules](#api-modules-srctoolsapi)
  - [Utility Layer](#utility-layer-srctoolsutils)
  - [Benefits](#benefits)
  - [Usage Pattern](#usage-pattern)
- [Debug Panel](#debug-panel)
- [Hash Tool: Why and How We Use It](#hash-tool-why-and-how-we-use-it)
  - [What is the Hash Tool?](#what-is-the-hash-tool)
  - [Why Use Hashes?](#why-use-hashes)
  - [Example Workflow](#example-workflow)
  - [Technical Example: How Hashes Are Computed](#technical-example-how-hashes-are-computed)
- [How to Use Edit Functionality (Customers & Suppliers)](#how-to-use-edit-functionality-customers--suppliers)
- [Security](#security)
- [Usage Notes](#usage-notes)
- [Future Tools](#future-tools)
- [Changelog](#changelog)
  - [Pre-deployment (Current Development)](#pre-deployment-current-development)
  - [Planned for V1.0.0 (Initial Release)](#planned-for-v100-initial-release)
  - [Future Roadmap](#future-roadmap)

## Overview

This Chrome extension enhances the Katana MRP web experience by providing advanced tools and workflow automation directly in a persistent side panel. It is designed for use with https://factory.katanamrp.com and interacts with the Katana API using your personal API key.

**Production Status:** Ready for Chrome Web Store submission with complete progress system implementation, centralized API architecture, and production-ready code quality.

## Features

### API Key Entry and Storage

- On first use, you are prompted to enter your Katana API key in the extension's side panel.
- The API key is stored securely in your browser's local storage, encrypted per session, and is never synced or sent anywhere except to the Katana API.
- You can change or remove your API key at any time using the controls in the extension footer.

### Navigation and Tool Loading

- The extension automatically detects which Katana page you are viewing in your main browser tab.
- Tools are loaded dynamically in the side panel based on the active tab's URL (e.g., price list pages, service item pages, customer list pages).
- The side panel remains open and persistent as you navigate Katana, and tools update automatically as you switch between supported pages.
- **Tool Visibility Management:** Control which tools appear on each page type through the collapsible management interface. Settings are saved persistently and take effect immediately.
- Some tool panels (like open orders and History) are persistent and will remain open until you clear them or the extension is closed.

### Global History Info Box

- A global persistent info box titled **History** is always visible in the side panel.
- All tools can append results, logs, or summaries to the History box using standardized messaging patterns.
- **Success Messages:** Clean, concise summaries with statistics (e.g., "59 Suppliers Downloaded", "15 Updates, 2 Errors").
- **Error Messages:** Clear error descriptions with context for troubleshooting.
- **Debug Messages:** Detailed technical information that persists for review and debugging.
- Each entry is appended and never overwrites previous content, maintaining a complete session history.
- The History box is ideal for keeping a running log of tool results, such as open sales orders, import summaries, or other important information.
- You can clear the History box at any time using the trashcan icon.

### Keyboard Shortcuts

- **Admin Panel Access:** Press `Ctrl+Shift+K` to instantly open the Katana admin panel in a new tab from anywhere in the application.
- **Add New Row:** Configure the Insert key (or other keys) to trigger "Add New Row" buttons on Katana pages through the Keyboard Shortcuts tool.
- **Persistent Configuration:** All keyboard shortcuts are saved to localStorage and remain active across browser sessions.

## Current Tools

### 1. Price List Customer Template & Import Tool

- **Pages:** Loads on `/price-list`, `/price-lists`, and their subpages.
- **Features:**
  - Download a customer price list Excel template (using ExcelJS).
  - Import customer price lists from Excel, with duplicate detection and detailed error/debug logging.
  - Skips customers already assigned to a price list and logs skipped names.
  - All import actions display a loading wheel overlay for user feedback.
  - Import results are shown in the info box with bold titles and line breaks for clarity. A "Download Results" hyperlink is provided for results files (not auto-downloaded).

### 2. Service Item Open Orders Tool

- **Pages:** Loads on `/service/<id>` (service item detail pages).
- **Features:**
  - Button to view all open sales orders for the current service item.
  - Fetches service details, variant, and all related open sales orders via the Katana API.
  - Displays sales order numbers as clickable links in the persistent, append-only History box.
  - Each time you view open orders for a service item, a new entry is appended to History (previous entries are never overwritten).
  - The History box remains visible across navigation until cleared by the user.
  - All actions display a loading wheel overlay for user feedback.
  - Info box messages use bold titles and line breaks for readability.

### 3. Customers Tool (with Edit Functionality)

- **Pages:** Loads on `/contacts/customers` (customer list page).
- **Features:**
  - **Download Customer Data:** Download all customer data from Katana as an Excel file.
  - **Download Import Template:** Download an Excel import template with the following headers (required fields marked with \*):
    - First Name, Last Name, Company, Display Name*, Email*, Phone, Currency, Comment, Discount (Must be Number), Reference ID, Category, Billing First Name, Billing Last Name, Billing Company, Billing Phone, Billing Address Line 1, Billing Address Line 2, Billing City, Billing State, Billing Zip, Billing Country, Default Shipping First Name, Default Shipping Last Name, Default Shipping Company, Default Shipping Phone, Default Shipping Address Line 1, Default Shipping Address Line 2, Default Shipping City, Default Shipping State, Default Shipping Zip, Default Shipping Country, Other Shipping First Name, Other Shipping Last Name, Other Shipping Company, Other Shipping Phone, Other Shipping Address Line 1, Other Shipping Address Line 2, Other Shipping City, Other Shipping State, Other Shipping Zip, Other Shipping Country
  - **Import Customers:** Import customers from an Excel file matching the template above. Each row is validated and posted to the Katana API. Import results (success or error) are written to a new results file for review, and progress is shown in the UI.
  - **Edit Customers:** Download the combined edit file, make changes to customer or address fields, and re-import. The tool uses hash logic to detect changes and only updates records that have been modified. Results are shown in the info box with a "Download Results" link for review.
  - All import and edit actions display a loading wheel overlay for user feedback.
  - All import and download actions append a summary to the History box for persistent reference, using bold titles and line breaks.

### 4. Suppliers Tool (with Edit Functionality)

- **Pages:** Loads on `/contacts/suppliers` (supplier list page).
- **Features:**
  - **Download Supplier Data:** Download all supplier data from Katana as an Excel file.
  - **Download Import Template:** Download an Excel import template with required supplier fields.
  - **Import Suppliers:** Import suppliers from an Excel file matching the template. Each row is validated and posted to the Katana API. Import results (success or error) are written to a new results file for review, and progress is shown in the UI.
  - **Edit Suppliers:** Download the combined edit file, make changes to supplier or address fields, and re-import. The tool uses hash logic to detect changes and only updates records that have been modified. Results are shown in the info box with a "Download Results" link for review.
  - All import and edit actions display a loading wheel overlay for user feedback.
  - All import and download actions append a summary to the History box for persistent reference, using bold titles and line breaks.

### 5. Data Table Component

- **Features:**
  - **Multi-format Input:** Supports JSON arrays, CSV strings, or individual objects for data display.
  - **Auto-header Detection:** Automatically extracts column headers from data structure.
  - **Export Capabilities:** Export displayed data to CSV, JSON, or Excel formats via professional export modal.
  - **Optional Editing:** Configurable inline editing with add/delete row functionality and real-time change callbacks.
  - **Responsive Design:** Clean, compact table with sticky headers and scrollable content that matches extension styling.
  - **Integration Ready:** Any tool can display tabular data using `window.showDataTable()` with flexible configuration options.

### 6. Custom Field Tools (Unified)

- **Pages:** Loads on `/products`, `/materials`, and `/inventory` pages.
- **Features:**
  - **Unified Interface:** Single tool providing custom field functionality across Products, Materials, and Inventory pages.
  - **Product Custom Fields:** Export product custom field data to Excel with all product details and custom field values.
  - **Material Custom Fields:** Export material custom field data to Excel with all material details and custom field values.
  - **Bulk Edit & Import:** Edit custom field values in Excel and re-import to update multiple records at once. The tool uses hash logic to detect changes and only updates records that have been modified, ensuring efficient processing and accurate change tracking.
  - **Hash-based Change Detection:** Only processes rows where custom field values have changed, skipping unchanged records to minimize unnecessary API calls and provide clear audit trails.
  - **Auto-detection:** Automatically detects which page type you're on and shows relevant custom field options.
  - **Progress Tracking:** Real-time progress indicators during export and import operations with detailed completion summaries.
  - **History Integration:** All export and import results are logged to the persistent History box for reference.

### 7. Service Items Management Tool

- **Pages:** Loads on `/services/` (services list page).
- **Features:**
  - **Download Services Template:** Generate an Excel template with proper headers for service import/editing.
  - **Download Services:** Export all existing services to Excel with Service ID tracking for updates.
  - **Import Service Items:** Import new services or update existing ones from Excel files.
  - **Hash-based Change Detection:** Only updates services that have been modified, skipping unchanged records.
  - **Dual Operation Mode:** Automatically detects whether to create new services or update existing ones based on Service ID presence.
  - **Progress Tracking:** Real-time import progress with detailed success/error reporting.
  - **Result Files:** Comprehensive result files showing which services were created, updated, or had errors.

### 8. Keyboard Shortcuts Tool

- **Pages:** Available as a tool for configuring keyboard shortcuts.
- **Features:**
  - **Add New Row Shortcut:** Configure keyboard shortcut to trigger "Add New Row" buttons on Katana pages.
  - **Material-UI Support:** Enhanced button detection that works with Material-UI components and complex DOM structures.
  - **Persistent Configuration:** Shortcuts are saved to localStorage and automatically active when configured.
  - **Current Options:** Insert key (default), with infrastructure for additional keys in future updates.
  - **Real-time Table:** Shows current shortcut configuration with immediate updates when changes are made.
  - **Smart Detection:** Finds Add Row buttons by text content, including those in span elements and nested structures.

### 9. Tool Visibility Management

- **Pages:** Available on all pages as a persistent management interface.
- **Features:**
  - **Granular Control:** Enable/disable specific tools per page type without affecting others.
  - **Persistent Settings:** Tool visibility preferences saved to localStorage and maintained across sessions.
  - **Collapsible Interface:** Clean, space-efficient management panel that stays out of the way.
  - **Real-time Updates:** Changes take effect immediately without requiring page refresh.
  - **Consolidated Options:** Simplified interface with logical groupings (e.g., unified Custom Field Tools).

### 10. Multiple Email Tool (Purchase Orders)

- **Pages:** Automatically active on `/purchaseorder/<id>` (purchase order detail pages).
- **Features:**
  - **Automatic Email Processing:** Monitors purchase order email functionality and automatically handles multiple email addresses.
  - **Supplier Email Workaround:** Enables sending purchase orders to multiple supplier email addresses (up to 3) when configured in supplier data.
  - **Error Detection & Correction:** Detects email validation errors and automatically extracts and processes multiple email addresses.
  - **Background Operation:** Runs transparently - no user interface required, activates when email button is pressed.
  - **Format Support:** Processes emails separated by ", " (comma and space) in supplier email fields.
- **Setup Requirements:**
  - Use Supplier Edit Tool to update supplier email field with multiple addresses separated by ", "
  - Format: "primary@email.com, secondary@email.com, third@email.com" (max 3 addresses)
- **⚠️ Important Warnings:**
  - **QBO Sync Issues:** Using multiple emails may cause QuickBooks Online sync issues as email is the primary sync field
  - **Supplier Card Errors:** Suppliers with multiple emails will show validation errors on their supplier cards
  - **Limited Supplier Updates:** In-app supplier updates will not function for suppliers with multiple emails - use Admin Panel instead
  - **API Bypass:** Multiple email updates bypass Katana's standard data validation

### 11. Historical Sales Orders Import Tool

- **Pages:** Loads on sales-related pages for historical data import.
- **Features:**
  - **Shopify Integration:** Direct import from Shopify order exports with automatic format detection
  - **Fulfillment Filtering:** Only imports "fulfilled" orders from Shopify exports (uses "Lineitem fulfillment status" column)
  - **Template Support:** Custom template format for non-Shopify historical data
  - **Inventory Balancing:** Creates stock adjustments to balance inventory (Stock Added = Stock Sold)
  - **Customer Management:** Automatically creates customers that don't exist, matches by email/name
  - **Cost Averaging:** Averages unit costs per SKU when multiple costs are provided
  - **Comprehensive Creation:** Creates stock adjustments, customers, sales orders, and fulfillments
  - **Date Validation:** Ensures compatibility with inventory closing dates (18-month maximum lookback)
  - **Real-time Progress:** Detailed progress tracking with per-phase updates
  - **Results Logging:** Comprehensive results with downloadable status logs
- **Import Process:**
  1. **Stock Adjustment:** Creates inventory to match historical sales (dated 1 day before oldest order)
  2. **Customer Creation:** Creates missing customers with contact information and addresses
  3. **Sales Order Creation:** Imports historical orders with proper dates and customer links
  4. **Fulfillment Creation:** Marks orders as fulfilled with historical fulfillment dates
- **Shopify Requirements:**
  - Standard Shopify order export with all columns
  - "Lineitem fulfillment status" column for accurate filtering
  - Optional "Cost Per Item" column for inventory costing
- **⚠️ Important Considerations:**
  - **Inventory Impact:** Adjusts inventory closing dates and stock levels
  - **Accountant Consultation:** Recommend consulting accountant before changing inventory closing dates
  - **18-Month Limit:** Cannot import orders older than 18 months from current date
  - **Fulfilled Orders Only:** Shopify imports skip all unfulfilled orders to maintain inventory accuracy

## API Architecture

### Centralized API Layer ✅ COMPLETED

The extension features a fully implemented, centralized API architecture that eliminates code duplication and follows Katana's official API best practices:

#### API Modules (`src/tools/api/`)

- **`customers.js`** - Complete customer CRUD operations ✅
- **`products.js`** - Product management and retrieval functions ✅
- **`materials.js`** - Material data operations ✅
- **`suppliers.js`** - Supplier management functions ✅
- **`customFields.js`** - Custom field collection operations ✅
- **`variants.js`** - Product variant management ✅
- **`priceLists.js`** - Price list and price list customer operations ✅
- **`services.js`** - Service operations and management ✅
- **`salesOrders.js`** - Sales order operations and sales order rows ✅
- **`factory.js`** - Factory settings and inventory closing date operations ✅
- **`stockAdjustments.js`** - Stock adjustment creation and management ✅

#### Utility Layer (`src/tools/utils/`)

- **`apiHelpers.js`** - Common utilities implementing Katana API best practices:
  - **Rate Limiting:** Proper 60 requests/60 seconds handling with header monitoring ✅
  - **Error Handling:** Following Katana's error structure (statusCode, name, message, code, details) ✅
  - **Pagination:** Using X-Pagination headers with metadata support for efficient data retrieval ✅
  - **API Key Management:** Consistent validation and authentication across all modules ✅
  - **Retry Logic:** Automatic retry for 429 rate limit responses with exponential backoff ✅

#### Benefits

- **Consistency:** All API calls follow the same patterns and error handling
- **Maintainability:** Single source of truth for API operations eliminates code duplication
- **Performance:** Proper rate limiting and pagination optimization
- **Reliability:** Robust error handling and retry logic for network issues
- **Compliance:** Full adherence to Katana's documented API best practices

#### Usage Pattern

```javascript
// Import centralized API functions
import { fetchAllCustomers, createCustomer } from "../api/customers.js";
import { paginatedFetch, apiRequest } from "../utils/apiHelpers.js";

// Use with consistent error handling and rate limiting
const customers = await fetchAllCustomers(apiKey, {
  limit: 250,
  onProgress: (current, total) => updateProgress(current, total),
});
```

## Debug Panel

- A debug panel is available in the extension footer.
- All tools log errors, API call details, and important events to the debug panel for transparency and troubleshooting.
- You can clear the debug log or toggle its visibility at any time.

## Hash Tool: Why and How We Use It

### What is the Hash Tool?

The hash tool is used to detect changes in customer and supplier records when editing via spreadsheet. Each row in the edit file contains a hash value representing the current state of the record's fields. When you re-import the file, the extension compares the hash in the file to a freshly computed hash from your edits. If the hashes differ, the tool knows the record has changed and will update it in Katana.

### Why Use Hashes?

- **Efficiency:** Only changed records are updated, minimizing unnecessary API calls.
- **Accuracy:** Prevents accidental overwrites and ensures only intentional edits are processed.
- **Auditability:** You can see exactly which rows were updated, skipped, or errored in the results file.

### Example Workflow

#### Technical Example: How Hashes Are Computed

When you download an edit file, each row includes a hash column. This hash is generated by combining the relevant fields (such as name, email, address, etc.) into a single string, then passing that string through a hashing function. For example:

**Real World Example:**

Suppose you have a customer row in your spreadsheet:

| Name      | Email         | Phone    | Company   | Currency | ... | Hash       |
| --------- | ------------- | -------- | --------- | -------- | --- | ---------- |
| Acme Inc. | info@acme.com | 555-1234 | Acme Inc. | USD      | ... | 1234567890 |

The hash column is generated by joining all relevant fields together (e.g., `Acme Inc.|info@acme.com|555-1234|Acme Inc.|USD|...`) and then hashing that string. When you edit any field (such as changing the phone number), the hash will change. On import, the extension compares the hash in the file to a newly computed hash:

- If the hash is unchanged, the row is skipped (no update needed).
- If the hash is different, the row is updated in Katana and marked as "Edited" in the results.

## How to Use Edit Functionality (Customers & Suppliers)

1. **Download the Edit File:** Use the "Download Customer Data" or "Download Supplier Data" button to get the combined edit file.
2. **Edit Fields:** Open the file in Excel and make changes to any customer/supplier or address fields. Do not modify the hash columns unless you know what you're doing.
3. **Save and Import:** Save your changes and use the "Import Customers" or "Import Suppliers" button to re-import the file.
4. **Review Results:** The extension will process only changed rows, show a summary in the info box (with bold title and line breaks), and provide a "Download Results" link for the results file.
5. **No Auto-Download:** Results files are only downloaded when you click the link in the info box.

- A debug panel is available in the extension footer.
- All tools log errors, API call details, and important events to the debug panel for transparency and troubleshooting.
- You can clear the debug log or toggle its visibility at any time.

## Security

- The API key is never synced or shared outside your browser.
- All API requests are made directly from your browser to the Katana API using HTTPS.

## Usage Notes

- The extension only works when you are logged into https://factory.katanamrp.com.
- The side panel must be open to use the tools.
- If you encounter issues with tool loading or API key prompts, try refreshing the extension or re-entering your API key.
- The History info box is append-only: previous results are never overwritten, and the title always remains visible.
- All info box messages use bold titles and line breaks for clarity. Results files are only downloaded when you click the "Download Results" link in the info box.

## Future Tools

- The extension is modular and designed for easy addition of new tools based on Katana page URLs.
- All new tools will follow the same UI/UX patterns: dynamic loading, persistent panels, loading overlays, debug logging, and append-only History logging.
- For detailed development history and version information, see [CHANGELOG.md](CHANGELOG.md).

---

For support or feature requests, please contact the extension author or open an issue in the repository.
