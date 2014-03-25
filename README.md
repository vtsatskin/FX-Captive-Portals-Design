# Handling Captive Portals in Firefox

## Background

When at a cafe or airport, the router man-in-the-middle intercepts the page and
takes over it. There are different types of captive portals (free, timed,
login). There are weird ones which require the tab open or else the connection
ends.

There is no set standard, so detection is difficult.

## Design spec

See [design/spec.md](design/spec.md).


## Detection

Apple, Microsoft and others have a comparison technology coupled with a list of
known whitelisted portals. The algorithm works as follows, a known website is
requested, and if the website differs it's considered a captive portal.

This and many other algorithms are imperfect solutions which can provide false
negatives and false positives. Therefore a design should be created to handle
these erroneous cases.

See [detection.md](detection.md) a more in-depth analysis.

## Tampering of requests

Since these captive portals will essentially intercept requests and alter their
contents, pages served over SSL will report a security warning. This can be
problematic when a user mostly visits secure websites or uses an addon such as
[HTTPS Everywhere][httpsEverywhere]. This causes two problems:

1. The user cannot access the captive portal because it is replaced by an SSL
error.
2. The user is unnecessarily having to deal with a security warning.

[httpsEverywhere]:https://www.eff.org/https-everywhere


## Use Scenarios

### User is on an SSL site and encounters a captive portal
Currently Firefox will display and SSL error because the portal is tampering
with the connection.

### User is on a non-SSL site

Currently the captive portal will inject content into the page.

### OS detects a captive portal

In some OSs (e.g. OSX, Windows, Android, iOS) the system can sometimes detect
a captive portal. Care should be taken to not display the captive portal twice,
one from the system and one from the browser.

If the OS does not detect the captive portal, Firefox should step in and fill in
the gap.

### User does not recognize they are on a captive portal

Some users may not recognize or understand that they are on the captive portal.
Others may not be familiar with the practice at all. The design should attempt
to communicate to the user that they are seeing a captive portal and what a
captive portal is.

### A existing web app is open while a captive is hijacking

If an existing web app (e.g. twitter, facebook) is open in a previous session
and the user connects to a captive portal, their web app may fail to display
and error and break.

### A captive portal is open from a previous visit but no longer needed

### Timed captive portal ends

Some captive portals are timed in the duration they allow the user to access the
internet.

### Captive portal is required to be open

### Limited internet access is allowed before logging in

Some captive portals allow partial access to the internet while the user is not
logged in. For example, checking airline flights at an airport.

### A "restore session" window open on launch

When a user launches Firefox after it crashed and a session restore window is
displayed and is currently connected to a captive portal and has not logged in.

### User has automatic restore on launch

When a user launches Firefox and their tabs are being restored from the last
session and is currently connected to a captive portal and has not logged in.

### The user is cycling wifi networks to find a suitable network

Users will cycle open wifi networks in order to find a suitable network, in the
process they may encounter networks with captive portals. A mix of open tabs
and windows may be open.


## Feature ideas

### Autofill

Use Firefox's form autofill feature to remember captive portal login
information. This can be useful when a user has to authenticate with a portal
several times a day.

### Automatic authentication

Extending the autofill scenario further, if a user has been to a captive portal
before and have authenticated and/or accepted the ToS, the browser should
automatically deal with the steps involved to connecting to the portal.

### Authenticate all devices

If a user has multiple devices that are all on Firefox Sync (e.g laptop and an
android phone) if the user logs into a captive portal on one device, they should
be logged into all other devices to that same network.
