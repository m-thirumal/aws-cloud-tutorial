### Multi Tenancy 

1. Tenant-specific Cognito configuration
   Required if you want your customers to set up SAML/AD integration or configure themselves the Cognito password policies.

2. Cognito Hosted UI
   Required if you have a web application and don’t want to maintain your own OAuth server (for details). You won’t need this for mobile-only applications.

3. Cross-tenant login page
   Required if you can’t ask your users to select the tenant e.g. by going to a tenant-specific URL like tenant.example.com
   
4. Same email in multiple tenants
   Required if you have users who need accounts in multiple of the tenants. For example: an implementation partner who supports multiple of your customers.

   You might be able to work around this by asking your partners to use different email addresses per tenant, e.g. joe+tenant1@gmail.com, joe+tenant2@gmail.com, etc