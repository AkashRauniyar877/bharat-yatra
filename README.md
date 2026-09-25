# 🇮🇳 BHARAT YATRA (भारत यात्रा)
### Centralized Indian Tourism Discovery, AI-Assisted Trip Planner & Monument Management Platform

---

## 📌 1. Overview & Vision

**Bharat Yatra** is a state-of-the-art, full-stack Indian tourism and heritage intelligence platform dedicated to showcasing the cultural, historical, and geographical diversity of India. The platform integrates **112+ comprehensive monuments and tourist destinations** across all 28 states and union territories, offering AI-assisted day-wise itinerary planning, intelligent budget calculation, real-time weather forecasts, GIS map discovery, and dedicated role-based administrative management with strict creator ownership protection.

---

## 🎯 2. Key Features & Platform Capabilities

### 🏛️ 1. Comprehensive Indian Monuments Directory (112+ Destinations)
* **UNESCO World Heritage Sites & Iconic Forts:** Taj Mahal, Red Fort, Amer Fort, Mehrangarh, Jaisalmer, Golconda, Hampi, Konark, etc.
* **Spiritual & Sacred Circuits:** Varanasi Ghats, Golden Temple, Kedarnath, Somnath, Meenakshi Amman, Mahabodhi.
* **Caves, Palaces & Natural Wonders:** Ajanta & Ellora Caves, Mysore Palace, Rann of Kutch, Valley of Flowers, Lonar Crater.
* **Beaches, Wildlife & Hill Stations:** Goa, Andaman, Munnar, Jim Corbett, Kaziranga, Ladakh Pangong Circuit.
* **Rich Metadata:** GPS coordinates, daily average budgets, ideal duration, best time to visit, regional foods, and transport connectivity.

### 🤖 2. Autonomous AI Destination Generator & Trip Planner
* **AI Monument Creator:** Enter any monument or city name (e.g. *"Ranthambore National Park"* or *"Khajuraho"*); the AI engine autonomously researches Wikipedia, Wikimedia Commons, OpenStreetMap Geocoding, and culinary databases to generate full verified records in seconds.
* **Personalized Day-Wise Trip Planner:** Generates custom **1 to 7 day itineraries** tailored by destination, traveler persona (Solo, Couple, Family, Friends), and budget style (Budget, Moderate, Luxury), saved directly to MongoDB Atlas.

### 🏨 3. Verified Hotels, Heritage Stays & Accommodations
* **Curated Accommodations:** Every monument page showcases recommended Luxury Heritage Resorts, Boutique Haveli stays, and Budget Backpackers homestays with price per night, ratings, amenities, and direct booking links.
* **Admin Hotel Manager:** Administrators can add, edit, or customize hotel options per destination.

### 📸 4. High-Definition Verified Tourism Photography
* **Multi-Tier Visual Archive:** Guaranteed high-resolution verified photographs for all 112+ monuments from Wikimedia Commons, Archaeological Survey of India (ASI) records, and Incredible India archives.
* **Interactive Lightbox:** Fullscreen photo preview with photographer credits and creative commons licenses.

### 🗺️ 5. Advanced GIS Interactive Map (4 Tile Layers)
* **Live GIS Mapping:** Real-time OpenStreetMap integration with dynamic pin clustering across Northern, Southern, Western, Eastern, and North-Eastern zones.
* **4 Tile Layer Modes:** Switch between CartoDB Voyager (Street), Standard OpenStreetMap, CartoDB Dark Matter (Night), and Esri HD Satellite view.
* **Quick-Jump Monument Ticker:** Click any monument ticker to smoothly animate and fly the map camera to the monument's exact coordinates.

### 💰 6. Smart Travel Budget Estimator
* Dynamic budget forecasting categorized into Stay, Food, Local Commute, Sightseeing Tickets, and Shopping/Buffer.
* Real-time expense sliders with money-saving travel hacks and seasonal cost optimization tips.

### 🍱 7. Regional Cuisine & 🚆 IRCTC Transport Hub
* State-wise authentic culinary guides with famous traditional thalis, street food, and iconic local eateries.
* Comprehensive transit advice covering Vande Bharat / IRCTC trains, domestic airports, and local commute options.

### 👑 8. Role-Based Architecture & Creator-Protected Admin Portal (`/admin`)
* **Dedicated Collections:** Independent `users` and `admins` database collections in MongoDB Atlas.
* **Strict Creator-Only Deletion Policy:** 
  - **Destinations Protection:** Only the administrator who created a destination record can delete it.
  - **Admin Team Protection:** Administrators can register new admin team members. **Only the creator admin who added an admin account can delete that admin account.** Other admins see a locked badge and get a permission denial guard.
* **Route Protection:** Protected routes restricting platform management strictly to verified administrators (`bharat_admin_2026`).

---

## 🛠️ 3. Technology Stack & Architecture

```
                       ┌──────────────────────────────────────────────┐
                       │             BHARAT YATRA CLIENT              │
                       │    React (Vite) + Tailwind CSS + Leaflet     │
                       │  Lucide Icons + Context API + Axios Client   │
                       └──────────────────────┬───────────────────────┘
                                              │ REST API / JSON (JWT)
                                              ▼
                       ┌──────────────────────────────────────────────┐
                       │           EXPRESS & NODE.JS BACKEND          │
                       │   Auth (bcryptjs + JWT), AI Planner Engine,  │
                       │   Destination Controller, Weather & External │
                       └──────────────────────┬───────────────────────┘
                                              │ Mongoose ODM
                                              ▼
                       ┌──────────────────────────────────────────────┐
                       │             MONGODB ATLAS DATABASE           │
                       │   • destinations (112+ Monument Documents)   │
                       │   • users (Traveler Profiles & Favorites)    │
                       │   • admins (Platform Managers & Credentials) │
                       └──────────────────────────────────────────────┘
```

* **Frontend:** React 18 (Vite), Tailwind CSS, React Router v6, Lucide React, Leaflet & React-Leaflet, Canvas Confetti.
* **Backend:** Node.js, Express.js, Mongoose ODM, JWT Authentication, bcryptjs password hashing, CORS, Dotenv.
* **Database:** MongoDB Atlas (`bharat_yatra` cluster).
* **APIs & Services:** Open-Meteo Weather API, Wikipedia & Wikimedia APIs, Geoapify GIS Places API.

---

## 🌐 4. API Endpoints Overview

| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/auth/register` | Register new user or admin account | Public |
| `POST` | `/api/auth/login` | Authenticate user or admin & return JWT token | Public |
| `GET` | `/api/auth/profile` | Get current user/admin profile | User / Admin |
| `GET` | `/api/destinations` | List all 112+ destinations with filters | Public |
| `GET` | `/api/destinations/:id` | Get detailed destination info with live weather | Public |
| `POST` | `/api/destinations` | Create new destination record | Admin Only |
| `POST` | `/api/destinations/ai-generate` | AI Auto-research & generate monument metadata | Admin Only |
| `DELETE` | `/api/destinations/:id` | Delete destination record *(Creator Only)* | Admin Only |
| `GET` | `/api/admin/users` | List all registered admin team accounts | Admin Only |
| `POST` | `/api/admin/users` | Register/Add a new admin team member | Admin Only |
| `DELETE` | `/api/admin/users/:id` | Delete admin team member *(Creator Only)* | Admin Only |
| `POST` | `/api/planner/generate` | Generate personalized day-wise AI itinerary | Public |
| `POST` | `/api/budget/calculate` | Calculate customized travel budget breakdown | Public |

---

## 📁 5. Project Structure

```
bharat-yatra/
├── server/
│   ├── controllers/       # authController, destinationController, plannerController, budgetController
│   ├── data/              # tourismData.js (112+ curated monuments dataset, cuisines, transport)
│   ├── middleware/        # auth.js (verifyToken, verifyAdmin)
│   ├── models/            # Admin.js, User.js, Destination.js, Itinerary.js, Review.js
│   ├── routes/            # apiRoutes.js
│   ├── services/          # destinationEnrichmentService, geoapifyService, wikimediaService
│   ├── seedDatabase.js    # Database seeder & synchronization script for 112 monuments
│   ├── server.js          # Express server entry point
│   ├── .env               # Environment configuration
│   └── package.json
├── client/
│   ├── src/
│   │   ├── components/    # Navbar, Footer, DestinationCard, InteractiveMap, HeroSection
│   │   ├── context/       # AuthContext (Traveler & Admin auth state, favorites)
│   │   ├── pages/         # Home, Explore, DestinationDetail, AIPlanner, BudgetCalculator,
│   │   │                  # CuisineGuide, TransportGuide, AdminDashboard, LoginRegister
│   │   ├── services/      # api.js (Axios API client with JWT interceptor & local fallbacks)
│   │   ├── App.jsx        # Routing and theme provider
│   │   └── index.css      # Indian heritage design system & custom gradients
│   ├── public/            # Monument static assets & favicons
│   ├── index.html
│   ├── vite.config.js
│   └── package.json
└── README.md
```

---

## 🚀 6. Getting Started & Installation

### 1. Prerequisites
* **Node.js (v18 or higher)**
* **MongoDB Atlas** account (or local MongoDB instance)
* **Git**

### 2. Clone the Repository
```bash
git clone https://github.com/ajitkumarsaini02/bharat-yatra.git
cd bharat-yatra
```

### 3. Server Setup & Configuration
```bash
cd server
npm install
```

Create a `.env` file in the `server` directory:
```env
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster1.mongodb.net/bharat_yatra?retryWrites=true&w=majority
JWT_SECRET=bharat_yatra_super_secret_key_2026
ADMIN_SECRET_KEY=bharat_admin_2026
```

Seed / Sync all 112 Monuments to MongoDB Atlas:
```bash
node seedDatabase.js
```

Start the Backend Server:
```bash
npm start
```
* Backend runs on: `http://localhost:5000`  
* Health status endpoint: `http://localhost:5000/api/health`

### 4. Client Setup
Open a new terminal window:
```bash
cd client
npm install
npm run dev
```
* Frontend runs on: `http://localhost:5173`

---

## 🔐 7. Authentication & Security Policies

### 🧳 Traveler (User) Account
* Register as **Traveler** to explore monuments, save favorite destinations to wishlist, and generate personalized AI itineraries.

### 🛡️ Administrator Account & Ownership Guard
* Register as **Admin** using the platform admin passcode (`bharat_admin_2026`).
* Admins access the **Administrator Control Center (`/admin`)**.
* **Strict Creator Ownership Policy:**
  1. **Destinations Deletion:** Only the admin who created a monument can delete it.
  2. **Admin Team Deletion:** An admin can add new admin team accounts. **Only the creator admin who added an admin can delete that admin.**

---

## 📄 License & Credits
Developed as an educational and cultural initiative to promote Indian heritage, tourism, and travel intelligence.
All rights reserved © 2026 Bharat Yatra Platform.
