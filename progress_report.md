# Progress Reports

**Table of Contents**
1. [Preliminary Progress Report](#prelim)
1. [1st Progress Report](#pr1)
1. [2nd Progress Report](#pr2)
1. [3rd Progress Report](#pr3)

## Preliminary Progress Report: Repository Constructed <a name="prelim"></a>
February 5, 2020

Added:
- `README` file that will contain a brief overview of the project
- `.gitignore` with some basics that should not be screened for upload by GitHub
- `LICENSE` file that will eventually contain a license delineating terms of use
- `project_plan` that contains a general overview of the project, and will be fleshed out in the future
- and of course this `progress_report` file

## 1st Progress Report: Rethinking the Project and Data Organization (Part I) <a name="pr1"></a>
February 25, 2020

The first thing that became necessary was changing up my whole plan for this project, since
finding a corpus that fit my original idea of looking at a syntactic structure unique to
spoken Arabic wasn't panning out. In the search for a corpus to use, I came across the
[Arabic Learner Corpus](https://www.arabiclearnercorpus.com/) and have decided to use it
for this project. Please see my [Project Plan](https://github.com/Data-Science-for-Linguists-2020/Arabic-Learner-Corpus-Considerations/blob/master/project_plan.md)
for more detailed information.

Aside from rethinking my project's scope, this progress report focused on the following:

### 1. Attempting and mostly completing the data acquisition process
Finding a corpus was about the only thing that went to plan at this stage. The data are available under a Creative Commons license,
so I'm free to use them for non-commercial purposes as long as I give proper attribution to the original authors. The entire corpus
is freely available for download from the ALC website in a number of formats (plain text, XML, etc.), so this step was straightforward.

### 2. Making headway into cleaning and reorganizing the data
[Data organization](https://github.com/Data-Science-for-Linguists-2020/Arabic-Learner-Corpus-Considerations/blob/master/data_analysis/ALC_Data_Organization.ipynb)
was a process easier said than done, especially when working with XML and in a language other than English! BeautifulSoup gave me a lot of issues at first 
and wasn't reading the text in correctly. The hunch was that encoding was to blame, and a visit to Jevon's office hours (thanks Jevon!) helped get to the
bottom of everything. At this point, I'm able to read in the entries; next step is to get things into `dataframe` objects in `pandas` and make something
useful out of everything.

### 3. Thinking about a "data endgame" (final form, target total size, format, etc.)
You can look at my [test data](https://github.com/Data-Science-for-Linguists-2020/Arabic-Learner-Corpus-Considerations/tree/master/test_data) here. Right
now, I'm planning on leaving all of the original corpus files in their original forms and keeping them in a private folder for use. The plan is to
have `pandas` `dataframe` objects that contain the relevant tagged data from the original essays (learner L1, text, age, location, etc.) along with
additional information like text length and TTR^2 that I will compute myself. 

### 4. Devising a couple of options regarding the "sharing plan" of the data
The corpus I'm using comes with a Creative Commons license already, so I plan on using the same one and similarly allowing
anything that results from my work to be used for copying, redistribution, and adaptation for non-commercial purposes and
given proper attribution. I'm committed to this license because 1) it's in keeping with the licensure of the original work,
2) it aligns with principles of open science and data sharing, and 3) it doesn't seem to pose any ethical issues with identifiability
of the learners who were participants and had their data collected. For more specific information, 
visit [my project's License page,](https://github.com/Data-Science-for-Linguists-2020/Arabic-Learner-Corpus-Considerations/blob/master/LICENSE.md)
which will be further fleshed out in a future update.

## 2nd Progress Report: Data Organization (Part II) and Analysis (Part I) <a name="pr2"></a>
March 17, 2020

This progress report focused on the following:

### 1. Completing the data acquisition process
Already done as of the last progress update; the main issue to work through this time was reading in, cleaning, and (re)organizing data.

### 2. Cleaning and reorganizing the data.
The information that I'm interested in is now more or less in its final form in a `pandas` `DataFrame` for use, and the final form 
has been safely pickled and saved locally on my machine. Data were cleaned to remove any NaN values from the "Title" column of the 
`DataFrame`; otherwise, all of the columns had information present. Additionally, information like tokenized word lists and TTR value
for the sample was added to each entry.

### 3. Documenting the overall format, shape, and size of the data.
Done; please see the [ALC Data Organization](https://github.com/Data-Science-for-Linguists-2020/Arabic-Learner-Corpus-Considerations/blob/master/Notebooks/ALC_Data_Organization.ipynb)
notebook for this information. In a nutshell, I'm working with all of the 1,585 entries from the original corpus, with 17 columns of data
for each entry.

### 4. Finalize the sharing scheme of the "found" portion of the data as well as the license for your own data and project.
I've elected to maintain the [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0) license](https://creativecommons.org/licenses/by-nc/4.0/)
that the original corpus was licensed under. This allows for the work to be shared and modified for **non-commercial use**, provided proper 
attribution to the original authors. It didn't feel right (or legal?) to use a different license here, since the original work did not
allow for commercial usage of the data.

Unfortunately, GitHub did not allow for all 1,585 XML files to be uploaded to my project's repository, but anyone interested
in replicating the project can [download the full corpus from the source](https://www.arabiclearnercorpus.com/download-en)
(signup/login required). I'll removed the 'test_data' folder in favor of just keeping the 'data' folder on GitHub, since removing
the 'Data' one would mean changing filepaths again. (Any guidance on how to git-rm remove a folder with 152 files?)

### 5. Start bringing in the analysis part into your project. In particular, your manipulation of data should be shaped by the linguistic analysis you are after.
To this end, I've created a new Notebook, [ALC Data Analysis](https://github.com/Data-Science-for-Linguists-2020/Arabic-Learner-Corpus-Considerations/blob/master/Notebooks/ALC_Data_Analysis.ipynb)
in which I plan to continue my work with the data I've curated.

## 3rd Progress Report: Data Organization (Final) and Analysis (Part II) <a name="pr3"></a>
For this slew of project updates, I focused on [finalizing the form of my data](https://github.com/Data-Science-for-Linguists-2020/Arabic-Learner-Corpus-Considerations/blob/master/Notebooks/ALC_Data_Organization.ipynb)
(adding an L1 family column to my `DataFrame` with some help from [Ethnologue](www.ethnologue.com) and attempting [a preliminary run of training an SVC classifier](https://github.com/Data-Science-for-Linguists-2020/Arabic-Learner-Corpus-Considerations/blob/master/Notebooks/ALC_Data_Analysis.ipynb)
to identify the L1 family of the writer based on their text. Short story: it didn't go so hot in terms of accuracy, capping at around 65%. It
seems like the imbalance of L1s represented in the data really is a huge stumbling block, and it makes me wonder if maybe collapsing
the categories further into "L1 Arabic" and "non-L1 Arabic" is the necessary conclusion to make something usable here. I'm comfortable
with saying at this point that I'm just interested in seeing if these data are conducive to training a classifier, narrowing the focus
of my initial broad research interest down from "can this dataset be useful for SLA" toward "can this dataset be useful for ML"? However,
I'd still like to investigate the distributions of the various subgroups in the data (i.e. TTR broken out by L1 family) and do some more work
on that. I just feel a bit less comfortable with that task, since figuring out classification has dominated my work up until now. Next step
is to refine the conclusions drawn from the classifier's performance and take a look around for meaningful patterns in the subgroups.

On a separate note, my license has been up and ready to go since the last update, and you can also now stop by and sign my 
[Project Guestbook](https://github.com/Data-Science-for-Linguists-2020/Class-Plaza/blob/master/guestbooks/guestbook_anthony.md)
if it floats your boat!