# Delivery Service Platform

# Users
- user_id PK
- email
- phone_number
- password
- name
- profile_picture
- address
- created_at
- updated_at

# Couriers
- courier_id PK
- name
- phone_number
- email
- vehicle_details
- created_at
- updated_at

# Deliveries
- delivery_id PK
- sender_id FK (references users(user_id))
- recipient_name
- recipient_address
- recipient_phone
- recipient_email
- parcel_weight
- parcel_dimensions
- parcel_description
- delivery_option ENUM (standard, express, insurance)
- status (requested, assigned, picked_up, in_transit, delivered)
- created_at
- updated_at

# Delivery Assignments
- assignment_id PK
- delivery_id FK (references deliveries(delivery_id))
- courier_id FK (references couriers(courier_id))
- assigned_at
- picked_up_at
- delivered_at

# Ratings
- rating_id PK
- user_id FK (references users(user_id))
- courier_id FK (references couriers(courier_id))
- delivery_id FK (references deliveries(delivery_id))
- rating
- comment
- created_at

# Notifications
- notification_id PK
- user_id FK (references users(user_id))
- delivery_id FK (references deliveries(delivery_id))
- content
- created_at
- read_at

# Locations
- location_id PK
- delivery_id FK (references deliveries(delivery_id))
- courier_id FK (references couriers(courier_id))
- latitude
- longitude
- timestamp

# could use WebSocker or Kafka for live location sharing and use maps to point the location
