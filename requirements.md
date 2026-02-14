# Requirements Document: Sarthi.ai - Hyper-Local Agentic OS

## Introduction

Sarthi.ai is a revolutionary mobile-first web application serving as a "Digital Lifeline" for India's next billion users. The system bridges the digital divide through a Zero-UI philosophy, leveraging multimodal AI (Voice, Vision, Gesture) to serve semi-literate users in Tier 2/3 cities and rural villages. The application combines futuristic "Bharat Cyberpunk" aesthetics with radical simplicity, creating an invisible interface that feels premium yet accessible.

## Glossary

- **Sarthi_System**: The complete web application including all features and interfaces
- **Pehchan_Module**: The biometric authentication system
- **Sarthi_Bot**: The AI-powered holographic orb serving as the primary interaction point
- **Drishti_Module**: The AR vision mode for camera-based object recognition
- **Setu_Module**: The volunteer and help bridge system
- **Schemes_Hub**: The government schemes intelligence system
- **User**: End-user accessing the application (semi-literate, Tier 2/3 cities, rural villages)
- **Volunteer**: Verified helper available through Setu Module
- **Biometric_Scan**: Face ID, Voice ID, or QR/Aadhar scan authentication
- **Hyper_Local_Data**: Location-specific information (weather, mandi prices, alerts)
- **Trust_Badge**: Visual indicator showing end-to-end encryption status

## Requirements

### Requirement 1: Universal Biometric Authentication

**User Story:** As a semi-literate user, I want to access the system without passwords, so that I can easily log in using my face, voice, or Aadhar.

#### Acceptance Criteria

1. WHEN a user accesses the login screen, THE Pehchan_Module SHALL display four authentication options: Face ID, Voice ID, Aadhar/QR Scan, and traditional login
2. WHEN a user selects Face ID, THE Pehchan_Module SHALL simulate a biometric facial scan and authenticate within 3 seconds
3. WHEN a user selects Voice ID, THE Pehchan_Module SHALL display a pulsing microphone and authenticate when the user speaks "Main Hoon"
4. WHEN a user selects Aadhar/QR Scan, THE Pehchan_Module SHALL activate the camera and process the scanned code for authentication
5. WHEN authentication succeeds, THE Sarthi_System SHALL transition to the Living Dashboard with a fluid animation
6. IF authentication fails, THEN THE Pehchan_Module SHALL display an error message in the user's selected language and allow retry

### Requirement 2: Responsive Design and Device Optimization

**User Story:** As a user, I want the application to work perfectly on my mobile phone and desktop, so that I can access services from any device.

#### Acceptance Criteria

1. THE Sarthi_System SHALL render in a mobile-first, app-like layout on devices with screen width below 768px
2. THE Sarthi_System SHALL render in a dashboard-like layout on devices with screen width 768px and above
3. WHEN the viewport size changes, THE Sarthi_System SHALL adapt the layout responsively without page reload
4. THE Sarthi_System SHALL support fullscreen mode activation and deactivation
5. WHEN in fullscreen mode, THE Sarthi_System SHALL hide browser chrome and maximize content area
6. THE Sarthi_System SHALL maintain touch-friendly interaction targets of minimum 44x44 pixels on mobile devices

### Requirement 3: Living Dashboard with Holographic Interface

**User Story:** As a user, I want an intuitive central hub with a talking AI assistant, so that I can interact naturally without complex menus.

#### Acceptance Criteria

1. WHEN the dashboard loads, THE Sarthi_Bot SHALL display as a pulsing holographic orb at the center of the screen
2. THE Sarthi_Bot SHALL animate with sound visualizer effects when processing voice input or speaking
3. THE Sarthi_System SHALL display real-time HUD elements including current date, time, timezone, and Trust_Badge
4. THE Sarthi_System SHALL fetch and display Hyper_Local_Data including weather with future predictions
5. WHEN weather conditions change significantly, THE Sarthi_System SHALL display actionable alerts in simple language
6. THE Sarthi_System SHALL update all dashboard elements in real-time without requiring page refresh

### Requirement 4: Notification Center with Hyper-Local Intelligence

**User Story:** As a user, I want to receive relevant local alerts about mandi prices and community events, so that I can make informed decisions.

#### Acceptance Criteria

1. THE Sarthi_System SHALL display a notification icon with unread count badge on the dashboard
2. WHEN a user taps the notification icon, THE Sarthi_System SHALL slide out a glass-panel notification center
3. THE Sarthi_System SHALL fetch and display Hyper_Local_Data including mandi prices, vaccination camps, and community alerts
4. WHEN new notifications arrive, THE Sarthi_System SHALL update the unread count and animate the notification icon
5. THE Sarthi_System SHALL organize notifications by priority with high-priority items using Deep Saffron color
6. WHEN a user taps a notification, THE Sarthi_System SHALL expand it to show full details and available actions

### Requirement 5: AR Vision Mode (Sarthi Drishti)

**User Story:** As a user, I want to point my camera at broken objects or diseased crops, so that I can get instant help and repair guidance.

#### Acceptance Criteria

1. WHEN a user activates Drishti_Module, THE Sarthi_System SHALL request camera permissions and activate the device camera
2. WHEN the camera captures an object, THE Drishti_Module SHALL perform object recognition within 5 seconds
3. WHEN object recognition completes, THE Drishti_Module SHALL provide voice explanation in the user's selected language
4. THE Drishti_Module SHALL display a step-by-step text checklist for addressing the identified issue
5. THE Drishti_Module SHALL automatically fetch and embed relevant YouTube tutorials in Hindi
6. THE Drishti_Module SHALL allow users to save the diagnosis and steps to their history

### Requirement 6: Volunteer Help Bridge (Sarthi Setu)

**User Story:** As a user needing technical help, I want to connect with nearby verified volunteers, so that I can get in-person assistance quickly.

#### Acceptance Criteria

1. WHEN a user activates Setu_Module, THE Sarthi_System SHALL display a "Madad Bulao" panic button prominently
2. WHEN a user taps "Madad Bulao", THE Setu_Module SHALL display an Uber-style radar map showing nearby volunteers
3. THE Setu_Module SHALL display volunteer profiles including name, rating, and neighbor feedback
4. WHEN a user selects a volunteer, THE Setu_Module SHALL provide options for Live Chat, Audio Call, and "Book Now"
5. WHEN a user books a volunteer, THE Setu_Module SHALL enable real-time tracking of the volunteer's location
6. THE Setu_Module SHALL integrate with WhatsApp for sending booking confirmations and updates
7. WHEN a session completes, THE Setu_Module SHALL prompt the user to rate and provide feedback

### Requirement 7: Government Schemes Intelligence Hub

**User Story:** As a user, I want to understand government schemes in simple language, so that I can access benefits I'm eligible for.

#### Acceptance Criteria

1. WHEN a user accesses Schemes_Hub, THE Sarthi_System SHALL display a list of relevant government schemes based on user profile
2. WHEN a user selects a scheme, THE Schemes_Hub SHALL analyze and display Benefits, Eligibility, and Application Steps in simple language
3. THE Schemes_Hub SHALL provide direct "Apply Now" buttons linking to official government portals
4. THE Schemes_Hub SHALL embed video explainers in the user's selected language
5. WHEN a user needs in-person assistance, THE Schemes_Hub SHALL provide GPS guidance to the nearest Seva Setu center
6. THE Schemes_Hub SHALL track application status and notify users of updates

### Requirement 8: Interaction History and Context Preservation

**User Story:** As a user, I want to review my past interactions and conversations, so that I can reference previous guidance and solutions.

#### Acceptance Criteria

1. THE Sarthi_System SHALL maintain a complete timeline of all user interactions
2. WHEN a user accesses "Sab Dekhen", THE Sarthi_System SHALL display the interaction history in reverse chronological order
3. WHEN a user taps a history item, THE Sarthi_System SHALL expand it to show full conversation context, steps taken, and videos watched
4. THE Sarthi_System SHALL allow users to search history by keywords or date range
5. THE Sarthi_System SHALL preserve history across sessions and devices for authenticated users
6. THE Sarthi_System SHALL allow users to bookmark important interactions for quick access

### Requirement 9: Multilingual Support

**User Story:** As a user, I want to switch between languages easily, so that I can use the app in my preferred language.

#### Acceptance Criteria

1. THE Sarthi_System SHALL support English, Hindi, Hinglish, and Marathi languages
2. WHEN a user taps the language selector, THE Sarthi_System SHALL display available language options
3. WHEN a user selects a language, THE Sarthi_System SHALL translate all UI text, notifications, and voice responses within 1 second
4. THE Sarthi_System SHALL persist the language preference across sessions
5. THE Sarthi_System SHALL maintain language consistency across all modules including Drishti, Setu, and Schemes_Hub
6. WHEN voice input is detected, THE Sarthi_System SHALL automatically detect the spoken language and respond accordingly

### Requirement 10: Bharat Cyberpunk Design System

**User Story:** As a user, I want a beautiful and trustworthy interface, so that I feel confident using digital services.

#### Acceptance Criteria

1. THE Sarthi_System SHALL use Deep Saffron (#FF9933) for high-priority actions and call-to-action buttons
2. THE Sarthi_System SHALL use Cyber-Teal (#008080) for trust verification elements and Trust_Badge
3. THE Sarthi_System SHALL use Deep Navy or Void Black as the primary background color
4. THE Sarthi_System SHALL apply glassmorphism effects (frosted glass panels with backdrop blur) to all card components
5. THE Sarthi_System SHALL apply neumorphism effects (soft, tactile shadows) to interactive elements
6. WHEN transitioning between screens or states, THE Sarthi_System SHALL use fluid, water-like animations with Framer Motion
7. THE Sarthi_System SHALL maintain animation frame rates above 30 FPS on mid-range mobile devices

### Requirement 11: Voice Interaction and Multimodal Input

**User Story:** As a semi-literate user, I want to interact using my voice, so that I don't need to read or type complex text.

#### Acceptance Criteria

1. THE Sarthi_Bot SHALL continuously listen for voice input when activated
2. WHEN a user speaks, THE Sarthi_Bot SHALL display real-time sound visualizer animations
3. THE Sarthi_Bot SHALL process voice commands in the user's selected language within 3 seconds
4. THE Sarthi_Bot SHALL respond with voice output in the same language as the input
5. THE Sarthi_Bot SHALL display text transcription of both user input and bot responses for accessibility
6. THE Sarthi_System SHALL support gesture-based navigation including swipe, pinch, and long-press
7. IF voice recognition fails, THEN THE Sarthi_Bot SHALL prompt the user to repeat or offer alternative input methods

### Requirement 12: Trust and Security Indicators

**User Story:** As a user, I want to know my data is secure, so that I can trust the system with sensitive information.

#### Acceptance Criteria

1. THE Sarthi_System SHALL display an "End-to-End Encrypted" Trust_Badge on all screens
2. THE Trust_Badge SHALL use Cyber-Teal color and a lock icon to indicate security
3. WHEN a user taps the Trust_Badge, THE Sarthi_System SHALL display a simple explanation of data protection
4. THE Sarthi_System SHALL display verification badges next to all volunteers in Setu_Module
5. THE Sarthi_System SHALL show official government logos next to verified scheme information
6. WHEN connecting to external services, THE Sarthi_System SHALL display a trust confirmation dialog

### Requirement 13: Offline Capability and Progressive Enhancement

**User Story:** As a user in an area with poor connectivity, I want basic features to work offline, so that I can still access critical information.

#### Acceptance Criteria

1. WHEN network connectivity is lost, THE Sarthi_System SHALL display a clear offline indicator
2. WHILE offline, THE Sarthi_System SHALL allow access to cached history and previously viewed content
3. WHILE offline, THE Sarthi_System SHALL queue user actions and sync when connectivity is restored
4. THE Sarthi_System SHALL cache Hyper_Local_Data for offline access with timestamps indicating freshness
5. WHEN connectivity is restored, THE Sarthi_System SHALL automatically sync queued actions and refresh data
6. THE Sarthi_System SHALL prioritize critical features (emergency contacts, saved guides) for offline availability

### Requirement 14: Performance and Accessibility

**User Story:** As a user with a low-end smartphone, I want the app to load quickly and work smoothly, so that I can access services without frustration.

#### Acceptance Criteria

1. THE Sarthi_System SHALL achieve initial page load within 3 seconds on 3G networks
2. THE Sarthi_System SHALL maintain interactive time-to-first-byte under 1 second for cached content
3. THE Sarthi_System SHALL optimize images and assets to reduce total page weight below 2MB
4. THE Sarthi_System SHALL support screen readers for visually impaired users
5. THE Sarthi_System SHALL provide high contrast mode for users with visual impairments
6. THE Sarthi_System SHALL support keyboard navigation for all interactive elements
7. THE Sarthi_System SHALL meet WCAG 2.1 Level AA guidelines for color contrast and text sizing
S
