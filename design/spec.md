# Captive Portal Design Spec

## A captive portal is detected but not logged in

Display status bar indicator indicating the network requires a login as shown in
Figure 1. Pressing "Open Login Page" will open a new tab and display the login
page. Pressing the close button will close the status bar for all tabs in all
windows.

![](status.bar.open.login.png)

**Figure 1:** Login prompt with a status bar.

Upon opening a new tab, the user will be presented with the login page for the
captive portal instead of the usual new tab behaviour. This is shown in
Figure 2.

If the user wishes to open the new tab page, they can do so with the button in
the status bar shown. Pressing "open new tab" should open the usual new tab
page. This status bar should be tab specific unlike the one shown in Figure 1.

![](wifi.login.new.tab.png)

**Figure 2:** Captive portal login replaces new tab.
