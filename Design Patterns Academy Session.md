#Day 1#
* ODS (Operational Data Store) is like a Staging DB before you push to WareHouse. We can do cleansing, Integration etc mostly technical operations on data and mostly we dont handle any business logic here. 
* ODS will be Normalized just like OLTP. We can Also generate Operational Reports from ODS. 
* OLTP to STG to ODS to DW to DM - this is Kimball approach. 
* INMON top down approach OR Kimball Bottom up Approach. Kimball is popular. 
* Why do we need STG DB? because generally we dont have access to OLTP for much time (because they want OLTP to be fast and stable). So may be 1 hr per day , we will get a chance to accessit. During that time we should just pull data and Store data in STG db and do further actions on that data to move it to warehouse later. So, this kind of Loading into staging first is nothing but ELT (Load first and transform later). Check what exactly is ELT in google. 
* ODS is needed if you have ER modelling in your warehouse. But if you use Dimensional Modeling and have proper Audit Columns in the FACT table, then We dont need ODS for Operational Reports. We can get them from DW itself. 
* INMON suggests ER model. Kimball suggests Dimensional Model. Query Performance will be better in kimball model. 
* MDM (Meta Data Repository) this holds Metadata for all DB systems in the BI Architechture. Some people maintain it in Excel files (Data Dictionary) which is not Reliable. 
* WHat has happened, Why it happened, How it happened?, what will happen, How to improve what will happen - These are five questions that a good BI System should be able to answer. 
* One draw back of Kimball Bottom Up Approach is that integration is difficult. THere is also a hybrid approach where in the Design phase we follow Top down Approach (Inmon) and then for the rest of phases (Dev, testing, UAT etc) we follow Kimball Approach (Bottom Up).
* Conformed dimension : is a common dimension on various departments in Bus Matrix. Example Time Dimension. 
* Dimensions are also called as subjects in Kimbal dimensional Model. and departments are nothing but processess. 
* Data Profiling should be done by person who understands DATA. 
* Kimbal suggests Normalized Fact (With most detailed level of grain) and De-normalized Dimension (which means clubbing related dimensions(Subjects) to a single Dimension Table).
* Data-Vault Modelling is a latest modelling design in which is completely flexible (with respect to adding or removing dimensions). drawbacks of this are, it is very complex to implement and also BI tools cannot directly access it as of now. So, in the current models, Star-Schema (kimball Dimensional Model) is a flexible model in which removing dimenison is good but adding dimension is still not really very flexible.
* SCD : Actually Type1 means no history and hence by definition of DW, Type 1 should not be in DW. So, generally we should avoid Type1. Type2 maintains Complete History. Type 3 is partial History. Kimball does not suggest Type 3. Best Approach for SCD is Type 2. 
* One reason for why people go to Type3 Scd is if we have Curr and Prev entry in the same row, when we are querying for a report which compares current previous data, we can do it with single query instead of multiple query (if Type2 were used) and hence performance will be better.
* Modelling - Conceptual - Logical - Physical Models. Conceptual comes from Client input. Logical model will be done by Modeller based on Conceptual Model by adding Attributes, Dimensions, Facts. Importance of Conceptual Model is it is a quick way to ensure that we and client are on the same page. If we directly start with Logical Model, THe client will be confused with the model since it is technical and complex and also we need lot of time to build Logical model and if what ever we built is not correct then all the time we spent is waste. 
* Data Stewardship : intorduced by Inmon. THis for securing the Data structure and Data as per business rules and one person (Data Steward) will have access to impose such constraints or Keys and if any one wants to make any changes, they need to contact him. 
* ELT - Oracle Data Integrator (ODI) uses ELT method. Informatica uses ETL method. 
* Opertaional Reports (Can be taken from OLTP Generally), Tactical Reports (Short term Strategic reports) and Strategic reports (Long term Stractegic reports).
* The Name DASHBOARD for BI is actually taken from CAR Dashboard. It actually means, Like the Dashboard in car, All the items that the user needs are placed on the dashboard (like Tabs in qlikview) and he can select what ever he wants. This is benefecial from traditional hierarchial approach because hierarchieal reports frustate the user and this causes the user to not use the bi tool itself (Imagine how frustated you will be if the items on the car dashboard are in hierarchieal manner).
* SUbject-Oriented, Non-Volatile, Time Variant and Integrated. These are the four pillars of Datawarehouse. OLTP is a process oriented design. DWH is a Subject oriented Design. 
* DATA MART is a Datawarehouse for a Specific Domain/process or a set of closely related processes. Whether it is DWH or Datamart, Dimensional Model is the best way to go if performance is the key. Two Types of Datamarts : Dependent and Independent. Kimbal Approach is Bottomup which means, build Datamart first and then warehouse. Inmon Approach is Topdown Approach, that  is to build DWH first and then Data Marts. Inmon Approach leads to Dependent Datamart. Kimball approach leads to Independent Datamarts.
* ODS is mostly used for B2B Transactions.. WHy?
* Federated Datawarehouse (Check Google).

#Day 2#
