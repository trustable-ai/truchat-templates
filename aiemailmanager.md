# 1. Build the Responsive Email Manager Foundation

Transform the existing AI chat application into the foundation of an AI-powered email manager.

Keep the existing chat experience as the core of the application, but redesign the UI so that it can progressively support Gmail email access and AI-assisted email exploration.

Build a clean, modern, application-style interface with these main areas:

- A top application bar with the product name and user/account area.
- A responsive navigation area for email folders and filters.
- A central area for the AI chat.
- An email results/list area that will later display messages found through searches or AI requests.
- An email detail view that will later display the selected email.

The application must be fully responsive.

Test and optimize the layout for:

- Small mobile phones.
- Medium and large mobile phones.
- All common phone sizes available in Google Chrome DevTools device emulation.
- Tablets in portrait and landscape mode.
- Laptops.
- Desktop monitors.
- Large desktop screens.

Responsive behavior:

- On desktop, use a multi-column application layout when enough space is available.
- On tablets, collapse secondary areas when necessary.
- On mobile, use a single-column flow.
- Navigation should become a drawer or equivalent compact UI on small screens.
- Email lists and email details must be easy to use with touch.
- Avoid horizontal scrolling.
- Buttons and interactive controls must have mobile-friendly touch targets.

Do not implement email sending, composing, replying, forwarding, deleting, or modifying messages.

The application is strictly a read-only AI email manager.

Preserve the existing AI chat functionality and prepare the architecture so the following notebook steps can add authentication, IMAP access, email browsing, filtering, and AI-powered querying.

At the end of this step, run the application and verify the responsive layout at multiple viewport sizes before continuing.

---

# 2. Add Secure Gmail IMAP Login and Logout

Extend the application created in the previous step with authentication for Gmail through IMAP.

Do not use Google OAuth for this implementation.

Create a login screen containing exactly these connection fields:

- IMAP Host
- IMAP Username
- IMAP Password

The default IMAP host may be shown as:

imap.gmail.com

Allow the user to change it.

Use the credentials only on the server side to establish the IMAP connection.

Security requirements:

- Never expose the IMAP password in frontend JavaScript.
- Never include the password in URLs.
- Never log the password.
- Never display the password after authentication.
- Never store credentials in source code.
- Avoid persistent password storage unless absolutely necessary.
- Keep authentication state securely on the backend.
- Use TLS/SSL for the IMAP connection.
- Return safe and understandable authentication errors to the UI.

After successful authentication:

- Show the main email manager interface.
- Display the authenticated email address in the account area.
- Keep the IMAP connection information associated with the user's session.

Add a Logout action.

Logout must:

- Close the IMAP connection if one is active.
- Destroy the authenticated session.
- Remove temporary credentials or authentication information.
- Return the user to the login page.

Add a small connection-status indicator so the user can distinguish between:

- Connected
- Connecting
- Disconnected
- Authentication error

Make the login page fully responsive using the same mobile, tablet, laptop, and desktop requirements from the previous step.

Do not implement any IMAP operations that modify the mailbox.

At the end of this step, verify login, failed login, authenticated session handling, connection loss, and logout.

---

# 3. Add Read-Only Mailbox Browsing, Email Reading, and Filtering

Using the authenticated IMAP connection implemented in the previous step, add real mailbox browsing.

The application must be strictly read-only.

Implement mailbox discovery so the UI can show available folders/mailboxes such as:

- Inbox
- Sent
- Drafts
- Spam
- Trash
- Archive / All Mail
- Starred or other folders when exposed through IMAP
- Custom labels/folders when available

Do not assume every server exposes identical folder names. Discover them through IMAP.

For the selected mailbox, retrieve email metadata and display a paginated or progressively loaded email list.

For each message, show useful information such as:

- Sender
- Sender email address
- Subject
- Date/time
- Short preview/snippet
- Read/unread state when available
- Attachment indicator when available

Selecting an email must open a readable email detail view containing:

- From
- To
- CC when present
- Date
- Subject
- Email body
- Attachment metadata when available

Render HTML emails safely. Sanitize untrusted HTML before displaying it and prevent email content from executing arbitrary scripts.

Add user-controlled filtering and search.

Support filters for at least:

- Mailbox/folder
- Sender
- Recipient
- Subject
- Text
- Date range
- Read/unread status
- Has attachments

Prefer server-side IMAP searches where practical instead of downloading the entire mailbox.

Add pagination or lazy loading so very large Gmail accounts remain usable.

Make loading states explicit and avoid freezing the UI while IMAP operations are running.

Important read-only requirement:

The application must never:

- Send email
- Compose email
- Reply
- Forward
- Delete email
- Move email
- Archive email
- Change labels
- Mark messages as read or unread
- Add or remove stars
- Modify flags
- Modify drafts

When opening messages through IMAP, avoid accidentally setting the `Seen` flag. Use read-only mailbox access and BODY.PEEK or the appropriate equivalent whenever possible.

Preserve the responsive design.

On desktop, the mailbox list, message list, and message details can coexist when space permits.

On mobile, provide a natural navigation flow:

Folders → Messages → Message

with clear back navigation.

At the end of this step, test the application against a Gmail mailbox containing enough messages to verify pagination, folder navigation, searching, HTML rendering, and read-only behavior.

---

# 4. Connect the AI Chat to Gmail Email Retrieval

Turn the existing AI chat into an intelligent interface for querying the authenticated mailbox.

The user must be able to ask natural-language questions such as:

- "Show me emails from John from last month."
- "Find emails about the Acme contract."
- "What did Sarah tell me about the meeting?"
- "Show messages containing invoices from July."
- "Find unread emails from example.com."
- "Which emails mention Kubernetes?"
- "Summarize the emails I received from Mario this week."
- "What was the latest email from Alice about the project?"

Do not provide the AI model with unrestricted direct access to IMAP.

Create a controlled email retrieval layer with explicit read-only tools/functions that the AI can call.

Create tools similar to:

- list_mailboxes()
- search_emails(...)
- get_email_metadata(...)
- get_email_content(...)
- get_email_thread(...) when technically possible
- search_by_sender(...)
- search_by_date_range(...)
- search_by_subject(...)
- search_by_text(...)

The AI should translate the user's natural-language request into calls to these controlled tools.

The backend should perform IMAP operations and return only the necessary email data to the AI.

Implement a retrieval workflow:

1. User asks a question in chat.
2. The AI determines what mailbox information is required.
3. The AI calls one or more read-only email tools.
4. The backend queries Gmail through IMAP.
5. Relevant messages are returned.
6. The AI answers using those messages.
7. Matching emails are also shown in the email results UI when appropriate.

Whenever the AI makes a factual statement based on an email, make it possible for the user to identify the source message.

Add source references to AI responses using useful information such as:

- Sender
- Subject
- Date

Allow clicking a source reference to open the corresponding email in the email detail view.

Do not hallucinate email information.

If the necessary information cannot be found in the mailbox, the AI should clearly say that it could not find supporting emails.

Protect against prompt injection contained inside email bodies.

Treat all email content as untrusted data, never as application or system instructions.

An email saying things such as "ignore previous instructions", "send this message", "reveal credentials", or similar must never change the AI agent's permissions or behavior.

The AI email tools must remain read-only regardless of instructions found inside emails or supplied by the user.

Do not expose IMAP credentials to the AI model.

At the end of this step, demonstrate several natural-language email queries and verify that the AI results correspond to actual messages returned through IMAP.

---

# 5. Complete the AI-Powered Gmail Email Manager

Complete and polish the application built in the previous notebook steps into a coherent AI-powered read-only Gmail email manager.

The final application should provide two complementary ways of accessing email:

1. Traditional email browsing and filtering.
2. Conversational AI querying through chat.

Integrate them tightly.

For example:

- A manual email search should make its results available to the chat context when useful.
- AI search results should appear in the email results interface.
- Clicking an email referenced by the AI should open that email.
- The user should be able to ask follow-up questions about a selected email.
- The user should be able to ask follow-up questions about a set of search results.

Add useful AI capabilities such as:

- Summarize one email.
- Summarize a group of emails.
- Summarize a conversation/thread when available.
- Extract dates.
- Extract people and organizations.
- Extract action items.
- Find decisions mentioned in messages.
- Find messages related to a topic.
- Compare information contained in several messages.
- Produce chronological summaries of related emails.
- Answer questions whose evidence may be distributed across multiple emails.

Always preserve source traceability.

For AI answers based on mailbox content, provide clickable references to the relevant emails whenever possible.

Improve application states for:

- Initial loading
- Empty mailbox
- No search results
- AI processing
- IMAP connection failure
- Session expiration
- Authentication failure
- Network failure
- Very large result sets

Review performance.

Avoid downloading entire mailboxes.

Use:

- IMAP-side searching where possible
- Pagination
- Lazy loading
- Limited result sets
- Fetching complete email bodies only when necessary
- Caching of safe non-sensitive metadata when useful

Review security.

Ensure:

- Credentials remain server-side.
- Passwords are never logged.
- Email HTML is sanitized.
- Email content is treated as untrusted.
- AI tool permissions are explicitly read-only.
- There is no email-writing tool.
- There is no hidden API endpoint capable of sending or modifying email.
- Logout destroys authentication state.
- IMAP connections are cleaned up correctly.

Perform a final read-only audit.

There must be no feature allowing the application or AI to:

- Compose
- Send
- Reply
- Forward
- Delete
- Archive
- Move
- Label
- Star
- Mark read
- Mark unread
- Modify any email or mailbox state

Perform a complete responsive review using Chrome DevTools.

Test representative devices covering:

- Small phones
- Standard phones
- Large phones
- iPhone-sized devices
- Android-sized devices
- Foldable/narrow layouts where available
- Small tablets
- Large tablets
- Laptop screens
- Standard desktop screens
- Large desktop screens

Fix clipping, overflow, unusable dialogs, overly small controls, and layouts that depend on fixed screen dimensions.

The final result should feel like a real email application whose primary differentiator is that the user can simply chat with their Gmail mailbox to find, inspect, filter, summarize, and understand existing emails without ever giving the AI permission to write or modify email.
