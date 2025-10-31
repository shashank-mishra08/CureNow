# CureNow - Online Doctor Appointment Booking System
## 🔗 Links

🚀 [Frontend](https://cure-now.vercel.app)  
🛠️ [Backend](https://curenow-tpv0.onrender.com)  
🧑‍⚕️ [Admin Panel And Doctor Login](https://cure-now-vyzf.vercel.app)

CureNow is a comprehensive full-stack application designed to streamline the process of booking doctor appointments. It features distinct panels for users, doctors, and administrators, ensuring a tailored experience for each role.

## Features

*   **User Management:** Secure registration, login, and profile management for patients.
*   **Doctor Management:** Administrators can add new doctors, manage their profiles, and track their availability. Doctors can manage their own profiles and availability.
*   **Appointment Management:** Users can book, view, and cancel appointments. Doctors can view and complete appointments. Administrators can view and cancel all appointments.
*   **Payment Integration:** Seamless payment processing through Razorpay and Stripe.
*   **Cloud Storage:** Image uploads (e.g., doctor profiles) are handled via Cloudinary.
*   **Admin Dashboard:** Overview and management capabilities for administrators.
*   **Doctor Dashboard:** Personalized dashboard for doctors to manage their appointments and availability.

## Tech Stack

**Frontend:**
*   React.js
*   Vite
*   Tailwind CSS

**Backend:**
*   Node.js
*   Express.js

**Database:**
*   MongoDB (via Mongoose ODM)

**Authentication:**
*   JWT (JSON Web Tokens)
*   Bcrypt (for password hashing)

**Payment Gateways:**
*   Razorpay
*   Stripe

**Cloud Storage:**
*   Cloudinary

**Deployment:**
*   Frontend: Vercel
*   Backend: Render

## Project Structure

The project is organized into three main directories:

*   `admin/`: Contains the React.js frontend application for the administrator panel.
*   `backend/`: Houses the Node.js/Express.js backend API.
*   `frontend/`: Contains the React.js frontend application for the user-facing portal.

## API Endpoints

The backend API is structured with clear routes for user, doctor, and admin functionalities.

### User Routes (`/api/user`)

| Method | Endpoint              | Description                                   | Authentication |
| :----- | :-------------------- | :-------------------------------------------- | :------------- |
| `POST` | `/register`           | Register a new user                           | None           |
| `POST` | `/login`              | Log in a user                                 | None           |
| `GET`  | `/get-profile`        | Get user profile data                         | `authUser`     |
| `POST` | `/update-profile`     | Update user profile (with image upload)       | `authUser`     |
| `POST` | `/book-appointment`   | Book a new appointment                        | `authUser`     |
| `GET`  | `/appointments`       | Get a list of user's appointments             | `authUser`     |
| `POST` | `/cancel-appointment` | Cancel an existing appointment                | `authUser`     |
| `POST` | `/payment-razorpay`   | Initiate Razorpay payment for an appointment  | `authUser`     |
| `POST` | `/verifyRazorpay`     | Verify Razorpay payment status                | `authUser`     |
| `POST` | `/payment-stripe`     | Initiate Stripe payment for an appointment    | `authUser`     |
| `POST` | `/verifyStripe`       | Verify Stripe payment status                  | `authUser`     |

### Doctor Routes (`/api/doctor`)

| Method | Endpoint              | Description                                   | Authentication |
| :----- | :-------------------- | :-------------------------------------------- | :------------- |
| `POST` | `/login`              | Log in a doctor                               | None           |
| `POST` | `/cancel-appointment` | Cancel a doctor's appointment                 | `authDoctor`   |
| `GET`  | `/appointments`       | Get a list of doctor's appointments           | `authDoctor`   |
| `GET`  | `/list`               | Get a list of all doctors                     | None           |
| `POST` | `/change-availability`| Change doctor's availability                  | `authDoctor`   |
| `POST` | `/complete-appointment`| Mark an appointment as complete               | `authDoctor`   |
| `GET`  | `/dashboard`          | Get doctor dashboard data                     | `authDoctor`   |
| `GET`  | `/profile`            | Get doctor profile data                       | `authDoctor`   |
| `POST` | `/update-profile`     | Update doctor profile                         | `authDoctor`   |

### Admin Routes (`/api/admin`)

| Method | Endpoint              | Description                                   | Authentication |
| :----- | :-------------------- | :-------------------------------------------- | :------------- |
| `POST` | `/login`              | Log in an admin                               | None           |
| `POST` | `/add-doctor`         | Add a new doctor (with image upload)          | `authAdmin`    |
| `GET`  | `/appointments`       | Get all appointments                          | `authAdmin`    |
| `POST` | `/cancel-appointment` | Cancel any appointment                        | `authAdmin`    |
| `GET`  | `/all-doctors`        | Get a list of all doctors                     | `authAdmin`    |
| `POST` | `/change-availability`| Change doctor's availability (admin override) | `authAdmin`    |
| `GET`  | `/dashboard`          | Get admin dashboard data                      | `authAdmin`    |

## Local Development Setup

To run this project locally, follow these steps:

### Prerequisites

*   Node.js (v18 or higher recommended)
*   MongoDB instance (local or cloud-hosted like MongoDB Atlas)
*   Cloudinary Account
*   Razorpay Account
*   Stripe Account

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd prescripto-full-stack
```

### 2. Backend Setup

Navigate to the `backend` directory:

```bash
cd backend
```

Create a `.env` file in the `backend` directory and add your environment variables:

```
PORT=4000
CURRENCY="INR"
JWT_SECRET="your_jwt_secret_key"

# Admin Panel Credentials
ADMIN_EMAIL="your_admin_email@example.com"
ADMIN_PASSWORD="your_admin_password"

# MongoDB Setup
MONGODB_URI="your_mongodb_connection_string"

# Cloudinary Setup
CLOUDINARY_NAME="your_cloudinary_cloud_name"
CLOUDINARY_API_KEY="your_cloudinary_api_key"
CLOUDINARY_SECRET_KEY="your_cloudinary_api_secret"

# Razorpay Payment Integration
RAZORPAY_KEY_ID="your_razorpay_key_id"
RAZORPAY_KEY_SECRET="your_razorpay_key_secret"

# Stripe Payment Integration
STRIPE_SECRET_KEY="your_stripe_secret_key"
```

Install dependencies and start the backend server:

```bash
npm install
npm start
```

The backend will run on `http://localhost:4000`.

### 3. Frontend Setup (User Portal)

Navigate to the `frontend` directory:

```bash
cd ../frontend
```

Create a `.env` file in the `frontend` directory:

```
VITE_BACKEND_URL="http://localhost:4000"
VITE_RAZORPAY_KEY_ID="your_razorpay_key_id"
```

Install dependencies and start the frontend development server:

```bash
npm install
npm run dev
```

The user frontend will typically run on `http://localhost:5173` (or another available port).

### 4. Admin Frontend Setup

Navigate to the `admin` directory:

```bash
cd ../admin
```

Create a `.env` file in the `admin` directory:

```
VITE_BACKEND_URL="http://localhost:4000"
```

Install dependencies and start the admin frontend development server:

```bash
npm install
npm run dev
```

The admin frontend will typically run on `http://localhost:5174` (or another available port).

## Deployment

This project is set up for deployment on Vercel (Frontend) and Render (Backend). Ensure you configure all necessary environment variables on both platforms as described in the "Backend Configuration (on Render)" and "Frontend Configuration (on Vercel)" sections above.

---

**Author:**
Shashank Mishra
---
