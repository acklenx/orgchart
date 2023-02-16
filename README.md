# OrgChart
Vanilla Javascript Organizational Chart - no dependencies

This is a simple org chart with not a lot of bells and whistles. There are _no required external dependencies_. There is not a build file.  This cannot be imported or installed.  You can however copy one file, edit it to point to your data source and be done (assuming your data is in the supported format).  This org chart is drawn with simple native template literals.  The templates are all included script tags inside the index.html file.  There are not many of them. They are just html.  Some do call a javascript helper function to format their data.  That should not be required, but it is convenient, if you need it.

The minimum working version consists of one index.html file with all the javascript and css required inline and one data.js file. There are optional other files that are not required for the org chart to function, but make it look and behave a little nicer. A service worker is included with an appropriate manifest file and icons to pass all PWA checks.  Photos are the nicest easy-add, if you have them. They really help the org chart come to life. Included here are sample photos that at present aren't even sized appropriately (this will reduce the Lighthouse - BEST PRACTICES score by 8 points).

This page is set to NOT be indexed by default. If you include PII data for your organization, you probably don't want bots to crawl the org chart and get names, phone numbers, and email addresses for your entire organization.  That would be bad.  You should use proper authentication and authorization controls for this org chart and your data.  But at a minimum I have set the page to not be indexed by default. That will automatically reduce the Lighthouse - SEO score by 10 points to a 90. Still green, but not a 100 (but for good reason).

**index.html** contains all script and css except for the data.js file.  Each functional area of script is broken out into its own script tag with the ID attribute indicating what the script is used for.

**data.js** is a simple javascript object.  The included file has around 600 fictitious people in it.

**LICENSE** MIT ftw!  Use this as you see fit, but please include the license (you know, with my name in it) if you use it.  

**serviceWorker.js** is a complete service worker definition.  On mobile devices in particular you will be able to save the page to your device and it will work completely offline.  It does include the default image in the assets along with a google font, Manrope.  Combined with the serviceworker_for_PWA script and the meta tags in the index.html file this will generate a perfect Lighthouse PWA score. If you're not interested in a WPA you should delete the entire serviceworker_for_PWA script since it tries to make a reference to the serviceWorker.js file that won't load if you don't have it.   The meta tags are good to keep around and shouldn't cause a problem if you remove the PWA.

**manifest.json** is required for the PWA and service worker.  If you don't want the PWA you should delete this too.  But really it's just nice to have offline mode available.

**images/** includes the two required PWA images size required for Android and iOS.  They are both org chart images and at least one is maskable as required.

**photos/** is a directory where you can put your photos of your organization.  Photos by default should be named <userID>.jpg  This can obviously be changed.  Because the sample data supplied is fake, the user id is the username portion of each person's email address.  The sample CEO Isabella Gray's email address is isabella.gray@example.com, her id is isabella.gray, and her photo is found that the url /photos/isabella.gray.jpg but in practice it should not be PII data, which presumably YOUR userIds are not.

**photos/_default_.webp** is a default missing photo picture. If you use photos, it's nice to have everything spaced the same. Without any photos this photo and reference should be removed

**photos/50x50/** is a default thumbnail size for photos. Everything in the parent directory is included here, but should be resized to 50 pixels by 50 pixels.  Might not be used at the time of this writing.  The is a getPhotoUrl() helper that takes a second parameter that is the size of the photo.  That function could, in theory, call a resizer proxy... it's just not at the moment.

**favicon.ico** is simple to put a delightful little org chart icon in your bookmarks should you choose to bookmark a site where this is deployed. Very not required, but 100% requested by browsers when they load your page.