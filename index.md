# Run-Pix Project

<img src="images/logo.png" alt="Run-Pix" width="100"/> <span style="font-size: '2 rem';"> <small> AI based race management from your mobile</small></span>

## Welcome to Run-Pix Documentation

Run-Pix is an AI-powered race management system that helps race organizers manage events, track timings, process photos, and generate results - all from a mobile device.

---

## Quick Links

### 📱 Application
- **Live App**: [https://run-pix.web.app](https://run-pix.web.app)
- **Admin Panel**: [run-pix-admin](https://run-pix-admin-nqmxzlpvyq-uc.a.run.app)
- **Face Recognition Service**: [runpix-face](https://runpix-face-nqmxzlpvyq-uc.a.run.app)

### 📚 Documentation

#### For Users
- **[User Guide](/runpix-docs/user-guide)** - Complete guide for participants and race organizers
- **[How-To Guide](/runpix-docs/howto)** - Quick tutorials and common tasks
- **[Races](/runpix-docs/races)** - Race management features

#### For Developers
- **[Technical Guide](/runpix-docs/technical-guide)** - Architecture, setup, and development
- **[Design Documentation](/runpix-docs/design)** - System design and architecture
- **[Overview](/runpix-docs/overview)** - High-level system overview

#### Project Management
- **[Release Notes & To-Dos](/runpix-docs/todo)** - Current status and roadmap
- **[GitHub Wiki](https://github.com/avinashmane/runpix/wiki)** - Additional documentation
- **[Feature Requests](https://github.com/avinashmane/runpix/discussions)** - Suggest new features

---

## Key Features

### 🏃 Race Management
- Create and manage multiple races
- Real-time timing with mobile camera
- Multiple distance categories
- Waypoint-based timing
- Start list management

### 📸 Photo Management
- AI-powered BIB number detection
- Face recognition search
- Bulk photo upload
- Automatic photo organization
- Social media sharing

### 🏆 Results & Certificates
- Automatic result generation
- Category-wise rankings
- Custom certificate templates
- Strava integration
- Downloadable certificates

### 📱 Mobile-First Design
- Responsive interface
- Camera integration
- Offline capability
- GPS tracking
- Progressive Web App (PWA)

---

## Getting Started

### For Participants
1. Visit [run-pix.web.app](https://run-pix.web.app)
2. Sign in with Google
3. Search for your race photos by BIB number
4. View results and download certificates

### For Race Organizers
1. Register and request organizer access
2. Create your race event
3. Upload start list
4. Record timings during race
5. Upload photos and generate results

### For Developers
1. Clone the repository
2. Install dependencies: `pnpm install`
3. Configure Firebase credentials
4. Start development: `pnpm dev`

See [Technical Guide](/runpix-docs/technical-guide) for detailed setup instructions.

---

## Technology Stack

- **Frontend**: Vue.js 3, Vite, Tailwind CSS, PrimeVue
- **Backend**: Firebase (Auth, Firestore, Storage, Functions)
- **AI/ML**: Tesseract.js (OCR), Custom face recognition
- **State Management**: Pinia, Vuex
- **Testing**: Mocha, Chai, Cucumber

---

## System Architecture

```
┌─────────────────┐
│   Vue.js App    │ ← Web Interface
└────────┬────────┘
         │
    ┌────┴────┐
    │ Firebase │
    │  Suite   │
    └────┬────┘
         │
    ┌────┴────────────────┐
    │                     │
┌───▼────┐         ┌─────▼──────┐
│ Cloud  │         │  AI/ML     │
│Functions│         │  Services  │
└────────┘         └────────────┘
```

See [Overview](/runpix-docs/overview) for detailed architecture.

---

## Support & Community

### Get Help
- **Documentation**: Browse guides above
- **GitHub Issues**: [Report bugs](https://github.com/avinashmane/runpix/issues)
- **Discussions**: [Ask questions](https://github.com/avinashmane/runpix/discussions)

### Contributing
We welcome contributions! See our [Technical Guide](/runpix-docs/technical-guide) for development setup.

### Contact
- **Developer**: [Avinash Mane](https://avinashmane.github.io/)
- **GitHub**: [avinashmane/runpix](https://github.com/avinashmane/runpix)

---

## Recent Updates

### Version 1.2.3
- ✅ Fixed dark/light theme inconsistencies
- ✅ Improved mobile camera integration
- ✅ Enhanced face recognition accuracy
- ✅ Updated PrimeVue to 4.1.0
- ✅ Added comprehensive documentation

See [Release Notes](/runpix-docs/todo) for complete changelog.

---

## Quick Navigation

| Category | Links |
|----------|-------|
| **User Docs** | [User Guide](/runpix-docs/user-guide) • [How-To](/runpix-docs/howto) • [Races](/runpix-docs/races) |
| **Developer Docs** | [Technical Guide](/runpix-docs/technical-guide) • [Design](/runpix-docs/design) • [Overview](/runpix-docs/overview) |
| **Project** | [To-Dos](/runpix-docs/todo) • [Wiki](https://github.com/avinashmane/runpix/wiki) • [Discussions](https://github.com/avinashmane/runpix/discussions) |

---

**Bookmark this page**: [https://avinashmane.github.io/runpix-docs/](https://avinashmane.github.io/runpix-docs/)

---

*Last Updated: June 2026*
