# sf-metadata-pkg
Reference of Deployment tags for package.xml on supported Metadata types. While working with Salesforce Deployment tools like ANT and DX I continue to search for various metadata tags used by package.xml file. Unfortunate I did not fiund a single place where all is documented. 

This guide is designed to give comprehensive list of tags adn examples uses that can be applied to package.xml to get or deploy different metadata items. code and declarative items.

Below are examples of supported metadata types tyhat can be managed by Metadata API via ANT or DX tools

## Code Items Section

### Apex Class

```
	<types>
        <members>CaseSelector</members>
        <members>CaseSelectorTest</members>
        <members>OpptySelectorTest</members>
        <name>ApexClass</name>
    </types>
```

### Visual Force Page

```
	<types>
        <members>MyTestPage</members>
        <name>ApexPage</name>
    </types>
```

### Lightning Components

```
	<types>
        <members>my_theme_footer</members>
        <members>my_theme_header</members>
        <name>AuraDefinitionBundle</name>
    </types>
```

## Declarative Items Section

### SObject
Sobjects can be standard and custom or custom metadata type. Custom object has `__c` and metadata type `__mdt` postfix.
For standard object such as `Case` below tag will pull all customizations in single file.
For custom objects metadata will have complete object xml definition with all fields included.

```
	<types>
        <members>Case</members>
        <members>MyCustomObject__c</members>
        <members>MyMeta_Settings__mdt</members>
        <name>CustomObject</name>
    </types>
```

### Custom Field

```
	<types>
        <members>MyObject__c.Final_Test__c</members>
        <members>MyObject__c.Total__c</members>
        <members>Lead.SomeCustomField__c</members>
        <name>CustomField</name>
    </types>
```
### Custom Metadata Type
```
	<types>
        <members>MY_Settings.My_Community</members>
        <name>CustomMetadata</name>
    </types>
```    
### Static Resource
Static resources are typically zip files containing images or JavaScript & CSS code or frameworks, data fiels, any file type. Static resources have org wide limit size: 250MB as of Winter '19 release.

```
	<types>
        <members>SLDS203</members>
        <members>jquery_min_1_12_4</members>
        <members>w3css</members>
        <name>StaticResource</name>
    </types>
```

### Quick Action

```
	<types>
        <members>Opportunity.Open_My_Page</members>
        <name>QuickAction</name>
    </types>  
```    
### Weblink
```
    <types>
        <members>Opportunity.My_Button</members>
        <name>WebLink</name>
    </types>
```
### Page Layout
The example below describe layout for Cutom metadata
```
	<types>
        <members>MyMeta_Settings__mdt-My Settings Layout</members>
        <name>Layout</name>
    </types>  
```  
### Flow or Process Builder
Automation items such as Flows or Process Builders are represented by `Flow` tag.

```
    <types>
        <members>Create_My_Inquiry_s_SOP_and_Activities-2</members>
        <name>Flow</name>
    </types>
```
### Custom Labels
Export all custom Labels defined in the org. Current Metadata can sdefine individual labels, however export or dseploy only full set on labels.

```
    <types>
        <members>CustomLabels</members>
        <name>CustomLabels</name>
    </types>
```
### Validation Rule
```
    <types>
        <members>Case.My Validation Name</members>
        <name>ValidationRule</name>
    </types>
```
