# GoTinyUrls – URL Shortener with Live Analytics

GoTinyUrls is a full-featured URL shortener built with a **modern microservices architecture**. It provides fast and reliable URL shortening, real-time analytics, and scalable performance optimizations using **Redis, BullMQ, and MongoDB**.

---

## Features

### 🔗 URL Management

- **Custom Aliases**: Create personalized short URLs
- **Password-Protected Links**: Restrict access with user-defined passwords
- **Expiry Dates**: Time-limited short URLs for temporary sharing
- **QR Code Generation**: Automatic QR codes for every shortened link
- **Bulk Operations**: Queue-based batch URL processing for real time analytics

### 👤 User Authentication

- Secure **JWT-based authentication**
- Password hashing with **bcryptjs**
- Protected frontend routes with middleware
- User dashboard to manage URLs, analytics, and settings

### 📊 Advanced Analytics

- Real-time **click tracking**
- **Geographic analytics** powered by IPinfo
- **Time-based insights** (daily, weekly, monthly trends)
- Interactive charts with **Recharts**
- **3D globe visualization** for geographic traffic patterns

---

## Tech Stack

### Frontend

- **React** with **Vite**
- **Redux Toolkit** for state management
- **Tailwind CSS** + **Radix UI / shadcn UI** for responsive, accessible UI
- **Recharts** for interactive data visualization
- **Globe.gl** for geographic analytics

### Backend

- **Node.js** + **Express.js** server
- **MongoDB Atlas** with **Mongoose ODM**
- **Redis (Upstash)** for caching and unique ID generation
- **BullMQ** for background job processing
- **JWT** authentication and **bcryptjs** password hashing
- **QRCode** generation for shortened URLs
- **Deployment**: Backend deployed on **Render**

---

## System Architecture

- **Microservices separation**:
  - Backend Service (API, authentication, URL ops)
  - Analytics Service (click + geo tracking)
  - Shared Module (models + config)
- **Performance optimizations**:
  - Redis caching (reduced latency by ~50%)
  - Base62 counter-based URL generation (14M+ unique URLs without collisions)
  - BullMQ-powered queue for analytics and batch processing
  - API rate limiting to prevent abuse

---

## Project Structure

```
/frontend
  ├── components/        # Reusable UI components
  ├── pages/             # Route-based pages (Home, Dashboard, Auth)
  ├── store/             # Redux Toolkit slices
  ├── utils/             # Frontend helpers

/backend
  ├── controllers/       # Business logic (URLs, Auth, Redirects)
  ├── routes/            # Express routes & middleware
  ├── utils/             # Token, encoding, Redis helpers
  ├── middleware/        # Auth & validation middleware

/shared
  ├── models/            # MongoDB schemas (User, Url, Analytics)
  ├── config/            # DB + Redis configurations

```

---

## Development

### Prerequisites

- Node.js (>=18)
- MongoDB
- Redis (Upstash or local)

### Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/gotinyurls.git
   cd gotinyurls
   ```

2. Install dependencies:

   ```bash
   cd frontend && npm install
   cd ../backend && npm install
   ```

3. Setup environment variables:
   - Create `.env` files for frontend and backend services.
   - Add variables like `MONGO_URI`, `REDIS_URL`, `JWT_SECRET`, etc.
4. Run development servers:

   ```bash
   # In /frontend
   npm run dev

   # In /backend
   npm run dev

   ```

---

## Deployment

- **Frontend**: Deployed on Netlify
- **Backend**: Deployed on Render
- **Database**: MongoDB Atlas
- **Caching/Queues**: Upstash Redis

---

## Key Highlights

- **QR code support** for easy sharing
- **Password-protected short URLs** for private access
- Handles **high throughput** with Redis-backed counter system
- Reduced **redirect latency by ~50%** through caching + queues
- Real-time **day-wise and region-wise analytics**
- Built with **enterprise-level architecture** for scalability and reliability

---
