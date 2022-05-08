# WHMCS plugin (deprecated)

WHMCS is an all-in-one client management, billing & support solution for online businesses (not included). Paired with Mailcheap's WHMCS plugin, you can automatically provision end-user accounts (for your clients) based on storage and number of domains/mailboxes/domain aliases/mailbox aliases.

WHMCS plugin is a provisioning module which creates a **DomainAdmin** user according to the product/plan specification (number of domains, mailboxes, storage quota, etc.) set by the administrator (you) in WHMCS.

The plugin files are contained in the ZIP file `mailcheap-v1.1.zip`.

### Install WHMCS plugin

- Unzip the WHMCS plugin.
- Upload `modules/servers/mailcheap` directory to your whmcs install `modules/servers/` folder.
- Set the correct permissions for the above uploaded folder and its subfolders/files.
- Your directory structure should now look like this `../your-whmcs-install-folder/modules/servers/mailcheap/..`

### Setup server in WHMCS

Step 1. From your WHMCS admin portal > navigate to _Setup_ (menu bar) > Products/Services > Servers.

Step 2. Create a server group by clicking _Create New Group_.

Step 3. Create a server by clicking _Add New Server_ and assign it to the previously created server group.

Fill in the below fields:

- Name: `Your-mail-server-name`
- Hostname: `Your-mail-server-hostname`
- IP Address: `Your-mail-server-IP`

- Type: `MailCheap`
- Username: `MasterAdmin-username`
- Password: `MasterAdmin-password`

!!! tip "Tip"
    It is recommended to create a new MasterAdmin for configuring in WHMCS.

Step 4. Check (enable) the option _Tick to use SSL Mode for Connections_.

Step 5. Press the red _Test Connection_ button, it should show green "SUCCESSFUL!" message.

Step 6. Click _Save Changes_ button.

### Setup product in WHMCS

Step 1. From your WHMCS admin portal > navigate to _Setup_ (menu bar) > Products/Services > Products/Services > Create a New Product > follow on-screen instructions.

Step 2. In _Module Settings_ tab > choose Module Name _MailCheap_ from the drop-down menu.

Step 3. Assign the previously created server group to the product in the _Server Group_ field.

Step 4. Set the product/plan account (**DomainAdmin** user) limits. You're able to set storage quota in MB, number of mailboxes, number of domains, aliases, etc.

Step 5. Check (enable) the option _Automatically setup the product when you manually accept a pending order_.

Step 6. Click _Save Changes_ button.

### Setup product welcome email

Set up a welcome email template for your product/plan in WHMCS. This welcome email will be sent to your client (end-user) upon product activation and will include login details and other information for them to get started with their hosted email plan.

Step 1. From your WHMCS admin portal > navigate to _Setup_ (menu bar) > _Email Templates_ > _Create New Email Template_ > choose Email Type as 'Product/Service' and Unique Name as 'Your-product-name Welcome Email' > click _Create_ button.

Step 2a. In the following 'Your-product-name Welcome Email' template page, choose Subject as 'New Product Information' and in the body (text area) enter the below details (modify accordingly):

```
Dear {$client_name},

Your order for {$service_product_name} has now been activated. Please keep this message for your records.

Product/Service: {$service_product_name}
Payment Method: {$service_payment_method}
Amount: {$service_recurring_amount}
Billing Cycle: {$service_billing_cycle}
Next Due Date: {$service_next_due_date}

Login Details:

Server hostname: {$service_server_hostname}
Web admin panel: https://{$service_server_hostname}
Webmail (Roundcube): https://{$service_server_hostname}/webmail/
Webmail (Rainloop): https://{$service_server_hostname}/rainloop/
Username: {$service_username}
Password: {$service_password}

Get started with your hosted email service by following our documentation: <enter your documentation URL here>

Please keep this email safely as it contains your access credentials, mailserver hostname, etc. It is highly recommended to change the above password upon login. Use a password manager to create random passwords for all your accounts.

Thank you for choosing us.

{$signature}
```

Step 2b. Click _Save Changes_ button.

Step 3. From your WHMCS admin portal > navigate to _Setup_ (menu bar) > Products/Services > Products/Services > select the product you set up earlier > Welcome Email > choose 'Your-product-name Welcome Email' from the drop-down menu > click _Save Changes_ button.
