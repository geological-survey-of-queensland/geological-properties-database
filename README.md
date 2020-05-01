# Geological Properties Database

One of the primary purposes of the Geological Survey of Queensland (GSQ) is to improve the understanding of resource potential in Queensland.

GSQ creates, collects and provides geoscience data, information and advice on mineral resources, coal resources, coal seam gas, petroleum including unconventional petroleum, oil shale and geothermal energy within the State of Queensland. GSQ creates this knowledge through a range of geoscience projects and initiatives including industry exploration grants.

The GSQ seeks to develop an understanding of the geological properties of the State of Queensland, both at surface and in the sub-surface.

## Important - Semantic Sensor Network Ontology!
The Geoproperties Database is based on the SOSA ontology. If you understand this ontology, you will understand geoproperties.

The Semantic Sensor Network (SSN) ontology https://www.w3.org/TR/vocab-ssn/ is an ontology for describing sensors and their observations, the involved procedures, the studied features of interest, the samples used to do so, and the observed properties, as well as actuators. 

SSN follows a horizontal and vertical modularization architecture by including a lightweight but self-contained core ontology called SOSA (Sensor, Observation, Sample, and Actuator) for its elementary classes and properties. 

With their different scope and different degrees of axiomatization, SSN and SOSA are able to support a wide range of applications and use cases, including satellite imagery, large-scale scientific monitoring, industrial and household infrastructures, social sensing, citizen science, observation-driven ontology engineering, and the Web of Things.

## The Geological Properties Database
The Geological Survey of Queensland is creating a new Geological Properties database as the single source of truth for historical and new data.

### Objectives of the Geological Properties Database
* Replace the existing Surface Geology functionality in the MERLIN system.  
* Replace the Cores and Cuttings functionality in MERLIN.  
* Replace the Mineral Occurrences functionality in MERLIN.  
* Replace the Aerial Geophysics functionality in GEM.  
* Replace the Seismic Survey functionality in GEM.  
* Capture the primary Geochemical data recorded in the Explorer3 system.  
* Provide a repository for new data created by the department.  
* Provide a repository for new data submitted to the department.

## Geological properties data model
<p align="center">
<img src="https://github.com/geological-survey-of-queensland/ssor-database/blob/master/images/geological-properties-model.svg" width="560"><br>
Figure 1: Geological properties data model</p>

### A plain English definition
We seek to understand the geological properties of a geological or administrative feature. We undertake a survey on the feature at a site. The site may comprise of the whole feature, part of the feature, or may encompass and extend beyond the feature. The survey yields samples that may be physical, such as a drillcore, or non-physical proxies such as photographs. We conduct observations on the samples using various procedures. The observation yields results as measured values or qualitative descriptions. We interpret the results to understand the geological properties of the feature.

## SSOR Examples
|SOSA Category|Borehole|Geophysics|Geochemistry|
|---|---|---|---|
|Feature|Bowen Basin|Queensland|Mary Kathleen U Deposit|
|Site|Well:<br>Fair Gully 1|Extent:<br>GSQ NWQ Gravity Survey 2020|Extent:<br>GSQ-2020 surface sampling campaign<br>Sub-site: Field Site GSQ-S01 (-20.744088, 140.013291)|
|Survey|Wireline:<br>FG1-Run-200|Survey:<br>GSQ-Grav-2020-1|Sample collection:<br>GSQ-S01|
|Sample|LAS File:<br>Fair Gully 1 MAINLOG.las*|Gravity Intensity Grid:<br>GSQ2020-A1 GravAn.gri*<br>Sub-Sample: Pixel (25736,4646)|Handsample:<br>HS035<br>-(processing: crush, split, seive)-><br>Sub-Sample: HS035-A1C-S80|
|Observation|Density Log (490mMD)|Gravity Intensity|XRF uranium reading |
|Result|1.62 g/cc|9791197.22 ums-2|142ppm(U)|

*array data such as LAS files, grids, and images may theoretically have atomised results, but practically may be only be described in the Geological Properties Database to the survey or sample level with the array data preserved in their original file formats as associated dataset resources.

## Understanding Surveys vs Observations

SOSA has a concept of an observation collection (what we call a survey). This collection can have one or more members. e.g. A Geophysical Observation Collection can have a gravity observation and a radiometric observation. See https://www.w3.org/TR/vocab-ssn-ext/#sosa:ObservationCollection

<p align="center">
<img src="https://www.w3.org/TR/vocab-ssn-ext/images/observation-collection.png" width="50%"><br>
Model for an observation-collection, in which the collection may carry one or more of the properties of its members if they have a shared value for all members</p>

### Aligning terminology between SOSA and Geoproperties

| SOSA                   | Geoprops           |
|------------------------|--------------------|
| Observation Collection | Survey             |
| Observation            | Observation Type   |
| Procedure              | Observation Method |
| Sensor                 | Instrument         |

### Example mapping

| Survey Type | Survey Method | Observation Type     | Observation Method | Observation Instrument       |
|-------------|---------------|----------------------|--------------------|------------------------------|
| Seismic     | Ground        | 2D Seismic           | Vibroseis          | Geophone make, model         |
| Seismic     | Marine        | 3D Seismic           | Air Gun            | Air Gun make model           |
| Geophysics  | Airborne      | Electromagnetic      | VTEM               | VTEM instrument make model   |
| Geophysics  | Ground        | Electromagnetic      | SkyTEM             | SkyTEM instrument make model |
| Geophysics  | Airborne      | Gravity Gradiometery | Falcon             | Helifalcon                   |
| Geophysics  | Ground        | Electrical           | DC Resistivity     | 10 kW Scintrex               |

### Definitions
#### Geological property
* The observable or measureable properties of a geological or administrative feature.  
* Examples: mineralogy, hydrocarbon properties, water properties, stratigraphy, engineering data.  

#### Geological or administrative feature
* Geological features have properties that are of interest for commercial, environmental and societal reasons.  
* Administrative features are spatial features that are defined and managed by regulatory agencies.
* Examples: basin, province, trough, craton, orogen, permit, sub-block, resource accumulation.
* See [GSQ Geological and Administrative Features vocabulary](https://vocabs.gsq.digital/vocabulary/gsq-features) and [GSQ Geo Admin Features Ontology](https://github.com/geological-survey-of-queensland/gsq-geoadminfeatures-ont)
* See [sosa:FeatureOfInterest](https://www.w3.org/TR/vocab-ssn/#SOSAFeatureOfInterest)

#### Site
* A location within, or wholly encompassing, a geological or administrative feature.  
* Where a survey is undertaken.
* A site may be a component of a larger site.
* Examples: outcrop, borehole, stream, seismic line, seismic shot-point.
* See the [GSQ Site Profile](https://github.com/geological-survey-of-queensland/gsq-site-profile)

#### Survey
* The one-off event examining a geological or administrative feature. 
* Surveys are activities that produce samples.
* The type of exploration work.   
* ```Survey``` is synonymous with the term ```Sampling```, and with the term ```Project``` in the geochemistry dataset. 
* Examples: seismic survey, geochemical survey, gravity survey, magnetotelluric survey.
* See [Exploration Work Types](https://github.com/geological-survey-of-queensland/ssor-database/blob/master/Exploration%20work%20type.md)
* See [GSQ Survey Profile](https://github.com/geological-survey-of-queensland/gsq-survey-profile)
* See [sosa:Sampling](https://www.w3.org/TR/vocab-ssn/#SOSASampling)

#### Sample
* The enduring extract that a survey produces.  
* Synonymous with ```specimen```.
*	The sample is a representative part a whole geological feature.
* Samples may be **original samples**, **subsamples** where a new sample is split into smaller samples, or **duplicates** - identical samples.
* A sample may be surveyed to produce a new sample or sub-sample e.g. An image (sample) may be the produced from an aerial photographic survey, each pixel within that image is a sub-sample.
* Examples: drill core, drill cuttings, soil sample, hand specimen, water, photograph, LAS file.
* See the [GSQ Sample Profile](https://github.com/geological-survey-of-queensland/gsq-sample-profile)
* See [sosa:Sample](https://www.w3.org/TR/vocab-ssn/#SOSASample)

#### Observation
* An act of carrying out an observation using a _procedure_ to measure, estimate or calculate a value of a geological or administrative feature, a site, or a sample.
* Observations are activities that produce results.
* Examples: field measurements, hyperspectral scanning, inductively coupled plasma spectrometry  
* See the [GSQ Observation Profile](https://github.com/geological-survey-of-queensland/gsq-observation-profile)
* See [sosa:Observation](https://www.w3.org/TR/vocab-ssn/#SOSAObservation)

#### Result
* The result of the observation performed on a sample, stored as a value together with the unit.  
* Examples: 
  - Physical properites, e.g. concentration, mass, temperature
  - Petrographic descriptions
  - Geophysical measurements e.g. gravity, magnetic field strength
  - Petrophysical log measurements e.g. gamma, density, resistivitiy.
* See [Units of measure](https://github.com/geological-survey-of-queensland/ssor-database/blob/master/Units%20of%20measure.md)
* See [sosa:Result](https://www.w3.org/TR/vocab-ssn/#SOSAResult)

## Geological Properties Database conceptual data model
<p align="center">
<img src="https://github.com/geological-survey-of-queensland/ssor-database/blob/master/images/geological-properties-conceptual-ERD.png"><br>
Figure 1: Geological Properties Conceptual Model</p>


## Geological Property data elements
|Data Element|Remarks|Source|DataType|Length|
|---|---|---|---|---|
|Geological property ID|A unique identifer|System|-|-|
|Geological property name|A textual name|User|-|-|
|Geological property type|Lookup to controlled list of property types|Vocab|-|-|
|Geological property status|Lookup to controlled list of status|Vocab|-|-|

## Geoadmin Feature data elements
|Data Element|Remarks|Source|DataType|Length|
|---|---|---|---|---|
|Feature ID|A unique identifer|System|-|-|
|Feature name|A textual name|User|-|-|
|Feature type|Lookup to controlled list of feature types|Vocab|-|-|
|Feature status|Lookup to controlled list of status|Vocab|-|-|
|Feature relationship|Records relationship between features|User|-|-|
|Feature geometry|Spatial representation(s) of feature|WKT|-|-|

## Site data elements
|Data Element|Remarks|Source|DataType|Length|
|---|---|---|---|---|
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

> Question: Do we record the stratigraphy at the site level?

## Survey data elements
|Data Element|Remarks|Source|DataType|Length|
|---|---|---|---|---|
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

## Samples data elements
|Data Element|Remarks|Source|DataType|Length|
|---|---|---|---|---|
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
|Data Element|Remarks|Source|DataType|Length|
|---|---|---|---|---|
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
|Data Element|Remarks|Source|DataType|Length|
|---|---|---|---|---|
|Result ID|A unique identifer|System|-|-|
|Result type|Geochem, hydrocarbons, biostratighy, geochronology?|Vocab|-|-|
|Analyte|Element, oxide, compound, or property that was determined or measured by the laboratory. |-|-|-|
|Value|Numeric or textual value|[QUDT](https://www.qudt.org/)|-|-|
|Unit of measure|Controlled list of measures|[QUDT](https://www.qudt.org/)|-|-|

> Does ```detection upper limit``` and ```detection lower limit``` fit in Results or Observations? Do we need them? Or do we just use, e.g.  __Values less than the lower limit of determination are negative (absolute value of the number given is the lower limit of determination) while values greater than the upper limit of determination are the upper limit with a .1111 suffix.__

## Geological Properties Database vocabularies
- Geological properties type -  _to be developed in future release_
- [Geoadmin feature type](https://vocabs.gsq.digital/vocabulary/gsq-features)
- [Geoadmin feature status](https://github.com/geological-survey-of-queensland/vocabularies/raw/master/vocabularies/qld-resource-permit-status.ttl) aka Permit Status
- Geoadmin feature relationship type _use site_relationship? what else is needed?_
- [Site types](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/gsq-sites.ttl)
- Site detail type -  _Need Clarification_
- [Site relationship](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/site-relationships.ttl)
- [Site status](https://github.com/geological-survey-of-queensland/vocabularies/raw/master/vocabularies/site-status.ttl)
- [Borehole purpose](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/borehole-purpose.ttl)
- [Borehole sub-purpose](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/borehole-sub-purpose.ttl)
- [Depth reference datum](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/depth-reference-datum.ttl) - To supercede Borehole Depth Datum. To use for any depth or elevation reference.
- [Borehole design](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/borehole-design.ttl)
- [Borhole origin circumstance](http://catalogue.linked.data.gov.au/index.php/resource/51)
- [Borehole drilling method](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/borehole-drilling-method.ttl)
- [Borehole Status and Site Status](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/site-status.ttl) _collections_ of borehole and minocc
- [Borehole status event](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/borehole-status-event.ttl)
- [Resource Project Lifecycle and Borehole Class](https://github.com/geological-survey-of-queensland/vocabularies/raw/master/vocabularies/resource-project-lifecycle.ttl)
- [Organisation Roles](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/gsq-roles.ttl)
- Geometry type -  _file type list?_
- [QLD Coordinate Reference Systems](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/qld-crs.ttl)
- [QLD UTM Zones](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/qld-utm-zones.ttl)
- [Survey type](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/survey-type.ttl)
- [Survey method](https://github.com/geological-survey-of-queensland/vocabularies/raw/master/vocabularies/survey-method.ttl)_note:use "svymh:seismic-methods a skos:Collection ;" where survey_type==seismic
- [Survey status](http://linked.data.gov.au/def/mining-survey-status)
- Survey detail type -  _Need clarification_
- [Sample type](https://github.com/geological-survey-of-queensland/vocabularies/raw/master/vocabularies/sample-type.ttl) _need to reconcile with [Sample Type](https://vocabs.ands.org.au/viewById/185)_
- [Sample method](http://linked.data.gov.au/def/sampling-method)
- [IGSN code](https://vocabs.ands.org.au/viewById/188)
- [Sample material type](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/sample-material.ttl)
- Sample relationship type _further work and clarification needed. Same as site type + derivedFrom, collectedWith, contains (for composites),associate, twinOf_ 
- [Sample facility](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/gsq-sample-facility.ttl) -  (Zillmere or Mt Isa)
- [Sample location status](https://raw.githubusercontent.com/geological-survey-of-queensland/vocabularies/master/vocabularies/sample-location-status.ttl)
- Sample detail type -  _Need clarification_
- [Sample location detail type](https://github.com/geological-survey-of-queensland/vocabularies/raw/master/vocabularies/sample-location-details.ttl)
- [Observation type](https://github.com/geological-survey-of-queensland/vocabularies/raw/master/vocabularies/observation-type.ttl)
- [Sample preparation](https://github.com/geological-survey-of-queensland/vocabularies/raw/master/vocabularies/sample-preparation.ttl)
- Observation detail type -  _Need clarification_
- [Result type](https://github.com/geological-survey-of-queensland/vocabularies/raw/master/vocabularies/result-type.ttl)
- Unit of measure -  _Integration with QUDT vocabulary to be done by NC_ [temporary vocab](https://github.com/qudt/qudt-public-repo/raw/master/vocab/unit/VOCAB_QUDT-UNITS-ALL-v2.1.ttl)
- [Data Access Rights](http://linked.data.gov.au/def/data-access-rights)

### Reference vocabs that may be used or harvested
- [Sample type](https://vocabs.ands.org.au/viewById/185)  
- [Observation Method](https://vocabs.ands.org.au/viewById/89)
- [Exploration Result](https://vocabs.ands.org.au/viewById/77)
- [Sampling Method](https://vocabs.ands.org.au/viewById/195)
- [Exploration Activity Type](https://vocabs.ands.org.au/viewById/79)
- [Analysis](https://vocabs.ands.org.au/viewById/189)
- [Instruments/Sensors](https://vocabs.ands.org.au/viewById/241)
- [NEII Observation Method](https://vocabs.ands.org.au/viewById/167


## Mapping to MERLIN tables
| Data Concept | MERLIN table | Comments |
|---|---|---|
|Geological Property|--|minocc?|
|Geoadmin Feature|--|--|
|Site|sgf_sites|--|
|Survey|sgf_survey|--|
|Sample|sgf_sample|--|
|Observation|sgf_explore_techniques|--|
|Result|sgf_analysis_results|--|


## Mapping to GEM Aerial Geophysics Surveys tables
| Data Concept | GEM table | Comments |
|---|---|---|
|Geological Property|--|--|
|Geoadmin Feature|Aerial geophysics spatial extent|--|
|Site|AerialGeophysicalTenure|--|
|Survey|AerialGeophysicalSurvey|--|
|Sample|--|--|
|Observation|--|--|
|Result|--|--|

## Mapping to GEM Seismic Surveys tables
| Data Concept | GEM table | Comments |
|---|---|---|
|Geological Property|--|--|
|Geoadmin Feature|--|--|
|Site|--|--|
|Survey|SeismicSurvey|--|
|Sample|--|--|
|Observation|--|--|
|Result|--|--|

## Mapping to Explorer3 tables
| Data Concept | Explorer3 table | Comments |
|---|---|---|
|Geological Property|--|--|
|Geoadmin Feature|--|--|
|Site|h_Loc|--|
|Survey|h_Suvey|--|
|Sample|h_Sample - drillhole samples<br>s_RC - rockchip samples<br>s_Soil - soil samples<br>s_Seds - stream sediment samples<br>s_WholeRock - wholerock samples|--|
|Observation|--|--|
|Result|--|--|

## Mapping to Geological Site Observation Database For Queensland (REGMAP)
Data in the Geological observation database is derived from the Surface Geology System in MERLIN. The data has been decoded and concatenated into simple, relational database structures with MS Access software interfaces and in-built forms and queries to interrogate the data.

The data compiled includes rock types, rock characteristics (e.g. colour, grain size, texture etc), structural measurements and formation name. See [Geological site observation database for Queensland (REGMAP).pdf](https://github.com/geological-survey-of-queensland/ssor-database/blob/master/files/Geological%20site%20observation%20database%20for%20Queensland%20(REGMAP).pdf) and [database_of_site_observations.png](https://github.com/geological-survey-of-queensland/ssor-database/blob/master/images/database_of_site_observations.png)

In the future, this publication will be able to produced from the data in the Geological Properties database.

| Table | -- | Comments |
|---|---|---|
|Agedets|--|--|
|Biblio|--|--|
|Comprep|h_Loc|--|
|Coord_conversion|--|--|
|Interval|--|--|
|Interval_Obs|--|--|
|Interval_Structure|--|--|
|Location|--|--|
|Mag_Sus|--|--|
|Petrography|--|--|
|Rock|--|--|
|Rock_Obs|--|--|
|Rock_Structure|--|--|
|Samples|--|--|
|Text|--|--|
|Whole Rock Geochem|--|--|

## Mapping to Mineral Occurrence Data for Queensland Database (MINOCC)
The MINOCC database is a MS Access database with mine information, sites by commodity, geology reports for mines, production and resources, deposit models. The data is derived from MERLIN. See [MinOccDB in CSV format.zip](https://github.com/geological-survey-of-queensland/ssor-database/blob/master/files/MinOccDB%20in%20CSV%20format.zip) and [minocc_database.png](https://github.com/geological-survey-of-queensland/ssor-database/blob/master/images/minocc_database.png)

In the future, this publication will be able to produced from the data in the Geological Properties database. 

| Table | -- | Comments |
|---|---|---|
|Biblio|--|--|
|Company reports|--|--|
|Det_Model|h_Loc|--|
|Explorer|--|--|
|Gen_Model|--|--|
|Host_Rock|--|--|
|Location|--|--|
|MineHist|--|--|
|OrebodyObs|--|--|
|OrebodyOrient|--|--|
|Oremin_Age|--|--|
|OreObs|--|--|
|Production|--|--|
|Resources|--|--|
|Tenure|--|--|
|Text|--|--|
|Total_Alluvial_Prod|--|--|
|Total_Ores_Prod|--|--|
|Workings|--|--|

## Derivation
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
**Mark Gordon**  
Geological Survey of Queensland  
Department of Natural Resources, Mines and Energy  
Brisbane, QLD, Australia  
<mark.gordon@dnrme.qld.gov.au>  

*Author*:  
**David Crosswell**  
Enterprise Architect  
Cross-Lateral Enterprises  
<https://crosslateral.com.au>  
