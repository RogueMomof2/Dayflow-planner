# Dayflow — iPhone Life Planner

## Included
- Dark, modern mobile-first planner
- Daily checklist and scheduled tasks with one-time, daily, weekday, or weekly labels
- Home/family checklist
- Weekly meal planner
- USD manual budget and expense categories
- Habit tracker and notes
- Saves information locally in the browser on this device using localStorage
- Calendar export (`.ics`) that can be imported into Apple Calendar
- Basic offline caching after first load

## Important limitations in this first deliverable
- This is a Progressive Web App (PWA), not an App Store app.
- **Notifications are not implemented in this build yet.** iOS web push requires an installed Home Screen web app, permission, a secure HTTPS origin, and a push service/backend for dependable scheduled push notifications. Browser-local reminders are not dependable while the app is closed.
- Calendar export is one-way: tasks can be exported into Apple Calendar, but edits do not sync back automatically.
- Data is local to this browser installation. Clearing Safari website data can erase it. It does not sync across devices or connect to bank accounts.
- Recurrence labels are saved, but automatic creation/reset of recurring task instances is not implemented in this initial build.
- No passcode/encryption layer is included. Use the device passcode and avoid storing highly sensitive financial details.

## Easiest iPhone installation
A PWA must be served from an HTTPS website to install reliably and use service workers. Opening `index.html` as a local file is for preview only and will not enable all features.

1. Upload the contents of this folder to a static HTTPS host you control (for example, a private repository with a static hosting service).
2. Open the resulting HTTPS URL in Safari on your iPhone.
3. Tap Share, then **Add to Home Screen**. If prompted, choose to open as a web app.
4. Launch Dayflow from the new Home Screen icon. Add a test task and refresh/reopen to confirm local persistence.
5. In Schedule, tap **Export calendar (.ics)**, then open the downloaded calendar file and follow iOS prompts to add events to Calendar.

## Private data
Task, meal, budget, habit and note data are stored in this browser's localStorage. It is not sent to a server by this code. Hosting the static app serves the app files but does not upload the planner data. Anyone with access to the unlocked browser profile may be able to view the data.

## Updating the app
Replace `index.html`, `manifest.webmanifest`, `sw.js`, and icons on the host. If caching serves an older version, change the cache name in `sw.js` (e.g. `dayflow-static-v2`) and reload the app.

## Recommended next engineering milestone
Implement robust recurring task instances, JSON backup/restore, configurable reminder schedules, and iOS Web Push through a secure push service. For true private on-device storage plus reliable scheduled notifications and native Calendar access, a native iOS app is the stronger option and requires Xcode/macOS plus Apple developer signing for device/App Store distribution.
