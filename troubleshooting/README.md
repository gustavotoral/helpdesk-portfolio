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

**ALWAYS make sure the user can log in. NEVER close the ticket and move on unless you want extra work and duplicate tickets**

![PW Reset Step 8](../screenshots/pw-reset-whoami-cmd.png)

I only show this to prove she logged in. In a real-world scenario, I'd be confirming with the user over the phone.


# Help Desk Ticket Scenario #002: User calls in saying they're locked out of their account

**Unlocking Locked Account**

Find the CORRECT user on Active Directory's ADUC and tick the unlock account.

![Account Lockout 1](../screenshots/account-locked-out.png)
![Account Lockout 2](../screenshots/aduc-unlock-account.png)
![Account Lockout 3](../screenshots/confirm-user-account-unlocked.png)

Make sure to ask if she needs the password reset or if she notices whether the CAPS LOCK was ON or she was typing the password incorrectly before ending the call.
