Final work report of Google Summer of Code 2021 with Hydra Ecosystem

# Google Summer of Code 2021 with Hydra Ecosystem
<div  align="center">
  
![GSOC_hydra](https://user-images.githubusercontent.com/49719371/130039150-d2017ef4-7886-4d9e-99ac-eb58b12a9784.png)

 ## [Building a banking service with Open Risk and Hydra](https://summerofcode.withgoogle.com/projects/#4830252137709568)
  
</div>

17th May 2021, my [proposal](https://docs.google.com/document/d/1VeSUJR7RQ4sBU9tPrb6qQYWoA2iPVdnoN_Pqw0VWQ8w/edit?usp=sharing) got selected for Google Summer of code'21 with [Hydra Ecosystem](https://www.hydraecosystem.org/), It was the most happiest moment in my life. My project was aimed to Build a [Hydra-powered](https://github.com/HTTP-APIs/) API for serving the loan portfolio managment with [Open-Risk](https://www.openriskmanagement.com/).

## :paperclip: Introduction
It was an amazing journey developing a project from scratch to mainting the repository, I have learned a lot of new thing, which are added in my developers bucket and will surely be heplful in the future.
The idea behind the project is to build a prototype of "APIs for Fintech" with Hydra Ecosystem.

#### Here's the brief idea behind the project: 

<div  align="center">
  
![Introduction](https://user-images.githubusercontent.com/49719371/130047355-379a8da0-9104-4c99-acd0-59f46af53afe.png)
  </div>  

## :paperclip: Working Product
The Final completed project can be found here:

#### Project's Repo : https://github.com/HTTP-APIs/creditrisk-poc
#### Project is live @ http://34.145.188.116:8080/

## :paperclip: Work and Contributions

We started with building a subset of POC with small Non-Performing Loan ontology. After the sucessfull completion of subset POC, we moved forward with the comlpete Non-Performing Looan ontlogy (All the classes and properties required for Loan portfolio data), where I needed to automate the creation of ApiDocumentation for which I have written two automation scripts:

* **Vocab_generator:**
vocab_generator generates “NonPerformingLoan.jsonld” using rdflib and pyld libraries to parse & serialize owl ontology to JSON-LD with the @context.
* **nplvocab_parser:**
nplvocab_parse parses all the classes & properties from“NonPerformingLoan.jsonld” and converts them to HydraClass & HydraClassProp. 

![Automation_structure](https://user-images.githubusercontent.com/49719371/130070526-077366f3-2def-4a8e-8f58-94aae8c4ce2c.png)

With the help of there two scripts `api_docwriter.py` generates the ApiDocumentation automatically according to Non-performing Loan ontology.

I have also developed `Mock_portfolio_generator` which is basically used as a mock_client to populate the database with the more realistic data, It automatically creates the object of the classes on the basis of ApiDocumentation.
Then I have Re-structured the complete repository according to the python standards and write test using pytest for the API.<br/>
While working with the creditrisk-poc we encountered an issue that the class attributes (columns) in the database are of type VARCHAR by default for every property in hydrus. After a good discussion with the mentors it was decisde that it's better to have attributes of a similar type as in the hydra property,
So my GSoC collegue implemented this feature in the hydrus and hydra-python-core, and then finally I was able to use it in creditrisk-poc successfully.
After the comlpletion of all these task I have tested the API on local system and got it reviewed with the mentors, now we were ready for the last stage i.e **DEPLOYMENT :rocket:**


[Here](https://drive.google.com/file/d/1HWd72JVtf13P7DdTF3Er2870FVx7c9BM/view?usp=sharing) is the final Database schema with the foreign key relation.

With the help of my GSoC collegue we have dockerized the application and tested it, we have also changed the database from sqlite to postgres.
Then I deployed the application Google Cloud Platform's compute engine and the API is live @ **http://34.145.188.116:8080/ :tada::tada:**

### Pull requests

| PR Link                                                                                                                                                              | Description                                              | Status    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- | --------- |
| [#1](https://github.com/HTTP-APIs/creditrisk-poc/pull/1) |NPL Jsonld for POC | Merged ✅ |
| [#3](https://github.com/HTTP-APIs/creditrisk-poc/pull/3) |API Doc Created & hydrus setup.| Merged ✅ |
| [#87](https://github.com/HTTP-APIs/hydra-python-core/pull/87)|HydraClass default endpoint set True| Merged ✅ |
| [#89](https://github.com/HTTP-APIs/hydra-python-core/pull/89)|@context updated to W3C version| Merged ✅ |
| [#2](https://github.com/HTTP-APIs/creditrisk-poc/pull/2)|Create README.md| Merged ✅ |
| [#7](https://github.com/HTTP-APIs/creditrisk-poc/pull/7)|Repository re-structured.| Merged ✅ |
| [#9](https://github.com/HTTP-APIs/creditrisk-poc/issues/9)|Create integration testing code| Merged ✅ |
| [#12](https://github.com/HTTP-APIs/creditrisk-poc/pull/12)|Functionality tests added.| Merged ✅ |
| [#13](https://github.com/HTTP-APIs/creditrisk-poc/pull/13)|readme updated| Merged ✅ |
| [#14](https://github.com/HTTP-APIs/creditrisk-poc/pull/14)|Collateral class added| Merged ✅ |
| [#8](https://github.com/HTTP-APIs/creditrisk-poc/pull/8)|README.md updated & Functional doc added.| Merged ✅ |
| [#17](https://github.com/HTTP-APIs/creditrisk-poc/pull/17)|ApiDoc Automation script created & mock portfolio data generator refectored.| Merged ✅ |
| [#19](https://github.com/HTTP-APIs/creditrisk-poc/issues/19)|Owl -> Jsonld automation script created.| Merged ✅ |
| [#21](https://github.com/HTTP-APIs/creditrisk-poc/pull/21)|Datatypes for DB implemented | Merged ✅ |
| [#22](https://github.com/HTTP-APIs/creditrisk-poc/pull/22)|Readme & docs updated, test for iri collection added| Merged ✅ |
| [#23](https://github.com/HTTP-APIs/creditrisk-poc/pull/23)|Test doc added| Merged ✅ |
| [#24](https://github.com/HTTP-APIs/creditrisk-poc/pull/24)|Final ApiDoc created, nplo jsonld & mock_portfolio_generator refactored| Merged ✅ |
| [#28](https://github.com/HTTP-APIs/creditrisk-poc/pull/28)|hydrus version upadated| Merged ✅ |

### Issues


| Issue link                                                                          | Description                                                        |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| [#4](https://github.com/HTTP-APIs/creditrisk-poc/issues/4) |Create NonPerforming Jsonld vocabulary|
| [#5](https://github.com/HTTP-APIs/creditrisk-poc/issues/5) |Create API_Doc & Setup hydrus|
| [#6](https://github.com/HTTP-APIs/creditrisk-poc/issues/6) |[Discussion] Check datatype of properties in the database|
| [#9](https://github.com/HTTP-APIs/creditrisk-poc/issues/9) |Create integration testing code|
| [#11](https://github.com/HTTP-APIs/creditrisk-poc/issues/11) |Add collateral class|
| [#74](https://github.com/HTTP-APIs/creditrisk-poc/issues/74)|Change hydra core fetching in context.|
| [#86](https://github.com/HTTP-APIs/creditrisk-poc/issues/86)|HydraClass default endpoint should be True|
| [#15](https://github.com/HTTP-APIs/creditrisk-poc/issues/15) |Create Automated script for creating NPL Vocabulary|
| [#16](https://github.com/HTTP-APIs/creditrisk-poc/issues/16) |Refactor the mock_data_generator|
| [#18](https://github.com/HTTP-APIs/creditrisk-poc/issues/18) |Automate ontology to josnld creation|
| [#20](https://github.com/HTTP-APIs/creditrisk-poc/issues/20) |Update Readme & Add more docs|
