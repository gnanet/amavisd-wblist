# WBList Version 0.01B 

THIS IS BETA SOFTWARE PLEASE TREAT IT AS SUCH.

I, James Bourne, am in no way responsible for any harm that may come to any
computer system due to any use of this software.  Please consider using this
software in a test environment until you are sure it meets your requirements
and that it will not delete all of your files and empty all of your bank
accounts...  It shouldn't do these things but I won't be responsible for
your stupidity if it does.

I may remove the above statement at some point, but that still won't make me
any more responsible for your stupidity.  Thanks but I'm stupid enough all
on my own.

Copyright (C) 2008 James Bourne <jbourne@hardrock.org>

# What is this anyway?

This is a web based interface to the amavisd-new policy database.  I'm tired
of having to explain to people why their mail is dropping into their spam
mailbox so now I can show them.

If you don't run amavisd-new, you really don't need this software.  Honestly
you don't.  If you insist on emailing me because you are having problems
with the software and you're not running amavisd-new, I can't help you.  See
a medical professional, they may be able to help with some of those new
patented medicines they have available.

The interface is really crude right now.  I wanted to first do functionality
then I will work on the interface.  I'm not an interface designer so if I
never get to it, that's why.  See the comment about patented medicines above
if the design gives you a headache...

## Requirements 

1) you have to be running amavisd-new.  I use version 2.5.3, I'm sure it
   will work with 2.5.2 though.
2) You have to be running a web server, I recommend apache.
3) Your webserver must be able to run PHP scripts and have the php mysql
   module installed.
4) You need to be running MySQL for any of the above to work.
5) You have to run your amavisd-new lookups against this very same mysql
   database, otherwise all of this is completely pointless.  Follow the
   README.sql-mysql from the readme files of amavisd-new.
6) Oh, and since this is a web based application, you'll need a web browser.
   links will work, as will lynx, or emacs, or anything you want really.  It
   has to be able to talk http to a web server.  You can even use netcat if
   you are really really smart and have nothing better to do with your time
   then input forms key=value pairs by hand.

## Installation instructions

1) Untar this tarball onto your web server.  I personally use an SSLd server
   and place it within a passworded directory but if you want to let any
   fool change your amavis filtering that's your doing.  I would recommend
   passwording it.

2) Change the file php/defines.php to point it at your amavisd-new database,
   the same database of course that your amavisd-new installation does
   lookups against.  This entire exercise will be utterly futile unless you
   are doing at least that.  If you don't already have a database setup or
   if you want to use a test database (see my recommendations at the top of
   the file) use the amavis-tables.mysql file for the basic table layout.

3) Point your web browser at your installation location and see if it lists
   anything.  If not, try adding a sender as that is the easiest form to
   complete.

# Operation

Basically it works like this:

1) You define a policy first.  This defines how the mail will be recieved. 
   Anything left blank or NULL will use the defaults in /etc/amavisd.conf.

2) Once you have an acceptable policy, add a receiver that uses this policy. 
   Each receiver will have a policy defined.

3) Next add a sender (this is a person at a remote site).

4) Add a wblist entry, basically relate your receiver to a sender and how
   that mail is handled.  A score will add to the resultant score like the
   soft whitelist table in /etc/amavisd.conf.  W will whitelist, B will
   blacklist and depending how you have your blacklist configured look at your
   maillogs for a "discard" line.  I like discard lines in my mail logs.

5) Search can search all just by clicking on the button.  That's easy.

6) Yes it's crude but it is functional.  It does what it needs to do.  Once
   I know this is working right I will work on the interface.  
