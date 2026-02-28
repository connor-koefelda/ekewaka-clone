# Ekewaka
A clone of our AI-powered long-term Financial Planner with personalized insights made for HackIllinois

See our video entry here:
[![Ekewaka Video Entry for HackIllinois 2025](https://img.youtube.com/vi/g4kpwycDYu4/0.jpg)](https://www.youtube.com/watch?v=g4kpwycDYu4)

Ekewaka — AI Financial Planning Assistant
Ekewaka is a conversational financial planning web app that helps users set goals, analyze spending, and visualize budgets with AI-powered insights. It combines an approachable chat UX with real-time analytics to produce actionable, personalized plans.

Built with React and Google Gemini, Ekewaka demonstrates end‑to‑end product thinking: UX, data ingestion, AI prompting, and visualization.

Highlights
AI copilot for finance: Integrated Google Gemini (model: gemini-2.0-flash) for guided, context-aware planning conversations.
Data pipeline: Ingested sample transaction data via the Capital One Nessie API, normalized it, and persisted to localStorage for analysis.
Budget visualization: Converted categorized spend into an interactive recharts pie chart for at-a-glance comparisons.
Fallback UX: When bank data is unavailable, users can input income/expenses/goals via a dedicated settings sidebar.
Modern React stack: React 19, React Router v7, Google OAuth, Bootstrap 5; clean state and context boundaries.
Features
Goal-driven onboarding on the landing page with inline validation.
Conversational analysis backed by a persistent chat session and safe error handling.
Automated categorization of transactions into spending groups using an AI-generated category map.
Interactive charts (Pie + Legend + Tooltip) to visualize spending distribution and compare budgets.
Bank connect flow (mock) to simulate linking an account and toggling use of bank data.
Account settings to store user-entered financial data in localStorage when not using bank data.
Tech Stack
Frontend: React 19, React Router v7, Bootstrap 5, CSS modules
AI: @google/generative-ai (Gemini gemini-2.0-flash)
Charts: recharts
Auth: @react-oauth/google (Google OAuth provider)
Tooling: Create React App, dotenv
Key Files (tour)
src/config/gemini.js: Initializes the Gemini client and a persistent chat session; exposes an async run(prompt) helper.
src/components/context/context.jsx: Context provider that formats AI responses and exposes onSent() to the app.
src/components/LandingPage.js: Captures the user’s goal, fetches sample transactions from Nessie with REACT_APP_NESSIE_API_KEY, stores normalized data in localStorage, and routes to analysis.
src/components/ChatAnalysisPage.js: Orchestrates the conversation, builds categorical spend from AI output, and renders charts with recharts.
src/components/SettingsSidebar.js: Lets users input income/expense targets and goals; values saved in localStorage as "User Settings".
Getting Started
Prerequisites
Node.js 18+ and npm
API key for Google Generative AI (Gemini)
Setup
Install dependencies:
npm install
Create a .env file in the project root with:
REACT_APP_GEMINI_API_KEY=your_gemini_api_key
REACT_APP_NESSIE_API_KEY=your_nessie_api_key (optional; used for sample banking data)
Start the app:
npm start
Open http://localhost:3000.
Notes:

.env is already git-ignored.
If you skip Nessie, you can still use the app by entering data in the settings sidebar.
Scripts
npm start: Run development server
npm test: Run tests in watch mode
npm run build: Build production bundle
npm run eject: Eject CRA config (one-way)
Architecture Notes
AI sessioning: A single long-lived chat is created on app start, enabling context carryover between messages.
State management: Lightweight context for AI messaging; page-level state for chat UI and charts.
Data handling: Normalized purchases/deposits/bills saved to localStorage for fast prototyping; a category map is inferred by AI and used to aggregate spend.
Routing: react-router-dom powers navigation between landing, analysis, about, login, and bank connect.
Security & Keys
Client-only prototype. Do not ship sensitive keys in production.
Store REACT_APP_GEMINI_API_KEY and REACT_APP_NESSIE_API_KEY in environment variables.
Attributions
Bootstrapped with Create React App.
Gemini by Google (@google/generative-ai).
Charts by recharts.
