# Productivity Platform Workflows - Google Workspace & Microsoft 365

## Quick Reference: What's Available

### Google Workspace (11 Working APIs via Python)
✅ **Gmail** • **Drive** • **Docs** • **Sheets** • **Slides** • **Calendar** • **Forms**
✅ **Cloud Vision** • **Vertex AI** • **BigQuery** • **Cloud Storage**

### Microsoft 365 (30 MCP Tools - Instant Access)
✅ **Email** • **Teams** • **Calendar** • **Planner** • **OneDrive/SharePoint** • **Contacts** • **Search**

---

## Access Methods

### Google Services
**Method**: Python scripts with Google API
**Location**: `scripts/` directory
**Authentication**: OAuth tokens in `C:\Users\MarieLexisDad\Old Files\google-workspace-mcp\token-personal.json`
**Account**: charlesmartinedd@gmail.com (default)

**Quick Actions**:
```bash
# Send email
python scripts/send_simple_email.py

# Create Google Doc
python scripts/create_google_doc.py

# Audit Drive
python scripts/audit_google_drive.py
```

### Microsoft Services
**Method**: MCP tools (instant, no scripts needed)
**Authentication**: OAuth tokens in `C:\Users\MarieLexisDad\.office-mcp-tokens.json`
**Access**: Direct MCP tool calls (e.g., `mcp__office-365-mcp__email`)

---

## Workflow Suggestions Guide

### When User Wants: Email Operations

**Google Gmail (Python)**:
```python
# Use when: User specifies Gmail or personal account
python scripts/send_simple_email.py
# Edit script with: recipient, subject, body
# Sent from: charlesmartinedd@gmail.com
```

**Microsoft Outlook (MCP)**:
```javascript
// Use when: User wants enterprise features, rules, or Office 365
mcp__office-365-mcp__email({
  operation: "send",
  to: ["recipient@example.com"],
  subject: "Subject",
  body: "HTML content"
})

// Advanced search with KQL
mcp__office-365-mcp__email_search({
  query: "from:john@example.com AND subject:report",
  startDate: "7d",  // Last 7 days
  maxResults: 50
})
```

**Claude Should Suggest**:
- Gmail: Simple personal emails, quick sending
- Outlook: Business emails, advanced filtering, email rules, focused inbox

---

### When User Wants: Document Creation

**Google Docs (Python)**:
```python
# Use when: Real-time collaboration, simple docs, easy sharing
from scripts.create_google_doc import create_google_doc

doc = create_google_doc(
    title="Project Proposal",
    content_paragraphs=[
        "Introduction paragraph here...",
        "Main content here...",
        "Conclusion here..."
    ]
)
# Returns: Document ID and shareable URL
```

**Google Sheets (Python)**:
```python
# Use when: Simple data, quick sharing, collaborative spreadsheets
from googleapiclient.discovery import build

service = build('sheets', 'v4', credentials=creds)
spreadsheet = service.spreadsheets().create(body={
    'properties': {'title': 'Sales Data 2025'}
}).execute()
```

**Microsoft Word/Excel (MCP)**:
```javascript
// Use when: Complex formatting, enterprise features, version control
mcp__office-365-mcp__files({
  operation: "upload",
  fileName: "Proposal.docx",
  content: "...",  // File content
  parentId: "folder-id"  // OneDrive/SharePoint folder
})
```

**Claude Should Suggest**:
- **Google Docs**: Quick collaborative documents, easy public sharing, simple formatting
- **Google Sheets**: Simple data analysis, collaborative spreadsheets, quick charts
- **Microsoft Word**: Professional documents, complex formatting, templates
- **Microsoft Excel**: Advanced data analysis, Power Query, complex formulas

---

### When User Wants: Presentations

**Google Slides (Python)**:
```python
# Use when: Quick presentations, easy sharing, web-first
from googleapiclient.discovery import build

service = build('slides', 'v1', credentials=creds)
presentation = service.presentations().create(body={
    'title': 'Q4 Strategy Review'
}).execute()
```

**Microsoft PowerPoint (MCP)**:
```javascript
// Use when: Professional presentations, advanced design, animations
mcp__office-365-mcp__files({
  operation: "upload",
  fileName: "Strategy.pptx",
  content: "...",
  parentId: "folder-id"
})
```

**Claude Should Suggest**:
- **Google Slides**: Quick creation, collaborative editing, web sharing
- **PowerPoint**: Professional design, advanced animations, corporate presentations

---

### When User Wants: Task/Project Management

**Google Calendar (Python)**:
```python
# Use when: Simple scheduling, personal tasks
from googleapiclient.discovery import build

service = build('calendar', 'v3', credentials=creds)
event = service.events().insert(
    calendarId='primary',
    body={
        'summary': 'Team Meeting',
        'start': {'dateTime': '2025-11-01T10:00:00-07:00'},
        'end': {'dateTime': '2025-11-01T11:00:00-07:00'}
    }
).execute()
```

**Microsoft Planner (MCP)**:
```javascript
// Use when: Team project management, visual boards, task tracking
// Create plan
mcp__office-365-mcp__planner_plan({
  operation: "create",
  groupId: "team-group-id",
  title: "Website Redesign Project"
})

// Create task
mcp__office-365-mcp__planner_task({
  operation: "create",
  planId: "plan-id",
  title: "Design homepage mockup",
  assignedTo: "user-id",
  dueDateTime: "2025-11-15T17:00:00Z",
  bucketId: "design-bucket-id"
})
```

**Claude Should Suggest**:
- **Google Calendar**: Personal scheduling, simple events, quick meetings
- **Microsoft Planner**: Team projects, visual task boards, collaborative workflows

---

### When User Wants: File Storage & Sharing

**Google Drive (Python)**:
```python
# Use when: Easy public sharing, unlimited storage, cross-platform
from googleapiclient.discovery import build

service = build('drive', 'v3', credentials=creds)

# List files
results = service.files().list(
    pageSize=10,
    fields="files(id, name, mimeType, webViewLink)"
).execute()

# Share file publicly
service.permissions().create(
    fileId='file-id',
    body={'type': 'anyone', 'role': 'reader'}
).execute()
```

**Microsoft OneDrive/SharePoint (MCP)**:
```javascript
// Use when: Enterprise security, version control, permissions
mcp__office-365-mcp__files({
  operation: "upload",
  fileName: "Contract.pdf",
  content: base64Content,
  parentId: "sharepoint-folder-id"
})

// Advanced search
mcp__office-365-mcp__files({
  operation: "search",
  query: "contract approval",
  fileTypes: ["pdf", "docx"]
})
```

**Claude Should Suggest**:
- **Google Drive**: Quick sharing, public links, mobile access, unlimited storage
- **OneDrive/SharePoint**: Enterprise security, compliance, detailed permissions, version history

---

### When User Wants: Team Communication

**Google Meet (via Calendar)**:
```python
# Use when: Quick video calls, simple scheduling
event = service.events().insert(
    calendarId='primary',
    body={
        'summary': 'Project Review',
        'conferenceData': {
            'createRequest': {'requestId': 'random-string'}
        }
    },
    conferenceDataVersion=1
).execute()
```

**Microsoft Teams (MCP)**:
```javascript
// Use when: Full collaboration platform, persistent chat, recordings
// Create Teams meeting
mcp__office-365-mcp__teams_meeting({
  operation: "create",
  subject: "Weekly Standup",
  startDateTime: "2025-11-01T10:00:00Z",
  endDateTime: "2025-11-01T10:30:00Z",
  attendees: ["user1@example.com", "user2@example.com"]
})

// Get meeting transcript
mcp__office-365-mcp__teams_meeting({
  operation: "list_transcripts",
  meetingId: "meeting-id"
})

// Team channel communication
mcp__office-365-mcp__teams_channel({
  operation: "create_message",
  teamId: "team-id",
  channelId: "channel-id",
  message: "Project update: Phase 1 complete!"
})
```

**Claude Should Suggest**:
- **Google Meet**: Quick calls, simple scheduling, no accounts needed for guests
- **Microsoft Teams**: Full collaboration, persistent chat, meeting transcripts/recordings, channels

---

### When User Wants: AI/ML & Advanced Features

**Google Cloud AI (Python)**:
```python
# Use when: Image analysis, document processing, AI features
from googleapiclient.discovery import build

# Cloud Vision - Image analysis
vision = build('vision', 'v1', credentials=creds)
# Analyze images, OCR, label detection

# Vertex AI - ML models
vertex = build('aiplatform', 'v1', credentials=creds)
# Train models, predictions, AutoML

# BigQuery - Data analytics
bigquery = build('bigquery', 'v2', credentials=creds)
# SQL queries on massive datasets
```

**Claude Should Suggest**:
- **Cloud Vision**: Image analysis, OCR, label detection, face detection
- **Vertex AI**: Custom ML models, AutoML, predictions
- **BigQuery**: Massive dataset analytics, SQL queries, data warehousing

---

### When User Wants: Contact Management

**Google Contacts (Python)**:
```python
# Note: Would need Google People API enabled
# Use when: Personal contacts, simple management
```

**Microsoft Contacts (MCP)**:
```javascript
// Use when: Professional contacts, CRM integration
mcp__office-365-mcp__contacts({
  operation: "create",
  givenName: "John",
  surname: "Smith",
  emailAddresses: ["john.smith@example.com"],
  companyName: "Acme Corp",
  jobTitle: "Senior Developer",
  businessPhones: ["+1-555-0100"]
})

// Search contacts
mcp__office-365-mcp__contacts({
  operation: "search",
  query: "john smith acme"
})
```

**Claude Should Suggest**:
- **Microsoft Contacts**: Business contacts, detailed info, CRM-style management

---

## Automated Workflow Suggestions

### Claude Should Proactively Suggest:

#### Scenario: User mentions "send email"
**Claude's Response**:
> "I can send this email using:
> 1. **Gmail** (charlesmartinedd@gmail.com) - Personal/quick emails
> 2. **Outlook** (Microsoft 365) - Business/enterprise emails with advanced features
>
> Which would you prefer? (I'll default to Gmail unless you specify)"

#### Scenario: User wants "create a document"
**Claude's Response**:
> "I can create a document using:
> 1. **Google Docs** - Quick collaborative doc with easy sharing
> 2. **Microsoft Word** (OneDrive) - Professional document with advanced formatting
>
> For a [describe content], I recommend [Google Docs/Word] because [reason]."

#### Scenario: User needs "project management"
**Claude's Response**:
> "For project management, I recommend **Microsoft Planner** because it offers:
> - Visual kanban boards
> - Task assignments with notifications
> - Progress tracking
> - Team collaboration
>
> I can create a plan and tasks right now. What's the project name?"

#### Scenario: User wants "analyze this image"
**Claude's Response**:
> "I can analyze images using **Google Cloud Vision API**:
> - Text detection (OCR)
> - Object/label detection
> - Face detection
> - Logo recognition
>
> Would you like me to analyze the image at [path]?"

#### Scenario: User mentions "big dataset" or "analytics"
**Claude's Response**:
> "For large-scale data analytics, I recommend **Google BigQuery**:
> - SQL queries on massive datasets (terabytes+)
> - Fast parallel processing
> - Data warehousing
>
> Would you like me to help set up a BigQuery query?"

---

## Platform Selection Decision Tree

```
User Request
    │
    ├─ Email?
    │   ├─ Personal/Quick → Gmail (Python)
    │   └─ Business/Rules → Outlook (MCP)
    │
    ├─ Document?
    │   ├─ Collaborative/Simple → Google Docs (Python)
    │   └─ Professional/Complex → Word (MCP)
    │
    ├─ Spreadsheet?
    │   ├─ Simple data/Quick → Google Sheets (Python)
    │   └─ Advanced formulas/Power Query → Excel (MCP)
    │
    ├─ Presentation?
    │   ├─ Quick/Web-first → Google Slides (Python)
    │   └─ Professional design → PowerPoint (MCP)
    │
    ├─ Project Management?
    │   ├─ Simple tasks/Calendar → Google Calendar (Python)
    │   └─ Team projects/Visual → Planner (MCP)
    │
    ├─ Video Meeting?
    │   ├─ Quick call → Google Meet (Python)
    │   └─ Full collaboration/Recordings → Teams (MCP)
    │
    ├─ File Storage?
    │   ├─ Easy sharing/Public → Google Drive (Python)
    │   └─ Enterprise/Security → OneDrive/SharePoint (MCP)
    │
    ├─ AI/ML?
    │   ├─ Image analysis → Cloud Vision (Python)
    │   ├─ ML models → Vertex AI (Python)
    │   └─ Big data analytics → BigQuery (Python)
    │
    └─ Contact Management? → Microsoft Contacts (MCP)
```

---

## Quick Command Reference

### Google Services (Python Scripts)
```bash
# Email
python scripts/send_simple_email.py

# Create document
python scripts/create_google_doc.py

# Test all APIs
python scripts/test_all_google_apis.py

# Audit Drive
python scripts/audit_google_drive.py
```

### Microsoft Services (MCP Tools)
```javascript
// Email
mcp__office-365-mcp__email({operation: "send", to: [...], subject: "...", body: "..."})

// Search everything
mcp__office-365-mcp__search({query: "project proposal", entityTypes: ["driveItem", "message"]})

// Create task
mcp__office-365-mcp__planner_task({operation: "create", planId: "...", title: "..."})

// Teams meeting
mcp__office-365-mcp__teams_meeting({operation: "create", subject: "...", startDateTime: "..."})
```

---

## Integration Patterns

### Cross-Platform Workflows

**Example 1: Email with Drive attachment**
```python
# 1. Create document in Google Docs
doc = create_google_doc("Proposal", [...])

# 2. Send email via Gmail with link
send_email(
    subject="Project Proposal",
    body=f"Please review: {doc['url']}"
)
```

**Example 2: Planner task with Drive files**
```javascript
// 1. Upload file to Drive (Python)
// 2. Create Planner task with Drive link (MCP)
mcp__office-365-mcp__planner_task({
  operation: "create",
  title: "Review proposal",
  description: "Google Doc: [link]"
})
```

---

## Summary: When to Use What

| Task | Google Workspace | Microsoft 365 |
|------|------------------|---------------|
| **Quick Email** | ✅ Gmail (faster) | Outlook |
| **Business Email** | Gmail | ✅ Outlook (better) |
| **Simple Docs** | ✅ Docs (faster) | Word |
| **Complex Docs** | Docs | ✅ Word (better) |
| **Collaboration** | ✅ Google (real-time) | Microsoft |
| **Project Mgmt** | Calendar | ✅ Planner (better) |
| **Video Calls** | Meet | ✅ Teams (recordings) |
| **File Sharing** | ✅ Drive (easier) | OneDrive |
| **Enterprise** | Google | ✅ Microsoft (better) |
| **AI/ML** | ✅ Google Cloud | Limited |
| **Big Data** | ✅ BigQuery | Limited |

---

**Last Updated**: October 2025
**Test Results**: 11/14 Google APIs working, 30 Microsoft MCP tools active
