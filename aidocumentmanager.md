# Document Manager

# 1 - Document Management Workspace Foundation

IMPORTANT: Keep the application fully responsive and use Tailwind CSS.

Transform the existing chat application into a modern AI-powered Document Management Workspace.

Use:

- React
- TypeScript
- Tailwind CSS
- shadcn/ui
- Framer Motion
- Lucide React

Do not create a traditional chatbot.

Create the application structure:

## Main Layout

Desktop:

- Left sidebar
- Main workspace
- Right AI assistant panel

Mobile:

- Responsive drawer navigation
- Bottom sheets
- Collapsible panels

Create:

## Left Sidebar

Document Library containing:

- Search bar
- Recent Documents
- Categories
- Tags
- Upload button
- New Document button

## Main Workspace

Create an empty document area with:

- Empty state
- Selected document placeholder
- Document information header

## Right Panel

Create AI Assistant panel with:

- Context indicator
- Quick action buttons
- Prompt input

Use:

- rounded cards
- glassmorphism
- animations
- skeleton loading
- responsive design

### Test checklist

Verify:

- Layout works on desktop and mobile
- Sidebar opens/closes
- Panels resize correctly
- Empty states are displayed
- No classic chat bubbles exist

---

# 2 - Document Library and File Management

Implement the document management system.

Create a document model containing:

- id
- title
- type
- size
- author
- creation date
- modification date
- version
- category
- tags
- status

Support document types:

- PDF
- DOCX
- TXT
- Markdown

Build the Document Library interface.

Each document must appear as a card with:

- file icon
- title
- metadata
- tags
- status badge
- actions menu

Actions:

- Open
- Rename
- Duplicate
- Archive
- Delete

Add:

- Search
- Filtering
- Sorting
- Categories
- Collections

Use mock documents initially.

### Test checklist

Verify:

- Documents appear in the library
- Search filters documents
- Categories work
- Opening a document updates the workspace
- Actions modify document state

---

# 3 - Document Viewer and AI Notebook Workspace

Create the document workspace.

When a document is selected display:

## Document Header

Include:

- Editable title
- Version
- Status
- Author
- Export button
- Create new version button

## Content Area

Create a document viewer/editor supporting:

- Markdown rendering
- Editable text blocks
- Sections
- Headings
- Notes
- Comments
- Highlighted changes

Add AI Notebook mode.

The workspace should contain blocks:

- Document Content Block
- AI Summary Block
- Notes Block
- Extracted Information Block
- Suggested Questions Block

The AI should modify blocks instead of sending chat messages.

### Test checklist

Verify:

- Selecting a document opens its workspace
- Editing text updates the document
- AI blocks render correctly
- Sections expand/collapse

---

# 4 - AI Document Analysis Engine Interface

Transform the AI assistant into a contextual document analysis tool.

The AI panel must work only with the currently opened document.

Add quick actions:

- Summarize Document
- Extract Information
- Find Issues
- Generate Checklist
- Create Report
- Improve Text
- Compare Versions

Each action must generate visual results.

Examples:

## Summarize Document

Generate summary cards:

- Main topic
- Key points
- Important sections


## Extract Information

Generate information dashboard:

- People
- Dates
- Numbers
- Entities
- Tasks


## Find Issues

Generate review panel:

- Missing information
- Inconsistencies
- Suggestions


## Create Checklist

Generate interactive checklist cards.

Do not display long AI messages.

### Test checklist

Verify:

- Buttons generate different visual components
- AI always references the selected document
- Results appear inside workspace cards

---

# 5 - Document Intelligence and Workflow System

Add advanced document lifecycle features.

Implement:

## Version Management

Allow:

- Create version
- Compare versions
- Restore previous version

Create visual comparison:

- Added sections
- Removed sections
- Modified paragraphs


## Document Workflow

Add statuses:

- Draft
- Review
- Approved
- Published
- Archived

Create workflow timeline:

- Created
- Modified
- Sent for review
- Approved


## Semantic Search

Create intelligent search interface.

Search documents by:

- keywords
- concepts
- related content

Display:

- matching documents
- similarity score
- related documents


## Document Connections

Create relationship visualization:

- linked documents
- references
- related topics

### Test checklist

Verify:

- Versions can be created
- Differences are displayed
- Status changes update UI
- Search finds related documents
- Connections appear visually

---

# 6 - Final Document Management SaaS Interface

Create the final professional SaaS experience.

Add:

# Dashboard Home

Create:

## Statistics Cards

Include:

- Total Documents
- Recent Documents
- Documents Under Review
- Documents Created This Week


## Recent Documents

Display:

- Preview
- Title
- Type
- Last Activity


## Quick Actions

Large buttons:

- New Document
- Upload File
- Import Cloud Document
- Create Template
- Search Documents


# Final Design System

Apply:

- Dark/light mode
- Premium spacing
- Smooth Framer Motion animations
- Drag and drop upload
- Responsive layouts
- Floating panels
- Beautiful empty states
- Loading skeletons
- Hover animations


Design inspiration:

- Notion
- Google Drive
- Obsidian
- ChatGPT Canvas
- Linear
- Vercel


Final requirements:

- No traditional chatbot interface
- AI works through document actions
- Every result is visual
- Documents are the center of the experience
- Fully responsive
- Production-quality SaaS interface


### Final acceptance checklist

- Upload flow works
- Document library works
- Document viewer works
- AI analysis works
- Version system works
- Search works
- Dashboard works
- Mobile experience works
- UI feels like a commercial product
