Cybersecurity Recommendation & Assessment Generator
A Streamlit app that turns raw findings or consultant comments into AI-driven recommendations, prioritised road-maps, and polished Word / Excel deliverables.

✨ What the app does
Workflow	Input	Output
1. Ask a Question	Free-form text (“How do I mitigate weak third-party risk management?”)	An LLM-generated recommendation with cost band, risk mitigated, and priority.
2. Findings → Recommendations	Excel with a Finding column	Processed_Findings.xlsx (adds Recommendation, Details, Risk, Cost, Priority) + Cybersecurity_Assessment_Report.docx.
3. Consultant Comments → Findings & Recommendations	Excel with Question + Consultant Comment columns	Processed_Consultant_Comments.xlsx + Consultant_Comments_Assessment_Report.docx.
4. Report-only mode	Excel that already contains Finding, Recommendation, Details, Risk Mitigated, Cost, Priority	A single Cybersecurity_Assessment_Report.docx summarising everything.

The Word report automatically includes:

Executive summary (AI-generated)

People / Process / Technology summary

Key findings and actionable recommendations (with cost & priority)

Improvement roadmap (short-/mid-/long-term)

All files are also saved to C:\TEST\AI_recommendations_output\ for audit-trail purposes.

📦 Installation
bash
Copy
Edit
git clone https://github.com/your-org/cybersec-rec-tool.git
cd cybersec-rec-tool

python -m venv .venv
source .venv/bin/activate               # Windows: .venv\Scripts\activate
pip install -r requirements.txt
requirements.txt

shell
Copy
Edit
streamlit>=1.34
pandas>=2.0
openai>=1.0
python-docx>=1.1
xlsxwriter>=3.1      # Excel export engine
🔑 Required environment variable
Variable	Example	Purpose
OPENAI_API_KEY	sk-...	Authenticates the app’s calls to OpenAI.

Set it (PowerShell):

powershell
Copy
Edit
$Env:OPENAI_API_KEY="sk-..."
🚀 Run the app
bash
Copy
Edit
streamlit run app.py
Your browser will open at http://localhost:8501.

📂 Accepted Excel templates
A. Findings file
pgsql
Copy
Edit
| Finding |
|---------|
| Third-party risk management is ad-hoc |
| MFA not enforced on VPN users        |
B. Consultant-comment file
pgsql
Copy
Edit
| Question                         | Consultant Comment                |
|----------------------------------|-----------------------------------|
| Do you have an access review?    | Reviews are done sporadically.    |
| How is data encrypted at rest?   | Only the database layer is using… |
C. Pre-populated findings + recs
pgsql
Copy
Edit
| Finding | Recommendation | Recommendation Details | Risk Mitigated | Cost | Priority |
|---------|---------------|------------------------|----------------|------|----------|
| …       | …             | …                      | High           | Low  | High     |
Tip: keep column names exact (case-sensitive) so the app recognises them.

🛠️ Customisation
Cost bands / risk logic – edit the long system prompt in ask_llm_question().

Save directory – change SAVE_DIR (C:/TEST/AI_recommendations_output).

Model choice – default is gpt-4 for generation, gpt-3.5-turbo for Q&A; tweak in function calls.

Word report layout – modify generate_report().

🔒 Security & privacy
Only the text you provide is sent to OpenAI; no files are uploaded to external servers.

All files are saved locally; ensure you secure C:/TEST/AI_recommendations_output/.

📜 License
MIT — free to use, adapt, and share. Pull requests welcome!
