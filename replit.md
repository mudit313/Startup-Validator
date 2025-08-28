# Startup Validator - Full-Stack Web Application

## Overview

Startup Validator is a full-stack web application designed for students and entrepreneurs to share, discuss, and validate startup ideas within their academic communities. The platform enables users to post startup concepts, engage through comments and likes, participate in real-time chats, and compete on leaderboards based on community engagement.

The application features a modern React frontend with a Node.js/Express backend, PostgreSQL database with Drizzle ORM, and real-time communication capabilities through WebSockets. It's built with a focus on community interaction, organizational filtering (by college/university), and gamification through leaderboards.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript using Vite as the build tool
- **UI Library**: Shadcn/ui components built on Radix UI primitives with Tailwind CSS for styling
- **State Management**: TanStack Query (React Query) for server state management and caching
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod schema validation
- **Authentication**: Context-based auth provider with protected routes

### Backend Architecture
- **Framework**: Express.js with TypeScript running on Node.js
- **Authentication**: Passport.js with local strategy, session-based authentication using express-session
- **Password Security**: Built-in scrypt hashing with salt for secure password storage
- **Real-time Communication**: WebSocket server for live chat functionality
- **API Design**: RESTful endpoints with proper error handling and request logging middleware

### Data Storage Solutions
- **Database**: PostgreSQL configured through Drizzle ORM
- **ORM**: Drizzle with schema-first approach, migrations stored in `/migrations` directory
- **Session Storage**: Configurable session store (memory store for development, can be extended to PostgreSQL with connect-pg-simple)
- **Database Provider**: Neon Database for serverless PostgreSQL hosting

### Database Schema Design
- **Users Table**: Stores user credentials (username, email, hashed password), profile info (name, organization), and metadata
- **Ideas Table**: Contains startup idea posts with title, description, industry categorization, contact info, engagement metrics (likes/comments count), and chat permissions
- **Comments Table**: Threaded discussion system linked to ideas and users
- **Likes Table**: User engagement tracking for ideas with unique constraints
- **Chats/Chat Messages Tables**: Real-time messaging system associated with specific ideas

### Authentication and Authorization
- **Strategy**: Session-based authentication using Passport.js local strategy
- **Password Security**: Scrypt-based hashing with random salt generation
- **Session Management**: Express sessions with configurable store (memory/PostgreSQL)
- **Route Protection**: Protected route wrapper component that redirects unauthenticated users
- **User Context**: React context provider for global authentication state

### Real-time Features
- **WebSocket Implementation**: Custom WebSocket server integrated with Express for real-time chat
- **Chat System**: Per-idea chat rooms with message broadcasting and participant tracking
- **Live Updates**: Real-time message delivery with connection status tracking

### API Structure
- **Ideas Endpoints**: CRUD operations with filtering (organization, industry) and sorting (recent, popular)
- **Comments System**: Nested comments with user attribution and timestamps
- **Engagement APIs**: Like/unlike functionality with aggregate counting
- **Leaderboard APIs**: Dynamic ranking calculation for colleges and users
- **Chat APIs**: Chat room management and message handling
- **Authentication Routes**: Login, logout, registration, and user session management

### UI/UX Design Patterns
- **Component Architecture**: Modular component design with reusable UI primitives
- **Design System**: Consistent styling using CSS custom properties and Tailwind utility classes
- **Responsive Design**: Mobile-first approach with responsive grid layouts
- **Loading States**: Skeleton components and loading indicators for better UX
- **Error Handling**: Toast notifications for user feedback and error states

## External Dependencies

### Core Framework Dependencies
- **@neondatabase/serverless**: Serverless PostgreSQL driver for Neon Database
- **drizzle-orm**: Type-safe SQL query builder and ORM
- **drizzle-kit**: Database migration and schema management tools

### Authentication & Security
- **passport**: Authentication middleware for Node.js
- **passport-local**: Local username/password authentication strategy
- **express-session**: Session middleware for Express
- **connect-pg-simple**: PostgreSQL session store for production sessions

### UI Component Libraries
- **@radix-ui/***: Comprehensive set of low-level UI primitives (dialogs, dropdowns, forms, etc.)
- **@tanstack/react-query**: Server state management and data fetching
- **react-hook-form**: Form handling with validation
- **@hookform/resolvers**: Form validation resolvers for various schema libraries

### Styling and Utilities
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Type-safe variant API for component styling
- **clsx**: Utility for constructing className strings conditionally
- **date-fns**: Date utility library for formatting and manipulation

### Development Tools
- **vite**: Fast build tool and development server
- **typescript**: Static type checking
- **tsx**: TypeScript execution engine for Node.js
- **esbuild**: Fast JavaScript bundler for production builds

### Real-time Communication
- **ws**: WebSocket library for Node.js
- **WebSocket API**: Native browser WebSocket for client-side real-time communication

### Form Validation
- **zod**: TypeScript-first schema validation
- **drizzle-zod**: Integration between Drizzle ORM and Zod schemas

### Deployment Platform
- **Replit**: Cloud development and hosting platform with integrated database provisioning