# EczeManage App - Complete Documentation

A personal informatics mobile app for eczema management among Filipinos, featuring AI-powered severity assessment, environmental data integration, and personalized recommendations.

## Table of Contents

- [Project Overview](#-project-overview)
- [Key Features](#-key-features)
- [Architecture](#-architecture)
- [Folder Structure](#-folder-structure)
- [Custom Components](#-custom-components)
- [Getting Started](#-getting-started)
- [Flutter Resources](#-flutter-resources)
- [Development Guidelines](#-development-guidelines)
- [Documentation](#-documentation)
- [Performance & Testing](#-performance--testing)

---

## Project Overview

EczeManage is a Flutter-based mobile application designed to help users track and manage their eczema condition through:

- **Care Routine Tracking** - Log daily skincare routines and products
- **Trigger Identification** - Track and analyze eczema triggers
- **Body Mapping** - Visual body part selection for affected areas
- **Progress Monitoring** - Historical data and pattern analysis
- **User Onboarding** - Guided setup for new users

---

## Architecture

### Design Patterns
- **Component-Based Architecture** - Reusable custom widgets
- **Feature-Based Organization** - Grouped by functionality
- **Local Storage** - SharedPreferences for data persistence
- **Model-View Pattern** - Clear separation of data and UI

### Technology Stack
- **Framework:** Flutter 3.x
- **Language:** Dart 3.x
- **State Management:** setState (StatefulWidget)
- **Local Storage:** SharedPreferences
- **Authentication:** Firebase Auth
- **Backend:** Firebase (Firestore, Analytics)
- **Fonts:** Google Fonts (Quicksand, OpenSans)

---

## Folder Structure

```
lib/
├── core/                                         # Core utilities and shared resources
│   ├── auth/                                     # Authentication utilities
│   │   └── auth_wrapper.dart                     # Auto-login session handler
│   ├── constants/                                # App-wide constants
│   │   ├── app_colors.dart                       # Color palette
│   │   ├── app_text_styles.dart                  # Typography styles
│   │   ├── app_header.dart                       # Standard app header
│   │   └── app_bottom_navigation.dart            # Bottom nav bar
│   └── widgets/                                  # Custom reusable components
│       ├── custom_header.dart                    # Page headers
│       ├── custom_input_field.dart               # Text inputs
│       ├── custom_dropdown.dart                  # Dropdowns
│       ├── custom_icon_button.dart               # Icon buttons
│       ├── custom_search_bar.dart                # Search functionality
│       ├── custom_stat_card.dart                 # Statistics display
│       ├── custom_empty_state.dart               # Empty state handling
│       ├── custom_chip.dart                      # Selectable chips
│       ├── custom_slider.dart                    # Advanced sliders
│       └── index.dart                            # Barrel exports
├── config/                                       # Configuration files
│   └── firebase_options.dart                     # Firebase configuration
├── models/                                       # Data models
│   ├── trigger_model.dart                        # Trigger data structure
│   ├── user_model.dart                           # User information
│   ├── daily_log_model.dart                      # Daily tracking
│   ├── flareup_log_model.dart                    # Flare-up tracking
│   ├── weekly_log_model.dart                     # Weekly assessments
│   ├── environment_log_model.dart                # Environmental data
│   └── onboarding_data_model.dart                # User onboarding data
├── services/                                     # Business logic and data services
│   ├── trigger_storage.dart                      # Trigger CRUD operations
│   ├── care_routine_storage.dart                 # Care routine CRUD
│   ├── auth_service.dart                         # Authentication & user management
│   ├── session_service.dart                      # Session & "Remember Me" handling
│   ├── firestore_services.dart                   # Firebase integration
│   └── notification_service.dart                 # Push notifications
├── utils/                                        # Utility functions
│   └── seed_data.dart                            # Database seeding for testing
├── screens/                                      # UI screens (detailed below)
│   ├── welcome/                                  # App entry point
│   ├── onboarding/                               # 6-step user setup flow
│   ├── login/                                    # Authentication
│   │   ├── login_page.dart                       # Login with error handling
│   │   └── forgot_password_page.dart             # Password reset
│   ├── dashboard/                                # Main dashboard
│   │   ├── dashboard_screen.dart                 # Home screen with stats
│   │   ├── account_edit_page.dart                # User profile editing
│   │   ├── poem_dashboard_page.dart              # POEM assessment
│   │   ├── skin_analysis_page.dart               # Skin condition analysis
│   │   └── weather_page.dart                     # Environmental data
│   ├── careRoutinePage/                          # Care routine management
│   │   ├── care_routine_page.dart                # Add/edit routines
│   │   ├── care_routine_history.dart             # View past routines
│   │   └── body_map_selector.dart                # Visual body mapping
│   ├── triggersPage/                             # Trigger tracking
│   ├── insightsPage/                             # Analytics & insights
│   ├── consent/                                  # Privacy compliance
│   └── test/                                     # Testing utilities
│       └── notification_test_screen.dart         # Notification testing
└── main.dart                                     # App entry point with AuthWrapper
```

---

## Key Features

### 1. Authentication & Session Management
- **Welcome Screen** - App entry with branding
- **Login/Signup** - Firebase authentication with error handling
- **Remember Me** - 14-day secure session management (industry standard)
- **Auto-Login** - Automatic authentication on app restart
- **Forgot Password** - Email verification and password reset flow
- **Smart Error Detection** - Field-specific error highlighting (email vs password)
- **Account Management** - Edit profile with hamburger menu drawer
- **Logout** - Session clearing with redirect to login page

### 2. User Onboarding
- **6-Step Setup Flow** - Comprehensive user information collection
  - Step 1: Eczema diagnosis timeline (when first diagnosed)
  - Step 2: Current severity assessment (1-10 scale)
  - Step 3: Affected body areas selection
  - Step 4: Common triggers identification (predefined categories)
  - Step 5: Management goals selection
  - Step 6: Personal information (name, gender, birthdate, email, password)
- **Privacy Consent** - Medical data consent with GDPR compliance
- **Welcome Screen Description** - "Your personal companion for managing eczema with confidence"
- **Data Validation** - Complete form validation before proceeding
- **Back Navigation** - Step 1 includes back button to return to welcome screen

### 3. Care Routine Management
- **Add/Edit Routines** - Form-based routine creation
- **Body Map Selection** - Visual area selection
- **History Tracking** - View all saved routines
- **Search & Filter** - Find specific routines
- **Statistics** - Usage metrics
- **Notification System** - Reminder notifications with testing tools
- **Debug Tools** - 3-button debug panel (Check Pending, Test Now, Notification Test)

### 4. Trigger Tracking
- **Trigger Categories** - Four predefined categories:
  - Environmental (dust mites, pollen, weather, etc.)
  - Food & Diet (dairy, nuts, gluten, etc.)
  - Personal Care (fragrances, soaps, detergents, etc.)
  - Lifestyle & Health (stress, sleep, hormones, etc.)
- **Severity Assessment** - 1-10 scale with visual feedback
- **Confidence Levels** - Optional certainty tracking
- **Symptom Mapping** - Multi-select symptoms
- **Pattern Analysis** - Historical trigger data
- **Search & Filter** - Quick trigger search across all categories
- **No Custom Triggers** - Only predefined triggers available for consistency

### 5. Dashboard & Analytics
- **Personalized Dashboard** - Welcome message with user's first name
- **Real-time Stats** - Daily and weekly logs
- **Severity Tracking** - POEM score-based severity assessment
- **Hamburger Menu** - Side drawer with:
  - User profile display (avatar, name, email)
  - Account editing
  - Logout with confirmation
- **Weather Integration** - Environmental data sync

### 6. Data Management
- **Local Storage** - SharedPreferences for preferences
- **Cloud Storage** - Firebase Firestore for user data
- **Session Management** - 14-day "Remember Me" with automatic expiration
- **CRUD Operations** - Full data lifecycle
- **Data Security** - No password storage in local preferences

---

## Custom Components

Our app uses a comprehensive set of custom widgets for consistency and performance:

### Core UI Components
| Component | Purpose | Usage |
|-----------|---------|--------|
| `CustomHeader` | Page headers with navigation | `CustomHeader(title: 'Page Title')` |
| `CustomInputField` | Text input fields | `CustomInputField(label: 'Name', controller: _controller)` |
| `CustomDropdown` | Selection dropdowns | `CustomDropdown<String>(items: options, onChanged: _callback)` |
| `CustomSearchBar` | Search functionality | `CustomSearchBar(onChanged: _search)` |

### Specialized Components
| Component | Purpose | Usage |
|-----------|---------|--------|
| `CustomSlider` | Advanced sliders with types | `CustomSlider(sliderType: CustomSliderType.severity)` |
| `CustomChip` | Selectable tags/chips | `CustomChip(label: 'Tag', isSelected: true)` |
| `CustomStatCard` | Statistics display | `CustomStatCard(title: 'Total', value: '25')` |
| `CustomEmptyState` | No data states | `CustomEmptyState(icon: Icons.info, title: 'Empty')` |

### Benefits
- **50% Code Reduction** - Eliminated repetitive UI code
- **Consistent Design** - Unified look and feel
- **Better Performance** - Optimized widget trees
- **Easy Maintenance** - Single source of truth for styling

---

## Getting Started

### Prerequisites
```bash
Flutter SDK 3.x+
Dart SDK 3.x+
Android Studio / VS Code
Android SDK / Xcode (for deployment)
```

### Installation
```bash
# Clone the repository
git clone <repository-url>
cd CAP2439IS_ECZEMA

# Install dependencies
flutter pub get

# Run the app
flutter run
```

### Development Setup
```bash
# Check Flutter doctor
flutter doctor

# Run in debug mode
flutter run --debug

# Build for release
flutter build apk --release
flutter build ios --release
```

---

## Flutter Resources

If this is your first Flutter project, here are some helpful resources to get you started:

### Official Documentation
- **[Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)** - Step-by-step tutorial
- **[Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)** - Common use cases and solutions
- **[Flutter Documentation](https://docs.flutter.dev/)** - Complete reference with tutorials, samples, and API docs

### Learning Path
1. **Flutter Basics** - Widgets, layouts, and navigation
2. **State Management** - Understanding setState and advanced patterns
3. **Platform Integration** - Working with device features
4. **Performance** - Optimizing app performance
5. **Testing** - Unit, widget, and integration testing

### Helpful Commands
```bash
# Check Flutter setup
flutter doctor

# Create new project
flutter create my_app

# Run app in debug mode
flutter run

# Hot reload (while app is running)
r

# Hot restart (while app is running)
R

# Build release version
flutter build apk --release
```

---

## 📐 Development Guidelines

### Code Style
- **Naming:** camelCase for variables, PascalCase for classes
- **Formatting:** Use `dart format` for consistent formatting
- **Imports:** Group imports (dart, flutter, package, relative)
- **Comments:** Document public APIs and complex logic

### Widget Guidelines
```dart
// ✅ Good: Use custom components
CustomInputField(
  label: 'Product Name',
  controller: nameController,
)

// ❌ Avoid: Repetitive custom styling
Container(
  decoration: BoxDecoration(
    color: AppColors.lightGrey,
    borderRadius: BorderRadius.circular(12),
  ),
  child: TextField(...),
)
```

### State Management
```dart
// ✅ Good: Clear state organization
class _MyPageState extends State<MyPage> {
  // Controllers
  final TextEditingController _controller = TextEditingController();

  // State variables
  String selectedValue = 'default';
  bool isLoading = false;

  // Lifecycle methods
  @override
  void initState() { /* ... */ }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }
}
```

### Navigation Patterns
```dart
// ✅ Good: Consistent navigation
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => TargetPage()),
);

// ✅ Good: Navigation with data
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => EditPage(item: existingItem),
  ),
);
```

### Error Handling
```dart
// ✅ Good: Proper error handling
try {
  await StorageService.saveItem(item);
  _showSuccessMessage();
} catch (e) {
  _showErrorMessage('Failed to save: $e');
}
```

---

## Documentation

### Available Documentation
- **[Widgets Documentation](widgets_documentation.md)** - Complete guide to custom components
- **[Screens Documentation](screens_documentation.md)** - All screens and navigation flows
- **[Architecture Documentation](README.md)** - This file

### Quick Reference
```dart
// Import all custom widgets
import '../../core/widgets/index.dart';

// Import app constants
import '../../core/constants/app_colors.dart';
import '../../core/constants/app_button_styles.dart';

// Import services
import '../../services/trigger_storage.dart';
import '../../services/care_routine_storage.dart';
```

---

## Design System

### Color Palette
```dart
AppColors.primaryBlue     // #007AFF - Primary actions
AppColors.darkBlue        // #003366 - Text headings
AppColors.lightGrey       // #F5F5F5 - Input backgrounds
AppColors.greyText        // #666666 - Secondary text
AppColors.white           // #FFFFFF - Card backgrounds
```

### Typography
```dart
GoogleFonts.quicksand     // Headings, titles, values
GoogleFonts.openSans      // Body text, labels, buttons
```

### Spacing System
```dart
8px   // Small gaps between related elements
12px  // Medium gaps, standard border radius
16px  // Large gaps, input padding
24px  // Section spacing, page margins
```

---

## Performance Optimizations

### Custom Components Benefits
- **Widget Reuse** - Single component, multiple instances
- **Tree Optimization** - Flutter's widget tree optimization
- **Memory Efficiency** - Shared styling and behavior
- **Bundle Size** - Reduced code duplication

### Best Practices
- Use `const` constructors where possible
- Dispose controllers in `dispose()` method
- Use `ListView.builder` for long lists
- Implement efficient search with `filteredItems` getters

---

## Testing Strategy

### Unit Testing
- Model serialization/deserialization
- Storage service operations
- Business logic validation

### Widget Testing
- Custom component behavior
- Form validation
- Navigation flows

### Integration Testing
- Complete user journeys
- Data persistence
- Cross-screen navigation

---

## Platform Support

### Android
- Minimum SDK: 21 (Android 5.0)
- Target SDK: 34
- Supports: Material Design 3

### iOS
- Minimum iOS: 12.0
- Target iOS: 17.0
- Supports: Cupertino widgets

---

## Future Enhancements

### Planned Features
- **Data Export** - CSV/PDF export functionality
- **Cloud Sync** - Firebase Firestore integration
- **Notifications** - Reminder system
- **Analytics** - Advanced pattern recognition
- **Sharing** - Export reports to healthcare providers

### Technical Improvements
- **State Management** - Migrate to Riverpod/Bloc
- **Testing** - Comprehensive test coverage
- **Accessibility** - Enhanced a11y support
- **Internationalization** - Multi-language support

---

---

## Performance & Testing

### Performance Metrics
- **50% Code Reduction** - Custom components eliminated repetitive code
- **Faster Builds** - Optimized widget trees improve compilation
- **Memory Efficiency** - Shared components reduce memory footprint
- **Bundle Size** - Smaller APK due to code reuse

### Testing Strategy
```bash
# Run all tests
flutter test

# Run tests with coverage
flutter test --coverage

# Run integration tests
flutter drive --target=test_driver/app.dart
```

### Performance Monitoring
- Use Flutter DevTools for performance profiling
- Monitor widget rebuilds and memory usage
- Test on real devices for accurate performance data
- Use const constructors to optimize widget creation

---

## Contributing

### Code Standards
- Follow the documented component patterns
- Use custom widgets instead of creating new styling
- Add tests for new functionality (soon)
- Update documentation for new features

### Pull Request Process
1. Create feature branch from main
2. Implement changes following guidelines
3. Add tests and documentation
4. Submit PR with clear description

---

## 📄 License

This project is part of CAP2439 Information Systems coursework focusing on mobile app development for healthcare management.
