# Bulk Reviewer

> Identify, review, and remove sensitive files

**Note: This project is under active development. A first release is expected in summer 2019.**

Bulk Reviewer is a software program that aids in identification, review, and removal of sensitive files in directories and disk images. Bulk Reviewer scans directories and disk images for personally identifiable information (PII) and other sensitive information using [bulk_extractor](https://github.com/simsong/bulk_extractor), a best-in-class digital forensics tool, and can optionally extract named entities (personal names as well as nationalities, religions, and political affiliations) using [spaCy](https://spacy.io/) and [Apache Tika](https://tika.apache.org/). A browser application enables users to configure, start, and review scans, generate reports, and export files, separating problematic files (e.g., those requiring redaction or further review) from those that are free of sensitive information.

Currently, Bulk Reviewer can scan directories and disk images for:

* Social Security Numbers (SSNs)
* Canadian Social Insurance Number (SINs)
* Credit card numbers
* Email addresses
* Phone numbers
* URLs, web domains, RFC822 headers, and HTTP logs
* GPS data
* EXIF metadata
* User-supplied regular expressions (uploaded as a txt file with each regexp on a new line)

Scanners planned but not yet implemented include:

* Personal names
* Names of nationalities, religions, and political affiliations
* Other national identifiers
* Banking information (e.g. IBAN and SWIFT account numbers)
* Personal health information
* Facebook and Outlook data
* Additional lexicons (like [those developed by the ePADD project team](https://library.stanford.edu/projects/epadd/community/lexicon-working-group))

The application is designed to aid archivists and librarians in processing and providing access to digital collections but may be useful in other domains as well. Bulk Reviewer has been made possible in part by the generous support of the [Library Innovation Lab](https://lil.law.harvard.edu) at Harvard University, where Tim Walsh was a 2018 Summer Fellow, and a Concordia University Library Research Grant.

An earlier server-based version of Bulk Reviewer developed using Django can be found [here](https://github.com/timothyryanwalsh/bulk-reviewer).

Contributions are welcome! Interested in getting involved? [Get in touch](mailto:tim.walsh@concordia.ca)!

## Dependencies

Bulk Reviewer requires that the following programs are installed on the same computer and that their command line interfaces are available on the system path:

* [bulk_extractor](https://github.com/simsong/bulk_extractor): Note that scanning for Canadian Social Insurance Numbers (SINs) was only added to the master branch of bulk_extractor (version 1.6.0-dev) as of commit [018b056](https://github.com/simsong/bulk_extractor/commit/018b056a2b24cca4335f92d17d06d7802792530e). In order for Bulk Reviewer to find display SIN results, you will need to build bulk_extractor from source from this or a later commit.
* [The Sleuth Kit (TSK)](https://github.com/sleuthkit/sleuthkit)

For Bulk Reviewer to be able to handle Encase/E01 disk images, bulk_extractor and The Sleuth Kit must be built with [libewf](https://github.com/libyal/libewf/).

These dependencies should already be installed in the [BitCurator Environment](https://confluence.educopia.org/display/BC/BitCurator+Environment) (unless you need to scan for Canadian SINs, in which case bulk_extractor will need to be rebuilt from source.)

## Development

Bulk Reviewer is an Electron desktop application with a Python backend. Local development requires Python 3, Node, and npm/yarn (instructions here use yarn).

1. Clone this repository

`git clone https://github.com/bulk-reviewer/bulk-reviewer`

2. Prepare Python virtual environment

``` bash
# First time

virtualenv -p python3 env
source env/bin/activate
pip install -r src/main/backend/requirements.txt

# Subsequent times

source env/bin/activate
```

3. Install npm modules (first time only)

`yarn install`

4. Start webpack development server

`yarn run dev`

## Build locally

Instructions forthcoming. Basic steps:

1. Package Python scripts

2. Build Electron application for production

`yarn run build`

## Logo design
[Bailey McGinn](https://baileymcginn.com/)

---

This project was generated with [electron-vue](https://github.com/SimulatedGREG/electron-vue)@[8fae476](https://github.com/SimulatedGREG/electron-vue/tree/8fae4763e9d225d3691b627e83b9e09b56f6c935) using [vue-cli](https://github.com/vuejs/vue-cli). Documentation about the original structure can be found [here](https://simulatedgreg.gitbooks.io/electron-vue/content/index.html).
