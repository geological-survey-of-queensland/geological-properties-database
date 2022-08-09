# Geological Properties Database

One of the primary purposes of the Geological Survey of Queensland (GSQ) is to improve the understanding of resource potential in Queensland.

GSQ creates, collects and provides geoscience data, information and advice on economic resources and seeks to develop an understanding of the geological properties of the State of Queensland, both at surface and in the sub-surface.

## Important! - Semantic Sensor Network Ontology (SOSA)
The [Sensor, Observation, Sample, and Actuator (SOSA)](https://www.w3.org/TR/vocab-ssn/) ontology provides a formal but lightweight general-purpose specification for modelling the interaction between the entities involved in the acts of observation, actuation, and sampling, the activity of which is called a "sensor". It assists with describing the relationships between database properties and entities. It is built upon the The Semantic Sensor Network (SSN) ontology, a framework for producing machine-processable representation of sensor capabilities, properties, observations and measurement processes. 

The Geoproperties Database is based on the SOSA/SSN ontology. Understanding this ontology is key to understanding the Geological Properties Database. See Figure 1 (High-level Geological Properties data model) below for an example of applying this ontology GSQ's data. Items such as "isSurveyOf" and "hasResult" are SOSA/SSN terms describing the relationship between entities in the Geological Properties Database. 

## The Geological Properties Database
The Geological Survey of Queensland is creating a new Geological Properties database as the single source of truth for historical and new data. You may see it referred to as "GeoProperties" or simply "GeoProps".

### Objectives of the Geological Properties Database
GeoProps streamlined several disparate legacy databases within the Queensland Government by coalscecing them into a single system. It provides a repository for new and legacy data and metadata submitted to the Department. It acts as a point-of-truth for much of the georesource data and metadata generated within Queensland.

## Geological properties data model
<p align="center">
<img src="https://github.com/geological-survey-of-queensland/ssor-database/blob/master/images/geological-properties-model.svg" width="560"><br>
Figure 1: High-level Geological Properties data model (Full model in Figure 2 below)</p>

### A plain English definition
We seek to understand the geological properties of a geological or administrative 'Feature'. We undertake a 'Survey' on the Feature at a 'Site'. The Site may comprise the whole Feature, part of the Feature, or may encompass and extend beyond the Feature. The Survey yields 'Samples' that may be physical, such as a drillcore, or non-physical proxies such as photographs. We conduct 'Observations' on the Samples using various procedures. The Observation yields 'Results' as measured values or qualitative descriptions. We interpret the Results to understand the **geological properties** of the Feature.

The table below demonstrates how these database elements may relate to each other for different data types (Borehole, Geophysics, Geochemistry) with example information. 

| |**Borehole**|**Geophysics**|**Geochemistry**|
|---|---|---|---|
|**Feature**|Bowen Basin|Queensland|Mary Kathleen U Deposit|
|**Site**|Well:<br>Fair Gully 1|Extent:<br>GSQ NWQ Gravity Survey 2020|Field Site GSQ-S01 (-20.744088, 140.013291)|
|**Survey**|Wireline:<br>FG1-Run-200|Survey:<br>GSQ-Grav-2020-1|Sample collection:<br>GSQ-S01|
|**Sample**|LAS File:<br>Fair Gully 1 MAINLOG.las*|Gravity Intensity Grid:<br>GSQ2020-A1 GravAn.gri*<br>Sub-Sample: Pixel (25736,4646)|Handsample:<br>HS035<br>-(processing: crush, split, seive)-><br>Sub-Sample: HS035-A1C-S80|
|**Observation**|Density Log (490mMD)|Gravity Intensity|XRF uranium reading |
|**Result**|1.62 g/cc|9791197.22 ums-2|142ppm(U)|

### Definitions
#### Geological Property
The observable or measureable properties of a geological or administrative Feature. The properties are derived from the combined insight of multiple Observations on a Feature as conducted by a Survey. Examples include, but not limited to: mineralogy, hydrocarbon potential, hydrological properties, stratigraphy, and geologic age.  

#### Feature (Ultimate Geological or Administrative Feature of Interest)
Geological Features are spatially-bound entities that have properties of interest for commercial, environmental and societal reasons. They are discrete, complete and internally coherent entities upon which there exists a consensus for its prescribed existence. For example, a stratigraphic formation may be a Feature of Interest, which itself may sit withn a larger Ultimate Feature of Interest such as a geological basin.

Administrative Features are spatially-bound entities that are defined and managed by regulatory agencies. For example, the Queensland Government can issue a Resource Authority ("RA" or "Tenure") which prescribes the allowable work area for the resource company who holds that tenure. As multiple Surveys are conducted, Observations made, and Results obtained, the Tenure becomes the Ultimate Feature of Interest.

Essentially, the scale of investigation will determine the Ultimate Feature of Interest, which itself is a collection of sub-scale Features. 

* See [GSQ Geological and Administrative Features vocabulary](https://vocabs.gsq.digital/vocabulary/gsq-features) and [GSQ Geo Admin Features Ontology](https://github.com/geological-survey-of-queensland/gsq-geoadminfeatures-ont)
* See [sosa:FeatureOfInterest](https://www.w3.org/TR/vocab-ssn/#SOSAFeatureOfInterest)

#### Site (Proximate Feature of Interest)
A Site is an entity or location within, wholly encompassing, or intersecting an Ultimate Feature that acts as a proxy to represent that complete (ultimate) feature. A Feature of Interest is proximate when it _represents_ an ultimate feature, as opposed to being a discrete component of a larger feature. For example, an outcrop can be examined as a representitive of a formation, whereas a formation does not represent a whole basin but is a component of it. A Site may be a component of a larger Site, and may encompass or equate to the spatial boundaries of an Ultimate Feature of Interest. 

* See the [GSQ Site Profile](https://github.com/geological-survey-of-queensland/gsq-site-profile)

#### Survey
A Survey is a one-off time-bound event examining a Geological or Administrative Feature and describes the type of exploration, assessment, or processing work that produces Samples or Observations.. It involves a group of activities, such as Sampling and Observations, that occur together and have a defined realtionship, typically being conducted on a Site. For example, a resource company may decide to conduct three different surveys – geophysical, geochemical, and petrophysical – on a tenure they hold. 

* See [Exploration Work Types](https://github.com/geological-survey-of-queensland/ssor-database/blob/master/Exploration%20work%20type.md)
* See [GSQ Survey Profile](https://github.com/geological-survey-of-queensland/gsq-survey-profile)
* See [sosa:Sampling](https://www.w3.org/TR/vocab-ssn/#SOSASampling)

#### Sample
A Sample is an artefact produced that has enduring relevance and is a representative part of a Feature of Interest. It may be conducted as part of a Survey as part of sampling activities and is synonymous with "specimen" for physical artefacts.

A sample itself does not have to persist to have enduring relevance. For example, the Observations pertaining to a core plug or cuttings sample are still of interest even if the plug is destroyed, or cuttings are aggregated, or the sample is sub-sampled. 

Samples may be **original sample**, **sub-sample** (where a sample is split into smaller samples), **processed sample** (where a sample content is retained but is processed to have altered properties), or **duplicate sample** (an identical sample).

* See the [GSQ Sample Profile](https://github.com/geological-survey-of-queensland/gsq-sample-profile)
* See [sosa:Sample](https://www.w3.org/TR/vocab-ssn/#SOSASample)

#### Observation
An Observation is an act of carrying out a measurment using a _procedure_ to estimate, calculate a value of, or describe a feature, site or sample. Observations differ from sampling in that sampling yields an artefact (for example, a physical specimen), whereas an observation yields a qualitative or quantitative Results (for example, a table of geochemical measurements for multiple elements).

* See the [GSQ Observation Profile](https://github.com/geological-survey-of-queensland/gsq-observation-profile)
* See [sosa:Observation](https://www.w3.org/TR/vocab-ssn/#SOSAObservation)

##### Survey vs Observation - what's the difference?
For clarity, a 'Survey' is a singlular activity that may contain one or many 'Observations'. Essentially, a Survey is a collection of observations, or an [_Observation Collection_](https://www.w3.org/TR/vocab-ssn-ext/#sosa:ObservationCollection). For example, a 'Geophysical Observation Collection' may contain both magnetic observations and radiometric observations.

Further examples of Surveys and their potential Observations are shown below. 

| Survey Type | Survey Method | Observation Type     | Observation Method | Observation Instrument       |
|-------------|---------------|----------------------|--------------------|------------------------------|
| Seismic     | Ground        | 2D Seismic           | Vibroseis          | Geophone make, model         |
| Seismic     | Marine        | 3D Seismic           | Air Gun            | Air Gun make model           |
| Geophysics  | Airborne      | Electromagnetic      | VTEM               | VTEM instrument make model   |
| Geophysics  | Ground        | Electromagnetic      | Moving Loop EM     | Moving Loop EM make model    |
| Geophysics  | Airborne      | Gravity Gradiometery | Falcon             | Einstein                     |
| Geophysics  | Ground        | Electrical           | DC Resistivity     | 10 kW Scintrex               |

#### Result
A Result is a description or a value, including a unit of measure, of an Observation performed on a Sample. For example, physical properites (concentration, mass, temperature), petrographic descriptions, geophysical measurements (gravity, magnetic field strength), petrophysical log measurements (gamma, density, resistivity).

* See [Units of measure](https://github.com/geological-survey-of-queensland/ssor-database/blob/master/Units%20of%20measure.md)
* See [sosa:Result](https://www.w3.org/TR/vocab-ssn/#SOSAResult)

## Geological Properties Database Conceptual Data Model
<p align="center">
<img src="https://github.com/geological-survey-of-queensland/ssor-database/blob/master/images/geological-properties-conceptual-ERD.png"><br>
Figure 2: Geological Properties Conceptual Model</p>

## Geological Property Data Elements
|Data Element|Remarks|Source|
|---|---|---|
|Geological property ID|A unique identifer|System|-|-|
|Geological property name|A textual name|User|-|-|
|Geological property type|Lookup to controlled list of property types|Vocab|-|-|
|Geological property status|Lookup to controlled list of status|Vocab|-|-|

## Geoadmin Feature data elements
|Data Element|Remarks|Source|
|---|---|---|
|Feature ID|A unique identifer|System|-|-|
|Feature name|A textual name|User|-|-|
|Feature type|Lookup to controlled list of feature types|Vocab|-|-|
|Feature status|Lookup to controlled list of status|Vocab|-|-|
|Feature relationship|Records relationship between features|User|-|-|
|Feature geometry|Spatial representation(s) of feature|WKT|-|-|

## Site data elements
|Data Element|Remarks|Source|
|---|---|---|
|Site ID|A unique identifer|System|-|-|
|Site name|A textual name|User|-|-|
|Site description|A textual description|User|-|-|
|Site type|A controlled list of site types|Vocab|-|-|
|Site status|Lookup to controlled list of status|Vocab|-|-|
|Site status start date|Date status active from|xsd:date|-|-|
|Site status end date|Date status set to inactive|xsd:date|-|-|
|Site relationship|Records relationship between sites|System|-|-|
|Site geometry|Spatial representation(s) of the site|WKT|-|-|
|Site details|Site-specific additional information|User|-|-|
|Dataset link|Links to related datasets including raw data|Hyperlink|-|-|

> NOTE: A borehole is a specialised type of site. See the [GSQ Borehole Database conceptual design](https://github.com/geological-survey-of-queensland/borehole-database). The Borehole Database is a component of the Geological Properties database.

## Survey data elements
|Data Element|Remarks|Source|
|---|---|---|
|Survey ID|A unique identifer|System|-|-|
|Survey title|A textual name|User|-|-|
|Survey description|A textual description|User|-|-|
|Survey type|Lookup to controlled list of survey types|Vocab|-|-|
|Survey method|Lookup to controlled list of survey methods|Vocab|-|-|
|Survey permit|The permit(s) that survey was performed under|Lookup|-|-|
|Survey status|Lifecycle status of the survey|Vocab|-|-|
|Survey operator|Lookup to controlled list of organisations|Lookup|-|-|
|Survey start time|Commencement date|xsd:date|-|-|
|Survey end time|Completion date|xsd:date|-|-|
|Survey geometry|Spatial representation of the survey|WKT|-|-|
|Survey access rights|Controls user and system access to the resource|Vocab|-|-|
|Survey details|Survey-specific additional information|User|-|-|
|Dataset link|Links to related datasets including raw data|Hyperlink|-|-|

## [Samples data elements](https://github.com/geological-survey-of-queensland/gsq-sample-profile)
|Data Element|Remarks|Source|
|---|---|---|
|IGSN number|A globally unique identifer|[ANDS IGSN minting service](https://www.ands.org.au/online-services/igsn-service)|-|-|
|Sample title|A textual name|User|-|-|
|Sample alias|An alternative identifier for the sample|User|-|-|
|Sample description|A textual description|User|-|-|
|IGSN object type|IGSN registered object type|[IGSN Codelist](https://vocabs.ands.org.au/viewById/188)|-|-|
|Sample alias|Alternative sample label defined by sample collector|User|-|-|
|Sample is result of|The survey that yielded the sample|User|-|-|
|Acquired by|Lookup to controlled list of organisations|Lookup|-|-|
|Date acquired|Lookup to controlled list of organisations|xsd:date|-|-|
|Sample method|Controlled list of methods|Vocab|-|-|
|Material type|Controlled list of materials|Vocab|-|-|
|Sample relationship|Records sample relationship to original sample|Vocab|-|-|
|Sampling allowed|Indicates if further sampling is allowed|Flag|-|-|
|Sample current location|Records physical location of sample (e.g. at EDC)|User|-|-|
|Current location|Can link to EDC location|--|-|-|
|Sampling allowed|Flag|--|-|-|
|Sample base|Origin height|[QUDT](https://www.qudt.org/)|-|-|
|Sample top|The top|[QUDT](https://www.qudt.org/)|-|-|
|Sample bottom|The bottom|[QUDT](https://www.qudt.org/)|-|-|
|Vertical datum|Australian Height Datum|[AHD](https://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/ahdgm/ahd)|-|-|
|Coverage|3 letter country code (AUS) for IGSN|[ISO 3166](https://www.iso.org/iso-3166-country-codes.html)|-|-|
|State|State or Territory (Queensland) for IGSN|[ASGS](https://www.abs.gov.au/websitedbs/D3310114.nsf/home/Australian+Statistical+Geography+Standard+\(ASGS\))|-|-|
|Access rights|Controls user and system access to the resource|Vocab|-|-|
|Sample details|Sample-specific additional information|User|-|-|
|Dataset link|Links to related datasets including raw data|Hyperlink|-|-|
|Sample geometry|Spatial representation of the sample|WKT|-|-|

## Observation data elements
|Data Element|Remarks|Source|
|---|---|---|
|Observation ID|A unique identifer|System|-|-|
|Observer|e.g. laboratory name (from org list)|Lookup|-|-|
|Observation type|Procedure or method|Vocab|-|-|
|Observation date|-|xsd:date|-|-|
|Observation top|-|[QUDT](https://www.qudt.org/)|-|-|
|Observation bottom|-|[QUDT](https://www.qudt.org/)|-|-|
|Sample preparation|Ideally a controlled list|Vocab?|-|-|
|Job no|Laboratory job/batch nummber|User|-|-|
|Assay code|Laboratory assay code|Vocab|-|-|
|Observation instrument|Ideally a controlled list|Vocab?|-|-|
|Observation details|Observation-specific additional information|User|-|-|

## Result data elements
|Data Element|Remarks|Source|
|---|---|---|
|Result ID|A unique identifer|System|-|-|
|Result type|Geochem, hydrocarbons, biostratighy, geochronology?|Vocab|-|-|
|Analyte|Element, oxide, compound, or property that was determined or measured by the laboratory. |-|-|-|
|Value|Numeric or textual value|[QUDT](https://www.qudt.org/)|-|-|
|Unit of measure|Controlled list of measures|[QUDT](https://www.qudt.org/)|-|-|

## Further reading
- [TERN Plot Ontology](http://www.linked.data.gov.au/def/plot/)
- [Minerals and coal reporting guideline (2019)](https://www.dnrme.qld.gov.au/mining-resources/initiatives/mineral-coal-reporting-guideline)
- [Petroleum and gas reporting guideline (2018)](https://www.dnrme.qld.gov.au/mining-resources/initiatives/pandg-reporting-guideline-2018)
- Government Geoscience Information Committee (GGIC) [Australian Requirements for the Submission of Digital Exploration Data](http://www.australiaminerals.gov.au/__data/assets/pdf_file/0004/60772/National_Guidelines_Version_4.5_February_18.pdf)
- [The Queensland Exploration Geochemistry And Drillhole Database and Database Packages Background information and operational guide](https://gsq-horizon.s3-ap-southeast-2.amazonaws.com/GEOCHEMISTRY+DATABASES/Geochemistry-data-instructions.pdf)
- [Geochemistry data model for the Open Geoscience Data Model](https://www.bgs.ac.uk/services/dataModels/geochemistry.html)
- [USGS National Geochemical Database data model](https://mrdata.usgs.gov/ngdb/sediment/about.php)
- [PPDM](https://ppdm.org) for petroleum and gas
- [GeoSciML](http://www.geosciml.org/) for minerals
- [CoalLog](https://ausimm.com/coal-log/) for coal  
- [IGSN](http://igsn.github.io/)
- [1EP Geoscience Project](http://appsuppt103/confluence/display/1EP/Geoscience)
- Geoscience Australia's [National Geochemical Survey of Australia Project](https://www.ga.gov.au/about/projects/resources/national-geochemical-survey). See also https://ecat.ga.gov.au/geonetwork/srv/eng/catalog.search#/metadata/65464
- Geoscience Australia's [Geochemistry and Geochronology Themes metadata](https://ecat.ga.gov.au/geonetwork/srv/eng/catalog.search#/metadata/65464)
- GSQ [Geological Observations Data Package](http://qdexdata.dnrm.qld.gov.au/QDEXDataDownloadManager/Results?type=Geology&id=GSQ%20Site%20Locations)
- GSQ [Mineral Occurence Data Package](http://qdexdata.dnrm.qld.gov.au/QDEXDataDownloadManager/Results?type=Geology&id=GSQ%20MinOcc)

## See also
* [Geoadmin features ontology](https://github.com/geological-survey-of-queensland/gsq-geoadminfeatures-ont)  
* [GSQ site profile](https://github.com/geological-survey-of-queensland/gsq-site-profile)  
* [GSQ survey profile](https://github.com/geological-survey-of-queensland/gsq-survey-profile)  
* [GSQ sample profile](https://github.com/geological-survey-of-queensland/gsq-sample-profile)
* [GSQ observation profile](https://github.com/geological-survey-of-queensland/gsq-observation-profile)

## Licence
This code repository's content are licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/), the deed of which is stored in this repository here: [LICENSE](LICENSE).

## Contacts
*System owner*:  
**Mark Gordon**,
Geological Survey of Queensland,
Department of Resources,
Brisbane, QLD, Australia,
<mark.gordon@resources.qld.gov.au>  

*Contributors*:  
**Vance Kelly**,
Principal Data Manager,
Geological Survey of Queensland,
Department of Resources,
Brisbane, QLD, Australia,  
<vance.kelly@resources.qld.gov.au>

**Luke Hauck**,
Geoscientist,
Geological Survey of Queensland,
Department of Resources,
Brisbane, QLD, Australia,
<luke.hauck@reosurces.qld.gov.au>

