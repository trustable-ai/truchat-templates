# 1. Build the Gmail Login and Read-Only Email Foundation

Transform the existing AI chat application into the first version of an AI-powered Gmail email manager.

The application must use **Google OAuth login only**. Do not require users to manually provide API keys, Gmail API keys, client secrets, tokens, or other credentials inside the application UI. The user must authenticate by clicking a **Sign in with Google** button and granting the required permissions through Google's authorization flow.

Request only the minimum Gmail permissions required for this application. The application must be strictly **read-only**:

* Access the authenticated user's Gmail mailbox.
* Read email messages.
* Read email metadata such as sender, recipients, subject, date, labels, thread ID, and message ID.
* Read email bodies when needed.
* List mailbox folders/labels.
* Search and filter messages.
* Do not send email.
* Do not compose email.
* Do not create drafts.
* Do not modify email.
* Do not delete email.
* Do not archive email.
* Do not change labels.
* Do not mark messages as read or unread.

Add authentication state management so that:

* Logged-out users see a clean Google login screen.
* Logged-in users enter the email manager.
* The current Google account is visible in the UI.
* A Logout action is available at all times.
* Logout clears the local application session and returns the user to the login screen.

Preserve the existing AI chat functionality as the main application foundation.

After login, retrieve a small initial set of recent Gmail messages and display them in a simple mailbox panel alongside the chat interface.

Each email item should show at least:

* Sender
* Subject
* Date/time
* Short preview/snippet

Clicking an email must open its complete readable content without modifying its Gmail state.

Handle authentication errors, expired sessions, missing permissions, network errors, and empty mailboxes gracefully.

The application architecture must already be suitable for later adding natural-language questions about the user's emails.

Make this first implementation functional before moving to the next step.

---

# 2. Build a Responsive Email Manager Interface Around the AI Chat

Starting from the Gmail-authenticated application built in the previous step, redesign the interface into a complete responsive AI email manager while preserving all existing functionality.

The product should feel primarily like an **AI chat application connected to Gmail**, rather than a traditional Gmail clone.

Create three logical areas:

1. Navigation and account controls.
2. Email browsing and filtering.
3. AI chat.

On large desktop screens, use the available horizontal space effectively. A preferred layout is:

* A compact navigation/sidebar area.
* A mailbox/message list area.
* A large AI chat area.

The AI chat should remain the primary visual focus.

On tablets, intelligently reduce panel widths and allow panels to collapse when required.

On mobile phones, avoid squeezing desktop columns together. Convert the interface into a mobile-first navigation model where the user can move between:

* Chat
* Emails
* Email details
* Filters/account

Use drawers, tabs, bottom navigation, stacked views, or another appropriate mobile interaction pattern.

The application must be fully responsive across the common mobile devices available in Chrome/Google DevTools device emulation, including small phones, modern iPhones, Android phones, foldable-sized narrow screens where practical, tablets, laptops, and large desktop monitors.

Design for at least these general viewport classes:

* Approximately 320–480 px wide phones.
* Approximately 600–900 px wide tablets.
* Approximately 1024–1440 px laptops/desktops.
* Large desktop displays above 1440 px.

Avoid:

* Horizontal page scrolling.
* Clipped buttons.
* Unreadable text.
* Fixed-width panels that break on small screens.
* Dialogs larger than the viewport.
* Controls that require mouse hover.
* Tiny touch targets.

Email rows must remain easy to scan and select on touch devices.

Keep the Google account identity and Logout action accessible without dominating the interface.

Create a professional, minimal UI suitable for managing a large mailbox.

Do not add any email-writing functionality.

---

# 3. Add Gmail Search, Filters, Labels, Threads, and Message Exploration

Extend the application so the user can efficiently explore their Gmail mailbox before using AI.

Implement read-only Gmail browsing capabilities.

Support:

* Recent emails.
* Pagination or incremental loading.
* Search by text.
* Sender filtering.
* Recipient filtering where applicable.
* Subject filtering.
* Date or date-range filtering.
* Gmail labels.
* Unread/read filtering when Gmail metadata makes it available.
* Attachments-present filtering when available.
* Thread/conversation grouping.
* Opening a complete thread.
* Opening an individual message.
* Returning from message details to previous results without losing filters.

Where useful, take advantage of Gmail's native search/query capabilities instead of downloading the complete mailbox to perform every search locally.

Add a search/filter interface that works well both with mouse/keyboard and touch.

Show active filters clearly and allow users to remove individual filters or reset all filters.

For an opened message, display useful read-only metadata such as:

* From
* To
* CC when present
* Subject
* Date
* Gmail labels
* Thread information
* Message content
* Attachment names and metadata when available

Do not introduce any operation that modifies Gmail.

Improve loading states for large inboxes. Do not block the entire interface while fetching another page of messages.

Use sensible caching where useful, while ensuring that one user's Gmail data can never leak into another authenticated user's session.

Keep all functionality from the previous notebook steps working.

---

# 4. Connect the AI Chat to Gmail and Answer Questions About Emails

Turn the existing AI chat into an intelligent conversational interface over the authenticated user's Gmail mailbox.

The user must be able to ask natural-language questions such as:

* "What emails did I receive from John last week?"
* "Summarize the emails from Acme about the contract."
* "Did anyone mention a deadline for the project?"
* "Find emails about the August invoice."
* "What did Sarah say about the meeting?"
* "Show me the latest messages from Google."
* "Which emails mention Kubernetes?"
* "Summarize my unread emails from today."
* "What are the most important things discussed in my emails this week?"

Create an AI email-retrieval layer rather than simply passing the entire mailbox to the model.

For each question:

1. Understand the user's intent.
2. Determine which Gmail searches or filters are appropriate.
3. Retrieve only the emails or threads relevant to the question.
4. Extract the necessary content.
5. Provide that context to the AI.
6. Generate an answer grounded in the retrieved Gmail messages.

Whenever possible, include references to the source emails used for the answer.

References should allow the user to click or tap and open the corresponding email or thread in the application.

For answers involving several messages, clearly distinguish:

* AI-generated explanation or summary.
* Source emails supporting the answer.

Do not invent information that does not exist in the retrieved emails.

If there is insufficient evidence, explicitly say that the requested information was not found.

If a question is ambiguous, use the available email context to make a reasonable interpretation, but allow the user to refine the query conversationally.

Preserve conversational context so follow-up questions work. For example:

User: "Find the messages from Alice about the conference."

Then:

User: "What date did she suggest?"

The second question should understand that "she" and the subject refer to the previous result.

Never allow the AI layer to send, edit, delete, archive, label, draft, or otherwise modify Gmail messages.

---

# 5. Complete the AI Email Manager and Make It Production-Ready

Starting from the complete application built in the previous steps, refine it into a polished read-only AI-powered Gmail email manager.

Review the entire implementation and remove temporary code, placeholders, duplicated components, fake data, development shortcuts, and unused dependencies.

Ensure the complete user flow works:

1. Open the application.
2. Sign in with Google.
3. Authorize read-only Gmail access.
4. Enter the email manager.
5. Browse emails.
6. Search and filter emails.
7. Open individual messages and threads.
8. Ask the AI questions about Gmail.
9. Open source messages referenced by AI answers.
10. Continue asking contextual follow-up questions.
11. Logout safely.

Improve AI answers so they are concise by default but can produce detailed summaries when requested.

For email-related AI answers, prefer a structure such as:

* Direct answer.
* Important details.
* Relevant email sources.

Do not expose raw Gmail API responses or unnecessary technical metadata to ordinary users.

Add appropriate:

* Loading indicators.
* Empty states.
* Authentication error states.
* Permission error states.
* Gmail retrieval error states.
* AI processing states.
* Retry actions.
* Session-expired handling.

Ensure sensitive Gmail content is never persisted unnecessarily in browser storage, logs, analytics, or debugging output.

Do not log email bodies or authentication tokens.

Maintain strict separation between authenticated users and their data.

Verify again that the Google OAuth permissions are the minimum necessary for read-only Gmail access.

Perform a complete responsive-design review using the mobile devices available in Chrome/Google DevTools and verify representative sizes for:

* Small mobile phones.
* Standard Android phones.
* Modern iPhones.
* Large phones.
* Tablets in portrait.
* Tablets in landscape.
* Small laptops.
* Standard desktop displays.
* Large desktop monitors.

Check important interactions in both portrait and landscape orientations where applicable.

The final application must remain fully usable with touch input and must not depend on hover interactions.

The final result should be a clean, fast, responsive application where the user experiences Gmail as a searchable knowledge source controlled primarily through an AI conversation.

The application must remain strictly read-only with regard to Gmail. Do not implement email composition, replies, forwarding, drafts, deletion, archiving, label changes, or any other mailbox mutation.
