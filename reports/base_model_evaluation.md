# Base Model Evaluation Results

| Index | Question | Base Model Answer | Problem |
|:----:|----------|-------------------|---------|
| **0** | **My laptop is not turning on. What should I do?** | States that the issue is caused by a firmware bug and recommends downloading firmware updates from Google Chrome OS/Chromebook support pages. It also provides generic power-cycle instructions that are unrelated to the IT Helpdesk environment. | The answer is generic, hallucinates a Chromebook-specific issue, and is not specific to our IT Helpdesk policy. |
| **1** | **How do I reset my password for the company's internal network?** | Lists placeholder IT department contact information (email, phone, fax) and repeatedly restates the question without actually explaining the password reset procedure. | The answer is generic, contains fabricated contact information, and is not specific to our IT Helpdesk policy. |
| **2** | **I can't access my email. What are the common troubleshooting steps?** | Repeats a user's problem statement (unable to access email despite webmail working) instead of providing troubleshooting steps or guidance. | The answer is generic, merely paraphrases the issue, and is not specific to our IT Helpdesk policy. |
| **3** | **My printer is not working. How can I fix it?** | Advises restarting the printer by turning it off and on again, claiming that this should resolve the issue. | The answer is overly generic, lacks meaningful troubleshooting steps, and is not specific to our IT Helpdesk policy. |
| **4** | **How do I connect to the office Wi-Fi?** | ```text Welcome to the office Wi-Fi! ``` | The answer is generic, provides no connection instructions, and is not specific to our IT Helpdesk policy. |
| **5** | **My computer is running very slowly. What could be the cause?** | Repeatedly states that the computer is slow but does not know the reason. It cycles through multiple variations of the same statement without offering any troubleshooting advice. | The answer is repetitive, unhelpful, and not specific to our IT Helpdesk policy. |
| **6** | **How do I install new software on my work computer?** | Provides generic installation wizard instructions (select software, click Install, follow the wizard, access the application afterward) without addressing enterprise approval or IT processes. | The answer is generic and not specific to our IT Helpdesk policy. |
| **7** | **I accidentally deleted an important file. Can I recover it?** | Begins by incorrectly stating that the file cannot be recovered, then describes Windows restore points and Recovery Console with inaccurate recovery instructions and an outdated Microsoft support link. | The answer is inaccurate, inconsistent, and not specific to our IT Helpdesk policy. |
| **8** | **What should I do if I suspect a phishing email?** | Advises not clicking links, reporting the incident to Fraud.com, and calling a phone number. It also includes unrelated information about Bootstrap, Sass, and JavaScript used to design a webpage. | The answer contains irrelevant information, external references, and is not specific to our IT Helpdesk policy. |
| **9** | **How do I request new hardware like a monitor or keyboard?** | States only that hardware issues will be taken care of as soon as possible. | The answer is too vague, does not explain the hardware request process, and is not specific to our IT Helpdesk policy. |

## Summary

**Overall observations:**

- The responses are **generic** and **not grounded in an enterprise IT Helpdesk knowledge base**.
- Several responses **hallucinate** product-specific information (e.g., Chromebook firmware, fabricated contact details, Fraud.com).
- Many answers are **repetitive**, **incomplete**, or **factually incorrect**.
- None of the responses follow a realistic **IT support workflow** (ticket creation, escalation, self-service portal, approval process, or company policies).
- These results indicate that the **base model lacks domain adaptation** and requires fine-tuning or retrieval-augmented generation (RAG) to provide organization-specific IT support responses.
```