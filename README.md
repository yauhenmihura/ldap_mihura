# Task2 ldap_mihura

<br><b>1. Configure Audit logging</b></br>
Added in /etc/openldap/slapd.conf
### Audit Log
moduleload auditlog.la
overlay auditlog
auditlog /var/log/ldap/audit.log
###
Then created user and check
![imgs](pic/src_1_cu.png "imgs")
![imgs](pic/src_2_check_log.png "imgs")

<br><b>2. Configure Password Policy</b></br>
![imgs](pic/policy.png "imgs")
and use
ldapadd -x -D "cn=admin,dc=mnt,dc=lab" -W -f /etc/openldap/ldap-policy.ldif
![imgs](pic/policy2.png "imgs")

<br><b>3. Create groupOfNames Jenkins and Zabbix. Add users into these groups.</b></br>
![imgs](pic/src.png "imgs")
![imgs](pic/ldapsearch.png "imgs")
![imgs](pic/task3.png "imgs")
![imgs](pic/lin.png "imgs")
Edit /etc/nslcd.conf:
filter passwd (&(objectClass=posixAccount)(memberOf=cn=Linux,ou=Groups,dc=mnt,dc=lab))

$ authconfig --enableldap --enableldapauth --ldapserver=ldap://192.168.33.15/ --ldapbasedn=dc=mnt,dc=lab --disablefingerprint --kickstart --enablemkhomedir
![imgs](pic/end.png "imgs")
![imgs](pic/id.png "imgs")

