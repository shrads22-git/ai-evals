# Starter Email-Summary Evaluation Dataset

## Cold-Start Prompt

The following prompt was used to bootstrap the initial dataset:

> Generate 20 evaluation examples for an email summarization benchmark.
>
> For each example include:
>
> - Input email
> - Candidate summary
> - Human label: Good or Bad
> - One sentence explaining why the label was assigned
>
> Requirements:
>
> - Create realistic workplace emails from areas such as engineering, product, marketing, HR, finance, customer support, legal, operations, and sales.
> - Create approximately 10 Good and 10 Bad examples.
> - Good summaries must be factually correct, concise, preserve priorities, and include important actions and deadlines.
> - Bad summaries should contain at least one failure such as missing critical information, hallucinated facts, excessive verbosity, misleading wording, incorrect priorities, or missing action items.
>
> Return everything as a markdown table.

## Starter Dataset
| # | Input Email | Candidate Summary | First-Pass Label | Reason |
|---|---|---|---|---|
| 1 | **Subject: Project Kickoff**<br><br>The analytics redesign project begins Tuesday at 10:00 AM. Engineering, Design, and Product should attend. Maya will circulate the technical plan Monday. Please review it before the meeting and add comments by 5:00 PM Monday. | The analytics redesign kicks off Tuesday at 10:00 AM with Engineering, Design, and Product. Maya will send the technical plan Monday; attendees must review and comment by 5:00 PM Monday. | Good | It accurately captures the meeting, participants, owner, action, and deadline without unnecessary detail. |
| 2 | **Subject: Production Deployment**<br><br>Release 4.8 is scheduled for Thursday at 7:00 PM Pacific. The checkout service will be unavailable for approximately 15 minutes. Support should notify affected enterprise customers by Wednesday noon. Rahul owns the rollback plan. | Release 4.8 will deploy Thursday at 7:00 PM Pacific with an expected 15-minute checkout outage. Support must notify enterprise customers by Wednesday noon, and Rahul owns rollback planning. | Good | It preserves the timing, expected impact, customer action, deadline, and owner. |
| 3 | **Subject: Budget Review**<br><br>Finance approved an additional $80,000 for the Q3 customer-retention campaign. Marketing must submit a revised spending plan by June 18. No additional contractor hiring was approved. | Finance approved $80,000 for the Q3 retention campaign. Marketing must submit the revised spending plan by June 18; contractor hiring was not approved. | Good | It includes the approved amount, purpose, required action, deadline, and hiring restriction. |
| 4 | **Subject: Customer Escalation**<br><br>Northstar Health reported that exports fail for files larger than 500 MB. Engineering identified a timeout issue and plans a hotfix by Friday. Support should update the customer every 24 hours until resolved. | Northstar Health is experiencing export failures above 500 MB because of a timeout issue. Engineering plans a Friday hotfix, and Support must provide daily updates until resolution. | Good | It concisely captures the customer, defect, cause, planned fix, and communication requirement. |
| 5 | **Subject: Interview Training**<br><br>All hiring managers must complete the updated structured-interview training by August 9. The course takes approximately 45 minutes. Managers who completed the pilot version in May do not need to repeat it. | Hiring managers must complete the 45-minute structured-interview training by August 9, except managers who completed the May pilot. | Good | It includes the audience, action, duration, deadline, and exception. |
| 6 | **Subject: Contract Renewal**<br><br>The Acme hosting agreement expires September 30. Legal recommends renewing for one year but wants the liability cap reduced before signature. Procurement must return revised terms by September 10. | Legal recommends a one-year Acme hosting renewal after reducing the liability cap. Procurement must return revised terms by September 10, ahead of the September 30 expiration. | Good | It accurately communicates the recommendation, condition, owner, deadline, and expiration date. |
| 7 | **Subject: Security Patch**<br><br>A critical authentication vulnerability affects mobile app versions earlier than 6.2. The patch is ready. Mobile Engineering must submit version 6.2 to both app stores today, and Customer Success should notify regulated customers after approval. | A critical authentication vulnerability affects versions before 6.2. Mobile Engineering must submit the patched release today; Customer Success will notify regulated customers once it is approved. | Good | It includes the severity, affected versions, immediate action, owner, and follow-up communication. |
| 8 | **Subject: Office Closure**<br><br>The Austin office will close Friday because of scheduled electrical maintenance. Employees should work remotely. The facilities help desk remains available for urgent access requests. | The Austin office will be closed Friday for electrical maintenance. Employees should work remotely, with Facilities available for urgent access needs. | Good | It clearly states the closure, reason, employee action, and support option. |
| 9 | **Subject: Sales Forecast**<br><br>The Q2 forecast increased from $4.2 million to $4.6 million after two enterprise deals moved forward. The forecast still depends on the Apex contract closing by June 25. Sales Operations will update the CRM by tomorrow morning. | The Q2 forecast rose to $4.6 million from $4.2 million, driven by two enterprise deals. It depends on Apex closing by June 25, and Sales Operations will update the CRM tomorrow morning. | Good | It preserves the forecast change, cause, risk, deadline, and next action. |
| 10 | **Subject: Benefits Enrollment**<br><br>Open enrollment ends November 15 at 11:59 PM Pacific. Employees who take no action will retain their current medical plan, but FSA elections will not carry over. HR will hold an information session Wednesday at 2:00 PM. | Benefits enrollment closes November 15 at 11:59 PM Pacific. Medical coverage carries over automatically, but employees must actively renew FSA elections. HR will host a Wednesday 2:00 PM information session. | Good | It includes the deadline, default outcome, important FSA exception, and help session. |
| 11 | **Subject: Production Deployment**<br><br>Release 4.8 is scheduled for Thursday at 7:00 PM Pacific. The checkout service will be unavailable for approximately 15 minutes. Support should notify affected enterprise customers by Wednesday noon. Rahul owns the rollback plan. | Release 4.8 is coming soon, and the team is preparing for a smooth deployment. | Bad | It omits the exact deployment time, outage, customer-notification deadline, and rollback owner. |
| 12 | **Subject: Budget Review**<br><br>Finance approved an additional $80,000 for the Q3 customer-retention campaign. Marketing must submit a revised spending plan by June 18. No additional contractor hiring was approved. | Finance approved $100,000 and authorized Marketing to hire two contractors for the campaign. | Bad | It hallucinates both the amount and contractor approval, directly contradicting the email. |
| 13 | **Subject: Customer Escalation**<br><br>Northstar Health reported that exports fail for files larger than 500 MB. Engineering identified a timeout issue and plans a hotfix by Friday. Support should update the customer every 24 hours until resolved. | Northstar Health has encountered an unfortunate technical situation involving certain export activities, and various internal teams are thoughtfully investigating how best to move toward a satisfactory resolution while maintaining communication. | Bad | It is excessively verbose and vague and omits the 500 MB threshold, Friday hotfix, and daily updates. |
| 14 | **Subject: Interview Training**<br><br>All hiring managers must complete the updated structured-interview training by August 9. The course takes approximately 45 minutes. Managers who completed the pilot version in May do not need to repeat it. | All employees must complete a two-hour interview course by August 1. | Bad | It changes the audience, duration, and deadline and removes the pilot exception. |
| 15 | **Subject: Contract Renewal**<br><br>The Acme hosting agreement expires September 30. Legal recommends renewing for one year but wants the liability cap reduced before signature. Procurement must return revised terms by September 10. | Acme’s contract should be renewed immediately because Legal has fully approved the current terms. | Bad | It falsely states that current terms were approved and omits the required liability change and Procurement deadline. |
| 16 | **Subject: Security Patch**<br><br>A critical authentication vulnerability affects mobile app versions earlier than 6.2. The patch is ready. Mobile Engineering must submit version 6.2 to both app stores today, and Customer Success should notify regulated customers after approval. | Customer Success should notify customers about a minor mobile issue sometime next week. | Bad | It understates a critical vulnerability and changes both the action sequence and timing. |
| 17 | **Subject: Office Closure**<br><br>The Austin office will close Friday because of scheduled electrical maintenance. Employees should work remotely. The facilities help desk remains available for urgent access requests. | The Austin office is permanently closing, and employees are being transferred to Dallas. | Bad | It invents a permanent closure and employee transfers that are not in the source email. |
| 18 | **Subject: Sales Forecast**<br><br>The Q2 forecast increased from $4.2 million to $4.6 million after two enterprise deals moved forward. The forecast still depends on the Apex contract closing by June 25. Sales Operations will update the CRM by tomorrow morning. | The sales forecast improved significantly, so the quarter is now guaranteed to exceed target. | Bad | It presents a conditional forecast as guaranteed and omits the Apex dependency and CRM action. |
| 19 | **Subject: Benefits Enrollment**<br><br>Open enrollment ends November 15 at 11:59 PM Pacific. Employees who take no action will retain their current medical plan, but FSA elections will not carry over. HR will hold an information session Wednesday at 2:00 PM. | Employees do not need to take any action because all benefits, including FSAs, will renew automatically. | Bad | It incorrectly says FSA elections carry over and could cause employees to lose an intended benefit. |
| 20 | **Subject: Data Migration**<br><br>The customer-data migration begins Saturday at 9:00 PM UTC and should finish within six hours. During that period, reporting dashboards will be read-only. Analytics must validate record counts by noon Sunday and report discrepancies in the migration channel. | The migration happens this weekend and may temporarily affect some systems. | Bad | It omits the exact timing, duration, dashboard limitation, validation owner, deadline, and reporting action. |

## Human Curation Notes

I manually reviewed the generated examples rather than treating the LLM-generated labels as ground truth.

During review, I checked whether each summary:

- Preserved critical facts from the source email.
- Included actions, owners, dependencies, and deadlines when present.
- Maintained the original severity and business priority.
- Avoided unsupported or hallucinated claims.
- Used concise wording appropriate for an executive reader.
- Avoided vague language that could cause a reader to make an incorrect decision.

The current dataset is a starter set rather than a fully validated golden dataset. It will require further review, additional edge cases, multiple human annotators, and agreement measurement before being used as trusted evaluation ground truth.

## Golden-Set Labeling Criteria

### Good Summary

A summary is labeled **Good** when it:

1. Accurately represents the source email without changing its meaning.
2. Includes all decision-critical facts.
3. Includes important actions, owners, deadlines, dependencies, and exceptions.
4. Preserves the urgency and priority of the original message.
5. Uses concise, direct language appropriate for a busy executive.
6. Does not introduce unsupported information.
7. Avoids unnecessary background, repetition, pleasantries, or commentary.

A summary may omit minor supporting details when those details do not affect a decision or required action.

### Bad Summary

A summary is labeled **Bad** when it contains one or more material failures:

1. Omits a critical action, deadline, owner, risk, dependency, or exception.
2. Introduces information that is not supported by the source email.
3. Changes factual details such as dates, amounts, scope, severity, or status.
4. Presents a conditional outcome as certain.
5. Changes the priority or intent of the original message.
6. Is so verbose or vague that the key information is difficult to identify.
7. Emphasizes minor details while hiding the most important business information.

A summary should be labeled Bad when its failure could cause a reader to make an incorrect decision or miss a required action.