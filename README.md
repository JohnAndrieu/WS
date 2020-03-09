# WS

## Partie 2 : Interrogation de la base de connaissances sur le cinéma

PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX : <http://www.semanticweb.org/nathalie/ontologies/cinemaTP#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>

SELECT ?film ?gps
WHERE {
  ?film a ?LabelFilm .
  ?LabelFilm rdfs:label "film"@fr .
  ?film :seDerouleA ?lieu .
  ?lieu :aPourGPS ?gps
}

PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX : <http://www.semanticweb.org/nathalie/ontologies/cinemaTP#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>

SELECT (group_concat(?nomFilms; separator=' ; ') as ?listeFilms) (count(?lesfilms) as ?nbfilms) ?gps
WHERE {
  ?lesfilms a ?LabelFilm .
  ?LabelFilm rdfs:label "film"@fr .
  ?lesfilms rdfs:label ?nomFilms .
  ?lesfilms :seDerouleA ?lieu .
  ?lieu :aPourGPS ?gps
}
GROUP BY ?gps
