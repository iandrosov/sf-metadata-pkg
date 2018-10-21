# sf-metadata-pkg
Reference of Deployment tags for package.xml on supported Metadata types. While working with Salesforce Deployment tools like [ANT Deployment tool](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_deploying_ant.htm) and [Salesforce DX](https://developer.salesforce.com/platform/dx) I continue to search for various metadata tags used by package.xml file. Unfortunate I did not find a single place where all of these tags are documented. 
[Metadata API Developer Guide](https://developer.salesforce.com/docs/atlas.en-us.api_meta.meta/api_meta/meta_objects_intro.htm) is a good resource but does not give all tags especially with naming of items differences.


This guide is a work in progress and will be updated with more supported items. It is designed to give easy reference list of tags and examples use cases that can be applied to package.xml to retrieve or deploy different metadata code and declarative items. For complete list of supported metadata items can be found at [Metadata Coverage report API v44.0](https://developer.salesforce.com/docs/metadata-coverage/44)

Below are examples of supported metadata types that can be managed by Metadata API via ANT or DX tools

## Code Items Section

### Access Control Policy
```
    <types>
        <members>*</members>
        <name>AccessControlPolicy</name>
    </types>
```

### Account Settings
```
    <types>
        <members>*</members>
        <name>AccountSettings</name>
    </types>
```
### Action Link Group Template
```
    <types>
        <members>*</members>
        <name>ActionLinkGroupTemplate</name>
    </types>
```
### Activities Settings
```
    <types>
        <members>*</members>
        <name>ActivitiesSettings</name>
    </types>
```
### Address Settings
```
    <types>
        <members>*</members>
        <name>AddressSettings</name>
    </types>
```
### Analytic Snapshot
```
    <types>
        <members>*</members>
        <name>AnalyticSnapshot</name>
    </types>
```
### Approval Process

```
    <types>
        <members>*</members>
        <name>ApprovalProcess</name>
    </types>
```

### Custom Application
```
    <types>
        <members>*</members>
        <name>CustomApplication</name>
    </types>
    
    // named app
    <types>
        <members>Corporate_Clients_App</members>
        <name>CustomApplication</name>
    </types>  
    
```
### Apex Class

```
    <types>
        <members>CaseSelector</members>
        <members>CaseSelectorTest</members>
        <name>ApexClass</name>
    </types>
```
### Apex Trigger

```
    <types>
        <members>CaseTrigger</members>
        <members>OpptyTrigger</members>
        <name>ApexTrigger</name>
    </types>
```

### Visual Force Page

```
    <types>
        <members>MyTestPage</members>
        <name>ApexPage</name>
    </types>
```
### Apex Component
```
    <types>
        <members>*</members>
        <name>ApexComponent</name>
    </types>
```    
### Apex Test Suite

Test suite is set up in Developer Console to collect relevant unit tests ot execute as groups

```
    <types>
        <members>*</members>
        <name>ApexTestSuite</name>
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
### Lightning App Page - Flexipage
```
    <types>
        <members>My_Record_Page</members>
        <name>FlexiPage</name>
    </types>
```

## Declarative Items Section

Note some differences in item definitions, some declarative items use API name with underscroes `_ ` or dashes `-` others uses spaces.

### AppMenu
```
    <types>
        <members>*</members>
        <name>AppMenu</name>
    </types>
```

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
### Custom Tab
```
    <types>
        <members>*</members>
        <name>CustomTab</name>
    </types>
```
### Custom Object translation
```
    <types>
          <members>*</members>
          <name>CustomObjectTranslation</name>
    </types>
```
### Custom Metadata Type
Custom Metadata containes object + all of the data. WHile deploying we can copy all the data or sepcific field as example bellow indicate

Copy single field data example:

```
    <types>
        <members>MY_Settings.My_Community</members>
        <name>CustomMetadata</name>
    </types>
```  
Copy all data and object definition for c=ustiom metadata type `LiveAgent_Custom__mdt` example:

```
    <types>
        <members>*</members>
        <name>CustomMetadata</name>
    </types>
    
    <types>
        <members>LiveAgent_Custom__mdt</members>
        <name>CustomObject</name>
    </types>    
```  
### Platform Event
```
    <types>
        <members>EventName__e</members>
        <name>CustomObject</name>
    </types>
```
### Document
```
    <types>
        <members>Images/Logo.png</members>
        <name>Document</name>
    </types>
``` 
### Sharing Criteria Rules
```
    <types>
        <members>Case.All_Access_User</members>
        <members>Case.DOC_Only_User</members>
        <members>Case.Market_Mgr</members>
	.
	.
	. 100s of rules
        <members>Case.VAT_Mgr</members>
        <name>SharingCriteriaRule</name>
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
### Compact Layout
```
    <types>
        <members>Lead.Corp_B2B</members>
        <members>Opportunity.Corp_B2B</members>
        <members>Account.Corp_B2B</members>
        <name>CompactLayout</name>
    </types>
```
### FlexiPages
This item can represent Lightning App definition (different from actual app build with APpBuilder or code)

```
    <types>
        <members>Opp_Corp_Record_Page</members>
        <members>Corp_Lead_Record_Page</members>
        <members>Corporate_Account_Record_Page</members>      
        <name>FlexiPage</name>
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
### Leterhead
```
 <types>
  <members>*</members>
  <name>Letterhead</name>
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
### Reports
```
<types>
        <members>ExtraReports</members><!--Report Folder-->
        <members>ExtraReports/AnyOccupation</members><!--Report-->
        <members>unfiled$public/Test</members><!--Report from Unfiled Public Reports-->
        <name>Report</name>
    </types>
    <types>
        <members>*</members>
        <name>ReportType</name>
    </types>
```
### Dashboard
```
    <types>
        <members>MyDashboards</members><!--Dashboard Folder-->
        <members>MyDashboards/AnyCourseType</members><!--Dashboard-->
        <name>Dashboard</name>
    </types>
```
### Permission Set
```
    <types>
        <members>My_Process_Update_Request</members>
        <name>PermissionSet</name>
    </types>
```
### Profile
```
    <types>
        <members>TestProfile</members>
        <name>Profile</name>
    </types>
```
### Role
```
    <types>
          <members>*</members>
          <name>Role</name>
    </types>
```
### Queue
```
    <types>
          <members>*</members>
          <name>Queue</name>
    </types>
    // named queue
    <types>
        <members>B2B_Lead_Q</members>
        <members>Corporate_Q</members>   
        <name>Queue</name>
    </types>    
```    
### Public Group
```
    <types>
          <members>*</members>
          <name>Group</name>
    </types>
    
    // Groups names
    <types>
        <members>HR_Mgr</members>
        <members>Sales_Mgr</members>
        <members>Market_West_Mgr</members>
        <members>Market_East_Mgr</members>
        <name>Group</name>
    </types>    
```
### Home Page
```
    <types>
        <members>*</members>
        <name>HomePageComponent</name>
    </types>
    <types>
        <members>*</members>
        <name>HomePageLayout</name>
    </types>
	<!-- Home Page Custom Link -->
    <types>
        <members>*</members>
        <name>CustomPageWebLink</name>
    </types>
```
## Workflow
### Worklow
```
    <types>
        <members>ObjectName.WorkFlowName</members>
        <name>Workflow</name>
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
### Workflow Alert
```
    <types>
        <members>ObjectName.FieldUpdateName</members>
        <name>WorkflowAlert</name>
    </types>
```
### WF Outbound Message
```
    <types>
        <members>ObjectName.FieldUpdateName</members>
        <name>WorkflowOutboundMessage</members>
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
### Workflow Task
```
    <types>
        <members>ObjectName.FieldUpdateName</members>
        <name>WorkflowTask</name>
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
### Audience
```
    <types>
        <members>*</members>
        <name>Audience</name>
    </types>

```
