# Troubleshooting

# Help Desk Ticket Scenario #001: User calls in saying they can't log in and need to reset their password

**Password Reset**

Found the correct user on ADUC and made sure they had to change their PW at next logon for security purposes.

![PW Reset Step 1](../screenshots/aduc-find-user.png)
![PW Reset Step 2](../screenshots/aduc-reset-pw.png)
![PW Reset Step 3](../screenshots/aduc-set-new-pw.png)
![PW Reset Step 4](../screenshots/aduc-set-new-pw-success.png)

**Confirmed Client Could Log In**

Made sure the user could successfully log in after the password reset.

![PW Reset Step 5](../screenshots/client-vm-change-pw-login.png)
![PW Reset Step 6](../screenshots/client-vm-set-new-pw.png)
![PW Reset Step 7](../screenshots/client-vm-change-pw-success.png)

**ALWAYS make sure the user can log in. NEVER close ticket and move on unless you want extra work and duplicate tickets**

![PW Reset Step 8](../screenshots/pw-reset-whoami-cmd.png)

I only show this to prove she logged in. In a real-world scenario, I'd be confirming with the user over the phone.
