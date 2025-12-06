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


3. Test Execution Log

| TC ID | Test Title | Device / Browser | OS / Version | App/Web Version | Date & Time | Status | Notes |
|-------|-------------|------------------|---------------|------------------|--------------|--------|--------|
| TC-01 | Install & Launch (AppTestingService) | Xiaomi Redmi Note 10 | Android 12 | v1.0.3 | 2025-11-10 11:45 AM | Pass | Installed & launched successfully; no crash |
| TC-02 | Install & Launch (EchoGPT Chat) | Samsung A52 | Android 13 | v2.1.0 | 2025-11-10 11:50 AM | Pass | Splash screen loaded; no ANR |
| TC-03 | Homepage Load (apptestingservice.com) | Chrome | Windows 10 | Web live version | 2025-11-10 12:00 PM | Pass | Loaded in under 4s |
| TC-04 | Homepage Load (echogpt.live) | Chrome | Windows 10 | Web live version | 2025-11-10 12:02 PM | Pass | No console errors detected |
| TC-05 | Create Account Signup | Pixel 6 | Android 14 | v1.0.3 | 2025-11-10 12:10 PM | Pass | Account created successfully |
| TC-06 | Login with Valid Credentials | Xiaomi Redmi Note 10 | Android 12 | v1.0.3 | 2025-11-10 12:12 PM | Pass | Login successful |
| TC-07 | Login Invalid (Negative) | Samsung A52 | Android 13 | v2.1.0 | 2025-11-10 12:14 PM | Pass | Correct error message displayed |
| TC-08 | Password Reset Flow | Chrome | Windows 10 | Web live version | 2025-11-10 12:20 PM | Fail | Reset email not received (Bug-01) |
| TC-09 | Chat Send/Receive | EchoGPT Android App | Android 13 | v2.1.0 | 2025-11-10 12:25 PM | Pass | Bot response received |
| TC-10 | File Upload (<5MB) | Chrome | Windows 10 | Web live version | 2025-11-10 12:30 PM | Pass | File uploaded successfully |
| TC-11 | File Upload Large (50MB) | Chrome | Windows 10 | Web live version | 2025-11-10 12:33 PM | Pass | Proper size error displayed |
| TC-12 | Form Validation | Chrome | Windows 10 | Web live version | 2025-11-10 12:35 PM | Pass | Validation working properly |
| TC-13 | Responsive Navigation | Chrome DevTools | Windows 10 | Web live version | 2025-11-10 12:37 PM | Pass | Menu responsive at all breakpoints |
| TC-14 | Offline Handling | EchoGPT Android | Android 13 | v2.1.0 | 2025-11-10 12:40 PM | Fail | App freezes on sending message offline (Bug-02) |
| TC-15 | Session Timeout | Chrome | Windows 10 | Web live version | 2025-11-10 12:50 PM | Pass | Session expired and auto logout |
| TC-16 | Accessibility Labels | Chrome + NVDA | Windows 10 | Web live version | 2025-11-10 1:00 PM | Fail | Missing ARIA labels for buttons (Bug-03) |
| TC-17 | Color Contrast | Chrome | Windows 10 | Web live version | 2025-11-10 1:05 PM | Pass | Contrast mostly acceptable |
| TC-18 | XSS Attempt | Chrome | Windows 10 | Web live version | 2025-11-10 1:10 PM | Pass | Script sanitized |
| TC-19 | Insecure Storage Check | Android File System | Android 12 | v1.0.3 | 2025-11-10 1:12 PM | Pass | No plaintext token stored |
| TC-20 | API Error Handling | Chrome | Windows 10 | Web live version | 2025-11-10 1:15 PM | Pass | Friendly error displayed; no stacktrace |
| TC-21 | UI Layout Screens | Samsung A52 | Android 13 | v2.1.0 | 2025-11-10 1:20 PM | Pass | Layout adjusts properly |
| TC-22 | Orientation Change | Pixel 6 | Android 14 | v1.0.3 | 2025-11-10 1:25 PM | Pass | State preserved on rotation |
| TC-23 | Performance Load Time | Chrome | Windows 10 | Web live version | 2025-11-10 1:28 PM | Pass | Load time <5s |
| TC-24 | Logout Flow | Chrome | Windows 10 | Web live version | 2025-11-10 1:32 PM | Pass | User logged out correctly |
| TC-25 | Push Notifications | Samsung A52 | Android 13 | v1.0.3 | 2025-11-10 1:35 PM | Not Tested | No test environment |
| TC-26 | Error Messages Usability | EchoGPT App | Android 13 | v2.1.0 | 2025-11-10 1:40 PM | Pass | Messages clear |
| TC-27 | Rate Limiting | Chrome | Windows 10 | Web live version | 2025-11-10 1:42 PM | Pass | Requests throttled properly |
| TC-28 | Data Persistence | Pixel 6 | Android 14 | v1.0.3 | 2025-11-10 1:45 PM | Pass | Data persisted correctly |
| TC-29 | Cross Browser Test | Firefox/Edge | Windows 10 | Web live version | 2025-11-10 1:50 PM | Pass | UI consistent |
| TC-30 | SQL Injection | Chrome | Windows 10 | Web live version | 2025-11-10 1:55 PM | Pass | Input sanitized |


3. Bug Reports

Bug 01 — Password Reset Email Not Received

### **Bug ID:** BUG-001  
### **Title:** Password reset email is not delivered after submitting "Forgot Password"  
### **Severity:** High  
### **Priority:** High  
### **Status:** Open  

### **Environment:**  
- Device: Windows 10 (Chrome 129)  
- Platform: https://apptestingservice.com  
- Network: Stable WiFi  
- Date: 2025-11-10  

### **Steps to Reproduce:**  
1. Open the website https://apptestingservice.com  
2. Click on **Forgot Password**  
3. Enter a registered email  
4. Click **Submit**  
5. Wait 5–10 minutes  
6. Check inbox & spam folder  

### **Expected Result:**  
A password reset email should be received immediately or within 1–2 minutes.

### **Actual Result:**  
No email received in inbox or spam.  
No confirmation email visible in server logs.

## Bug 02 — App Freezes When Sending Message Offline

### **Bug ID:** BUG-002  
### **Title:** EchoGPT app freezes when trying to send a message with no internet  
### **Severity:** Critical  
### **Priority:** High  
### **Status:** Open  

### **Environment:**  
- Device: Samsung A52  
- OS: Android 13  
- App: EchoGPT v2.1.0  
- Network: Mobile Data OFF  
- Date: 2025-11-10  

### **Steps to Reproduce:**  
1. Open the **EchoGPT Chat App**  
2. Turn off Wi-Fi and mobile data  
3. Type a message  
4. Tap **Send**  
5. Observe the UI  

### **Expected Result:**  
A proper error message like **“No internet connection”** should appear.  
The app should remain responsive.

### **Actual Result:**  
The app **freezes** for 10–12 seconds and sometimes becomes unresponsive.  
Force close is required in some cases.

## Bug 03 — Missing ARIA Labels for Buttons (Accessibility Issue)

### **Bug ID:** BUG-003  
### **Title:** Missing ARIA labels for interactive buttons on homepage (echogpt.live)  
### **Severity:** Medium  
### **Priority:** Medium  
### **Status:** Open  

### **Environment:**  
- Device: Windows 10  
- Browser: Chrome 129  
- Accessibility Tools: NVDA screen reader  
- Website: https://echogpt.live  
- Date: 2025-11-10  

### **Steps to Reproduce:**  
1. Open **https://echogpt.live**  
2. Turn on **NVDA** or **VoiceOver**  
3. Navigate through the main banner and top buttons  
4. Listen to screen reader output  

### **Expected Result:**  
Screen reader should read button names clearly, such as:  
- “Start Chat”  
- “Login”  
- “Sign Up”

### **Actual Result:**  
Screen reader reads:  
- “Button… button…”  
- “Clickable… clickable item…”  
No meaningful labels available.

