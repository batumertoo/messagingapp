# Real-time Messaging App

A cross-platform real-time messaging application built with Flutter and Firebase, demonstrating modern mobile development practices including real-time data synchronization, secure authentication, and responsive UI design.

## 📱 Features

- **Real-time Messaging**: Instant message delivery and synchronization across all connected devices using Firebase Realtime Database
- **Anonymous Authentication**: Secure access to the chat system without requiring user registration
- **Username-based Chat**: Simple username entry to join the conversation
- **Modern UI**: Clean, Material Design 3 interface with message bubbles
- **Message Timestamps**: Formatted timestamps showing when each message was sent (HH:mm format)
- **User-specific Message Styling**: Different colors for own messages vs. others' messages
- **Cross-platform Support**: Works on Android, iOS, Web, Windows, Linux, and macOS

## 🏗️ Architecture

The application follows a simple yet effective architecture:

### Main Components

1. **UserSelectionPage**: Entry screen where users enter their username
2. **MessagingPage**: Main chat interface with real-time message display
3. **Message Model**: Data class representing individual messages

### Data Flow

```
User Input → Firebase Realtime Database → Stream Listener → UI Update
```

Messages are stored in Firebase Realtime Database with the following structure:
```json
{
  "messages": {
    "uniqueId": {
      "username": "string",
      "text": "string",
      "timestamp": "number (milliseconds)"
    }
  }
}
```

## 🛠️ Technology Stack

- **Framework**: Flutter 3.x
- **Language**: Dart 3.x
- **Backend Services**:
  - Firebase Core (^3.6.0)
  - Firebase Realtime Database (^11.1.4)
  - Firebase Authentication (^5.1.0)
- **Utilities**:
  - intl (^0.19.0) - For timestamp formatting
- **UI**: Material Design 3

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- Flutter SDK (3.0.0 or higher)
- Dart SDK (3.0.0 or higher)
- A Firebase project with:
  - Realtime Database enabled
  - Authentication enabled (Anonymous sign-in method)
  - Appropriate security rules configured

## 🚀 Setup and Installation

### 1. Clone the Repository

```bash
git clone https://github.com/batumertoo/messagingapp.git
cd messagingapp
```

### 2. Install Dependencies

```bash
flutter pub get
```

### 3. Firebase Configuration

#### For Android:
- Place your `google-services.json` file in `android/app/`

#### For iOS:
- Place your `GoogleService-Info.plist` file in `ios/Runner/`

#### For Web/Other Platforms:
- Configure Firebase manually in your platform-specific files

### 4. Firebase Security Rules

Set up your Firebase Realtime Database rules to require authentication:

```json
{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}
```

### 5. Run the Application

```bash
# For development
flutter run

# For specific platform
flutter run -d android
flutter run -d ios
flutter run -d chrome
```

## 💻 Usage

1. **Launch the app** on your device or emulator
2. **Enter a username** on the welcome screen
3. **Click "Enter Chat"** to join the chat room
4. **Type your message** in the text field at the bottom
5. **Press send** or hit Enter to send your message
6. **View messages** in real-time from all connected users

## 🔐 Security Features

- **Anonymous Authentication**: Each device receives a unique anonymous user ID
- **Authenticated Access**: All database operations require valid authentication
- **Firebase Security Rules**: Backend rules enforce authentication requirements
- **Error Handling**: Graceful handling of authentication and network errors

## 📁 Project Structure

```
lib/
└── main.dart          # Main application file containing all components
android/
├── app/
│   └── google-services.json  # Firebase Android configuration
ios/
├── Runner/
│   └── GoogleService-Info.plist  # Firebase iOS configuration
test/
└── widget_test.dart   # Widget tests
pubspec.yaml           # Project dependencies
```

## 🧪 Testing

Run tests with:

```bash
flutter test
```

Run analysis:

```bash
flutter analyze
```

## 📚 Key Learning Objectives

This project demonstrates proficiency in:

1. **Real-time Database Operations**: Implementing Firebase Realtime Database with instant data synchronization
2. **Asynchronous Programming**: Effective use of Flutter's async/await and Stream listeners
3. **Authentication Flow**: Secure user authentication with Firebase Anonymous Auth
4. **State Management**: Managing application state with StatefulWidget
5. **UI/UX Design**: Creating responsive, user-friendly interfaces with Material Design
6. **Error Handling**: Implementing proper error handling for network and authentication operations

## 🔧 Technical Implementation Details

### Initialization Sequence

The app follows a strict initialization order to ensure security:

1. Flutter binding initialization
2. Firebase Core initialization
3. Anonymous authentication
4. UI launch

### Real-time Updates

Messages are listened to using Firebase's `onChildAdded` stream:
- New messages automatically appear at the top of the chat
- Messages are displayed in reverse chronological order
- UI updates happen reactively without manual refresh

### Message Formatting

- Timestamps are converted from milliseconds to HH:mm format
- Messages from the current user appear on the right with blue background
- Messages from other users appear on the left with grey background

## 🐛 Troubleshooting

### Common Issues

1. **"Permission Denied" error**
   - Ensure Firebase Security Rules are configured correctly
   - Verify Anonymous Authentication is enabled in Firebase Console

2. **"ClassNotFoundException" on Android**
   - Verify `google-services.json` is in the correct location
   - Check that package name matches between Firebase and `android/app/build.gradle`

3. **Build fails**
   - Run `flutter clean` and `flutter pub get`
   - Ensure all dependencies are compatible

## 📝 License

This project is available for educational purposes.

## 👤 Author

**batumertoo**

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!
