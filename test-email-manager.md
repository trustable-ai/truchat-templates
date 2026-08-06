# 1 - Transform the Chat into a Modern AI Email Manager Foundation

Transform the existing chat application into a modern AI-powered email management workspace.

IMPORTANT:
- Keep the application fully responsive using Tailwind CSS.
- Do not build only a chatbot.
- The AI chat is one interaction method inside a complete email productivity interface.

Use:

- React
- TypeScript
- Tailwind CSS
- shadcn/ui
- Lucide React icons
- Framer Motion animations

Create a professional productivity interface inspired by:

- Linear
- Notion
- Gmail
- Superhuman
- Vercel


## Application Layout

Create:

## Left Sidebar

Include:

- Inbox
- Starred
- Sent
- Drafts
- Spam
- Trash
- Labels

## Main Area

Create:

- Email list
- Search bar
- Filters
- Empty states
- Loading skeletons

## Right Panel

Create:

- AI Assistant panel
- Context information
- Suggested actions
- Prompt input


## Top Navigation

Include:

- Account area
- Notifications
- Search
- Command palette button (Ctrl+K)


## Floating Actions

Add:

- Compose button
- Quick actions


The interface must include:

- rounded cards
- premium spacing
- smooth animations
- responsive layouts
- hover states
- empty states


### Test checklist

Verify:

- Sidebar works
- Email list renders
- AI panel opens/closes
- Layout adapts to mobile
- Compose button works
- Command palette opens


---

# 2 - Email Data Layer and Mock Mailbox

Create the email management data structure.

Implement email objects containing:

- id
- sender
- recipients
- subject
- preview
- body
- timestamp
- attachments
- labels
- read status
- starred status
- priority
- thread id


Create realistic mock mailbox data.

Include:

- Inbox
- Sent
- Drafts
- Trash
- Spam
- Labels


Build the email list UI.

Each email card should display:

- sender avatar
- sender name
- subject
- preview
- timestamp
- labels
- attachment indicator
- unread state


Add interactions:

- Open email
- Mark read/unread
- Star
- Select multiple emails
- Archive
- Delete


Create bulk actions toolbar:

- Archive selected
- Delete selected
- Mark read
- Add label


### Test checklist

Verify:

- Emails appear correctly
- Selecting emails works
- Bulk actions update state
- Opening an email displays details
- Labels and unread states update


---

# 3 - Temporary Google OAuth and Gmail Integration

Integrate temporary Google OAuth authentication as the only login method.

Use:

- Google OAuth 2.0
- Gmail API


Requirements:

- No username/password authentication
- Authentication isolated in services
- Easy replacement with another provider later


Create dedicated services:

- Auth Service
- Gmail Service
- Token Service
- Session Service


After authentication retrieve:

- User profile
- Avatar
- Email address


Request Gmail permissions for:

- Inbox
- Sent
- Drafts
- Trash
- Labels
- Attachments
- Threads


Create account management UI:

Display:

- Connected account
- Profile image
- Email
- Last synchronization
- Connection status


Actions:

- Refresh mailbox
- Disconnect account
- Reconnect account


Create synchronization interface:

- Progress indicator
- Loading animation
- Error states
- Retry button


If Gmail API is unavailable:

Show:

- Friendly fallback screen
- Retry action
- Connection status


Security requirements:

- Never expose OAuth secrets
- Keep API logic modular
- Prepare future backend migration


### Test checklist

Verify:

- Login screen works
- Authentication state changes correctly
- Account information is displayed
- Sync states are visible
- Errors have recovery actions


---

# 4 - AI Email Assistant and Visual Actions

Transform the AI assistant into an email management engine.

The AI must understand commands like:

- summarize today's emails
- show unread emails
- archive this
- reply politely
- write a professional answer
- delete spam
- search invoices
- find emails from a contact
- show attachments
- draft a follow-up


Do not return only text responses.

Every AI action should generate visual results.

Examples:


## Summarize emails

Display:

- Summary cards
- Important messages
- Priority indicators
- Action items


## Search invoices

Display:

- Matching email cards
- Sender
- Date
- Attachment preview


## Extract tasks

Display:

- Checklist
- Deadlines
- Responsible person


## Draft reply

Display:

- Rich text editor
- Tone selector
- Generate button
- Send button


Add visible graphical controls for every AI action:

- Buttons
- Menus
- Context actions
- Toolbars


### Test checklist

Verify:

- AI commands trigger different UI components
- Results are visual
- Actions update email state
- AI understands selected email context


---

# 5 - Complete Email Workspace Experience

Create the full email productivity workspace.

Implement:

## Email Preview Panel

Include:

- Sender information
- Conversation thread
- Rich email content
- Attachments
- Metadata


Actions:

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
- Pin conversation


## Compose Experience

Create a modern compose window:

Features:

- Rich text editor
- Recipients
- Attachments
- Draft saving
- AI writing assistance


AI writing features:

- Improve text
- Change tone
- Translate
- Shorten
- Make professional
- Generate follow-up


## Advanced UX

Add:

- Drag and drop attachments
- Undo actions
- Toast notifications
- Confirmation dialogs
- Optimistic updates
- Loading overlays
- Skeleton loaders


### Test checklist

Verify:

- Opening emails works
- Threads display correctly
- Compose works
- Attachments preview correctly
- AI writing tools modify content
- Undo actions work


---

# 6 - Final AI Email Manager SaaS Interface

Polish the entire application into a premium email management platform.

Add:


## Responsive Experience

Desktop:

- Collapsible sidebar
- Resizable AI panel
- Multi-column workspace


Tablet:

- Adaptive layout
- Touch-friendly controls


Mobile:

- Bottom navigation
- Drawers
- Mobile compose
- Touch interactions


## Design System

Apply:

- Dark mode
- Light mode
- Rounded components
- Glassmorphism
- Smooth transitions
- Premium shadows
- Elegant spacing
- Animated states


## Productivity Features

Include:

- Keyboard shortcuts
- Command palette
- Smart filters
- Search experience
- Notifications
- Quick actions


Final requirements:

- AI chat is not the main interface
- Email management happens visually
- Every action is available through UI controls
- Gmail integration is modular
- Fully responsive
- Production-quality SaaS design


### Final acceptance checklist

- Email dashboard works
- Authentication works
- Gmail service structure exists
- Mailbox synchronization works
- AI assistant works
- Compose works
- Search works
- Filters work
- Mobile experience works
- Interface feels like a commercial productivity application
