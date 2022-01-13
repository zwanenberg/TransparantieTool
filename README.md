# Zwanenberg Food Group TransparantieTool

## Introduction
Zwanenberg Food Group requires from all meat suppliers to publish their transparancy information of the supply chain.  The prefered way to provide this information to Zwanenberg is by publishing this information in GS1 fTrace (https://web.ftrace.com/en/). In the situation that GS1 fTrace cannot be used, Zwanenberg can receive the transparancy information via a direct connection.

### via GS1 fTrace
You can publish the GTIN of the products that you sell to Zwanenberg Food Group to GS1 fTrace.
After publishing you can release the information (when, what, where) of the chain (origin, slaughtering, splitting, sending) to the GLN of Zwanenberg (08710581000017).

![1](https://user-images.githubusercontent.com/59997944/148361792-f1f74fe0-e856-471f-8569-7d974d94bf72.JPG)

For every batch/lot you send to Zwanenberg you need to update the information in fTrace.

### via ZFGTrace
In the situation that GS1 fTrace cannot be used, Zwanenberg can receive the transparancy information via a direct connection.

![2](https://user-images.githubusercontent.com/59997944/148362252-585c84b5-909f-48e8-a41d-701c8590ef2b.JPG)

For every delivery to a Zwanenberg plant you need to upload one XML file with the requested information. You can upload the XML via sFTP to our servers. Information about the sFTP connection will be provided to you after both parties have agreed about using this method instead and tested the first XML.

## XML
The information requested by Zwanenberg needs to be provided in a structered XML file.

This XML has the following structure:

- a **SUPPLIER** 
- delivers to a **RECEIVER**  
- one or more **PRODUCTS**
- Each **PRODUCT** has one or more **BATCHES**
- Each **BATCH** has 
- one or more **ORIGINS** where the meat was sourced from (farm)
- one or more **SLAUGHTERINGS** where the animal was slaughtered
- optional: one or more **SPLITTINGS** with internal procession steps
- optional: one or more **HANDOVERS** with combining internal batches to the final batch

### Supplier
```
<supplier>
    <id>04003730000001</id>
    <name>Gelderland</name>
    <county>Kleve</county>
    <municipality />
    <state>Nordrheinwestfalen</state>
    <country>DE</country>
    <reference />
    <date>20210210T092315+00:00</date>
  </supplier>
 ``` 
 
 The supplier section is mandatory. We need an ID which is a GLN (GTIN13 or GTIN14). NAME and COUNTRY are also mandatory. 
 We need an ISO 3166-1 alpha-2, 2 letter code (See: https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)
 
 Dates are always in  UTC format:  yyyymmddThhmmsszzzzzz
				  
          zzzzzz represents the timezone +01:00 or -05:00
				  
          March, 4th 2021 at 3:54pm in Amsterdam = 20210304T155400+01:00
 
### Receiver
```
 <receiver>
    <id>08710581000017</id>
    <name>Zwanenberg Food Group</name>
  </receiver>
```
The receiver information is also mandatory and is a static field. The ID is the GLN of Zwanenberg (08710581000017) and can be used 
for deliveries to all plants.

### Products

Each delivery has one or more Products. The ID (GTIN13 or GTIN14) and the name are mandatory.
```
<product>
      <id>04003730481688</id>
      <name>Rindfleischwürfel gegart</name>
```

### Batches

Each product has one or more batches. Please specify the size of the batch in <weightkg>.

Specify the ORIGINS when the information is available. For now this information is optional.
  
Specify the SLAUGHTERINGS. The EG code is mandatory. Make sure to start it with the 2 letter country code. 
See https://ec.europa.eu/food/food/biological-safety/food-hygiene/approved-eu-food-establishments_en

```  
<eg>AT50145</eg>
```

### Splittings & handovers
  
For now the information on SPLITTINGS and HANDOVERS are optional.


## XSD
  
The XML needs to be validated to the XSD. You can validate your test XML with the TransparantieTool XSD e.g. at https://www.freeformatter.com/xml-validator-xsd.html

The XSD contains also additional information for each tag.

  
 ## Example
  
See the example with the information that is required. 

