# <center>An Object Oriented Approach To Web-Scrapping</center>
### Here we're scrapping friend's photos from facebook.
### But there are some common methods/ classes which can be used to scrape any site with minor changes
<br>
This notebook is divided into following classes
## Common "Util Method" class for all scraping functions
### It has the below methods
<ul>
    <li> <b>Get Session</b>: Creates and returns a new session. Also adds User Agent header so that request doesn't look like coming from a bot</li>
    <li> <b>Get Existing Session Cookies</b>: It checks if a session exists already on the basis of cookie provided and uses the same instead of getting new</li>
    <li> <b>Save Cookie</b>:Saves a cookie at the path so that session can use this cookie instead of creating a new session everytime</li>
    <li> <b>Delete Session:</b> Deletes the associated cookies and the session</li>
    <li> <b>Make Request:</b> Makes a get/ post request. Returns <strike>yummy</strike> beautiful soup (:P) if asked for!</li>
    <li> <b>Download Photos:</b> Makes a get request to get image stream and download at specified path</li>
</ul>

## Class To Login to Base site
### It has the below methods
<ul>
    <li> <b>Constructor</b>: Takes username and password (But never saves them! Makes a call to login and deletes them!) Constructor is also responsible for getting a new or an existing session if cookie is already present.</li>
    <li> <b>Get Login Form Data</b>: Creates form data to login</li>
    <li> <b>Logout</b>: Makes a call to utility function clear cookies to delete the session.</li>
    <li> Also has a class variable, <b>Util</b> to have an instance for <b>Utility Methods</b></li>
  </ul>
  
  ## Class for getting the profile to scrape
### A Child class for Login
### It has the below methods
<ul>
    <li> <b>Constructor</b>: Takes username and password and passes it to super class.</li>
    <li> <b>Add Base Url</b>: A method to add base site url</li>
    <li> <b>Create Profile Url from Scratch</b>:If this class is being provided a user name instead of url, this method generates url</li>
    <li> <b>Get Username From Url:</b> If this class is being provided a url instead of user name, this method generates username</li>
    <li> <b>Prepare Profile Url:</b> Appends basic details to profile url or creates a profile from scratch if username is given</li>
    <li> <b>Get Profile:</b> Gets the requested profile's beautiful soup internally calling other methods to generate the same</li>
</ul>

## Class for taking the scraping actions on profile
### A Child class for Profile
### It has the below methods
<ul>
    <li> <b>Constructor</b>: Takes username and password and passes it to super class.</li>
    <li> <b>Download Multiple Users Photos</b>: Takes a list of user ids/ user urls to scrape their photos, which iterative calls method for scraping single profile</li>
    <li> <b>Download User Photos</b>:Gets the profile from parent class and uses beautiful soup to generate set(for uniqueness) of urls of the user photos</li>
    <li> <b>Get Image Url From Soup:</b> It is used to get image urls from soup which is further giving to utility methods download images method to save it to your local system</li>
    <li>Hey wait, here's a bonus parameter too!</li>
    <li><b>Restricting number of images per user:</b> Since social network sites are full of images, we can restrict images per user.</li>
    </ul>
<br>
p.s., This project is purely developed for <b>learning purposes</b> and is intended to be used for same.
<br>p.p.s., <b>Avoid using on google colab</b>, probably due to some ip restrictions/ proxies, you won't be able to scrape there. But yeah, you may try. Either you'll end up banging your head on the wall or enlighten us all with a solution! :P
### Happy <strike>Scraping</strike> Learning! 
## Do refer to legal risks involved in scraping and do it at your own risk
