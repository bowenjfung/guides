Title:	frustration review  
Author: bowen j fung
BibTeX: lib

## Citation workflow
I want to be able to do a couple of things when writing academically.

1. Insert citekeys from a library on the fly.
2. Automatically format and reformat these depending on journal demands.
3. Use plain text, but (sigh) retain the ability to convert to Word if PI  / journal demands it

Solution:
1. Use Zotero and the Safari Zotero connector to build a library of citekeys and quick copy them into documents.
2. Run through the pandoc filter, pointing to my entire (autoupdating) Zotero library as a .bib file:

	```pandoc --filter pandoc-citeproc writing+citations.md --bibliography library.bib --csl apa-old-doi-prefix.csl```\
then copy and paste the html output back into iA Writer.
  
3. Use iA Writer and write in markdown, using built in conversion (or pandoc conversion if -> LaTeX)

Example: here is some text and then a single citation [@abler2005]


## Other methods

this command seems to approximate the ideal output:

	pandoc --filter pandoc-citeproc test.md --bibliography lib.bib --csl apa-old-doi-prefix.csl -o test2.md -t markdown-raw_html-citations-native_divs-native_spans

or straight to pdf:

	pandoc --filter pandoc-citeproc --bibliography=paper.bib --variable classoption=twocolumn --variable papersize=a4paper -s paper.md -o paper.pdf


# References
