---
title: "Change a user name and email address in Office 365"
ms.author: kwekua
author: kwekua
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- Adm_O365_Top
- strat_admin_top
ms.custom:
- Adm_O365
- Adm_O365_FullSet
- Adm_O365_Top
- Core_O365Admin_Migration
- MiniMaven
- strat_admin_top
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: fb5ac074-e203-4e1f-9843-b9d1a3e03297
description: "Learn how a global admin can change a user's Office 365 email address and display name. "
---

# Change a user name and email address in Office 365

   
You may need to change someone's Office 365 email address and display name if, for example, they get married and their last name changes.
  
## Change a user's email address

You must be an [Office 365 global admin](about-admin-roles.md) to do these steps. 
  
1. In the Admin center, go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Active users</a> page, or choose **Users** \> **Active users**.
    
    
    
2. On the **Active Users** page, select the name of the person you want to edit. 
    
3. On the right, in the **Username / Email Aliases** row, choose **Edit**.
    
4. In the **Alias** box, type the first part of the new email address. If you added your own domain to Office 365, you can choose the domain for the new email alias by using the drop-down list. Then choose **Add**. 
    
    **IMPORTANT**: 
    
  - If you get the error message " **A parameter cannot be found that matches parameter name 'EmailAddresses**" it means that it's taking a bit longer for Office 365 to finish setting up your tenant, or your custom domain if you recently added one. The setup process can take up to 4 hours to complete. Wait a while so the setup process has time to finish, and then try again. If the problem persists, call Support and they will do a full sync for you.
    
  - If you get the error message " **We're sorry, the user couldn't be edited. Review the user information and try again**." it means you aren't an Office 365 global admin and you don't have permissions to change the user name. 
    
    ![The Edit email addresses and username pane showing the primary email address, and a new alias to be added.](../media/2518a8b8-1136-4639-b159-35ad21f61437.png)
  
5. Choose **Set as Primary** for the email address that you want to set as the primary email address for that person. 
    
    **IMPORTANT**: You won't see this option to Set as Primary if you purchased Office 365 from GoDaddy or another Partner service that provides a management console. Instead, sign in to the GoDaddy / partner's management console to set the primary alias. 
    
    Also, you'll only see this option if you're an Office 365 global admin. If you don't see the option, you don't have permissions to change a user's name and primary email address.
    
    ![The Edit email addresses and username pane showing the primary email address, and an alias that can be set as the primary email address.](../media/2de59654-fd2d-4a65-8eb0-c49079c4a4e9.png)
  
6. You'll see a big yellow warning that you're about to change the person's sign-in information. Choose **Save**, then **Close**.
    
7. Tell the person the following information:
    
  - What their new username is. They'll need it to sign in to Office 365.
    
  - If they are using Skype for Business Online, tell them they will need to reschedule any Skype for Business Online meetings that they organized, and that they will need to tell their external contacts to update the old contact information.
  
  - If they are using OneDrive, tell them that the URL of their OneDrive will change. Other applications such as OneNote may need to updated to use the changed OneDrive URL.
    
  - If their password changed too, tell them that they will be prompted to enter the new password on their mobile device, or it won't sync.
    
## Change a user's display name


1. Next to the person's display name, choose **Edit**.
    
    ![Close-up of the Display name row, with a hand pointing to the Edit button.](../media/f93aefa1-f74d-49f3-836c-ec155e1721ad.png)
  
2. Type a new name for the person and then choose **Save**.
    
    If you get the error message " **We're sorry, the user couldn't be edited. Review the user information and try again**." it means you aren't an Office 365 global admin and you don't have permissions to change the user name.
    
    ![The edit contact pane where you can type a new first, last, and display name.](../media/61bd5d52-3a2c-467c-acf3-0c41ae02e54f.png)
  
## Did you get "A parameter cannot be found that matches parameter name 'EmailAddresses"?


If you get the error message " **A parameter cannot be found that matches parameter name 'EmailAddresses**" it means that it's taking a bit longer for Office 365 to finish setting up your tenant, or your custom domain if you recently added one. The setup process can take up to 4 hours to complete. Wait a while so the set up process has time to finish, and then try again. If the problem persists, call Support and they will do a full sync for you.
  
## Did you get "We're sorry, the user couldn't be edited. Review the user information and try again"?


If you get the error message " **We're sorry, the user couldn't be edited. Review the user information and try again**." it means you aren't an Office 365 global admin and you don't have permissions to change the user name. Find the Office 365 global admin in your business and ask them to make the change.
  
## More information on changing or adding email addresses


### Tip: Keep the person's old email address

A person's previous primary email address is retained as an additional email address. **We strongly recommend that you don't remove the old email address.**
  
Some people will likely continue to send email to the person's old email address and deleting it may result in NDR failures. Office 365 will automatically route it to the new one. Also, do not reuse old SMTP email addresses and apply them to new accounts. This can also cause NDR failures or delivery to an unintended mailbox.
  
### How long until the new name appears across services?

It might take up to 24 hours for this change to take effect across all services. After the change has taken effect, the person will have to sign in to Outlook, Skype for Business and SharePoint with their updated username, so be sure to tell them about this change.
  
### What if the person's offline address book won't sync with the Global Address List?

If they are using Exchange Online or if their Office 365 account is linked with your organization's on-premises Exchange environment, you may see this error when you try to change a username and email address: "This user is synchronized with your local Active Directory. Some details can be edited only through your local Active Directory."
  
This is due to the Microsoft Online Email Routing Address (MOERA). The MOERA is constructed from the person's  _userPrincipalName_ attribute in Active Directory and is automatically assigned to the cloud account during the initial sync and once created, it cannot be modified or removed in Office 365. You can subsequently change the username in the Active Directory, but it will not change the MOERA and you may run into issues displaying the newly changed name in the Global Address List. 
  
To fix this, log in to the [Azure Active Directory Module for PowerShell]( https://go.microsoft.com/fwlink/?LinkId=823193) with your Office 365 administrator credentials. and use the following syntax: 
  
```
Set-MsolUserPrincipalName -UserPrincipalName anne.wallace@contoso.onmicrosoft.com -NewUserPrincipalName anne.jones@contoso.com
```

> [!TIP]
> This changes the person's **userPrincipalName** attribute and has no bearing on their email address. It is best practice, however, to have the person's logon UPN match their primary SMTP address. 
  
To learn how to change someone's username in Active Directory, in Windows Server 2003 and earlier, see [Rename a user account](https://go.microsoft.com/fwlink/?LinkId=809091).
  
## Related Topics


[Admins: Reset a password for one or more users in Office 365](reset-passwords.md)
  
[Add another email address to a user in Office 365](../email/add-another-email-alias-for-a-user.md)
  

