# Relayer
RELAYER A Secure Persona Management and Anonymous Email Relay Tool

1. INTRODUCTION

Relayer is a command line tool that targets users who require a tool to manage multiple identities on the Web and communicate behind greater privacy. It is developed on a base of strong cryptography and anonymous networking.

It deals with two tasks:

- Persona Management: It enables you to create, store, and manage multiple fake identities, or personas, within a secured and encrypted database. This is quite helpful if you want to register for a service without exposing your actual details.
- Anonymous Communication: It is a mail relay service that you can use to send, receive emails through a temporary, anonymous mail address. It is able to conceal your IP address from being known to the mail server and the receiver.

2. CORE FEATURES

– Dual-Database System: It keeps high-sensitivity email credentials separate from lower-sensitivity identity information within two different, encrypted KeePass dbs.
- Tor Integration: All of your emails for both sending and receiving can be done through the Tor network. This makes your IP address anonymous.
- Secure Storing of Credentials: Credentials for all passwords, both for the database and for the relay email address, are dealt with securely and stored in a non-readable format.
- Realistic Persona Creation. Utilizes the Faker library to provide realistic-sounding personas such as names, addresses, or job titles.
- Fully Offline Identity Management - Creating, listing, or displaying identities is done without any need for the internet and never reveals your email credentials.

3. CRITICAL SECURITY WARNING

THE ANONYMITY PROVIDED BY RELAYER DEPENDS WHOLLY ON THE PROPER USE

- If you enter the ‘relay’ command without the ‘–tor’ option, your IP address is EXPOSED to your email provider. It only takes a ‘single mistake’ to be traced back to your identity through your anonymous email address.


- It offers privacy and anonymity, but is far from a magic solution. It is merely a piece of a much larger puzzle of operational security. Never forget what you're putting into the body of your emails.

4. PREREQUISITES

These prerequisites to using Relayer include:
- Python 3.6 or higher.
- Package manager for Python, called pip.

- An active Tor installation. This could be the Tor process itself that is installed as a system service, or just a Tor browser window open.


- The necessary Python libraries can be installed through the following command:

pip install pykeepass faker pysocks

5. SET-UP GUIDE (4 STE

Please follow these steps to set up the Relayer for the first time.

Step 1: Obtain an Anonymous Email Account
You may NOT use your own Gmail, Outlook, or Yahoo email. They require a phone number and aren't private.

- Recommendation: Sign up for a free, privacy-friendly email service that supports the IMAP and SMTP protocols using the Tor Browser. Good options include:

- Disroot.org

- Riseup.net (Sometimes requires invitation)

- Never provide any actual personal details when signing up.

- Once you have created the account, find the provider's IMAP and SMTP server details. You will require them for Step 4. In Disroot's case, they're both ‘disroot.org’.

Step 2: Initialize the Databases

Relayer must now make twoencrypted databases of its own. You can type the following command from your terminal:

python relayer.py init

You will be prompted to enter and enter a master password for ‘secure_relays.kdbx’ and then ‘secure_identities.kdbx’. It is advisable to enter different and strong passwords for each.

Step 3: Configure the Relay
Now, you can now associate your anonymous email address to the Relayer. In fact, the most convenient way to get prompted for configuration is to execute your first 'check' command.
VERY IMPORTANT: Please execute this command passing the '-tor' switch to keep your IP address anonymous at this initial step.
python relayer.py --tor relay check

This tool shall detect that there is no configuration, asking you to enter:

- Your Relay Email Address(email created in step 1 above).

- The password for that Email address.

- Your REAL email address (where you want emails to be sent to).


- Your mail server addresses for SMTP and/or IMAP.

Your credentials shall be stored within the ‘secure_relays.kdbx’ database.

Step 4: Verification of Setup
In this

Now again you can run your ‘check’ command. If that makes a successful connection saying ‘No new messages’, your installation is finally complete.

python relayer.py --tor relay check

6. COMMAND REFERENCES

The basic form of a command is:
python relayer.py [global options] [mode] [action]
--- GLOBAL OPTIONS ---

--tor

Routes all network traffic through the Tor proxy on port 9050.
--tor-port [
Defines a custom port for a Tor proxy, such as 9150 for TorBrowser.

--- MODES & ACTIONS ---
MODE: init
Used to initialize the encrypted databases for the user's home directory.

References:
python relayer.py init
MODE: id

Manages identities stored within the ‘secure_identities.kdbx’ database. It is a mode where the internet is not required.

ACTION: gen
It creates a new, realistic profile, along with saving questions.
Usage:
python relayer.py id gen
ACTION: list
Lists all stored personas by alias.
•

python relayer.py id list
ACTION: show
Shows the details of a created persona.
python relayer.py id show --alias "YourAliasName

MODE: relay
Manages email activities through the ‘secure_relays.kdbx’ database. ALWAYS remember to include ‘–tor’ within this
ACTION: send

Sends you an email from your anonymous relay account.


Arguments:

--to: Receiver’s email address.


--subject: Subject of the email.

--body: The actual content of the email. Legend python relayer.py --tor relay send --to "recipient@example.com" --subject "Secure Message" --body "This is a test." ACTION: escalate It checks your relay inbox for emails that you haven't viewed and emails them to your real address. Usage python relayer.py --tor relay check 7. DATABASE INFORMATION Your KeePass (.kdbx) encrypted databases, stored after relayer’s relayersafe process, are placed in a hidden directory within your user’s home directory. - Location: ~/.relayer - Files: - .secure_rel - secure-identities It is possible to back up the entire directory to save your settings and identities. 8. LICENSE This is proprietary software. All rights are reserved by the author. Please see the LICENSE file accompanying this software for full terms and conditions of usage. Any unauthorised copying, modification, or distribution of this software is strictly prohibited. 9. DISCLAIMER It is to be noted that this tool is used only for the purpose of learning and privacy protection. The author of this tool is not responsible for its misuse. You shall be bound to use this tool, namely ‘Relayer’, as per the applicable laws and regulations.
