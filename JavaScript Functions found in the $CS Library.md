# JavaScript functions found in the $CS Library

Field and form rules | Javascript functions
By default, script should be written in JavaScript format only. Moreover, jQuery and $CS have been added in global scope, thus allowing the user to write code using jQuery (v 1.8.3) and $CS library. (Note: $ is not supported for accessing elements using jQuery).

JavaScript functions Available in $CS Library 

$CS.getValue(field) 

You can get the value of a field by using this function.

var statusId=$CS.getValue("STATUS"); 

var subject= $CS.getValue("SUBJECT");

var created_date=$CS.getValue("CREATEDDATE");  //This will return a JavaScript Date Object

var additional_hardware=$CS.getValue("RES_3_QUS_3"); //For checkbox type resource fields returns an array of selected resources

var email_id=$CS.getValue("REQUESTER.EMAILID"); 

var department=$CS.getValue("REQUESTER.DEPARTMENT"); 

var job_title=$CS.getValue("REQUESTER.JOBTITLE"); 

var mobile_number=$CS.getValue("REQUESTER.MOBILE"); 

var contact_number=$CS.getValue("REQUESTER.CONTACTNUMBER");

Note: To retain existing checked resources, store existing resources in an array and than add resources to that array. Now set resource field using this updated array.

————————————————————————————————————————————————————————————————————————————————————————

$CS.setValue(field,value) 

You can set the value of a field by using this function.

For input text type fields, this function sets the input text.

For select (Pick List) type fields, this function sets the value of the selected option.

$CS.setValue("STATUS","1"); 

$CS.setValue("SUBJECT","test request"); 

$CS.setValue("UDF_DATE1", new Date());

$CS.setValue("RES_3_QUS_3", ["CD RW", "External Harddisk" , "Optical Mouse"]); //Will remove existing selected resources and add this resources for checkbox type resource fields.

————————————————————————————————————————————————————————————————————————————————————————

$CS.getText(field) 

You can get the selected option text of a field by using this function.

This function should be used only for select (Pick List) type fields.

var status=$CS.getText("STATUS");

————————————————————————————————————————————————————————————————————————————————————————

$CS.setText(field,text) 

You can set selected option text of a field by using this function.
This function should only be used for select (Pick List) type fields.
$CS.setText("STATUS","Open");

————————————————————————————————————————————————————————————————————————————————————————

$CS.addOptions(field,options)

You can add options to a field by using this function.

Here, the options should be an  array  of options.

This function should be used only for select (Pick List) type fields. 

$CS.addOptions("STATUS",["Open","Closed"]);

————————————————————————————————————————————————————————————————————————————————————————

$CS.removeOptions(field,options)

You can remove the existing options of a field by using this function.

Here, the options should be an array of options.

This function should be used only for select (Pick List) type fields. 

$CS.removeOptions("STATUS",["Open","Closed"]);

————————————————————————————————————————————————————————————————————————————————————————

$CS.removeAllOptions(fields)

You can remove all the existing options of one or more select (Pick List) type fields by using this function.

Here, the fields should be an array of fields whose options need to be removed.

$CS.removeAllOptions(["STATUS"]);   // If all options of status field is removed, new request creation will not work. Since every request should have a status.

$CS.removeAllOptions(["STATUS","PRIORITY"]); 

————————————————————————————————————————————————————————————————————————————————————————

$CS.enableField(fields)

You can enable one or more fields by using this function.

Here, the fields should be an array of fields that you wish to enable.

$CS.enableField(["LEVEL","PRIORITY","URGENCY"]); 

————————————————————————————————————————————————————————————————————————————————————————

$CS.disableField(fields)

You can disable one or more fields by using this function. This allows the user only to view the fields, but not to edit them.

Here, the fields should be an array of fields that you wiish to disable.

$CS.disableField(["LEVEL","PRIORITY","URGENCY"]); 

————————————————————————————————————————————————————————————————————————————————————————

$CS.hideField(fields)

You can hide one or more fields by using this function. This restricts the user from viewing those fields.

Here, the fields should be an array of fields that you wish to hide.

$CS.hideField(["LEVEL","PRIORITY","URGENCY"]); 

——————————————————————————————————————————————————————————————————————————————————————

$CS.showField(fields)

You can show one or more hidden fields by using this function. This allows the user to view those fields.

Here, the fields should be an array of fields that you wish to show.

$CS.showField(["LEVEL","PRIORITY","URGENCY"]); 

————————————————————————————————————————————————————————————————————————————————————————

$CS.mandateField(fields)

You can mandate one or more fields by using this function. This restricts the user from submitting the form without filling values for those fields.

Here, the fields should be an array of fields that you wish to mandate.

$CS.mandateField(["LEVEL","PRIORITY","URGENCY"]); 

————————————————————————————————————————————————————————————————————————————————————————

$CS.nonMandateField(fields)

You can remove mandate from one or more fields by using this function. This allows the user to submit the form without filling values for those fields.       

$CS.nonMandateField(["LEVEL","PRIORITY","URGENCY"]); 

————————————————————————————————————————————————————————————————————————————————————————

$CS.stopFormSubmission()

You can use this function to stop form submission. 

This function will work only when applied to "On Form Submit" event.

var status=$CS.getText("STATUS");

if(status==="Closed")

{

$CS.stopFormSubmission();

}

————————————————————————————————————————————————————————————————————————————————————————

$CS.isRequester()

You can use this function to find if a logged-in user is a Requester or not.

This function returns the value True, if the logged-in user is a Requester, else returns the value False. 

————————————————————————————————————————————————————————————————————————————————————————

$CS.isTechnician()

You can use this function to find if a logged-in user is a Technician or not.

This function returns the value True, if the logged-in user is a Technician, else returns the value False.

————————————————————————————————————————————————————————————————————————————————————————

$CS.hasRole(role)

You can use this function to find if a logged-in user has the assigned role.

This function returns the value True, if the logged-in user possesses the assigned role, else returns the value False.

$CS.hasRole("SDAdmin");

————————————————————————————————————————————————————————————————————————————————————————

$CS.getLoggedInUserId()

You can use this function to get the User ID of a logged-in user. 

var userId=$CS.getLoggedInUserId();

————————————————————————————————————————————————————————————————————————————————————————

$CS.getLoggedInUserName()

You can use this function to get the User Name of a logged-in user.

var userName= $CS.getLoggedInUserName();

————————————————————————————————————————————————————————————————————————————————————————

$CS.setFieldDependency(dependencyObject)

You can use this function to set dependency among the fields based on dependency JSON Object. 

Here, the same function works for both two-field and three-field dependencies.

$CS.setFieldDependency(dependencyObject);

————————————————————————————————————————————————————————————————————————————————————————

$CS.setTasks(tasksArray)

You can set an array of given task ids by using this function.

$CS.setTasks(["templateTask1","templateTask2","templateTask3"]);

————————————————————————————————————————————————————————————————————————————————————————

$CS.unSetTasks(tasksArray)

You can set an array of given task ids by using this function.
$CS.unSetTasks(["templateTask1","templateTask2","templateTask3"]);

————————————————————————————————————————————————————————————————————————————————————————

$CS.setDescription(description)

You can set content of description field by using this function.

$CS.setDescription("Application crashes / hangs frequently in user environment causing instability for the system.");

————————————————————————————————————————————————————————————————————————————————————————

$CS.getDescription()

You can get content of description field by using this function.

var descriptionContent=$CS.getDescription();

————————————————————————————————————————————————————————————————————————————————————————

$CS.disableOptions(fieldId,options)

You can disable options of a field by using this function.

This function should be used only for select (Pick List) type fields. 

Here, the options should be an array of options.
$CS.disableOptions("STATUS",["Open","Closed"]);

————————————————————————————————————————————————————————————————————————————————————————

$CS.enableOptions(fieldId,options)

You can enable the disabled options of a field by using this function.

This function should be used only for select (Pick List) type fields. 

Here, the options should be an array of options.

$CS.enableOptions("STATUS",["Open","Closed"]);

————————————————————————————————————————————————————————————————————————————————————————

$CS.isVisible(field)

You can check whether a field or resource is currently visible by using this function.

var isPriorityFieldVisiable=$CS.isVisible("PRIORITY");

————————————————————————————————————————————————————————————————————————————————————————

$CS.isEnabled(field)

You can check whether a field or resource is currently enabled for editing by using this function.

$CS.isEnabled("PRIORITY");

————————————————————————————————————————————————————————————————————————————————————————

$CS.isMandated(field)

You can check whether a field or resource is currently mandated by using this function.
$CS.isMandated("PRIORITY");

————————————————————————————————————————————————————————————————————————————————————————

Note: 

Errors encountered during script execution will be visible at console in the following format:

Caught following exception in executing field & form rules script execution of rule:[ Rule name ] at line number: [ line number ] and column:[ column number ] --> Error Message

Example:

Caught following exception in executing field & form rules script execution of rule:[ check for open request ] at line number: [ 2 ] and column: [ 8 ] --> Uncaught SyntaxError: Unexpected token = .
