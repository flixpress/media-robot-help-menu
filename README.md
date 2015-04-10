# Media Robot Help Menu

Why "Media Robot"?  
Because.

------------

## Wiring it up

The files in the cleverly named `files` folder are all that need to be
uploaded to the server. They create a help menu in the Colorbox modal that
appears when a template has been selected.

They are designed to be run as a hook into the colorbox open event, so add a
call to the `help-menu.js` script to a skin file that opens a colorbox. For
example, using it for its original intended purpose would be to add the
following to `.../Amicable-Black/MegaSkinAT.ascx`:

```javascript

$(document).bind('cbox_open', function(){
  $.get('/path/to/this/file/help-menu.js');
});

```

This repo contains other files which can be altered in the dependencies
section near the top of the `help-menu.js` script. As long as all the url's
match up, it really doesn't matter where all the files are served from.

NOTE: jQuery and jwplayer must be loaded before anything runs.

## The 'other' files

The files in the root directory of this repository are really only helpful
to me. They run a couple node scripts that allow me to keep these files in
version control (as they are getting more complex) and automatically copies
them to the server every time I save.

In theory, you could also use them in Windows, but you'd probably have to
alter the `pathToServer` property in `Gruntfile.js` first.

------------

## Releases

### v0.1.0

Initial commit. I'm not super pleased with the way that the `jwplayer` script
gets loaded into the global scope of `iframe#colorbox`. There has to be a
better way, but for now, it is not worth the time to save one single http
request... There are many more things that can be optimized on Flixpress.com
first.

The disappearing help menu on browser-width resize is bizarre and probably had
best be fixed, though.
