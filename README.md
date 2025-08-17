# 🍲 FlavorWorld - Recipe Social Network

> **A modern social network for sharing recipes, connecting food lovers, and building culinary communities**

FlavorWorld is a full-stack mobile application that combines the love of cooking with social networking. Built with React Native and powered by a robust Node.js backend with real-time capabilities.

---

## ✨ Features

### 👤 **User Management**
- 🔐 Complete authentication system (register, login, password recovery)
- 📝 Customizable user profiles with avatars and bios
- 🔄 Follow/unfollow system to connect with other food enthusiasts
- 🔒 Secure password management with validation

### 🍽️ **Recipe Sharing**
- 📸 Create and share recipes with high-quality images
- 🏷️ Categorize recipes by cuisine type, meat preferences, and cooking time
- ⭐ Like and comment system for community engagement
- ✏️ Edit and delete your own recipes
- 🔍 Advanced search functionality

### 👥 **Groups & Communities**
- 🏠 Create public and private cooking groups
- 👑 Admin controls for group management
- 📋 Approval system for private groups
- 📝 Group-specific recipe sharing
- ⚙️ Customizable group settings and permissions

### 💬 **Real-time Communication**
- ⚡ Private messaging between users
- 👥 Group chat functionality
- 🔴 Live typing indicators
- 📱 Unread message counters
- 🎯 Real-time notifications

### 📊 **Analytics & Insights**
- 📈 User engagement statistics
- 📊 Recipe popularity metrics
- 👥 Follower growth tracking
- 📋 Group activity analytics
- 🎯 Personalized content recommendations

### 🔔 **Smart Notifications**
- 💝 Real-time push notifications
- 👍 Like and comment alerts
- 👥 Follow notifications
- 📱 Group activity updates
- ⚙️ Customizable notification preferences

---

## 🏗️ Architecture

### **Frontend (React Native)**
```
📱 Mobile App
├── 🖥️ Authentication Screens
├── 🏠 Home & Feed
├── 👥 Groups Management
├── 💬 Chat System
├── 👤 Profile Management
├── 🔍 Search & Discovery
└── 📊 Analytics Dashboard
```

### **Backend (Microservices)**
```
🔧 API Gateway (Port 3000)
├── 🔐 Auth Service
├── 👤 User Service
├── 🍲 Recipe Service
├── 👥 Group Service
├── 💬 Chat Services
├── 🔔 Notification Service
└── ⚡ Socket.IO Server
```

### **Database (MongoDB)**
```
🗄️ MongoDB Collections
├── 👥 users
├── 🍲 recipes
├── 👥 groups
├── 📝 groupPosts
├── 💬 messages
├── 👥 privateChats
├── 👥 groupChats
├── 💬 groupChatMessages
├── 🔔 notifications
└── 🔑 passwordResets
```

---

## 🚀 Quick Start

### **Prerequisites**
- Node.js (v16 or higher)
- npm or yarn
- MongoDB (local or Atlas)
- Expo CLI
- Android Studio / Xcode (for device testing)

### **Installation**

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/flavorworld.git
   cd flavorworld
   ```

2. **Setup Backend Server**
   ```bash
   # Navigate to server directory
   cd server
   
   # Install server dependencies
   npm install socket.io express mongoose cors multer dotenv nodemailer
   ```

3. **Setup Client**
   ```bash
   # Navigate back to main project directory
   cd ..
   
   # Install client dependencies
   npm install socket.io-client expo-modules-core expo-document-picker nodemailer
   ```

4. **Environment Setup**
   Create a `.env` file in the `server` directory:
   ```env
   PORT=3000
   MONGODB_URI=mongodb://localhost:27017/flavorworld
   EMAIL_USER=your-email
   EMAIL_PASS=your-password
   JWT_SECRET=your-super-secret-jwt-key
   ```

5. **Start MongoDB**
   ```bash
   # Local MongoDB
   mongod
   
   # Or use MongoDB Atlas (update MONGODB_URI in .env)
   ```

6. **Run the Backend Server**
   ```bash
   # From server directory
   cd server
   node index.js
   ```

7. **Run the React Native App**
   ```bash
   # Open new terminal, navigate to main directory
   npx expo start -c
   ```

8. **Open the app**
   - 📱 Scan QR code with Expo Go app
   - 🤖 Press 'a' for Android emulator
   - 🍎 Press 'i' for iOS simulator

---

## 📚 API Documentation

### **Authentication Endpoints**
```http
POST /api/auth/register          # User registration
POST /api/auth/login             # User login
POST /api/auth/check-email       # Email existence check
POST /api/auth/send-reset-code   # Password reset
POST /api/auth/verify-reset-code # Verify reset code
POST /api/auth/reset-password    # Reset password
```

### **Recipe Endpoints**
```http
GET    /api/recipes              # Get all recipes
POST   /api/recipes              # Create recipe
GET    /api/recipes/:id          # Get recipe by ID
PUT    /api/recipes/:id          # Update recipe
DELETE /api/recipes/:id          # Delete recipe
POST   /api/recipes/:id/like     # Like recipe
DELETE /api/recipes/:id/like     # Unlike recipe
POST   /api/recipes/:id/comments # Add comment
```

### **Group Endpoints**
```http
GET    /api/groups               # Get all groups
POST   /api/groups               # Create group
GET    /api/groups/:id           # Get group details
PUT    /api/groups/:id           # Update group
DELETE /api/groups/:id           # Delete group
POST   /api/groups/:id/join      # Join group
DELETE /api/groups/:id/leave/:userId # Leave group
```

### **Chat Endpoints**
```http
GET    /api/chats/my             # Get user's chats
POST   /api/chats/private        # Create private chat
GET    /api/chats/:id/messages   # Get chat messages
POST   /api/chats/:id/messages   # Send message
PUT    /api/chats/:id/read       # Mark as read
```

---

## 🔌 Socket.IO Events

### **Private Chat Events**
```javascript
// Client to Server
socket.emit('join_chat', chatId)
socket.emit('send_message', messageData)
socket.emit('mark_as_read', { chatId, userId })
socket.emit('start_typing', { chatId, userId })
socket.emit('stop_typing', { chatId, userId })

// Server to Client
socket.on('message_received', messageData)
socket.on('messages_marked_read', { chatId, userId })
socket.on('typing_started', { chatId, userId })
socket.on('typing_stopped', { chatId, userId })
```

### **Group Chat Events**
```javascript
// Client to Server
socket.emit('join_group_chat', chatId)
socket.emit('send_group_message', messageData)
socket.emit('mark_group_as_read', { chatId, userId })

// Server to Client
socket.on('group_message_received', messageData)
socket.on('group_messages_marked_read', { chatId, userId })
```

---

## 🛠️ Development

### **Project Structure**
```
flavorworld/
├── 📱 App.js                    # Main app component
├── 📂 components/               # Reusable components
│   ├── common/                  # Common UI components
│   ├── screens/                 # Screen components
│   └── navigation/              # Navigation setup
├── 🔧 server/                   # Backend code
│   ├── models/                  # MongoDB models
│   ├── routes/                  # API routes
│   ├── services/                # Business logic
│   └── index.js                 # Server entry point
├── 📄 package.json              # Dependencies
├── 🔧 .env                      # Environment variables
└── 📖 README.md                 # This file
```

### **Available Scripts**
```bash
npm start          # Start Expo development server
npm run android    # Run on Android emulator
npm run ios        # Run on iOS simulator
npm run web        # Run in web browser
```

### **Environment Variables**
| Variable | Description | Required |
|----------|-------------|----------|
| `PORT` | Server port | ✅ |
| `MONGODB_URI` | MongoDB connection string | ✅ |
| `EMAIL_USER` | Email for notifications | ✅ |
| `EMAIL_PASS` | Email app password | ✅ |
| `JWT_SECRET` | JWT signing secret | ✅ |

---

## 🧪 Testing

### **Manual Testing**
1. **User Authentication**
   - Register new account
   - Login with credentials
   - Password reset flow

2. **Recipe Management**
   - Create recipe with image
   - Edit existing recipe
   - Delete recipe
   - Like/unlike recipes

3. **Group Features**
   - Create public/private groups
   - Join/leave groups
   - Post recipes in groups
   - Manage group members

4. **Chat Functionality**
   - Send private messages
   - Create group chats
   - Real-time message delivery
   - Read receipts

### **Performance Testing**
- Image upload handling (max 5MB)
- Real-time message delivery
- Database query optimization
- Socket.IO connection stability

---

## 📦 Dependencies

### **Frontend**
- **React Native 0.79.2** - Mobile app framework
- **Expo ~53.0.9** - Development platform
- **React Navigation** - Navigation library
- **Socket.IO Client** - Real-time communication
- **D3.js** - Data visualization
- **Axios** - HTTP client

### **Backend**
- **Express 5.1.0** - Web framework
- **Socket.IO 4.8.1** - Real-time engine
- **Mongoose 8.15.1** - MongoDB ODM
- **Multer** - File upload handling
- **bcryptjs** - Password hashing
- **nodemailer** - Email service
- **jsonwebtoken** - JWT authentication

---

## 🚀 Deployment

### **Backend Deployment**
1. **Environment Setup**
   ```bash
   # Production environment variables
   NODE_ENV=production
   MONGODB_URI=mongodb+srv://your-atlas-connection
   PORT=3000
   ```

2. **Deploy to Heroku/Railway/Vercel**
   ```bash
   # Example for Heroku
   git push heroku main
   ```

### **Frontend Deployment**
1. **Build for Production**
   ```bash
   expo build:android
   expo build:ios
   ```

2. **Submit to App Stores**
   ```bash
   expo submit:android
   expo submit:ios
   ```

---

## 🤝 Contributing

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/amazing-feature`)
3. **Commit changes** (`git commit -m 'Add amazing feature'`)
4. **Push to branch** (`git push origin feature/amazing-feature`)
5. **Open a Pull Request**

### **Development Guidelines**
- Follow React Native best practices
- Write clean, documented code
- Test all features before submitting
- Follow the existing code style
- Update documentation as needed

---

## 🐛 Troubleshooting

### **Common Issues**

**MongoDB Connection Failed**
```bash
# Check MongoDB status
brew services list | grep mongodb
# Start MongoDB
brew services start mongodb/brew/mongodb-community
```

**Expo Start Issues**
```bash
# Clear cache
expo start --clear
# Reset Metro bundler
npx react-native start --reset-cache
```

**Socket.IO Connection Issues**
```javascript
// Check server URL in Socket.IO client
const socket = io('http://your-server-url:3000');
```

**Image Upload Errors**
- Check file size (max 5MB)
- Verify MIME type support
- Ensure proper base64 encoding

---

## 🙏 Acknowledgments

- **React Native Community** for the amazing framework
- **MongoDB** for the flexible database solution
- **Socket.IO** for real-time capabilities
- **Expo** for simplifying mobile development

---

## 📞 Contact

**Developer:** Lir Chen  
**Email:** lirhen2000@gmail.com  
**LinkedIn:** [https://www.linkedin.com/in/lir-chen/](https://www.linkedin.com/in/lir-chen/)  
**GitHub:** [https://github.com/LirChen](https://github.com/LirChen)

---

<div align="center">

**⭐ Star this repository if you found it helpful!**

Made with ❤️ and lots of ☕

</div>
