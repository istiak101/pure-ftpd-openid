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

Workflow:
The module will query the idP with the provided username and password. After the authentication is complete the module must return response in stdout for pure-authd in following manner.

```
auth_ok:1
uid:42
gid:21
dir:/home/j
end
```
auth_ok can have 3 different values, 0,1 and -1.
0 - User not found
1 - User found and auth success
-1 - User found and auth failed

uid & gid must be greater than 0 which stands for the root user.

And at last this must end with `end`.

A callback URI will be required for openid connect so this will involve a TCP socket on some port. And we will likely need a proxy if we want to have this on port 80(how to make authentication the slowest thing on earth).
