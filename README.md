# Cyber Threat Intelligence & Analysis Dashboard 🛡️

A web-based analysis dashboard designed to enable cybersecurity analysts to examine unknown IP addresses in network traffic in real-time. It automatically collects technical data belonging to suspicious IP addresses from a live external API, passes it through a custom risk assessment model, and generates actionable security intelligence.

## 🔗 Live Project
👉 **[Click here to view the live dashboard](https://busra055.github.io/SGM258-Suspicious-IP-Reputation-and-Behavior-Analyzer/)**

---

## ⚠️ CRITICAL: How to Run and Test the Project (Mixed Content Fix)
The free tier of our threat intelligence API (`ip-api.com`) restricts access exclusively to the unencrypted `http://` protocol. Because this repository is hosted on a secure platform like GitHub Pages (`https://`), modern web browsers will block the API call as **Mixed Content** by default.

To ensure the dashboard can fetch live data and execute the risk scoring algorithm successfully, **please follow these brief steps before testing**:

1. Click on the **Site Settings / Shield icon** (🔒 or 📄) located on the left side of your browser's address bar.
2. Click on **Site settings** (Site Ayarları).
3. Find **Insecure content** (Güvenli olmayan içerik) in the permissions list.
4. Change it from *Block (Default)* to **Allow** (İzin Ver).
5. Reload the dashboard page, enter a valid IP address (e.g., `185.213.155.138`), and click **Analyze the IP**.

---

## Custom Risk Scoring Algorithm & Thresholds
Rather than just displaying raw data, the application processes data on the client side to produce custom risk metrics:

*   **Proxy or VPN Usage:** +40 Points
*   **Data Center / Hosting Infrastructure:** +30 Points
*   **Mobile Network Usage:** +15 Points
*   **Missing Reverse DNS Record:** +15 Points

### 📊 Threat Severity Tiers:
*   🔴 **Score ≥ 60 (High Risk):** Very high probability of being malicious or attack infrastructure.
*   🟠 **Score between 25 and 59 (Medium Risk):** Suspicious configuration, requires close monitoring.
*   🟢 **Score < 25 (Low Risk):** Standard, clean consumer internet profile.

---

## 🛡️ Security Implementations
*   **Input Validation:** Strict IPv4 regex structural filter applied before any external network call to prevent application crashes and overhead.
*   **XSS Mitigation:** Utilizes secure text assignment properties (`textContent`) instead of generic HTML insertion to ensure third-party JSON objects cannot execute rogue scripts.
