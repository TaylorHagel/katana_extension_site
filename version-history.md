---
layout: page
title: Changelog
permalink: /changelog/
---

# Changelog

All notable changes to the Katana Master Extension will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- Additional keyboard shortcuts beyond Insert key  
- New tools based on user feedback and Katana page requirements
- Advanced export/import capabilities
- Integration with additional Katana API endpoints

## [1.0.0] - 2025-09-30

### Added
- **🎉 INITIAL CHROME WEB STORE RELEASE** - Production-ready extension with comprehensive functionality
- **10 comprehensive tools** for Katana MRP workflow enhancement:
  1. Price List Customer Template & Import Tool
  2. Service Item Open Orders Tool  
  3. Customer Data Management (with edit functionality)
  4. Supplier Data Management (with edit functionality)
  5. Data Table Component
  6. Custom Field Tools (unified across Products, Materials, Inventory)
  7. Service Items Management Tool
  8. Keyboard Shortcuts Tool
  9. Tool Visibility Management System
  10. Multiple Email Tool (Purchase Orders)
- **Centralized API architecture** with 9 specialized modules eliminating code duplication
- **Progress tracking system** with real-time feedback replacing all loading wheels
- **Encrypted API key storage** with AES-GCM encryption and session-based security
- **Tool visibility management** with persistent settings and collapsible interface
- **Keyboard shortcuts system** with Insert key for "Add New Row" and Ctrl+Shift+K for admin panel
- **Data table component** with multi-format input, export capabilities, and optional editing
- **Service import/export** with hash-based change detection and dual create/update modes
- **Hash-based change detection** for efficient updates across customer, supplier, and service tools

### Changed
- **Consolidated custom field tools** from three separate tools into single unified interface
- **Migrated from loading wheels** to modern progress system with real-time feedback
- **Improved user interface** with collapsible tool management reducing complexity
- **Enhanced error handling** and debugging capabilities across all tools
- **Streamlined tool loading** with proper debouncing and visibility management

### Fixed
- **Individual fulfillment progress logging** in historical sales orders tool
- **Tool loading and duplication issues** with proper state management
- **Import path errors** across multiple tools for reliable module loading

## Key Features by Tool

### Customer Data Management
- **Download:** Export all customer data with proper formatting
- **Import:** Bulk customer creation from Excel templates
- **Edit:** Update existing customers with hash-based change detection
- **Validation:** Comprehensive data validation and error reporting

### Supplier Data Management  
- **Download:** Complete supplier export including contact information
- **Import:** Bulk supplier creation with template support
- **Edit:** Update supplier data with change detection
- **Multiple Emails:** Support for multiple email addresses per supplier (Purchase Order tool)

### Service Items Management
- **Export:** Download all service items with complete details
- **Import:** Create new service items from templates
- **Update:** Modify existing services with hash detection
- **Order Tracking:** View open orders for individual service items

### Custom Field Tools
- **Products Export:** Download products with custom field values
- **Materials Export:** Export materials including custom fields
- **Inventory Export:** Complete inventory data with custom fields
- **Bulk Editing:** Modify custom field values in bulk operations

### Multiple Email Tool (Purchase Orders)
- **Automatic Detection:** Identifies suppliers with multiple configured emails
- **Background Processing:** Runs automatically without user intervention
- **Error Handling:** Graceful processing of email validation errors
- **Multi-Recipient Support:** Sends to up to 3 email addresses per supplier

**⚠️ Important Notes:**
- Multiple emails may impact QuickBooks Online integration
- Suppliers with multiple emails show validation errors in Katana UI
- Future edits require Admin Panel or extension tools

### Tool Visibility Management
- **Page-Specific Controls:** Show/hide tools per page type
- **Persistent Settings:** Preferences saved across sessions
- **Collapsible Interface:** Reduces UI complexity when needed
- **Real-time Updates:** Changes apply immediately without refresh

### Keyboard Shortcuts
- **Insert Key:** Automatically clicks "Add New Row" buttons
- **Ctrl+Shift+K:** Opens Katana admin panel in new tab
- **Context Aware:** Only activates on appropriate pages
- **Configurable:** Enable/disable shortcuts as needed

## Technical Improvements

### API Architecture
- **Centralized System:** All API calls through unified system
- **Error Handling:** Consistent error processing across tools
- **Authentication:** Centralized API key management
- **Modularity:** Reusable API methods reduce code duplication

### Progress Tracking
- **Real-time Updates:** Live progress bars for all operations
- **Detailed Logging:** Comprehensive operation history
- **Error Reporting:** Clear error messages with solutions
- **Result Downloads:** Detailed result files for review

### Security Enhancements
- **Encrypted Storage:** AES-GCM encryption for API keys
- **Session-Based:** Keys cleared on browser close
- **Local Only:** No data transmitted to third parties
- **Direct API:** All requests go directly to Katana servers

---

**For detailed usage instructions, see the [User Guide]({{ site.baseurl }}/instructions/)**

**For technical details, see the [Technical Documentation]({{ site.baseurl }}/readme/)**