# Changelog

All notable changes to the Katana Master Extension will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
- **Console logging cleanup** for production-ready output while maintaining debugging
- **Material import bugs** including "Invalid product id" errors
- **API endpoint detection** for proper material and product handling

### Security
- **Local-only data storage** with AES-GCM encryption and no external transmission
- **Comprehensive hash-based change detection** preventing unnecessary API calls
- **Result cleanup patterns** to prevent data persistence across page navigation
- **Secure API key management** with session-based encryption
- **Privacy-focused architecture** with no analytics or tracking

---

## Release Notes

### Version 1.0.0 - Initial Chrome Web Store Release 🎉

**Release Date:** September 30, 2025  
**Status:** READY FOR PUBLICATION  
**Chrome Web Store:** Under review for host permissions  

### Version 1.0.0 Features

**Core Tools:**
1. Price List Customer Template & Import Tool
2. Service Item Open Orders Tool
3. Customer Data Management (with edit functionality)
4. Supplier Data Management (with edit functionality)
5. Data Table Component
6. Custom Field Tools (unified)
7. Service Items Management Tool
8. Keyboard Shortcuts Tool
9. Tool Visibility Management
10. Multiple Email Tool (Purchase Orders)

**API Architecture:**
- Centralized API layer with 9 comprehensive modules
- Rate limiting with proper 60 requests/60 seconds handling
- Error handling following Katana's official error structure
- Pagination with X-Pagination header metadata support
- Retry logic for 429 rate limit responses

**Security & Privacy:**
- Local API key encryption using AES-GCM
- No external data transmission
- Secure local storage only
- Full user control over data

**User Experience:**
- Real-time progress tracking
- Persistent Memory info box
- Collapsible tool management interface
- Keyboard shortcuts for productivity
- Comprehensive error handling and debugging

---

## Versioning Strategy

Starting with **v1.0.0**, this project follows [Semantic Versioning](https://semver.org/):

- **MAJOR** (x.0.0): Breaking changes, major new features, or architectural updates
- **MINOR** (1.x.0): New features, tools, or significant enhancements (backward compatible)
- **PATCH** (1.0.x): Bug fixes, security updates, or minor improvements (backward compatible)

### Version History Tracking
All changes will be documented in this changelog with:
- Clear categorization (Added/Changed/Fixed/Security/Removed)
- Release dates and version numbers
- Impact assessment and upgrade notes when applicable
- Chrome Web Store submission status

### Release Process
1. Update CHANGELOG.md with new version
2. Update manifest.json version number
3. Test all functionality comprehensively  
4. Submit to Chrome Web Store
5. Create GitHub release tag
6. Monitor for user feedback and issues