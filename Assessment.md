# What can be seen?

## sending
- Spammer use real calendaring infrastructure with good reputation to send calendar spam
- first calendar spam seen was send with Google (2016) and current examples are send from Yahoo (2017)
- they might use more systems
- many receiver are within the used system (Yahoo<->Yahoo)

## content
- still very basic
- same description as body of basic spam emails
- no recurrence
- no date in the future

## detection
- still many calendar spam mails are not detected as spam

## remediation challenges
- events detected as spam during delivery
	- reject message
	- junk folder in mail, but not put into calendar
	- put into calendar but mark? quarantine equivalent for calendar?
- events not detected until after delivery
	- delete without cancellation on behalf of users
	- send fbl for original mail if referent exists
	- create and maintain organiser blacklist? on user or system level?

## outlook
- attached ics will not correspond to mail body anymore, to be less detectable
- recurrence
- event dates in the future 
