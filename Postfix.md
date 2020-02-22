### IPV4 only
* in /etc/postfix/main.cf
  * Change inet_protocols value from inet_protocols = all to inet_protocols = ipv4.
  * restart postfix