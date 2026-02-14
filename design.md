# Design Document: Sarthi.ai - Hyper-Local Agentic OS

## Overview

Sarthi.ai is a mobile-first, progressive web application that serves as a digital lifeline for India's next billion users. The system implements a Zero-UI philosophy through multimodal AI interactions (Voice, Vision, Gesture), wrapped in a "Bharat Cyberpunk" aesthetic that fuses futuristic design with cultural warmth.

The architecture prioritizes radical simplicity for semi-literate users while maintaining premium visual quality. The application uses React with Vite for optimal performance, Tailwind CSS for responsive design, Framer Motion for fluid animations, and mock JSON data simulating AWS Bedrock AI responses.

## Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Presentation Layer                       │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Mobile UI  │  │  Desktop UI  │  │  Fullscreen  │      │
│  │  (< 768px)   │  │  (≥ 768px)   │  │     Mode     │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────────┐
│                    Component Layer                           │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐      │
│  │ Pehchan  │ │ Dashboard│ │  Drishti │ │   Setu   │      │
│  │  Module  │ │   Hub    │ │  Module  │ │  Module  │      │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘      │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐                   │
│  │ Schemes  │ │ History  │ │ Language │                   │
│  │   Hub    │ │  Viewer  │ │ Switcher │                   │
│  └──────────┘ └──────────┘ └──────────┘                   │
└─────────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────────┐
│                     State Management                         │
│  ┌──────────────────────────────────────────────────────┐  │
│  │           React Context API (Global State)            │  │
│  │  - Auth State  - User Profile  - Language Preference │  │
│  │  - Location    - Notifications - Interaction History │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────────┐
│                      Service Layer                           │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐      │
│  │   AI     │ │  Camera  │ │   Geo    │ │  Storage │      │
│  │ Service  │ │ Service  │ │ Service  │ │ Service  │      │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘      │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐                   │
│  │  Voice   │ │  Weather │ │   Mock   │                   │
│  │ Service  │ │ Service  │ │   API    │                   │
│  └──────────┘ └──────────┘ └──────────┘                   │
└─────────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────────┐
│                      Data Layer                              │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  LocalStorage (Offline Cache, User Preferences)      │  │
│  │  IndexedDB (History, Large Assets)                   │  │
│  │  Mock JSON (Simulated AWS Bedrock Responses)         │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

### Technology Stack

- **Frontend Framework**: React 18+ with Vite for fast builds and HMR
- **Styling**: Tailwind CSS 3+ with custom Bharat Cyberpunk theme
- **Animations**: Framer Motion for fluid, physics-based animations
- **Icons**: Lucide React for consistent iconography
- **State Management**: React Context API with useReducer for complex state
- **Routing**: React Router v6 for navigation
- **Camera/Media**: Browser MediaDevices API
- **Geolocation**: Browser Geolocation API
- **Voice**: Web Speech API (SpeechRecognition, SpeechSynthesis)
- **Storage**: LocalStorage for preferences, IndexedDB for large data
- **Build Tool**: Vite with optimized production builds
- **Type Safety**: PropTypes for runtime validation

## Components and Interfaces

### 1. Pehchan Module (Authentication)

**Purpose**: Password-less biometric authentication system

**Component Structure**:
```
PehchanModule/
├── LoginScreen.jsx          # Main authentication screen
├── FaceIDScanner.jsx        # Simulated facial recognition
├── VoiceIDCapture.jsx       # Voice authentication with "Main Hoon"
├── AadharQRScanner.jsx      # QR/Aadhar code scanner
└── AuthContext.jsx          # Authentication state management
```

**Key Interfaces**:
```javascript
// Authentication State
interface AuthState {
  isAuthenticated: boolean
  user: UserProfile | null
  authMethod: 'face' | 'voice' | 'aadhar' | 'traditional' | null
  loading: boolean
  error: string | null
}

// User Profile
interface UserProfile {
  id: string
  name: string
  phone: string
  location: GeoLocation
  language: 'en' | 'hi' | 'hinglish' | 'mr'
  preferences: UserPreferences
}

// Authentication Methods
interface AuthMethods {
  authenticateWithFace(): Promise<AuthResult>
  authenticateWithVoice(audioBlob: Blob): Promise<AuthResult>
  authenticateWithAadhar(qrCode: string): Promise<AuthResult>
}
```

**Design Details**:
- Face ID: Animated scanning overlay with pulsing rings, 3-second simulation
- Voice ID: Pulsing microphone with waveform visualization, listens for "Main Hoon"
- Aadhar/QR: Camera viewfinder with corner guides, auto-capture on detection
- Transitions: Fluid morph animation from login to dashboard (800ms duration)

### 2. Living Dashboard

**Purpose**: Central hub with holographic Sarthi Bot and real-time HUD

**Component Structure**:
```
Dashboard/
├── DashboardLayout.jsx      # Responsive layout wrapper
├── SarthiBot.jsx            # Holographic pulsing orb
├── HUDElements.jsx          # Date, time, trust badge
├── WeatherWidget.jsx        # Hyper-local weather with predictions
├── NotificationCenter.jsx   # Glass-panel slide-out
└── QuickActions.jsx         # Primary action buttons
```

**Key Interfaces**:
```javascript
// Sarthi Bot State
interface SarthiBotState {
  isListening: boolean
  isSpeaking: boolean
  currentMessage: string
  soundLevel: number        // 0-100 for visualizer
  mood: 'idle' | 'thinking' | 'responding' | 'error'
}

// HUD Data
interface HUDData {
  currentTime: Date
  timezone: string
  isEncrypted: boolean
  connectionStatus: 'online' | 'offline' | 'slow'
}

// Weather Data
interface WeatherData {
  temperature: number
  condition: string
  forecast: ForecastItem[]
  alerts: WeatherAlert[]
  location: string
}

interface WeatherAlert {
  type: 'rain' | 'storm' | 'heat' | 'cold'
  message: string
  actionable: string        // e.g., "Cover your crops"
  timeToEvent: number       // minutes
}
```

**Design Details**:
- Sarthi Bot: 3D-like orb with gradient (saffron to teal), pulsing at 60bpm idle
- Sound Visualizer: Radial bars around orb, reactive to voice amplitude
- HUD: Glassmorphism cards with backdrop-blur-md, positioned at screen edges
- Weather: Large temperature display, icon-based conditions, scrollable forecast
- Animations: Orb scales 1.0 to 1.1 on interaction, rotates continuously

### 3. Notification Center

**Purpose**: Hyper-local alerts and community information

**Component Structure**:
```
NotificationCenter/
├── NotificationPanel.jsx    # Slide-out glass panel
├── NotificationItem.jsx     # Individual notification card
├── NotificationFilters.jsx  # Priority/category filters
└── NotificationService.js   # Fetch and manage notifications
```

**Key Interfaces**:
```javascript
// Notification
interface Notification {
  id: string
  type: 'mandi' | 'health' | 'scheme' | 'community' | 'alert'
  priority: 'high' | 'medium' | 'low'
  title: string
  message: string
  timestamp: Date
  read: boolean
  actionable: boolean
  action?: NotificationAction
}

interface NotificationAction {
  label: string
  type: 'navigate' | 'external' | 'call'
  target: string
}

// Hyper-Local Data
interface HyperLocalData {
  mandiPrices: MandiPrice[]
  healthCamps: HealthCamp[]
  communityEvents: CommunityEvent[]
}
```

**Design Details**:
- Panel: Slides from right (mobile) or top-right (desktop), 80% viewport height
- Glass Effect: backdrop-blur-lg, bg-opacity-10, border with gradient
- Priority Colors: High (Deep Saffron), Medium (Cyber-Teal), Low (Gray)
- Animations: Stagger children with 50ms delay, spring physics

### 4. Drishti Module (AR Vision)

**Purpose**: Camera-based object recognition with guided solutions

**Component Structure**:
```
DrishtiModule/
├── CameraView.jsx           # Live camera feed
├── ObjectRecognition.jsx    # AI-powered recognition
├── VoiceExplainer.jsx       # Text-to-speech explanation
├── StepChecklist.jsx        # Interactive step-by-step guide
├── VideoEmbed.jsx           # YouTube tutorial integration
└── DiagnosisHistory.jsx     # Save and review past scans
```

**Key Interfaces**:
```javascript
// Recognition Result
interface RecognitionResult {
  objectType: string
  confidence: number
  issue: string | null
  explanation: string
  steps: RepairStep[]
  videoTutorials: VideoTutorial[]
}

interface RepairStep {
  id: number
  description: string
  completed: boolean
  imageUrl?: string
}

interface VideoTutorial {
  id: string
  title: string
  youtubeId: string
  duration: number
  language: string
}

// Camera Service
interface CameraService {
  requestPermission(): Promise<boolean>
  startCamera(): Promise<MediaStream>
  captureFrame(): Promise<Blob>
  stopCamera(): void
}
```

**Design Details**:
- Camera View: Full-screen with overlay guides, capture button at bottom
- Recognition: Loading animation (scanning lines), 5-second max processing
- Voice: Auto-plays explanation, shows text transcript simultaneously
- Checklist: Large touch targets, checkboxes with satisfying animation
- Video: Embedded YouTube player, auto-suggests Hindi tutorials

### 5. Setu Module (Volunteer Bridge)

**Purpose**: Connect users with nearby verified volunteers

**Component Structure**:
```
SetuModule/
├── MadadButton.jsx          # Panic/help button
├── VolunteerMap.jsx         # Radar-style map with nearby volunteers
├── VolunteerCard.jsx        # Profile with rating and feedback
├── ChatInterface.jsx        # Live text chat
├── AudioCall.jsx            # Voice call integration
├── BookingFlow.jsx          # Booking and tracking
└── RatingFeedback.jsx       # Post-session rating
```

**Key Interfaces**:
```javascript
// Volunteer Profile
interface Volunteer {
  id: string
  name: string
  photo: string
  rating: number
  totalSessions: number
  specialties: string[]
  distance: number          // in kilometers
  available: boolean
  location: GeoLocation
  feedback: VolunteerFeedback[]
}

interface VolunteerFeedback {
  userId: string
  userName: string
  rating: number
  comment: string
  date: Date
}

// Booking
interface Booking {
  id: string
  volunteerId: string
  userId: string
  status: 'pending' | 'accepted' | 'in-progress' | 'completed' | 'cancelled'
  issue: string
  scheduledTime: Date
  location: GeoLocation
  trackingEnabled: boolean
}

// Communication
interface ChatMessage {
  id: string
  senderId: string
  message: string
  timestamp: Date
  type: 'text' | 'audio' | 'image'
}
```

**Design Details**:
- Madad Button: Large, pulsing Deep Saffron button, always accessible
- Map: Circular radar with pulsing rings, volunteer pins with distance labels
- Volunteer Cards: Glassmorphism, star ratings, "Book Now" CTA
- Chat: WhatsApp-style interface, voice message support
- Tracking: Real-time map with volunteer location, ETA display

### 6. Schemes Hub (Government Intelligence)

**Purpose**: Simplify government schemes with AI analysis

**Component Structure**:
```
SchemesHub/
├── SchemesList.jsx          # Browse available schemes
├── SchemeDetail.jsx         # Detailed scheme information
├── EligibilityChecker.jsx   # AI-powered eligibility analysis
├── ApplicationGuide.jsx     # Step-by-step application process
├── VideoExplainer.jsx       # Embedded video tutorials
├── SevaSetuLocator.jsx      # GPS navigation to centers
└── ApplicationTracker.jsx   # Track application status
```

**Key Interfaces**:
```javascript
// Government Scheme
interface GovernmentScheme {
  id: string
  name: string
  department: string
  benefits: string[]
  eligibility: EligibilityCriteria
  applicationSteps: ApplicationStep[]
  documents: string[]
  officialUrl: string
  videoExplainers: VideoTutorial[]
  nearestCenters: SevaSetuCenter[]
}

interface EligibilityCriteria {
  ageRange?: [number, number]
  income?: { max: number, currency: string }
  occupation?: string[]
  location?: string[]
  other: string[]
}

interface ApplicationStep {
  stepNumber: number
  description: string
  estimatedTime: number
  online: boolean
  url?: string
}

interface SevaSetuCenter {
  id: string
  name: string
  address: string
  location: GeoLocation
  distance: number
  openHours: string
  phone: string
}
```

**Design Details**:
- Scheme Cards: Grid layout, government logos, benefit highlights
- AI Analysis: Conversational breakdown in simple language, bullet points
- Apply Now: Prominent CTA button, opens official portal in new tab
- Video: Auto-play explainer, subtitles in selected language
- GPS: Integrated map with turn-by-turn directions, call center button

### 7. History Viewer (Sab Dekhen)

**Purpose**: Timeline of past interactions with full context

**Component Structure**:
```
HistoryViewer/
├── HistoryTimeline.jsx      # Chronological list
├── HistoryItem.jsx          # Expandable interaction card
├── HistorySearch.jsx        # Keyword and date search
├── HistoryBookmarks.jsx     # Saved important interactions
└── HistoryExport.jsx        # Share or export history
```

**Key Interfaces**:
```javascript
// History Entry
interface HistoryEntry {
  id: string
  timestamp: Date
  module: 'drishti' | 'setu' | 'schemes' | 'chat' | 'other'
  title: string
  summary: string
  fullContext: HistoryContext
  bookmarked: boolean
  tags: string[]
}

interface HistoryContext {
  conversation: ChatMessage[]
  stepsCompleted: string[]
  videosWatched: VideoTutorial[]
  documentsViewed: string[]
  outcome: string
}

// Search
interface HistorySearch {
  query: string
  dateRange?: [Date, Date]
  modules?: string[]
  bookmarkedOnly?: boolean
}
```

**Design Details**:
- Timeline: Vertical line with date markers, cards attached
- Expandable Cards: Collapsed shows summary, expanded shows full context
- Search: Floating search bar, instant filter results
- Bookmarks: Star icon, quick access section at top
- Export: Share via WhatsApp, download as PDF

### 8. Language Switcher

**Purpose**: One-tap multilingual support

**Component Structure**:
```
LanguageSwitcher/
├── LanguageSelector.jsx     # Dropdown or modal selector
├── TranslationService.js    # Handle translations
└── LanguageContext.jsx      # Global language state
```

**Key Interfaces**:
```javascript
// Language Configuration
interface LanguageConfig {
  code: 'en' | 'hi' | 'hinglish' | 'mr'
  name: string
  nativeName: string
  flag: string
  rtl: boolean
}

// Translation Service
interface TranslationService {
  translate(key: string, language: string): string
  translateBatch(keys: string[], language: string): Record<string, string>
  detectLanguage(text: string): string
}

// Translations
interface Translations {
  [languageCode: string]: {
    [key: string]: string
  }
}
```

**Design Details**:
- Selector: Globe icon in header, modal with large language cards
- Instant Switch: All text updates within 1 second, smooth fade transition
- Voice Sync: Voice responses automatically match selected language
- Persistence: Language saved to LocalStorage, synced across devices

## Data Models

### User Profile Model
```javascript
const UserProfileSchema = {
  id: String,              // Unique identifier
  name: String,
  phone: String,
  aadharHash: String,      // Hashed for security
  location: {
    latitude: Number,
    longitude: Number,
    city: String,
    state: String,
    pincode: String
  },
  language: String,        // 'en' | 'hi' | 'hinglish' | 'mr'
  preferences: {
    voiceEnabled: Boolean,
    notificationsEnabled: Boolean,
    offlineMode: Boolean,
    highContrast: Boolean
  },
  authMethods: {
    faceId: Boolean,
    voiceId: Boolean,
    aadhar: Boolean
  },
  createdAt: Date,
  lastLogin: Date
}
```

### Interaction History Model
```javascript
const HistoryEntrySchema = {
  id: String,
  userId: String,
  timestamp: Date,
  module: String,          // 'drishti' | 'setu' | 'schemes' | 'chat'
  title: String,
  summary: String,
  context: {
    conversation: Array,   // ChatMessage[]
    steps: Array,          // String[]
    videos: Array,         // VideoTutorial[]
    outcome: String
  },
  bookmarked: Boolean,
  tags: Array,             // String[]
  syncStatus: String       // 'synced' | 'pending' | 'offline'
}
```

### Notification Model
```javascript
const NotificationSchema = {
  id: String,
  userId: String,
  type: String,            // 'mandi' | 'health' | 'scheme' | 'community'
  priority: String,        // 'high' | 'medium' | 'low'
  title: String,
  message: String,
  timestamp: Date,
  read: Boolean,
  actionable: Boolean,
  action: {
    label: String,
    type: String,          // 'navigate' | 'external' | 'call'
    target: String
  },
  expiresAt: Date
}
```

### Volunteer Model
```javascript
const VolunteerSchema = {
  id: String,
  name: String,
  photo: String,
  phone: String,
  location: {
    latitude: Number,
    longitude: Number,
    city: String
  },
  rating: Number,          // 0-5
  totalSessions: Number,
  specialties: Array,      // String[]
  available: Boolean,
  verificationStatus: String, // 'verified' | 'pending' | 'rejected'
  feedback: Array,         // VolunteerFeedback[]
  joinedAt: Date
}
```

### Scheme Model
```javascript
const SchemeSchema = {
  id: String,
  name: String,
  nameTranslations: Object, // { en: '', hi: '', mr: '' }
  department: String,
  category: String,
  benefits: Array,         // String[]
  eligibility: {
    ageRange: Array,       // [min, max]
    income: Object,        // { max: Number, currency: String }
    occupation: Array,
    location: Array,
    other: Array
  },
  applicationSteps: Array, // ApplicationStep[]
  documents: Array,        // String[]
  officialUrl: String,
  videoExplainers: Array,  // VideoTutorial[]
  lastUpdated: Date
}
```

## Correctness Properties

*A property is a characteristic or behavior that should hold true across all valid executions of a system—essentially, a formal statement about what the system should do. Properties serve as the bridge between human-readable specifications and machine-verifiable correctness guarantees.*


### Property Reflection

After analyzing all acceptance criteria, I've identified several areas where properties can be consolidated:

**Consolidation Opportunities:**
1. **Authentication timing properties (1.2, 11.3)**: Both test 3-second timing requirements - can be combined into one comprehensive authentication timing property
2. **Language consistency properties (9.3, 9.5, 11.4)**: All test language consistency across the system - can be combined
3. **Design system color properties (10.1, 10.2, 10.3)**: All test color usage - can be combined into one design system property
4. **Offline behavior properties (13.2, 13.3, 13.5, 13.6)**: Related offline functionality - can be consolidated
5. **Performance properties (14.1, 14.2, 14.3)**: All test performance metrics - can be combined
6. **Accessibility properties (14.4, 14.5, 14.6, 14.7)**: All test accessibility features - can be consolidated
7. **Round-trip properties (2.4, 5.6, 8.5, 8.6, 9.4)**: Multiple save/restore cycles - keep separate as they test different domains
8. **UI element presence (multiple "example" tests)**: Keep as unit tests rather than properties

**Properties to Keep Separate:**
- Module-specific behaviors (Drishti, Setu, Schemes) - each tests unique functionality
- Interaction behaviors - each tests different user flows
- Data display properties - each tests different data types

### Correctness Properties

#### Property 1: Authentication Method Timing
*For any* authentication method (Face ID, Voice ID, Aadhar/QR), the authentication process should complete within 3 seconds from initiation to result.

**Validates: Requirements 1.2, 11.3**

#### Property 2: Authentication Error Handling
*For any* failed authentication attempt, the system should display an error message in the user's currently selected language and allow retry without requiring navigation.

**Validates: Requirements 1.6**

#### Property 3: Responsive Layout Adaptation
*For any* viewport width, the system should render the appropriate layout (mobile for <768px, desktop for ≥768px) and adapt without page reload when viewport size changes.

**Validates: Requirements 2.1, 2.2, 2.3**

#### Property 4: Fullscreen Mode Round-Trip
*For any* application state, activating fullscreen mode and then deactivating it should return the application to its original state with all UI elements restored.

**Validates: Requirements 2.4**

#### Property 5: Touch Target Accessibility
*For all* interactive elements on mobile devices (<768px width), the touch target size should be at least 44x44 pixels to ensure accessibility.

**Validates: Requirements 2.6**

#### Property 6: Voice Interaction Visualization
*For any* voice input or bot speech, the Sarthi Bot should display real-time sound visualizer animations that reflect the audio amplitude.

**Validates: Requirements 3.2, 11.2**

#### Property 7: Real-Time Dashboard Updates
*For any* data change in weather, notifications, or hyper-local information, the dashboard should update the display without requiring page refresh.

**Validates: Requirements 3.6**

#### Property 8: Notification Priority Sorting
*For any* set of notifications, they should be organized by priority (high, medium, low) with high-priority items displayed using Deep Saffron color (#FF9933).

**Validates: Requirements 4.5**

#### Property 9: Notification Interaction Expansion
*For any* notification in the notification center, tapping it should expand the notification to show full details and available actions.

**Validates: Requirements 4.2, 4.6**

#### Property 10: Object Recognition Timing
*For any* captured image in Drishti Module, object recognition should complete and return results within 5 seconds.

**Validates: Requirements 5.2**

#### Property 11: Drishti Output Completeness
*For any* successful object recognition, the result should include voice explanation in user's language, step-by-step text checklist, and relevant YouTube tutorials.

**Validates: Requirements 5.3, 5.4, 5.5**

#### Property 12: Drishti History Round-Trip
*For any* diagnosis saved to history, retrieving it from the history should return the complete diagnosis including object type, steps, and videos.

**Validates: Requirements 5.6**

#### Property 13: Volunteer Profile Completeness
*For all* volunteers displayed in Setu Module, their profiles should include name, rating, total sessions, specialties, distance, and verification status.

**Validates: Requirements 6.3**

#### Property 14: Volunteer Booking Flow
*For any* volunteer booking, the system should enable real-time tracking, send WhatsApp confirmation, and prompt for rating upon completion.

**Validates: Requirements 6.5, 6.6, 6.7**

#### Property 15: Scheme Personalization
*For any* user profile, the Schemes Hub should display only schemes where the user meets at least one eligibility criterion.

**Validates: Requirements 7.1**

#### Property 16: Scheme Detail Completeness
*For any* selected government scheme, the detail view should display benefits, eligibility criteria, application steps, and video explainers in the user's selected language.

**Validates: Requirements 7.2, 7.4**

#### Property 17: History Timeline Ordering
*For any* set of user interactions, the history timeline should display them in reverse chronological order (newest first).

**Validates: Requirements 8.2**

#### Property 18: History Search Filtering
*For any* search query (keywords or date range), the history results should include only items that match the search criteria.

**Validates: Requirements 8.4**

#### Property 19: History Persistence Round-Trip
*For any* authenticated user, logging out and logging back in should restore their complete interaction history.

**Validates: Requirements 8.5**

#### Property 20: Bookmark Round-Trip
*For any* history item, bookmarking it and then accessing bookmarks should include that item in the bookmarked list.

**Validates: Requirements 8.6**

#### Property 21: Language Consistency
*For any* selected language, all UI text, notifications, voice responses, and module content should be translated to that language within 1 second and remain consistent across all modules.

**Validates: Requirements 9.3, 9.5, 11.4**

#### Property 22: Language Preference Persistence
*For any* language selection, logging out and logging back in should restore the user's language preference.

**Validates: Requirements 9.4**

#### Property 23: Voice Language Detection
*For any* voice input, the system should automatically detect the spoken language and respond in the same language.

**Validates: Requirements 9.6**

#### Property 24: Design System Color Consistency
*For all* UI elements, high-priority actions should use Deep Saffron (#FF9933), trust elements should use Cyber-Teal (#008080), and backgrounds should use Deep Navy or Void Black.

**Validates: Requirements 10.1, 10.2, 10.3**

#### Property 25: Glassmorphism Application
*For all* card components, the CSS should include backdrop-filter blur and semi-transparent backgrounds to achieve glassmorphism effect.

**Validates: Requirements 10.4**

#### Property 26: Animation Frame Rate
*For any* screen transition or animation, the frame rate should remain above 30 FPS on mid-range mobile devices.

**Validates: Requirements 10.7**

#### Property 27: Voice Recognition Error Handling
*For any* failed voice recognition attempt, the Sarthi Bot should prompt the user to repeat or offer alternative input methods.

**Validates: Requirements 11.7**

#### Property 28: Trust Badge Presence
*For all* screens in the application, an "End-to-End Encrypted" trust badge should be visible.

**Validates: Requirements 12.1**

#### Property 29: Verification Badge Display
*For all* volunteers in Setu Module and all schemes in Schemes Hub, verification badges or official logos should be displayed next to verified items.

**Validates: Requirements 12.4, 12.5**

#### Property 30: Offline Indicator
*For any* network connectivity loss, the system should display a clear offline indicator within 2 seconds of detection.

**Validates: Requirements 13.1**

#### Property 31: Offline Functionality
*While* offline, the system should allow access to cached history, queue user actions, and sync all queued actions when connectivity is restored.

**Validates: Requirements 13.2, 13.3, 13.5**

#### Property 32: Performance Metrics
*For any* page load on 3G network, initial load should complete within 3 seconds, cached content TTFB should be under 1 second, and total page weight should be below 2MB.

**Validates: Requirements 14.1, 14.2, 14.3**

#### Property 33: Accessibility Compliance
*For all* interactive elements, the system should support screen readers, provide high contrast mode, support keyboard navigation, and meet WCAG 2.1 Level AA guidelines.

**Validates: Requirements 14.4, 14.5, 14.6, 14.7**

## Error Handling

### Authentication Errors

**Face ID Failures**:
- Camera access denied → Display permission request with explanation
- Face not detected → Show guidance overlay with face positioning tips
- Recognition timeout → Offer alternative authentication methods
- Multiple failures → Suggest Voice ID or Aadhar scan

**Voice ID Failures**:
- Microphone access denied → Display permission request
- Phrase not recognized → Display "Main Hoon" pronunciation guide
- Background noise → Suggest quieter environment
- Multiple failures → Offer Face ID or Aadhar scan

**Network Errors**:
- Connection timeout → Retry with exponential backoff (1s, 2s, 4s)
- Server error → Display user-friendly message in selected language
- Offline mode → Queue authentication for later sync

### Camera and AR Errors

**Drishti Module Errors**:
- Camera permission denied → Explain why camera is needed, offer to retry
- Object not recognized → Suggest better lighting or different angle
- Recognition timeout (>5s) → Display loading state, offer to cancel
- No internet for YouTube → Show cached tutorials if available

**Error Recovery**:
- All errors display in user's selected language
- Provide actionable next steps (not just error codes)
- Offer alternative paths (e.g., text input if voice fails)
- Log errors for debugging without exposing technical details to user

### Data Errors

**Hyper-Local Data Failures**:
- Weather API failure → Show cached data with timestamp
- Mandi price unavailable → Display last known prices
- Location access denied → Prompt for manual location entry

**Scheme Data Errors**:
- Scheme details unavailable → Show basic info, offer to retry
- External portal link broken → Display phone number for assistance
- Video embed failure → Provide text-based instructions

### Volunteer and Booking Errors

**Setu Module Errors**:
- No volunteers available → Suggest expanding search radius
- Booking conflict → Show alternative volunteers or time slots
- Tracking failure → Fall back to estimated arrival time
- WhatsApp integration failure → Offer SMS or in-app notification

**Error Notification Strategy**:
- Critical errors: Full-screen modal with clear action
- Warning errors: Toast notification with dismiss option
- Info errors: Inline message within component
- All errors: Logged to history for user reference

### Offline Error Handling

**Graceful Degradation**:
- Queue all user actions with timestamps
- Display clear "offline" badge on all screens
- Disable features requiring real-time data (live tracking, video streaming)
- Enable cached features (history, saved guides, bookmarked schemes)

**Sync Conflict Resolution**:
- On reconnection, sync queued actions in chronological order
- If conflict detected (e.g., volunteer no longer available), notify user
- Preserve user data integrity (never lose queued actions)

## Testing Strategy

### Dual Testing Approach

Sarthi.ai requires comprehensive testing using both unit tests and property-based tests:

**Unit Tests**: Focus on specific examples, edge cases, and integration points
- Authentication flow examples (Face ID success, Voice ID with "Main Hoon")
- UI component rendering (dashboard layout, notification panel)
- Edge cases (empty notifications, no volunteers available)
- Error conditions (network failures, permission denials)
- Integration between modules (navigation, state sharing)

**Property-Based Tests**: Verify universal properties across all inputs
- Use **fast-check** library for JavaScript/TypeScript property testing
- Minimum 100 iterations per property test
- Each test tagged with: **Feature: sarthi-ai, Property {number}: {property_text}**

### Property-Based Testing Configuration

**Library**: fast-check (JavaScript/TypeScript)
```javascript
import fc from 'fast-check';

// Example property test structure
describe('Feature: sarthi-ai, Property 1: Authentication Method Timing', () => {
  it('should complete authentication within 3 seconds for any method', () => {
    fc.assert(
      fc.property(
        fc.constantFrom('face', 'voice', 'aadhar'),
        async (authMethod) => {
          const startTime = Date.now();
          await authenticate(authMethod);
          const duration = Date.now() - startTime;
          expect(duration).toBeLessThan(3000);
        }
      ),
      { numRuns: 100 }
    );
  });
});
```

**Test Configuration**:
- Minimum 100 runs per property test
- Seed-based reproducibility for failed tests
- Shrinking enabled to find minimal failing cases
- Timeout: 30 seconds per property test

### Testing Priorities

**Critical Path Testing** (Must have 100% coverage):
1. Authentication flows (all methods)
2. Voice interaction and language detection
3. Offline functionality and sync
4. Data persistence (history, bookmarks, preferences)
5. Security features (encryption badges, verification)

**High Priority Testing** (Target 90% coverage):
1. Responsive layout adaptation
2. Notification system
3. Drishti object recognition flow
4. Setu volunteer booking flow
5. Schemes Hub personalization

**Medium Priority Testing** (Target 70% coverage):
1. Animation performance
2. Design system consistency
3. Accessibility features
4. Error handling and recovery
5. WhatsApp integration

### Test Data Generation

**Generators for Property Tests**:
```javascript
// User profile generator
const userProfileArb = fc.record({
  id: fc.uuid(),
  name: fc.string({ minLength: 2, maxLength: 50 }),
  language: fc.constantFrom('en', 'hi', 'hinglish', 'mr'),
  location: fc.record({
    latitude: fc.double({ min: 8.0, max: 37.0 }),
    longitude: fc.double({ min: 68.0, max: 97.0 })
  })
});

// Notification generator
const notificationArb = fc.record({
  type: fc.constantFrom('mandi', 'health', 'scheme', 'community'),
  priority: fc.constantFrom('high', 'medium', 'low'),
  title: fc.string({ minLength: 5, maxLength: 100 }),
  message: fc.string({ minLength: 10, maxLength: 500 }),
  timestamp: fc.date()
});

// Volunteer generator
const volunteerArb = fc.record({
  id: fc.uuid(),
  name: fc.string({ minLength: 2, maxLength: 50 }),
  rating: fc.double({ min: 0, max: 5 }),
  distance: fc.double({ min: 0.1, max: 50 }),
  available: fc.boolean()
});
```

### Integration Testing

**Module Integration Tests**:
- Pehchan → Dashboard: Authentication success navigates to dashboard
- Dashboard → Drishti: Camera activation from dashboard
- Dashboard → Setu: Volunteer search from dashboard
- Dashboard → Schemes: Scheme browsing from dashboard
- Any Module → History: All interactions saved to history

**State Management Tests**:
- Language change propagates to all modules
- User profile updates reflect across components
- Notification count updates in real-time
- Offline queue persists across page reloads

### Performance Testing

**Metrics to Track**:
- Initial page load time (target: <3s on 3G)
- Time to interactive (target: <5s)
- Animation frame rate (target: >30 FPS)
- Memory usage (target: <100MB on mobile)
- Bundle size (target: <2MB total)

**Performance Test Tools**:
- Lighthouse for page load metrics
- Chrome DevTools Performance profiler
- React DevTools Profiler for component rendering
- Network throttling to simulate 3G/4G

### Accessibility Testing

**Automated Tests**:
- axe-core for WCAG compliance
- Color contrast ratio checks (minimum 4.5:1)
- Keyboard navigation flow tests
- Screen reader compatibility (ARIA labels)

**Manual Tests**:
- Screen reader testing (NVDA, JAWS, VoiceOver)
- Keyboard-only navigation
- High contrast mode verification
- Touch target size verification on real devices

### Mock Data Strategy

**Mock AWS Bedrock Responses**:
```javascript
// Mock AI responses for testing
const mockBedrockResponses = {
  objectRecognition: {
    'broken_phone': {
      objectType: 'smartphone',
      issue: 'cracked screen',
      explanation: 'Your phone screen is cracked...',
      steps: ['Clean the screen', 'Apply screen protector', 'Visit repair shop'],
      videos: [{ youtubeId: 'abc123', title: 'Phone Screen Repair' }]
    },
    'diseased_crop': {
      objectType: 'wheat plant',
      issue: 'rust disease',
      explanation: 'Your wheat has rust disease...',
      steps: ['Remove infected plants', 'Apply fungicide', 'Monitor daily'],
      videos: [{ youtubeId: 'def456', title: 'Wheat Rust Treatment' }]
    }
  },
  voiceCommands: {
    'weather': 'The weather today is sunny with a high of 32°C...',
    'schemes': 'Here are government schemes you may be eligible for...',
    'help': 'I can help you with repairs, government schemes, or finding volunteers...'
  }
};
```

### Test Environment Setup

**Development Environment**:
- Vite dev server with hot module replacement
- Mock service workers for API simulation
- Browser DevTools for debugging
- React DevTools for component inspection

**CI/CD Pipeline**:
- Run unit tests on every commit
- Run property tests on pull requests
- Run integration tests before deployment
- Generate coverage reports (target: >80%)

**Testing Devices**:
- Desktop: Chrome, Firefox, Safari (latest versions)
- Mobile: iOS Safari, Chrome Android (latest + 2 previous versions)
- Screen sizes: 320px, 375px, 768px, 1024px, 1920px
- Network conditions: 3G, 4G, WiFi, Offline

### Continuous Monitoring

**Production Monitoring**:
- Error tracking (Sentry or similar)
- Performance monitoring (Web Vitals)
- User analytics (anonymized)
- A/B testing for UI improvements

**Success Metrics**:
- Authentication success rate >95%
- Average session duration >5 minutes
- Feature adoption rate (Drishti, Setu, Schemes)
- User retention rate (7-day, 30-day)
- Error rate <1% of sessions

## Implementation Notes

### Development Workflow

1. **Setup Phase**:
   - Initialize Vite + React project
   - Configure Tailwind with custom Bharat Cyberpunk theme
   - Set up Framer Motion and Lucide React
   - Create mock data structure for AWS Bedrock simulation

2. **Component Development Order**:
   - Design system components (buttons, cards, badges)
   - Layout components (responsive wrappers)
   - Pehchan Module (authentication)
   - Dashboard with Sarthi Bot
   - Notification Center
   - Drishti Module
   - Setu Module
   - Schemes Hub
   - History Viewer
   - Language Switcher

3. **Integration Phase**:
   - Connect all modules to global state
   - Implement routing and navigation
   - Add offline support with service workers
   - Integrate mock AI responses

4. **Polish Phase**:
   - Refine animations and transitions
   - Optimize performance (code splitting, lazy loading)
   - Add accessibility features
   - Conduct user testing with target audience

### Key Technical Decisions

**Why React Context over Redux**:
- Simpler for moderate state complexity
- No external dependencies
- Built-in React feature
- Sufficient for Sarthi.ai's state needs

**Why Vite over Create React App**:
- Faster development builds (ESBuild)
- Better hot module replacement
- Smaller production bundles
- Modern tooling

**Why Mock Data over Real Backend**:
- Faster prototyping and iteration
- No backend infrastructure needed initially
- Easy to demonstrate and test
- Can be replaced with real API later

**Why Web APIs over Native**:
- Cross-platform (works on any device with browser)
- No app store approval needed
- Instant updates
- Progressive Web App capabilities

### Deployment Considerations

**Hosting Requirements**:
- Static hosting (Vercel, Netlify, or AWS S3 + CloudFront)
- HTTPS required (for camera, geolocation, service workers)
- CDN for fast global delivery
- Gzip/Brotli compression enabled

**Progressive Web App**:
- Service worker for offline support
- Web app manifest for "Add to Home Screen"
- App-like experience on mobile
- Push notifications for alerts

**Localization**:
- JSON files for each language
- Dynamic import for language bundles
- Fallback to English if translation missing
- Right-to-left support (future: Urdu)

### Security Considerations

**Data Protection**:
- No sensitive data stored in LocalStorage (use IndexedDB with encryption)
- Aadhar numbers hashed before storage
- HTTPS-only communication
- Content Security Policy headers

**Privacy**:
- Minimal data collection
- User consent for camera, microphone, location
- Clear privacy policy in simple language
- Option to delete all user data

**Authentication**:
- Biometric data never leaves device
- Token-based authentication for API calls
- Session timeout after 30 minutes of inactivity
- Secure logout clears all local data

This design provides a comprehensive blueprint for building Sarthi.ai as a revolutionary digital lifeline for India's next billion users, combining cutting-edge technology with radical simplicity and cultural sensitivity.
