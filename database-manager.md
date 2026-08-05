# Database Manager

# 1 - Transform the AI Chat into a Visual PostgreSQL Workspace (Foundation)

Transform the existing AI-powered chat into a premium PostgreSQL workspace where AI is the engine behind the interface—not the interface itself.

Use:

* React
* TypeScript
* Tailwind CSS
* shadcn/ui
* Framer Motion
* Lucide React

Requirements:

* Fully responsive (mobile-first)
* Modern SaaS design
* No classic chatbot UI
* No chat bubbles
* Only one persistent AI prompt bar fixed at the bottom
* Everything above the prompt must be graphical

Build the application shell including:

* Responsive App Layout
* Left Sidebar
* Top Navigation
* Main Workspace
* Right Inspector Panel (desktop)
* Mobile Drawer
* Bottom AI Prompt Bar

Design inspiration:

* Supabase Studio
* Prisma Studio
* Vercel
* Linear
* Arc Browser
* Raycast
* Notion

Use:

* glassmorphism
* rounded corners
* elegant shadows
* subtle gradients
* premium spacing
* Framer Motion transitions
* reusable components

The interface should include placeholder cards and beautiful empty states.

### Test checklist

* Responsive on desktop/tablet/mobile
* Sidebar collapses correctly
* Mobile drawer works
* Bottom AI prompt stays fixed
* No traditional chat interface remains

---

# 2 - AI Workspace Renderer

Replace conversational responses with graphical workspaces.

The AI must never create long conversations.

Instead, each command dynamically renders reusable React components.

Implement a renderer capable of switching workspace depending on AI intent.

Support example intents:

* Show Tables
* Database Overview
* Schema Explorer
* Show Indexes
* Slow Queries
* Query History
* Storage
* Performance
* Activity
* Empty State

Each workspace should animate with Framer Motion.

Include:

* Statistic Cards
* Dashboard Widgets
* Animated Cards
* Responsive Grids
* Skeleton Loading
* Empty States

Keep textual explanations minimal.

### Test checklist

Typing example commands should switch between graphical workspaces without creating chat messages.

---

# 3 - PostgreSQL Sandbox & Connection Manager

Create a built-in PostgreSQL Sandbox.

The sandbox should simulate a realistic production database of approximately 200 MB containing multiple schemas and thousands of records.

Example entities:

* Users
* Roles
* Permissions
* Orders
* Products
* Categories
* Inventory
* Payments
* Invoices
* Shipments
* Sessions
* Audit Logs
* Notifications
* Analytics

Sandbox actions:

* Reset
* Delete
* Recreate
* Duplicate
* Restore Demo Data

Deleting the sandbox must never affect external databases.

Create a graphical Connection Manager.

Each database appears as a card displaying:

* Name
* Host
* PostgreSQL Version
* Size
* Schemas
* Tables
* Active Connections
* Last Sync
* Status
* Environment Badge
* Favorite
* Tags

Support:

* Add Database
* Edit
* Duplicate
* Delete
* Test Connection
* SSL
* Connection String

### Test checklist

* Sandbox loads by default
* Sandbox actions update UI
* New fake connections can be added
* Connection cards are fully responsive

---

# 4 - Database Explorer

Build a graphical PostgreSQL Explorer.

Include:

* Schema Tree
* Table Explorer
* Column Inspector
* Constraints
* Relationships
* Indexes
* Views
* Functions

Desktop:

* collapsible sidebar
* floating inspector

Mobile:

* bottom sheets
* drawers

Opening a table should display:

* Columns
* Constraints
* Indexes
* Relationships
* Sample Rows

No raw SQL except inside dedicated SQL Cards.

### Test checklist

Opening tables updates the explorer and inspector without page reloads.

---

# 5 - SQL Workspace

Create a premium SQL experience.

SQL must only appear inside SQL Cards.

Each SQL Card includes:

* Syntax Highlighting
* Copy
* Edit
* Explain
* Execute
* Save

Query results appear inside responsive tables supporting:

* Sorting
* Filtering
* Pagination
* Column Resize
* Row Selection
* CSV Export
* JSON Export

Use animated transitions.

### Test checklist

Executing demo SQL updates the result table and shows loading animations.

---

# 6 - AI Insights Dashboard

Generate AI-powered insight cards instead of chat messages.

Examples:

* Missing Index
* Unused Index
* Duplicate Records
* Slow Query
* Missing Foreign Key
* Missing Primary Key
* Storage Optimization
* Vacuum Recommendation
* Deadlock
* Security Issue
* Backup Reminder
* Replication Warning
* Growth Trend

Each card contains:

* Icon
* Severity
* Title
* Description
* Confidence
* Affected Objects
* Storage Impact
* Performance Impact
* Timestamp

Clicking a card opens a slide-over panel displaying:

* Explanation
* Affected Objects
* Generated SQL
* Execution Preview
* Estimated Improvement
* Before / After
* Related Docs
* Execute
* Save
* Dismiss

Insights refresh automatically after every executed query.

### Test checklist

Opening an insight displays the slide-over and action buttons; dismissing or executing updates the dashboard.

---

# 7 - Final Polish

Polish the application until it feels like a commercial PostgreSQL IDE.

Improve:

* animations
* spacing
* typography
* hover effects
* loading states
* transitions
* responsiveness
* accessibility
* dark mode
* reusable components
* performance

Remove all placeholder UI that is no longer needed.

The final result should resemble a blend of:

* Supabase Studio
* Prisma Studio
* Vercel Dashboard
* Linear
* Arc Browser

The AI should always render graphical workspaces instead of conversations.

### Final acceptance checklist

* No traditional chat interface
* AI prompt bar is the only persistent text input
* All responses are graphical
* Responsive across all screen sizes
* Sandbox operational
* Connection Manager operational
* Database Explorer operational
* SQL Workspace operational
* AI Insights operational
* Smooth Framer Motion animations throughout
* Premium SaaS-quality visual design
