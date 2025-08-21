# 🎓 E-Learning Platform

[![Next.js](https://img.shields.io/badge/Next.js-13.0-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18.0-green?style=for-the-badge&logo=node.js)](https://nodejs.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

> A modern, feature-rich e-learning platform built with Next.js, TypeScript, and Node.js

## 🌟 Features

### 🎯 Core Learning Features
- **Course Management**: Create, edit, and organize courses with rich content
- **User Authentication**: Secure login/register system with JWT
- **Dashboard**: Personalized learning dashboard for students and instructors
- **Progress Tracking**: Monitor learning progress and achievements
- **Video Streaming**: High-quality video content delivery
- **Quiz System**: Interactive assessments and quizzes
- **Discussion Forum**: Community-driven learning discussions

### 🚀 Advanced Features
- **Admin Panel**: Comprehensive platform management tools
- **Analytics Dashboard**: Detailed learning analytics and reports
- **Mobile Responsive**: Optimized for all devices
- **PWA Support**: Progressive Web App capabilities
- **Real-time Notifications**: Instant updates and alerts
- **Multi-language Support**: Internationalization ready
- **Certificate Generation**: Automated completion certificates
- **Gamification**: Achievement system and leaderboards

### 🔒 Security & Performance
- **JWT Authentication**: Secure token-based authentication
- **Role-based Access Control**: Different permissions for students, instructors, and admins
- **Data Validation**: Input sanitization and validation
- **Performance Optimization**: Caching and optimization strategies
- **Audit Logging**: Comprehensive security audit trails

## 🏗️ Architecture

```
elearning-platform/
├── elearning/                 # Main application directory
│   ├── app/                  # Next.js app directory (App Router)
│   │   ├── actions/         # Server actions
│   │   ├── admin/           # Admin panel pages
│   │   ├── courses/         # Course-related pages
│   │   ├── dashboard/       # User dashboard
│   │   ├── auth/            # Authentication pages
│   │   └── layout.tsx       # Root layout
│   ├── backend/             # Backend API server
│   │   ├── src/
│   │   │   ├── controllers/ # API controllers
│   │   │   ├── models/      # Database models
│   │   │   ├── routes/      # API routes
│   │   │   ├── middleware/  # Custom middleware
│   │   │   └── utils/       # Utility functions
│   │   └── package.json     # Backend dependencies
│   ├── components/          # Reusable UI components
│   │   ├── ui/             # Shadcn/ui components
│   │   ├── navbar.tsx      # Navigation component
│   │   └── footer.tsx      # Footer component
│   ├── hooks/              # Custom React hooks
│   ├── lib/                # Utility libraries
│   └── public/             # Static assets
└── README.md               # This file
```

## 🚀 Getting Started

### Prerequisites

- **Node.js** 18.0 or higher
- **npm** or **yarn** or **pnpm**
- **MongoDB** (for database)
- **Git**

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Tson28/elearning-platform.git
   cd elearning-platform
   ```

2. **Install frontend dependencies**
   ```bash
   cd elearning
   npm install
   # or
   yarn install
   # or
   pnpm install
   ```

3. **Install backend dependencies**
   ```bash
   cd backend
   npm install
   ```

4. **Environment Setup**
   ```bash
   # Frontend (.env.local)
   NEXT_PUBLIC_API_URL=http://localhost:5000/api
   NEXT_PUBLIC_APP_URL=http://localhost:3000
   
   # Backend (.env)
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/elearning
   JWT_SECRET=your_jwt_secret_here
   MAIL_HOST=smtp.gmail.com
   MAIL_PORT=587
   MAIL_USER=your_email@gmail.com
   MAIL_PASS=your_app_password
   ```

5. **Start the development servers**
   ```bash
   # Terminal 1 - Frontend
   cd elearning
   npm run dev
   
   # Terminal 2 - Backend
   cd elearning/backend
   npm run dev
   ```

6. **Open your browser**
   - Frontend: [http://localhost:3000](http://localhost:3000)
   - Backend API: [http://localhost:5000](http://localhost:5000)

## 🛠️ Tech Stack

### Frontend
- **Next.js 13+** - React framework with App Router
- **TypeScript** - Type-safe JavaScript
- **Tailwind CSS** - Utility-first CSS framework
- **Shadcn/ui** - Beautiful UI components
- **React Hook Form** - Form handling
- **Zod** - Schema validation

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **JWT** - Authentication
- **Multer** - File uploads
- **Nodemailer** - Email services

### Development Tools
- **ESLint** - Code linting
- **Prettier** - Code formatting
- **TypeScript** - Type checking
- **Git** - Version control

## 📱 Available Scripts

### Frontend (elearning/)
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint
npm run type-check   # Run TypeScript check
```

### Backend (elearning/backend/)
```bash
npm run dev          # Start development server
npm run start        # Start production server
npm run build        # Build TypeScript
npm run lint         # Run ESLint
```

## 🌐 API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `POST /api/auth/forgot-password` - Forgot password
- `POST /api/auth/reset-password` - Reset password
- `POST /api/auth/verify-email` - Email verification

### Courses
- `GET /api/courses` - Get all courses
- `GET /api/courses/:id` - Get course by ID
- `POST /api/courses` - Create new course
- `PUT /api/courses/:id` - Update course
- `DELETE /api/courses/:id` - Delete course

### Users
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update user profile
- `GET /api/users` - Get all users (admin only)
- `DELETE /api/users/:id` - Delete user (admin only)

## 🗄️ Database Schema

### User Model
```typescript
interface User {
  _id: ObjectId;
  email: string;
  password: string;
  firstName: string;
  lastName: string;
  role: 'student' | 'instructor' | 'admin';
  isVerified: boolean;
  profilePicture?: string;
  createdAt: Date;
  updatedAt: Date;
}
```

### Course Model
```typescript
interface Course {
  _id: ObjectId;
  title: string;
  description: string;
  instructor: ObjectId;
  category: string;
  price: number;
  thumbnail: string;
  lessons: Lesson[];
  enrolledStudents: ObjectId[];
  createdAt: Date;
  updatedAt: Date;
}
```

## 🔐 Authentication & Authorization

The platform uses JWT (JSON Web Tokens) for authentication with role-based access control:

- **Students**: Can enroll in courses, track progress, participate in discussions
- **Instructors**: Can create and manage courses, view student progress
- **Admins**: Full platform access including user management and analytics

## 🎨 UI Components

Built with **Shadcn/ui** components for a consistent and beautiful design:

- **Navigation**: Responsive navbar with mobile menu
- **Cards**: Course cards, user cards, and content cards
- **Forms**: Login, registration, and course creation forms
- **Tables**: Data tables for admin panels
- **Modals**: Confirmation dialogs and forms
- **Charts**: Analytics and progress visualization

## 📱 Responsive Design

The platform is fully responsive and optimized for:
- **Desktop** (1200px+)
- **Tablet** (768px - 1199px)
- **Mobile** (320px - 767px)

## 🚀 Deployment

### Frontend (Vercel)
```bash
npm run build
vercel --prod
```

### Backend (Railway/Render)
```bash
npm run build
# Deploy to your preferred platform
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Team

- **Developer**: [Tson28](https://github.com/Tson28)
- **Project**: E-Learning Platform

## 📞 Support

If you have any questions or need help:
- Create an issue on GitHub
- Contact the development team
- Check the documentation

---

**Made with ❤️ for better education**

---

# 🎓 Nền Tảng Học Trực Tuyến

> Một nền tảng học trực tuyến hiện đại, đầy đủ tính năng được xây dựng với Next.js, TypeScript và Node.js

## 🌟 Tính Năng

### 🎯 Tính Năng Học Tập Cốt Lõi
- **Quản Lý Khóa Học**: Tạo, chỉnh sửa và tổ chức khóa học với nội dung phong phú
- **Xác Thực Người Dùng**: Hệ thống đăng nhập/đăng ký an toàn với JWT
- **Bảng Điều Khiển**: Bảng điều khiển học tập cá nhân hóa cho học viên và giảng viên
- **Theo Dõi Tiến Độ**: Giám sát tiến độ học tập và thành tích
- **Phát Video**: Cung cấp nội dung video chất lượng cao
- **Hệ Thống Quiz**: Đánh giá và quiz tương tác
- **Diễn Đàn Thảo Luận**: Thảo luận học tập do cộng đồng thúc đẩy

### 🚀 Tính Năng Nâng Cao
- **Bảng Điều Khiển Admin**: Công cụ quản lý nền tảng toàn diện
- **Bảng Điều Khiển Phân Tích**: Phân tích học tập chi tiết và báo cáo
- **Thiết Kế Responsive**: Tối ưu hóa cho mọi thiết bị
- **Hỗ Trợ PWA**: Khả năng ứng dụng web tiến bộ
- **Thông Báo Thời Gian Thực**: Cập nhật và cảnh báo tức thì
- **Hỗ Trợ Đa Ngôn Ngữ**: Sẵn sàng quốc tế hóa
- **Tạo Chứng Chỉ**: Chứng chỉ hoàn thành tự động
- **Gamification**: Hệ thống thành tích và bảng xếp hạng

## 🚀 Bắt Đầu

### Yêu Cầu Hệ Thống
- **Node.js** 18.0 trở lên
- **npm** hoặc **yarn** hoặc **pnpm**
- **MongoDB** (cho cơ sở dữ liệu)
- **Git**

### Cài Đặt

1. **Clone repository**
   ```bash
   git clone https://github.com/Tson28/elearning-platform.git
   cd elearning-platform
   ```

2. **Cài đặt dependencies frontend**
   ```bash
   cd elearning
   npm install
   ```

3. **Cài đặt dependencies backend**
   ```bash
   cd backend
   npm install
   ```

4. **Khởi chạy máy chủ phát triển**
   ```bash
   # Terminal 1 - Frontend
   cd elearning
   npm run dev
   
   # Terminal 2 - Backend
   cd elearning/backend
   npm run dev
   ```

5. **Mở trình duyệt**
   - Frontend: [http://localhost:3000](http://localhost:3000)
   - Backend API: [http://localhost:5000](http://localhost:5000)

## 🛠️ Công Nghệ Sử Dụng

### Frontend
- **Next.js 13+** - Framework React với App Router
- **TypeScript** - JavaScript an toàn kiểu dữ liệu
- **Tailwind CSS** - Framework CSS utility-first
- **Shadcn/ui** - Component UI đẹp mắt

### Backend
- **Node.js** - Runtime JavaScript
- **Express.js** - Framework web
- **MongoDB** - Cơ sở dữ liệu NoSQL
- **Mongoose** - ODM MongoDB
- **JWT** - Xác thực

## 📱 Scripts Có Sẵn

### Frontend (elearning/)
```bash
npm run dev          # Khởi chạy máy chủ phát triển
npm run build        # Build cho production
npm run start        # Khởi chạy máy chủ production
```

### Backend (elearning/backend/)
```bash
npm run dev          # Khởi chạy máy chủ phát triển
npm run start        # Khởi chạy máy chủ production
```

## 🤝 Đóng Góp

1. Fork repository
2. Tạo feature branch (`git checkout -b feature/tinh-nang-moi`)
3. Commit thay đổi (`git commit -m 'Thêm tính năng mới'`)
4. Push lên branch (`git push origin feature/tinh-nang-moi`)
5. Mở Pull Request

## 📄 Giấy Phép

Dự án này được cấp phép theo MIT License.

## 👥 Nhóm Phát Triển

- **Developer**: [Tson28](https://github.com/Tson28)
- **Dự án**: Nền Tảng Học Trực Tuyến

---

**Được tạo với ❤️ cho giáo dục tốt hơn**
