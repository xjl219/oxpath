## **IMPORTANT: NEWER VERSIONS OF OXPATH WILL BE AVAILABLE [HERE](http://www.oxpath.org/download/)** ##

## OXPath extends XPath for web data extraction, adding: ##


  * **Actions**, allowing the simulation of user actions (e.g., click, form filling) to interact with the scripted multi-page interfaces of web applications.

  * **Extraction Markers**, a new kind of qualifier, to identify nodes as representative for records and to form attributes from extracted data.

  * **Style Axis and Visible Field**, allow node and form field selection based on visual features by exposing all CSS properties via a new axis called style.

  * **Intensional Axes**, to relate nodes through multiple conditions, e.g., to select all nodes which are at the same vertical position and have the same color as the current node, which is not expressible in XPath.

OXPath runs in a real browser, therefore every site rendered by a modern browser can be interacted with and extracted with perfect accuracy. For this, OXPath from version 2.0 relies on [WebDriver](http://code.google.com/p/selenium/) (supported Firefox <=28 only). However, when a full browser is not necessary, OXPath can be used with the headless browser emulator [HTMLUnit](http://htmlunit.sourceforge.net/). OXPath allows for storing the extracted data as XML, RDF or Relational Database. Further, a custom output handler can be provided.
See the project page http://www.oxpath.org for more information.

For a complete description and to cite OXPath, please refer to the article
[OXPath: A language for scalable data extraction, automation, and crawling on the deep web](http://www.oxpath.org/papers/2013--vldbj--oxpath-a-language-for-scalable-data-extraction-automation-and-crawling-the-deep-web.pdf) [(bibtex)](http://dblp.uni-trier.de/rec/bibtex/journals/vldb/FurcheGGSS13)

