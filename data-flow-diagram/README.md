# Data Flow Diagram (DFD)

This folder contains the Data Flow Diagram for the Airbnb Clone backend.  
It illustrates how data moves between users, the system, and external components such as the database and payment gateway.

## Purpose
The goal of this DFD is to visualize how major entities (Users, Properties, Bookings, and Payments) interact with system processes.  
It helps developers and designers understand how data flows through the backend, ensuring clarity before implementation.

## Key Components

### External Entities
- **User (Guest/Host):** Initiates actions like registration, booking, or property listing.
- **Payment Gateway:** Handles secure transactions between Guests and Hosts.

### Main Processes
1. **User Management**
   - Registration and login  
   - Profile updates  
   - Authentication and session handling  

2. **Property Management**
   - Listing creation, update, and removal  
   - Availability management  
   - Host dashboard and property overview  

3. **Booking Management**
   - Search and filter properties  
   - Booking confirmation and cancellation  
   - Review and rating submissions  

4. **Payment Processing**
   - Secure guest payments  
   - Host payouts after stays  
   - Refunds for valid cancellations  

### Data Stores
- **User Database:** Stores user credentials and profiles  
- **Property Database:** Holds property details, pricing, and availability  
- **Booking Database:** Tracks bookings, dates, and statuses  
- **Payment Records:** Maintains transaction and refund details  



