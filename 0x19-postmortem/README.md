Outage Postmortem: The Great "404 Frenzy"
Issue Summary
Duration:
Start: June 20, 2024, 14:15 UTC
End: June 20, 2024, 16:45 UTC

Impact:
Our primary web application was significantly impaired during this period. Users experienced an unusual surge in 404 (Not Found) errors when attempting to access various parts of the website. Approximately 60% of our users were affected, leading to a substantial drop in user activity and a spike in support tickets.

Root Cause:
A misconfigured deployment script led to the accidental deletion of a crucial directory on our web server.

Timeline
14:15 UTC - Issue detected via monitoring alert indicating a sudden spike in 404 errors.
14:17 UTC - Support team started receiving user complaints about pages not loading.
14:20 UTC - Initial investigation by the on-call engineer pointed towards a potential problem with the web server configuration.
14:30 UTC - On-call engineer restarted the web server, assuming a temporary glitch.
14:35 UTC - Issue persisted. The engineering team was notified and began a deeper investigation.
14:45 UTC - Misleading assumption: Network issues were suspected, and network diagnostics were performed.
15:00 UTC - Network team ruled out any network-related problems.
15:15 UTC - Focus shifted to recent deployments. Deployment logs were reviewed.
15:30 UTC - Misleading investigation: Assumed a rollback of the latest deployment might resolve the issue.
15:45 UTC - Rollback did not resolve the issue. Escalated to the senior engineering team.
16:00 UTC - Detailed file system inspection revealed the accidental deletion of the "/public_html/assets" directory.
16:15 UTC - Emergency meeting with DevOps and senior engineers to discuss a recovery plan.
16:30 UTC - Restoration of the deleted directory from the latest backup.
16:45 UTC - All services restored, and normal operations resumed.
Root Cause and Resolution
Root Cause:
The root cause of the outage was a misconfigured deployment script. During a routine update, the script included an erroneous command that inadvertently deleted the "/public_html/assets" directory, which contained critical static resources such as images, CSS, and JavaScript files. Without these assets, the web pages could not be properly rendered, resulting in the 404 errors.

Resolution:
Once identified, the resolution involved restoring the deleted directory from the most recent backup. The directory was successfully restored at 16:30 UTC, and full functionality was confirmed by 16:45 UTC. The deployment script was immediately corrected to prevent recurrence.

Corrective and Preventative Measures
Improvements/Fixes:

Implement additional checks in deployment scripts to prevent accidental deletions.
Enhance monitoring to detect and alert on unusual patterns of 404 errors sooner.
Conduct regular audits of deployment scripts and processes.
Task List:

Patch Deployment Script: Update the deployment script to include safeguards against directory deletions.
Add Monitoring: Implement a monitoring system to track the presence and integrity of critical directories and files.
Backup Verification: Regularly verify backups to ensure they can be restored quickly and accurately.
Staff Training: Conduct a training session for engineers on best practices for deployment and script management.
Deploy Staging Environment: Create a more robust staging environment to catch issues before they reach production.
Incident Review: Schedule a follow-up meeting to review the incident and ensure all corrective actions have been implemented.
A Little Humor to Lighten the Mood

"When you misplace your keys, you panic. When you misplace a directory, the whole company panics."

By addressing these issues, we aim to prevent such outages in the future and ensure a more reliable experience for our users. Thank you for your understanding and continued support.
