# Vulnerability Report: ogladajanime.pl

---

## 🚀 Project & Scope

- **Target:** ogladajanime.pl
- **Users:** ~80000

---

## 🔎 Findings

### 1. Reflected XSS in /search/name

- **What:** Payload executes whenever someone views the search results
- **How:** URL‑encode `<img src="…gif" onerror="…">`, add a random `.` at start
- **Proof:**
  - Live demo:  
    https://ogladajanime.pl/search/name/%3Cscript%3Edocument.body.style.backgroundImage%20%3D%20%22url%28%27https%3A%2F%2Fmedia.tenor.com%2FfktkLkfB4i4AAAAM%2Fspinning-skull-skull.gif%27%29%22%3B%3C%2Fscript%3E
  - Screenshot: ![Deface demo](https://i.imgur.com/psXjU9g.png)

### 2. Stored XSS in watch togheter rooms

- **What:** Crafted a modal that looks like real login, steals creds + cookies to my Vercel webhook
- **Where:** watch togheter section
- **Proof:** see payload in [`payloads`](./payloads/payloads.txt)

---

## 📂 Payloads & PoC

All my full payloads are in [`payloads`](./payloads/payloads.txt).

---

⚡ Appendix

    Payload list & links: see payloads.txt
    Room‑creation XSS proof: https://imgur.com/a/sxjHl5B


