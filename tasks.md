# Implementation Tasks: Sarthi.ai

## Phase 1: Project Setup and Foundation

### 1. Project Initialization
- [ ] 1.1 Initialize Vite + React project with TypeScript support
- [ ] 1.2 Configure Tailwind CSS with custom Bharat Cyberpunk theme (Deep Saffron #FF9933, Cyber-Teal #008080, Deep Navy/Void Black)
- [ ] 1.3 Install and configure dependencies (Framer Motion, Lucide React, React Router v6, fast-check)
- [ ] 1.4 Set up project structure with folders for components, services, contexts, and mock data
- [ ] 1.5 Configure Vite for optimal production builds (code splitting, lazy loading)

### 2. Design System Components
- [ ] 2.1 Create base Button component with Deep Saffron primary and Cyber-Teal secondary variants
- [ ] 2.2 Create Card component with glassmorphism effects (backdrop-blur, semi-transparent backgrounds)
- [ ] 2.3 Create Badge component for trust indicators and verification badges
- [ ] 2.4 Create Input components with neumorphism effects (soft, tactile shadows)
- [ ] 2.5 Create Modal component with fluid animations using Framer Motion
- [ ] 2.6 Write unit tests for all design system components
- [ ] 2.7 Write property-based test for Property 24: Design System Color Consistency

### 3. Layout and Responsive Framework
- [ ] 3.1 Create ResponsiveLayout component that adapts to mobile (<768px) and desktop (≥768px)
- [ ] 3.2 Implement fullscreen mode toggle functionality
- [ ] 3.3 Create HUD component for date, time, timezone, and trust badge display
- [ ] 3.4 Ensure all interactive elements have minimum 44x44px touch targets on mobile
- [ ] 3.5 Write unit tests for responsive layout behavior
- [ ] 3.6 Write property-based test for Property 3: Responsive Layout Adaptation
- [ ] 3.7 Write property-based test for Property 4: Fullscreen Mode Round-Trip
- [ ] 3.8 Write property-based test for Property 5: Touch Target Accessibility

## Phase 2: Authentication System (Pehchan Module)

### 4. Authentication Context and State
- [ ] 4.1 Create AuthContext with user profile, auth method, loading, and error states
- [ ] 4.2 Implement authentication state management with useReducer
- [ ] 4.3 Create mock authentication service with simulated delays
- [ ] 4.4 Implement session persistence using LocalStorage
- [ ] 4.5 Write unit tests for authentication state management

### 5. Biometric Authentication UI
- [ ] 5.1 Create LoginScreen component with four authentication options
- [ ] 5.2 Create FaceIDScanner component with animated scanning overlay and pulsing rings
- [ ] 5.3 Create VoiceIDCapture component with pulsing microphone and waveform visualization
- [ ] 5.4 Create AadharQRScanner component with camera viewfinder and corner guides
- [ ] 5.5 Implement fluid transition animation from login to dashboard (800ms duration)
- [ ] 5.6 Implement error handling with language-specific error messages
- [ ] 5.7 Write unit tests for each authentication method
- [ ] 5.8 Write property-based test for Property 1: Authentication Method Timing
- [ ] 5.9 Write property-based test for Property 2: Authentication Error Handling

## Phase 3: Living Dashboard

### 6. Sarthi Bot (Holographic Orb)
- [ ] 6.1 Create SarthiBot component with pulsing holographic orb (gradient saffron to teal)
- [ ] 6.2 Implement sound visualizer with radial bars reactive to voice amplitude
- [ ] 6.3 Add orb animations (scale 1.0 to 1.1 on interaction, continuous rotation)
- [ ] 6.4 Implement bot state management (idle, listening, speaking, thinking, error)
- [ ] 6.5 Integrate Web Speech API for voice recognition and synthesis
- [ ] 6.6 Write unit tests for bot state transitions
- [ ] 6.7 Write property-based test for Property 6: Voice Interaction Visualization

### 7. Dashboard Components
- [ ] 7.1 Create DashboardLayout component with central orb and surrounding widgets
- [ ] 7.2 Create WeatherWidget with real-time forecast and future predictions
- [ ] 7.3 Create NotificationIcon with unread count badge
- [ ] 7.4 Implement real-time dashboard updates without page refresh
- [ ] 7.5 Create mock hyper-local data service (weather, mandi prices, alerts)
- [ ] 7.6 Write unit tests for dashboard components
- [ ] 7.7 Write property-based test for Property 7: Real-Time Dashboard Updates

### 8. Notification Center
- [ ] 8.1 Create NotificationPanel component with glass-panel slide-out animation
- [ ] 8.2 Create NotificationItem component with expandable details
- [ ] 8.3 Implement notification priority sorting (high, medium, low)
- [ ] 8.4 Apply Deep Saffron color to high-priority notifications
- [ ] 8.5 Create NotificationService for fetching and managing notifications
- [ ] 8.6 Implement notification expansion on tap
- [ ] 8.7 Write unit tests for notification center
- [ ] 8.8 Write property-based test for Property 8: Notification Priority Sorting
- [ ] 8.9 Write property-based test for Property 9: Notification Interaction Expansion

## Phase 4: AR Vision Mode (Drishti Module)

### 9. Camera and Object Recognition
- [ ] 9.1 Create CameraView component with live camera feed and capture button
- [ ] 9.2 Implement CameraService using MediaDevices API with permission handling
- [ ] 9.3 Create ObjectRecognition component with loading animation (scanning lines)
- [ ] 9.4 Create mock object recognition service simulating AWS Bedrock responses
- [ ] 9.5 Ensure recognition completes within 5 seconds
- [ ] 9.6 Write unit tests for camera service and object recognition
- [ ] 9.7 Write property-based test for Property 10: Object Recognition Timing

### 10. Drishti Results and Guidance
- [ ] 10.1 Create VoiceExplainer component with text-to-speech and transcript display
- [ ] 10.2 Create StepChecklist component with interactive checkboxes
- [ ] 10.3 Create VideoEmbed component for YouTube tutorial integration
- [ ] 10.4 Implement automatic Hindi tutorial fetching
- [ ] 10.5 Create DiagnosisHistory component for saving and reviewing past scans
- [ ] 10.6 Write unit tests for Drishti results components
- [ ] 10.7 Write property-based test for Property 11: Drishti Output Completeness
- [ ] 10.8 Write property-based test for Property 12: Drishti History Round-Trip

## Phase 5: Volunteer Bridge (Setu Module)

### 11. Volunteer Discovery and Profiles
- [ ] 11.1 Create MadadButton component (large, pulsing Deep Saffron button)
- [ ] 11.2 Create VolunteerMap component with Uber-style radar and pulsing rings
- [ ] 11.3 Create VolunteerCard component with glassmorphism, ratings, and "Book Now" CTA
- [ ] 11.4 Create mock volunteer service with nearby volunteer data
- [ ] 11.5 Implement geolocation service for distance calculation
- [ ] 11.6 Write unit tests for volunteer discovery
- [ ] 11.7 Write property-based test for Property 13: Volunteer Profile Completeness

### 12. Volunteer Interaction and Booking
- [ ] 12.1 Create ChatInterface component (WhatsApp-style with voice message support)
- [ ] 12.2 Create AudioCall component for voice call integration
- [ ] 12.3 Create BookingFlow component with real-time tracking
- [ ] 12.4 Implement WhatsApp integration for booking confirmations
- [ ] 12.5 Create RatingFeedback component for post-session rating
- [ ] 12.6 Write unit tests for booking flow
- [ ] 12.7 Write property-based test for Property 14: Volunteer Booking Flow

## Phase 6: Government Schemes Hub

### 13. Schemes Discovery and Personalization
- [ ] 13.1 Create SchemesList component with grid layout and government logos
- [ ] 13.2 Implement scheme personalization based on user eligibility
- [ ] 13.3 Create mock schemes service with government scheme data
- [ ] 13.4 Write unit tests for scheme personalization
- [ ] 13.5 Write property-based test for Property 15: Scheme Personalization

### 14. Scheme Details and Application
- [ ] 14.1 Create SchemeDetail component with benefits, eligibility, and steps
- [ ] 14.2 Create EligibilityChecker component with AI-powered analysis
- [ ] 14.3 Create ApplicationGuide component with step-by-step process
- [ ] 14.4 Create VideoExplainer component with language-specific tutorials
- [ ] 14.5 Create SevaSetuLocator component with GPS navigation
- [ ] 14.6 Implement "Apply Now" buttons linking to official portals
- [ ] 14.7 Write unit tests for scheme details
- [ ] 14.8 Write property-based test for Property 16: Scheme Detail Completeness

## Phase 7: History and Context Preservation

### 15. History Timeline and Search
- [ ] 15.1 Create HistoryTimeline component with chronological list
- [ ] 15.2 Create HistoryItem component with expandable details
- [ ] 15.3 Implement reverse chronological ordering (newest first)
- [ ] 15.4 Create HistorySearch component with keyword and date range filters
- [ ] 15.5 Implement history persistence using IndexedDB
- [ ] 15.6 Write unit tests for history timeline
- [ ] 15.7 Write property-based test for Property 17: History Timeline Ordering
- [ ] 15.8 Write property-based test for Property 18: History Search Filtering
- [ ] 15.9 Write property-based test for Property 19: History Persistence Round-Trip

### 16. Bookmarks and Export
- [ ] 16.1 Create HistoryBookmarks component with quick access section
- [ ] 16.2 Implement bookmark functionality with star icon
- [ ] 16.3 Create HistoryExport component for sharing via WhatsApp or PDF
- [ ] 16.4 Write unit tests for bookmarks
- [ ] 16.5 Write property-based test for Property 20: Bookmark Round-Trip

## Phase 8: Multilingual Support

### 17. Language System
- [ ] 17.1 Create LanguageContext with global language state
- [ ] 17.2 Create LanguageSelector component with modal and large language cards
- [ ] 17.3 Create translation JSON files for English, Hindi, Hinglish, and Marathi
- [ ] 17.4 Implement TranslationService with dynamic imports
- [ ] 17.5 Ensure all UI text updates within 1 second of language change
- [ ] 17.6 Implement language preference persistence using LocalStorage
- [ ] 17.7 Write unit tests for translation service
- [ ] 17.8 Write property-based test for Property 21: Language Consistency
- [ ] 17.9 Write property-based test for Property 22: Language Preference Persistence

### 18. Voice Language Detection
- [ ] 18.1 Implement automatic language detection for voice input
- [ ] 18.2 Ensure voice responses match detected language
- [ ] 18.3 Write unit tests for language detection
- [ ] 18.4 Write property-based test for Property 23: Voice Language Detection

## Phase 9: Trust and Security

### 19. Trust Indicators
- [ ] 19.1 Create TrustBadge component with "End-to-End Encrypted" label
- [ ] 19.2 Display trust badge on all screens using Cyber-Teal color
- [ ] 19.3 Implement trust badge explanation modal
- [ ] 19.4 Add verification badges to volunteers and schemes
- [ ] 19.5 Write unit tests for trust indicators
- [ ] 19.6 Write property-based test for Property 28: Trust Badge Presence
- [ ] 19.7 Write property-based test for Property 29: Verification Badge Display

## Phase 10: Offline Support

### 20. Offline Functionality
- [ ] 20.1 Implement service worker for offline support
- [ ] 20.2 Create offline indicator component
- [ ] 20.3 Implement action queuing for offline mode
- [ ] 20.4 Implement data caching with timestamps
- [ ] 20.5 Implement automatic sync when connectivity is restored
- [ ] 20.6 Write unit tests for offline functionality
- [ ] 20.7 Write property-based test for Property 30: Offline Indicator
- [ ] 20.8 Write property-based test for Property 31: Offline Functionality

## Phase 11: Performance and Accessibility

### 21. Performance Optimization
- [ ] 21.1 Implement code splitting and lazy loading for routes
- [ ] 21.2 Optimize images and assets (compress, use WebP)
- [ ] 21.3 Ensure total page weight is below 2MB
- [ ] 21.4 Implement performance monitoring (Web Vitals)
- [ ] 21.5 Test on 3G network and ensure initial load within 3 seconds
- [ ] 21.6 Write unit tests for performance metrics
- [ ] 21.7 Write property-based test for Property 32: Performance Metrics

### 22. Accessibility Features
- [ ] 22.1 Add ARIA labels to all interactive elements
- [ ] 22.2 Implement keyboard navigation support
- [ ] 22.3 Create high contrast mode toggle
- [ ] 22.4 Ensure color contrast meets WCAG 2.1 Level AA (minimum 4.5:1)
- [ ] 22.5 Test with screen readers (NVDA, JAWS, VoiceOver)
- [ ] 22.6 Write unit tests for accessibility features
- [ ] 22.7 Write property-based test for Property 33: Accessibility Compliance

## Phase 12: Animation and Polish

### 23. Animation System
- [ ] 23.1 Implement fluid transitions between screens using Framer Motion
- [ ] 23.2 Add water-like animations for state changes
- [ ] 23.3 Ensure animation frame rate stays above 30 FPS on mid-range devices
- [ ] 23.4 Add stagger animations for lists (50ms delay between items)
- [ ] 23.5 Implement spring physics for interactive elements
- [ ] 23.6 Write unit tests for animation performance
- [ ] 23.7 Write property-based test for Property 26: Animation Frame Rate

### 24. Glassmorphism and Neumorphism
- [ ] 24.1 Apply glassmorphism to all card components (backdrop-blur-lg, bg-opacity-10)
- [ ] 24.2 Apply neumorphism to interactive elements (soft shadows)
- [ ] 24.3 Ensure design consistency across all modules
- [ ] 24.4 Write unit tests for design system application
- [ ] 24.5 Write property-based test for Property 25: Glassmorphism Application

## Phase 13: Voice Interaction

### 25. Voice System
- [ ] 25.1 Integrate Web Speech API for voice recognition
- [ ] 25.2 Integrate Web Speech API for voice synthesis
- [ ] 25.3 Implement voice command processing with mock AI responses
- [ ] 25.4 Add voice error handling with retry and alternative input options
- [ ] 25.5 Display text transcription of voice input and responses
- [ ] 25.6 Write unit tests for voice system
- [ ] 25.7 Write property-based test for Property 27: Voice Recognition Error Handling

## Phase 14: Integration and Testing

### 26. Module Integration
- [ ] 26.1 Connect all modules to global state (AuthContext, LanguageContext)
- [ ] 26.2 Implement routing with React Router v6
- [ ] 26.3 Test navigation between all modules
- [ ] 26.4 Ensure state persistence across navigation
- [ ] 26.5 Write integration tests for module interactions

### 27. Mock Data and Services
- [ ] 27.1 Create comprehensive mock data for all features
- [ ] 27.2 Implement mock AWS Bedrock responses for AI interactions
- [ ] 27.3 Create mock services for weather, mandi prices, and schemes
- [ ] 27.4 Implement mock volunteer and booking data
- [ ] 27.5 Write unit tests for mock services

### 28. End-to-End Testing
- [ ] 28.1 Test complete authentication flow (all methods)
- [ ] 28.2 Test complete Drishti flow (camera to results)
- [ ] 28.3 Test complete Setu flow (search to booking)
- [ ] 28.4 Test complete Schemes flow (browse to apply)
- [ ] 28.5 Test offline mode and sync
- [ ] 28.6 Test language switching across all modules

## Phase 15: Deployment and PWA

### 29. Progressive Web App
- [ ] 29.1 Create web app manifest for "Add to Home Screen"
- [ ] 29.2 Configure service worker for offline support
- [ ] 29.3 Add app icons for various platforms
- [ ] 29.4 Test PWA installation on mobile devices
- [ ] 29.5 Write unit tests for PWA functionality

### 30. Production Build and Deployment
- [ ] 30.1 Configure Vite for optimized production build
- [ ] 30.2 Enable Gzip/Brotli compression
- [ ] 30.3 Set up static hosting (Vercel, Netlify, or AWS S3 + CloudFront)
- [ ] 30.4 Configure HTTPS and CDN
- [ ] 30.5 Set up Content Security Policy headers
- [ ] 30.6 Test production build on multiple devices and browsers
- [ ] 30.7 Set up error tracking and performance monitoring

## Notes

- All property-based tests should use fast-check library with minimum 100 iterations
- Each property test should be tagged with: **Feature: sarthi-ai, Property {number}: {property_text}**
- All components should be tested on mobile (<768px) and desktop (≥768px) viewports
- All text should support English, Hindi, Hinglish, and Marathi languages
- All animations should maintain >30 FPS on mid-range mobile devices
- Total page weight should be <2MB
- Initial page load should be <3 seconds on 3G networks
