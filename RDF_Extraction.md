The following OXPath expression shows how to extract data from real estate properties (on a test page), converting it to RDF triple.


```

doc('http://diadem.cs.ox.ac.uk/test/re/fast/wwagency/')//select#sale_type_id/{0 /}
                                                      //button.formbtn/{click /}
   /(/descendant::a.pagenum[last()]/{click /})*{0,1}
          //div.proplist_wrap:<gr:Offering>
             [? .//span.prop_price/text():<dd:hasPrice(xsd:double)=substring-after(.,'£')> ]
             [? .//div.prop_img/a/@href:<foaf:page=string(.)> ]
             [.:<gr:includes(dd:House)>
                [? .//ul.prop_keypoints/li[1]/strong:<dd:bedrooms=string(.)> ]
                [? .//ul.prop_keypoints/li[2]/strong:<dd:bathrooms=string(.)> ]
                [? .//strong.orange:<vcard:postal-code=string(.)> ]
                //div.prop_img/a/{click /}//body
		[? .//div#breadcrumb/text()[last()]:<vcard:locality=string(.)> ]
		[? .//div#propertypage_copy/p[1]:<gr:description=string(.)> ]
             ]

   
```


Note how OXPath allows shortcuts borrowed from CSS selectors (e.g, . and # ).

A sample of the output for a single property looks like

```

dd:v1126581762173694c
      dd:hasPrice "449,950"^^xsd:double ;
      gr:includes dd:v1126581762295351c ;
      foaf:page "/property-in-oxford/Spring-Lane-Littlemore-OX4/589"


dd:v1126581762295351c
      a       dd:House ;
      dd:bathrooms 2 ;
      dd:bedrooms 4 ;
      gr:description "Substantial detached family house providing well proportioned living space throughout, immaculate condition, enclosed corner plot with driveway and two private garages." ;
      vcard:locality " » Spring Lane Littlemore OX4            " ;
      vcard:postal-code "OX4" .
```


Namespace abbreviations are specified in the configuration file, for instance

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<oxpath xml:space="preserve">
<rdf>
	<outputfile>path/to/out/file</outputfile>
	
	<prefixmapping>    
	        <prefix>gr</prefix>
	        <namespace>http://purl.org/goodrelations/v1#</namespace>
	</prefixmapping>
	<prefixmapping>
		<prefix>vcard</prefix>
		<namespace>http://www.w3.org/2006/vcard/ns#</namespace>
	</prefixmapping>
	<prefixmapping>
		<prefix>dd</prefix>
		<namespace>http://your.namespace#</namespace>
	</prefixmapping>
	<prefixmapping>
		<prefix>foaf</prefix>
		<namespace>http://xmlns.com/foaf/0.1/</namespace>
	</prefixmapping>
	<resultnamespace>http://your.namespace/ontologies/real-estate#</resultnamespace>
	<rdfoutputformat>TURTLE</rdfoutputformat>
</rdf>
</oxpath>
```

Sources to run this example are available for downloading.