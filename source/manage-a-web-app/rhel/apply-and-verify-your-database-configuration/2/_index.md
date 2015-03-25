## 2. Use Berkshelf to upload the cookbooks to the Chef server

Now run `berks upload` to upload everything to the Chef server.

```bash
# ~/chef-repo/cookbooks/web_application
$ berks upload
Skipping apache2 (3.0.1) (frozen)
Uploaded apt (2.7.0) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded build-essential (2.2.1) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded chef-sugar (3.0.1) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded database (4.0.3) to: 'https://api.opscode.com:443/organizations/your-org-name'
Skipping iptables (0.14.1) (frozen)
Skipping logrotate (1.9.1) (frozen)
Uploaded mariadb (0.3.0) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded mysql (6.0.18) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded mysql2_chef_gem (1.0.1) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded openssl (4.0.0) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded postgresql (3.4.18) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded rbac (1.0.2) to: 'https://api.opscode.com:443/organizations/your-org-name'
Skipping selinux (0.9.0) (frozen)
Uploaded smf (2.2.6) to: 'https://api.opscode.com:443/organizations/your-org-name'
Skipping web_application (0.1.0) (frozen)
Uploaded yum (3.5.3) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded yum-epel (0.6.0) to: 'https://api.opscode.com:443/organizations/your-org-name'
Uploaded yum-mysql-community (0.1.14) to: 'https://api.opscode.com:443/organizations/your-org-name'
```

One advantage to pinning to specific cookbook versions is that Berkshelf can skip the upload process for cookbook versions that already exist on the Chef server. However, you'll notice that your `web_application` was skipped as well!

```bash
# ~/chef-repo/cookbooks/web_application
Skipping web_application (0.1.0) (frozen)
```

That's because the Chef server already has version `0.1.0`, so Berkshelf didn't upload it again. This is actually a good thing because it helps ensure that each cookbook version has no variants.