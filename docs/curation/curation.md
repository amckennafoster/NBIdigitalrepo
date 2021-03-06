---
permalink: /curation/
layout: curators
---


# The Curation Process

Everything on this page is the responsibility of the NBI Wrangler. The curation process prepares research outputs for upload and creates a record of the files for later use by the NBI Uploader. Information from the [FlattenedFauna](https://app.gitbook.com/@flattenedfauna/s/practice-space/) project informed this protocol. 

The three main sections on this page are:

1. Data Embargoes: Work with the researcher to plan when their data is uploaded. 
1. Curating Data & Reports: Formatting the dataset and report so they meet open science best practices.
2. Metadata: Recording the information that describes the dataset and report (title, authors, etc). This is essential to make the files searchable and useful once uploaded to the Repository.


# Data Embargoes

In an ideal world, a dataset would be ready for upload with the report. However, there are many reasons why a researcher may want to postpone uploading their data (or not submit data at all). Researchers have the option to submit their data with their report to NBI under an agreed upon embargo, postponing upload to a future date.  The default time period is **two years**. The benefit of embargoing, rather than just submitting data at some later point, is that NBI holds a copy of the data in case the researcher either loses the dataset or goes incommunicado. Additionally, timely submission of data means the NBI Wrangler can curate the dataset while the project is fresh on the mind.  Work with the researcher to fill out the [Data Plan](https://raw.githubusercontent.com/nantucketbiodiversity/NBIdigitalrepo/master/files/documents/Researcher-Data-Plan.pdf).

The researcher has the following options:

1. Submit data with report for upload.
2. Submit data with report and agree to a default two year embargo period for upload, or arrange a different embargo timeline. Report is submitted for upload.
3. Submit a report only and agree to a custom data agreement.

Universities and institutions may have their own data policies that will complicate this. Ultimately, the data should be published somewhere. If a researcher uses their institutional repository or a third party repository, their report record in the NBI Digital Repository can point to the published data wherever it sits.

Here is an example: A PhD student hopes to publish a paper based on their data as part of their dissertation. They think it will be 3 years before publication. The student agrees to submit data with their report but have it embargoed for 3 years. At the end of their grant year, NBI receives the report and dataset. The report is uploaded to Zenodo immediately. The NBI Wrangler curates the dataset and puts it in a folder marked with the specified date of upload.  In 3 years, NBI contacts the researcher to get final confirmation for data upload. At this point the researcher may send a more complete dataset or let NBI know the data has been pubished elsewhere. In the latter case, the NBI uploader can add the DOI of the published data to the existing report record in the NBI Repository.

---

# Curating Data & Reports

Researchers should do most of this work (steps 1-4) since they know their data the best. However, the curator will need to check the dataset and make sure it meets the standards listed below. Here is an overview of the steps involved:

1. Tidy the data: Make sure the data is in an appropriate open science format.
2. Clean the data: Check for consistancy and null cells
3. Create a data dictionary: List of the variables (columns) in a new csv file
4. Examine each data column and fill in the data dictionary
5. Create metadata

<a href=" https://htmlpreview.github.io/?https://raw.githubusercontent.com/nantucketbiodiversity/NBIdigitalrepo/master/docs/assets/files/exampleIsopodData.html" target="_blank">Here is an example</a> of a cleaned and properly formatted dataset.


An excellent and mandatory read for anyone who works with data is Broman and Woo's (2018) ["Data Organization in Spreadsheets"](https://www.tandfonline.com/doi/full/10.1080/00031305.2017.1375989).


## Tidy Data
Tidy data is important because it is easy to read and facilitates analysis and summarization. 

It has the following characteristics.
- Data are in a [stacked format](https://www.displayr.com/what-is-data-stacking/).  This means that variables are the columns and observations are the rows.
- Each cell contains only one piece of information (e.g. rather than 'Garden 015', 'Garden' should be in a location column and '015' should be in a plot column.)

---

## Cleaning Data

#### General
- Remove leading zeros and consecutive white spaces ([OpenRefine](https://openrefine.org/) is a great tool for this)
- Correct all misspellings
	- Extract all the unique values for a column and check for variation. After corrections, use this list in the data dictionary, if approporiate.
- Normalize capitalization within columns
	- Use camalCase. No spaces and first word is lowercase while all following words have the first letter capitalized.
- Normalize and define abbreviations
	- Normalize the abbreviations in the data and define them in the data dictionary.
- Remove or escape special characters including /@#\$%
	- Work with the researcher to remove special characters from data values unless they are absolutely necessary. Rather than changing the content of notes and comments fields, escape the special characters here by putting a backslash (\\) before the special character.
- Encode missing values and blank cells
  - No cells should be empty
  - Missing value codes should match the data type:
    - String: null
    - Numeric: -9999

#### Georeference
- Seperate latitude and longitude columns
- Data type is double and values are decimal degrees (e.g. 41.39283)
- Longitude values are appropriately signed negative or positive (on Nantucket, the longitude should be negative)
- If known, in the data dictionary note the datum used (e.g. NAD87)

#### Date and Time
- Date and Time are separate columns
- Date is separated into three columns: year, month, and day
- If time is important to the data, separate the time parts into seperate columns (e.g. hour, minutes, seconds) and use a 24 hour format.

---

## Data Dictionary
[Data dictionaries](https://help.osf.io/hc/en-us/articles/360019739054-How-to-Make-a-Data-Dictionary) tell users what the column names mean, what the data values mean, and anything else that would help someone use the data wisely.

Create a csv file in your favorite spreadsheet program. The data dictionary will define the variables used in all the data files uploaded as one package, under one DOI. If you have a dataset with more than one data table that each have many of the same variables (e.g. survey data and trap data for the same study subject), make each table its own csv file and list all the variables from each file in the data dictionary file.
Add the following columns to the dataDictionary:

- Variable = Variable (column) name
- Type = string, integer, double, date, etc
- Description = A brief description of the variable
- Units = Units for the variable (e.g. meters). If a string, use 'null'
- Allowed Values = For variables that have a discrete list of values that number fewer than 50, list them here alphabetically, separated by commas. For continuous data types, use 'Any'
- Notes = Add any other useful information to help some one understand the values or the variable. One important thing to add is why any missing values exist

---

## File Names and Types

File naming convention is the following:
- Reports: authorlastname-nbi-report-year.pdf   For multiple authors: (author1 last name)-et-al-nbi-report-year.pdf
	- Example: richardson-nbi-report-2011.pdf   For multiple authors: richardson-et-al-nbi-report-2011.pdf
- Datasets: Describe the file contents using camalCase. The more descriptive, the better.
	- Basic Examples: capturesByDate.csv or pRigidaHeights.csv or allPitfallData.csv or anova.R

When adding the year to a filename, use the year of publication rather than the year of the grant. This will make it easier for people to figure out how to cite it.


All file types should be 'open' meaning a user does not need propriatary software to open and use the file.

#### Data
**CSV** Comma Separated Values

CSV is a standard format for open data. Most spreadsheet programs (like Excel) will allow you to save a file as .csv. All formatting is stripped away. If you have the option, save as CSV UTF-8. This will store unusual characters used in any note or comment fields properly.

**TXT** Text file

Data can also be saved as a text file as long as there is a way for a spreadsheet program to figure out how the data values are separated from each other.

#### Reports

**PDF**

PDF is the preferred report format. Almost any word processor can export a document to the pdf format. There are online tools to combine several pdfs into one.

#### Code

This section in progress...

#### Images

Images can be uploaded to the repository. The format matters though and if you need more information check out the Library of Congress [digital preservation](https://www.loc.gov/preservation/resources/rfs/stillimg.html) site. The [Center for Digital Architecture](https://digitalarch.org/blog/2017/4/7/best-image-formats-for-archival-photography) also has a very readable summary of the various types. If you can, add your name to the image and upload a high quality version. The use case of this is a future researcher or journalist could request permission to reproduce your image. Rather than trying to find a high quality copy, just put one in the repository.

**TIFF**

[Tiff](https://www.loc.gov/preservation/digital/formats/fdd/fdd000022.shtml) is the preferred archival format, but only if you can create the original image as Tiff. If your original image is a jpeg, use jpeg or jpeg2000 rather than Tiff.

**JPEG and JPEG2000**

If your orgigial image is jpeg, use [jpeg](https://www.loc.gov/preservation/digital/formats/fdd/fdd000018.shtml) or [jpeg2000](https://www.loc.gov/preservation/digital/formats/fdd/fdd000143.shtml). Jpeg2000 is better for long term preservation than jpeg.

**Other File Types**

Png is also an option but its preservation capabilities may be less than the other formats.

---

# Metadata
Metadata is information about an object, like author, date created, etc. Good metadata is essential to making reports and datasets findable and usable. Metadata gives context to a resource and without it, that resource (the report and dataset) will never be used again or, even worse, never even accessed again. All your hard curation work will be for naught!


>"To data users, good metadata is like summer rain after a long drought- it's refreshing and you don't know when you'll see it again." -the authors of this documentation :)


## Filling Out the Metadata Form
The NBI Wrangler submits metadata related to the report and dataset to NBI via the Metadata Form. The fields are set up to match what is available on Zenodo. Once a year, the NBI Uploader (the committee member responsible for uploading to Zenodo) will use the information entered into the Metadata Form to fill in values on Zenodo.

#### Upload Type
Choose the upload type from the dropdown list. If the upload will include both a report and a dataset, use dataset.

#### Title
Paste in the title from the researcher report, if available. Otherwise, create a descriptive title. If it is only a dataset, begin the title with "Data for" and then include the title of the report or paper associated with the data.  Titles should be descriptive.  

#### Report Date
If there is a report as part of the upload, use the date of the report.  If it has no date, use February 15 of the year following the grant year. For example, for a report on work done as part of a 2019 grant, the date would be 02-15-2020.  If this is only a data file or code, use today's date.

#### Authors 
Include all authors in the format: last name1, first name1, affiliation1, ORCID1; last name2, first name2, affiliation2, ORCID2

If the author's ORCID is unknown, leave blank.

#### Author contact email
This is especially important if the author chooses to embargo data and is also useful if errors are found in the report or data in the future.

#### Basic Description
Paste in the abstract of the researcher report and include any other relevant information.

#### File Description
List the name of each file being uploaded, including the file extension (e.g. wormData.csv). If necessary, include a description that would help a user know what the file contains. This is helpful there are many files and the file names do not fully convey their contents.

This list will be used by the NBI Uploader to confirm they have the right files to upload. It will also be included in the Description field on the Repository.

#### Subject
Enter the url for the study subject (species studied) if one exists. Use the [Global Biodiversity Inforamtion Facility](https://www.gbif.org/) to find the url.  
- If the subject is not represented on GBIF, use the lowest taxonomic term available and include your subject's species name as a keyword.  
- If there are many subjects, include the lowest taxonomic term that describes them all (e.g. [https://www.gbif.org/species/6163](https://www.gbif.org/species/6163) for a study on spiders in the family Thomisidae).

#### Kingdom 
Choose the kingdom that the subject of the study is classified in. If the study focuses on subjects in more than one kingdom, add another kingdom as an additional keyword in the free text box at the end of the page. This will help users find all NBI studies related to plants or animals or fungi.

#### Group
This list is sourced from the original NBI list of grants.  It is a 'folksonomy' and is useful for grouping reserach outputs into general subjects of study.

#### Study Type
Study type is how the collected data is analyzed or what it produces. Examples include: checklist, species survey, genetic analysis, species-area curve, etc.

#### Locations -Geography and Specific Location
General Geography
- The General Geography locations are the islands or other land masses, please choose as appropriate to the study. 

Specific Locations
- The second set of locations are more specific. If your study had more than six specific locations, add additional specific locations as keywords in the free text keyword box. However, please do not enter more than 10 total specific locations. If a project has more than 10 specific locations, the General Geography of "nantucket" will suffice.

Specific locations may include properties, generally accepted place names, property owner (e.g. Nantucket Conservation Foundation), or geographic feature (e.g. pond, hill, beach).
 
#### Methods
Choose two methods used to collect data in the study. If more than two methods were used add additional method keywords in the free text box at the end of the page. Methods are the ways data was acquired, not the way it was analyzed.

#### Additional Keywords
Examples of this could include ecosystem analysis, symbiotic relationships, diet analysis etc. Include important words that a user might search for. Add any information here that did not fit in the above fields.  

#### Funding Keyword
This helps the NBI uploader fill out the metadata properly on Zenodo.  Choose NBI Grant, Other Grant, Both or multiple or None.

#### License
The recommended license is Creative Commons Attribution 4.0. This allows maximum reusability and requires users to cite the upload. For more information on the world of open data licenses see <a href="{{site.baseurl}}/specs/#licenses">the specifications and technical details section</a> of this site.

#### Embargoes
Enter the embargo information in this field. Note why the data is embargoed and what month and year it should be uploaded.  Here is an example:

> "Embargoed 3 years: upload in 2024. Researcher plans to do a follow up study and publish a paper."

#### Related Identifiers
The dataset or report may be related to a research output that is already published and has a DOI. Related identifiers may point to a research output within the NBI Digital Repository on Zenodo or may point to an external source. For example, a researcher conducts a pilot study on Nantucket and NBI uploads the dataset and report to the repository. These likely have no related identifiers. The following year, the researcher conducts follow up research and collects a much larger dataset, subsequently publishing the results in a peer reviewed journal. The researcher submits the dataset to NBI for upload. That dataset would have two related identifiers: one for the pilot study and one for the peer reviewed publication.

Related Identifier Relationships

Here are the relationships that will likely be useful to NBI, however Zenodo has a much <a href="{{site.baseurl}}/specs/#controlled-vocabularies">longer list</a>.

<table>
<tr><th>Related Identifier is</th><th>Use this relationship</th><th>Notes</th></tr>
<tr><td>Published paper that does not cite the uploaded data</td><td>is supplemented by this upload</td><td></td></tr>
<tr><td>Published paper that cites the uploaded dataset</td><td>cites this upload</td><td>This is likely added after paper publication</td></tr>
<tr><td>Data already published that this data is a subset of</td><td>has this upload as part</td><td>An example is beetle count data from pitfall trap data for a spider study. The published spider data and documentation act as the parent to this upload.</td></tr>
<tr><td>Data that is part of a pilot study or earlier study</td><td>is continued by this upload</td><td></td></tr>
<tr><td>Published data used/cited in the current upload</td><td>is cited by this upload</td><td></td></tr>
</table>

#### Grant Funding
Information regarding single or multiple grants that funded this research in this format: Grant funder, grant name or grant number; Grant funder, grant name or grant number; etc. If this is NBI funded, enter the year of the grant.  This helps the NBI uploader enter the metadata properly.

#### Contributors
Contributors are those who helped significantly with data collection/analysis/management or the research project as a whole but are not authors. People in the Acknoledgments should not be automatically added here. However, you, as the NBI Wrangler should be noted here (relationship = Related person) because you likely facilitated the work overall. If you oversaw the data curation of the dataset, **include yourself as Data curator!**. Use the following format: last name1, first name1, affiliation1, relationship1; last name2, first name2, affiliation2, relationship2

The relationship is important. Use any of the following:

<table>
<tr><td>Contact Person</td><td>Data curator</td><td>Data collector</td><td>Data manager</td><td>Distributor</td></tr>
<tr><td>Editor</td><td>Hosting institution</td><td>Other</td><td>Producer</td><td>Project leader</td></tr>
<tr><td>Project manager</td><td>Project member</td><td>Registration agency</td><td>Registration authority</td><td>Related person</td></tr>
<tr><td>Research group</td><td>Researcher</td><td>Rights holder</td><td>Sponsor</td><td>Supervisor</td></tr>
<tr><td>Work package leader</td><td></td><td></td><td></td><td></td></tr>
</table>


