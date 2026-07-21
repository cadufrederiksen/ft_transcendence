# 📸 Intragram - Community Social Network for 42

*This project is the final project ft_transcendence from 42 Málaga Fundación Telefónica made by [Ateibuzena](https://github.com/Ateibuzena), [Mariano Fernández Rodero](https://github.com/), [Pedro González](https://github.com/petazz) and myself*

![TypeScript](https://img.shields.io/badge/Language-TypeScript-blue) ![React](https://img.shields.io/badge/Frontend-React%2019-lightblue) ![NestJS](https://img.shields.io/badge/Backend-NestJS-red) ![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL%2016-blue) ![Docker](https://img.shields.io/badge/DevOps-Docker--Compose-informational) ![Grafana](https://img.shields.io/badge/Monitoring-Prometheus%20%26%20Grafana-orange)

**Intragram** is a community-oriented social network tailored specifically for the 42 school ecosystem. Built as a full-stack, enterprise-grade web application for **ft_transcendence**, the platform combines remote **42 OAuth** authentication, automated intra profile synchronization, a rich social feed, real-time 1-on-1 messaging, and an asynchronous microservices architecture. All operations are deployed via Docker containers and served under a secure single-host NGINX HTTPS proxy with complete system telemetry.
 

## 📋 Project Goal & Architecture Overview

The main objective of **Intragram** is to construct a production-ready, scalable, multi-service web application that launches with a single command (`docker-compose up --build`):

- **Microservices Architecture**: Decoupled domain services (`auth-service`, `users-service`, `posts-service`, `chat-service`) orchestrated behind a central HTTP API Gateway.
- **Unified Entry Point (NGINX)**: Single-host HTTPS reverse proxy serving the frontend web app, REST API, WebSockets, and observability tooling.
- **Real-Time Synchronicity**: WebSockets (Socket.IO) backed by a Redis adapter to ensure real-time messaging, typing indicators, presence tracking, and notification distribution scale across multiple gateway replicas.
- **Relational Consistency**: PostgreSQL 16 database storing persistent chat logs, relational user profiles, posts, comments, reactions, and friendships.
- **Shared Contracts**: Inter-service DTOs and data models shared seamlessly across frontend and backend packages to avoid contract duplication.

---

## 📚 Core Concepts

- **Microservices & API Gateway**: Centralizing authentication, payload validation, and client route proxying while maintaining isolated domain business logic.
- **Asynchronous WebSockets & Pub/Sub**: Handling real-time client-server communication using Socket.IO, with Redis adapter distribution for horizontal scalability.
- **OAuth 2.0 & JWT Security**: Exchanging 42 authorization codes for user credentials, generating local JWTs, and enforcing route guards.
- **I/O Multiplexing & Observability**: Scraping node telemetry and custom application metrics using Prometheus, rendered visually on Grafana dashboards.
- **Containerization & TLS Termination**: Offloading SSL/TLS security to NGINX while isolating internal service communications inside Docker networks.

---

## ✨ Selected Modules & Point Calculation (Total: 17 / 14 Points)

To exceed the 14-point requirement for *ft_transcendence*, our team successfully implemented **7 Major Modules (14 pts)** and **3 Minor Modules (3 pts)**:

### 🌐 Major Modules (14 Points / 7 Modules)
1. **Framework for Frontend & Backend (2 pts)**: React 19 (Frontend) and NestJS (Backend).
2. **Real-Time Features via WebSockets (2 pts)**: Live 1-on-1 chat, presence, post reactions/comments, and push notifications.
3. **User Interaction & Social System (2 pts)**: Private messaging, user profile viewing, and full friendship management.
4. **Public API Gateway (2 pts)**: Centralized REST API endpoints exposed via Gateway with token validation.
5. **Standard User Management & Auth (2 pts)**: Profile management, avatar sync, online presence tracking, and friends lists.
6. **Backend as Microservices (2 pts)**: Decoupled Gateway, Auth, Users, Posts, and Chat microservices.
7. **Monitoring & Observability System (2 pts)**: Full telemetry with Prometheus metric collection and Grafana visualization.

### 🎨 Minor Modules (3 Points / 3 Modules)
1. **OAuth 2.0 Remote Authentication (1 pt)**: Remote authentication integrated natively with 42 Intra.
2. **Custom Design System (1 pt)**: Reusable React UI component library, custom color palette, typography, and icon set.
3. **Advanced Search & Filtering (1 pt)**: Multi-feed sorting (Recent, Friends, Favorites, Trending, Self) with pagination.

---

## 🛠️ Implemented Features Detail

### 🔐 Auth & User Management
- **42 OAuth Integration**: Automated handshake, callback processing, and user synchronization from 42 Intra payload.
- **Session Management**: JWT stored safely with route guards and seamless logout clearing local state.
- **Profile Synchronization**: Automatic profile updates synced from Intra data into local PostgreSQL records.

### 📰 Social Feed & Interactions
- **Multi-Filter Feed**: View recent posts, posts from accepted friends, bookmarked favorites, or trending content.
- **Post Creation & Reactions**: Rich text post creation, persistent media attachments, likes, and comment threads with live counter updates.
- **Favorites System**: Bookmark and manage saved posts directly from the user interface.

### 💬 Real-Time Chat & Presence
- **1-on-1 Messaging**: Persistent chat history with real-time delivery over WebSockets.
- **Live UX Feedback**: Typing indicators, unread message badges, and real-time online/offline status updates.
- **Redis Multi-replica Adapter**: Multi-node gateway socket synchronization using Redis Pub/Sub.

---

## 🛠️ Tech Stack & Tools

| Layer | Technologies Used |
| :--- | :--- |
| **Frontend** | React 19, TypeScript, Vite, React Router, Tailwind CSS, Component CSS Modules |
| **Backend** | NestJS, TypeScript, TypeORM, Axios (`@nestjs/axios`), JWT, bcrypt, Socket.IO |
| **Database & Cache** | PostgreSQL 16, Redis |
| **DevOps & Proxy** | Docker, Docker Compose, NGINX (HTTPS Reverse Proxy) |
| **Observability** | Prometheus, Grafana |

---
