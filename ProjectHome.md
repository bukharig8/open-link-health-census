<font color='green' size='3'><b>Exposing the Canadian health Census to LOD</b></font>

<font color='red' size='3'>HC2LOD won first prize in New Brunswick health research conference <a href='http://www.nbhrf.com/news/20131127/2013-nb-health-research-conference-poster-competition-results'>Detail</a></font>

<img src='http://ahmedchan.files.wordpress.com/2013/12/nbhrf-e1388692094164.png' alt='healthcensus' width='475' height='350' />

## Presentaion ##
<a href='http://www.youtube.com/watch?feature=player_embedded&v=VdasP1RKy-0' target='_blank'><img src='http://img.youtube.com/vi/VdasP1RKy-0/0.jpg' width='425' height=344 /></a>
## Goal: ##
  * Transforming the open Canadian Health health census data into RDF and hooking it up with LOD cloud

## Possible End users: ##
  * Application Developers
  * Government Agencies
  * NGOs to private businesses
  * Interested Citizens

## Benefits: ##
  * Health Care Need assessment and right decision making at right time
  * Better accountability on government policies regarding health sector
  * Its linkage with linked open data cloud improves the ability of developers in   developments (Mashups Development)

## Tools and Technologies: ##
  * Java as development language (Jena API)
  * D2RQ for mapping generation
  * Sesame triple store
  * Jetty Server
  * SPARQL

## Ontologies Use: ##

  * DBPedia
  * FOAF
  * SIOC
  * SKOS
  * Dublin Core
  * Relationship
  * Time
  * Aktor
  * Geo Nmaes
  * Chealth

## Possible SPARQL Queries: ##

====SPARQL Query 1:===  Show me the years and number of breast cancer patients survival reported among female patients between the ages of 40 to 49 years.

SELECT DISTINCT  ?year ?value WHERE {
?patient foaf:gender "Female".
?patient dbpedia:unitCost "Number of cases".
?patient dbpedia:statisticValue ?value.
?patient dbpedia:year ?year.
?patient foaf:age "40 to 49 years".
?patient rdf:type akt:person-being-visited.
}
ORDER BY DESC(?value)

=== SPARQL Query 2:===  Give me total number of breast feeding mothers from New Brunswick province that have the ages between 20 to 24.

SELECT count ()
Where {
?person dcterms:Location "New Brunswick".
?person rdf:type  bio:immediatelyPrecedingEvent.
?person foaf:age "20 to 24 years".
> }

=== SPARQL Query 3:===  Show the number of deaths reported due to Gallbladder and Prostate cancer among male patients Canada wise during 2001 to 2003.

SELECT DISTINCT ?death ?cancerType
Where {
?person foaf:gender "Male".
?person dbpedia:part "Gallbladder".
?person dbpedia:part "Prostate".
?person dbpedia:statisticValue ?death.
?Cancer dbpedia:part ?cancerType.
?year dbpedia:year  "2001 to 2003".
?person rdf:type akt:Knowledge-Lifecycle.
> }
Limit 50

=== SPARQL Query 4:===   Display the age group among female person from New Brunswick province who has maximum practice in smoking.

SELECT DISTINCT ?AgeGroup
Where{
?person rdf:type dbpedia:Activity.
?person foaf:gender "Female".
?person dcterms:Location "New Brunswick".
{
SELECT ?statval
Where{?person rdf:type dbpedia:Activity .
?person foaf:gender "Female" .
?person dcterms:Location "New Brunswick" .
?person dbpedia:statisticValue ?statval.
}
ORDER BY DESC(?statval)
limit 1
}
?person dbpedia:statisticValue ?statval.
?person foaf:age ?AgeGroup.
> }
LIMIT 10

=== SPARQL Query 5:===  Display the year and location and number of value where the people use jug filter and they are using non-municipal water supply between the year 2007 to 2009 in New Brunswick and British Columbia.

SELECT DISTINCT ?year ?location ?value{
?treatment rdf:type   geonames:U.SCNU.
?treatment  dbpedia:year  ?year.
Filter (?year>="2007<sup>^xsd:double" && ?year<="2009</sup>^xsd:double").
?treatment  dcterms:Location  ?location.
Filter (?location="New Brunswick" || ?location="British Columbia").
?treatment  dcterms:type "Used a jug filter".
?treatment  dcterms:type "non-municipal water supply".
?treatment  dbpedia:statisticValue ?value.
}

## Mapping Schema: ##
<img src='http://open-link-health-census.googlecode.com/files/mappingsemanticimage.jpg' alt='healthcensus' />

## SPARQL end point ##

<img src='http://open-link-health-census.googlecode.com/files/SPARQL%20QUERIES.png' alt='healthcensus' />

## Publication ##

We will update this section soon.



<a href='http://www4.clustrmaps.com/user/391107623'><img src='http://www4.clustrmaps.com/stats/maps-no_clusters/code.google.com-p-open-link-health-census--thumb.jpg' alt='Locations of visitors to this page' /></a>