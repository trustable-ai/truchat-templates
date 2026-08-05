# 1 - Document Management Chat

IMPORTANT: Keep the application fully responsive and use Tailwind CSS.

Transform this chat into an AI assistant specialized in document management.

The goal is to create a chat-based workspace that allows users to:

- upload, analyze, and organize documents;
- read content from PDF, DOCX, TXT, and Markdown files;
- extract important information;
- create summaries, structures, checklists, and operational notes;
- compare different versions of the same document;
- assist with writing and editing content while maintaining context.

Design the interaction as a document notebook:

- each document must have its own isolated context;
- store metadata such as title, date, version, category, and status;
- always show which documents are available in the current session;
- allow users to request specific actions on documents using natural language.

Create an initial structure with:

- Document Library
- Recent Documents
- Active Document
- Document Actions

The chat should behave as an intelligent document workspace, not as a simple conversation.

---

# 2 - Document Analysis Workspace

Evolve the previous chat into an advanced document analysis environment.

Add features for:

- automatically analyzing document content;
- recognizing document type, topic, and structure;
- extracting titles, sections, people, dates, numbers, and key information;
- generating a document map;
- creating short, medium, and detailed summaries;
- highlighting issues, missing information, and inconsistent sections.

Each document should be displayed with:

- general information;
- section index;
- main content;
- AI-generated notes;
- suggested questions for deeper analysis.

Implement a contextual conversation system where the user can write:

"analyze this document"

"find differences with the previous version"

"create a report"

"extract the tasks to complete"

and the chat should automatically understand which document should be used.

---

# 3 - Intelligent Document Assistant

Transform the system into a complete AI assistant for the entire document lifecycle.

Add:

- creation of new documents through chat;
- collaborative content editing;
- version management;
- revision comparison;
- document approval workflow and status tracking;
- automatic categorization;
- semantic search across documents;
- connections between related documents.

Create an experience similar to an AI notebook where each document can become an independent project.

The chat must support workflows such as:

1. Import document
2. Analyze content
3. Extract information
4. Generate improvements
5. Create a new version
6. Archive or publish

Design the interface and logic as a professional system for companies, teams, and personal knowledge management.

---

# 4 - Document Management Interface Design

Transform the document chat into a complete graphical application for document management with a modern AI Workspace interface.

Create a complete UI composed of:

## Main Layout

Build a three-column structure:

---

## Left Sidebar - Document Library

Create a document library with:

- list of all available documents;
- intelligent search;
- filters by:
  - document type;
  - category;
  - modification date;
  - status;
  - tags;
- folders and custom collections;
- "New Document" button;
- "Upload Document" button.

Each document must be displayed as a card containing:

- file format icon (PDF, DOCX, TXT, MD);
- title;
- last modification date;
- author;
- tags;
- status (Draft, Review, Published);
- action menu:
  - Open;
  - Rename;
  - Duplicate;
  - Compare version;
  - Archive.

---

## Center Area - Document Workspace

Create a main area where the selected document is displayed.

The screen must contain:

Document Header:

- editable title;
- current version;
- status;
- share button;
- export button;
- create new version button.

Content area:

- document viewer;
- Markdown/WYSIWYG editor;
- expandable sections;
- change highlighting;
- comments and annotations.

Add an "AI Notebook" mode:

- content blocks;
- AI analysis blocks;
- generated notes;
- suggested questions;
- processing results.

---

## Right Sidebar - AI Assistant

Create a chat panel connected to the opened document.

The chat must display:

- active document context;
- conversation history;
- quick suggestions.

Buttons:

- Summarize Document
- Extract Information
- Find Issues
- Create Checklist
- Generate Report
- Improve Text
- Compare Versions

The assistant must always know which document is open and work only on that document.

---

# 5 - Document Dashboard

Add an initial home dashboard with an overview.

## Statistics Cards

Include:

- Total Documents
- Recent Documents
- Documents Under Review
- Documents Created This Week

## Recent Documents Section

Display recently opened documents with:

- preview;
- title;
- type;
- latest activity.

## Quick Actions Section

Create large action buttons:

+ New Document

+ Upload File

+ Import From Cloud

+ Create Template

+ Search Documents

---

# 6 - Design System

Use a modern design style:

- dark/light mode support;
- rounded cards;
- collapsible sidebars;
- smooth animations;
- drag & drop document management;
- minimal icons;
- responsive layout for desktop/tablet/mobile.

Design inspiration:

- Notion for content management;
- Google Drive for document libraries;
- Obsidian for connections and knowledge graphs;
- ChatGPT Canvas for AI interaction.

The final result should look like a professional SaaS product for intelligent knowledge and document management.
