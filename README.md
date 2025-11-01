# Claude Instructions - Version Control Repository

Versioned repository for Claude AI instruction files and configuration.

## Purpose

This repository maintains a version history of Claude AI configuration and instruction files, allowing us to:
- Track changes to AI behavior and instructions over time
- Roll back to previous versions if needed
- Document the evolution of our Claude setup
- Share configurations across projects and team members

## Repository Structure

```
Claude-Instructions/
├── README.md                    # This file
├── CHANGELOG.md                 # Version history and changes
├── current/                     # Latest version (always updated)
│   ├── CLAUDE.md               # Main instruction file
│   ├── docs/                   # Supporting documentation
│   └── .claude/                # Configuration files
└── versions/                    # Historical versions
    ├── v1.0.0/                 # Initial version
    ├── v1.1.0/                 # Feature additions
    └── v1.2.0/                 # Latest updates
```

## Versioning System

We use **Semantic Versioning** (MAJOR.MINOR.PATCH):

- **MAJOR** (v1.0.0 → v2.0.0): Significant overhauls, breaking changes
- **MINOR** (v1.0.0 → v1.1.0): New features, capabilities, or sections added
- **PATCH** (v1.0.0 → v1.0.1): Bug fixes, clarifications, minor corrections

## Version History

### v1.0.0 - October 31, 2025
**Initial Release - Productivity Platform Intelligence**

Added:
- Complete Google Workspace API capabilities (11 APIs)
- Microsoft 365 MCP tool documentation (30 tools)
- Productivity Platform Intelligence section
- Auto-suggestion protocol for tool selection
- Platform selection decision trees
- Comprehensive workflow documentation

Features:
- Gmail, Drive, Docs, Sheets, Slides, Calendar, Forms integration
- Cloud Vision, Vertex AI, BigQuery, Cloud Storage
- Office 365 Email, Teams, Planner, OneDrive, SharePoint
- Smart suggestions based on context
- No unnecessary questions protocol

## How to Use

### For Claude AI
Reference the latest instructions from the `current/` directory:
```
Use instructions from: Claude-Instructions/current/CLAUDE.md
```

### For Version Control
When making updates to Claude instructions:

1. **Make changes** to `current/CLAUDE.md`
2. **Test the changes** with Claude
3. **Determine version bump** (MAJOR, MINOR, or PATCH)
4. **Create new version**:
   ```bash
   # Copy current to new version
   cp -r current versions/v1.1.0

   # Update CHANGELOG.md with changes
   # Commit and push
   git add .
   git commit -m "Release v1.1.0: [description]"
   git tag v1.1.0
   git push origin main --tags
   ```

### For Rollback
To revert to a previous version:
```bash
# Copy old version to current
cp -r versions/v1.0.0/* current/

# Commit the rollback
git add current/
git commit -m "Rollback to v1.0.0: [reason]"
git push
```

## File Organization

### current/CLAUDE.md
The main instruction file that Claude reads. Contains:
- System identity and purpose
- Tool configurations (Google, Microsoft, APIs)
- Workflow protocols
- Auto-suggestion rules
- Platform selection guidelines

### current/docs/
Supporting documentation referenced by CLAUDE.md:
- `PRODUCTIVITY_PLATFORM_WORKFLOWS.md` - Detailed workflow guide
- `BLENDER_AND_3D_TOOLS.md` - 3D modeling documentation
- Other specialized guides

### current/.claude/
Configuration files:
- `mcp_settings.json` - MCP server configuration
- `system-inventory.json` - Available tools and services

## Update Process

**When to create a new version:**

- **Daily tweaks/fixes** → Update `current/` directly, no version bump
- **Weekly improvements** → PATCH version (v1.0.1)
- **New features/tools** → MINOR version (v1.1.0)
- **Major restructuring** → MAJOR version (v2.0.0)

**Best practices:**
- Always update CHANGELOG.md
- Test changes before versioning
- Tag releases in git
- Document breaking changes clearly

## Integration with Projects

Link this repository in project READMEs:
```markdown
**Claude Instructions**: See [Claude-Instructions](https://github.com/charlesmartinedd/Claude-Instructions) for AI configuration
```

## License

Private repository for Alexandria's Design internal use.

---

**Last Updated**: October 31, 2025
**Current Version**: v1.0.0
**Maintainer**: Charles Martin (charlesmartinedd@gmail.com)
