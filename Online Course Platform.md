# Online Course Platform
![IMG_20240606_141543](https://github.com/nandishns/LLD/assets/92267208/b9ab19e7-7e63-4536-ac9c-1dba8a1fd985)

# Database Schema
# Users
- user_id PK
- email
- phone_number
- password
- name
- profile_picture
- bio
- created_at
- updated_at

# Instructors
- instructor_id PK
- user_id FK (references users(user_id))
- bio
- created_at
- updated_at

# Courses
- course_id PK
- instructor_id FK (references instructors(instructor_id))
- title
- description
- category
- price
- status (approved/pending/rejected)
- created_at
- updated_at

# Course Content
- content_id PK
- course_id FK (references courses(course_id))
- title
- content_type (video/document/quiz)
- file_path
- created_at
- updated_at

# Enrollments
- enrollment_id PK
- user_id FK (references users(user_id))
- course_id FK (references courses(course_id))
- enrollment_date
- progress
- completion_status
- completion_date

# Payments
- payment_id PK
- user_id FK (references users(user_id))
- course_id FK (references courses(course_id))
- amount
- payment_date
- status

# Quizzes
- quiz_id PK
- course_id FK (references courses(course_id))
- title
- created_at
- updated_at

# Quiz Questions
- question_id PK
- quiz_id FK (references quizzes(quiz_id))
- question_text
- created_at
- updated_at

# Quiz Answers
- answer_id PK
- question_id FK (references quiz_questions(question_id))
- answer_text
- is_correct
- created_at
- updated_at

# User Quiz Attempts
- attempt_id PK
- user_id FK (references users(user_id))
- quiz_id FK (references quizzes(quiz_id))
- attempt_date
- score
- created_at

# Forums
- forum_id PK
- course_id FK (references courses(course_id))
- title
- created_at
- updated_at

# Forum Posts
- post_id PK
- forum_id FK (references forums(forum_id))
- user_id FK (references users(user_id))
- content
- created_at
- updated_at

# Certificates
- certificate_id PK
- user_id FK (references users(user_id))
- course_id FK (references courses(course_id))
- issued_date
- file_path

### Considerations and Edge Cases

- Course Creation:
  - Manage draft courses.
  - Handle rejection feedback from admin.
  - Allow updates to approved courses (with new review).

- Course Enrollment:
  - Support for different payment gateways.
  - Handle payment failures and retries.
  - Manage refund requests.

- Learning Experience:
  - Track user activity and progress accurately.
  - Provide support for multimedia content.
  - Handle quiz retries and scoring.

