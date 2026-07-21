# Eventify – Event Management and Ticketing Platform

Eventify is a full-stack event management and ticketing platform that allows users to discover events, purchase tickets, receive QR-code-based tickets, and manage their event activity through role-based dashboards.

The platform also provides organizers and administrators with tools for event creation, ticket management, attendee tracking, payments, analytics, notifications, waitlists, and customer support.

---

## Project Overview

Eventify was developed as a capstone project to demonstrate the design and implementation of a complete full-stack application.

The application supports multiple user roles:

- Attendees
- Event organizers
- Administrators

Each role receives a customized dashboard and access to role-specific features.

---

## Key Features

### User Features

- User registration and login
- JWT-based authentication
- Password reset functionality
- User onboarding
- Event discovery and event details
- Favorite events
- Ticket purchasing
- QR-code-based ticket generation
- Ticket upgrades
- Refund requests
- Organizer profiles
- Event sharing
- Notifications
- Support ticket submission

### Organizer Features

- Organizer application workflow
- Event creation and management
- Ticket-tier configuration
- Seating arrangement management
- Attendee management
- Waitlist management
- Event analytics
- Communication with attendees
- Event image management
- Sales and ticket performance tracking

### Administrator Features

- Administrative dashboard
- User and event management
- Organizer application review
- Event moderation
- Communication testing
- Support ticket management
- Platform monitoring and analytics

---

## Technology Stack

### Frontend

- Next.js
- React
- TypeScript
- Tailwind CSS
- Framer Motion
- React Context API
- Stripe.js

### Backend

- Node.js
- Express.js
- JavaScript
- REST APIs
- JWT authentication
- bcrypt
- Socket.IO

### Database

- PostgreSQL
- Prisma ORM
- Prisma migrations

### Integrations

- Stripe for payment processing
- AWS S3 for file and image storage
- Email notifications
- SMS notifications
- Push notifications
- QR-code ticket generation
- PDF ticket generation

### DevOps and Documentation

- Git
- GitHub
- Jenkins
- OpenAPI / Swagger
- ESLint

---

## System Architecture

```text
┌─────────────────────────────┐
│        Next.js Client       │
│                             │
│  Attendee | Organizer       │
│  Admin Dashboards           │
└──────────────┬──────────────┘
               │
               │ HTTPS / REST API
               │ Socket.IO
               ▼
┌─────────────────────────────┐
│     Node.js / Express API   │
│                             │
│ Authentication              │
│ Events                      │
│ Tickets                     │
│ Payments                    │
│ Notifications               │
│ Analytics                   │
│ Support                     │
└──────────────┬──────────────┘
               │
               │ Prisma ORM
               ▼
┌─────────────────────────────┐
│        PostgreSQL           │
│                             │
│ Users                       │
│ Events                      │
│ Tickets                     │
│ Payments                    │
│ Notifications               │
│ Support Records             │
└─────────────────────────────┘

External Services:
Stripe | AWS S3 | Email | SMS | Push Notifications

Repository Structure
eventify-event-management-platform/
│
├── backend/
│   ├── docs/
│   │   └── api-docs.yaml
│   ├── prisma/
│   │   ├── migrations/
│   │   └── schema.prisma
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── jobs/
│   │   ├── lib/
│   │   ├── middleware/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── utils/
│   │   └── server.js
│   ├── Jenkinsfile
│   └── package.json
│
├── frontend/
│   ├── config/
│   ├── src/
│   │   ├── app/
│   │   ├── components/
│   │   ├── contexts/
│   │   ├── data/
│   │   ├── hooks/
│   │   ├── lib/
│   │   ├── store/
│   │   ├── types/
│   │   └── utils/
│   ├── Jenkinsfile
│   ├── next.config.js
│   ├── tailwind.config.js
│   └── package.json
│
├── .gitignore
└── README.md

Backend Architecture

The backend follows a modular architecture:

Controllers contain application business logic.
Routes define REST API endpoints.
Middleware handles authentication, authorization, errors, and asynchronous requests.
Services manage notifications, communication, and real-time socket functionality.
Utilities support email, SMS, uploads, PDF generation, AWS S3, and push notifications.
Prisma provides database access and schema management.

Frontend Architecture

The frontend uses the Next.js App Router and reusable React components.

Important frontend areas include:

Authentication
Event discovery
Checkout
Ticket management
Organizer dashboards
Administrator dashboards
Analytics
Notifications
Support management
Role-based access control

React Context is used to manage authentication, application data, users, and Socket.IO connections.

Installation
Prerequisites

Install the following before running the application:

Node.js
npm
PostgreSQL
Git

Clone the Repository
Navigate to the backend folder:

cd backend

Install dependencies:

npm install

Create a .env file using the required environment variables.
Example:
DATABASE_URL=postgresql://username:password@localhost:5432/eventify
JWT_SECRET=your_jwt_secret
PORT=5000

STRIPE_SECRET_KEY=your_stripe_secret_key

AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
AWS_REGION=your_aws_region
AWS_S3_BUCKET_NAME=your_bucket_name

EMAIL_USER=your_email
EMAIL_PASSWORD=your_email_password

TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_PHONE_NUMBER=your_twilio_phone_number

Generate the Prisma client:

npx prisma generate

Run database migrations:

npx prisma migrate dev

Start the backend server:

npm run dev

Frontend Setup

Open another terminal and navigate to the frontend folder:

cd frontend

Install dependencies:

npm install

Create a .env.local file.

Example:

NEXT_PUBLIC_API_URL=http://localhost:5000
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key

Start the frontend application:

npm run dev

Open the application in your browser:

http://localhost:3000


API Documentation

Backend API documentation is available in:
backend/docs/api-docs.yaml

The API includes endpoints for:

Authentication
Users
Events
Tickets
Ticket tiers
Payments
Analytics
Favorites
Notifications
Organizer applications
Waitlists
Support tickets
Uploads
Communication services


Database Management

Open Prisma Studio to inspect and manage database records:
cd backend
npx prisma studio

Security

The application includes:

JWT-based authentication
Password hashing with bcrypt
Role-based authorization
Protected API routes
Input validation
Centralized error handling
Secure environment-variable management
Payment processing through Stripe

Sensitive credentials and environment files are excluded from Git through .gitignore.


CI/CD

The frontend and backend include separate Jenkins pipeline files.

backend/Jenkinsfile
frontend/Jenkinsfile

These pipelines can be configured to automate:

Dependency installation
Application builds
Code-quality checks
Testing
Deployment


Future Enhancements
Dockerize the frontend, backend, and PostgreSQL database
Add automated unit and integration testing
Add GitHub Actions
Deploy the frontend and backend to cloud platforms
Add monitoring and centralized logging
Expand analytics and reporting
Add automated database backups
Improve accessibility
Add multilingual support
Add recommendation features for personalized event discovery

Project Highlights

This project demonstrates experience with:

Full-stack application development
REST API design
Relational database modeling
Role-based access control
Payment integration
Real-time communication
Notification systems
CI/CD pipelines
Cloud storage integration
Secure application configuration
Scalable frontend and backend architecture


Author

Anitha Raj Bale

GitHub: Anitharaj31
Location: New York, USA

License

This project is intended for educational and portfolio purposes.










