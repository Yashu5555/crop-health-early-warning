# Crop Health Early-Warning & Action System

## 1. Purpose

The system is an AI-powered crop-health early-warning and decision-support web application.

It combines:

- Crop information
- Crop growth stage
- Soil information
- Weather conditions
- Disease/image analysis

to identify potential crop-health risks and provide an explainable action plan.

The system should answer:

> What is likely to go wrong, why might it happen, and what should the farmer do now?

---

## 2. MVP Architecture

The MVP follows a simple modular architecture:

React Frontend
        ↓
FastAPI Backend
        ↓
Analysis / Recommendation Layer
        ↓
Weather API + Risk Engine + Disease Model
        ↓
Action Plan
        ↓
React Dashboard

---

## 3. Frontend

Technology:

- React
- Vite
- Tailwind CSS

Responsibilities:

- Display landing page
- Collect farm information
- Send analysis request to backend
- Display weather information
- Display crop-health risks
- Display disease analysis
- Display fertilizer/4R recommendations
- Display action plan
- Handle loading and error states

The frontend should not contain core agricultural decision logic.

---

## 4. Backend

Technology:

- Python
- FastAPI

Responsibilities:

- Receive requests from frontend
- Validate input
- Call weather service
- Call disease prediction module
- Run risk analysis
- Run recommendation engine
- Return structured JSON responses

The backend acts as the main orchestration layer.

---

## 5. Disease Detection Module

The MVP will use a pretrained crop-disease model rather than training a new model.

Input:

- Crop/leaf image

Output:

- Predicted disease/class
- Confidence score
- Basic interpretation
- Next recommended action

If confidence is too low, the system should return an inconclusive result rather than pretending the prediction is certain.

---

## 6. Risk Engine

The risk engine combines available signals such as:

- Crop type
- Crop growth stage
- Weather
- Temperature
- Humidity
- Recent rainfall
- Soil information
- Disease indicators

The MVP risk engine may initially use transparent rules and scoring rather than a trained risk model.

Risk output should be expressed as:

- Low
- Moderate
- High

Risk scores and thresholds used in the MVP are demo-level indicators unless validated against authoritative agricultural guidance.

---

## 7. Recommendation Engine

The recommendation engine converts detected risks into actions.

The fertilizer/input component follows the 4R principle:

- Right Source
- Right Rate
- Right Time
- Right Place

Recommendations should explain:

1. What action is suggested
2. Why it is suggested
3. When it should be considered

The MVP should avoid presenting unvalidated recommendations as definitive agronomic prescriptions.

---

## 8. Weather Service

The backend will retrieve weather information from an external weather API.

Weather data may contribute to:

- Disease risk
- Irrigation guidance
- Weather alerts
- Crop-health analysis

The frontend should receive normalized weather data from our backend rather than calling the weather provider directly.

---

## 9. Data Flow

1. Farmer enters farm information.
2. Frontend sends farm data to FastAPI.
3. Backend validates the request.
4. Backend retrieves relevant weather data.
5. Risk engine evaluates available conditions.
6. Recommendation engine generates an action plan.
7. Backend returns structured JSON.
8. Frontend displays the analysis.

For disease checking:

1. Farmer uploads an image.
2. Frontend sends the image to FastAPI.
3. Backend passes the image to the disease model.
4. Model returns prediction and confidence.
5. Backend converts the result into a user-friendly response.
6. Frontend displays the result and next action.

---

## 10. MVP Scope

The MVP will support:

- One farmer/farm session
- Basic farm setup
- Selected crops
- Weather information
- Crop-health risk analysis
- Disease image checking
- Basic nutrient/4R guidance
- Irrigation guidance
- Action plan

The MVP will NOT initially include:

- User authentication
- Payments
- Social features
- Voice assistant
- Native mobile application
- Custom ML training
- Complex database architecture
- Large-scale multilingual support
- Advanced admin system

---

## 11. Design Principle

Build the smallest working system first.

Every module should be:

- Simple
- Testable
- Replaceable
- Independently understandable

AI agents should not introduce unnecessary frameworks, services, or architecture without approval.