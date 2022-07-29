# Database

### Location
The database settings and construction are located in *../osd2f/database/**

### Memory vs on-disk
The default location of the donation database is in-memory. For testing
purposes, it has been valuable to see that the data actually gets that far,
and as such the database location was temporarily rerouted to on-disk
storage in *../osd2f/database/testingDB/testBase.db*. While data was stored here
precaution was taken to ensure only mock data was donated. This database can
be re-activated by editing the "DB_URL" variable of *../osd2f/config.py*.
```python
# Default DB_URL configuration:
DB_URL = "sqlite://:memory:"
# Testing on-disk DB_URL Configuration
DB_URL = "sqlite:C:/<directory_location>/osd2f/osd2f/database/testingDB/testBase.db"
```

### Deployment
While this has proven valuable for testing purposes, it is important to remember
that you must change back to the default configuration before deployment. This is both due to
security reasons and to make deployment to (for example) Azure easier.

Consult *deploying_to_azure.md* and *deploying_as_a_container.md* in the *OriginalDocs* folder
to be guided through the Deployment process.