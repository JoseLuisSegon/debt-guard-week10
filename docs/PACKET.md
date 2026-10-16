# PACKET — WEEK 10: DEBT GUARDRAIL & INSTALLMENT CHECKER
**Student:** Jose Luis Segon (Technologist)  
**Project:** Pre-Purchase Installment & Debt Guardrail (Honoring Team Blueprint)  

### 1. Problem in Your Words
Mexican shoppers face an aggressive wave of uncoordinated BNPL (Kueski, Aplazo, Mercado Crédito) and credit card installments. Because no open banking API unifies these debts, consumers stack monthly obligations blindly, leading to severe over-indebtedness.

### 2. Exact User
Doña Mari or young urban professionals in Mexico buying apparel or electronics via social commerce, tempted by "pay in 5 easy installments" without realizing how it impacts next month's fixed cash flow.

### 3. Success Definition ("Before the module closes, X works")
A deployed web interface where a user inputs a prospective purchase price, number of installments, and their current monthly fixed income/debts; the system deterministically calculates the new debt-to-income ratio and outputs an honest **"GREEN LIGHT"**, **"CAUTION"**, or **"STOP: UNSTABLE DEBT LOAD"** verdict with a clear payment schedule timeline.

### 4. Image-Generated Mockup Description
A clean mobile-first web dashboard featuring a dark mode financial safety card, input fields for purchase cost and installments, a visual timeline bar showing overlapping monthly payments, and a prominent color-coded decision badge.

### 5. Mermaid Flow Diagram
```mermaid
flowchart TD
    A[User Inputs Purchase & Installment Plan] --> B[Local Financial Ledger / Existing Debts]
    B --> C[Deterministic Constraint Engine]
    C --> D{Debt-to-Income > Safe Threshold?}
    D -- Yes --> E[Issue STOP / CAUTION Verdict & Show Overlapping Timeline]
    D -- No --> F[Issue GREEN LIGHT & Verified Schedule]
6. Benchmark Line
Global Best Solution: Klarna Insights / Snoop (UK).
Local Adaptation / Difference: Snoop relies on open banking APIs which don't exist universally for Mexican BNPL apps. Our tool uses a local user-fed deterministic ledger with zero bank API integrations.
7. Long-View Paragraph (Light Charter)
If this slice works, it evolves over 3 years into an independent, non-predatory consumer financial co-pilot across all Mexican digital channels. By keeping user data strictly local and client-side, it restores purchasing agency against manipulative sell-side algorithms.
8. Scope Cut (What We Are NOT Building)
No automated bank login.
No autonomous checkout or direct wallet execution.
No lender affiliate commissions.
9. Architecture & Stack Table
Layer	Technology
Frontend	React, Tailwind CSS, Lucide Icons (via Next.js / v0)
Logic / Engine	Client-side JavaScript (Deterministic math for DTI & installment timelines)
Hosting	Vercel (Free tier, instant deployments)
Security	Zero personal financial data stored in remote servers (local state only)
10. Test Plan
Input a safe purchase ($500 MXN over 2 months with $10,000 income) -> Expect Green Light.
Input an aggressive purchase ($5,000 MXN over 6 installments with $8,000 income and existing debts) -> Expect Red Light (Stop Verdict).
Verify that all calculations match the deterministic ledger.
