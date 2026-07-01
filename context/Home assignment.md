# Assignment: User Leaderboard System

---

## Overview

As a gaming company experiencing rapid user growth, implementing a user leaderboard system is essential to showcase top players and display user rankings. A leaderboard feature is known to drive engagement and boost retention, ultimately impacting revenue. The leaderboard should display a user’s position, name, image, and total score, as shown in [leaderboard.png](leaderboard.png).

The system must efficiently handle over 10 million users while delivering high performance and scalability. The tech stack includes Node.js, TypeScript, PostgreSQL, and (optionally) Redis for caching. The solution should work locally with a Kubernetes-compatible Docker setup.

## Objectives

Your objective is to design, implement, and deploy a fully functional leaderboard system with the following components:

### 1. Data Structure Design

- **Design an efficient data structure** to store and manage user scores and rankings.
- Ensure the data structure supports quick retrieval of leaderboard positions and scores for a large user base.
- **Document your design choices** and explain how they contribute to scalability and performance.

### 2. Database Schema

- Define a **PostgreSQL schema** to store user information and scores.
- Outline tables, columns, and relationships to support leaderboard functionality.
- **Explain how the schema supports efficient leaderboard operations**, especially with a high volume of users.

### 3. API Development

- Implement a **Node.js API with TypeScript** to interact with the leaderboard system.
- Develop the following API endpoints:

  - **Add a new user with a score**
  - **Update a user’s score**
  - **Retrieve the top N users on the leaderboard**
  - **Retrieve a user’s position on the leaderboard**, along with the 5 users above and below them.

- _(Bonus)_ Integrate **Redis caching** for optimized leaderboard data retrieval, or alternatively, rely on PostgreSQL with future Redis optimization in mind.

### 4. AWS Cloud Architecture (Design Only)

- Design a scalable **AWS cloud architecture** for the leaderboard system, considering components relevant to supporting a high-traffic, scalable service.

### 5. Testing (Bonus)

- Write **unit tests for API endpoints**, considering edge cases and handling a large number of users.
- Provide clear instructions on running tests.

### 6. Deployment

- Deploy the complete system on a **local environment**, including database setup.
- Include a **Dockerfile** to support Kubernetes deployment.

## Submission

Please submit a fully functional leaderboard system, including server and database setup. Include a README with instructions on using the deployed system and running tests. Upload your work to a private GitHub repository.

## Estimated Time

The estimated time for this task is **4 hours**. If you exceed this limit, submit the code in its current state, even if incomplete.

---

## Evaluation Criteria

Your submission will be evaluated based on:

- **Efficiency of data structure and database schema**
- **Performance and accuracy of the API**
- **Completeness and functionality of deployment**
