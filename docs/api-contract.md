# API Contract — Crop Health Early-Warning & Action System

## 1. Purpose

This document defines the API contract between the React frontend
and the FastAPI backend.

The frontend must use the endpoints and response structures defined here.

The backend may change its internal implementation, but the API structure
should remain stable unless the team agrees to change this document.

---

## 2. Base URL

Local development:

http://localhost:8000

All API endpoints are relative to this base URL.

Example:

GET http://localhost:8000/health

---

## 3. API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/health` | Check whether the backend is running |
| POST | `/analyze-farm` | Analyze farm conditions and generate an action plan |
| GET | `/weather` | Retrieve weather information |
| POST | `/predict-disease` | Analyze an uploaded crop/leaf image |

---

# 4. GET /health

## Purpose

Used by the frontend to check whether the FastAPI backend is available.

## Request

No request body.

## Example

```http
GET /health