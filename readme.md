# Vulnerability Report: ogladajanime.pl

> A quick write‑up of the security holes I found on ogladajanime.pl (≈ 80 000 users)  
> by [kindercode1ne](https://github.com/kindercode1ne) · July 2025

---

## 🚀 Project & Scope

- **Target:** ogladajanime.pl
- **Users:** ~80000
- **Goal:** poke around for XSS, SQLi, requests, etc.

---

## 📝 Timeline

- **9 Jul 2025** – Stored XSS in “Wyszukaj anime” (only first `.` sanitized)

---

## 🔎 Findings

### 1. Stored XSS in /search/name

- **What:** Payload executes whenever someone views the search results
- **How:** URL‑encode `<img src="…gif" onerror="…">`, add a random `.` at start
- **Proof:**
  - Live demo:  
    https://ogladajanime.pl/search/name/%3Cscript%3Edocument.body.style.backgroundImage%20%3D%20%22url%28%27https%3A%2F%2Fmedia.tenor.com%2FfktkLkfB4i4AAAAM%2Fspinning-skull-skull.gif%27%29%22%3B%3C%2Fscript%3E
  - Screenshot: ![Deface demo](https://i.imgur.com/psXjU9g.png)

### 2. Fake‑Login Cookie Grabber

- **What:** Crafted a modal that looks like real login, steals creds + cookies to my Vercel webhook
- **Where:** user‑profile “delete account” flow (no email check)
- **Proof:** see payload in [`payloads`](./payloads/payloads.txt)

---

## 📂 Payloads & PoC

All my full payloads are in [`payloads`](./payloads/payloads.txt).

---

⚡ Appendix

    Payload list & links: see payloads.txt
    Room‑creation XSS proof: https://imgur.com/a/sxjHl5B
