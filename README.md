# Wikimedia-Counterpoint-Sidebar
A Wikimedia extension that allows comments or counterarguments assocaited with a specific passage of the main article to be creain a sidebar


.Variable to be set in LocalSettings.php					
					
Variable Name	    Option A	    Option B	        default		   Comments
Sbar_Default	    All_pages_on	All_pages_off	    on		
sbar_width	      number in pixels or percent		  25%		
sbar_height	      number of rows autodisplayed		4	  			(rebuttal sections to be displayed in truncated form, terminated by an ellipsis that can be clicked to reveal the full text of that rebuttal section. This prevents long rebuttals from interrupting the case text flow	)


sbar_max					Max characters in sidebar entry		no limit.   (Any length allowed	If the entry exceeds the limit, truncate display of text and add to end of displayed sidebar, "(Excess truncated)")

sbar_background		color of background							none			(Define a default color.  Wiki markup code may alter.)	
sbar_textcolor		color of sidebar text						none	    (Define a default color.  Wiki markup code may alter.)
sbar_reserve      yes or no                       yes 			(If there are no sidebar entries on a page that allows them, still reserve the space for the sidebar so that the layout does not dramatically change once a sidebar entry is created)		
					
					
Page Attributes only editable by Administrators					

Sbar_Enabled			Yes			No		(This allows Admin to force override of Sbar_Default)

<sbar></sbar>
					
Example of Usage in text					
Main text makes is composed of two sentences.<sbar>All the content, including markup, between the sbar tags will appear in the sidbar next to the first sentence in this example.</sbar>  Here is the second sentence of the main text.					
					
					
Other Specifications					
Here's where we can discuss additional changes.


.					
