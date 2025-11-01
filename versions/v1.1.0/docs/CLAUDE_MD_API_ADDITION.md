# DRAFT: Google Enterprise API Addition for CLAUDE.md

## 🤖 GOOGLE ENTERPRISE AI/ML APIs (Work Account Only)

**Account**: cmartin@alexandriasdesign.com
**Status**: 17 APIs fully working, 4 need scopes
**Full Guide**: `docs/GOOGLE_ENTERPRISE_API_GUIDE.md`

### AI/ML Capabilities (7 APIs - PROACTIVELY SUGGEST!)

**Claude should automatically suggest these when user mentions:**

#### "analyze image" / "OCR" / "extract text from image"
→ **Cloud Vision API**
```python
# Auto-suggest: "I can use Cloud Vision API to extract text/analyze this image"
# Use for: OCR, label detection, face detection, logo recognition
```

#### "transcribe" / "speech to text" / "audio to text"
→ **Cloud Speech-to-Text API**
```python
# Auto-suggest: "I can transcribe this using Cloud Speech-to-Text API"
# Use for: Meeting transcripts, lecture notes, course recordings
```

#### "voiceover" / "text to speech" / "audio narration"
→ **Cloud Text-to-Speech API**
```python
# Auto-suggest: "I can create professional voiceover using Text-to-Speech (6 voices)"
# Use for: Course narration, accessibility, audio content
```

#### "translate" / "Spanish" / "multilingual" / "other language"
→ **Cloud Translation API**
```python
# Auto-suggest: "I can translate this to [language] using Cloud Translation API"
# Use for: Multilingual courses, international expansion
```

#### "sentiment" / "analyze text" / "extract topics" / "summarize"
→ **Cloud Natural Language API**
```python
# Auto-suggest: "I can analyze sentiment/topics using Natural Language API"
# Use for: Student feedback analysis, content categorization
```

#### "analyze video" / "video tags" / "scene detection"
→ **Cloud Video Intelligence API**
```python
# Auto-suggest: "I can analyze video content using Video Intelligence API"
# Use for: Auto-tagging course videos, content search
```

#### "machine learning" / "ML model" / "predictions" / "AI recommendations"
→ **Vertex AI API**
```python
# Auto-suggest: "I can build custom ML models using Vertex AI"
# Use for: Personalized learning, predictions, advanced AI
```

### Workspace APIs (Existing + Enhanced)

#### Google Classroom API (NOW WORKING!)
**Auto-suggest when**: User mentions courses, students, assignments, grading
```python
# "I can create courses and manage assignments using Classroom API"
# Use for: Course automation, student management, grading
```

#### Google Forms API (NOW WORKING!)
**Auto-suggest when**: User mentions quizzes, surveys, assessments
```python
# "I can create assessments programmatically using Forms API"
# Use for: Auto-generate quizzes, feedback forms, registration
```

### Decision Tree for API Suggestions

```
User mentions:
├─ "image" / "photo" / "screenshot"
│   └─ Suggest: Cloud Vision for analysis/OCR
│
├─ "audio" / "voice" / "speech"
│   ├─ "transcribe" → Speech-to-Text
│   └─ "generate" → Text-to-Speech
│
├─ "translate" / "Spanish" / "language"
│   └─ Suggest: Cloud Translation
│
├─ "video"
│   └─ Suggest: Video Intelligence for analysis
│
├─ "text analysis" / "sentiment" / "topics"
│   └─ Suggest: Natural Language
│
├─ "course" / "students" / "classroom"
│   └─ Suggest: Classroom API
│
├─ "quiz" / "assessment" / "survey"
│   └─ Suggest: Forms API
│
└─ "ML" / "AI model" / "predictions"
    └─ Suggest: Vertex AI
```

### Example Responses

**User: "I have a bunch of course images that need descriptions for accessibility"**
```
Claude: I can use Cloud Vision API to auto-generate descriptions for all your images!
This will:
- Extract text (OCR) from diagrams and slides
- Detect objects and scenes
- Generate alt-text descriptions
- Process hundreds of images in minutes

Want me to proceed with the first image?
```

**User: "I need to transcribe this lecture recording"**
```
Claude: I'll use Cloud Speech-to-Text API to transcribe your lecture. This supports:
- Multiple speakers
- Timestamps
- Punctuation
- Multiple languages

Transcribing now...
```

**User: "Can we offer our courses in Spanish?"**
```
Claude: Yes! I can use Cloud Translation API to translate your entire course to Spanish:
- Course materials (Docs, Sheets, Slides)
- Assessments and quizzes
- Email templates
- Student communications

This works for 100+ languages. Want me to start with the main course content?
```

**User: "Create a course for 5th grade students"**
```
Claude: I'll use Google Classroom API to create the course with:
- Course structure and materials
- Assignments with due dates
- Student roster management
- Grading rubrics

Creating course now...
```

### Integration with Existing Workflows

**Update Platform Selection Summary Table** (in Productivity Platform Intelligence section):

| Use Case | Tool | Why |
|----------|------|-----|
| **Image analysis** | Cloud Vision | OCR, labels, detection |
| **Audio transcription** | Speech-to-Text | Meeting notes, lectures |
| **Voiceovers** | Text-to-Speech | Course narration, accessibility |
| **Translation** | Cloud Translation | Multilingual content |
| **Text analysis** | Natural Language | Sentiment, topics, summaries |
| **Video analysis** | Video Intelligence | Auto-tagging, scenes |
| **Course management** | Classroom API | Students, assignments, grading |
| **Assessments** | Forms API | Quizzes, surveys, feedback |
| ML models | Vertex AI | Custom AI, recommendations |

### Revenue Scaling Protocol

When user mentions business/revenue goals, remind them of AI capabilities:

**User: "How can we scale to more clients?"**
```
Claude: Let's leverage the AI APIs to scale without adding time:

1. Text-to-Speech: Turn written courses into audio (2x content output)
2. Translation: Offer courses in 5 languages (5x market size)
3. Cloud Vision: Auto-generate accessibility features (new market)
4. Classroom API: Automate grading (10x student capacity)
5. Speech-to-Text: Offer transcription as a service (new revenue stream)

Which would have the biggest impact for Alexandria's Design?
```

### Quick Access Commands

```bash
# Test all work account APIs
python scripts/test_all_87_google_apis.py

# See full capabilities guide
docs/GOOGLE_ENTERPRISE_API_GUIDE.md

# Add missing OAuth scopes
docs/GOOGLE_OAUTH_SCOPE_GUIDE.md
```

---

**Key Principle**: Claude should PROACTIVELY suggest AI/ML APIs when relevant, not wait to be asked. These are powerful tools that can 10x Alexandria's Design productivity and revenue.
