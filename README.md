# SH Community - Full Stack Web Application

## 🚀 Overview

SH Community is a premium private network platform for 100 elite members, led by Suraj Shinde. This is a full-stack application with React frontend, Node.js/Express backend, MongoDB database, and real-time Socket.io chat.

---

## ✨ Features (Original + Enhanced)

### Original Features
- Public home page with hero, features, leader section
- Explore page (community preview)
- Join request form (3-step)
- Member login (email + Google OAuth)
- Member dashboard with sidebar navigation
- Real-time group chat (Socket.io)
- Events calendar with RSVP
- Polls & voting system
- File sharing
- Gallery
- Notifications
- WhatsApp group integration
- Admin dashboard (accept/reject members, manage everything)

### ✅ Enhanced Features Added
1. **3-Step Join Application** — Name/email/phone → City/profession/LinkedIn → Reason/motivation
2. **XP & Leaderboard System** — Members earn XP for messages (+2), events (+25), polls (+5), resources (+10), referrals (+50)
3. **Mentorship Program** — Request 1:1 sessions with mentors, track scheduled sessions
4. **Resource Library** — Curated books, courses, templates, tools (save/bookmark)
5. **Community Analytics** (Admin) — Member growth chart, city breakdown, engagement metrics
6. **Event RSVP System** — Going / Maybe / Not Going with seat tracking
7. **Announcement System** — Pinned/important/normal types with full management
8. **Profile Page** — Avatar, bio, profession, XP bar, stats (messages, events, XP)
9. **Settings Page** — Notifications, privacy toggles, password change, theme switcher
10. **Countdown Timer** — Live countdown to next event on homepage
11. **Activity Feed** — Real-time community activity in dashboard
12. **Message Reactions** — Emoji reactions on chat messages
13. **Typing Indicators** — See who's typing in chat
14. **Direct Messages** — Private 1:1 chat with members
15. **Community Health Dashboard** — Admin sees capacity, engagement, retention stats
16. **Content Management** — Admin creates announcements, events, polls from one panel
17. **Danger Zone** — Admin can clear messages, export data, reset stats
18. **Testimonials Section** — Social proof on homepage
19. **Community Rules** — Publicly visible guidelines
20. **Responsive Mobile UI** — Full mobile-first design

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite + Tailwind CSS |
| Backend | Node.js + Express.js |
| Database | MongoDB + Mongoose |
| Auth | JWT + Google OAuth (Passport.js) |
| Real-time | Socket.io |
| File Storage | Multer (local) → S3 (production) |
| State | React Context + useReducer |

---

## 📁 Project Structure

```
sh-community/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── common/          # Button, Card, Modal, Toast, Badge
│   │   │   ├── layout/          # Navbar, Sidebar, Footer
│   │   │   ├── home/            # Hero, Features, Leader, CTA
│   │   │   ├── dashboard/       # Overview, Chat, Events, Polls...
│   │   │   └── admin/           # AdminOverview, Requests, Analytics
│   │   ├── pages/               # Home, Explore, Join, Login, Dashboard, Admin
│   │   ├── context/             # AuthContext, NotificationContext
│   │   ├── hooks/               # useAuth, useSocket, useNotifications
│   │   └── utils/               # api.js, socket.js, helpers.js
│   ├── package.json
│   └── tailwind.config.js
│
├── backend/
│   ├── models/
│   │   ├── User.js
│   │   ├── JoinRequest.js
│   │   ├── Event.js
│   │   ├── Poll.js
│   │   ├── Message.js
│   │   ├── Announcement.js
│   │   ├── Notification.js
│   │   ├── Activity.js
│   │   ├── File.js
│   │   ├── Gallery.js
│   │   ├── Settings.js
│   │   ├── Mentorship.js
│   │   └── Resource.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── users.js
│   │   ├── joinRequests.js
│   │   ├── events.js
│   │   ├── polls.js
│   │   ├── messages.js
│   │   ├── announcements.js
│   │   ├── files.js
│   │   ├── gallery.js
│   │   ├── notifications.js
│   │   ├── activity.js
│   │   ├── mentorship.js
│   │   ├── resources.js
│   │   └── settings.js
│   ├── middleware/
│   │   ├── auth.js              # JWT protect + adminOnly
│   │   ├── passport.js          # Google OAuth strategy
│   │   └── upload.js            # Multer config
│   ├── socket/
│   │   └── chat.js              # Socket.io event handlers
│   ├── controllers/             # Business logic (one per route)
│   ├── uploads/                 # Local file storage
│   ├── .env
│   └── server.js
│
└── README.md
```

---

## ⚙️ Setup Instructions

### 1. Prerequisites
- Node.js 18+
- MongoDB (local or Atlas)
- Google OAuth credentials (optional)

### 2. Backend Setup

```bash
cd backend
npm install
cp .env.example .env
# Edit .env with your values
npm run dev
```

### 3. Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

### 4. Environment Variables

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/sh-community
JWT_SECRET=your_jwt_secret_here
JWT_EXPIRE=7d
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_CALLBACK_URL=http://localhost:5000/api/auth/google/callback
SESSION_SECRET=your_session_secret
CLIENT_URL=http://localhost:3000
ADMIN_EMAIL=admin@shcommunity.com
ADMIN_PASSWORD=admin123
WHATSAPP_LINK=https://chat.whatsapp.com/your_group_link
```

---

## 🔑 Demo Credentials

| Role | Email | Password |
|------|-------|----------|
| Admin | admin@shcommunity.com | admin123 |
| Member | member@shcommunity.com | member123 |

---

## 🌐 Deployment

### Frontend → Vercel
```bash
cd frontend && npm run build
vercel deploy
```

### Backend → Railway / Render
```bash
# Set all env vars in dashboard
# Deploy from GitHub
```

### Database → MongoDB Atlas
- Create cluster at mongodb.com/atlas
- Update MONGODB_URI in env

---

## 🔌 API Endpoints Summary

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | /api/auth/login | Login | Public |
| POST | /api/auth/google | Google OAuth | Public |
| POST | /api/joinRequests | Submit application | Public |
| GET | /api/users | List members | Member |
| GET | /api/events | List events | Member |
| POST | /api/events | Create event | Admin |
| POST | /api/polls/:id/vote | Vote | Member |
| GET | /api/notifications | Get notifications | Member |
| PUT | /api/joinRequests/:id/approve | Approve member | Admin |
| GET | /api/activity/leaderboard | XP rankings | Member |
| GET | /api/settings/whatsapp | WhatsApp link | Member |
| PUT | /api/settings/whatsapp | Update WA link | Admin |

---

## 📱 Socket.io Events

| Event | Direction | Description |
|-------|-----------|-------------|
| join_room | Client → Server | Join chat room |
| send_message | Client → Server | Send message |
| new_message | Server → Client | Receive message |
| typing | Client → Server | User is typing |
| user_typing | Server → Client | Show typing indicator |
| delete_message | Admin → Server | Remove message |
| user_online | Server → Client | User went online |
| user_offline | Server → Client | User went offline |

---

## 📄 License
Private — SH Community © 2026. All rights reserved.
