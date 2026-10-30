# AgroLoop — Growing Smarter. Farming Stronger.

> Complete Full-Stack Smart Agriculture, Livestock & Farmer Livelihood Platform combining Sentinel-2 Satellite Earth Observation, Multimodal AI Foliar Diagnostics, Precision Agronomy, and Fair-Trade Commerce.

---

## 🌾 Project Overview

**AgroLoop** is an intelligent agricultural ecosystem designed to connect smallholder farmers, FPOs (Farmer Producer Organizations), agronomists, and veterinarians with actionable technology, satellite monitoring, and direct fair-price markets.

### Key Capabilities
- **Hyperlocal Agrometeorology & Space Intelligence**: Sentinel-2 10m Normalized Difference Vegetation Index (NDVI) heatmaps, 7-day agricultural forecasts, soil moisture sensors, and multilingual Voice/SMS alerts.
- **AI Crop Doctor**: Instant foliar pathology scanning for paddy, wheat, cotton, and vegetables with scientific chemical remedies, organic bio-control alternatives, and preventive guidelines.
- **Livestock Health & Reproduction**: Complete herd tagging, AI veterinary triage, smart immunization calendar, and species-specific gestation calculators (Cattle, Buffalo, Goat, Sheep, Swine).
- **Direct Farmer Marketplace**: Direct producer-to-buyer grain, pulse, and produce trading with live Mandi MSP comparison benchmarks and farm machinery rentals (0% commission).
- **Carbon Credit Estimator**: Environmental footprint quantification for regenerative farming practices (zero-tillage, biochar, cover cropping, and agroforestry).
- **Government Scheme Discovery**: Searchable central and state agricultural subsidies (PM-KISAN, PMFBY, PMKSY, SMAM, NLM, PKVY) with instant eligibility calculators and checklist of required documents.
- **Fertilizer Intelligence**: Precision NPK dosage calculation for Urea, DAP, MOP, Neem Cake, and biofertilizers with split application timelines.
- **Kisan Chaupal Community**: Discussion forums with image uploads, likes, comments, and community moderation.

---

## 🛠️ Architecture & Technology Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18, Vite 6, Tailwind CSS, React Router v6, Lucide React Icons |
| **Backend & Database** | Supabase, PostgreSQL 15, Row-Level Security (RLS) |
| **Authentication** | Supabase Auth (Phone OTP, Email/Password, and Instant Demo Mode) |
| **Storage** | Supabase Storage (Buckets: `profiles`, `farms`, `crop-diagnoses`, `livestock`, `marketplace`, `community`) |
| **Edge Functions** | Supabase Deno Edge Functions (`crop-doctor-ai`, `weather-advisory`) |
| **Hosting & CI/CD** | GitHub, Vercel, Supabase Cloud |

---

## 📂 Project Directory Structure

```text
AgriLoop2.O/
├── index.html
├── package.json
├── vite.config.js
├── tailwind.config.js
├── postcss.config.js
├── .env.example
├── .gitignore
├── public/
│   └── leaf-orbit.svg           # Green leaf logo with circular orbit
├── src/
│   ├── main.jsx                 # Application entry point
│   ├── App.jsx                  # Route definitions (19 modules)
│   ├── index.css                # Tailwind directives & styles
│   ├── context/
│   │   ├── AuthContext.jsx      # Supabase auth + Demo fallback
│   │   └── ToastContext.jsx     # Floating notifications
│   ├── components/
│   │   ├── common/              # LeafOrbitLogo, Badge, Modal, DemoBanner, Footer
│   │   └── navigation/          # Sidebar, TopNavbar, MobileBottomNav
│   ├── layouts/
│   │   ├── DashboardLayout.jsx  # Main application shell with sidebar & mobile nav
│   │   └── PublicLayout.jsx     # Public shell with landing navigation & footer
│   ├── pages/
│   │   ├── HomePage.jsx         # Modern landing page
│   │   ├── auth/                # RegisterPage, LoginPage
│   │   ├── onboarding/          # Multi-step Farm Onboarding Wizard
│   │   ├── dashboard/           # Main Farmer Dashboard
│   │   ├── farm/                # MyFarmPage (Plot management & crops)
│   │   ├── weather/             # Weather & Satellite Intelligence (NDVI)
│   │   ├── crops/               # AI Crop Doctor
│   │   ├── livestock/           # Herd Care, Calendar & Gestation Calculator
│   │   ├── veterinary/          # Veterinary Clinics Directory
│   │   ├── calendar/            # Smart Agricultural Calendar
│   │   ├── schemes/             # Government Scheme Finder & Eligibility
│   │   ├── carbon/              # Carbon Credit Estimator
│   │   ├── marketplace/         # Direct Produce Marketplace & Mandi Ticker
│   │   ├── community/           # Kisan Chaupal Community Forum
│   │   ├── fertilizers/         # Fertilizer Intelligence & Dosage Calculator
│   │   ├── subscription/        # Pricing Tiers & Checkout
│   │   ├── profile/             # Farmer Profile
│   │   └── settings/            # Settings, Sovereignty & JSON Data Export
│   ├── services/
│   │   ├── supabase.js          # Supabase client initializer
│   │   ├── authService.js
│   │   ├── farmService.js
│   │   ├── livestockService.js
│   │   ├── cropService.js
│   │   ├── weatherService.js
│   │   ├── fertilizerService.js
│   │   ├── schemeService.js
│   │   ├── marketplaceService.js
│   │   ├── communityService.js
│   │   ├── calendarService.js
│   │   ├── veterinaryService.js
│   │   ├── carbonService.js
│   │   ├── subscriptionService.js
│   │   └── storageService.js
│   └── utils/
│       └── constants.js         # Master crops, states, soils, demo records
└── supabase/
    ├── migrations/
    │   └── 20250101000000_agroloop_schema.sql  # 22 PostgreSQL tables + RLS
    ├── seed.sql                                # Seed schemes, fertilizers, clinics
    └── functions/
        ├── crop-doctor-ai/index.ts             # AI disease analysis Edge Function
        └── weather-advisory/index.ts           # Satellite NDVI Edge Function
```

---

## 🗄️ Database Architecture (22 PostgreSQL Tables)

All user-owned tables enforce PostgreSQL **Row-Level Security (RLS)**:

1. `profiles`: Farmer personal details, language, phone, village, KYC role.
2. `farms`: Farm acreage, GPS coordinates, soil type, irrigation layout.
3. `farm_crops`: Seasonal parcel rotations, sowing/harvest dates, vegetative stage.
4. `livestock`: Animal breed registry, identification tag ID, gender, weight, status.
5. `livestock_health_records`: Symptom logs, preliminary diagnoses, urgency ratings.
6. `livestock_pregnancies`: Breeding dates, sire details, ultrasound milestones.
7. `livestock_reminders`: Immunization, deworming, and medication due dates.
8. `farm_calendar_events`: Field operations (sowing, fertigation, pest scouting, harvest).
9. `crop_diagnoses`: AI disease scans, confidence %, chemical & organic remedies.
10. `weather_alerts`: Severe meteorological advisories, heatwaves, heavy rainfall.
11. `government_schemes`: PM-KISAN, PMFBY, SMAM, PMKSY directory and eligibility criteria.
12. `veterinary_clinics`: Government hospitals and mobile veterinary diagnostic clinics.
13. `fertilizer_products`: NPK ratios, biofertilizers, zinc sulphate usage guide.
14. `marketplace_listings`: Produce quantities, asking prices, harvest dates, seller contact.
15. `community_posts`: Farmer Chaupal questions, experience sharing, photo posts.
16. `community_comments`: Discussion threads.
17. `community_likes`: Post upvotes.
18. `community_reports`: Inappropriate content moderation flags.
19. `carbon_assessments`: tCO2e baseline emissions, soil sequestration, credit estimates.
20. `notifications`: Hyperlocal agromet alerts, buyer inquiries, reminder notices.
21. `subscription_plans`: Kisan Basic, Smart Farmer, AgroLoop Pro & FPO.
22. `user_subscriptions`: Entitlements, validity dates, billing cycles.

---

## 🚀 Getting Started Locally

### 1. Prerequisites
- **Node.js** (v18+ or v20+)
- **npm** (v9+)

### 2. Installation
```bash
# Clone or navigate to the project directory
cd AgriLoop2.O

# Install dependencies
npm install
```

### 3. Environment Configuration
Copy `.env.example` to `.env`:
```bash
cp .env.example .env
```

Edit `.env` with your Supabase credentials:
```env
VITE_SUPABASE_URL=https://your-project-id.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.your-anon-key
```
*(Note: If Supabase credentials are not yet set, AgroLoop automatically launches in **Interactive Demo Mode** pre-loaded with mock farm records, satellite NDVI telemetry, and AI foliar scans for zero-friction exploration).*

### 4. Running the Development Server
```bash
npm run dev
```
Open your browser at `http://localhost:3000`.

### 5. Production Build
```bash
npm run build
npm run preview
```

---

## ☁️ Deployment Guide

### Deploying the Database to Supabase
1. Create a new project at [supabase.com](https://supabase.com).
2. Open the **SQL Editor** in your Supabase project dashboard.
3. Paste and run `supabase/migrations/20250101000000_agroloop_schema.sql` to generate all 22 tables and RLS security policies.
4. Run `supabase/seed.sql` to populate government schemes, veterinary clinics, fertilizer compendiums, and subscription plans.
5. In **Storage**, create public buckets for `profiles`, `farms`, `crop-diagnoses`, `livestock`, and `marketplace`.

### Deploying Frontend to Vercel
1. Push your repository to **GitHub**:
   ```bash
   git init
   git add .
   git commit -m "feat: complete AgroLoop smart agriculture platform"
   git branch -M main
   git remote add origin https://github.com/your-username/agroloop.git
   git push -u origin main
   ```
2. Go to [vercel.com](https://vercel.com) and click **"Add New Project"**.
3. Select your GitHub repository.
4. Add the following environment variables in the Vercel project settings:
   - `VITE_SUPABASE_URL`: Your Supabase project URL
   - `VITE_SUPABASE_ANON_KEY`: Your Supabase anonymous client key
5. Click **Deploy**. Vercel will build and deploy your site with global edge CDN distribution.

---

## 🔒 Security & Privacy Notice
- Frontend environment variables only store public/anonymous Supabase keys.
- Sensitive AI provider keys (Gemini API) and commercial weather tokens are strictly confined to Supabase Edge Functions.
- All diagnoses and gestation calculators carry statutory advisories emphasizing that AI recommendations are preliminary screening tools that should be verified with local Krishi Vigyan Kendra (KVK) agronomists or registered veterinarians.

---

## 📄 License
AgroLoop is licensed under the MIT License. Built for the agricultural prosperity and livelihood resilience of farmers worldwide.

