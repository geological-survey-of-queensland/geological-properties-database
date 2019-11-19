# Sites, samples, observations &amp; results database <br>(Geological Properties Database)

One of the primary purposes of the Geological Survey of Queensland (GSQ) is to improve the understanding of resource potential in Queensland.

GSQ creates, collects and provides geoscience data, information and advice on mineral resources, coal resources, coal seam gas, petroleum including unconventional petroleum, oil shale and geothermal energy within the State of Queensland. GSQ creates this knowledge through a range of geoscience projects and initiatives including industry exploration grants.

The GSQ seeks to develop an understanding of the geological properties of the State of Queensland, both at surface and in the sub-surface.

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

* Example:
  - Feature:      _Bowen Basin_
  - Site:         _Wellname 1_
  - Survey:       _Petrophysical Logging Job 1_
  - Sample:        _LAS file_
  - Observation:   _Density Curve Analysis_
  - Result:        _1.62 g/cc @ 490mMD_

  - Geological Property: The density of material is 1.62g/cc at 490m measured depth located in Wellname 1 within the Bowen Basin. 
  
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
* The type of exploration work.   
* ```Survey``` is synonymous with the term ```Project``` in the geochemistry dataset. 
* Examples: seismic survey, geochemical survey, gravity survey, magnetotelluric survey.
* See [Exploration Work Types](https://github.com/geological-survey-of-queensland/ssor-database/blob/master/Exploration%20work%20type.md)
* See [GSQ Survey Profile](https://github.com/geological-survey-of-queensland/gsq-survey-profile)
* See [sosa:Sampling](https://www.w3.org/TR/vocab-ssn/#SOSASampling)

#### Sample
* The enduring extract that the survey of the a produces.  
* Synonymous with ```specimen```.
*	The sample is a representative part a whole geological feature.
* Samples may be **original samples**, **subsamples** where a new sample is split into smaller samples, or **duplicates** - identical samples.
* Examples: drill core, drill cuttings, soil sample, hand specimen, water, photograph, LAS file.
* See the [GSQ Sample Profile](https://github.com/geological-survey-of-queensland/gsq-sample-profile)
* See [sosa:Sample](https://www.w3.org/TR/vocab-ssn/#SOSASample)

#### Observation
* An act of carrying out an observation using a _procedure_ to measure, estimate or calculate a value of a geological or administrative feature.
* Examples: field measurements, hyperspectral scanning, inductively coupled plasma spectrometry, 
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
TO DO  

## Geological Property data elements
|Data Element|Remarks|Source|
|---|---|---|
|Geological property ID|A unique identifer|System|
|Geological property name|A textual name|User|
|Geological property type|Lookup to controlled list of property types|Vocab|
|Geological property status|Lookup to controlled list of status|Vocab|
|-|-|-|
|-|-|-|

## Geoadmin Feature data elements
|Data Element|Remarks|Source|
|---|---|---|
|Feature ID|A unique identifer|System|
|Feature name|A textual name|-|
|Feature type|Lookup to controlled list of feature types|Vocab|
|Feature status|Lookup to controlled list of status|Vocab|
|Feature relationship|Records relationship between features|-|
|Feature geometry|Spatial representation(s) of feature|-|
|-|-|-|

## Site data elements
|Data Element|Remarks|Source|
|---|---|---|
|Site ID|A unique identifer|System|
|Site name|A textual name|User|
|Site type|A controlled list of site types|Vocab|
|Site relationship|Records relationship between sites|System|
|Site geometry|Spatial representation(s) of the site|WKT|
|Site start date|Date active from|xsd:date|
|Site end date|Date set to inactive|xsd:date|
|Site details|Site-specific additional information|User|

> NOTE: A borehole is a specialised type of site. See the [GSQ Borehole Database conceptual design](https://github.com/geological-survey-of-queensland/borehole-database). The Borehole Database is a component of the Geological Properties database.

> Question: Do we record the stratigraphy at the site level?

## Survey data elements
|Data Element|Remarks|Source|
|---|---|---|
|Survey ID|A unique identifer|System|
|Survey title|A textual name|User|
|Survey description|A textual description|User|
|Survey type|Lookup to controlled list of survey types|Vocab|
|Survey operator|Lookup to controlled list of organisations|Lookup|
|Survey status|Lifecycle status of the survey|Vocab|
|Survey dimensionality|2D, 3D, 4D, etc.|Vocab|
|Surveying instrument|Ideally a controlled list|Vocab?|
|Survey start time|Commencement date|xsd:date|
|Survey end time|Completion date|xsd:date|
|Survey geometry|Spatial representation of the survey|WKT|
|Access Rights|Controls user and system access to the resource|Vocab|
|Dataset link|Links to related datasets including raw data|Hyperlink|

## Samples data elements
|Data Element|Remarks|Source|
|---|---|---|
|IGSN number|A globally unique identifer|[ANDS IGSN minting service](https://www.ands.org.au/online-services/igsn-service)|
|IGSN object type|IGSN registered object type|[IGSN Codelist](https://vocabs.ands.org.au/viewById/188)|
|Sample alias|Alternative sample label defined by sample collector|User|
|Sample title|A textual title|User|
|Sample method|Controlled list of methods|Vocab|
|Sample type|Controlled list of sample types|Vocab|
|Sample description|A textual description|User|
|Material type|Controlled list of materials|Vocab|
|Lithology|NOTE: This goes in results?|--|
|Parent sample|Records subsample relationship to original sample|--|
|Date acquired|Lookup to controlled list of organisations|xsd:date|
|Acquired by|Lookup to controlled list of organisations|Lookup|
|Current location|Can link to EDC location|--|
|Sampling allowed|Flag|--|
|Base|Origin height|[QUDT](https://www.qudt.org/)|
|Sample top|--|[QUDT](https://www.qudt.org/)|
|Sample bottom|--|[QUDT](https://www.qudt.org/)|
|Vertical datum|Australian Height Datum|[AHD](https://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/ahdgm/ahd)|
|Geometry|Spatial representation of the sample|--|
|Coverage|3 letter country code|[ISO 3166](https://www.iso.org/iso-3166-country-codes.html)|
|State|State or Territory|[ASGS](https://www.abs.gov.au/websitedbs/D3310114.nsf/home/Australian+Statistical+Geography+Standard+\(ASGS\))|
|Access rights|Controls user and system access to the resource|Vocab|
|Dataset link|Links to related datasets including raw data|Hyperlink|

## Observation data elements
|Data Element|Remarks|Source|
|---|---|---|
|Observation ID|A unique identifer|System|
|Observation type|Procedure or method|Vocab|
|Observation date|-|xsd:date|
|Observation top|-|[QUDT](https://www.qudt.org/)|
|Observation bottom|-|[QUDT](https://www.qudt.org/)|
|Observer|e.g. laboratory name (from org list)|Vocab|
|Job no|Laboratory job/batch nummber|User|
|Assay code|Laboratory assay code|Vocab|
|Sample preparation|Ideally a controlled list|Vocab?|
|Observation instrument|Ideally a controlled list|Vocab?|


## Result data elements
|Data Element|Remarks|Source|
|---|---|---|
|Result ID|A unique identifer|System|
|Result type|Geochem, hydrocarbons, biostratighy, geochronology?|Vocab|
|Analyte?|Element, oxide, compound, or property that was determined or measured by the laboratory. |-|
|Value|Numeric or textual value|[QUDT](https://www.qudt.org/)|
|Unit of measure|Controlled list of measures|[QUDT](https://www.qudt.org/)|

> Does ```detection upper limit``` and ```detection lower limit``` fit in Results or Observations? Do we need them? Or do we just use, e.g.  __Values less than the lower limit of determination are negative (absolute value of the number given is the lower limit of determination) while values greater than the upper limit of determination are the upper limit with a .1111 suffix.__

## Geological Properties Database vocabularies
- [Geoadmin features](https://vocabs.gsq.digital/vocabulary/gsq-features)
- [Sample method](https://vocabs.gsq.digital/vocabulary/sampling-method)
- [Data Access Rights](https://vocabs.gsq.digital/vocabulary/data-access-rights)
- [Sample method](https://vocabs.gsq.digital/vocabulary/sampling-method) (requires review)
- [Survey status](https://vocabs.gsq.digital/vocabulary/survey-status)
- Observation types (new)
- Site types (new)
- Survey types (new)

### Reference vocabs that may be used or harvested
- [Sample type](https://vocabs.ands.org.au/viewById/185)  
- [IGSN Codelist](https://vocabs.ands.org.au/viewById/188)
- [Observation Method](https://vocabs.ands.org.au/viewById/89)
- [Exploration Result](https://vocabs.ands.org.au/viewById/77)
- [Sampling Method](https://vocabs.ands.org.au/viewById/195)
- [Sampling Procedure](https://vocabs.ands.org.au/viewById/153)
- [Sample Type](https://vocabs.ands.org.au/viewById/185)
- [Exploration Activity Type](https://vocabs.ands.org.au/viewById/79)
- [Analysis](https://vocabs.ands.org.au/viewById/189)
- [Instruments/Sensors](https://vocabs.ands.org.au/viewById/241)
- [NEII Observation Method](https://vocabs.ands.org.au/viewById/167)


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


## Derivation
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
Geological Survey of Quensland  
Department of Natural Resources, Mines and Energy  
Brisbane, QLD, Australia  
<mark.gordon@dnrme.qld.gov.au>  

*Author*:  
**David Crosswell**  
Enterprise Architect  
Cross-Lateral Enterprises  
<https://crosslateral.com.au>  
