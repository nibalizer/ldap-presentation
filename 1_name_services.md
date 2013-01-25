!SLIDE callout

# Name Services

Name Services

!SLIDE

# What is a name service?

* Name service interacts with the name database
  * 3 big databases you NEED to know about
  * passwd
  * shadow
  * group

!SLIDE

# How is the name service database interacted with?

* Getent
* id
* groups

!SLIDE commandline incremental

# Getent

	$ getent passwd nibz
	nibz:x:1861:300:Spencer O Krum:/u/nibz:/bin/zsh
	
	$ cat /etc/passwd | grep snmp
	snmp:x:120:130::/var/lib/snmp:/bin/false
	
	$ getent passwd snmp
	snmp:x:120:130::/var/lib/snmp:/bin/false
	
	$ cat /etc/passwd | grep nibz

!SLIDE commandline incremental

# id

	$ id snmp                                                                   
	uid=120(snmp) gid=130(snmp) groups=130(snmp)                                
	
	$ id krum                                                                   
	uid=11467(krum) gid=300(them) groups=185(psuacm),1086(wetlab),300(them)     

!SLIDE commandline incremental

# groups

	$ groups krum                
	krum : them psuacm wetlab    

	$ groups snmp                
	snmp : snmp                  


!SLIDE commandline incremental

# Application of this

	
	$ ls -ln | head -n 3
	total 4840146
	drwx------  3 1861 300          4 2012-04-29 23:39 2555779
	-rw-------  1 1861 300          6 2012-02-29 19:29 750
	
	$ getent passwd 1861
	nibz:x:1861:300:Spencer O Krum:/u/nibz:/bin/zsh

!SLIDE

# Name services

* The major name services
  * passwd:     
  * shadow:     
  * group:      
  * hosts:      
  * ethers:     
  * netmasks:   
  * networks:   
  * protocols:  
  * rpc:        
  * services:   
  * automount:  
  * aliases:    

!SLIDE code smaller

	passwd:         files ldap            
	shadow:         files ldap            
	group:          files ldap            
	                                      
	hosts:          files dns             
	networks:       files                 
	                                      
	protocols:      db files ldap         
	services:       db files ldap         
	ethers:         db files ldap         
	rpc:            db files              
                                      
	netgroup:       ldap                  
	automount:      files ldap            


!SLIDE

* NSSwitch backends
  * files
  * ldap
  * wins
  * nis
  * nisplus

!SLIDE

* Pop Quiz
  * passwd
  * shadow
  * group
  * hosts
  * automount

!SLIDE

* DNS
  * TANGENT!
  * `host -t ns .`
