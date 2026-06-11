# nelo-ops-triage
What the tool is: Triage Classifier - Auto-tag & prioritize incoming tickets using category + merchant GMV + SLA age
Ticket Scoring formula: 
Each ticket gets a 0–100 score from four components: 
-	priority (0–30); 
-	category risk (0–30 — weights derived from observed breach rates, payment_issue gets the maximum because it breaches at ~31% vs. 4–8% for all other categories); 
-	merchant GMV (0–25, scored in the same size bands used in the diagnosis — >750K=25, 500–750K=20, 250–500K=15, 100–250K=8, <100K=3 — capped so a single large merchant cannot bury the rest of the queue);
-	SLA aging (0–15, rising as a ticket approaches and passes its threshold so nothing rots silently). 
Tiers: P0 ≥75 (escalate now), P1 ≥55, P2 ≥35, P3 below. Every weight and threshold is shown in “Scoring engine settings” panel, because the weights are calibrated assumptions rather than ground truth — ops can recalibrate without touching code.
