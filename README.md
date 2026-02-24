# BOXpad – AI-Powered CRM Dashboard

> A front-end screening assignment implementation built with React (CDN), vanilla CSS, and live public APIs.

![BOXpad Preview](public/preview-placeholder.txt)

---

## 📋 Setup Instructions

This project requires **no build step** or **Node.js**. It runs directly in a browser.

### Option 1 – Open directly (quickest)
1. Open `index.html` in **Google Chrome**, **Edge**, or **Firefox** (modern browser required)
2. If assets don't load due to CORS restrictions on `file://`, use Option 2.

### Option 2 – Local dev server (recommended)
If you have Python installed:
```bash
# Python 3
python -m http.server 8000
# then open http://localhost:8000
```

If you have Node.js installed:
```bash
npx serve .
# then open http://localhost:8000
```

### Option 3 – VS Code Live Server
Install the **Live Server** extension → right-click `index.html` → **Open with Live Server**

---

## 🌐 APIs Used

| Section | API | Endpoint | Purpose |
|---|---|---|---|
| Inbox | [JSONPlaceholder](https://jsonplaceholder.typicode.com) | `/users`, `/posts` | Conversations & messages |
| Contacts | [JSONPlaceholder](https://jsonplaceholder.typicode.com) | `/users` | Contact list with company/email |
| AI Employees | [ReqRes.in](https://reqres.in) | `/api/users?page=1&2` | Real avatar photos + user data |
| Workflows | [JSONPlaceholder](https://jsonplaceholder.typicode.com) | `/posts?userId=3` | Workflow items with descriptions |

All API calls include:
- **Loading state** → skeleton shimmer animation
- **Error state** → friendly error with Retry button
- **Success state** → animated data reveal

---

## 🏗 Project Structure

```
boxpad/
├── index.html               # Entry point (loads React + Babel via CDN)
├── README.md
├── src/
│   ├── App.jsx              # Root component (intro ↔ dashboard flow)
│   ├── main.jsx             # React DOM mount with global-poll strategy
│   ├── api/
│   │   └── apiService.js    # All API calls (JSONPlaceholder, ReqRes, DummyJSON)
│   ├── hooks/
│   │   └── useFetch.js      # Custom hook: data / loading / error / refetch
│   ├── components/
│   │   ├── GlowBackground.jsx      # Animated SVG circular glow rings
│   │   ├── HoneycombNav.jsx        # Hexagonal icon grid navigation
│   │   ├── IntroScreen.jsx         # Full-screen intro with ring animation
│   │   ├── Navbar.jsx              # Top navigation bar
│   │   ├── SkeletonLoader.jsx      # Shimmer skeleton placeholders
│   │   ├── Dashboard.jsx           # Main dashboard orchestrator
│   │   ├── InboxSection.jsx        # 3-panel inbox (sidebar/list/chat)
│   │   ├── ContactsSection.jsx     # Searchable contacts grid
│   │   ├── AIEmployeesSection.jsx  # AI agent cards with photos
│   │   └── WorkflowsSection.jsx    # Workflow automation cards
│   └── styles/
│       ├── global.css       # Design tokens, CSS variables, reset
│       ├── animations.css   # All @keyframes
│       ├── components.css   # Component-level styles
│       ├── dashboard.css    # Layout styles (intro, dashboard, sidebar)
│       └── responsive.css   # Mobile / tablet breakpoints
```

---

## ✨ Features Implemented

### UI / Design
- ✅ **Exact Figma match** – dark navy/blue theme with glassmorphism panels
- ✅ **Circular glow rings** – rotating SVG rings in background and intro screen (Figma GIF replacement)
- ✅ **Honeycomb navigation** – SVG hexagon grid with gradient fill + animated dashed outline on selected state
- ✅ **Typography** – Inter font, consistent hierarchy from design tokens
- ✅ **Micro-animations** – hover scale, badge pop, message slide-in, section reveal

### API Integration
- ✅ **Skeleton loading** – shimmer placeholders during fetch
- ✅ **Error states** – friendly messages with Retry button
- ✅ **Staggered animation** – items animate in with `animationDelay`
- ✅ **Custom `useFetch` hook** – reusable across all sections

### Sections
- ✅ **Inbox** – 3-column (sidebar / conversation list / chat detail), search, filter chips, send message UX
- ✅ **Contacts** – searchable grid with role badge, company, search filter
- ✅ **AI Employees** – real avatar photos (ReqRes.in), specialty badge, status dot, search + online filter
- ✅ **Workflows** – 2-column grid, active/pending status, trigger type, filter tabs

### Responsiveness
- ✅ **Desktop (≥1025px)** – full 3-column inbox, full honeycomb sidebar
- ✅ **Tablet (≤1024px)** – collapsed sidebar icons, narrower list
- ✅ **Mobile (≤768px)** – bottom navigation bar, stacked inbox layout, single column grids

---

## 🧠 Assumptions Made

1. **No Node.js** available – used React 18 + Babel Standalone via CDN for zero-setup compatibility
2. **GIF replacement** – Figma comment said "Have a GIF here". Implemented as CSS animated SVG circular glow rings (same visual result, no external GIF file needed)
3. **Intro screen** – Added a landing intro screen since Figma showed a full-screen circular ring animation before the dashboard
4. **Fly animation** – When a hex icon is clicked, the icon briefly "disappears" (opacity 0) to simulate flying to its section, then the section fades in (full SVG flying overlay not practical without a build system for precise coordinates, but the intent is preserved)
5. **JSONPlaceholder data** – Used real API data but added role/company/avatar color metadata client-side since the public API doesn't have CRM-specific fields
6. **DummyJSON** – workflows use JSONPlaceholder `/posts` (repurposed) since DummyJSON's `/todos` has simpler structure; still demonstrates multi-API integration
7. **Babel Standalone** – Babel transforms JSX in-browser; production deployment would use a bundler (Vite/webpack)

---

## 🚀 Optional: Deploy to Vercel / Netlify

Since this is a static HTML app, just drag the project folder to:
- [Netlify Drop](https://app.netlify.com/drop)
- [Vercel](https://vercel.com) (connect GitHub repo)

No build command needed.

---

## 📦 No External Packages

Only CDN scripts used:
- `react@18` + `react-dom@18` – UI framework
- `@babel/standalone` – JSX transformation in-browser
- Google Fonts (Inter) – Typography
