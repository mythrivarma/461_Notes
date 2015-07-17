#QlikView Tutorial#
**Completed till page: 23, Skipped "Working With Qlikview" Section. Current Page:179**

##Introduction ##
* QlikView standalone can be used for free, as a Personal Edition. With QlikView Personal Edition you can make full use of the QlikView functionality, but it is not possible to open documents created by other users. To do this, you need a QlikView license
* The QlikView product group also includes QlikView Server and QlikView Publisher that can be used for centralized management of QlikView applications, for automated updates and for distribution of documents to several users. Documents published on a QlikView Server can be accessed by different clients including Internet Explorer Plugin, AJAX Zero Footprint and several mobile clients such as iPhone, iPad, Android and RIM devices.
* 

##Working with QlikView##
*Skipped

##Creating a Document##
* A QlikView document is created by retrieving data from one or several sources, e.g. from a relational database or from text files containing data tables. This retrieval is done by writing and executing a script, in which the database, the tables and the fields to be retrieved are specified. The script can be generated automatically with the tools included in QlikView. Note that QlikView in itself is not a traditional database, i.e. you cannot add or alter data in the source database.
* For two fields to be associated, they need to have the exact same name (case sensitive). Thus, Name and name are not the same and will not be associated.
* If a certain field has the exact same value in several different input tables, QlikView will treat it as one value and also assume that the records (rows) containing the value should be associated.Thus: Name and name are not the same and are not associated. The numbers 123 and 00123 are the same and are associated.
* If two tables that have exactly the same set of fields are loaded, QlikView automatically treats the second table as a continuation of the first. This is called concatenation of tables.
* Sometimes you want to concatenate tables also when they have different sets of fields. QlikView will then not automatically concatenate the two tables: you need to use the concatenate statement, which concatenates a table with the last created logical table.
* Structures with circular references, i.e. when the chain becomes a ring, should usually be avoided. These are sometimes a sign of an incorrect data model, in which two similar fields that have slightly different interpretations are treated as one and the same field. If QlikView discovers the circular reference during the execution of the script, the tables will be set to loosely coupled. For further information, see the QlikView Reference Manual.
* When loading data from files, QlikView uses the file names as table names in the document. Unfortunately, in real life the data source files do not always have meaningful, self-explanatory names. In these case you can and should assign adequate
table labels to the tables when loading them in the script. This is done by stating the table label followed by a colon right before the load statement loading the table.
* Themes are very useful because you only need to create a layout formatting once, then copy it to any new documents that you create. The basic idea is to “extract” layout settings from an existing QlikView document to a theme file, and then apply the
same settings to the new document.
* The file associated with a field value will be shown, played, executed, etc. depending on the file type. Some file types, e.g. files of the bmp (images) or wav (sounds) type are handled internally in QlikView. For other file types, the associated program is used to open the document. --Should Check This!! . If you use the key word BUNDLE before INFO, Then the pictures will be Embedded in the Qlikview document.
* 
* 


