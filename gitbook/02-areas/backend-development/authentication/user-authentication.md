MIT opencourseware
Video - https://www.youtube.com/watch?v=MT7X17ZRo1U

- Passwords - weakest authentication technique
	- very less entropy
	- easy for hackers to guess
	- security questions used to retrieve password have lower entropies than the password themselves
	- users use same password across many websites
- the continued domination of passwords over all of the methods of end-user authentication is a major embarrassment for security researchers.
### Storing passwords
- Password - secret shared between user and server
	- naive implementation - a table in server that maps user with their password
	- this table can be compromised to an attacker
	- next improvement: user -> hash(password)
	- hash functions difficult to invert
	- but still passwords in practice have skewed distributions
		- top 5000 passwords cover about 20% of users - attackers who got this 5000 passwords can hack 20% users
		- passwords: 10-20 bits of entropy
	- to avoid this, you can use expensive key derivation function for hashing - eg: PBKDF2, BCrypt - takes more time to crack compared to regular hashing functions - these operations are basically hashing multiple times
	- Con - rainbow tables - map of password to hash values can be created by attacker
	- salt - input some additional some randomness - hash(salt, password) - salt is stored in clear text in server-side - prevents attackers from building a single rainbow table and use it against all DBs of passwords - if two users have same password, now the hash will not be same for both of them. when user changes password, ideal to change his/her salt too - so that even if a lazy user uses his/her old password, this time the hash will be different cuz of the new salt
### Transmitting passwords
1. Send password in the clear - bad
2. Send over any encrypted connection - transfer the password before transmitting - encryption key can be pulled down from the middle of the transmission
	1. if the receiver (server) is not authenticated, the client could be wrongly sending the password directly to a middle-man attacker - here hashing or encryption everything looses it power as we are handing over the encryption key and password directly to the attacker
3. Challenge/response protocol
	1. client sends hi, server sends back a challenge string C; client sends back hash(C+password)
	2. Cons:
		1. Client is not introducing any randomness here, only server is adding C
		2. Server can pick the same C again and again - allowing to build a rainbow table easily
	3. Ways to improve:
		1. User expensive hash functions
		2. Client can add its own challenge C to password
4. Anti-hammering defenses
	1. rate-limits number of password guesses that a bad client can issue
		1. 3 guesses per second
	2. also, implement time-outs between bunch of requests
		1. after 3 failed guesses per second, block for 10 seconds
		   
	>Telepathwords - site guesses your next letter of password - has a database of common passwords, popular phrases and common user biases of user's way of picking passwords 

	3.  Is your password offline guessable
		1. this was a problem kerberos v4 and v5 (without preauth) had - here anyone could ask the KDC for a ticket that would be encrypted with the user's password. KDC was not authenticated requests that were coming from a client
	4. Password recovery
		1. strength of the overall system = min(password's entropy, recovery question's entropy)
		2. Cons of recovery questions:
			1. Low entropy
			2. social media leaks - "what's your fav movie?" - answer might be there on your imdb profile
			3. if user selects the question - they are very weak - like "what's 2 + 3?"
### Evaluating authentication schemes
#### Metrics
##### 1. Usability
- easy to learn? (passwords - yes)
- infrequent errors? (passwords - quas: yes - subjective)
- scalable for users? (passwords - no, users have to remember to a lot of different passwords - hence ppl re-use)
- easy recovery? (passwords - yes)
- nothing to carry? do you need to have a smartphone app to authenticate, carry an otp? (password - yes)
- 