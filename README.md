🌾 Farm Copilot

A full-stack platform built to help farmers make smarter, faster decisions — combining AI-powered crop diagnosis, multilingual advisory, treatment recommendations, weather forecasting, vendor/equipment marketplace, and IoT-based soil health monitoring, all in one place.

🚀 Features
AI Crop Advisory (11 Languages) — Farmers can upload a photo of their crop or ask questions directly, and get AI-generated advisory support in 11 different languages.
Disease Detection & Treatment — The AI detects crop diseases from photos and recommends appropriate treatment.
Weather Forecasting — Real-time and forecasted weather data to help plan sowing, irrigation, and harvesting.
Nearby Shops & Vendors — Locates nearby agri-shops, fertilizer dealers, and equipment vendors on a map, with ratings and distance.
Orders — Farmers can order necessary agricultural products directly through the platform.
Equipment Rental — A marketplace where farmers can rent equipment and machinery from vendors.
Soil Test (NPK Hardware Integration) — Connects to a physical NPK meter (via USB, serial baud connection) to read soil nutrient levels — Nitrogen, Phosphorus, Potassium, and more — or lets users enter values manually. Saved tests build a farm's soil profile over time for AI-driven trend analysis.
My Farms — Manage multiple farms, each with its own location and crop details.
🛠️ Tech Stack

Frontend

React (Vite)
TypeScript
Tailwind CSS
ESLint

Backend

Node.js / Express

Hardware

NPK soil nutrient sensor/meter (serial/USB connection)

Integrations

Maps (for nearby vendors/shops)
Weather API
AI/ML models for crop disease detection & multilingual advisory
📁 Project Structure
├── backend/         # API and server logic
├── frontend/         # React + Vite client
│   ├── public/
│   ├── src/
│   └── ...
├── Claude outputs/   # Generated docs/assets
├── guide.md
└── copilot.md
⚙️ Getting Started
Prerequisites
Node.js (v18+ recommended)
npm
Installation
Clone the repository
bash
   git clone https://github.com/Anubhabcysec/<repo-name>.git
   cd <repo-name>
Install frontend dependencies
bash
   cd frontend
   npm install
   npm run dev
Install backend dependencies
bash
   cd backend
   npm install
   npm start
🧑‍🌾 How It Works
A farmer adds their farm details (location, crop) under My Farms.
Under Advisory, they can upload a crop photo or ask a question in their preferred language (11 supported) and get AI-generated guidance.
If a disease is detected, the Treatment section provides recommended treatment steps.
Nearby agri-shops and vendors are shown on a map with ratings and distance, so farmers know where to buy what they need.
Needed products can be ordered directly through Orders; equipment can be rented via Equipment.
Weather gives forecasts to support irrigation and harvesting decisions.
Under Soil Test, farmers connect an NPK meter (or enter values manually) to analyze soil nutrient levels. Saved results build a soil profile per farm, feeding future AI trend analysis.

