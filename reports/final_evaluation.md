# Base Model vs SFT Model vs DPO Model Comparison

| Index | Question | Base Model Answer | SFT Model Answer | DPO Model Answer | Best Answer | Reason |
|:----:|----------|-------------------|------------------|------------------|-------------|--------|
| **0** | **My laptop is not turning on. What should I do?** | Claims the issue is due to a Chromebook firmware bug and recommends downloading firmware updates from Google support pages. | Suggests holding the Windows power button for 15 seconds and then contacting customer support if the issue persists. | Suggests charging the laptop battery and provides a support document link. | **SFT Model** | Provides the most practical and actionable troubleshooting steps with escalation guidance. |
| **1** | **How do I reset my password for the company's internal network?** | Repeats placeholder IT department contact information without explaining the reset procedure. | Produces a password reset template with company placeholders but remains repetitive. | States that the password reset service will be available later and advises contacting the company's support team. | **DPO Model** | Concise and appropriately directs users to the support team instead of generating repetitive placeholder content. |
| **2** | **I can't access my email. What are the common troubleshooting steps?** | Repeats the user's problem instead of providing troubleshooting guidance. | Generates only repeated `*` characters with no useful information. | Explains that SMTP authentication may not be enabled and recommends enabling it in the mail client or ISP settings. | **DPO Model** | Provides an actual troubleshooting suggestion rather than repeating the prompt. |
| **3** | **My printer is not working. How can I fix it?** | Advises restarting the printer by turning it off and on again. | Replies with "You are not supposed to use printers." | Provides troubleshooting steps including checking drivers, reconnecting the printer, updating software, and contacting IT if needed. | **DPO Model** | Offers the most complete troubleshooting guidance, although some steps are generic. |
| **4** | **How do I connect to the office Wi-Fi?** | Displays only "Welcome to the office Wi-Fi!". | States that the office Wi-Fi is available 24/7 but repeats the same statement multiple times. | Produces unrelated metadata and configuration information instead of connection instructions. | **SFT Model** | Although repetitive, it is more relevant than the Base or DPO responses. |
| **5** | **My computer is running very slowly. What could be the cause?** | Repeatedly says it does not know why the computer is slow. | Suggests minimizing open windows, disabling automatic updates, reducing software installations, and checking fan speed. | Lists several realistic causes such as slow internet, high CPU usage, insufficient storage, overheating, antivirus interference, malware, and aging hardware. | **DPO Model** | Provides the most comprehensive and realistic diagnosis. |
| **6** | **How do I install new software on my work computer?** | Gives generic Software Installation Wizard instructions. | Returns only the Linux command `sudo apt-get update && sudo apt-get install -y gdebi`. | Explains that installation depends on administrator privileges and discusses software deployment concepts. | **DPO Model** | More informative than the other responses, although still not aligned with enterprise IT policies. |
| **7** | **I accidentally deleted an important file. Can I recover it?** | Provides inaccurate Windows Restore Point and Recovery Console instructions. | States that it will check the file the next day and asks how long to wait for backup. | States that deleted files cannot be recovered but suggests recovering data from external media if available. | **None** | None of the responses provide an accurate or reliable file recovery procedure. |
| **8** | **What should I do if I suspect a phishing email?** | Advises reporting to Fraud.com and includes unrelated web development information. | Advises contacting the local police (911). | Advises not clicking links, contacting IT, ensuring system security, updating software, and maintaining backups. | **DPO Model** | Most closely resembles standard enterprise phishing guidance. |
| **9** | **How do I request new hardware like a monitor or keyboard?** | Simply states that hardware issues will be handled as soon as possible. | Explains the hardware request process, turnaround time, and required request details. | Advises emailing the team with an order number and links to a product website. | **SFT Model** | Best aligned with a typical IT Helpdesk hardware request workflow. |

## Overall Summary

| Model | Strengths | Weaknesses |
|-------|-----------|------------|
| **Base Model** | Occasionally provides basic troubleshooting suggestions. | Frequently hallucinates information, is repetitive, generic, and not aligned with enterprise IT Helpdesk workflows. |
| **SFT Model** | Produces more domain-specific responses and follows IT Helpdesk workflows more closely. | Still contains repetitive text, placeholder information, and occasional hallucinations. |
| **DPO Model** | Generates more natural, detailed, and helpful explanations for several troubleshooting scenarios. | Sometimes invents unsupported information, includes irrelevant links, or gives inaccurate enterprise-specific guidance. |

## Overall Winner

| Model | Best Responses |
|-------|---------------:|
| **Base Model** | 0 |
| **SFT Model** | 3 |
| **DPO Model** | 5 |
| **None** | 1 |

**Conclusion:** The **DPO Model** produces the strongest overall responses, particularly for troubleshooting and security-related questions. However, the **SFT Model** performs better for organization-specific IT Helpdesk workflows such as hardware requests and Wi-Fi access. Both models would benefit from further fine-tuning using organization-specific IT support data or integration with a Retrieval-Augmented Generation (RAG) system.