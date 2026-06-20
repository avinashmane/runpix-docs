# Run-Pix How-To Guide

<img src="images/logo.png" alt="Run-Pix" width="100"/> <span style="font-size: '2 rem';"> Run-PiX <small> AI based race management from your mobile</small></span>

## Quick Start Guides

### For Participants

#### How to Find Your Race Photos

1. **Navigate to Photos Page**
   - Go to [run-pix.web.app](https://run-pix.web.app)
   - Click on **Photos** in the navigation menu
   - Select your race from the dropdown

2. **Search by BIB Number**
   - Enter your BIB number in the search box
   - Click the search icon 🔍
   - Browse through your photos
   - Click on any photo to view full size
   - Use the share button to post on social media

3. **Search by Face (if enabled)**
   - Click **Upload Face Photo** button
   - Upload a cropped photo of your face
   - System will find all photos with matching faces
   - Download or share your photos

#### How to View Your Results

1. Go to **Results** page
2. Select your race
3. Find your BIB number in the list
4. View your:
   - Finish time
   - Overall rank
   - Category rank
   - Pace per kilometer

#### How to Download Your Certificate

1. Navigate to **Results** page
2. Find your BIB number
3. Click **Certificate** button
4. Certificate will open in new tab
5. Right-click and **Save As** or print directly

---

### For Race Organizers

#### How to Create a New Race

1. **Login as Organizer**
   - Sign in with your organizer account
   - Navigate to **Races** page

2. **Fill Race Details**
   ```
   Race Name: Mumbai Marathon 2024
   Date: 2024-01-21
   Location: Mumbai, Maharashtra
   Distances: 5K, 10K, 21K, 42K
   Waypoints: START, 5K, 10K, 15K, 21K, FINISH
   Organization: Mumbai Runners Club
   ```

3. **Add Links**
   - Registration URL
   - Organization website
   - Results page (can be added later)

4. **Set Status**
   - Start with `planned`
   - Change to `started` on race day
   - Update to `provisional` when results ready
   - Mark as `final` after verification

5. **Save Race**
   - Click **Save Changes**
   - Race is now visible to participants

#### How to Upload Start List

1. **Prepare CSV File**
   ```csv
   BIB,Name,Category,Distance
   101,John Doe,M-30-39,10K
   102,Jane Smith,F-40-49,5K
   103,Bob Johnson,M-50-59,21K
   ```

2. **Upload to Firestore**
   - Use Firebase Console or Admin API
   - Collection: `/races/{raceId}/startlist`
   - Each row becomes a document

3. **Verify Upload**
   - Check race page
   - Ensure all participants visible
   - Correct any errors before race day

#### How to Record Race Timings

**Method 1: Camera Mode (Recommended)**

1. **Setup**
   - Open race page on mobile
   - Click **Camera** button
   - Allow camera permissions

2. **During Race**
   - Position yourself at waypoint
   - As runner passes, enter their BIB number
   - Select distance category
   - Tap record button
   - System captures timestamp automatically

3. **Tips**
   - Have backup device ready
   - Test before race starts
   - Keep device charged
   - Use good lighting

**Method 2: Video Recording**

1. Click **Video Recording** mode
2. Start recording before first runner
3. Call out BIB numbers as runners pass
4. Stop recording after last runner
5. System processes video and extracts timings

**Method 3: Manual Entry**

1. Go to **Race Log** page
2. Enter BIB number
3. Select waypoint
4. Click **Record**
5. System uses current time

#### How to Upload Race Photos

1. **Prepare Photos**
   - Ensure good quality (min 1920x1080)
   - BIB numbers should be visible
   - Rename files if needed (optional)

2. **Bulk Upload**
   - Navigate to race → **Photos**
   - Click **Upload Photos**
   - Select multiple files (Ctrl+Click or Cmd+Click)
   - Wait for upload to complete

3. **Enable Photo Search**
   - Go to race settings
   - Set `photoStatus` to `"face,available"` or `"available"`
   - Save changes

4. **Verify Upload**
   - Check a few photos are visible
   - Test BIB number search
   - Test face search (if enabled)

#### How to Generate Results

1. **Verify Data**
   - Check all timings recorded
   - Verify start list complete
   - Review any flagged entries

2. **Generate Results**
   - Go to race page
   - Click **Generate Results**
   - System processes all timings
   - Calculates ranks and categories

3. **Review Results**
   - Check for anomalies
   - Verify top finishers
   - Look for missing entries

4. **Publish Results**
   - Set race status to `provisional`
   - Announce to participants
   - After verification, set to `final`

#### How to Create Custom Certificates

1. **Design Template**
   - Create certificate design (PNG/JPG)
   - Use placeholders for dynamic content:
     - `{Name}` - Participant name
     - `{Time}` - Finish time
     - `{Rank}` - Overall rank
     - `{Category}` - Category name
     - `{CategoryRank}` - Category rank
     - `{Distance}` - Race distance
     - `{Date}` - Race date
     - `{logo_img_url}` - Logo image URL

2. **Upload Template**
   - Go to race settings
   - Upload certificate template
   - Configure field positions

3. **Test Certificate**
   - Generate sample certificate
   - Verify all fields display correctly
   - Adjust positions if needed

4. **Enable for Race**
   - Set `certificate.finisherCertificate` to `true`
   - Participants can now download

---

## Common Tasks

### How to Enable Face Search

1. **Configure Race**
   ```javascript
   photoStatus: ["face", "available"]
   ```

2. **Build Face Database**
   - Participants upload face photos
   - System processes and stores face embeddings
   - Database builds automatically

3. **Test Search**
   - Upload test face photo
   - Verify matching works
   - Adjust confidence threshold if needed

### How to Handle Timing Corrections

1. **Identify Issue**
   - Check race log
   - Find incorrect entry

2. **Manual Correction**
   - Go to Firebase Console
   - Navigate to `/races/{raceId}/readings`
   - Find reading document
   - Edit timestamp or mark as invalid

3. **Regenerate Results**
   - Click **Generate Results** again
   - System recalculates with corrections

### How to Export Results

1. **From Firebase Console**
   - Go to Firestore
   - Navigate to `/races/{raceId}/results`
   - Export collection as JSON

2. **Convert to CSV**
   - Use online JSON to CSV converter
   - Or use script:
   ```javascript
   const results = await db.collection('races')
     .doc(raceId).collection('results').get();
   const csv = results.docs.map(doc => doc.data());
   ```

### How to Integrate with Strava

1. **Get Strava Activity IDs**
   - Participants provide their activity IDs
   - Or use Strava API to fetch

2. **Add to Results**
   ```javascript
   {
     bib: "101",
     activity: "1234567890" // Strava activity ID
   }
   ```

3. **Display in Results**
   - System automatically creates links
   - Participants can click to view on Strava

---

## Troubleshooting

### Photos Not Showing

**Problem**: Uploaded photos don't appear

**Solutions**:
1. Check `photoStatus` includes `"available"`
2. Verify photos uploaded to correct path
3. Check file permissions in Storage
4. Clear browser cache

### BIB Number Not Detected

**Problem**: OCR not finding BIB numbers

**Solutions**:
1. Ensure BIB is clearly visible
2. Check photo quality and lighting
3. Try manual tagging
4. Adjust OCR confidence threshold

### Timing Discrepancies

**Problem**: Times don't match manual records

**Solutions**:
1. Check device time synchronization
2. Verify waypoint selection
3. Review race log for duplicates
4. Check for timezone issues

### Certificate Not Generating

**Problem**: Certificate download fails

**Solutions**:
1. Verify race status is `final` or `provisional`
2. Check certificate template exists
3. Ensure BIB number in results
4. Check browser console for errors

---

## Advanced Features

### Video OCR Processing

1. Record video of finish line
2. Upload to Cloud Storage
3. Run video OCR function
4. System extracts BIB numbers and timestamps
5. Review and validate results

### Batch Operations

**Bulk BIB Assignment**:
```javascript
const batch = db.batch();
participants.forEach(p => {
  const ref = db.collection('races').doc(raceId)
    .collection('startlist').doc(p.bib);
  batch.set(ref, p);
});
await batch.commit();
```

### Custom Webhooks

Configure webhooks for:
- New photo uploads
- Result generation
- Certificate downloads
- Timing updates

---

## Testing

### Test Setup

For testing, use:
- Email: `avinashmane@yahoo.com` (with test admin user)
- Test race ID: Create in development environment
- Sample photos: Use provided test images

### Test Checklist

- [ ] User registration and login
- [ ] Race creation
- [ ] Photo upload
- [ ] BIB search
- [ ] Face search
- [ ] Timing recording
- [ ] Result generation
- [ ] Certificate download
- [ ] Mobile responsiveness
- [ ] Dark/light theme

---

## Database Schema Reference

### Race Document
```javascript
/races/{raceId}
{
  Name: string,
  Date: string,
  Location: string,
  Distances: string[],
  Waypoints: string[],
  status: string[],
  photoStatus: string[],
  timestamp: {
    create: ISO8601,
    modify: ISO8601,
    start: ISO8601
  }
}
```

### Reading Document
```javascript
/races/{raceId}/readings/{readingId}
{
  timestamp: ISO8601,
  bib: string,
  waypoint: string,
  distance: string,
  userId: string,
  status: 'valid' | 'invalid'
}
```

### Result Document
```javascript
/races/{raceId}/results/{bibNumber}
{
  bib: string,
  Name: string,
  Category: string,
  Time: string,
  Rank: number,
  CategoryRank: number
}
```

---

## Best Practices

### For Organizers

1. **Before Race Day**
   - Test all equipment
   - Upload complete start list
   - Brief timing volunteers
   - Have backup devices

2. **During Race**
   - Start timing early
   - Record all waypoints
   - Monitor for issues
   - Keep devices charged

3. **After Race**
   - Upload photos within 24 hours
   - Generate provisional results
   - Review and verify
   - Publish final results

### For Developers

1. **Code Quality**
   - Follow ESLint rules
   - Write unit tests
   - Document functions
   - Use TypeScript types

2. **Performance**
   - Optimize images
   - Lazy load components
   - Use pagination
   - Cache API calls

3. **Security**
   - Validate all inputs
   - Use Firebase rules
   - Sanitize user data
   - Implement rate limiting

---

## Support

Need help? Check:
- [User Guide](user-guide.md) - Comprehensive documentation
- [Technical Guide](technical-guide.md) - Developer documentation
- [GitHub Issues](https://github.com/avinashmane/runpix/issues) - Report bugs
- [Discussions](https://github.com/avinashmane/runpix/discussions) - Ask questions

---

[Back to Index](/runpix-docs/)