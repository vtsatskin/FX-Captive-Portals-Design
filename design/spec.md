# Captive Portal Design Spec

## A captive portal detected after connecting to a network.

Open the detected captive portal in a new tab in the active window. This can be
seen in Figure 1.

![](wifi.login.auto.tab.png)

**Figure 1:** Captive portal login automatically opened.

## A captive portal is detected but not logged in

Display status bar indicator indicating the network requires a login as shown in
Figure 2. The status bar will be dismissed once the captive portal has been
logged into.

Pressing "Open Login Page" will open a new tab and display the login page.
If the captive portal is already open, switch to the tab.

Pressing the close button will close the status bar for all tabs in all windows.

![](status.bar.open.login.png)

**Figure 2:** Login prompt with a status bar.

Upon opening a new tab, the user will be presented with the login page for the
captive portal instead of the usual new tab behaviour. This is shown in
Figure 3.

If the user wishes to open the new tab page, they can do so with the button in
the status bar shown. Pressing "open new tab" should open the usual new tab
page. This status bar should be tab specific unlike the one shown in Figure 2.

![](wifi.login.new.tab.png)

**Figure 3:** Captive portal login replaces new tab.

## Restoring sessions

If Firefox is starting and the user will be prompted to restore their tabs
(e.g. after a crash), show the restore tabs button along with the captive portal
login to the right of it.

If Firefox is automatically going to open all of the previously open tabs upon
starting, then also display a captive portal login tab.

## Captive portal tampering with SSL connections

If a captive portal is detected and a page with an SSL connection is being
loaded and appears to be tampered with, display a different warning page before
the SSL connection error as shown in Figure 4.

**Figure 4:** TODO: MITM informative page.

## Cycling WiFi Networks

Sometimes a user may cycle wifi networks in order to find a suitable internet
connection. In the process multiple captive portals may be detected. In order
to prevent many tabs being open, if an existing captive portal is already open
overwrite it when a new captive portal is detected.
