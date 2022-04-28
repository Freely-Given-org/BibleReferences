# BibleReferences

Open string definitions for referencing Bible text

There's zero attempt to force this upon anybody, but simply to have something available for those who are looking.

## Background

[Paratext Bible Translation Editor](https://paratext.org/) has a defined reference system for saying things like "See John 3:16 in this Bible version". Because USFM and Paratext are defined by the same groups, this reference system was built into [USFM3](https://ubsicap.github.io/usfm) -- see https://ubsicap.github.io/usfm/linking/index.html. This describes links like "prj:RSV52 MAT 3:1-4" and "prj:GNTSB #article-Ruth" where *prj* stands for project and presumably refers to a Paratext project.

There are a number of limitations of this link format:

1. The link text contains spaces so most libraries will not tokenise the link as a single entity
2. "prj" means nothing outside of Paratext
3. There's no indication of any set of names like "RSV52" and "GNTSB" in the USFM spec, so presumably they are defined by whatever abbreviation was given when the texts/projects referred to were imported (usually as encrypted files) into Paratext
4. The Scripture reference part is defined in the USFM3 spec by the regular expression "[A-Z1-4]{3}(-[A-Z1-4]{3})? ?[a-z0-9\-:]\*", i.e., one or two three-character (UPPERCASE letters or digits 1,2,3,4) book IDs, an optional space, then one or more lowercase letters, digits, or hyphen or colon. Chapter verse references like "3:4" must always use a colon, and verse ranges like "3:4-5" must always use a hyphen. (No mention of chapter ranges.) The optional space seems strange so "MAT3:4" is also allowed -- this spec seems not tight enough for widespread use.
5. There's no specified way to select a word or other smaller unit in a text
6. There's no obligation of the owner of the standard to heed to any non-Paratext requests -- in fact they will almost certainly be summarily rejected if they required any work to be done by the Paratext team
7. This format doesn't work in HTML as the colon can have different meanings there

## Proposal

1. To not have or allow any whitespace within the links
2. To use our forthcoming Bible Codes for Bible IDs -- owners of Bible versions can submit their codes via Issues
3. To use our [Bible Books Codes](https://github.com/Freely-Given-org/BibleBooksCodes) which all start with letters and so can also be used as variable names in most computer languages
4. To try to make use of punctuation unambiguous, e.g., if if a period separates Bible Code from Book Code like "RSV52.MAT" to not also use period in another part of the link.
5. To propose an HTML compatible form for use on websites -- currently every man and his dog uses different links, e.g id="C4V5" or "004-005", etc.
