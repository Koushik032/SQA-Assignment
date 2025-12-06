1. Test Plan :

i. Scope:

    Check the main user activities and overall quality of both Android apps and both websites. This includes installing and opening the apps, login/logout, main features , page loading, file uploads, form submissions, navigation, and error messages. Also test the user interface, responsiveness on different screens, basic accessibility, basic security checks, and perform exploratory testing.

ii. Devices & OS:

    Android: Samsung Galaxy A12 — Android 11
    Android: Google Pixel 6 — Android 13
    Android: Xiaomi Redmi Note 14 — Android 15
    Desktop Browsers: Chrome , Firefox , Microsoft Edge on Windows 11
    Mobile Browser (responsive): Chrome on Android


iii. Types of tests to run:

    Functional testing — core flows, inputs/outputs, form validation.
    UI/UX — layout, alignment, responsive behavior, touch targets, typography.
    Stability & Performance — app crashes, page load time, memory spikes.
    Security basics — sensitive data exposure, input validation, insecure storage check for apps.
    Accessibility — keyboard navigation, screen-reader labels, color contrast, tappable target sizes.
    Exploratory testing — 30–45 minute session per app and site to look for unexpected issues.

2. Test Cases:

# Test Cases — Apps & Websites

| ID | Title | Steps | Expected Result | Severity |
|----|--------|--------|----------------|----------|
| TC-01 | Install & Launch (AppTestingService) | 1. Open Play Store → search `com.apptestingservice` → Install → Launch | App installs and launches to onboarding/login screen without crash | High |
| TC-02 | Install & Launch (EchoGPT Chat) | 1. Install `com.echogpt.chatapp` → Launch | App opens to onboarding/login or splash screen; no ANR/crash | High |
| TC-03 | Homepage Load (apptestingservice.com) | 1. Open https://apptestingservice.com on Chrome desktop | Homepage loads fully in <5s; navigation visible & clickable | Medium |
| TC-04 | Homepage Load (echogpt.live) | 1. Open https://echogpt.live | Page loads; chat widget renders; no console errors | Medium |
| TC-05 | Create Account / Signup (App) | 1. Open app → Signup with valid email/password → Verify email | Account created; user redirected to dashboard/home | High |
| TC-06 | Login with valid credentials (both apps) | 1. Open app → Enter valid credentials → Login | Successful login → main app screen shown | High |
| TC-07 | Login with invalid credentials (negative) | 1. Enter wrong email/password → Login | Clear error displayed; login blocked; no crash | Medium |
| TC-08 | Password reset flow (App/Web) | 1. Click Forgot Password → Enter email → Submit | Reset email sent or reset flow initiated | Medium |
| TC-09 | Chat send/receive (EchoGPT web/app) | 1. Open chat → Type message → Send | Message sent; bot response received | High |
| TC-10 | File Upload (Report Upload) | 1. Choose valid PDF/image (<5MB) → Upload | File uploaded successfully without crash | High |
| TC-11 | File Upload — Large File (Negative) | 1. Attempt to upload a 50MB file | File rejected with size-limit error; no crash | Medium |
| TC-12 | Form validation (registration) | 1. Submit form with empty/invalid fields | Proper validation messages shown; submit blocked | Medium |
| TC-13 | Navigation menu responsive | 1. Resize browser/mobile → Open nav menu | Menu opens correctly; links clickable | Low |
| TC-14 | Offline handling (app) | 1. Turn off network → Try login/send message | Offline message shown; no crash | High |
| TC-15 | Session timeout / auto logout (web) | 1. Login → Stay idle until session expires → Try action | User asked to login again or session renewed | Medium |
| TC-16 | Accessibility — screen reader labels | 1. Turn on NVDA/VoiceOver → Navigate pages | Elements have ARIA/alt labels; accessible | High |
| TC-17 | Accessibility — color contrast | 1. Check main buttons/text contrast | Meets WCAG contrast ratios | Medium |
| TC-18 | Security — XSS input check | 1. Enter `<script>alert(1)</script>` in input → Submit | Script blocked; sanitized input; no execution | High |
| TC-19 | Security — insecure storage | 1. Inspect device storage for tokens | No plain-text credentials stored | High |
| TC-20 | API error handling | 1. Trigger API failure or invalid request | Friendly error shown; no stacktrace leak | High |
| TC-21 | UI layout different screens | 1. Test on small/large screens | Layout adapts; no overlapping elements | Medium |
| TC-22 | Orientation change (mobile app) | 1. Rotate device while using app | App maintains state; no glitch/crash | Medium |
| TC-23 | Performance — initial load time | 1. Measure load time via Lighthouse or stopwatch | Load time <5s on 3G/4G simulated | Medium |
| TC-24 | Logout flow | 1. Login → Click Logout → Try accessing protected page | User logged out; protected content not accessible | Medium |
| TC-25 | Push notifications (if available) | 1. Trigger push notification | Notification received; deep-link works | Low |
| TC-26 | Error messages usability | 1. Trigger error (invalid file, offline) | Clear helpful error message shown | Low |
| TC-27 | Rate limiting (chat security) | 1. Send rapid repeated messages (10/sec) | System throttles; no crash or data leak | High |
| TC-28 | Data persistence & sync | 1. Save data → Logout → Login again | Data persists and syncs properly | High |
| TC-29 | Cross-browser compatibility | 1. Test on Chrome/Firefox/Edge | Consistent behavior/UI across browsers | Medium |
| TC-30 | SQL Injection Input (Negative) | 1. Enter `' OR '1'='1` in fields → Submit | Input sanitized; no bypass or data exposure | High |
