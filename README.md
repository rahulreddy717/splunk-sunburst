#sunburst-splunk

Download splunk and install it
[splunk](https://download.splunk.com/products/splunk/releases/7.3.2/windows/splunk-7.3.2-c60db69f8e32-x64-release.msi)

During the installation it will ask you for a username and a password. Put in some username and password but make sure you remember it.
Now this installation should start the splunk local server on your computer on port 8000.

Navigate to C:\Program Files\Splunk\etc\system\local.
Create a new file called web.conf
Enter the following configurations in the file:
[settings]
minify_js = False
minify_css = False
js_no_cache = True
cacheEntriesLimit = 0
cacheBytesLimit = 0
enableWebDebug = True

Navigate to you installation directory, for example (C:\Program Files\Splunk).
Navigate to the bin folder and adminstrator command prompt.
Enter the command splunk start.
This should start the splunk server. (It takes some time, so hang on)
IMPORTANT make sure nothing is running on port 8000. Or you can google and find out how to change the splunk port.

Clone this project in C:\Program Files\Splunk\etc\apps
After cloning navigate to \appserver\static\visualizations\radial_meter
Open Adminstrator command prompt and enter the following commands.

npm install

"C:/Program Files/Splunk/bin/splunk" cmd node ./node_modules/webpack/bin/webpack.js

This should compile your code.
Go to localhost:8000
Enter the credentials you entered during the installation.
Click on the search button on the left hand side.
Enter the following in the input box:

| makeresults count = 60
| stats count

Click on visualisation and then on a chart with the name radial-meter.
You'll see the chart.
