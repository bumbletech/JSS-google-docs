google-docs
===========

Libraries and functions used within Google Docs

Now with a function to pull JSON data from JAMF's Casper JSS API!

To do this, open the script editor in Google Sheets using the Tools > Script Editor menu item. Then copy-and-paste the ImportJSON code.gs contents, be sure to set the "user" and "password" variables for your environemtn. Use File > Save to save the script. You should then be able to use ImportJSON within your spreadsheet.

You can use the fuction ImportJSONJSS like any other google sheet function.

For example
```
=ImportJSONBasicAuthentication("https://your.jss:8443/JSSResource/mobiledevices/serialnumber/YOURSERIALHERE", "/mobile_device/general/id", "noHeaders")
```
Woould give you the JSS ID of that mobile device?

Why would this be helpful?

I've used to to help keep track of known devices as we enroll into Casper. I have a static list of iPads including their serial numeber, and use this funciton to reference that serial number with a formula like:
```
=iF(ISERROR(ImportJSONBasicAuthentication("https://your.jss:8443/JSSResource/mobiledevices/serialnumber/" & A2, "/mobile_device/general/serial", "noHeaders")),"No","Yes")
```
If an iPad isn't enrolled in the JSS, the formula prints "No" and for enrolled devices "Yes". It's a pretty easy way to keep track of things with resorting to exports and VLOOKUPS.
