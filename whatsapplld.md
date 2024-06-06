# Whatsapp Schema

# Users
- user_id PK
- phone_number
- name
- profile_picture
- status
- created_at
- updated_at

# Contacts
- contact_id PK
- user_id FK (references users(user_id))
- contact_user_id FK (references users(user_id))
- added_at

# Messages
- message_id PK
- sender_id FK (references users(user_id))
- receiver_id FK (references users(user_id))
- content
- sent_at
- delivered_at
- read_at
- forwarded_from_message_id FK (references messages(message_id))

# Groups
- group_id PK
- group_name
- created_by FK (references users(user_id))
- created_at

# Group Members
- group_member_id PK
- group_id FK (references groups(group_id))
- user_id FK (references users(user_id))
- added_at

# Group Messages
- group_message_id PK
- group_id FK (references groups(group_id))
- sender_id FK (references users(user_id))
- content
- sent_at
- delivered_at
- read_at
- forwarded_from_group_message_id FK (references group_messages(group_message_id))

# Communities
- community_id PK
- community_name
- created_by FK (references users(user_id))
- created_at

# Community Groups
- community_group_id PK
- community_id FK (references communities(community_id))
- group_id FK (references groups(group_id))
- added_at

# Community Announcements
- announcement_id PK
- community_id FK (references communities(community_id))
- sender_id FK (references users(user_id))
- content
- sent_at

# Multimedia
- multimedia_id PK
- message_id FK (references messages(message_id))
- group_message_id FK (references group_messages(group_message_id))
- community_announcement_id FK (references community_announcements(announcement_id))
- file_path
- file_type
- uploaded_at
- forwarded_from_multimedia_id FK (references multimedia(multimedia_id))

# Stories
- story_id PK
- user_id FK (references users(user_id))
- content
- file_path
- file_type
- created_at
- expires_at

# Story Views
- story_view_id PK
- story_id FK (references stories(story_id))
- user_id FK (references users(user_id))
- viewed_at

# Calls
- call_id PK
- caller_id FK (references users(user_id))
- receiver_id FK (references users(user_id))
- call_type
- call_started_at
- call_ended_at