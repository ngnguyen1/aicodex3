# Kahoot Clone

This project is a clone of the popular quiz game Kahoot. It allows users to create, share, and play quizzes in a fun and interactive way.
- Create HighLevel Requirements
- Create Functional Requirement: prototype, validation, ...
- Create System Design
- Create Infra Design
- Create API Design for each module
- Create DB Design for each module


Creating a comprehensive clone of Kahoot involves multiple layers of planning and design. Below are detailed outlines for High-Level Requirements, Functional Requirements, System Design, Infrastructure Design, API Design, and Database Design tailored to your project.

---

## 1. High-Level Requirements

### 1.1 **User Management**
- **User Registration/Login:** Support for user sign-up, login, password recovery.
- **Profile Management:** Users can edit their profiles, including avatars and personal information.
- **Roles and Permissions:** Different roles such as Admin, Creator, Player.

### 1.2 **Quiz Creation**
- **Create Quizzes:** Users can create multiple-choice quizzes with questions, answers, timers.
- **Media Support:** Ability to add images, videos, and other media to questions.
- **Templates:** Predefined templates for different types of quizzes.

### 1.3 **Quiz Sharing and Management**
- **Share Quizzes:** Share via links, social media, or within the platform.
- **Manage Quizzes:** Edit, delete, duplicate quizzes.
- **Privacy Settings:** Public, private, or restricted access quizzes.

### 1.4 **Playing Quizzes**
- **Live Games:** Host real-time quiz games with multiple players.
- **Single-Player Mode:** Play quizzes individually for practice or assessment.
- **Leaderboard:** Display rankings based on scores and response times.

### 1.5 **Interactive Features**
- **Real-time Interaction:** Live updates, chat, and polls during quizzes.
- **Gamification:** Points, badges, and rewards to enhance engagement.

### 1.6 **Analytics and Reporting**
- **Performance Analytics:** Track user performance, quiz statistics.
- **Export Data:** Export reports in various formats (CSV, PDF).

### 1.7 **Notifications and Messaging**
- **Email/SMS Notifications:** Inform users about quiz invitations, results.
- **In-App Messaging:** Communication between players and creators.

### 1.8 **Security and Compliance**
- **Data Protection:** Ensure user data privacy and compliance with regulations (e.g., GDPR).
- **Secure Authentication:** Use secure methods for user authentication and data access.

---

## 2. Functional Requirements

### 2.1 **Prototype Development**
- **Wireframes and Mockups:** Create visual representations of key interfaces (e.g., quiz creator, game lobby).
- **Interactive Prototype:** Develop a clickable prototype to demonstrate user flows.

### 2.2 **Validation**
- **User Testing:** Conduct usability testing sessions with target users.
- **Feedback Integration:** Collect and incorporate feedback to refine functionalities.
- **Automated Testing:** Implement unit, integration, and end-to-end tests to ensure functionality.

### 2.3 **Core Functionalities**
- **User Authentication:** Register, login, logout, password reset.
- **Quiz Management:** Create, edit, delete, duplicate quizzes.
- **Game Hosting:** Start, join, and manage live quiz sessions.
- **Real-time Communication:** Implement WebSockets or similar for live interactions.
- **Scoring System:** Calculate and display scores based on accuracy and speed.
- **Media Handling:** Upload and serve multimedia content within quizzes.
- **Analytics Dashboard:** Provide insights into quiz performance and user engagement.

### 2.4 **User Interface**
- **Responsive Design:** Ensure compatibility across devices (desktop, mobile, tablets).
- **Accessibility:** Adhere to accessibility standards (e.g., WCAG).

### 2.5 **Integration**
- **Third-Party Services:** Integrate with services like email providers, social media, analytics tools.
- **APIs:** Provide RESTful APIs for external integrations and mobile applications.

---

## 3. System Design

### 3.1 **Architecture Overview**
- **Microservices Architecture:** Separate services for user management, quiz management, game sessions, real-time communication, analytics.
- **Client-Server Model:** Frontend interacts with backend services via APIs.

### 3.2 **Components**
- **Frontend Application:**
  - Built with frameworks like React, Angular, or Vue.js.
  - Handles user interface, client-side logic, real-time updates.
  
- **Backend Services:**
  - **User Service:** Handles authentication, authorization, profile management.
  - **Quiz Service:** Manages quiz creation, storage, retrieval.
  - **Game Service:** Manages live game sessions, player interactions.
  - **Media Service:** Handles media uploads, storage, and delivery.
  - **Analytics Service:** Collects and processes data for reporting.
  
- **Real-Time Communication:**
  - Implemented using WebSockets or technologies like Socket.io for live interactions.

- **Database Layer:**
  - Use relational databases (e.g., PostgreSQL) for structured data.
  - Use NoSQL databases (e.g., MongoDB) for unstructured data if necessary.

- **Caching Layer:**
  - Utilize Redis or Memcached for caching frequently accessed data.

- **API Gateway:**
  - Manage and route API requests, handle rate limiting, authentication.

### 3.3 **Data Flow**
1. **User Interaction:** Users interact with the frontend application.
2. **API Requests:** Frontend sends requests to backend services via API Gateway.
3. **Service Processing:** Backend services process requests, interact with databases/cache.
4. **Real-Time Updates:** For live games, use WebSockets to push updates to clients.
5. **Data Storage:** Persist data in appropriate databases.
6. **Analytics Processing:** Collect and analyze data for reporting.

---

## 4. Infrastructure Design

### 4.1 **Deployment Architecture**
- **Cloud Provider:** Utilize AWS, Azure, or Google Cloud for scalable infrastructure.
- **Containerization:** Use Docker to containerize services.
- **Orchestration:** Use Kubernetes for managing containerized applications.
- **Load Balancing:** Implement load balancers to distribute traffic evenly across servers.

### 4.2 **Scalability and Reliability**
- **Auto-Scaling:** Automatically scale services based on demand.
- **High Availability:** Deploy services across multiple availability zones.
- **Disaster Recovery:** Implement backup and recovery strategies.

### 4.3 **Storage Solutions**
- **Database Services:** Managed database services (e.g., AWS RDS, Google Cloud SQL).
- **Object Storage:** Use services like AWS S3 for media and file storage.
- **Content Delivery Network (CDN):** Distribute static assets globally for faster access.

### 4.4 **Security**
- **Network Security:** Use Virtual Private Clouds (VPC), firewalls, and security groups.
- **Data Encryption:** Encrypt data at rest and in transit (SSL/TLS).
- **Access Control:** Implement IAM roles and policies to restrict access.

### 4.5 **Monitoring and Logging**
- **Monitoring Tools:** Use tools like Prometheus, Grafana for system monitoring.
- **Logging Services:** Centralize logs with services like ELK Stack (Elasticsearch, Logstash, Kibana) or AWS CloudWatch.
- **Alerting:** Set up alerts for system failures, performance issues.

### 4.6 **CI/CD Pipeline**
- **Continuous Integration:** Automate builds and testing with tools like Jenkins, GitHub Actions.
- **Continuous Deployment:** Deploy updates automatically to staging and production environments.

---

## 5. API Design for Each Module

### 5.1 **User Service API**

**Endpoints:**
- `POST /api/users/register` – Register a new user.
- `POST /api/users/login` – Authenticate a user.
- `GET /api/users/profile` – Get user profile.
- `PUT /api/users/profile` – Update user profile.
- `POST /api/users/password-reset` – Initiate password reset.
- `PUT /api/users/password-reset` – Complete password reset.

**Sample Request/Response:**

- **Register:**
  - **Request:**
    ```json
    {
      "username": "johndoe",
      "email": "john@example.com",
      "password": "SecurePass123"
    }
    ```
  - **Response:**
    ```json
    {
      "userId": "abc123",
      "username": "johndoe",
      "email": "john@example.com",
      "token": "jwt-token"
    }
    ```

### 5.2 **Quiz Service API**

**Endpoints:**
- `POST /api/quizzes` – Create a new quiz.
- `GET /api/quizzes/{quizId}` – Retrieve a quiz.
- `PUT /api/quizzes/{quizId}` – Update a quiz.
- `DELETE /api/quizzes/{quizId}` – Delete a quiz.
- `GET /api/quizzes` – List quizzes with filtering options.

**Sample Request/Response:**

- **Create Quiz:**
  - **Request:**
    ```json
    {
      "title": "General Knowledge",
      "description": "A quiz on general knowledge topics.",
      "questions": [
        {
          "questionText": "What is the capital of France?",
          "options": ["Paris", "Berlin", "Rome", "Madrid"],
          "correctOption": "Paris",
          "mediaUrl": "http://example.com/image1.png",
          "timeLimit": 30
        },
        // More questions...
      ],
      "isPublic": true
    }
    ```
  - **Response:**
    ```json
    {
      "quizId": "quiz123",
      "title": "General Knowledge",
      "description": "A quiz on general knowledge topics.",
      "creatorId": "user123",
      "createdAt": "2024-04-27T12:34:56Z",
      "isPublic": true
    }
    ```

### 5.3 **Game Service API**

**Endpoints:**
- `POST /api/games` – Create a new game session.
- `GET /api/games/{gameId}` – Get game session details.
- `POST /api/games/{gameId}/join` – Join a game session.
- `POST /api/games/{gameId}/start` – Start the game.
- `POST /api/games/{gameId}/answer` – Submit an answer.
- `GET /api/games/{gameId}/leaderboard` – Get leaderboard.

**Sample Request/Response:**

- **Join Game:**
  - **Request:**
    ```json
    {
      "gameId": "game123",
      "userId": "user456",
      "username": "player1"
    }
    ```
  - **Response:**
    ```json
    {
      "gameId": "game123",
      "playerId": "player456",
      "username": "player1",
      "status": "joined"
    }
    ```

### 5.4 **Analytics Service API**

**Endpoints:**
- `GET /api/analytics/quizzes` – Get analytics for quizzes.
- `GET /api/analytics/users` – Get user engagement data.
- `GET /api/analytics/games/{gameId}` – Get detailed game analytics.

**Sample Request/Response:**

- **Get Quiz Analytics:**
  - **Request:**
    ```
    GET /api/analytics/quizzes?quizId=quiz123
    ```
  - **Response:**
    ```json
    {
      "quizId": "quiz123",
      "totalPlays": 1500,
      "averageScore": 75,
      "mostMissedQuestions": [
        {
          "questionId": "q1",
          "text": "What is the capital of France?",
          "incorrectAttempts": 300
        },
        // More questions...
      ]
    }
    ```

### 5.5 **Media Service API**

**Endpoints:**
- `POST /api/media/upload` – Upload media files.
- `GET /api/media/{mediaId}` – Retrieve media files.
- `DELETE /api/media/{mediaId}` – Delete media files.

**Sample Request/Response:**

- **Upload Media:**
  - **Request:**
    - Multipart form data with file.
  - **Response:**
    ```json
    {
      "mediaId": "media123",
      "url": "http://cdn.example.com/media/media123.png",
      "uploadedAt": "2024-04-27T12:34:56Z"
    }
    ```

---

## 6. Database Design for Each Module

### 6.1 **User Service Database**

**Tables:**

- **Users**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | user_id      | UUID        | Primary Key               |
  | username     | VARCHAR(50) | Unique, Not Null          |
  | email        | VARCHAR(100)| Unique, Not Null          |
  | password_hash| VARCHAR(255)| Not Null                  |
  | avatar_url   | VARCHAR(255)| Nullable                  |
  | role         | ENUM        | ('Admin', 'Creator', 'Player') |
  | created_at   | TIMESTAMP   | Default Current Timestamp |
  | updated_at   | TIMESTAMP   | On Update Current Timestamp |

- **Password_Reset_Tokens**
  | Field       | Type      | Constraints               |
  |-------------|-----------|---------------------------|
  | token_id    | UUID      | Primary Key               |
  | user_id     | UUID      | Foreign Key to Users      |
  | token       | VARCHAR(255)| Unique, Not Null        |
  | expires_at  | TIMESTAMP | Not Null                  |
  | created_at  | TIMESTAMP | Default Current Timestamp |

### 6.2 **Quiz Service Database**

**Tables:**

- **Quizzes**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | quiz_id      | UUID        | Primary Key               |
  | title        | VARCHAR(255)| Not Null                  |
  | description  | TEXT        | Nullable                  |
  | creator_id   | UUID        | Foreign Key to Users      |
  | is_public    | BOOLEAN     | Default False             |
  | created_at   | TIMESTAMP   | Default Current Timestamp |
  | updated_at   | TIMESTAMP   | On Update Current Timestamp |

- **Questions**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | question_id  | UUID        | Primary Key               |
  | quiz_id      | UUID        | Foreign Key to Quizzes    |
  | question_text| TEXT        | Not Null                  |
  | media_url    | VARCHAR(255)| Nullable                  |
  | time_limit   | INTEGER     | Not Null (seconds)        |
  | order        | INTEGER     | Not Null                  |

- **Options**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | option_id    | UUID        | Primary Key               |
  | question_id  | UUID        | Foreign Key to Questions  |
  | option_text  | VARCHAR(255)| Not Null                  |
  | is_correct   | BOOLEAN     | Default False             |
  | order        | INTEGER     | Not Null                  |

- **Quiz_Sharing**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | share_id     | UUID        | Primary Key               |
  | quiz_id      | UUID        | Foreign Key to Quizzes    |
  | shared_with  | VARCHAR(255)| Email or user identifier  |
  | shared_at    | TIMESTAMP   | Default Current Timestamp |

### 6.3 **Game Service Database**

**Tables:**

- **Games**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | game_id      | UUID        | Primary Key               |
  | quiz_id      | UUID        | Foreign Key to Quizzes    |
  | host_id      | UUID        | Foreign Key to Users      |
  | status       | ENUM        | ('Pending', 'Active', 'Completed') |
  | started_at   | TIMESTAMP   | Nullable                  |
  | ended_at     | TIMESTAMP   | Nullable                  |

- **Game_Players**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | game_id      | UUID        | Foreign Key to Games      |
  | player_id    | UUID        | Foreign Key to Users      |
  | username     | VARCHAR(50) | Not Null                  |
  | score        | INTEGER     | Default 0                 |
  | joined_at    | TIMESTAMP   | Default Current Timestamp |
  | PRIMARY KEY (game_id, player_id) |

- **Player_Answers**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | answer_id    | UUID        | Primary Key               |
  | game_id      | UUID        | Foreign Key to Games      |
  | player_id    | UUID        | Foreign Key to Users      |
  | question_id  | UUID        | Foreign Key to Questions  |
  | selected_option | UUID     | Foreign Key to Options    |
  | answered_at  | TIMESTAMP   | Default Current Timestamp |

### 6.4 **Analytics Service Database**

**Tables:**

- **Quiz_Analytics**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | analytics_id | UUID        | Primary Key               |
  | quiz_id      | UUID        | Foreign Key to Quizzes    |
  | total_plays   | INTEGER     | Default 0                 |
  | average_score | FLOAT       | Nullable                  |
  | created_at    | TIMESTAMP   | Default Current Timestamp |

- **Question_Analytics**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | analytics_id | UUID        | Primary Key               |
  | question_id  | UUID        | Foreign Key to Questions  |
  | incorrect_attempts | INTEGER | Default 0                 |
  | created_at    | TIMESTAMP   | Default Current Timestamp |

- **User_Engagement**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | engagement_id| UUID        | Primary Key               |
  | user_id      | UUID        | Foreign Key to Users      |
  | quizzes_played| INTEGER    | Default 0                 |
  | quizzes_created| INTEGER   | Default 0                 |
  | last_active   | TIMESTAMP   | Nullable                  |

### 6.5 **Media Service Database**

**Tables:**

- **Media**
  | Field        | Type        | Constraints               |
  |--------------|-------------|---------------------------|
  | media_id     | UUID        | Primary Key               |
  | uploader_id  | UUID        | Foreign Key to Users      |
  | url          | VARCHAR(255)| Not Null                  |
  | file_type    | VARCHAR(50) | Not Null                  |
  | size         | INTEGER     | Not Null (bytes)          |
  | uploaded_at  | TIMESTAMP   | Default Current Timestamp |

