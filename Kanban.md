# User Journey Flow for a Kanban Board Platform
![IMG_20240606_141527](https://github.com/nandishns/LLD/assets/92267208/27af8637-a644-41e9-a050-c2b6cb3d6897)
# Database Schema

# Users
- user_id PK
- email
- password
- name
- profile_picture
- created_at
- updated_at

# Boards
- board_id PK
- name
- description
- visibility ENUMS (private/public) 
- created_by FK (references users(user_id))
- created_at
- updated_at

# Board Members
- board_member_id PK
- board_id FK (references boards(board_id))
- user_id FK (references users(user_id))
- invited_at
- accepted_at

# Lists
- list_id PK
- board_id FK (references boards(board_id))
- name
- position
- created_at
- updated_at

# Cards
- card_id PK
- list_id FK (references lists(list_id))
- title
- description
- due_date
- created_by FK (references users(user_id))
- created_at
- updated_at

# Card Assignees
- card_assignee_id PK
- card_id FK (references cards(card_id))
- user_id FK (references users(user_id))

# Checklists
- checklist_id PK
- card_id FK (references cards(card_id))
- title
- created_at
- updated_at

# Checklist Items
- checklist_item_id PK
- checklist_id FK (references checklists(checklist_id))
- description
- is_completed
- created_at
- updated_at

# Attachments
- attachment_id PK
- card_id FK (references cards(card_id))
- file_path
- uploaded_by FK (references users(user_id))
- uploaded_at

# Comments
- comment_id PK
- card_id FK (references cards(card_id))
- user_id FK (references users(user_id))
- content
- created_at
- updated_at

# Labels
- label_id PK
- board_id FK (references boards(board_id))
- name
- color
- created_at
- updated_at

# Card Labels
- card_label_id PK
- card_id FK (references cards(card_id))
- label_id FK (references labels(label_id))

# Notifications
- notification_id PK
- user_id FK (references users(user_id))
- content
- created_at
- read_at

# Activity Logs
- activity_log_id PK
- board_id FK (references boards(board_id))
- user_id FK (references users(user_id))
- action
- details
- created_at

