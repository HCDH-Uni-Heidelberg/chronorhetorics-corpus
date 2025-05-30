<p align="center">
  <a href="#chronorhetorics-corpus">
    <img src="https://github.com/HCDH-Uni-Heidelberg/chronorhetorics-corpus/blob/main/assets/LOGO_TB_300.png?raw=true" alt="Chronorhetorics logo" width="300" height="300">
  </a>
</p>

<h3 align="center">Chronorhetorics Corpus</h3>

<p align="center">
  A large-scale corpus of political speeches for analyzing temporal figures and political enforcement patterns in times of change.
  <br>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-1.0-blue.svg" alt="Version">
  <img src="https://img.shields.io/badge/last%20updated-2025--05--29-green.svg" alt="Last Updated">
  <img src="https://img.shields.io/badge/DOI-10.5281/zenodo.15548394-orange.svg" alt="DOI">
  <img src="https://img.shields.io/badge/license-CC%20BY%204.0-lightgrey.svg" alt="License">
  <img src="https://img.shields.io/badge/languages-DE%20|%20EN-blueviolet.svg" alt="Languages">
</p>

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [Research Context](#research-context)
- [Corpus Description](#corpus-description)
  - [Sources](#sources)
  - [Content Types](#content-types)
  - [Temporal Coverage](#temporal-coverage)
  - [Metadata](#metadata)
- [Data Structure](#data-structure)
  - [Field Descriptions](#field-descriptions)
    - [Metadata Fields](#metadata-fields)
    - [Structured Content](#structured-content)
- [File Structure](#file-structure)
  - [Naming Conventions](#naming-conventions)
- [Download](#download)
  - [Complete Corpus](#complete-corpus)
  - [Subcorpora](#subcorpora)
  - [Data Formats](#data-formats)
  - [System Requirements](#system-requirements)
  - [Quick Start](#quick-start)
- [License \& Usage](#license--usage)
- [Contributors](#contributors)
- [Citation](#citation)
- [References](#references)
- [Contact](#contact)
- [Acknowledgments](#acknowledgments)

## Overview

This corpus was created to study **Chronorhetorics** - the relationship between temporal language patterns and political enforcement in political discourse. The dataset enables computational linguistic analysis of how political actors use temporal references to advance their political projects and legitimize power.

> **⚠️ Work in Progress:** This corpus is currently under active development. While we are making it available for research purposes, please be aware that additional content may be added over time, data structure changes may occur as we refine our approach, and field modifications might happen based on research needs and technical considerations. We recognize that some current technical design decisions may not be optimal and are subject to revision. Researchers using this corpus should expect potential updates and changes. We recommend checking back regularly for updates and versioning information.

## Research Context

Our work explores the concept of **Chronopolitics**, specifically focusing on "politicized time" - time employed as a weapon of politics and a means of legitimizing political programs (Esposito & Becker, 2023). We investigate:

- How patterns and linkages between political and temporal language can be made visible using computational linguistics
- How these patterns manifest, especially in contexts of looming conflict and crises

## Corpus Description

### Sources

The corpus contains various forms of political speeches from multiple official and archival sources:

**Government Sources:**
- **US White House** - Presidential remarks and speeches
  - Current: [whitehouse.gov/remarks/](https://www.whitehouse.gov/remarks/)
  - Biden Archive: [bidenwhitehouse.archives.gov](https://bidenwhitehouse.archives.gov/)
  - Trump Archive: [trumpwhitehouse.archives.gov/remarks/](https://trumpwhitehouse.archives.gov/remarks/)
  - Obama Archive: [obamawhitehouse.archives.gov](https://obamawhitehouse.archives.gov/briefing-room/speeches-and-remarks)
  - Bush Archive: [georgewbush-whitehouse.archives.gov](https://georgewbush-whitehouse.archives.gov/index.html)

- **Russian Presidential Speeches** - Kremlin transcripts and statements (English translations)
  - [tadadit.xyz/datasets/kremlin.ru_ru/](https://tadadit.xyz/datasets/kremlin.ru_ru/) (base dataset)
  - [en.kremlin.ru/events/president/transcripts](http://www.en.kremlin.ru/events/president/transcripts) (updated through March 2025)

- **German Bundestag** - Parliamentary debates and proceedings
  - Historical: [GermaParl corpus](https://www.uni-due.de/politik/germaparl.php) (Blätte & Blessing, 2018)
  - Recent: [bundestag.de/services/opendata](https://www.bundestag.de/services/opendata)

- **German Chancellor Speeches** - Olaf Scholz addresses
  - [bundeskanzler.de/bk-de/aktuelles/reden](https://www.bundeskanzler.de/bk-de/aktuelles/reden)

- **Ukrainian Presidential Speeches** - Volodymyr Zelenskyy addresses (English translations)
  - [president.gov.ua/en](https://www.president.gov.ua/en)

- **UK House of Commons** - Parliamentary speeches and debates
  - [parliament.uk](https://parliament.uk) (Hansard archives)
  - [parser.theyworkforyou.com/hansard.html](https://parser.theyworkforyou.com/hansard.html) (XML dataset)

**Specialized Collections:**
- **Munich Security Conference** - Annual conference speeches (1963-2024)
  - [MSC Speeches Collection](https://securityconference.org/assets/MSC_Speeches_1963_2024_Ansicht.pdf)

- **Hitler Speeches** - Adolf Hitler speeches from Max Domarus collections
  - Domarus, Max. *Hitler: Speeches and Proclamations 1932-1945* (Volumes 1 & 2)

### Content Types

- Public addresses and announcements
- Parliamentary debates and proceedings
- Public interviews and hearings
- Holiday announcements and ceremonial speeches

### Temporal Coverage

- **Time span**: 1919 - March 2025
- **Languages**: German (de), English (en)
- **Total size**: Over 90% of tokens come from Bundestag and House of Commons speeches

### Metadata

Each speech includes standardized metadata:
- Date of speech
- Speaker information (individuals and institutions)
- Language code
- Source institution
- Speech type/context

## Data Structure

Each speech in the corpus is stored as a JSON object with standardized metadata and structured content. Here's an example:

```json
{
  "id": "DE-Bundeskanzler-Speech-Scholz-0001",
  "url": "https://www.bundeskanzler.de/bk-de/aktuelles/...",
  "title": "Rede von Bundeskanzler Scholz anlässlich der State of the World Sessions...",
  "source_language": "de",
  "source_type": "Person",
  "source_name": "Bundeskanzler Scholz",
  "date": "Mittwoch, 19. Januar 2022",
  "date_iso": "2022-01-19T00:00:00",
  "location": "Davos",
  "structured_content": [
    {
      "type": "speech",
      "sequence": 1,
      "speaker": "Bundeskanzler Scholz",
      "text": "Sehr geehrter Herr Professor Schwab..."
    }
  ]
}
```

### Field Descriptions

#### Metadata Fields
- **id**: Unique identifier mostly following the pattern `{COUNTRY}-{INSTITUTION}-{TYPE}-{SPEAKER}-{NUMBER}`
- **url**: Original source URL of the speech
- **title**: Full title of the speech or address
- **source_language**: Language code (de/en)
- **source_type**: Type of speaker (Person/Institution)
- **source_name**: Name of the speaker or institution
- **date**: Human-readable date in original language
- **date_iso**: ISO 8601 formatted date for computational processing
- **location**: Location where speech was delivered (if available)

#### Structured Content
The `structured_content` field contains an array of speech segments, each representing a distinct part of the political discourse. The structure and available fields vary depending on the source type and institutional context.

**Common fields across all sources:**
- **sequence**: Numerical order of the segment within the document
- **text**: Full text content of the segment

**Content type identifiers:**
- `"speech"`: Primary speech content
- `"question"`: Parliamentary questions or audience questions
- `"answer"`: Responses to questions
- `"interjection"`: Parliamentary interruptions, applause, or audience reactions
- `"interruption"`: Formal parliamentary interruptions
- `"procedural"`: Procedural statements or announcements
- `"procedural_note"`: Administrative notes and formal procedures
- `"section_header"`: Agenda items or major section dividers
- `"subsection_header"`: Minor headings within larger sections

**Speaker information (varies by source):**

*Simple speeches (White House, Kremlin):*
- **speaker**: String with speaker name

*Parliamentary sources (Bundestag, House of Commons):*
- **speaker**: Object containing detailed information:
  - `name`: Full name of the speaker
  - `person_id`: Unique identifier for the person (may be null)
  - `party`: Political party affiliation (may be null)
  - `parliamentary_group`: Parliamentary group membership (Bundestag only)
  - `role`: Role type (`"mp"`, `"presidency"`, `"minister"`, etc.)
  - `position`: Specific position (`"Präsident"`, `"Alterspräsident"`, etc.)

**Source-specific fields:**

*Bundestag documents include:*
- **bundestag_id**: Internal Bundestag segment identifier
- **content_type**: More specific content categorization
- **legislative_period**: Parliamentary term number
- **session_no**: Session number within the legislative period

*House of Commons documents include:*
- **hansard_id**: Unique Hansard identifier for each segment
- **xml_tag**: Original XML structure tag from Hansard archives
- **files_combined**: List of source XML files used to construct the document

## File Structure

The corpus is organized into two main categories based on the source type:

```
chronorhetorics-corpus/
└── data/
    ├── institution/
    │   ├── msc/
    │   ├── parliament/
    │   │   ├── de-bundestag/
    │   │   └── uk-house-of-commons-protocols/
    │   ├── ru-putin-speeches/
    │   └── us-white-house-remarks/
    │       ├── biden/
    │       ├── bush/
    │       ├── obama/
    │       ├── trump17/
    │       └── trump25/
    └── person/
        ├── de-bundeskanzler-speeches/
        ├── de-hitler-speeches/
        └── ua-zelenskyy-speeches/
```

### Naming Conventions

**Standard Format:**
Most files follow the pattern: `{COUNTRY}-{INSTITUTION}-{TYPE}-{SPEAKER}-{NUMBER}.json`

Examples:
- `DE-Bundestag-Protocol-0001.json`
- `US-WhiteHouse-Remarks-Biden-0042.json`
- `DE-Bundeskanzler-Speech-Scholz-0007.json`

**Munich Security Conference (MSC) Format:**
MSC files use a specialized naming format: `MSC-{YEAR}-{SPEAKER-NAME}-Speech.json`

Examples:
- `MSC-1966-Karl-Theodor-Freiherr-von-und-zu-Guttenberg-Speech.json`
- `MSC-2015-Angela-Merkel-Speech.json`
- `MSC-2022-Volodymyr-Zelenskyy-Speech.json`

## Download

The Chronorhetorics Corpus is available for download through Zenodo:

### Complete Corpus

**Zenodo Repository** (Recommended)
- **Full Corpus**: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.15548394.svg)](https://doi.org/10.5281/zenodo.15548394)
- Direct download: [zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-all.zip](https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-all.zip?download=1)

### Subcorpora

For researchers interested in specific political systems or time periods:

| Subcorpus | Time Coverage | Description | Size | Download |
|-----------|---------------|-------------|------|----------|
| **German Political Speeches** | 1949 - March 2025 | Bundestag debates + Chancellor speeches | ~3.44GB | [Download](https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-de-political-speeches.zip?download=1) |
| **US Presidential Speeches** | 2003 - March 2025 | White House remarks (Bush-Biden) | ~207MB | [Download](https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-us-presidential-speeches.zip?download=1) |
| **UK House of Commons Protocols** | 1919 - March 2025 | House of Commons Hansard | ~2.1GB | [Download](https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-uk-house-of-commons-protocols.zip?download=1) |
| **Ukrainian Presidential Speeches** | 2019 - March 2025 | Ukrainian President Zelenskyy speeches | ~8.3MB | [Download](https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-ua-zelenskyy-speeches.zip?download=1) |
| **Russian Presidential Speeches** | 1999 - March 2025 | Kremlin transcripts (English) | ~122.3MB | [Download](https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-russian-presidential-speeches.zip?download=1) |
| **Hitler Speeches** | 1933 - 1945 | Hitler speeches from Domarus collections | ~2.7MB | [Download](https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-hitler-speeches.zip?download=1) |
| **International Conferences** | 1966 - March 2025 | Munich Security Conference | ~744KB | [Download](https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-international-conferences.zip?download=1) |

### Data Formats

- **JSON**: Structured data with full metadata

### System Requirements

- **Disk Space**: ~5.9GB for complete corpus

### Quick Start

```bash
# Download and extract
wget https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-all.zip
unzip chronorhetorics-corpus-v1.0-all.zip

# Basic usage (Python)
import json
with open('data/speeches/bundestag/DE-Bundestag-Protocol-0001.json', 'r') as f:
    speech = json.load(f)
    print(speech['title'])
```

## License & Usage

This corpus is licensed under Creative Commons Attribution 4.0 International (CC BY 4.0).

By downloading and using the corpus, you agree to:

- Cite the corpus appropriately in any publications using the provided citation format
- Respect the terms of use for derivative datasets (GermaParl, etc.)
- Attribute the work when redistributing or creating derivative works
- Use the data for research, educational, and commercial purposes as permitted under CC BY 4.0

To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/ 

## Contributors

- **Dr. Florian Nieser** - Heidelberg Center for Digital Humanities (HCDH), Heidelberg University
- **Jonathan Gaede** - Heidelberg Center for Digital Humanities (HCDH), Heidelberg University  
- **David Schatz** - Heidelberg Center for Digital Humanities (HCDH), Heidelberg University
- **Dr. Stefan Pietrusky** - Heidelberg Center for Digital Humanities (HCDH), Heidelberg University

## Citation

If you use this corpus in your research, please cite:

```bibtex
@dataset{nieser2025chronorhetorics,
  title={Chronorhetorics Corpus: Political Speeches for Temporal-Political Analysis},
  author={Nieser, Florian and Gaede, Jonathan and Schatz, David and Pietrusky, Stefan},
  year={2025},
  institution={Heidelberg Center for Digital Humanities, Heidelberg University},
  url={https://zenodo.org/records/15548394/files/chronorhetorics-corpus-v1.0-all.zip}
}
```

## References

Blaette, Andreas (2017): GermaParl. Corpus of Plenary Protocols of the German Bundestag. TEI files, available at: https://github.com/PolMine/GermaParlTEI.

Divita, David. "Radical-right populism in spain and the strategy of chronopolitics." *History and Theory*, 62/4:3–23, 2023.

Domarus, Max. *Hitler: Speeches and Proclamations 1932-1945*. Volumes 1 & 2. Wauconda, IL: Bolchazy-Carducci Publishers.

Esposito, Fernando and Tobias Becker. "The time of politics, the politics of time, and politiced time: An introduction to chronopolitics." *Language in Society*, 52:757–781, 2023.

## Contact

If you have any questions about the corpus or research, feel free to reach out to the members of the HCDH!

## Acknowledgments

This research was conducted at the Heidelberg Center for Digital Humanities (HCDH), Heidelberg University. We thank the institutions that make their political speeches publicly available, enabling this research.

**Special acknowledgments:**
- The **GermaParl project** (Blätte & Blessing, 2018) for providing comprehensive German parliamentary data
- The **German Bundestag's open data portal** for transparency and open government data access
- **Tadadit.xyz / Giorgio Comai** for providing the foundational Kremlin speeches dataset
- **Munich Security Conference** for making historical speeches available
- **TheyWorkForYou.com** for providing the comprehensive Hansard XML dataset that enabled UK parliamentary data integration
- Various government archives and institutions for maintaining accessible speech collections

---
