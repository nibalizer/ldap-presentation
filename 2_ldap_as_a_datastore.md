!SLIDE

* Leightweight Directory Access Protocol
  * fundamental goal it to centralized and reduce replication of data

!SLIDE 

* CORE RFCS
  * TANGENT RFCs
  * Request for Comments
  * Internet Engineering Task Force (IETF)
  * invented by Steve Crocker in 1969 
  * http://www.ietf.org/rfc/rfc0001
  * show off some favorites
  * http://www.ietf.org/rfc/rfc3514.txt

!SLIDE 

* CORE RFCS (trying again)
  * http://www.ietf.org/rfc/rfc255[1-6].txt -> core
  * http://www.ietf.org/rfc/rfc2829.txt -> authentication methods
  * http://www.ietf.org/rfc/rfc2830.txt -> LDAP TLS(transport layer security) extensions
  * http://www.ietf.org/rfc/rfc3377.txt -> LDAP  Technical Specification

!SLIDE

* comment on leightweight
  * X.500 (implemented whole osi stack)
  * NIS(+) (kennobakas drinking problem)

!SLIDE

* What goes in ldap?
  * Text mostly
  * JPEGs can go in(wat)
  * Browser history? Browser cache?
  * Isnt it possible to put browser metadata into ldap and have it sync accross lab computers?

!SLIDE

* LDAP, by the way, is a protocol
  * LDAP is message-based client/server protocol defined in RFC 2551
  * Async(not guaranteed return order)(draw picture)

!SLIDE

# Models

* LDAP is a tree, sometimes called a Directory Information Tree (DIT)
* Each entry has a unique name, built from a chain of relative distinguished names (RDN)s called its distinguished name (DN)
* Secuirty model: Access control lists (ACLs) have not been standardized


# LDAP

* LDAP as a DATASTORE
  * optimized for reads
  * not optimized for writes
  * dc is domain component
  * backed by hba
  * 'hdb is a variant of the bdb backend that uses a hierarchical database layout which supports subtree renames. It is otherwise identical to the bdb behavior, and all the same configuration options apply'

!SLIDE

# LDAP

* optimized for reads
* distrubuted model for storing information
* extend the types of information it stores
* advanced search capabilities
* loosely consistent replication among directory servers

!SLIDE

# Marut CS-tyme

* Holy datatypes Batman! its a tree!

!SLIDE

# Whats in here?

	$ ldapsearch -xLLL -h ldap.cat.pdx.edu uid=nibz uidNumber   
	dn: uid=nibz,ou=People,dc=catnip                            
	uidNumber: 1861                                             


!SLIDE

# How to query

* ldapsearch
  * -x
  * -LLL
  * -h
  * -b
  * -W
  * -D
  * -Z[Z]
  * search
  * returns


!SLIDE

# entry

* Start with a user
* structure of an entry cn=

!SLIDE

# multivalued RDN

* no, just no
  * example 'cn=Jane Smith+ou=Engineering,dc=science,dc=org'
  * escapes '\'
  * '#' at the beginning
  * ' ' at the  end

!SLIDE

# Case

* WTF ldap
  * case-preserving AND case-insensitive
  * wat
  * cn=nibz,dc=catnip == cn=Nibz,dc=Catnip

!SLIDE

# Attributes
* stuff
* things
* thing of it as a variable in a computer program
* can be multivalued
* -> kinda just adds, unless specifiaclly replaced
* this gets back to the idea that ldap/ldif is bonghits
* we will get more into this later but some questions:
* when are two attributes the same?
* when are two attributes different but still the same?

!SLIDE

# ObjectClass

* Every entry must have an object class, please try to find one that doesnt
* multiple values are common, required even
* some combinations of these are verbotten
* templates for data to be stored in an entry
* Support inheritance through SUP


!SLIDE

# Authentication

* userPassword attribute
* hashes
  * {MD5}Astnufirn8j7fthhe4hf4at==
  * {CRYPT}Astnufirn8j7fthhe4hf4at==
  * {SHA}Astnufirn8j7fthhe4hf4at==
  * {SSHA}Astnufirn8j7fthhe4hf4at==
  * $seed$number$hash

!SLIDE

# Authenticate to server

* Binding process
* Anonymous Authentication (-x)
* Simple authentication
  * login name(as dn) and password(CLEAR!)
  * ldap server attempts to match
* Simple Auth over SSL/TLS
  * LDAP over SSL tcp/636
  * StartTLS tcp/389

!SLIDE

#Authenticate to server

* SASL (Simple Authentication and Security Layer)
  * Kerb
  * GSSAPI (Generic Security Service Application Program Interface) (also kerb)
  * One time passwords via S/Key
  * EXTERNAL, wat
  * or HTTP/1.1 Digest (who remembers how digest works? I forgot)

!SLIDE

# Beyond mcecs

* ldapsearch -xLLL -h ldap.oit.pdx.edu -b dc=pdx,dc=edu uid=krum  
* dc.cecs.pdx.edu



