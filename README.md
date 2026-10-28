# FestPass - Docker & Container Security (CA-2 Assessment)

## 1. Candidate & Environment Details
* **Student Name:** Arth Srivastava
* **Registration Number (REGNO):** 202401100200089
* **Port:** 8089 (`80` + last 2 digits `89`)
* **Docker Hub Username:** blazearth
* **Docker Hub Repository Link:** [https://hub.docker.com/r/blazearth/fest-backend](https://hub.docker.com/r/blazearth/fest-backend)
* **Backend Image Tag:** `blazearth/fest-backend:1.0.0`
* **Digest of 1.0.0:** `sha256:cbe5da77aba87305653af6bc6428a7b641052beca2722b9e44aa5d112595e910` (Manifest: `sha256:a74016da24e9acb1c1ff717bb2a5f8b507021495bcead3074e8cd7035808ee8f`)

---

## 2. AI Tools Used
* **AI Tool:** Antigravity IDE (Gemini 3.8)
* **Usage Declaration:** 
  - Assistance with multi-stage Dockerfile design (pinning base images, implementing non-root user `appuser`).
  - Structuring `compose.yaml` with dedicated frontend and backend bridge networks and volume persistence.
  - Interpreting Trivy vulnerability scanning reports and optimizing library versions.
  - Generating and validating Cosign cryptographic digital signatures and key verification pipelines.

---

## 3. Vulnerability & Image Size Remediation Table (Stage 3.3)

| Metric / Severity | Before Fix (`fest-backend:0.1`) | After Fix (`fest-backend:0.2` / `1.0.0`) |
| :--- | :--- | :--- |
| **Base Image** | `python:3.9` (Debian 13.1) | `python:3.12-alpine` (Alpine 3.24.3) |
| **Execution User** | `root` (UID 0) | `appuser` (Non-root, UID 100) |
| **CRITICAL** | 234 | **0** |
| **HIGH** | 2,243 | **0** |
| **MEDIUM** | 7,516 | **0** |
| **LOW** | 3,206 | **0** |
| **Total Findings** | 13,199 | **0 (Clean)** |
| **Image Size** | **1.61 GB** | **106 MB** (~93.4% reduction, 26.2 MB compressed) |

---

## 4. Uncompleted Steps
* **None**: All stages (Stage 1 through Stage 5) were fully completed and verified according to the assessment specifications.

---

## 5. Security & Verification Checklist
- [x] Every terminal screenshot includes the custom prompt `[202401100200089] \w $`.
- [x] All evidence files reside in the `screenshots/` directory.
- [x] `cosign.key` and `.env` are strictly excluded from git tracking via `.gitignore`.
- [x] Only `cosign.pub` is committed to the repository.
- [x] Version `1.0.0` is cryptographically signed via digest, and unsigned release `1.0.1` is rejected by `cosign verify`.

---

## 6. Project Structure
```
202401100200089-docker-assessment/
├── README.md
├── compose.yaml
├── .env.example
├── .gitignore
├── cosign.pub
├── backend/
│   ├── app.py
│   ├── requirements.txt
│   ├── Dockerfile
│   └── .dockerignore
├── frontend/
│   ├── index.html
│   └── nginx.conf
├── reports/
│   ├── trivy-before.txt
│   └── trivy-after.txt
└── screenshots/
    ├── S1-2.png
    ├── S1-3.png
    ├── S2-2.png
    ├── S2-3.png
    ├── S2-4.png
    ├── S3-1.png
    ├── S3-3.png
    ├── S4-1.png
    ├── S4-2.png
    ├── S4-3.png
    ├── S5-1.png
    ├── S5-2.png
    ├── S5-3.png
    ├── S5-2_S5-3.png
    └── S5-4.png
```
