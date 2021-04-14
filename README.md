General Information:
--------------------

This is a PHP Chat based on LE CHAT v.1.14. An up-to-date copy of this script can be downloaded at https://github.com/DanWin/le-chat-php
The original perl LE CHAT script by Lucky Eddie can be downloaded at [his site](http://4fvfamdpoulu2nms.onion/lechat/) or via a tor2web proxy like [this one](https://4fvfamdpoulu2nms.onion.to/lechat/) if you don't have Tor installed.
If you add your own cool features or have a feature request, please tell me and I will add them, if I like them.
Please also let me know about any bugs you find in the code, so I can fix them.
Now a piece of information about the origin of the name "LE CHAT" copied from the original script:
The "LE" in the name you can take as  "Lucky Eddie", or since the script was meant to be lean and easy on server resources, as "Light Edition".
It may even be the French word for "the" if you prefer. Translated from French to English, "le chat" means: "the cat".

Features:
---------

* Optimized for Tor
* No JavaScript needed
* Cookies supported, but not needed
* Captcha
* Multiple languages
* Members and guests
* Waiting room for guests
* Moderatoral approval of new guests
* Public, member, moderator and admin only chats
* Private messages
* Multi-line messages
* Change font, colour and refresh rate in profile settings
* Autologout when inactive for some time
* Image embedding
* Notes for admins and moderators
* Clone the chat to have multiple tabs
* Kick chatters
* Clean selected messages
* Clean the whole room
* Plain text message filter
* Regex message filter
* And more

Installation Instructions:
--------------------------

You'll need to have php with pdo, pcre, mbstring and date extension, and a web-server installed.
You will also need the pdo_sqlite, pdo_mysql or pdo_pgsql extension, depending on which database you choose.
Optionally, you can install:
- the gd extension for the captcha feature
- the json extension for save/restore
- a memcached server and the memcached extension and change the configuration to use memcached. This will lessen the database load a bit.
- a MySQL or PostgreSQL server to use as an external database instead of SQLite
- the libsodium extension (PHP >= 7.2) for encryption of messages and notes in the database
When you have everything installed and use MySQL or PostgreSQL, you'll have to create a database and a user for the chat.
Then edit the configuration at the bottom of the script to reflect the appropriate database settings and to modify the chat settings the way you like them.
Then copy the script to your web-server directory and call the script in your browser with a parameter like this:
	http://(server)/(script-name).php?action=setup
Now you can create the Superadmin account. With this account you can administer the chat and add new members and set the guest access.
As soon as you are done with the setup, all necessary database tables will be created and the chat can be used.
Note: If you updated the script, please visit http://(server)/(script-name).php?action=setup again, to make sure, that any database changes are applied and no errors occur.

Translating:
------------

Copy `lang_en.php` and rename it to `lang_YOUR_LANGCODE.php`
Then edit the file and translate the messages into your language and change `$I` to `$T` at the top.
If you ever use a `'` character, you have to escape it by using `\'` instead or the script will fail.
When you are done, you have to edit the chat script, to include your translation. Simply add a line with
`'lang_code'	=>'Language name',`
to the `$L` array in the load_lang() function at the bottom, similar to what I did for the German translation.
Please share your translation with me, so I can add it to the official version.
To update your translation, you can copy each new string to your translation file or edit the automated `lang_update.php` script to reflect you language and run it.

Regex:
------

Yes, the chat supports regular expression filtering of messages. As regex tends to be difficult for most people, I decided to give it an extra section here.
Regex is very powerful and can be used to filter messages that contain certain expressions and replace them with something else.
It can be used e.g. to turn BB Code into html, so it is possible to use BB Code in the chat to format messages.
To do this, use this Regex-Match `\[(u|b)\](.*?)\[\/\1\]` and this Regex-Replace `<$1>$2</$1>` and your text will be `[b]bold[/b]` or `[u]underlined[/u]`.
You can also use smilies by using this Regex-Match `(?-i::(cry|eek|lol|sad|smile|surprised|wink):)` and this Regex-Replace `<img src="/pictures/$1.gif" alt=":$1:">`
And now if you enter `:smile:` an image with the smiley will be loaded from your server at `/pictures/smile.gif`.
The following should be escaped by putting `\` in front of it, if you are trying to match one of these characters `/ \ ^ . $ | ( ) [ ] * + ? { } ,`.
I used `/` as delimiter, so you will have to escape that, too. The only options I used is `i` to make the regex case insensitive.
If you want to test your regex, before applying you can use [this site](http://www.phpliveregex.com/) and enter your Regex and Replacement there and click on preg_replace.
If you never used regex before, check out [this starting guide](http://docs.activestate.com/komodo/4.4/regex-intro.html) to begin with regular expressions.

Live demo:
----------

If you want to see the script in action, you can visit my [Tor hidden service](http://danschat356lctri3zavzh6fbxg2a7lo6z3etgkctzzpspewu7zdsaqd.onion/chat.php) or via [my clearnet proxy](https://chat.danwin1210.me/chat.php) if you don't have Tor installed.
Considering this is a hidden service, you should be prepared for the worst case, as people tend to do illegal activities in the Tor network.
