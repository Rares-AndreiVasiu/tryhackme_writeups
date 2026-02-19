# The Phishing Pond

> This challenge presents a list of emails and I will be required to identify wheather they are phishing emails or not.

## Here is how I tackled this assignment:

The first step is always observation of emails. I checked for the following clues in their email addresses:
- *Look-alike sender addresses*: such as g00gle.com instead of google.com, rnicrosoft.com instead of microsoft.com  
- *Impersonation*: when the display name of sender is familiar, but the domain name doesn't match with the company's domain.

Moreover I jump into the content of the email to investigate further for:
- *Scare tactics, urgency, immediate actions*: these keywords lead to a possible phishing email as to distrub the receiver by its sense of urgency and fall into the trap.
- *Ridiculously implausible offers*: big prizes, huge discounts, mega deals, high paying job opportunities which all have one thing in common. Sharing sensitive information.
- *Malicious attachments*:  different file types DOC, XLS, ZIP asking you to “enable macros” or containing malware.

## Hands-on

![email 1](./images/2026-02-19_13-08.png)
> It is a legitimate email.

:x: **PHISHING**
---

![email_2](./images/2026-02-19_13-09.png)
> Email contains an **attachment** and the sender asks us to **enable macros**.

:white_check_mark: **PHISHING**
---

![email_3](./images/2026-02-19_13-09_1.png)
> The sender requests us to **enable macros** to "review the attachment".

:white_check_mark: **PHISHING**
---

![email_4](./images/2026-02-19_13-09_2.png)
> It is a legitimate email from the HR departament informing the receiver about a meeting on Thursday at 14:00.

:x: **PHISHING**
---

![email_5](./images/2026-02-19_13-10.png)
> Sender's domain *(@gmail.com)* **does not match the company's domain** *@tryhackme.com*. "Emma" **impersonates** herself as a member of **HR** department and asks the receiver to open 
an attached file and fill in with **bank** details and sensitive information. There is no sense of urgency.

:white_check_mark: **PHISHING**
---

![email_6](./images/2026-02-19_13-10_1.png)
> This is friendly email from an office colleague, Jane Doe. Nothing odd to be seen here.

:x: **PHISHING**
---

![email_7](./images/2026-02-19_13-10_2.png)
> The sender asks Peter to open a link which in theory should redirect to a payment portal. Although this is not the case, since the link uses a deceptive domain to mimic that payment
portal.

:white_check_mark: **PHISHING**

---

![email_8](./images/2026-02-19_13-11.png)

---

![email_9](./images/2026-02-19_13-11_1.png)

---

![email_10](./images/2026-02-19_13-11_2.png)


