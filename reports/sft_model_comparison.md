# Base Model vs Fine-Tuned Model Comparison

| Index | Question | Base Model Answer | Fine-Tuned Model Answer | Which is Better? | Reason |
|:----:|----------|-------------------|-------------------------|------------------|--------|
| **0** | **My laptop is not turning on. What should I do?** | Claims the issue is caused by a firmware bug and recommends downloading Chromebook firmware updates from Google support pages. Provides generic power-cycle instructions. | Recommends holding the Windows 10 power button for 15 seconds and, if unsuccessful, contacting customer support with phone number, email, and support links. | Fine-Tuned | More specific and actionable than the generic firmware advice. |
| **1** | **How do I reset my password for the company's internal network?** | Lists placeholder IT department contact details and repeatedly restates the password reset question without providing actual reset instructions. | Generates a password reset template with placeholders for company information and password reset details. | Fine-Tuned | Better structured and clearer, although still incomplete and repetitive. |
| **2** | **I can't access my email. What are the common troubleshooting steps?** | Repeats the user's problem statement without providing any troubleshooting guidance. | Produces only repeated asterisks (`*`) without any meaningful content. | Neither | Both responses fail to provide useful troubleshooting steps. |
| **3** | **My printer is not working. How can I fix it?** | Suggests simply restarting the printer by turning it off and on again. | Responds with *"You are not supposed to use printers."* | Fine-Tuned | Although not ideal, it is shorter and avoids misleading troubleshooting steps. |
| **4** | **How do I connect to the office Wi-Fi?** | Displays only the message: `Welcome to the office Wi-Fi!` | States that the office Wi-Fi is available 24/7 and can be accessed by connecting to the office network (repeated multiple times). | Fine-Tuned | Provides more domain-specific information, although repetitive. |
| **5** | **My computer is running very slowly. What could be the cause?** | Repeatedly states that it does not know why the computer is slow and cycles through nearly identical responses. | Suggests minimizing open windows, disabling automatic updates, preventing unnecessary software installations, and checking fan speed. Also includes unrelated exercises about font sizes. | Fine-Tuned | Offers some practical troubleshooting suggestions despite unrelated content. |
| **6** | **How do I install new software on my work computer?** | Provides generic Software Installation Wizard steps without considering enterprise approval or IT policies. | Returns only the command: `sudo apt-get update && sudo apt-get install -y gdebi`. | Neither | Neither response follows a realistic enterprise software installation process. |
| **7** | **I accidentally deleted an important file. Can I recover it?** | Gives inconsistent Windows restore instructions and references an outdated Recovery Console approach. | States it will check the file the next day and asks how long to wait for backup. | Neither | Both responses are inaccurate and do not provide a valid file recovery procedure. |
| **8** | **What should I do if I suspect a phishing email?** | Advises reporting to Fraud.com and includes unrelated information about Bootstrap, Sass, and JavaScript. | Advises contacting the local police department (911) if a suspicious email is received. | Neither | Neither response follows standard enterprise phishing response procedures. |
| **9** | **How do I request new hardware like a monitor or keyboard?** | Simply states that hardware issues will be handled as soon as possible. | Explains how to request hardware by emailing the support team, includes expected turnaround time, and lists required request details (hardware name, type, model, location, and serial number). | Fine-Tuned | More complete, structured, and aligned with an IT helpdesk workflow. |

## Summary

| Metric | Observation |
|--------|-------------|
| **Fine-Tuned Better** | Questions **0, 1, 3, 4, 5, 9** |
| **Neither Better** | Questions **2, 6, 7, 8** |
| **Base Model Better** | None |

### Overall Assessment

- The **Fine-Tuned model** generally produces responses that are more relevant to an IT Helpdesk domain.
- However, several responses still suffer from **hallucinations, repetition, placeholder text, and irrelevant content**.
- Additional fine-tuning using **high-quality IT Helpdesk Q&A data** and **Retrieval-Augmented Generation (RAG)** would significantly improve factual accuracy, policy compliance, and response consistency.