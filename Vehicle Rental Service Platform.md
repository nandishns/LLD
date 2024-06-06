

# User Journey Flow for a Vehicle Rental Service Platform

# Users
- user_id PK
- email
- phone_number
- password
- name
- profile_picture
- driver_license_number
- driver_license_expiry
- address
- created_at
- updated_at

# Vehicles
- vehicle_id PK
- license_plate
- make
- model
- year
- color
- rental_price_per_day
- rental_price_per_week
- rental_price_per_month
- status ENUM (available, rented, maintenance)
- location
- created_at
- updated_at

# Bookings
- booking_id PK
- user_id FK (references users(user_id))
- vehicle_id FK (references vehicles(vehicle_id))
- pickup_location
- dropoff_location
- rental_start_date
- rental_end_date
- total_price
- payment_plan (daily, weekly, monthly)
- booking_status (confirmed, canceled, completed)
- created_at
- updated_at

# Payments
- payment_id PK
- booking_id FK (references bookings(booking_id))
- user_id FK (references users(user_id))
- amount
- payment_method ENUM (card, online, cash)
- payment_status ENUM (pending, completed, failed)
- payment_date
- payment_plan ENUM (daily, weekly, monthly)
- next_payment_date

# Inspections
- inspection_id PK
- booking_id FK (references bookings(booking_id))
- vehicle_id FK (references vehicles(vehicle_id))
- inspection_type ENUM (pickup, return)
- damages_reported
- created_at
- updated_at

# Extensions
- extension_id PK
- booking_id FK (references bookings(booking_id))
- new_rental_end_date
- additional_price
- created_at
- updated_at

# Ratings
- rating_id PK
- user_id FK (references users(user_id))
- vehicle_id FK (references vehicles(vehicle_id))
- rating
- comment
- created_at

# Notifications
- notification_id PK
- user_id FK (references users(user_id))
- content
- created_at
- read_at

