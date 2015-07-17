#QlikView Tutorial#
**Completed till page: 23, Skipped "Working With Qlikview" Section. Current Page:146**

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
* 


