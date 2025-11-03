Create a full-stack English Vocabulary Builder web application with the following specifications:
TECHNOLOGY STACK:
⦁	Backend: Node.js + Express + SQLite3 + JWT authentication
⦁	Frontend: React (standalone HTML with CDN)
⦁	Server: Ubuntu 24.04 with Nginx
⦁	Database: SQLite with separate databases per user
CORE FEATURES:
1.	AUTHENTICATION SYSTEM:
⦁	Login page with username/password
⦁	JWT token-based sessions (24-hour expiry)
⦁	Password change functionality
⦁	Default admin user: username "shen" with password "admin123"
⦁	Admin can create/delete other users
⦁	Each user has isolated vocabulary database
2.	ADD WORD PAGE:
⦁	Word input field with "Lookup" button linking to Cambridge Dictionary
⦁	Phonetic (IPA) input field
⦁	Meaning input field (English | Chinese format)
⦁	Up to 10 example sentences with add/remove functionality
⦁	Save button to store word with all details
3.	REVIEW PAGE:
⦁	Time period filters:
⦁	Last 7 days (today to today-7 days)
⦁	Last week (today-7 to today-13 days)
⦁	Week before (today-14 to today-20 days)
⦁	Custom date range (with start/end date pickers)
⦁	All words
⦁	Randomly shuffle and display one word at a time
⦁	Show/Hide button to reveal: phonetic, meaning, examples
⦁	Next button to advance to next word
⦁	Progress counter (e.g., "Word 3 of 15")
4.	SEARCH & MODIFY PAGE:
⦁	Search with wildcard support (* for multiple chars, ? for single char)
⦁	Display multiple results when wildcards used (clickable list)
⦁	For selected word, show: word, phonetic, meaning, examples
⦁	Edit meaning button (opens textarea with Save/Cancel)
⦁	Add new example sentences (max 10 per word)
⦁	Display date added
5.	USER MANAGEMENT (Admin only):
⦁	"Add User" button visible only to admin
⦁	Create users with username and password (min 6 chars)
⦁	List all users with admin badges
⦁	Delete users (except admin)
TECHNICAL REQUIREMENTS:
⦁	Backend runs on port 3002
⦁	API endpoints: /api/auth/, /api/users/, /api/words/*
⦁	Database schema:
⦁	users table: id, username, password(hashed), is_admin, created_at
⦁	words table: id, word(unique), phonetic, meaning, date_added
⦁	examples table: id, word_id(FK), example_text
⦁	User databases stored at: /home/shen/vocabulary-builder-V2/backend/databases/{username}_vocabulary.db
⦁	Systemd service: vocabulary-api-v2
⦁	Frontend served from: /var/www/vol.jscom.com.au
⦁	Nginx config at: /etc/nginx/sites-available/vol.jscom.com.au
UI/UX REQUIREMENTS:
⦁	Fully responsive design (mobile-first with Tailwind CSS)
⦁	Color scheme: Indigo/blue gradient background
⦁	Button states: hover effects, loading spinners, disabled states
⦁	Notifications: green for success, red for errors (auto-dismiss in 3s)
⦁	Text wrapping: break-words for long content
⦁	Touch-friendly: minimum 44px tap targets on mobile
DELIVERABLES:
1.	Complete server.js with all endpoints
2.	Complete index.html with React app
3.	package.json with dependencies
4.	Deployment bash script
5.	Systemd service configuration
6.	Nginx configuration
7.	Database migration/fix scripts if needed
SPECIFIC BEHAVIORS:
⦁	Wildcard search: convert * to %, ? to _ for SQL LIKE queries
⦁	Multiple search results displayed in blue box, click to select
⦁	Edit meaning replaces entire meaning (not appending)
⦁	Examples stored in separate table with foreign key
⦁	Passwords hashed with bcrypt (10 rounds)
⦁	JWT secret should be configurable via environment variable
