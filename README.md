# Entry-Task
## To make a static copy of a dynamic website using open source tools

## Objectives

1. To create a static copy of [this website](https://ukiericoncretecongress.com/Home/).
1. Use only Open Source tools.
1. Check if all links work offline (except for external links).
1. Target time 8:00 P.M. 20/7/22.


## Understanding the problem

To convert a **dynamic** website to a **static** one, we first need to understand what these terms mean in the first place

**Dynamic** websites are those sites, whose content will change according to factors like,
* person trying to access the site
* time in the day
* device
Examples of dynamic website are YouTube and WordPress, the sites will appear different to diffenrent users. YouTube may recommend history documentries to a person, while recommending standup comedy videos to another.

**Static** websites on other hand remain unchanged by the above mentioned features. It is important to remember that such websites, can be interactive and can use HTML, CSS, JavaScript. Only difference is that such websites, cant change there contents.

## Advantages of converting websites to static
We can use this to save and archive websites, by this process we can save content like: images, links, interface of the website in offline mode, while perserving the fucntionality.

## Solving the problem.
After reserching the internet for some time, the i came to the conclusion that wget is the way to go.
***wget*** is an opensource GNU computer program, that is used to retrive content from webservers. A dynamic website is hosted on a webserver. We can use this software to create an offline copy of a website in static form.

### Installing wget
wget is a free and open source program. It can be downloaded [here](https://eternallybored.org/misc/wget/), it has both .zip and .exe binaries. Downloaded .exe file from here and extracted it. Then I copied the wget.exe to system32 folder, (which was already added to path in my device).


### Trial 1

Then i executed the following batch script:
```
cd desktop
mkdir task
cd task
wget -k -K -E -r -l 10 -p -N -F -H https://www.ukiericoncretecongress.com/Home
```
### Problems faced

1. wget is a little confusing, doing something like the above took alot of trial and error.
1. Links of the home page don't connect to other pages, even if they are downloaded properly
1. There are some issuse with the website as well, for some reason I was unable to do the above task while connected to college Wifi.

---

### Trial 2

Batch script
```
cd desktop
mkdir task
cd task
wget -k -K -E --adjust-extention -r -l 2 -t 2 -p -N -F -x https://www.ukiericoncretecongress.com/Home
```
### Problems resolved from previous trial

1. -k was responsible for making the links functional, but it works only when the complete website have been downloaded. I used to manually termiante the operation, when it exceeded more than 10 failures. This stopped -k form working. To resolve this issure I reduced to number of tries to 2 as well as recursions to 2. The website was downloaded with all the relevent content within a few minutes.


This code creates a folder named 'task' on desktop and startes the wget program with different attributes explained below:
*  -k,  converts links after the complete website is downloaded (after the contents are downloaded it makes them suitable for viewing locally)
*  -K,  before converting file X, back up as X.orig (this backs up a file as X.orig before converting it)
*  -E   save HTML/CSS documents with proper extensions (it converts file extentions to .html if they are not in .html, **helps to make the downloaded website static**)
*  -r   specify recursive download (it will retrive a page first, and then follow all the links on the page and repeat the same process recursivly on those pages)
*  -l   maximum recursion depth (specified here 10)
*  -p   get all images, etc. needed to display HTML page (helps download all the images and media on the pages, .jpeg, .png, .gif)
*  -N   don't re-retrieve files unless newer than local (don't download file if server version older than local version)
*  -F   treat input file as HTML (treates downloaded pages as HTML pages)
*  -H   create host directories (is a directory option that tells wget to structure directories)
*  -t   set number of retries to number specified (retries to download if it fails)
*  -x   force creation of dir (organises content of download)

Above mentioned data can be accessed by following commands
```
wget --help
```
To get the contents in a txt file
```
wget --help >> help.txt
```
On execution of this batch script, a folder will be created that will contain offline version of our dynamic website in static form.

### Unresolved issues
The wget fails to connect, when device is connected to the college WiFi.
