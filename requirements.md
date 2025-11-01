Backend Feature Specifications
==============================

This document describes the main backend features for the Airbnb Clone project. It focuses on three core areas: User Authentication, Property Management, and Booking System.

1\. User Authentication
-----------------------

Overview:This feature handles how users register, log in, and manage their profiles. It supports both Guests and Hosts.

API Endpoints:

*   POST /api/auth/register — Create a new account
    
*   POST /api/auth/login — Log in an existing user
    
*   GET /api/users/{id} — Retrieve a user’s profile
    
*   PUT /api/users/{id} — Update user details
    

Example Request:{"name": "Jane Doe","email": "jane@example.com","password": "SecurePass123!"}

Example Response:{"id": 1,"name": "Jane Doe","email": "jane@example.com","role": "guest","token": "jwt-token"}

Rules:

*   Email must be unique and valid.
    
*   Password must be at least 8 characters, include uppercase, lowercase, and a number.
    
*   Role can only be guest or host.
    

Performance:

*   Requests should respond in under 300ms.
    
*   JWT tokens expire after 24 hours.
    
*   Passwords are securely hashed using bcrypt.
    

2\. Property Management
-----------------------

Overview:Hosts use this feature to create, update, and manage property listings.

API Endpoints:

*   POST /api/properties — Add a new property
    
*   GET /api/properties/{id} — View property details
    
*   PUT /api/properties/{id} — Edit property info
    
*   DELETE /api/properties/{id} — Remove a property
    
*   GET /api/properties/host/{hostId} — List all properties by host
    

Example Request:{"title": "Seaside Apartment","location": "Mombasa, Kenya","price\_per\_night": 85,"amenities": \"Wi-Fi", "Pool", "Air Conditioning"\}

Example Response:{"id": 102,"title": "Seaside Apartment","host\_id": 5,"status": "active"}

Rules:

*   Title and location are required.
    
*   Price must be greater than zero.
    
*   Host must be authenticated before adding or editing a property.
    

Performance:

*   CRUD operations should complete within 500ms.
    
*   Results support pagination (default: 10 items per page).
    

3\. Booking System
------------------

Overview:Guests use this feature to check property availability, make bookings, and manage reservations.

API Endpoints:

*   POST /api/bookings — Create a booking
    
*   GET /api/bookings/{id} — View booking details
    
*   DELETE /api/bookings/{id} — Cancel a booking
    
*   GET /api/bookings/user/{userId} — Get all bookings for a user
    

Example Request:{"user\_id": 3,"property\_id": 102,"check\_in": "2025-12-10","check\_out": "2025-12-15"}

Example Response:{"booking\_id": 88,"status": "confirmed","total\_price": 425}

Rules:

*   Check-in date must be before check-out.
    
*   Property must be available for the chosen dates.
    
*   No overlapping confirmed bookings allowed.
    

Performance:

*   Booking creation should take less than 400ms.
    
*   Concurrency handling must prevent double bookings.
    
*   Frequent availability checks should be cached.