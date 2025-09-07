User Authentication
Functional Requirements

--User Registration

    System must allow users to sign up as a guest or host.
    Users must provide: first name, last name, email (unique), password.
    Optional fields: phone number, profile picture.
    Passwords must be securely hashed and stored.

--User Login

    Login via email and password.
    OAuth integration (Google, Facebook) for social login.

--Session Management

    Use JWT tokens for authentication in APIs.
    Refresh tokens for long-term sessions.
    Expired tokens must be invalidated.

--Password Management

    Forgot password: Send password reset link via email.
    Change password: Requires current password verification.

Role-based Access Control (RBAC)

    Guest → Can book properties, leave reviews.
    Host → Can add/manage properties.
    Admin → Can manage users, properties, bookings, payments.

Non-Functional Requirements

    Secure transmission of credentials using HTTPS/TLS.
    JWT tokens must be signed with strong algorithms (HS256/RS256).
    Limit login attempts to prevent brute force attacks.
    Authentication API must respond within 500ms.

Property Management
Functional Requirements

Create Property
    Hosts can add new properties with:
    Title, description, location, amenities, price per night, availability calendar, and images.

Update Property

Hosts can edit property details (price, description, availability).
Delete Property
Hosts can deactivate/remove a property listing.

View Property

    Guests can view property listings with details and images.
    Search and Filter
    Guests can filter by:
        Location
        Price range
        Number of guests
        Amenities (Wi-Fi, pool, pet-friendly)
        Pagination for large results.

Non-Functional Requirements

    Property images stored in cloud storage (e.g., AWS S3, Firebase Storage).
    Search queries must return results within 2 seconds.
    Support scaling to handle 10,000+ property listings.

Booking System
Functional Requirements

    Create Booking
    Guests select property and dates.
    System validates availability to prevent double-booking.
    Booking is marked as pending until payment is confirmed.
    Booking Confirmation
    Upon successful payment, status changes to confirmed.
    Booking Cancellation
    Guest or host can cancel:
        Guest → Refund according to cancellation policy.
        Host → Notify guest and process refund.
    Status updated to canceled.
    Booking Status Tracking
    Possible statuses: pending, confirmed, canceled, completed.
