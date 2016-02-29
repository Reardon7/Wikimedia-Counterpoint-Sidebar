# Wikimedia-Counterpoint-Sidebar
A Wikimedia extension that allows comments or counterarguments assocaited with a specific passage of the main article to be creain a sidebar


I've created a spread sheet with some detailed specs that you can comment on:  https://docs.google.com/spreadsheets/d/1lljcU5gftxmR9fqBlhS5Buceksh49LqP0JuNrBrWWb8/edit?usp=sharing



A rough example of the layout is seen at https://www.cairn.info/revue-internationale-de-philosophie-2005-4-page-491.htm#no7 which shows a portion of the endnotes to the left of the main article.  I think it would be better to have them to the right, but it could be an option that the wiki owner could choose.  

Another example, for WordPress, is http://futureofthebook.org/commentpress/ and also http://kevinw.de/greenbird/inline-comments-demo/


The database layout for WordPress has the advantage of treating comments as separate entities.  I'm not sure this is as easily done in MediaWiki....but I'm open to using another open source Wiki platform if it is easier to implement these features in a different platform.

I need this for a wiki dedicated to discuss/debate theological and philosophical issues where the main article would be addressed to defend a specific proposition and the sidebar would be used to critique the statements or claims being made in the main article.   

With perhaps dozens or hundreds of people editing on one or both sides, the rule of etiquette would be that "each side" would be entitled to put their best arguments forward in each section and that the critic's objections, comments would be confined to the sidebar rather than in wrestling over contested edits of the main article to develop a consensus that doesn't exist (as per what happens in contentious Wikipedia articles).

This goal of having collaborative editing is why I don't see it as a good fit for expanding on the WordPress examples above.

I believe this format would be very valuable for many types of wikis . . . not only those engaged in any point/counterpoint presentations, but also for collaborative development of business plans, industry standards, etc, where portions of what would now appear on the discussion page can be moved to the main page by way of sidebar edits.


Operational Details

I would envision a new wiki code, similar to <ref> which would instead be <sidebar> or perhaps <sb>
All the text and formatting, including wiki links to other articles and sidebar references (which would appear at the bottom of the sidebar), would appear between the sidebar start tag and the sidebar end tag. 

Given the potential complexity of the sidebar counter-arguments, rather than put all the text between the the brackets such as <sidebar Here's a three paragraph comment . . . . >,  I might suggest breaking use <sidebar start>  "Here's a three paragraph comment . . . ." <sidebar end>.   

When material between the sidebar tags are displayed, ignore any white space preceding or following the <sidebar start> and <sidebar end> tags so that in the source code, editors could add a couple carriage returns to more clearly display the sidebar code apart from the main article code.  

Preferably, all of this would be done using a WYSIWYG editor (now common for logged in wikipedia editors_ but some accommodation might be made as suggested for those who edit the source code.

Options:

1.  Option to turn on the comment sidebar feature for the wiki or specified pages.

2.  Option to highlight any amount of text  to which the comment is to be attached and displayed next to in the sidebar.

3.  Option to show only X number of lines of the comment, with an <expand> link which would reveal the entire comment, reformatting the page to push down the next paragraph of the main article, if necessary, so the entire comment can be shown.   The idea here is that normally the reader is reading the main article and should be able to focus on the main article without formatting requirements for a long comment to disrupt the layout of the main article.





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
