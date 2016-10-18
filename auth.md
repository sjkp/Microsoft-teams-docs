# Authenticating your Microsoft Teams tab

TODO

You may need basic information or context about the user, team, or company (tenant) to provide a seamless experience.  In particular.  This information can help you:
	• Create or associate resources in your system with the user or team
	• Start an OAuth or similar redirect flow against AAD or other identity provider, without the user being unnecessarily prompted again for their username.  


This information can be used as a hint to AAD when kicking off an authentication flow within your iframe.  If the UPN, tenant ID and existing AAD session cookies are sufficient for you to silently authenticate the user against your service then you can stop here and merrily go about building your experience; otherwise, see User authentication - pop-up flow

TODO

