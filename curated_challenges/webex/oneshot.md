# Oneshot
This challenge asks us to find the flag by guessing the password of the different levels of the website. We do this by manipulating the HTML code of the web page.
# Working
First we try standard SQL injections to bypass the filter but it does not work. The website basically creates new password and new table with every new session so we only have one chance to find the flag per session.
According to the source code, the flag is returned when our query returns atleast one row, and tells us that we failed otherwise. In the code, it shows that the Id requires only the first 16 characters to be hex, so we can add sql payloads after the already existing Id value to manipulate the code into giving us the flag.
we use "WHERE 1=1 UNION SELECT ? --". Since as per the code, the value gets directly concatenated as a string in the query, if we add "WHERE 1=1 UNION SELECT ? --" after the value, it will always return a row because 1=1 always.

<img width="1920" height="873" alt="image" src="https://github.com/user-attachments/assets/7687e891-bad0-438f-9dc9-68048b78aaa0" />

<img width="1298" height="743" alt="image" src="https://github.com/user-attachments/assets/fbf8f9e7-dc15-4826-8ed3-a303dfde6a1f" />

We get the flag as atleast one row is returned.

# Flag
Flag: nite{are_you_feeling_the_heat_now :)}
# Resources
https://portswigger.net/web-security/sql-injection/union-attacks

https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master

