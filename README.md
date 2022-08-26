# pure-ftpd-openid
Pure-ftpd OpenID connect external authentication plugin

If I ever have time to write this authentication plugin for my SSO server I will probably finish this!

Pros:
Integration with 3rd party idP provider like Google, Facebook, Amazon.

Cons:
As this involves pure-authd communication with idP through the custom authentication module and replying back to pure-ftpd
the authentication will be slower than other authentication methods natively available in pure-ftpd. If your organization 
uses PAM or LDAP those are already available in pure-ftpd. There is no point adding another layer to your application to 
make it slow. But if you must rely on 3rd party idP let me finish writing this module!
