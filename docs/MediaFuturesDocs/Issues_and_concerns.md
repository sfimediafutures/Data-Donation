# Known Issues and Concerns

#### The purpose of this document is to showcase issues and concerns regarding the developmental problems, as well as unresolved challenges that may have occured during the development process.

## Incorrect encoding
The server seems to have difficulties encoding utf-8 properly and as such cannot always display in cleartext. Unicodes used
instead are listed below. 

```bash
æ : \u00E6
ø : \u00F8
å : \u00E5
Æ : \u00C6
Ø : \u00D8
Å : \u00C5
```

### Consent popup (Pasted from front_end_development.md)
The consent popup must be written by someone legally inclined, so that details and format are completely correct
and in line with industry standards. The text-prompt for the consent popup can be found within 
*../osd2f/settings/default_content_settings.yaml*, scrolling if required until the single indent "conset_popup" 
is found. Here, the title and lead of the consent popup can also be edited. The *points* tab is where the declaration
of consent itself should be written.

## Waiting time when requesting GDPR data and download-by dates.

How long you may be required to wait when requesting GDPR data from various big platforms can vary greatly.
Additionally, due to security measures, the download links are only valid for an x amount of days, which
also vary. some examples below:
```
Meta (Instagram & Facebook): up to 14 day wait, 4 day link validity
Twitter: up to "24 hrs or longer" (mine was ready in 3 days) wait, 6 day link validity
Schibsted: up to 30 day wait, 6 day link validity
```

This presents some challenges regarding getting customers to:
1. Care enough about the data donation to return when they receive their data.
2. Remember to return and donate the data.
3. Check emails often enough to download the data before the link runs out. 

#### Reminders?
The first idea is to present an option for donors to receive a notice reminding them to donate their data. 
However, if the donor requests their (for example) Instagram data and receives it after just two days, the
link will run out by day 6 and a reminder after 14 days will be insufficient. 
Conversely, a second idea of serving several reminders to combat every possible window where the user 
*both* has the download link and the link is still valid will potentially be very invasive and annoying
for the donor. While this doesn't seem like a huge problem in and of itself, it aids in raising the bar and
making the donation of data less accessible, which will be one of the main obstacles when trying to attract
potential donors to the project.

#### Testing with real-world data
Continuation of point on wait times for real world data, all testing has been done by use of the included mock 
data within the project itself. Project developer waited too long to request data as he was not aware there would be
extensive wait times upon requesting a gdpr-related package download. As such, testing the anonymizers should
ideally be done on real-world data before deployment into production.

Testing with real world data is furthermore required because of rigorous anonymization requirements. If a platform
formats suffixes (eg. "user posted thing" vs "user published thing" or "user tweeted thing") all of these would
have to be included in the sep_strings list of the anonymization files (*../osd2f/anonymizers/*)

## Safety concerns
At the start of the project (June 8th 2022) A meeting was arranged with cybersec engineers working on UiBs 
SAFE technology, with the hope of utilising SAFE for storage of data donation packages. They had several
security concerns that would need to be adressed before deployment:

#### Responsibilites
Once the package is uploaded, MediaFutures assumes legal liability for the integrity and safety of the data.
This means that the data needs to be 1. encrypted to ensure security and 2. properly anonymized to ensure
that a data leak will not breach gdpr (Anonymized data falls outside the scope of the gdpr)


#### Asymmetric encryption of keys
A method proposed by one of the security experts is to utilise an asymmetric key encryption, where the file
is first encrypted on a public key to then be decrypted on a private key. MediaFutures would hold both 
the public and private key, the donor would only have access to the public key. While this is safe,
it causes some concern about the average tech-illiterate John Doe's ability to do it. Even with a
tutorial, some may see a guide and identify it as too "technological" and drop the entire process.

#### Encryption must happen after data-minimization
As the  possibility for the donor to minimize their data before donation exists, the data
cannot be encrypted before this step is complete. Data-minimizing processes would not be feasible 
post-encryption.

#### Concerns with un-encrypted data
If data is not encrypted on the web-server, it opens up for cross-scripting or other methods of "breaking
into" the web-server. For this reason, it may be recommended to include a method of monitoring the server
actively.

#### Getting the data into SAFE
Possibility of "Handshake solution"? SAFE is an airlocked (completely disconnected) system and as such may
need a manual transfer of data from a temporary database that receives the donation packages. Someone may
then need to manually transfer the packages from the temp server into SAFE. (Automatic or manual way of truncating
the data from the airlock database post-handshake may/should be considered.)