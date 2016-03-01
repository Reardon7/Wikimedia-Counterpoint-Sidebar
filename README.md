# Wikimedia-Counterpoint-Sidebar
A Wikimedia extension that allows comments or counterarguments assocaited with a specific passage of the main article to be created and displayed in a sidebar.   

This extension must be created to work with the WikiMedia Visual Editor . . . https://www.mediawiki.org/wiki/Extension:VisualEditor . . . which means that the VisualEditor extension will also require modification to properly display and allow editing of the sidebar comments.  This modification should be done as part of the Wikimedia project so the features will be available to all wikimedia users.


I've created a spread sheet with some detailed specs that you can comment on:  https://docs.google.com/spreadsheets/d/1lljcU5gftxmR9fqBlhS5Buceksh49LqP0JuNrBrWWb8/edit?usp=sharing


# EXAMPLES OF HOW IT WILL ROUGHLY LOOK
A rough example of the layout is seen at https://www.cairn.info/revue-internationale-de-philosophie-2005-4-page-491.htm#no7 which shows a portion of the endnotes to the left of the main article.  I think it would be better to have them to the right, but it could be an option that the wiki owner could choose.  

Another example, for WordPress, is http://futureofthebook.org/commentpress/ and also http://kevinw.de/greenbird/inline-comments-demo/

# DESCRIPTION OF USE
I need this for a wiki dedicated to discuss/debate theological and philosophical issues where the main article would be addressed to defend a specific proposition and the sidebar would be used to critique the statements or claims being made in the main article.   

With perhaps dozens or hundreds of people editing on one or both sides, the rule of etiquette would be that "each side" would be entitled to put their best arguments forward in each section and that the critic's objections, comments would be confined to the sidebar rather than in wrestling over contested edits of the main article to develop a consensus that doesn't exist (as per what happens in contentious Wikipedia articles).

I believe this format would be very valuable for many types of wikis . . . not only those engaged in any point/counterpoint presentations, but also for collaborative development of business plans, industry standards, etc, where portions of what would now appear on the discussion page can be moved to the main page by way of sidebar edits.


# Operational Details

I would envision a new wiki code, similar to |ref| which would instead be |sidebar|> or perhaps |sb|. (I am using the | character since the angle-bracket will not display in this readme.md file) 

All the text and formatting, including wiki links to other articles and sidebar references (which would appear at the bottom of the sidebar), would appear between the sidebar start tag and the sidebar end tag. 

Given the potential complexity of the sidebar counter-arguments, rather than put all the text between the the brackets such as |sidebar Here's a three paragraph comment . . . . |  I would prefer to see us breaking use |sidebar start|  "Here's a three paragraph comment in wikicode that can display links and incluide other formatting such as bold, italics, indent, et cetera . . . ." |sidebar end|.   

When material between the sidebar tags are displayed, we should ignore any white space preceding or following the <sidebar start> and <sidebar end> tags so that in the source code, editors could add a couple carriage returns to more clearly display the sidebar code apart from the main article code.  

Preferably, all of this would be done using a WYSIWYG editor (now common for logged in wikipedia editors_ but some accommodation might be made as suggested for those who edit the source code.

Options:

1.  Option to turn on the comment sidebar feature for the wiki or specified pages.

2.  Option to highlight any amount of text  to which the comment is to be attached and displayed next to in the sidebar.

3.  Option to show only X number of lines of the comment, with an <expand> link which would reveal the entire comment, reformatting the page to push down the next paragraph of the main article, if necessary, so the entire comment can be shown.   The idea here is that normally the reader is reading the main article and should be able to focus on the main article without formatting requirements for a long comment to disrupt the layout of the main article.



Example of Usage in text					
Main text makes is composed of two sentences. |sbar| All the content, including markup, between the sbar tags will appear in the sidbar next to the first sentence in this example.|/sbar|  Here is the second sentence of the main text.					
DETAILS
I've created a spread sheet with some detailed specs that you can comment on:  https://docs.google.com/spreadsheets/d/1lljcU5gftxmR9fqBlhS5Buceksh49LqP0JuNrBrWWb8/edit?usp=sharing
					
Other Specifications					
Here's where we can discuss additional changes.


# DATA BASE OPTIONS

See the following links:

https://www.mediawiki.org/wiki/Manual:Database_layout 

https://www.mediawiki.org/wiki/Manual:Page_table

The page table can be considered the "core of the wiki". Each page in a MediaWiki installation has an entry here which identifies it by title and contains some essential metadata. It was first introduced in r6710, in MediaWiki 1.5.
The text of the page itself is stored in the text table. To retrieve the text of an article, MediaWiki first searches for page_title in the page table. Then, page_latest is used to search the revision table for rev_id, and rev_text_id is obtained in the process. The value obtained for rev_text_id is used to search for old_id in the text table to retrieve the text. When a page is deleted, the revisions are moved to the archive table.

https://www.mediawiki.org/wiki/Manual:Text_table
The text table holds the wikitext of individual page revisions. If using Postgres or Oracle, this table is named pagecontent.

# MY SUGGESTION REGARDING THE DATA BASE SCHEMA

I think it may be best if we try to follow the general schema outlined above for page table and text table, applying the same elements to a Sidebar table.

1.  We create a new table, SideBar Table, with all the elements of page table.
2.  The wikitext for each SideBar entry is actually stored in the text table, just as is done with page table.
3.  When a comment is created and associated with a specific paragraph in the wikitext of the individual page, a hook like |sidebar:xxxxxxxx| is inserted in the text, where xxxxxx points to the sidebar revision ID tag used to retrieve the sidebar text for rendering on the displayed page.   (The xxxxxx may be replaced with a user provided text which is actually linked to the equivalent of the sidebar-rev_text_id).

By keeping as close as possible to the structure used for pages in Wikimedia, we can hopefully minimize future coding efforts required to keep sidebar text entry and rendering up to par with page entry and rendering.




