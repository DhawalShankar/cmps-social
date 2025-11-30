# Campus Got Social 🎓💼

A community-based social platform designed for colleges and companies to facilitate internal communication, lost & found management, peer-to-peer marketplace, and community discussions.

![Campus Got Social](https://img.shields.io/badge/React-18.x-blue) ![License](https://img.shields.io/badge/license-MIT-green)

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Getting Started](#getting-started)
- [How It Works](#how-it-works)
- [User Guide](#user-guide)
- [Technical Details](#technical-details)
- [Auto-Deletion Policy](#auto-deletion-policy)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)

## 🌟 Overview

**Campus Got Social** is a web application that creates isolated communities for colleges and companies. Each community operates independently with its own members, posts, and discussions. The platform helps community members connect, trade items, find lost belongings, and stay updated on campus/office activities.

### Why Campus Got Social?

- **Lost Something?** Post it in Lost & Found and get notified when someone finds it
- **Need to Sell?** List your used items in the Buy & Sell marketplace
- **Campus Events?** Stay updated with Hub Activities
- **Want to Connect?** Share thoughts and photos in Discussions

## ✨ Features

### 🏘️ Community Management

- **Automatic Community Creation**: First user creates the community by entering their college/company name
- **Easy Joining**: Subsequent users automatically join by entering the same community name
- **Member Tracking**: See how many people are in your community
- **Dual Mode**: Supports both student (college) and employee (company) communities

### 📱 Four Core Sections

#### 1. Lost & Found 🔍
- Post items as **Lost** or **Found**
- Add detailed descriptions and locations
- Comment system for claiming items
- Mark items as "Found/Returned" when resolved
- Auto-deletion after 2 months or when resolved

#### 2. Buy & Sell 🛒
- List used items with prices (₹)
- Detailed product descriptions
- Buyer-seller communication via comments
- Mark items as "Sold" when transaction complete
- Auto-deletion after 2 months or when sold

#### 3. Hub Activities 📅
- Post campus/office events
- Include event dates and locations
- RSVP and discuss via comments
- No auto-deletion (events remain for reference)

#### 4. Discussions 💬
- General community chat
- Share updates and thoughts
- Optional image sharing (via URL)
- Auto-deletion after 1 month

### 💬 Communication Features

- **Comment System**: Engage with any post through comments
- **Automatic Contact Sharing**: Email and phone number displayed in comments for easy contact
- **Real-time Updates**: All changes reflect immediately
- **User Attribution**: See who posted what and when

### 🔒 Privacy & Control

- **Community Isolation**: Each community's data is completely separate
- **Post Ownership**: Only post creators can delete or mark posts as resolved
- **Contact Information**: Shared only when users actively comment
- **Secure Login**: Email and password authentication

## 🚀 Getting Started

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection (for initial load)
- Valid email address

### Installation

This is a client-side React application. To run locally:

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/campus-got-social.git
   cd campus-got-social
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Run the application**
   ```bash
   npm start
   ```

4. **Open in browser**
   ```
   http://localhost:3000
   ```

### Quick Deploy

The app can be deployed to any static hosting service:
- **Netlify**: Drag and drop the build folder
- **Vercel**: Connect your GitHub repository
- **GitHub Pages**: Push to gh-pages branch

## 📖 How It Works

### Community Creation Flow

```
1. User signs up with college/company name
   ↓
2. System checks if community exists
   ↓
3a. If YES → User joins existing community
3b. If NO  → New community created, user becomes first member
   ↓
4. User accesses community dashboard
```

### Data Storage

- **LocalStorage**: All data stored in browser's localStorage
- **Community Structure**:
  ```javascript
  {
    "CommunityName": {
      name: "CommunityName",
      type: "college" | "company",
      members: [...],
      lostFound: [...],
      buySell: [...],
      activities: [...],
      discussions: [...]
    }
  }
  ```

### Auto-Deletion Mechanism

The app checks post dates on every load and automatically removes:
- Lost & Found posts older than 2 months (unless resolved)
- Buy & Sell posts older than 2 months (unless resolved)
- Discussion posts older than 1 month
- Resolved posts are deleted immediately after marking

## 👥 User Guide

### For New Users

1. **Sign Up**
   - Click "Sign Up" on the welcome screen
   - Choose "Student" or "Employee"
   - Enter your full name
   - Enter your college/company name (this creates/joins community)
   - Provide email and password
   - Add phone number (optional but recommended)

2. **First Login**
   - You'll see the community dashboard
   - Check the member count in the header
   - Explore all four tabs

### Creating Posts

1. Click the "**+ New Post**" button
2. Fill in the form based on the active tab:
   - **Lost & Found**: Choose Lost/Found, add title, description, location
   - **Buy & Sell**: Add title, description, price, location
   - **Hub Activities**: Add title, description, event date, location
   - **Discussions**: Add title, description, optional image URL
3. Click "**Post**" to publish

### Engaging with Posts

1. **Commenting**
   - Click "Add Comment" below any post
   - Write your message
   - Your contact info (email/phone) will be visible to others
   - Click "Post Comment"

2. **Marking as Resolved** (Lost & Found / Buy & Sell only)
   - Only post owner can mark as resolved
   - Click "Mark as Found/Returned" or "Mark as Sold"
   - Post will show "Resolved" badge and fade out
   - Post will be auto-deleted on next login

3. **Deleting Posts**
   - Only post owner can delete
   - Click trash icon in top-right of post
   - Confirm deletion

### Best Practices

✅ **DO**:
- Write clear, detailed descriptions
- Include location information
- Respond to comments promptly
- Mark items as resolved when complete
- Use discussions for general community chat

❌ **DON'T**:
- Share sensitive personal information publicly
- Post spam or irrelevant content
- Create duplicate posts
- Forget to mark items as resolved

## 🛠️ Technical Details

### Tech Stack

- **Frontend**: React 18.x
- **Styling**: Tailwind CSS
- **Icons**: Lucide React
- **Storage**: Browser LocalStorage
- **State Management**: React Hooks (useState, useEffect)

### Key Components

- **Authentication System**: Login/Signup with community management
- **Community Manager**: Handles community creation and member joining
- **Post Manager**: CRUD operations for all post types
- **Comment System**: Thread-based commenting with contact sharing
- **Auto-deletion Service**: Time-based post cleanup

### Data Persistence

All data is stored in browser's localStorage:
- **Key**: `campusCommunities` - Stores all community data
- **Key**: `campusUser` - Stores current user session

### Browser Compatibility

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

## ⏰ Auto-Deletion Policy

### Timeline

| Post Type | Auto-Delete After | Exception |
|-----------|-------------------|-----------|
| Lost & Found | 2 months | Marked as resolved |
| Buy & Sell | 2 months | Marked as sold |
| Discussions | 1 month | None |
| Hub Activities | Never | Manual deletion only |

### How It Works

1. Each post stores a `createdAt` timestamp
2. On app load, system calculates post age
3. Posts exceeding threshold are automatically removed
4. Resolved posts bypass the time check and delete immediately
5. Users see cleaned-up feed without manual intervention

## 🔮 Future Enhancements

### Planned Features

- [ ] **Image Upload**: Direct image upload instead of URL
- [ ] **Push Notifications**: Real-time alerts for comments
- [ ] **Search & Filter**: Find posts quickly
- [ ] **User Profiles**: View member profiles and post history
- [ ] **Admin Panel**: Community moderation tools
- [ ] **Chat Feature**: Direct messaging between users
- [ ] **Analytics**: Community engagement statistics
- [ ] **Mobile App**: Native iOS and Android apps
- [ ] **Email Integration**: Email notifications for important events
- [ ] **Verification System**: Verify college/company email addresses
- [ ] **Categories & Tags**: Better organization of posts
- [ ] **Ratings & Reviews**: Reputation system for Buy & Sell

### Technical Improvements

- [ ] Backend API integration
- [ ] Database storage (PostgreSQL/MongoDB)
- [ ] User authentication with JWT
- [ ] Real-time updates with WebSockets
- [ ] Image CDN for photo storage
- [ ] Progressive Web App (PWA) support
- [ ] Multi-language support
- [ ] Dark mode

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Reporting Bugs

1. Check if the bug is already reported
2. Create a new issue with:
   - Clear title and description
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots if applicable

### Suggesting Features

1. Open an issue with the "feature request" label
2. Describe the feature and its benefits
3. Explain use cases

### Pull Requests

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Code Style

- Use functional components and hooks
- Follow existing code formatting
- Add comments for complex logic
- Update documentation for new features

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Authors

- **Dhawal Shukla** - *Initial work* - [YourGitHub](https://github.com/dhawalshankar)

## 🙏 Acknowledgments

- Inspired by community needs in colleges and workplaces
- Built with ❤️ for better campus connectivity
- Special thanks to all contributors

<!-- ## 📞 Support

Need help? Reach out:

- **Email**: support@campusgotsocial.com
- **Twitter**: [@CampusGotSocial](https://twitter.com/campusgotsocial)
- **Issues**: [GitHub Issues](https://github.com/yourusername/campus-got-social/issues) -->

<!-- ## 🌐 Demo

Try the live demo: [Campus Got Social Demo](https://your-demo-url.com)

--- -->

**Made with ❤️ for communities everywhere**

*Last Updated: November 2025*