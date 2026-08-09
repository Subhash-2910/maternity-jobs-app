# Maternity Jobs App

A Flutter mobile application designed to connect job seekers with maternity-friendly employment opportunities. Built with Flutter 3.x, Dart, and Supabase backend.

## 🚀 Features

### Authentication
- **Email/Password Sign Up & Login**
- **User Role Management** (Job Seeker / Employer)
- **Session Persistence**
- **Forgot Password** functionality
- **Secure Authentication** with Supabase

### Job Seeker Features
- **Browse Job Listings** with maternity-friendly filter
- **Apply for Jobs** with resume upload
- **Save Jobs** for later viewing
- **Profile Management** with skills and experience
- **Application Tracking**

### Employer Features
- **Post Job Listings** with maternity-friendly options
- **View Applications** for posted jobs
- **Company Profile Management**
- **Job Management** (edit, delete)

### Technical Features
- **Responsive Design** for mobile and web
- **Real-time Updates** with Supabase
- **File Upload** for resumes
- **Push Notifications** (planned)
- **Clean Architecture** with Provider state management

## 🛠 Tech Stack

- **Frontend**: Flutter 3.x, Dart
- **Backend**: Supabase (PostgreSQL, Auth, Storage)
- **State Management**: Provider
- **Routing**: Go Router
- **UI**: Material Design 3
- **File Handling**: File Picker, Image Picker

## 📱 Screenshots

*Screenshots will be added here*

## 🚀 Getting Started

### Prerequisites

- Flutter SDK (3.x or higher)
- Dart SDK
- Android Studio / VS Code
- Supabase Account

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/maternity-jobs-app.git
   cd maternity-jobs-app
   ```

2. **Install dependencies**
   ```bash
   flutter pub get
   ```

3. **Configure Supabase**
   - Create a new Supabase project
   - Update `lib/utils/supabase_config.dart` with your credentials:
   ```dart
   static const String supabaseUrl = 'YOUR_SUPABASE_URL';
   static const String supabaseAnonKey = 'YOUR_SUPABASE_ANON_KEY';
   ```

4. **Set up Database Schema**
   - Run the SQL commands in `MANUAL_FIX.sql` in your Supabase SQL Editor
   - This creates the necessary tables and functions

5. **Run the app**
   ```bash
   flutter run
   ```

## 🗄 Database Schema

### Users Table
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email TEXT UNIQUE NOT NULL,
  name TEXT NOT NULL,
  role TEXT NOT NULL CHECK (role IN ('job_seeker', 'employer')),
  skills TEXT[],
  experience TEXT,
  maternity_status BOOLEAN DEFAULT FALSE,
  resume_url TEXT,
  company_name TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);
```

### Jobs Table
```sql
CREATE TABLE jobs (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  title TEXT NOT NULL,
  company TEXT NOT NULL,
  type TEXT NOT NULL,
  description TEXT NOT NULL,
  maternity_friendly BOOLEAN DEFAULT FALSE,
  employer_id UUID REFERENCES users(id),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);
```

### Applications Table
```sql
CREATE TABLE applications (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  job_id UUID REFERENCES jobs(id),
  applicant_id UUID REFERENCES users(id),
  name TEXT NOT NULL,
  email TEXT NOT NULL,
  message TEXT,
  resume_url TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);
```

## 📁 Project Structure

```
lib/
├── main.dart                 # App entry point
├── models/                   # Data models
│   ├── user_model.dart
│   ├── job_model.dart
│   └── application_model.dart
├── providers/               # State management
│   ├── auth_provider.dart
│   ├── job_provider.dart
│   └── application_provider.dart
├── screens/                 # UI screens
│   ├── auth/
│   ├── home/
│   ├── jobs/
│   ├── profile/
│   └── applications/
├── services/               # API services
│   ├── auth_service.dart
│   ├── job_service.dart
│   └── application_service.dart
├── utils/                  # Utilities
│   ├── theme.dart
│   ├── constants.dart
│   ├── router.dart
│   └── supabase_config.dart
└── widgets/                # Reusable widgets
    ├── custom_button.dart
    └── custom_text_field.dart
```

## 🔧 Configuration

### Environment Variables
Create a `.env` file in the root directory:
```env
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_supabase_anon_key
```

### Supabase Setup
1. Enable Row Level Security (RLS)
2. Create storage buckets for resumes
3. Set up authentication providers
4. Configure CORS settings

## 🧪 Testing

```bash
# Run unit tests
flutter test

# Run integration tests
flutter test integration_test/
```

## 📦 Building

### Android
```bash
flutter build apk --release
```

### iOS
```bash
flutter build ios --release
```

### Web
```bash
flutter build web --release
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Flutter team for the amazing framework
- Supabase for the backend services
- Material Design for the UI guidelines

## 📞 Support

If you have any questions or need help, please open an issue on GitHub.

---

**Made with ❤️ for working parents**



### Built as part of Women's Day Hackathon on 8th March 2025 : (PS:Ended up tied at 3rd place) 

## 👥 Team Members

- **Subhash Kashyap K H** - [github](https://github.com/Subhash-2910) 
- **Chiranthan T R** - [github](https://github.com/moduloous) 
- **Nikhil R** - [github](https://github.com/Nikhil-r-projects)
