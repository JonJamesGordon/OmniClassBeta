## OmniClassBeta
This GitHub project consolidates documentation and feedback for CSI's OmniClass Web API service.

This Readme will be updated according to the current status of the OmniClass API service.

### The OmniClass API service is currently in the beta testing phase.
- Only those organizations or individuals who have been accepted as beta testers will be able to use the service at this time.  [Contact CSI](mailto:csi@csinet.org) regarding becoming a beta tester.
- Errors, slow response times, and unfinished features are to be expected;  Please help us to improve the service by reporting problems in our [issues section](https://github.com/csi-net/OmniClassBeta/issues), using the "bug" label.
- New features and improvements to existing features are still being considered.  Please submit any suggestions to our [issues section](https://github.com/csi-net/OmniClassBeta/issues), using the "enhancement" label.
- Existing features are subject to change or removal.  Such modifications will be noted on this document in addition to email notifications.

### OC_Data.dll
OC_Data is a .NET package that provides an easy way to access the OmniClass API.

- Download OC_Data.dll from this repository and add it as a reference in your project.
- Included is the OCAccess class that exposes all implemented API requests and Response classes that contain returned data.
- The source code in Visual Basic has been provided as a reference.

### Direct API Access
It is possible to access the API without linking to OC_Data.dll.  Accessing the API via urls will result in the raw XML files being returned.

The API is currently accessible at:  
http://ocservice.csinet.org/OmniClass_Service.svc  
Clicking this link will take you to an "Endpoint not found." page and return no XML file.  This is not a bug.  Append an API Request to generate an XML response.

All requests require at least 1 argument.  Append a ? and provide your vendor key like this:  
http://ocservice.csinet.org/OmniClass_Service.svc/GetAllTableGuids?key=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

For requests requiring multiple arguments, separate the arguments with &  
http://ocservice.csinet.org/OmniClass_Service.svc/GetOCTable?key=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&table=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

### API Requests Currently Available

The following requests are implemented.  Visiting these urls in a browser will show the XML file returned by the request.

- GetAllTableGuids  
http://ocservice.csinet.org/OmniClass_Service.svc/GetAllTableGuids  
Arguments: *key*  
Returns a list of GUIDs that represent OmniClass Tables

- GetOCTable  
http://ocservice.csinet.org/OmniClass_Service.svc/GetOCTable  
Arguments: *key*, *table*, *version (optional)*  
Given a GUID for a table, returns that table's properties and a list of GUIDs representing it's root objects.  Setting version to a valid Version GUID will get the table's status as of that version, rather than the newest version which is the default.

- GetAllVersionGuids  
http://ocservice.csinet.org/OmniClass_Service.svc/GetAllVersionGuids  
Arguments: *key*, *table*, *unpublished (optional)*  
Given a GUID for a table, returns a list of GUIDs representing versions of that table.  This list will only include the most recent revision of each.  unpublished=true will also include table versions that are not yet published.

- GetOCVersion  
http://ocservice.csinet.org/OmniClass_Service.svc/GetOCVersion  
Arguments: *key*, *version*  
Given a GUID for a version (or revision), returns that version's properties

- GetAllRevisionGuids  
http://ocservice.csinet.org/OmniClass_Service.svc/GetAllRevisionGuids  
Arguments: *key*, *version*, *unpublished (optional)*  
Given a GUID for a version, returns a list of GUIDs representing revision-versions of that table, including the submitted version.  unpublished=true will also include revision-versions that are not yet published.

- GetOCObject  
http://ocservice.csinet.org/OmniClass_Service.svc/GetOCObject  
Arguments: *key*, *guid*, *version (optional)*  
Given a GUID for an object, returns that object's properties and a list of GUIDs representing its child objects.  Setting version to a valid Version GUID will get the object's status as of that version, rather than the newest version which is the default.

### Planned Features
These features are subject to change and will see varying implementation over time during the Beta.  Once all of the following have been implemented, The service will leave Beta status.

- Improved Accompanying OmniClass Website
- SSL for the API and improved authentication process
- "Helper" methods for searching OmniClass Objects (for example, retrieving Guids by Number/Title)
- Backdated versions of OmniClass tables (The current release includes only the most recent versions)
- Ability to create and manage custom OmniClass Table Versions through API and browser-based tool
- Language translations and methods for requesting multilingual data

### Feedback and Support
Please post all service feedback or requests for technical support to the [issues section](https://github.com/csi-net/OmniClassBeta/issues) and apply an appropriate label (*bug* for service breaking issues, *enhancement* for feature requests or improvement suggestions, or *help wanted* for questions and support).