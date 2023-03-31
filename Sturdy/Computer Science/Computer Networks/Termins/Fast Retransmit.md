
If sender receives 3 ACKs for same data (“triple duplicate ACKs”), resend unacked segment with smallest seq#
Likely that unacked segment lost, so don’ t wait for timeout


- time-out period often relatively long: 
	- long delay before resending lost packet
- detect lost segments via duplicate ACKs. 
	- sender often sends many segments backto-back 
	- if segment is lost, there will likely be many duplicate ACKs

