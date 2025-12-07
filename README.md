## 1. Test Plan :

i. Scope:

    Check the main user activities and overall quality of both Android apps and both websites. This includes installing and opening the apps, login/logout, main features , page loading, file uploads, form submissions, navigation, and error messages. Also test the user interface, responsiveness on different screens, basic accessibility, basic security checks, and perform exploratory testing.

ii. Devices & OS:

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

## 2. Test Cases:

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


## 3. Test Execution Log

| TC ID | Test Title | Device / Browser | OS / Version | App/Web Version | Date & Time | Status | Notes |
|-------|-------------|------------------|---------------|------------------|--------------|--------|--------|
| TC-01 | Install & Launch (AppTestingService) | Xiaomi Redmi Note 14 | Android 15 | v1.0.3 | 2025-12-02 11:45 AM | Pass | Installed & launched successfully; no crash |
| TC-02 | Install & Launch (EchoGPT Chat) | Xiaomi Redmi Note 14 | Android 15 | v2.1.0 | 2025-12-02 11:50 AM | Pass | Splash screen loaded; no ANR |
| TC-03 | Homepage Load (apptestingservice.com) | Chrome | Windows 11 | Web live version | 2025-12-02 12:00 PM | Pass | Loaded in under 4s |
| TC-04 | Homepage Load (echogpt.live) | Chrome | Windows 11 | Web live version | 2025-12-02 12:02 PM | Pass | No console errors detected |
| TC-05 | Create Account Signup | Xiaomi Redmi Note 14 | Android 15 | v1.0.3 | 2025-12-02 12:10 PM | Pass | Account created successfully |
| TC-06 | Login with Valid Credentials | Xiaomi Redmi Note 14 | Android 15 | v1.0.3 | 2025-12-02 12:12 PM | Pass | Login successful |
| TC-07 | Login Invalid (Negative) | Xiaomi Redmi Note 14 | Android 15 | v2.1.0 | 2025-12-02 12:14 PM | Pass | Correct error message displayed |
| TC-08 | Password Reset Flow | Chrome | Windows 11 | Web live version | 2025-12-02 12:20 PM | Fail | Reset email not received (Bug-01) |
| TC-09 | Chat Send/Receive(EchoGPT Android App) | Xiaomi Redmi Note 14 | Android 15 | v2.1.0 | 2025-12-02 12:25 PM | Pass | Bot response received |
| TC-10 | File Upload (<5MB) | Chrome | Windows 11 | Web live version | 2025-12-02 12:30 PM | Pass | File uploaded successfully |
| TC-11 | File Upload Large (50MB) | Chrome | Windows 11 | Web live version | 2025-12-02 12:33 PM | Pass | Proper size error displayed |
| TC-12 | Form Validation | Chrome | Windows 11 | Web live version | 2025-12-02 12:35 PM | Pass | Validation working properly |
| TC-13 | Responsive Navigation | Chrome DevTools | Windows 11 | Web live version | 2025-12-02 12:37 PM | Pass | Menu responsive at all breakpoints |
| TC-14 | Offline Handling | EchoGPT Android | Android 15 | v2.1.0 | 2025-12-02 12:40 PM | Fail | App freezes on sending message offline (Bug-02) |
| TC-15 | Session Timeout | Chrome | Windows 11 | Web live version | 2025-12-02 12:50 PM | Pass | Session expired and auto logout |
| TC-16 | Accessibility Labels | Chrome + NVDA | Windows 11 | Web live version | 2025-12-02 1:00 PM | Fail | Missing ARIA labels for buttons (Bug-03) |
| TC-17 | Color Contrast | Chrome | Windows 11 | Web live version | 2025-12-02 1:05 PM | Pass | Contrast mostly acceptable |
| TC-18 | XSS Attempt | Chrome | Windows 11 | Web live version | 2025-12-02 1:10 PM | Pass | Script sanitized |
| TC-19 | Insecure Storage Check | Android File System | Android 15 | v1.0.3 | 2025-12-02 1:12 PM | Pass | No plaintext token stored |
| TC-20 | API Error Handling | Chrome | Windows 11 | Web live version | 2025-12-02 1:15 PM | Pass | Friendly error displayed; no stacktrace |
| TC-21 | UI Layout Screens | Xiaomi Redmi Note 14 | Android 15 | v2.1.0 | 2025-12-02 1:20 PM | Pass | Layout adjusts properly |
| TC-22 | Orientation Change | Xiaomi Redmi Note 14 | Android 15 | v1.0.3 | 2025-12-02 1:25 PM | Pass | State preserved on rotation |
| TC-23 | Performance Load Time | Chrome | Windows 11 | Web live version | 2025-12-02 1:28 PM | Pass | Load time <5s |
| TC-24 | Logout Flow | Chrome | Windows 11 | Web live version | 2025-12-02 1:32 PM | Pass | User logged out correctly |
| TC-25 | Push Notifications | Xiaomi Redmi Note 14 | Android 15 | v1.0.3 | 2025-12-02 1:35 PM | Not Tested | No test environment |
| TC-26 | Error Messages Usability | EchoGPT App | Android 15 | v2.1.0 | 2025-12-02 1:40 PM | Pass | Messages clear |
| TC-27 | Rate Limiting | Chrome | Windows 11 | Web live version | 2025-12-02 1:42 PM | Pass | Requests throttled properly |
| TC-28 | Data Persistence | Xiaomi Redmi Note 14 | Android 15 | v1.0.3 | 2025-12-02 1:45 PM | Pass | Data persisted correctly |
| TC-29 | Cross Browser Test | Firefox/Edge | Windows 11 | Web live version | 2025-12-02 1:50 PM | Pass | UI consistent |
| TC-30 | SQL Injection | Chrome | Windows 11 | Web live version | 2025-12-02 1:55 PM | Pass | Input sanitized |


## 4. Bug Reports

## Bug 01 — Password Reset Email Not Received

### **Bug ID: BUG-001** 
Title: Password reset email is not delivered after submitting "Forgot Password"  
Severity: High  
Priority: High  
Status: Open  

### **Environment:**  
- Device: Windows 11 (Chrome)  
- Platform: https://apptestingservice.com  
- Network: Stable WiFi  
- Date: 2025-12-02  

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
Title: EchoGPT app freezes when trying to send a message with no internet  
Severity: Critical  
Priority: High  
Status: Open  

### **Environment:**  
- Device: Xiaomi Redmi Note 14  
- OS: Android 15
- App: EchoGPT v2.1.0  
- Network: Mobile Data OFF  
- Date: 2025-12-03  

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
Title: Missing ARIA labels for interactive buttons on homepage (echogpt.live)  
Severity: Medium  
Priority: Medium  
Status: Open  

### **Environment:**  
- Device: Windows 11
- Browser: Chrome  
- Accessibility Tools: NVDA screen reader  
- Website: https://echogpt.live  
- Date: 2025-12-03  

### **Steps to Reproduce:**  
1. Open **https://echogpt.live**  
2. Turn on **NVDA**  
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


## 5. Exploratory Testing Notes

Date: 04 December 2025

Duration: 40 minutes

Tester: Koushik Roy

Scope: Android Apps (AppTestingService, EchoGPT App) and Websites (echogpt.live, apptestingservice.com)

  ##  1. Test Charter (Mission for the Session)

    Explore the core user flows, chat behavior, file upload, navigation, and offline/error handling to identify functional issues, usability gaps, performance delays, and UI inconsistencies.
    The goal is to uncover bugs that scripted test cases may miss.

  ##  2. Areas Explored During the Session

    App installation & launch experience

    Signup & login flows

    Chat message send/receive

    File upload (PDF, image, large file)

    Offline behavior (no network test)

    Navigation responsiveness (web)

    Form validation and error messages

    UI layout on different screen sizes

    Accessibility behavior (screen reader brief check)

    Browser console warnings (web)

  ##  3. Key Findings (Issues, Observations, Bugs)

    Functional/Usability Issues

    Password reset email not received

    Severity: High

    Occurs on apptestingservice.com

    No confirmation email received even after waiting 10 minutes.

    Chat freezes when sending message offline (EchoGPT app)

    Severity: Critical

    App becomes unresponsive for 10–12 seconds.

    No proper offline message shown.

    EchoGPT web chat sometimes delays response (3–5 sec longer)

    Severity: Medium

    Not always reproducible; suspected backend latency.

    File upload progress missing

    Severity: Medium

    Large file (>3MB) shows no progress indicator; user unsure if upload is working.

    Navigation menu overlaps text on small-width mobile view

    Severity: Low

    Menu items overlay with main headline.

    UI/Design Issues

    Chat bubble alignment inconsistent

    Severity: Low

    Long messages wrap awkwardly on screen.

    Button hover state looks different across browsers

    Severity: Low

    Chrome vs Firefox differences detected.

    Signup form error messages not aligned properly

    Severity: Medium

    Validation messages appear too close to input fields.

    Accessibility Issues

    Missing ARIA labels for buttons on echogpt.live

    Severity: Medium

    Screen reader reads “button” instead of descriptive names.

    Contrast issue on secondary buttons

    Severity: Low

    Fails WCAG contrast ratio guidelines.

    Console/Logs Issues (Web)

    Minor JavaScript warnings on console
    Example:

    Warning: Unknown props passed to DOM element


    Severity: Low

##  4. Notes & Recommendations

    Add offline handling messages across both apps.

    Improve error messages to be clearer and friendlier.

    Add upload progress bar to improve user confidence.

    Improve responsiveness for smaller devices.

    Add ARIA labels to ensure accessibility compliance.

    Fix chat freeze issue, which is a major blocker.

##  5. Overall Summary of Session

    The exploratory session found multiple user-impacting issues, especially in:

    Forgot password flow

    Offline chat handling

    Accessibility

    UI layout on small screens

    Missing progress indicators

    No critical security issues were discovered during this time window, but some functional problems significantly affect user experience.\


## 6. Short Summary Report

## 1. Overview
A full test cycle was executed on two Android applications (**AppTestingService** and **EchoGPT Chat App**) and two websites (**apptestingservice.com** and **echogpt.live**).  
The testing objectives were to validate:

- Functional correctness  
- UI quality and usability  
- Stability and performance  
- Accessibility compliance  
- Basic security measures  

Testing methods included **manual test cases**, **exploratory testing**, and **basic negative/security checks**.

---

## 2. Major Issues Found

| ID       | Issue Summary                                         | Severity  | Status |
|----------|------------------------------------------------------|-----------|--------|
| BUG-001  | Password reset email not delivered                   | High      | Open   |
| BUG-002  | EchoGPT app freezes when sending a message offline  | Critical  | Open   |
| BUG-003  | Missing ARIA labels on key buttons (accessibility failure) | Medium    | Open   |

**Impact:**  
- Password reset issue blocks user account recovery.  
- Offline freeze affects app stability and usability.  
- Missing accessibility labels hinder visually impaired users and fail WCAG guidelines.

---

## 3. Release Readiness Assessment

| Category       | Status             | Notes                                         |
|----------------|------------------|-----------------------------------------------|
| Functional     | Partially Ready | Core flows functional; fixes required in some areas |
| Performance    | ✅ Ready           | Load times and interaction speed acceptable |
| Stability      | Not Fully Ready | Offline freeze bug affects reliability      |
| Security       | Acceptable      | No major vulnerabilities detected; minor sanitization checks pending |
| Accessibility  | Needs Improvement | Missing ARIA labels reduce compliance       |

**Overall Release Decision:** **NOT READY** for full release  
**Recommendation:** Apply a **hotfix round** before production deployment.

---

## 4. Risk List

| Risk                        | Description                                  | Impact | Likelihood |
|------------------------------|----------------------------------------------|--------|-----------|
| Password reset not working    | Users cannot recover accounts               | High   | High      |
| App freezing offline          | Poor user experience; risk of uninstalls   | High   | Medium    |
| Missing accessibility labels  | Excludes disabled users; compliance failure| Medium | Medium    |
| Large file upload handling    | May crash low-memory devices               | Medium | Low       |
| Chat API rate-limiting        | Risk of abuse or server overload           | Medium | Low       |

---

## 5. Recommended Next Steps

1. **Critical & High-Severity Bug Fixes**  
   - Implement proper offline handling and retry logic for chat.  
   - Fix password reset API or SMTP integration.  
   - Add missing ARIA labels and alt texts for accessibility.

2. **Regression & Testing**  
   - Re-test core flows after bug fixes.  
   - Add automated unit/UI tests for login, chat, and file upload flows.  
   - Conduct a full accessibility audit (WCAG 2.1 AA).  

3. **UX & Performance Improvements**  
   - Improve error messages for network/upload issues.  
   - Plan a performance load test for chat endpoints under peak load.  
   - Prepare a staging environment with proper logging for future test cycles.

---

## 6. Final Summary
The system demonstrates strong potential, with most core functionalities operational. However, **stability, account recovery, and accessibility** issues must be addressed before release. With a focused bug-fix round and targeted regression testing, the product can reach **production-ready quality** in the next iteration.
