# PhDTitle

This repo contains the LaTeX style file for the PhD Thesis title page, following the guidelines set out by the [EDMADIS doctoral school](https://edmadis.univ-lille.fr/pendant-le-doctorat/soutenance) from the University of Lille.
As such, two PhD title pages are provided by default, the first in French followed by another in English.
We also provide two distinct versions of the title pages, one for the review process and one for the final submission.

We also provide a different title page format, for the intermediate PhD review process, which takes place at the end of the first year (in EDMADIS).
This CST version provides the necessary information for the report without the need for indepth thesis related information, contrary to the PhD title version.

## Index

1. [PhD Title](#phd-title)
      1. [Main Commands](#main-commands)
      2. [Thesis Versions](#thesis-versions)
          1. [Final Version](#final-version)
          2. [Review Version](#review-version)
2. [CST](#cst)
3.  [Customisation](#customisation)
    1. [Languages](#languages)
    2. [Logos](#logos)
    2. [Title Style](#title-style)

## PhD Title

To use this style, simply place the `phdtitle.sty` file in your working directory and include it in your main TeX file.
The PhDTitle package redefines the `\maketitle` command to generate the front page.
As such, you can use the `\author{#1}` command to set your own name.

```LaTeX
\usepackage{phdtitle} % import package

\author{Edward Staddon} % set your name

% commands and customisation here

\maketitle % print title page
```

### Main commands

From here, you can customise the output as needed.
All customisation commands follow the same concept: `\command{english version}{french version}`.
Here we present the main commands:

* `\title{#1}{#2}`: prints the title in the centre of the document, surrounded by black lines
* `\university{#1}{#2}`: prints the name of the university at the top of the page
* `\doctoralschool{#1}{#2}`: prints the name of the doctoral school, under the university
* `\laboratory{#1}{#2}`: prints the name of the laboratory, under the doctoral school
* `\degree{#1}{#2}`: prints the name title of the PhD degree
* `\speciality{#1}{#2}`: prints the speciailisation of the PhD in qustion

Below are the commands used in my own thesis, visible on the examples provided.

```LaTeX
\title
{Threat Detection, Identification and Quarantine in Wireless IoT based Critical Infrastructures} % title in English
{Détection, identification et mise en quarantaine des menaces dans les infrastructures critiques sans fil basées sur l'IoT} % title in French

\university
{University of Lille} % university in English
{Université de Lille} % university in French

\laboratory
{Inria Lille - Nord Europe} % laboratory in English
{Inria Lille - Nord Europe} % laboratory in French

\doctoralschool
{Doctoral School MAthematics and DIgital Sciences} % doctoral school in English
{École Doctorale Mathématiques, sciences du numérique et de leurs interactions} % doctoral school in French

\degree
{PhD in Computer Science} % degree in English
{Docteur en Informatique} % degree in French

\speciality
{IT and Applications} % speciality in English
{Informatique et Applications} % speciality in French

```

> ℹ️ The first field of the `\title` command is used as the PDF title, and is also set as the PDF bookmark for the first page

> ![PDF Bookmark][bookmark]

### Thesis versions

Following the guidlines provided by the University of Lille, there are two versions of the title page, corresponding to the different stages in the writing of the thesis.
The first corresonds to the submitted version of the thesis post defence whereas the second is considered the 'working' version, that which is sent to the reviewers for evaluation.
The main format remains the same, however, some information is changed between the two, mainly related to the defence itself.

#### Final version

This version is the default format of the style.
Here we need to add two new elements: defence date and the jury members.
To do this, we add two new commands:
* `\datedefended{#1}{#2}`: the date of the thesis defence. Once again this is in two versions: English followed by French.
* `\jurymember{#1}{#2}{#3}{#4}{#5}`: adds a new person to the list of jury members and can be used as many times as needed.

> ⚠️ the `\jurymember` command is order specific, thus jury members wuill be printed in the order they are added

Compared to the previous commands, the `\jurymember` command possesses a different format.
Indeed, here we need to add both their affiliation as well as their role in the jury, and once again this must be in both English and French.
Each option is presented below:

* `#1`: the name of the jury member
* `#2`: their role in the defence, in English
* `#3`: their affiliation, in English
* `#4`: their role in the defence, in French
* `#5`: their affiliation, in French

Below are the commands used after my my own defence.

```LaTeX
\datedefended % defence date in both versions, can be in whatever format and is printed as is
{9th December 2022}
{9 décembre 2022}

% list of the five jury members from my defence.
% reminder that the order is important!
\jurymember
{Thomas Noël} % jury member's name
{Examiner} % their role in the defence, in English
{Full Professor, Université de Strasbourg} % their affilitation, in English
{Examinateur} % their role in the defence, in French
{Professeur des Universités, Université de Strasbourg} % their affiliation, in French

\jurymember
{Thomas Begin}
{Reviewer}
{Associate Professor, Université Claude Bernard Lyon 1}
{Rapporteur}
{Maître de Conférences HDR, Université Claude Bernard Lyon 1}

\jurymember
{Thierry Val}
{Reviewer}
{Full Professor, IRIT}
{Rapporteur}
{Professeur des Universités, IRIT}

\jurymember
{Nathalie Mitton}
{Supervisor}
{Research Director, Inria}
{Directrice de Thèse}
{Directrice de Recherche, Inria}

\jurymember
{Valeria Loscri}
{Co-Supervisor}
{Permanent Researcher, Inria}
{Co-Directrice de Thèse}
{Chargée de Recherche HDR, Inria}
```

The two final titles are shown here.

![French final version][phd-final-fr]
![English final version][phd-final-en]

#### Review version

As specified by the University of Lille, there is another version of the title page, corresponding to the current working version which is sent to the reviewers.
To select this format, you must use the following

```LaTeX
\definitiffalse % set the version as 'working'
```

Since this corresponds to the review version, only one new command is added, corresponding to the submission date:
* `\datesubmitted{#1}{#2}`: the date of the submission to the reviewers, once again in English and French

The example from my thesis is as follows

```LaTeX
\definitiffalse % set revew version

\datesubmitted # add submission date, in whatever version required
{17th October 2022}
{17 octobre 2022}
```

The two review pages are shown here.

![French review version][phd-submit-fr]
![English review version][phd-submit-en]

## CST

One requirement of many doctoral schools is to provide a written repot on the activites of that year.
At the University of Lille, this CST (Comitée de Suivi de These) or CSI (Comitée de Suivi Individuel), only takes place at the end of the first year, where a report is ent to reviewers who verify that the student is on track and hasn't encountered any major problems, both professionally and socially.
As a result, a CST version has also been created, posessing a slightly different format than the PhD version.
The main difference here is that only a single page is necessary, here taking the language directly from the global definition using the `babel` package

Its use is identical to previously, by adding `phdtitle.sty` file to the working directory and using the phdtitle package.
Only this time, we specify from the getgo that we are using the CST version with the `\csttrue` command:

```LaTeX
\usepackage[english]{babel} % set the language to english
\usepackage{phdtitle} % import package

\csttrue % set package into CST mode
\author{Edward Staddon} % set your name

% commands and customisation here

\maketitle % print title page
```

Since only a single page is generated in the language of choice, the commands also receive a slight overhaul:
* `\title{#1}{#2}`: prints both a title (`#1`) and subtitle (`#2`) in the centre of the page, both are mandatory
* `\university{#1}{#2}`: prints the name of the university at the top of the page, option `#2` is ignored
* `\doctoralschool{#1}{#2}`: prints the name of the doctoral school, under the university, option `#2` is ignored
* `\laboratory{#1}{#2}`: prints the name of the laboratory, under the doctoral school, option `#2` is ignored
* `\academicyear{#1}{#2}`: prints the current academic year, wher `#1` is the start and `#2` the end
* `\supervisors{#1}{#2}`: prints the names of up to two PhD supervisors, if only one then `#2` must be left empty
* `\dates{#1}{#2}`: prints the dates of the PhD with `#1` the start and `#2` the end of the contract

![CST Report][cst]

Below are the commands used in my own CST report from the image above.

```LaTeX
\title
{Threat Detection, Identification and Quarantine in Wireless IoT based Critical Infrastructures} % main title
{First year CST Report} % sub title

\university
{University of Lille} % university
{} % not used

\laboratory
{Inria Lille - Nord Europe} % laboratory
{} % not used

\doctoralschool
{Doctoral School MAthematics and DIgital Sciences} % doctoral school
{} % not used

\academicyear % the current academic year 2019-2020
{2019}
{2020}

\supervisors
{Nathalie Mitton} % Supervisor
{Valeria Loscri} % Co-supervisor if present, if not then this must be specified as empty i.e., {}

\dates
{01/10/19} % start date
{30/09/2022} % end date

```

## Customisation

This style allows for customisation of various elements, from the logos to the representation of the title itself.

### Languages

Depending on the language of the Thesis, the title page can be customised accordingly.
In France, the rules state that a thesis written in French needs only a French title page.
However, if this thesis is written in English, then both a French and an Englsih title page are needed, which is the case of my own thesis.

To do this, we can select which version of the title page is required using the following commands:

```LaTeX
\englishonlytrue % prints only the English title page
\frenchonlytrue % prints only the French title page
```

> ⚠️ These commands are mutually exclusive, and if both are present then an error will occur.

If you wish to add a new language to the style, then you can use the `\addto\captions` command to add the language.
Below are the examples of both the French and English language settings for the title page

```LaTeX
\addto\captionsenglish{
    % Thesis specific
    \renewcommand{\school}{\univEN}
    \renewcommand{\doctoral}{\doctEN}
    \renewcommand{\research}{Research Institute\xspace\laboEN}
    \renewcommand{\preparedby}{Thesis prepared by}
    \renewcommand{\grade}{with the view of obtaining the degree of\xspace\textbf{\degreeEN}}
    \renewcommand{\discipline}{Discipline\xspace\textbf{\speciEN}}
    \renewcommand{\titletext}{\titleEN}
    \renewcommand{\defended}{Thesis defended the\xspace\defEN\xspace in-front of the jury comprised of:}
    \renewcommand{\jury}{\juryEN}
    \renewcommand{\submitted}{Thesis submitted to the reviewers on the\xspace\subEN}
    % CST specific
    \renewcommand{\phdstudent}{PhD Student}
    \renewcommand{\datestitle}{Dates}
    \renewcommand{\supervisorstitle}{Supervisors}
    \renewcommand{\academicyeartitle}{Academic year}
}

\addto\captionsfrench{
    % Thesis specific
    \renewcommand{\school}{\univFR}
    \renewcommand{\doctoral}{\doctFR}
    \renewcommand{\research}{Institut de Recherche\xspace\laboFR}
    \renewcommand{\preparedby}{Thèse préparée par}
    \renewcommand{\grade}{en vue de l’obtention du grade de\xspace\textbf{\degreeFR}}
    \renewcommand{\discipline}{Discipline\xspace\textbf{\speciFR}}
    \renewcommand{\titletext}{\titleFR}
    \renewcommand{\defended}{Thèse soutenue le\xspace\defFR\xspace devant le jury composé de :}
    \renewcommand{\jury}{\juryFR}
    \renewcommand{\submitted}{Thèse soumise aux rapporteurs pour examination le\xspace\subFR}
    % CST specific
    \renewcommand{\phdstudent}{Doctorant}
    \renewcommand{\datestitle}{Dates}
    \renewcommand{\supervisorstitle}{Encadrants}
    \renewcommand{\academicyeartitle}{Année Académique}
}
```

If you wish to replace the french langauge with your own, such as Italien for example, then you can simply recreate the above commands using `\addto\captionsitalien{...}`, using the french subcommands suchas `\univFR` etc.
These commands get their values from the user commands presented previously.
For example, `\univFR` takes its value from the French field of the `\university` command.
Thus, by simply replacing all French values in the thesis information commands with the Italien versions, they will be associated and used as needed.

> ⚠️ To get the `\maketitle` command to recognise the new language, it is necessary to replace the `french` language with our own in the style source file in the `\renewcommand{\maketitle}` at the bottom of the file.
> Multilingual support will be added in future versions.

### Logos

![PDF Logos][normal-logos]

The minimum requirements for this title page are the logo of the university and the laboratory of affiliation.
The output order is always the same, first the laboratory then the university.
These by default are set to the University of Lille and Inria, as provided in the `logos/` folder.
However, these can be overriden and customised as required with the following commands:

```LaTeX
\renewcommand{\logoInria}{logos/INRIA_logo} # set the laboratory logo
\renewcommand{\logoULille}{logos/Univ_Lille_Logo} # set the university logo
```

As can be seen in my thesis and CST report, there is also another logo, that of the project which financed my work.
This logo is optional, but if requeted will be appended to the row of logos, moving the university into the centre position:

```LaTeX
\extraimage{logos/LogoCybersane_RVB}
```

![Extended Logos][extended-logos]

### Title Style

By default, the title is surrounded by small black lines, adding emphasis to the text, the default values of which are:
* length: `2.5cm`
* thickness: `0.2mm`
These lines are completely customisable, allowing the user to modify both the length and thickness of the lines themselves.

```LaTeX
\titleruler{%
#1 % the length of the top ruler
}{
#2 % the thickness of the top ruler
}{
#3 % the length of the bottom ruler
}{
#4 % the thickness of the bottom ruler
}
```

Not all options are required, so if you only wish to increase the length of the top ruler and the thickness of the bottom, then you can use the following command which will give this output.

```LaTeX
\titleruler{10cm}{}{}{2.5mm}
```

![Customisable Title][ruler]

[bookmark]: ./images/pdf_bookmark.png
[phd-final-fr]: ./images/phd_final_fr.png
[phd-final-en]: ./images/phd_final_en.png
[phd-submit-fr]: ./images/phd_submit_fr.png
[phd-submit-en]: ./images/phd_submit_en.png
[cst]: ./images/cst.png
[normal-logos]: ./images/normal_logos.png
[extended-logos]: ./images/extended_logos.png
[ruler]: ./images/ruler.png
