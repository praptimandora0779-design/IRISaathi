# IRISaathi — SIH PS 26038 Frontend

Professional frontend prototype for **Explainable AI for Diabetic Retinopathy Screening in Rural India**.

## Stack
- HTML5
- CSS3
- Vanilla JavaScript
- Browser LocalStorage for demo registration/login
- No framework or build step required

## Authentication flow
1. Open the portal.
2. Select **Yes, I am registered** or **No, create my account**.
3. Registration collects:
   - Name
   - Age
   - Gender
   - Diabetes duration
   - Password
4. A reusable **Profile ID** is generated.
5. On every login, the user enters:
   - Profile ID
   - Password
   - **Patient ID** for the current screening record
6. Patient ID is intentionally separate from the profile and can change for a new screening record.

### Demo login
- Profile ID: `RA-10482`
- Password: `1234`
- Patient ID: `PID-2026-8941`

## Prototype modules
- Overview dashboard
- Fundus image upload / drag-and-drop
- Image quality gate UI (DeepDRiD)
- CLAHE + normalization stage UI
- Retinal structure analysis UI (DRIVE / IDRiD)
- Lesion evidence UI (MA / EX / HE / SE)
- DR grading UI (APTOS, Grade 0–4)
- Grad-CAM + lesion evidence UI
- Confidence calibration display
- Automated clinical report
- Ophthalmologist review workflow
- Simulink-style district resource simulation controls

## Real AI integration
The current frontend uses demo/mock inference so it can be demonstrated without GPU models. Replace the pipeline simulation in `app.js` with API calls to a Python/FastAPI or MATLAB service.

Recommended production architecture:

Browser → FastAPI gateway → Python AI services / MATLAB Engine → Simulink resource model → JSON → Browser

Suggested endpoints:
- `POST /api/screening/quality`
- `POST /api/screening/enhance`
- `POST /api/screening/structures`
- `POST /api/screening/lesions`
- `POST /api/screening/grade`
- `POST /api/screening/explain`
- `POST /api/screening/report`
- `POST /api/simulation/run`

## Run
Open `index.html` with VS Code Live Server, or simply open it in a browser.

## Important medical note
This is a research/hackathon prototype. It must not be presented as a standalone clinical diagnosis system until the models are validated and clinically reviewed.

## V3 updates
- Light professional clinical theme with larger typography.
- Patient Registry page for previous patient details.
- Total patients till now counter based on unique registered profiles in browser storage.
- Screening history records with patient ID, scan ID, date, eye and result.
- Patient ID remains record-specific and can change without creating a new profile.
- Demo history is seeded from the supplied SIH screening report case.
