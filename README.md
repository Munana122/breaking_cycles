# Breaking Cycles

## 🌟 Mission
Breaking the cycle of poverty among women through education and empowerment.

## 🎯 Overview
Breaking Cycles is a web platform designed to empower young women, single mothers, and girls with disabilities through:
- **Free Education**: Curated courses in Financial Literacy, Coding, Entrepreneurship, and Beauty & Wellness
- **Community Support**: Safe spaces for peer support and mentorship
- **Success Stories**: Inspiring narratives from women who have overcome challenges
- **Resource Center**: Links to scholarships, NGOs, and support organizations

## ✨ Features

### For Learners
- 🎓 Access 12+ free courses across 4 categories
- 💬 Join community chat rooms (Young Mothers, Empowered Abilities, Sisters Supporting Sisters)
- 🏆 Earn badges for course completion
- ✍️ Share your success story
- 📧 Contact support team

### For Admins
- 📝 Review and approve user-submitted stories
- 🛡️ Moderate community forums
- 📊 View platform statistics

### Technical Features
- 🔐 Firebase Authentication (Email/Password)
- 💾 Cloud Firestore database for real-time data
- 🔄 Real-time chat with message persistence
- 📱 Fully responsive (mobile, tablet, desktop)
- ⚡ Single-page application with smooth transitions

## 🛠️ Tech Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Backend**: Firebase (Authentication + Firestore)
- **Hosting**: Firebase Hosting / Netlify / Vercel
- **Architecture**: Single-page application (SPA)

## 🚀 Quick Start

### Prerequisites
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Firebase account (free tier)
- Text editor (VS Code recommended)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/breaking-cycles.git
cd breaking-cycles
```

2. **Set up Firebase**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Create a new project: "breaking-cycles"
   - Enable Authentication (Email/Password)
   - Create Firestore Database (test mode)
   - Get your config from Project Settings

3. **Add Firebase Config**
   - Open `index.html`
   - Find line ~12 (Firebase config section)
   - Replace with your Firebase config:
```javascript
   const firebaseConfig = {
       apiKey: "YOUR_API_KEY",
       authDomain: "YOUR_PROJECT.firebaseapp.com",
       projectId: "YOUR_PROJECT_ID",
       storageBucket: "YOUR_PROJECT.appspot.com",
       messagingSenderId: "YOUR_SENDER_ID",
       appId: "YOUR_APP_ID"
   };
```

4. **Run locally**
   - Simply open `index.html` in your browser, or
   - Use a local server:
```bash
   # Python 3
   python -m http.server 8000
   
   # Node.js (install http-server globally first)
   npx http-server
```
   - Navigate to `http://localhost:8000`

5. **Deploy**

   **Option A: Firebase Hosting**
```bash
   npm install -g firebase-tools
   firebase login
   firebase init hosting
   firebase deploy
```

   **Option B: Netlify**
   - Drag and drop `index.html` to [netlify.com/drop](https://app.netlify.com/drop)

   **Option C: GitHub Pages**
   - Push to GitHub
   - Enable Pages in repo settings
   - Select main branch

## 👤 Admin Access

Admin features are automatically enabled for the founder email:
- Email: `m.munana@alustudent.com`
- Admin panel accessible from user dropdown menu

## 📊 Firebase Database Structure
```
firestore/
├── users/
│   └── {userId}/
│       ├── name: string
│       ├── email: string
│       ├── badges: array
│       ├── completedCourses: array
│       └── createdAt: timestamp
│
├── chatRooms/
│   ├── Young Mothers Circle/
│   │   └── messages/
│   │       └── {messageId}/
│   │           ├── text: string
│   │           ├── author: string
│   │           ├── userId: string
│   │           └── timestamp: timestamp
│   │
│   ├── Empowered Abilities/messages/...
│   └── Sisters Supporting Sisters/messages/...
│
├── stories/
│   └── {storyId}/
│       ├── name: string
│       ├── title: string
│       ├── text: string
│       ├── category: string
│       ├── status: string (pending/approved/rejected)
│       ├── userId: string
│       └── createdAt: timestamp
│
└── contactSubmissions/
    └── {submissionId}/
        ├── name: string
        ├── email: string
        ├── subject: string
        ├── message: string
        ├── userId: string
        └── createdAt: timestamp
```

## 🎓 Usage Guide

### For Users
1. **Sign Up**: Click "Sign Up" → Enter details → Create account
2. **Browse Courses**: Go to "Learn" → Explore categories
3. **Complete Courses**: Click "✓ Complete" to earn badges
4. **Join Chat**: Go to "Community" → Select a group → Join Chat
5. **Share Story**: Go to "Stories" → "Share Your Story"
6. **Contact**: Go to "Contact" → Fill form → Send message

### For Admins
1. Login with admin email
2. Access "Admin Panel" from user dropdown
3. Review pending stories and moderate content

## 🧪 Testing

### Test Credentials (Create these in Firebase)
- **Regular User**: test@example.com / test123
- **Admin**: m.munana@alustudent.com / [your-password]

### Test Scenarios
✅ User registration and login
✅ Course completion and badge earning
✅ Chat room messaging
✅ Story submission
✅ Contact form submission
✅ Admin story approval
✅ Mobile responsiveness

## 📱 Browser Support

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

## 🔒 Security

- HTTPS enforced (via Firebase/Netlify)
- Password minimum 6 characters
- Firebase security rules (set to test mode for MVP)
- XSS protection via HTML escaping
- CORS configured for production domains

## 📈 Future Enhancements

- [ ] Email notifications (SendGrid integration)
- [ ] Video course content hosting
- [ ] Payment gateway for premium courses
- [ ] Mobile native apps (React Native)
- [ ] Advanced analytics dashboard
- [ ] Multilingual support (Kinyarwanda, French)
- [ ] AI-powered course recommendations
- [ ] Mentorship matching system

## 👥 Team

**Founder & Developer**
- Munana Merveille
- Email: m.munana@alustudent.com
- Phone: +250791839793
- Location: Kigali, Rwanda
- Institution: African Leadership University (ALU)

## 📄 License

This project is part of an academic submission for ALU's Software Engineering course.

## 🙏 Acknowledgments

- African Leadership University
- Firebase team for excellent documentation
- All the inspiring women whose stories motivate this project

## 📞 Support

For questions or support:
- Email: m.munana@alustudent.com
- Phone: +250791839793

## 🚀 Deployment Status

- **Development**: ✅ Complete
- **Testing**: ⏳ In Progress
- **Production**: 🔄 Ready to Deploy

---

**Built with 💜 to empower women and break cycles of poverty**
