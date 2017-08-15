# fmdocs

**A guidline for documenting FileMaker Scripts and Functions**

FileMaker scripts and custom functions can get complex.  Now that we have JSON the data that gets passed in and out can get very complex and therefor focumenting what goes in and out of scripts can get tricky. We needed a way to clealy and consistantly document our FileMaker code as part of Karbon project.  This repo contains our current itteration on that thinking.

This is a living document. It will change as we get further in,

## Considerations
We did want to reinvent the wheel. We wanted someth that might lend itself to documentation generation. And we wanted it to be as easy as possible to read and to understand.

## Sources
We draw on [jsdoc](http://usejsdoc.org/) and [apidocs](http://apidocjs.com/) as primary material. We landed closer to jsdocs, but addopted some of the ideas from apidcos having to do with example inputs and results. Somebody who is familiar with either of those two style should have no problem understanding fmdocs.


## Example

Script: Create User ( {Party , AccountName} )
```
#/##
 
# Creates a User
 
# @param {object} userData
# @param {string} userData.AccountName
# @param {object} userData.Party the party Object @see Create Party
# @param {string} userData.Party.Id the id of the Party
// Insert Text [ $@example ] [ Select ]
 
 
# @returnSuccess {object} UserData
# @returnSuccess {string} UserData.Id the Id of the New user record
# @returnSuccess {...} other properties
// Insert Text [ $@successExample ] [ Select ]
 
 
# @rreturnError {object} errorData
# @returnError {number} errorData.code the error code
# @returnError {...} other properties
// Insert Text [ $@errorExample ] [ Select ]
 
# @public
# @author Todd Geist
# @version 1 intial working rev
 
# #/
```

## How It works

The "DocBlock" goes from "/##" to "/#".  This is a little different from the source specs since we are forced to use # on any line with a comment.

Tags are denoted with "@". "@param" is a parameter. @returnSuccess is a succesful return value, @returnError is a return when there was an error.

The next value after the tag is the type. It goes inside a "{}"  The next word after that is the name of the thing.  Anything that follows is comments on that tag.
