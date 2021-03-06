# Common Errors

## PHP Mongo Extension Error

Some users that have not used MongoDB on thier system before may experience errors when trying to install the `DevMarketer/LaraMongo` extension. The error commonly looks like this:

![the requested php extension mongodb is missing from your system](https://user-images.githubusercontent.com/537329/31060511-720ca466-a6d2-11e7-8e2d-6d2e6d6bf3b3.png)

This is easy to fix. I will walk you through it.

### 1. Why are you getting this error?

This composer error comes because composer knows that the LaraMongo package is a wrapper for the MongoDB PHP Library that is maintained by MongoDB themselves. That library is actually a wrapper of the low(er) level driver extension that is maintained by PHP. Have you heard of trickle-down economics? Well this is trickle-down dev headaches.

Basically if you can enable the MongoDB extension your problem will be solved. Now PHP MongoDB Driver will work, which means that the MongoDB PHP Library will be happy, which means that LaraMongo will be happy, which means comoser will be happy.

### 2. See If the MongoDB Extension is Installed

Before we continue we will need to check if you have the MongoDB php extension installed. You can do this easily in your terminal with the following command:

    php -m

This will make a long list of extensions you have installed. Scroll through to see if you see a line that says `mongodb`. (The list is in alphabetical order)

**Note: the `mongo` extension is not the same as the `mongodb` extension. You need the `mongodb` one.**

If you do not see `mongodb` on the list, then you **DO NOT** have mongodb extension installed on your system. You need to install it!

### 3. Install mongodb Extension

The way you install the mongodb extension varies depending on your operating system and php version. It is best to follow [these instructions and comments on the PHP.net site](http://php.net/manual/en/mongodb.installation.php) to install the extension.

Once it is installed, run `php -m` again and make sure that `mongodb` is on your list now.

### 4. Still not working?

You will need to reboot PHP or just reboot your computer for the new change to take effect.

If you run a `phpinfo()` page, then you should have a whole section dedicated to MongoDB and a quick `ctrl + F` for "mongo" should yield many results. If you don't have any mentions of Mongo then it has not successfully installed the `mongodb` extension or your PHP install hasn't recognized it yet. This usually is resolved with a reboot.

## Find Your PHP.ini

Looking for your `php.ini` file? This is easy to find.

    php --ini

This should return 3 lines of information. Long story short, you want the middle one, it is your config file for php.

    Configuration File (php.ini) Path:  /usr/local/etc/php/7.0
    Loaded Configuration File:          /usr/local/etc/php/7.0/php.ini
    Scan for additional .ini files in:  /usr/local/etc/php/7.0/conf.d
