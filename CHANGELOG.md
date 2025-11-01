# Changelog

All notable changes to Claude AI instructions will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-10-31

### Added
- **Productivity Platform Intelligence section** - Comprehensive guide for auto-suggesting Google Workspace vs Microsoft 365 tools
- **Google Workspace API integration** (11 working APIs):
  - Gmail, Drive, Docs, Sheets, Slides, Calendar, Forms
  - Cloud Vision, Vertex AI, BigQuery, Cloud Storage
- **Microsoft 365 MCP tools** (30 tools):
  - Email, Teams (meetings/chat/channels), Calendar
  - Planner (8 specialized tools for project management)
  - OneDrive/SharePoint, Contacts, Search, Notifications
- **Auto-suggestion protocol** - Rules for Claude to proactively suggest best tools without asking unnecessary questions
- **Platform selection decision trees** - Clear guidelines for when to use which tool
- **Test scripts**:
  - `scripts/test_all_google_apis.py` - Tests all Google APIs
  - `scripts/test_office365_capabilities.py` - Lists Office 365 tools
  - `scripts/check_and_add_scopes.py` - OAuth scope checker
- **Email sending simplification** - Gmail as default, no permission needed
- **Comprehensive workflow documentation** - `docs/PRODUCTIVITY_PLATFORM_WORKFLOWS.md`

### Changed
- **Email Account Selection Protocol** - Simplified to use Gmail by default
- **Gmail Sending Protocol** - Direct script execution without asking permission
- **Tool selection approach** - From "ask first" to "suggest intelligently"

### Improved
- Clearer guidelines for when to use Google vs Microsoft tools
- Better integration examples between platforms
- More actionable decision trees for tool selection

## Guidelines for Future Versions

### MAJOR Version (x.0.0)
- Complete restructuring of instruction format
- Breaking changes to how Claude interprets instructions
- Major philosophical shifts in approach
- Removal of significant features

### MINOR Version (1.x.0)
- New tool integrations (new APIs, MCPs, services)
- New sections or capabilities
- Significant feature additions
- Enhanced workflows

### PATCH Version (1.0.x)
- Bug fixes in instructions
- Clarifications and corrections
- Small improvements
- Documentation updates

---

**Next planned changes**:
- [ ] Add Google Classroom and YouTube OAuth scopes
- [ ] Create helper scripts for common workflows
- [ ] Add more AI/ML workflow examples
- [ ] Document MCP server troubleshooting
