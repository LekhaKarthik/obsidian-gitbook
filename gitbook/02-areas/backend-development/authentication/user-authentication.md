MIT opencourseware
Video - https://www.youtube.com/watch?v=MT7X17ZRo1U

- Passwords - weakest authentication technique
	- very less entropy
	- easy for hackers to guess
	- security questions used to retrieve password have lower entropies than the password themselves
	- users use same password across many websites
- the continued domination of passwords over all of the methods of end-user authentication is a major embarrassment for security researchers.



- Password - secret shared between user and server
	- naive implementation - a table in server that maps user with their password
	- this table can be compromised to an attacker
	- next improvement: user -> hash(password)
	- hash funcs difficult to invert
	- but still passwords in practice have skewed distributions
		- top 5000 passwords cover about 20% of users - attackers who got this 5000 passwds can hack 20% users
		- passwords: 10-20 bits of entropy
	- to avoid this, you can use expensive key derivation function for hashing - eg: PBKDF2, BCrypt - takes more time to crack compared to regular hashing funcs
	- Con - rainbow tables - map of passwd to hash values can be created by attacker
	- salt - input some additional some randomness - hash(salt, passwd) - salt is stored in clear text in server-side - prevents attackers building a rainbow table - if two users have same passwd, now the hash will not be same for both of them


Transmitting passwords

1. Send pw in the clear - bad
2. Send over any crypted connection - transfer the pw before transmitting - encryption key can be pulled down from the middle of the transmission
3. Challenge/response protocol
	1. client sends hi, server sends back a challenge string C
	2. client sends back hash(C+passwd)
4. 