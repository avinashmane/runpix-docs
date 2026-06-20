# Run-Pix User Guide

<img src="images/logo.png" alt="Run-Pix" width="100"/> <span style="font-size: '2 rem';"> Run-PiX <small> AI based race management from your mobile</small></span>

## Table of Contents

1. [Getting Started](#getting-started)
2. [User Roles](#user-roles)
3. [Race Management](#race-management)
4. [Photo Management](#photo-management)
5. [Results & Certificates](#results--certificates)
6. [Mobile Features](#mobile-features)

---

## Getting Started

### Registration & Login

1. **Access the App**: Visit [https://run-pix.web.app](https://run-pix.web.app)
2. **Login Options**:
   - Google Sign-In (Recommended)
   - Email/Password authentication
3. **First Time Setup**:
   - Complete your profile
   - Set your display name
   - Upload profile picture (optional)

### Dashboard Overview

After logging in, you'll see:
- **Home**: List of upcoming and past races
- **My Races**: Races you're managing or participating in
- **Photos**: Search and view race photos
- **Results**: View race results and certificates
- **Profile**: Manage your account settings

---

## User Roles

### Participant
- Search for race photos by BIB number
- View race results
- Download finisher certificates
- Share photos on social media

### Race Organizer
- Create and manage races
- Record race timings
- Upload and manage photos
- Generate results
- Create custom certificates

### Administrator
- Full system access
- Manage all races
- User management
- System configuration

---

## Race Management

### Creating a New Race

1. Navigate to **Races** → **Create New Race**
2. Fill in race details:
   - **Race Name**: Official name of the event
   - **Date**: Event date
   - **Location**: Venue/City
   - **Distances**: Available race categories (e.g., 5K, 10K, Half Marathon)
   - **Waypoints**: Timing points (e.g., START, 5K, FINISH)
   - **Organization**: Organizing body
   - **Links**: Website, registration, results URLs

3. **Race Status Options**:
   - `planned`: Race is scheduled but not started
   - `started`: Race is currently in progress
   - `stopped`: Race timing has ended
   - `provisional`: Preliminary results available
   - `final`: Official results published
   - `nolist`: Results not publicly listed

### Managing Race Information

#### Edit Mode
1. Click on race card
2. Toggle **Edit** button
3. Modify race details
4. Click **Save Changes**

#### Flag Off (Race Start)
1. Enter Edit mode
2. Click **Flag Off** button
3. Confirms race start time
4. Records timestamp in database

### Recording Race Timings

#### Using Camera Mode
1. Navigate to race page
2. Select **Camera** or **Video Recording**
3. Enter BIB number
4. Select distance category
5. Tap to record timing
6. System automatically timestamps entry

#### Manual Entry
1. Go to **Race Log**
2. Enter BIB number
3. Select waypoint
4. System records current time
5. Review and validate entries

---

## Photo Management

### Uploading Photos

#### Bulk Upload
1. Navigate to race → **Photos**
2. Click **Upload Photos**
3. Select multiple images
4. System processes and generates thumbnails
5. Photos are automatically organized by BIB number (if detected)

#### Face Recognition Setup
1. Enable face search in race settings
2. Upload cropped face images
3. System builds face database
4. Participants can search by uploading their photo

### Searching for Photos

#### By BIB Number
1. Go to **Photos** page
2. Enter your BIB number
3. Click **Search**
4. View all photos with your BIB

#### By Face Recognition
1. Upload a cropped face photo
2. System matches against database
3. Returns photos with matching faces
4. Download or share directly

### Photo Status Flags
- `face`: Face recognition enabled
- `faceonly`: Only face search available (no BIB search)
- `avail`: Photos available for viewing

---

## Results & Certificates

### Viewing Results

1. Navigate to **Results** page
2. Select race from list
3. View results by:
   - Overall rankings
   - Category rankings
   - Gender rankings
   - Age group rankings

### Result Information Displayed
- BIB Number
- Participant Name
- Finish Time
- Category
- Rank (Overall/Category)
- Pace
- Strava Activity Link (if available)

### Downloading Certificates

#### Finisher Certificate
1. Go to race results
2. Find your BIB number
3. Click **Certificate** button
4. Certificate generates with:
   - Your name
   - Race details
   - Finish time
   - Category rank
   - Custom race logo/design

#### Certificate Templates
Race organizers can create custom templates with:
- Dynamic fields: `{Name}`, `{Time}`, `{Rank}`, `{Category}`
- Custom images: `{logo_img_url}`, `{sponsor_img_url}`
- Race-specific branding

---

## Mobile Features

### Camera Integration
- Real-time BIB number capture
- Video recording for continuous timing
- Automatic timestamp recording
- Offline capability with sync

### Geolocation
- Automatic waypoint detection
- GPS-based timing validation
- Location-based photo tagging

### Offline Mode
- Record timings without internet
- Auto-sync when connection restored
- Local data storage

---

## Tips & Best Practices

### For Participants
- Register early to ensure BIB number is in system
- Keep your BIB visible in photos
- Check results within 24 hours of race
- Download certificates promptly

### For Race Organizers
- Test timing system before race day
- Have backup devices ready
- Upload start list before race
- Process photos within 48 hours
- Verify results before marking as "final"

### Photo Quality
- Ensure good lighting
- Keep BIB numbers visible and unobstructed
- Use landscape orientation for group photos
- Minimum resolution: 1920x1080

---

## Troubleshooting

### Can't Find Photos
- Verify BIB number is correct
- Check if photos are marked as "available"
- Try face search if enabled
- Contact race organizer

### Login Issues
- Clear browser cache
- Try incognito/private mode
- Use Google Sign-In
- Reset password if needed

### Certificate Not Generating
- Ensure race status is "final" or "provisional"
- Verify your BIB number in results
- Check if certificates are enabled for the race
- Contact race organizer

---

## Support

### Getting Help
- **Documentation**: [https://avinashmane.github.io/runpix-docs/](https://avinashmane.github.io/runpix-docs/)
- **Feature Requests**: [GitHub Discussions](https://github.com/avinashmane/runpix/discussions)
- **Bug Reports**: [GitHub Issues](https://github.com/avinashmane/runpix/issues)
- **Contact**: [Avinash Mane](https://avinashmane.github.io/)

---

[Back to Index](/runpix-docs/) | [Technical Documentation](technical-guide.md)