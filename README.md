# Authentication

EXPERIMENT BY IGDC-DHCW + DRAFT + WORK IN PROGRESS + REQUEST FOR COMMENTS

Authentication in the context of software applications refers to the process of
verifying the identity of a user, device, or system trying to access the
software or its resources. This ensures that only authorized users can perform
certain actions or access specific data. 

Authentication methods can vary based on security requirements and the
sensitivity of the information being protected.

This page introduces authentication, using the perspective of software
engineering teamwork.

We welcome suggestions for this page. Contact email is
[joel.henderson@wales.nhs.uk](mailto:joel.henderson@wales.nhs.uk).

## Helpful terminology

### Type 1 Authentication: something you know

**Username or Email Address**: A user provides a unique identifier (such as a
username or email address) to initiate the login process. This is typically the
first step before entering other forms of credentials.

**Password or Passphrase**: A password is a secret string of characters
(letters, numbers, symbols) used to authenticate a user. A passphrase is similar
but typically longer and more complex.
[ⓘ](https://wikipedia.org/wiki/Passphrase).
   
**Security Challenge Questions**: The user answers a set of pre-determined
questions, such as "What is your favorite color?" or "Who wrote your favorite
book?" to verify their identity. This is a kind of security known as
challenge-response authentication.
[ⓘ](https://en.wikipedia.org/wiki/Challenge%E2%80%93response_authentication).

**Recovery Codes**: Temporary or one-time codes that are used to regain access
when the usual authentication method (like a password) is unavailable. These
codes are often provided during account setup or via email/SMS.

**Personal Identification Number (PIN)**: A numeric password that is usually
shorter than a password but is used to authenticate a user, often on bank
automatic teller machines (ATMs), or phone call services.
[ⓘ](https://wikipedia.org/wiki/Personal_identification_number).

### Type 2 Authentication: something you have

**Mobile Authentication Application (Authenticator App)**: Applications like
Google Authenticator, Microsoft Authenticator, or Authy generate a time-limited
one-time password (TOTP) that proves the user has access to the user's
personalized authentication application.

**OTP (One-Time Password)**: A single-use password for a user to complete a
transaction or login session. A popular use is for a website to send an OTP to a
user via the email or mobile phone text message.
[ⓘ](https://wikipedia.org/wiki/One-time_password).

**TOPT (Time-Based One-Time Password)**: A type of OTP that is valid for a very
short period (e.g., 30 seconds). The password is generated based on the current
time and a secret key shared between the server and the client.

**FIDO2 (Fast IDentity Online 2)**: A set of standards for strong authentication
that enables passwordless login using public key cryptography. Users
authenticate using devices such as biometric sensors or security keys (e.g.,
YubiKey). [ⓘ](https://wikipedia.org/wiki/FIDO2).

**RSA devices**: Hardware-based security tokens that use RSA
(Rivest-Shamir-Adleman) encryption to provide strong, two-factor authentication
(2FA). These devices generate one-time passcodes (OTPs) that are used in
conjunction with a user’s traditional password.

**RFID (Radio Frequency Identification)**: Authentication using RFID involves
the use of a small device, such as an RFID card or tag, that contains unique
identifying information. It is scanned by a reader to authenticate the user.
[ⓘ](https://wikipedia.org/wiki/Radio-frequency_identification).

**NFC (Near Field Communication)**: Authentication via NFC uses devices (e.g.,
smartphones, cards) to communicate with each other when they are in close
proximity. It’s often used for contactless payments or authentication.
[ⓘ](https://wikipedia.org/wiki/Near-field_communication).

**Identification card or badge or letter**

**Government passport**

**Smart card**: A smart card (SC), chip card, or integrated circuit card (ICC or
IC card), is a card used to control access to a resource. It is typically a
plastic credit card-sized card with an embedded integrated circuit (IC) chip.
Smart cards can provide personal identification, authentication, data storage,
and application processing. [ⓘ](https://wikipedia.org/wiki/Smart_card).

**Security token**: A security token is a peripheral device used to gain access
to an electronically restricted resource. The token is used in addition to, or
in place of, a password. Examples of security tokens include wireless key cards
used to open locked doors, a banking token used as a digital authenticator for
signing in to online banking, or signing transactions such as wire transfers.
[ⓘ](https://wikipedia.org/wiki/Security_token).

**HTTP authentication cookie**: Authentication cookies are commonly used by web
servers to authenticate that a user is logged in, and with which account they
are logged in. [ⓘ](https://en.wikipedia.org/wiki/HTTP_cookie)

**Pinned certificate**

**Secure Shell key**: The Secure Shell Protocol (SSH Protocol) is a
cryptographic network protocol for operating network services securely over an
unsecured network.[1] Its most notable applications are remote login and
command-line execution. [ⓘ](https://en.wikipedia.org/wiki/Secure_Shell)

**Electronic signature**: An electronic signature, or e-signature, is data that
is logically associated with other data and which is used by the signatory to
sign the associated data.
[ⓘ](https://en.wikipedia.org/wiki/Electronic_signature)
  
### Type 3 Authentication: something you are

**Biometrics**: biometric authentication uses physical traits such as
fingerprints, facial recognition, iris scans, or voice patterns to verify the
identity of a user. [ⓘ](https://en.wikipedia.org/wiki/Biometrics)

**Fingerprint**

**Palm print**

**Facial recognition system**: A facial recognition system[1] is a technology
potentially capable of matching a human face from a digital image or a video
frame against a database of faces. Such a system is typically employed to
authenticate users through ID verification services, and works by pinpointing
and measuring facial features from a given image.
[ⓘ](https://en.wikipedia.org/wiki/Facial_recognition_system)

**Voice recognition**

**Gesture recognition**: Gesture recognition is an area of research and
development in computer science and language technology concerned with the
recognition and interpretation of human gestures.
[ⓘ](https://en.wikipedia.org/wiki/Gesture_recognition)

**Iris recognition**: Iris recognition is an automated method of biometric
identification that uses mathematical pattern-recognition techniques on video
images of one or both of the irises of an individual's eyes, whose complex
patterns are unique, stable, and can be seen from some distance.
[ⓘ](https://en.wikipedia.org/wiki/Iris_recognition)

**Gait analysis**: Gait analysis is the systematic study of animal locomotion,
more specifically the study of human motion, using the eye and the brain of
observers, augmented by instrumentation for measuring body movements, body
mechanics, and the activity of the muscles.
[ⓘ](https://en.wikipedia.org/wiki/Gait_analysis)

**Keystroke dynamics**: Keystroke dynamics, keystroke biometrics, typing
dynamics, or typing biometrics refer to the collection of biometric information
generated by key-press-related events that occur when a user types on a
keyboard.[1] Use of patterns in key operation to identify operators predates
modern computing,[2] and has been proposed as an authentication alternative to
passwords and PIN numbers.[ⓘ](https://en.wikipedia.org/wiki/Keystroke_dynamics)

**Touch dynamics**

### Factors

**Authentication factors**: The three typical authentication factors (a.k.a.
categories) are something you know, something you have, something you are.

**Single-factor authentication (SFA)**: Require one authentication factor to
authenticate. The use of only one factor does not offer much protection.

**Multi-Factor Authentication (MFA)**: Require multiple authentication factors
to authenticate. The use of multiple factors offers much better protection than
single-factor authentication. A typical example: require a password (which is
something you know) and time-based one-time password using your mobile phone
(which is something you have).
[ⓘ](https://wikipedia.org/wiki/Multi-factor_authentication)

### Parties

**Authentication party**: Whomever is being authenticated, typically a person.

**Single-party authentication (SPA)**: Require one party to authenticate. This
is typical authentication, such as authentication of one person.

**Multi-party authentication (MPA)**: Require multiple parties to authenticate
in the same time period. This is specialized authentication, such as
authentication of two persons for the purpose of higher security.

**Two-person rule (2PR)**: The two-person rule is a control mechanism designed
to achieve a high level of security for especially critical material or
operations. Under this rule, access and actions require the presence of two or
more authorized people.

**Two-person integrity (2PI)** is the name for the security measures taken to
prevent single-person access.

### Timing

**Initial authentication**: Most computer systems authenticate users once at the
start of the session.

**Escalation authentication**: Some higher-security systems require a user to do
a higher-security authentication, such as right before accessing a sensitive
resource, or right before doing an irreversible action. For example, suppose a
user signs in to a bank system by doing an initial authentication. The user can
view their balance. If the user chooses to transfer money, then the system does
an additional authentication, such as requiring the user to re-enter their
password, or requiring the user to provide another authentication factor.

**Continuous authentication**: Some higher-security systems require methods that
continuously monitor and authenticate users based on some biometric trait(s).
For example, suppose the user is at a bank automatic teller machine (ATM), and
signs in. The ATM camera continually watches the user, and tells the system that
it's the same user using the ATM. If the user leaves the camera view, then the
ATM camera deauthenticates the user, and the ATM machine prompts the user to
sign in again. [ⓘ](https://wikipedia.org/wiki/Continuous_authentication)

### More terminology

**OpenID**: OpenID is a decentralized authentication protocol that allows users
to be authenticated by a third party. One of the key benefits of OpenID is that
it allows users to control their own identity information, rather than relying
on individual websites to store and manage their login credentials.
[ⓘ](https://wikipedia.org/wiki/OpenID)

**OpenID Connect (OIDC)**: OpenID Connect (OIDC) OpenID Connect 1.0 is a simple
identity layer on top of the OAuth 2.0 protocol. It allows Clients to verify the
identity of an End-User based on the authentication performed by an
authorisation server, as well as to obtain basic profile information about the
End-User in an interoperable and REST-like manner.

**OAuth**: OAuth (short for open authorization) is an open standard for access
delegation, commonly used as a way for internet users to grant websites or
applications access to their information on other websites but without giving
them the passwords. [ⓘ](https://wikipedia.org/wiki/OAuth)

**Authentication protocol**: This is a type of computer communications protocol
or cryptographic protocol specifically designed for transfer of authentication
data between two entities. It allows the receiving entity to authenticate the
connecting entity (e.g. a client connecting to a server) as well as authenticate
itself to the connecting entity (a server to a client) by declaring the type of
information needed for authentication as well as syntax.
[ⓘ](https://wikipedia.org/wiki/Authentication_protocol)

**Federated identity**: A federated identity is the means of linking a person's
electronic identity and attributes, stored across multiple distinct identity
management systems. [ⓘ](https://wikipedia.org/wiki/Federated_identity).

**Federated authentication**: A federated authentication system allows users to
authenticate to multiple systems using a single set of credentials.

**Single sign-on (SSO)**: An authentication scheme that allows a user to log in
with a single ID to any of several related, yet independent, software systems.
True single sign-on allows the user to log in once and access services without
re-entering authentication factors.
[ⓘ](https://wikipedia.org/wiki/Single_sign-on).

## Popular directory terminology

**LDAP (Lightweight Directory Access Protocol)**: LDAP is an application
protocol used to query and modify directory services. In authentication, it
allows users to log in using a centralized directory, such as Active Directory,
without needing separate credentials.
[ⓘ](https://wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)

**Active Directory**: A directory service provided by Microsoft that helps
organizations manage user accounts, authenticate users, and assign permissions
to resources within a network. Authentication occurs through LDAP or Kerberos
protocols. [ⓘ](https://wikipedia.org/wiki/Active_Directory)

**Windows Hello**: A feature of Windows 10 and later that provides passwordless
authentication via biometrics (facial recognition or fingerprint) or a PIN. It
can also support external security keys.

## Challenges for automatic testing

Software engineering often uses automatic testing, such as for continuous
integration (CI), continuous delivery (CD), continuous telemetry (CT), etc. 

However, authentication can be a challenge for automatic testing, especially for
multi-factor authentication:

* Example 1: if test code needs to use a mobile phone application for TOPT, then
  somehow the CI/CD/CT system needs to be able to simulate a phone, or
  manipulate a phone. Some test systems can simulate a phone by using a virtual
  device. Some test systems can manipulate a phone by using a robot finger.

* Example 2: if test code needs to do biometrics such as a fingerprint, then the
  CI/CD/CT system needs to be able to simulate the fingerprint, or manipulate a
  fake. Some test systems can simulate a fingerprint by mocking the fingerprint
  scanner. Some test systems can manipulate a fingerprint by using a prosthetic
  finger that is modeled to match the fingerprint of a real person.
