# Best practices for mitigating ways calendar spam occurs

## Mitigating spam on source system
User accounts could be compromised by malicious actors or free hosting providers could be abused with bots signing up for free accounts.  These accounts are then used to create calendar spam events.  The calendar system uses templating to send an email invitation with the calendar event attached and the event content will also be inserted into body of the email.  The "source" hosting provider can take steps to detect and mitigate this internal abuse on the calendar system and the email system.

### using calendar systems
- abuse detection for frontend usage (network, user agent, click rate/path, ...)
- check event content (subject, description, recurrence, links, ...) for typical spam pattern before creating the event or email invitation
- actions if potential spam detected? not sending? general error? alert end-user? rate limiting? CAPTCHA?

### using smtp
- abuse detection for smtp access (network, DNSBL, ...)
- check email for spam pattern using standard email anti-spam scanning applications.  Are all anti-spam scanners capable of parsing calendar events?
- actions if potential spam detected? not sending (reject? discard?) using black mailer for sending? 

## Mitigating spam on receiving system
Spam events are typically recieved by recipients in two ways: via email from an external system, or directly from another account (bot or compromised) within the calendar system.  Events from internal accounts may propogate natively within the calendar system or they may propogate over email, depending on implementation.  The "recieving" hosting provider can take steps to detect and mitigate this "external" abuse on the calendar system and the email system.

### mail system
- abuse detection for receiving email (network, mail header/structure, ...)
- check email for spam pattern using standard email anti-spam scanning applications, DNSBLs, URIBLs, etc.  Are all anti-spam scanners capable of parsing calendar events?
- check sender From address reputation (subscribe to InfoSec feeds of known malicious addresses, organiser on white list, ...)
- actions if potential spam detected? not accepting (reject? discard?) spam folder? Problem is there is no interaction with calendar system, so the recipient has no way to handle false positives. 
- manual insert into calendar option in app/web app/... for all events (those inserted automatically and events, where this is not done because of the mentioned reasons)
- insert into a different "junk mail" calendar that offers the end-user additional security controls?

### interaction mail / calendar system
- parse email for event
- check event content for spam pattern (subject, description, recurrence, links, ...)
- check settings for insert (e.g. only automatic insert for organisers on a white list/personal address book)
- actions if potential spam detected? not inserting. deactivate notifications. 

### calendar system
- store information about how event was inserted into the users calendar? Mail ID?
- delete option for unwanted events -> mark as spam.  Does ARF need to be extended for calendar abuse reporting?
- actions if spam is identified by user? Feedback loop if MailID and original mail is still available

## other ways calendar spam can occur

### subscribing to shared calendars containing malicious events
- shared calendars could also include malicious events.  popular calendars could be target for phishing / takeover by spammers.
- single events can not be deleted if shared read-only. More robust controls may be needed for calendar subscribers.
- unsubscribing the specific calendar can solve the problem (all or nothing)

### iTIP
- iTIP implementators should consider anti-abuse options 
