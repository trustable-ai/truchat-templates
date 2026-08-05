# 1. Transform the Chat into a Modern AI Email Manager

Transform the existing chat application into a complete AI-powered email management platform while preserving the conversational experience.

Use:

- React
- Tailwind CSS
- TypeScript
- Lucide React icons
- Framer Motion animations
- Responsive design (desktop, tablet, mobile)
- Accessible UI (keyboard navigation, ARIA labels)

The application must feel like a modern productivity tool, similar to Linear, Notion, Gmail, and Superhuman.

Create a clean interface composed of:

- Left sidebar
  - Inbox
  - Starred
  - Sent
  - Drafts
  - Spam
  - Trash
  - Labels
- Main email list
- AI chat panel
- Top navigation bar
- Floating compose button
- Notification system
- Command palette (Ctrl+K)

The AI chat must become the primary interaction method for email management.

The assistant should understand commands like:

- summarize today's emails
- unread emails
- archive this
- reply politely
- write a professional answer
- delete spam
- mark as unread
- search invoices
- find emails from John
- show attachments
- draft a follow-up

Every AI action must also be available through visible graphical controls.

Include:

- contextual action buttons
- dropdown menus
- right-click context menus
- bulk selection toolbar
- drag & drop
- keyboard shortcuts
- animated loading states
- empty states
- skeleton loaders

Use Tailwind throughout the project and ensure the interface is fully responsive from the beginning.

---

# 2. Add Temporary Google OAuth Email Integration

Integrate a temporary Google OAuth login as the ONLY authentication method.

Use OAuth 2.0 with Google Sign-In.

Requirements:

- Temporary authentication only
- No local username/password
- Easy replacement later with another provider
- Keep authentication isolated inside dedicated services

After login retrieve:

- user profile
- avatar
- email address

Then request Gmail API permissions to manage emails.

Create services for:

- Authentication
- Gmail API
- Token management
- Session management

After authentication load:

- Inbox
- Sent
- Drafts
- Trash
- Labels
- Attachments
- Threads

Display synchronization progress with animated progress indicators.

Provide visible UI for:

- Refresh mailbox
- Disconnect account
- Reconnect account
- Account information
- Last synchronization
- Active account

If the Gmail API is unavailable, show graceful fallback screens with retry options.

Never expose OAuth secrets inside the frontend.

Keep all API logic modular for future backend migration.

Everything must remain fully responsive using Tailwind CSS.

---

# 3. Build an AI-Driven Visual Email Workspace

Turn the application into an intelligent visual email workspace where every operation can be performed either by chatting with the AI or by interacting with graphical controls.

Design a polished modern UI featuring:

- responsive split layout
- collapsible sidebar
- resizable chat panel
- email preview panel
- conversation threads
- rich text compose window
- attachment previews
- drag & drop uploads
- search bar
- filters
- smart categories
- dark mode
- light mode
- smooth animations

Implement graphical actions for every email:

- Reply
- Reply All
- Forward
- Archive
- Delete
- Mark Read
- Mark Unread
- Star
- Move
- Label
- Download attachments
- Copy email
- Pin conversation

The AI assistant should be capable of:

- summarizing long conversations
- generating replies
- rewriting emails
- translating emails
- changing tone
- extracting action items
- extracting deadlines
- creating follow-up drafts
- finding important messages
- organizing emails by priority

The interface should continuously synchronize graphical interactions with the chat so that actions performed in one are immediately reflected in the other.

Include polished UX details:

- toast notifications
- confirmation dialogs
- loading overlays
- undo actions
- skeleton loading
- optimistic UI updates
- keyboard shortcuts
- responsive mobile navigation
- touch-friendly interactions
- smooth transitions
- modern cards
- rounded corners
- subtle shadows
- glassmorphism where appropriate

Use Tailwind CSS for every component and build the application mobile-first, ensuring an excellent experience on desktop, tablet, and smartphones.
