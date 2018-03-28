# Way calendar spam takes and possible best practices for each part

## sending
### using calendar systems
- abuse detection for frontend usage (network, user agent, click rate/path, ...)
- check event content (subject, description, recurrence, links, ...) for typical spam pattern before creating email
- actions if potential spam detected? not sending? general error?
- calendar system uses templating for creating email with calendar attachement -> content will also be inserted into body of email

### using smtp
- abuse detection for smtp access (network, ...)
- check email for spam pattern
- actions if potential spam detected? not sending? using black mailer for sending?

## receiving
### mail system
- abuse detection for receiving email (network, mail header/structure, ...)
- check email for spam pattern (organiser on white list, ...)
- actions if potential spam detected? not accepting? spam folder? no interaction with calendar system. 
- manual insert into calendar option in app/web app/... for all events (those inserted automatically and events, where this is not done because of the mentioned reasons)

### interaction mail / calendar system
- parse email for event
- check event content for spam pattern (subject, description, recurrence, links, ...)
- check settings for insert (e.g. only automatic insert for organiser while list)
- actions if potential spam detected? not inserting. deactivate notifications. 

### calendar system
- store information about how event was inserted into the users calendar? Mail ID?
- delete option for unwanted events -> mark as spam
- actions if spam is identified by user? Feedback loop if MailID and original mail is still available

## other ways

### subscribing to shared calendars containing malicious events
- shared calendars could also include malicious events
- single events can not be deleted if shared read-only
- unsubscribing the specific calendar can solve the problem