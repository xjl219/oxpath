The following OXPath expression shows how to extract data from user profiles on Google Scholar, and save it into a database


```

doc("http://scholar.google.co.uk/")//input[@name='q']/{click/}
		//input[@name='q']/{"giovanni grasso oxford"/}
		//descendant::button[@name='btnG'][1]/{click/}
			//a[starts-with(.,'User profiles for')]/{click/}/
				(//div.cit-dgb[1]//td/a[.#='Next']/{click[wait=1]/})*
				//tr[contains(@class,"item")]:<paper>
				[?.//a.cit-dark-large-link:<title=string(.)>]
				[?.//td#col-title/span[1]:<authors=string(.)>]
				[? .//td#col-title/span[2]:<proc=string(.)>]
				[? .//a.cit-dark-link:<citations=string(.)>]
				[? .//td#col-year:<year=string(.)>]

   
```


Note how OXPath allows shortcuts borrowed from CSS selectors (e.g, . and # ).

A sample of the XML output for a single paper looks like

```

<paper>
    <title>OXPATH: A Language for Scalable Data Extraction, Automation, and Crawling on the Deep Web</title>
    <authors>T Furche, G Gottlob, G Grasso, C Schallhart, A Sellers</authors>
    <proc>The VLDB Journal 22 (1 - Special issue on best papers of VLDB 2011), 47-72</proc>
    <year>2013</year>
  </paper>
```


Sources to run this example are available for downloading.