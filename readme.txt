/* 
**	Custom MultiSelect Picklist
*/

Functional purpose: Create a visual force page to allow for selection of greater than 150 entries and write the selections back to the originating lead once done.  


Overview of how it works:  Link to VF page is clicked in Lead record.  Lead ID is passed as an apex page variable to the multiselect VF page. The code checks if any coutries were previously selected and builds the All coutries and selected countries lists as the page is generated, using the Country object records as its source. User can then interact with the lists to remove or add countries as needed.  When done, and save is clicked, it converts the selected coutries to a string and writes it back to the lead id that was originally passed when the page was opened.    
   

Implementation requirements (as designed) - 
	Custom Object - Country__c to serve as a list of all countries.					    
	Custom long text field on Lead - Selected_Countries_List__c to store selected countries				    
	Custom formula (text) field on Lead - Country_Select__c with the following formula: 								hyperlink("/apex/MultiSelect?Id="&Id,"Click to add or update selected countries",'_self')



Components: MultiselectController.apxc, MultiselectControllerTest.apxc, MultiselectOptions.apxc, MultiSelectOptionsTest.apxc, MultiSelect.vfp, MultiSelectPicklist.vfc

Component Descriptions:

MultiselectController.apxc - Main controller function.  Populates the all countries and selected countries list.  Also builds the message to be written back to the originating lead.  

MultiselectControllerTest.apxc - Test class with 100% code coverage

MultiselectOptions.apxc - Controls the location of the selections based on the actions the user takes while working in the visualforce page.  

MultiSelectOptionsTest.apxc - Test class with 100% code coverage

MultiSelect.vfp - Visualforce page to populate the left and right selectable options, as well as handle the save action once the user is done selecting.  

MultiSelectPicklist.vfc - Visualforce component to build all page elements and handle all actions taken on the various page elements.


