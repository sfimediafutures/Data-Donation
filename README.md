![Python application](https://github.com/uvacw/osd2f/workflows/Python%20application/badge.svg?branch=main)
<a href="https://github.com/psf/black"><img alt="Code style: black" src="https://img.shields.io/badge/code%20style-black-000000.svg"></a>
# OSD2F: Open Source Data Donation Framework

## Goal

Using OSD2F in conjunction with UiBs SAFE to facilitate a safe and easy-to-operate way to receive GDPR data donation packages from users.
These packages can then be used for media research that sits in line with MediaFutures' values. 
You can specify the files and the whitelist of JSON fields through YAML configuration. 
As such it supports Data Donation Packages of arbitrary format in JSON files (although it assumes they are UTF-8 encoded). 

Consult the [documentation](/docs) folders to read a combination of documentation from the creators of osd2f and MediaFutures, 
which will hopefully give a comprehensive view as to where the project is now and where it should be going, as well as how to potentially get there. 

The docs also contain instructions for local installation, needed for further development on the project. While the front-end of the project is written in norwegian, all code and documentation is written in english.

## Framework Credits:

If you use this tool, please cite the paper:

*APA:*

Araujo, T., Ausloos, J., van Atteveldt, W., Loecherbach, F., Moeller, J., Ohme, J., Trilling, D., van de Velde, B., de Vreese, C., & Welbers, K. (Forthcoming). OSD2F: An Open-Source Data Donation Framework. *Computational Communication Research*, https://osf.io/preprints/socarxiv/xjk6t/

*Bibtex:* 

```
@article{osd2f,
 title={OSD2F: An Open-Source Data Donation Framework},
 DOI={10.31235/osf.io/xjk6t},
 author={Araujo, Theo and Ausloos, Jef and {van Atteveldt}, Wouter and Loecherbach, Felicia and Moeller, Judith and Ohme, Jakob and Trilling, Damian and {van de Velde}, Bob and {de Vreese}, Claes and Welbers, Kasper},
 year={forthcoming},
 journal = {Computational Communication Research}
}
```


This tool is inspired in earlier approaches that enable researchers to partner with individuals willing to donate their data for academic research, including [Web Historian](https://github.com/erickaakcire/webhistorian) (Menchen-Trevino, 2016), among others.
