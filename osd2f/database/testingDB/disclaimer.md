# DIRECTORY ONLY USED FOR TESTING
The testBase.db database should only contain fake mock data and must never contain real 
GDPR package information. Consult the documentation to see how you can adress
this directory in testing. If you end up using it for testing, it is
very important that you remember to change it back to in-memory storage before production. Post-production, the testingDB directory 
can even be deleted with no consequence.