---
layout: post
title: Pyre
search_exclude: true
permalink: /pyre
---

# Pyre Project Experience

## Experience Building Pyre

*Jun 10, 2025 • 13 min read*

---

# Pyre: AI-Powered Wildfire Prediction System - A Journey Through Real-World Problem Solving

## Executive Summary
Pyre is an AI-powered wildfire monitoring platform designed to enhance emergency preparedness and real-time response. It integrates environmental data, user-reported hazards, and live fire incidents into a seamless single-page application tailored for emergency scenarios. Throughout this project, I led engineering efforts, managed team dynamics, and pushed for iterative improvements based on both user feedback and field testing.

---

## Project Vision & Impact
Wildfires are fast, brutal, and often under-monitored. Pyre closes the gap between scattered environmental data and actionable insights. It empowers residents, firefighters, and local governments to make critical decisions during wildfire threats with a clear, unified platform.

---

## Core Challenges & Solutions

### 1. **Unclear Project Value Proposition**
**Problem:** Stakeholders weren’t sold on our pitch — too much tech jargon, not enough real-world relevance.

**Why:** We buried the lede. Instead of showing how Pyre could save lives, we showcased technical features without clear user benefit.

**Fix:**
- Led with wildfire casualty stats and the problem statement.
- Developed user personas for first responders, local officials, and evacuees.
- Walked through realistic emergency workflows.
- Added demo quotes from San Diego fire department contacts who beta-tested the prototype.

**Result:** Turned confusion into support — got buy-in from emergency planners and local organizations.

---

### 2. **Scattered User Experience**
**Problem:** Tools were fragmented across multiple pages — a nightmare when seconds matter.

**Finding:** Testing showed it took users ~45 seconds to access evacuation info. That’s a death sentence in a fast-moving fire.

**Fix:**
- Merged everything into a unified single-page app.
- Added modals for fast switching between tools.
- Introduced a high-contrast emergency mode and keyboard navigation.
- Slashed task completion time to 8 seconds via design overhauls and user testing.

**Impact:** 75% more engagement, vastly reduced abandonment under stress.

---

### 3. **Missing AI Assistant Functionality**
**Problem:** Users struggled with tool navigation and didn't know where to start during emergencies.

**What We Built Instead of ML:**
- I integrated Google's Gemini AI using the Gemini API key I registered and secured through service configuration.
- Created an in-app chatbot using modal architecture so it could live on every screen.
- Trained the assistant with Pyre’s feature set and basic fire safety protocols.

**Functionality:**
- Users can ask where to evacuate, how to report a fire, or get a route in real-time.
- Gemini handles natural language requests and guides them to the right tool instantly.

**Why It Worked:**
- Replaced traditional machine learning models with a much more adaptable assistant.
- 90%+ of testers preferred the AI assistant for navigation over traditional menus.

---

### 4. **Team Coordination Woes**
**Problem:** A six-person team, two subsystems (fire + earthquake), one tangled mess of integrations.

**Symptoms:** Merge conflicts, duplicated features, API miscommunication — all the classics.

**My Fix:**
- Co-led agile planning with teammate Pranav.
- Implemented strict API documentation protocols.
- Added weekly syncs between fire and quake teams.
- Built integration testing pipelines for all REST endpoints.

**Result:** Integration bugs dropped 80%. Dev speed jumped 40%.

---

### 5. **Performance & Scalability**
**Problem:** Our first test deployment loaded like it was stuck in molasses. 30+ seconds to see anything useful.

**Analysis:** Large datasets, excessive API calls, zero caching. Basically, rookie mistakes.

**My Fixes:**
- Implemented lazy loading + pagination.
- Cached Gemini API responses and weather data to avoid redundant requests.
- Preprocessed incoming incident feeds before frontend rendering.
- Set up CDN distribution for static content.

**Result:** Load time dropped 95%. We hit 99.9% uptime during simulated emergency testing.

---

### 6. **Community Reporting Wasn’t Trusted**
**Problem:** How do you crowdsource fire hazard reports without letting trolls or panicked misreports hijack the system?

**Solution:**
- Designed a robust reporting tool with field validation, geotagging, and image uploads.
- Built an admin dashboard for verifying incoming reports.
- Reports flow through: `Pending → Verified → Resolved`.

**Tech Stack:** Flask-RESTful APIs with role-based permissions and rate limiting. Geo-indexed PostgreSQL database for spatial queries.

**Impact:** Emergency team feedback showed 40% faster hazard response compared to traditional call-in reports.

---

### 7. **Emergency Communication Delays**
**Problem:** If people don’t get the message in time, everything else we built is meaningless.

**Solution:**
- Integrated Twilio API for automated voice alerts.
- Developed location-based alert logic — only notify those at real risk.
- Scaled to simulate high-load emergencies, with 95% of calls completed within 3 minutes.

**Future-Ready:** Framework supports SMS, push notifications, and email — ready to scale with user needs.

---

## Leadership & Deployment

### Engineering Lead
- Spearheaded fire-side subsystem development.
- Oversaw Gemini AI integration, frontend redesign, and system unification.

### Agile Workflow Setup
- Ran 2-week sprints with velocity tracking.
- Maintained GitHub Project boards and ran retrospectives.
- Authored detailed user stories from multiple stakeholder perspectives.

### Deployment & DevOps
- Productionized Flask backend using Gunicorn + Nginx.
- Optimized PostgreSQL with indexing and connection pooling.
- Configured logging and monitoring using Grafana + Prometheus.
- Seamlessly deployed under Open Coding Society’s platform umbrella.

---

## Skills Highlighted
- **Frontend:** React.js, ES6, modal architecture, accessibility  
- **Backend:** Flask, REST API design, authentication, rate limiting  
- **DevOps:** Gunicorn, Nginx, CDN, caching, uptime monitoring  
- **Integration:** Gemini AI, Twilio, Google Maps, NASA FIRMS, San Diego Police feeds  
- **Teamwork:** Agile leadership, stakeholder feedback, sprint management  
- **UX/UI:** Single-page architecture, chatbot design, task optimization  

---

## Final Reflection
Pyre wasn’t just a project — it was a stress test of what I could build, lead, and fix under pressure. While others went the traditional machine learning route, I doubled down on user-centric design and practical AI integration. We made an intuitive, production-ready tool that’s already drawing real-world interest.

In a crisis, people don’t need more dashboards. They need clarity. Pyre delivers that — fast, clean, and backed by engineering that can hold under fire.

