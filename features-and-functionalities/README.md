# Features and Functionalities – Airbnb Clone Backend

This document outlines the key backend features and functionalities required to support the Airbnb Clone platform.

---

## 🔐 1. User Authentication and Authorization
- **User Registration**: New users can register with email, password, and role (guest/host).
- **Login/Logout**: Secure login using hashed passwords and session/token-based authentication.
- **User Roles**:
  - **Guest**: Can search and book properties.
  - **Host**: Can list properties and manage bookings.
  - **Admin**: Can manage users and oversee platform data.

---

## 🏠 2. Property Management
- **Add New Property**: Hosts can list properties with details like name, description, location, and nightly price.
- **Edit/Delete Property**: Hosts can modify or remove their property listings.
- **Upload Property Photos**: Supports image storage and retrieval.
- **Set Availability**: Hosts define available booking periods.

---

## 🔎 3. Search and Filter
- **Search by Location**: Guests can search properties based on city or location.
- **Filters**: Filter by price range, availability, property type, and ratings.

---

## 📆 4. Booking System
- **Create Booking**: Guests can book properties for specific dates.
- **Check Availability**: System prevents overlapping bookings.
- **Cancel Booking**: Users can cancel bookings before a certain deadline.
- **Booking Status**: `pending`, `confirmed`, `canceled`

---

## 💳 5. Payment Handling
- **Supported Methods**: PayPal, Stripe, and Credit/Debit Cards.
- **Payment Link to Booking**: Each booking has an associated payment.
- **Transaction History**: Guests can view their payment history.
- **Refund Handling**: Automatic status updates on booking cancellation.

---

## 🌟 6. Reviews and Ratings
- **Submit Review**: Guests can review and rate a property after checkout.
- **View Reviews**: All users can read property reviews before booking.
- **Rating Scale**: 1 to 5 stars.

---

## 💬 7. Messaging System
- **User Messaging**: Guests and hosts can send messages to each other.
- **Inbox Management**: View conversations by recipient/sender.

---

## 🛠 8. Admin Features
- **User Management**: Ban users, reset passwords, manage roles.
- **Property Moderation**: View and approve/reject listings.
- **System Metrics**: View stats on bookings, users, and payments.

---

## 📁 Directory Info
- **Location**: `features-and-functionalities/`
- **File**: `README.md`
- **Diagram**: Include `features-and-functionalities.png` exported from Draw.io

---

## 📌 Notes
- This documentation will guide the creation of a **Use Case Diagram**, **User Stories**, **Data Flow Diagram**, and **Requirements Specification**.
