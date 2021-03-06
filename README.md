# `bibfile_cleaner`
A quick script for bibfile organizing

Do you have a variety of people working from a shared bibtex bibliography file? Has that bibfile gotten somewhat messy with unsorted entries, varied capitalization standards, and even a few duplicate bib entries lurking to trip you up during your next submission deadline? Worry no more! This script will help impose the order you crave on those supporting files you rarely look at.  

Usage:  

    python cleanbib.py bibfile.in bibfile.out  

This Python 2.x script reads the entire input file before opening the output file, so you can use the same file for input and output. Beware, however, that it will clobber whatever output file you give it, so if there is some unforeseen crash, the output file will be unusable. Any files with duplicate IDs will be listed to stdout after sorting everything.

Features:  
* Alphabetizes bibfile  
* Converts keys to lowercase  
* Enforces curly brace delimiters around each value of a key-value pair (replaces existing delimiters)  
* Lists duplicate IDs  
* Standardizes author names to {LAST}, FIRST  

Also includes `alignbib.py`, which standardizes bib ID format in preparation for merging a new bibfile into an existing bibfile.

Usage:

    python alignbib.py bibfile.in bibfile.out  

Default ID format is `last1(|last2|etal)year3year4`. Also removes `file` key-value pairs from bibfile.in in order to remove Mendeley information (if it exists) from the other file.

To merge two bibfiles:

    python alignbib.py bibfile.in bibfile.out  
    cat bibfile.out >> bibfile.old  
    python cleanbib.py bibfile.old bibfile.new  
