# Run-Pix Technical Documentation

<img src="images/logo.png" alt="Run-Pix" width="100"/> <span style="font-size: '2 rem';"> Run-PiX <small> AI based race management from your mobile</small></span>

## Table of Contents

1. [Architecture Overview](#architecture-overview)
2. [Technology Stack](#technology-stack)
3. [Project Structure](#project-structure)
4. [Development Setup](#development-setup)
5. [Theming System](#theming-system)
6. [API Reference](#api-reference)
7. [Deployment](#deployment)

---

## Architecture Overview

Run-Pix is a modern web application built with Vue.js 3 and Firebase, designed for AI-powered race management.

### System Components

```
┌─────────────────┐
│   Vue.js App    │ ← Frontend (Vite + Vue 3)
│  (run-pix.web)  │
└────────┬────────┘
         │
         ├─────────────────────────────────┐
         │                                 │
┌────────▼────────┐              ┌────────▼────────┐
│  Firebase Auth  │              │   Firestore DB  │
│  (Google OAuth) │              │   (NoSQL)       │
└─────────────────┘              └─────────────────┘
         │                                 │
         └─────────────┬───────────────────┘
                       │
              ┌────────▼────────┐
              │ Cloud Functions │
              │  (Node.js API)  │
              └────────┬────────┘
                       │
         ┌─────────────┼─────────────┐
         │             │             │
┌────────▼────┐ ┌─────▼──────┐ ┌───▼────────┐
│   Storage   │ │  AI/ML     │ │  Admin     │
│  (Images)   │ │  Services  │ │  (Python)  │
└─────────────┘ └────────────┘ └────────────┘
```

### Key Features
- **Real-time Updates**: Firestore real-time database
- **AI-Powered**: Face recognition and OCR for BIB detection
- **Serverless**: Cloud Functions for backend processing
- **Scalable**: Firebase infrastructure
- **Mobile-First**: Responsive design with PWA capabilities

---

## Technology Stack

### Frontend
- **Framework**: Vue.js 3.4.10 (Composition API)
- **Build Tool**: Vite 5.4.8
- **UI Library**: PrimeVue 4.1.0
- **Styling**: 
  - Tailwind CSS 3.4.1
  - PrimeVue Themes (Aura preset)
- **State Management**: 
  - Pinia 2.1.7 (primary)
  - Vuex 4.1.0 (legacy support)
- **Routing**: Vue Router 4.2.5
- **Date Handling**: Day.js 1.11.13
- **Utilities**: Lodash-es 4.17.21

### Backend
- **Platform**: Firebase (Google Cloud)
- **Authentication**: Firebase Auth + Google OAuth
- **Database**: Cloud Firestore (NoSQL)
- **Storage**: Cloud Storage
- **Functions**: Cloud Functions (Node.js)
- **Hosting**: Firebase Hosting

### AI/ML Services
- **OCR**: Tesseract.js 7.0.0
- **Face Recognition**: Custom Python service (runpix-face)
- **Image Processing**: Cloud Functions + Python admin service

### Development Tools
- **Testing**: 
  - Mocha 10.4.0
  - Chai 5.1.1
  - Cucumber 10.9.0
- **Linting**: ESLint 8.56.0
- **Code Quality**: NYC (coverage)

---

## Project Structure

```
runpix/
├── src/
│   ├── api/              # API integration layer
│   ├── assets/           # Static assets (images, fonts)
│   ├── components/       # Vue components
│   │   ├── BackButton.vue
│   │   ├── Camera.vue
│   │   ├── CameraVideo.vue
│   │   ├── LoginCard.vue
│   │   ├── ProfileCard.vue
│   │   ├── RaceCard.vue
│   │   ├── RaceInfoPanel.vue
│   │   ├── RegisterCard.vue
│   │   ├── ResultCard.vue
│   │   └── ...
│   ├── helpers/          # Utility functions
│   │   ├── dayjs.js
│   │   ├── file-uploader.js
│   │   └── index.js
│   ├── pages/            # Page components (routes)
│   │   ├── HomePage.vue
│   │   ├── LoginPage.vue
│   │   ├── PhotosPage.vue
│   │   ├── ProfilePage.vue
│   │   ├── RaceEntry.vue
│   │   ├── RaceForm.vue
│   │   ├── ResultsPage.vue
│   │   └── ...
│   ├── router/           # Vue Router configuration
│   ├── stores/           # Pinia stores
│   ├── store_vuex/       # Legacy Vuex stores
│   ├── App.vue           # Root component
│   ├── main.js           # Application entry point
│   ├── config.js         # App configuration
│   ├── theme.js          # PrimeVue theme configuration
│   ├── style.css         # Global styles
│   └── index.css         # Tailwind imports
├── functions/            # Firebase Cloud Functions
│   ├── express.js        # Express server
│   ├── imageocr.js       # OCR processing
│   ├── imageProcessing.js
│   ├── races.js          # Race management
│   ├── raceTiming.js     # Timing logic
│   ├── videoocr.js       # Video OCR
│   └── test/             # Function tests
├── public/               # Public static files
├── docs/                 # Documentation
├── firebase/             # Firebase configuration
├── test/                 # E2E tests
├── .env.example          # Environment template
├── firebase.json         # Firebase config
├── package.json          # Dependencies
├── tailwind.config.js    # Tailwind configuration
└── vite.config.js        # Vite configuration
```

---

## Development Setup

### Prerequisites
- Node.js 18+ 
- npm or pnpm
- Firebase CLI
- Git

### Installation

1. **Clone Repository**
```bash
git clone https://github.com/avinashmane/runpix.git
cd runpix
```

2. **Install Dependencies**
```bash
pnpm install
# or
npm install
```

3. **Configure Environment**
```bash
cp .env.example .env
```

Edit `.env` with your Firebase credentials:
```env
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

4. **Start Development Server**
```bash
pnpm dev
# or
npm run dev
```

Access at: `http://localhost:5173`

### Available Scripts

```bash
# Development
pnpm dev              # Start dev server
pnpm build            # Build for production
pnpm serve            # Preview production build

# Firebase
pnpm deploy-hosting   # Deploy frontend
pnpm deploy-functions # Deploy cloud functions
pnpm func-serve       # Test functions locally

# Testing
pnpm test:unit        # Run unit tests
pnpm test:e2e         # Run E2E tests
pnpm coverage         # Generate coverage report

# Functions
pnpm express          # Run Express server locally
```

---

## Theming System

### Dark/Light Mode Support

Run-Pix implements a comprehensive theming system supporting both light and dark modes.

#### Theme Configuration

**PrimeVue Theme** (`src/theme.js`):
```javascript
import Aura from '@primevue/themes/aura';
import { definePreset } from '@primevue/themes';

export const MyPreset = definePreset(Aura, {
    semantic: {
        primary: {
            50: '{indigo.50}',
            // ... color scale
            950: '{indigo.950}'
        },
        colorScheme: {
            light: {
                formField: {
                    hoverBorderColor: '{primary.color}'
                }
            },
            dark: {
                formField: {
                    hoverBorderColor: '{primary.color}'
                }
            }
        }
    }
});
```

#### Tailwind Dark Mode

**Configuration** (`tailwind.config.js`):
```javascript
module.exports = {
  darkMode: 'media', // Uses prefers-color-scheme
  theme: {
    extend: {
      colors: {
        gray: {
          900: '#202225',
          800: '#2f3136',
          // ... custom grays
        }
      }
    }
  }
}
```

#### CSS Variables Approach

**Global Styles** (`src/style.css`):
```css
:root {
  /* Light mode (default) */
  color: #213547;
  background-color: #ffffff;
}

@media (prefers-color-scheme: dark) {
  :root {
    color: rgba(255, 255, 255, 0.87);
    background-color: #242424;
  }
}
```

#### Component-Level Dark Mode

Use Tailwind's `dark:` variant:
```vue
<template>
  <div class="bg-white dark:bg-slate-800">
    <button class="bg-blue-500 dark:bg-blue-700 
                   hover:bg-blue-400 dark:hover:bg-blue-600">
      Click Me
    </button>
  </div>
</template>
```

#### Best Practices

1. **Always provide dark variants** for:
   - Background colors (`bg-*`)
   - Text colors (`text-*`)
   - Border colors (`border-*`)
   - Hover states

2. **Use semantic color scales**:
   - Light mode: `slate-50` to `slate-200`
   - Dark mode: `slate-700` to `slate-900`

3. **Test both themes** during development

4. **Avoid hardcoded colors** - use Tailwind classes

---

## API Reference

### Firebase Collections

#### `/races/{raceId}`
```javascript
{
  id: string,
  Name: string,
  Date: string,
  Location: string,
  Distances: string[],
  Waypoints: string[],
  status: string[],
  photoStatus: string[],
  linkOrg: string,
  linkPhotos: string,
  linkResults: string,
  coverPage: string,
  timestamp: {
    create: ISO8601,
    modify: ISO8601,
    start: ISO8601
  }
}
```

#### `/races/{raceId}/readings/{readingId}`
```javascript
{
  timestamp: ISO8601,
  bib: string,
  waypoint: string,
  distance: string,
  userId: string,
  status: 'valid' | 'invalid'
}
```

#### `/races/{raceId}/results/{bibNumber}`
```javascript
{
  bib: string,
  Name: string,
  Category: string,
  Time: string,
  Rank: number,
  CategoryRank: number,
  activity: string // Strava ID
}
```

### Cloud Functions

#### Image Processing
```
POST /api/processImages
Body: { raceId: string, images: File[] }
```

#### OCR Processing
```
POST /api/scanImages
Body: { raceId: string, imageUrl: string }
```

#### Results Generation
```
POST /api/generateResults
Body: { raceId: string }
```

---

## Deployment

### Production Build

```bash
# Build frontend
pnpm build

# Deploy to Firebase
firebase deploy --only hosting

# Deploy functions
firebase deploy --only functions
```

### Environment Variables

Production environment variables are managed in Firebase:
```bash
firebase functions:config:set app.key="value"
```

### CI/CD

GitHub Actions workflow (`.github/workflows/deploy.yml`):
```yaml
name: Deploy to Firebase
on:
  push:
    branches: [ main ]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm ci && npm run build
      - uses: FirebaseExtended/action-hosting-deploy@v0
```

---

## Contributing

### Code Style
- Use ESLint configuration
- Follow Vue.js style guide
- Write meaningful commit messages
- Add tests for new features

### Pull Request Process
1. Fork the repository
2. Create feature branch
3. Make changes with tests
4. Submit PR with description

---

## Resources

- **Live App**: [https://run-pix.web.app](https://run-pix.web.app)
- **Documentation**: [https://avinashmane.github.io/runpix-docs/](https://avinashmane.github.io/runpix-docs/)
- **GitHub**: [https://github.com/avinashmane/runpix](https://github.com/avinashmane/runpix)
- **Wiki**: [https://github.com/avinashmane/runpix/wiki](https://github.com/avinashmane/runpix/wiki)

---

[Back to Index](/runpix-docs/) | [User Guide](user-guide.md)