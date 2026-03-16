# Day-79-100-Days-challenge-in-cybersecurity
## 🗓️ Day 79: Weak Session IDs & Session Management

### 🔍 Overview
Explored the mechanics of **Session Management** and the risks associated with **Weak/Predictable Session IDs** using the DVWA (Damnvulnerable Web Application) environment.

### 💡 Concept: The "Wristband" Analogy
HTTP is a **stateless** protocol; it does not retain user data between requests. To maintain a "logged-in" state, servers issue a **Session ID**.
* **Authentication:** User provides credentials.
* **Authorization:** Server provides a Session ID (The "Wristband").
* **Maintenance:** The browser sends this ID with every subsequent request.

### 🚩 The Vulnerability (DVWA Low Level)
In the lab environment, I observed that Session IDs were generated using simple incremental logic (e.g., `1, 2, 3...`). 

**Impacts observed:**
1.  **Session Hijacking:** Predicting a valid ID to take over an active user session.
2.  **MFA Bypass:** Since the session is already "authenticated," the attacker bypasses the login screen entirely.
3.  **Data Exposure:** Access to PII and sensitive account settings.

### 🛠️ Mitigation
To prevent hijacking, session tokens must be:
* **Long:** To prevent brute-force attacks.
* **Random:** Using cryptographically secure pseudo-random number generators (CSPRNG).
* **Unique:** Never reused or recycled.

---
