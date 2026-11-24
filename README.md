# AI-Powered Ticket Management System

A smart ticket management system that uses AI to automatically categorize, prioritize, and assign support tickets to the most appropriate moderators.

## Features

- **AI-Powered Ticket Processing**

  - Automatic ticket categorization
  - Smart priority assignment
  - Skill-based moderator matching
  - AI-generated helpful notes for moderators

- **Smart Moderator Assignment**

  - Automatic matching of tickets to moderators based on skills
  - Fallback to admin assignment if no matching moderator found
  - Skill-based routing system

- **User Management**

  - Role-based access control (User, Moderator, Admin)
  - Skill management for moderators
  - User authentication with JWT

- **Background Processing**
  - Event-driven architecture using Inngest
  - Automated email notifications
  - Asynchronous ticket processing

## Tech Stack

- **Backend**: Node.js with Express
- **Frontend**: React with Vite, Tailwind CSS, DaisyUI
- **Database**: MongoDB
- **Authentication**: JWT
- **Background Jobs**: Inngest
- **AI Integration**: Google Gemini API
- **Email**: Nodemailer with Mailtrap

## Prerequisites

- Node.js (v14 or higher)
- MongoDB
- Google Gemini API key
- Mailtrap account (for email testing)

## Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd AI-Ticket-System
   ```

2. **Install backend dependencies**

   ```bash
   cd ai-ticket-assistant
   npm install
   ```

3. **Install frontend dependencies**

   ```bash
   cd ai-ticket-frontend
   npm install
   ```

4. **Environment Setup**
   Create a `.env` file in `ai-ticket-assistant/` with the following variables:

   ```env
   MONGO_URI=your_mongodb_uri
   JWT_SECRET=your_jwt_secret
   MAILTRAP_SMTP_HOST=your_mailtrap_host
   MAILTRAP_SMTP_PORT=your_mailtrap_port
   MAILTRAP_SMTP_USER=your_mailtrap_user
   MAILTRAP_SMTP_PASS=your_mailtrap_password
   GEMINI_API_KEY=your_gemini_api_key
   APP_URL=http://localhost:3000
   ```

## Running the Application

1. **Start the backend server**

   ```bash
   cd ai-ticket-assistant
   npm run dev
   ```

2. **Start the Inngest dev server**

   ```bash
   npm run inngest-dev
   ```

3. **Start the frontend**
   ```bash
   cd ai-ticket-frontend
   npm run dev
   ```

## API Endpoints

### Authentication

- `POST /api/auth/signup` - Register a new user
- `POST /api/auth/login` - Login and get JWT token

### Tickets

- `POST /api/tickets` - Create a new ticket
- `GET /api/tickets` - Get all tickets for logged-in user
- `GET /api/tickets/:id` - Get ticket details

### Admin

- `GET /api/auth/users` - Get all users (Admin only)
- `POST /api/auth/update-user` - Update user role & skills (Admin only)

## Ticket Processing Flow

1. **Ticket Creation** - User submits a ticket with title and description
2. **AI Processing** - Inngest triggers background processing, AI analyzes content and generates skills, priority, notes, and type
3. **Moderator Assignment** - System matches moderators by skills, falls back to admin if no match
4. **Notification** - Email sent to assigned moderator with ticket details and AI notes
