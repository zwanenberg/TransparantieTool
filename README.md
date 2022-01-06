# TransparantieTool
Zwanenberg Food Group requires from all meat suppliers to publish their transparancy information of the supply chain.  The prefered way to provide this information to Zwanenberg is by publishing this information in GS1 fTrace (https://web.ftrace.com/en/). After publishing the supplier can release the information (when, what, where) of the chain (origin, slaughtering, splitting, sending) to the GLN of Zwanenberg (08710581000017).

![1](https://user-images.githubusercontent.com/59997944/148361792-f1f74fe0-e856-471f-8569-7d974d94bf72.JPG)

In the situation that GS1 fTrace cannot be used, Zwanenberg can receive the transparancy information via a direct connection.

![2](https://user-images.githubusercontent.com/59997944/148362252-585c84b5-909f-48e8-a41d-701c8590ef2b.JPG)

For every delivery to a Zwanenberg plant you need to upload one XML file with the requested information. See the example with the information that is required. 
You can upload the XML via sFTP. Information about the sFTP connection will be provided to you after both parties have agreed about using this method instead and tested the first XML.

The XML needs to be validated to the XSD. You can validate your test XML with the TransparantieTool XSD e.g. at https://www.freeformatter.com/xml-validator-xsd.html

See the document **Additional_Information.md** for extra explanation of the XML structure.
