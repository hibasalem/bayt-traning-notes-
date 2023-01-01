

## HTTP 
Hypertext Transfer Protocol   

is an application-layer protocol for transmitting hypermedia documents, such as HTML. It was designed for communication between web browsers and web servers, but it can also be used for other purposes.


## HTTPS 
Hypertext Transfer Protocol Secure (https) is a combination of the Hypertext Transfer Protocol (HTTP) with the Secure Socket Layer (SSL)/Transport Layer Security (TLS) protocol.

## Why HTTPS matters 

HTTPS protects the integrity of your website      
HTTPS protects the privacy and security of your users   


HTTPS prevents websites from having their information broadcast in a way that’s easily viewed by anyone snooping on the network. When information is sent over regular HTTP, the information is broken into packets of data that can be easily “sniffed” using free software. This makes communication over the an unsecure medium, such as public Wi-Fi, highly vulnerable to interception. In fact, all communications that occur over HTTP occur in plain text, making them highly accessible to anyone with the correct tools, and vulnerable to on-path attacks.    

With HTTPS, traffic is encrypted such that even if the packets are sniffed or otherwise intercepted, they will come across as nonsensical characters.

## How does HTTPS work?

HTTPS uses an encryption protocol to encrypt communications. The protocol is called Transport Layer Security (TLS), although formerly it was known as Secure Sockets Layer (SSL). This protocol secures communications by using what’s known as an asymmetric public key infrastructure. This type of security system uses two different keys to encrypt communications between two parties:   

The private key - this key is controlled by the owner of a website and it’s kept, as the reader may have speculated, private. This key lives on a web server and is used to decrypt information encrypted by the public key.   
The public key - this key is available to everyone who wants to interact with the server in a way that’s secure. Information that’s encrypted by the public key can only be decrypted by the private key.    


## How does a website start using HTTPS?
Many website hosting providers and other services will offer TLS/SSL certificates for a fee. These certificates will be often be shared amongst many customers. More expensive certificates are available which can be individually registered to particular web properties.

## SSL 
SSL stands for Secure Sockets Layer     
a security protocol that creates an encrypted link between a web server and a web browser.

An SSL certificate is a small digital certificate that is used to authenticate the identity of a web site    

(also known as a TLS or SSL/TLS certificate) is a digital document that binds the identity of a website to a cryptographic key pair consisting of a public key and a private key. The public key, included in the certificate, allows a web browser to initiate an encrypted communication session with a web server via the TLS and HTTPS protocols. The private key is kept secure on the server, and is used to digitally sign web pages and other documents (such as images and JavaScript files).   
also includes identifying information about a website, including its domain name and, optionally, identifying information about the site's owner. If the web server's SSL certificate is signed by a publicly trusted certificate authority (CA), like SSL.com, digitally signed content from the server will be trusted by end users' web browsers and operating systems as authentic.

## TLS
Transport Layer Security (TLS) is a cryptographic protocol designed to provide communications security over a computer network. The protocol is widely used in applications such as email, instant messaging, and voice over IP, but its use in securing HTTPS remains the most publicly visible.    

The TLS protocol aims primarily to provide security, including privacy (confidentiality), integrity, and authenticity through the use of cryptography, such as the use of certificates, between two or more communicating computer applications. It runs in the presentation layer and is itself composed of two layers: the TLS record and the TLS handshake protocols.    

TLS is an improved version of SSL. It works in much the same way as the SSL, using encryption to protect the transfer of data and information     



SSL (Secure Sockets Layer) and its successor, TLS (Transport Layer Security), are protocols for establishing authenticated and encrypted links between networked computers.    

## OWASP

Open Web Application Security Project     
an online community that produces freely-available articles, methodologies, documentation, tools, and technologies in the field of web application security.    

OWASP Top 10 is the list of the 10 most common application vulnerabilities. It also shows their risks, impacts, and countermeasures. Updated every three to four years    

- Injection
  happens when an attacker sends invalid data to the web application with the intention to make it do something that the application was not designed/programmed to do.

- Broken authentication
  can allow an attacker to use manual and/or automatic methods to try to gain control over any account they want in a system – or even worse – to gain complete control over the system.

- Sensitive data exposure
  one of the most widespread vulnerabilities on the OWASP list. It consists of compromising data that should have been protected

- XML external entities (XXE)
  a type of attack against an application that parses XML input. This attack occurs when XML input containing a reference to an external entity is processed by a weakly configured XML parser

- Broken access control

- Security misconfigurations

- Cross site scripting (XSS)

- Insecure deserialization

- Using components with known vulnerabilities

- Insufficient logging and monitoring

## AJAX Security Cheat Sheet

#### Client Side (JavaScript) 

- Use `.innerText` instead of `.innerHTML`

- Don't use `eval()`, `new Function()` or other code evaluation tools

- Canonicalize data to consumer  , When using data to build HTML, script, CSS, XML, JSON, etc. make sure you take into account how that data must be presented in a literal sense to keep its logical meaning.

- Don't rely on client logic for security (number of browser plugins are available to set breakpoints, skip code, change values, etc. Never rely on client logic for security)

- Don't rely on client business logic 

- Avoid writing serialization code

- Avoid building XML or JSON dynamically

- Never transmit secrets to the client

- Don't perform encryption in client side code Use TLS/SSL and encrypt on the server

 SSL/TLS encrypts communications between a client and server, primarily web browsers and web sites/applications. SSL (Secure Sockets Layer) encryption, and its more modern and secure replacement, TLS (Transport Layer Security) encryption, protect data sent over the internet or a computer network.
 
Don't perform security impacting logic on client side

#### Server Side

Use CSRF Protection (Cross-Site Request Forgery Prevention)

Protect against JSON Hijacking for Older Browsers  , (Always have the outside primitive be an object for JSON strings)

Avoid writing serialization code Server Side 

Services can be called by users directly

Avoid building XML or JSON by hand, use the framework

Use JSON And XML Schema for Webservices (You need to use a third-party library to validate web services.)

## Content Security Policy (CSP)

is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross-Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft, to site defacement, to malware distribution.    
To enable CSP, you need to configure your web server to return the Content-Security-Policy HTTP header. (Sometimes you may see mentions of the X-Content-Security-Policy header, but that's an older version and you don't need to specify it anymore.)     
Alternatively, the <meta> element can be used to configure a policy

## CORS

Cross-Origin Resource Sharing (CORS)

