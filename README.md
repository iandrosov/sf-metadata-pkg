# sf-metadata-pkg
Reference of Deployment tags for package.xml on supported Metadata types. While working with Salesforce Deployment tools like [ANT Deployment tool](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_deploying_ant.htm) and [Salesforce DX](https://developer.salesforce.com/platform/dx) I continue to search for various metadata tags used by package.xml file. Unfortunate I did not find a single place where all is documented. 
[Metadata API Developer Guide](https://developer.salesforce.com/docs/atlas.en-us.api_meta.meta/api_meta/meta_objects_intro.htm) is a good resource but does not give all tags especially with naming of items differences.


This guide is a work ion progressa nd will b eupdated as more items are discovered. It is designed to give comprehensive list of tags and examples use cases that can be applied to package.xml to retrieve or deploy different metadata code and declarative items.

Below are examples of supported metadata types that can be managed by Metadata API via ANT or DX tools

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

Note some differences in item definitions, some declarative items use API name with underscroes `_ ` or dashes `-` others uses spaces.

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
Automation items such as Flows or Process Builders are represented by `Flow` tag. Note a version number on flow tag after name indicates what version of PB or FLOW is used `Create_Lead_Activities-2`

```
    <types>
        <members>Create_Lead_Activities-2</members>
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
### Email Template
```
	<types>
        <members>MyFolder/My_Test_Changed_Password</members>
        <members>MyFolder/My_Test_Forgot_Password</members>
        <members>NewFolder/My_Welcome_Email</members>
        <name>EmailTemplate</name>
    </types>   
```
### Workflow Field Update
```
	<types>
        <members>Account.Email_Invalid</members>
        <members>Lead.Invalid_Email</members>
        <name>WorkflowFieldUpdate</name>
    </types>
```
### Workflow Rule
```
    <types>
        <members>Account.Invalid Email Changed or Blank - Account</members>
        <members>Lead.Invalid Email Changed or Blank - Lead</members>
        <name>WorkflowRule</name>
    </types>
```
### Record Type
```
	<types>
        <members>Account.recordTypeName</members>
        <name>RecordType</name>
    </types>  
```
### Assignment Rule
Assignment rules can be for Case or Lead or other objects.

```
	<types>
        <members>Case.Case Assignment Rule</members>
        <name>AssignmentRule</name>
    </types>     
```
### Business Process
```
	<types>
        <members>Case.Course Update Request</members>
        <name>BusinessProcess</name>
    </types>
```
### List View
```
	<types>
        <members>Case.Course_Update_Cases</members>
        <name>ListView</name>
    </types>
```
### Permission Set
```
	<types>
        <members>My_Process_Update_Request</members>
        <name>PermissionSet</name>
    </types>
```

## Community
Deploying Community changes with metadata can be challenging, need ot deploy 3 different items described here bellow.

### Custom Site
```
    <types>
        <members>ECommerce</members>
        <name>CustomSite</name>
    </types>
```
### Network
```
    <types>
        <members>ECommerce_C</members>
        <name>SiteDotCom</name>
    </types>
```
### SiteDotCom
```
    <types>
        <members>ECommerce_C</members>
        <name>SiteDotCom</name>
    </types>
```