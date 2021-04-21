### What is Authentication and Authorization?

`Authentication` - "Who you are?", is the process of ascertaining that somebody really is who they claim to be.

`Authorization` refers to rules that determine who is allowed to do what. E.g. Thirumal may be authorized to create and delete databases, while Jesicca is only authorized to read.


#### There are many ways of authentication, few of which are worth discussing here:

   1. `Knowledge-based authentication`: The username password combination is a type of knowledge-based authentication. The idea is to verify the user based on the knowledge of the user for example answer to security questions, passwords, something which only the user should know.


   2. `Possession based authentication`: This type of authentication is based on verifying something which a user possesses. For example, when an application sends you One Time Passwords (OTPs) or a text message.

   Modern authentication practices use a combination of both types, also known as `Multi-Factor authentication`.


### Password handling in databases

1. Storing it in the plain `String` format
	* Hacking methods
		* It's open to developers, database administrator, etc..
2. Storing password as `HASH`
  * Possible attacks/hacking methods
		* MD5/SHA1 collisions
		* Rainbow Tables
		* Dictionary attacks, brute-force(GPUs can compute billions of hashes/sec)
3. Salted HASH
	 * Possible attacks/hacking methods
	 	* Incorporate app-specific salt + random user-specific salt
		* Use algorithm with configurable # of iteration (e.g. bycrypt, PBKDF2) to slow down brute force attacks

4. Secure Remote password (SRP) Protocol
	* Verified based Protocol
	* Password never travel over the wire
	* Resistant to several attack vectors
	* Perfect forward secrecy
