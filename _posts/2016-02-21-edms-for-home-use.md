---
title: EDMS For Home Use
updated: 2016-02-21 20:05
---

As well as [molify](http://www.mollify.org/), I have been looking into options for Electronic Document Management Systems and sort of refined my requirements. I am going to use this for 2 separate purposes: a placeholder for day-to-day paperwork (bills/administrative/etc) and an entry point for manuals/reference books, the second requiring pretty sound performance to run OCR on documents composed of hundreds of pages.


* Easy to install
* Easy to use: it is intended for home use, I don't need every bell and whistle under the sun and then have to spend hours configuring stuff
* Easy to backup the actual documents: I want to have all my scanned documents somewhere when/if the EDMS fails/breaks/doesn't work out.
* Performance: see above, especially for OCR processing
* Web interface

My experiences so far

* [paperless](https://github.com/danielquinn/paperless) - I did like it and it does a lot of things right even though a) I had to tweak the composer settings file because it couldn't find the docker image, b) the web UI isn't as polished as it could be, c) I first uploaded files without setting the permissions correctly (OCR parsing failed), and couldn't re-upload the files after setting the permissions correctly. The deal breaker was in the end the processing time for a sample 144 pages sample PDF document. Would work for bills, not for reference manuals.
* [Mayan EDMS](http://www.mayan-edms.com/) - Very polished web UI, handles big documents without issues, has a preview of the documents in the search results.

Others to potential look at:

* [Archivista](http://archivista.ch/)
* [LogicalDoc](http://www.logicaldoc.com/download-logicaldoc-community.html)
* [OpenKM](http://www.openkm.com/en/)
* [NemakiWare](http://nemakiware.com/)
* [SeedDMS](http://www.seeddms.org/index.php?id=2)