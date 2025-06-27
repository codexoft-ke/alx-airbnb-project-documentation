# Airbnb Clone – Backend Requirements Specification

This document defines the **functional**, **technical**, and **performance** requirements for the backend of the Airbnb Clone project. It covers three main features: **User Authentication**, **Property Management**, and **Booking System**.

---

## 🔐 1. User Authentication

### Description
Allow users to register, log in, log out, and securely access protected features based on their role (guest, host, or admin).

### API Endpoints

| Method | Endpoint                 | Description           |
|--------|--------------------------|-----------------------|
| POST   | /api/v1/auth/register     | Register new user     |
| POST   | /api/v1/auth/login        | Log in user           |
| GET    | /api/v1/auth/logout       | Log out user          |

### Input (Registration)
```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "password": "SecurePass123!",
  "role": "guest"
}
```

### Output (Login Success)
```json
{
  "token": "jwt_token_string",
  "user": {
    "id": "UUID",
    "email": "john@example.com",
    "role": "guest"
  }
}
```

### Validation Rules
- Email must be valid and unique.
- Password must be at least 8 characters with letters and numbers.
- Role must be either **guest**, **host**, or **admin**.

### Security & Performance
- Passwords are stored using hashed encryption (e.g., bcrypt).
- Token-based (JWT) authentication.
- Response time under 500ms for login/register.
- Tokens expire in 24 hours and are securely signed.

---

## 🏠 2. Property Management

### Description
Hosts can list, view, update, and delete property listings that guests can search and book.

### API Endpoints

| Method | Endpoint                  | Description               |
|--------|---------------------------|---------------------------|
| POST   | /api/v1/properties         | Create new property listing |
| GET    | /api/v1/properties         | List/search all properties  |
| GET    | /api/v1/properties/:id     | Get a specific property     |
| PUT    | /api/v1/properties/:id     | Update a property listing   |
| DELETE | /api/v1/properties/:id     | Delete a property           |

### Input (Create Property)
```json
{
  "name": "Oceanview Apartment",
  "description": "2-bedroom apartment by the beach",
  "location": "Mombasa, Kenya",
  "pricepernight": 85.00,
  "images": ["https://cdn.example.com/photo1.jpg"]
}
```

### Output (Success Response)
```json
{
  "id": "UUID",
  "host_id": "UUID",
  "name": "Oceanview Apartment",
  "pricepernight": 85.00,
  "location": "Mombasa"
}
```

### Validation Rules
- Only users with role **host** can create or modify listings.
- Price must be positive.
- Image URLs must be valid strings.
- Location and name are required fields.

### Performance
- All properties must be searchable with filters (location, price, rating).
- Listing creation/edit response time under 1 second.

---

## 📅 3. Booking System

### Description
Enable guests to book available properties, manage reservations, and make payments.

### API Endpoints

| Method | Endpoint                  | Description               |
|--------|---------------------------|---------------------------|
| POST   | /api/v1/bookings          | Create new booking        |
| GET    | /api/v1/bookings          | List all bookings (user role) |
| GET    | /api/v1/bookings/:id      | View booking details      |
| DELETE | /api/v1/bookings/:id      | Cancel a booking          |

### Input (Book a Property)
```json
{
  "property_id": "UUID",
  "start_date": "2025-08-01",
  "end_date": "2025-08-05"
}
```

### Output (Booking Confirmation)
```json
{
  "booking_id": "UUID",
  "user_id": "UUID",
  "property_id": "UUID",
  "total_price": 340.00,
  "status": "confirmed"
}
```

### Validation Rules
- The start date must be earlier than the end date.
- Dates must not overlap with existing bookings.
- Bookings must not be created in the past.
- Only authenticated users with role **guest** can book.

### Performance
- Availability check must support concurrent access.
- Booking confirmation within 2 seconds.
- Cancellations should trigger status updates and refunds (if applicable).

---

## 🔁 Other Notes
- All API requests must be authenticated (except register/login).
- Admins have access to all routes for moderation and system overview.
- Validation errors must return meaningful HTTP 400 messages.
- Rate limiting should apply to prevent abuse (e.g., login brute force).
