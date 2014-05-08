ML-PST-Extract
==============
##PST Extraction for MarkLogic
#####Forked from libpst

.pst - as defined in wiki "A Personal Storage Table (.pst) is an open proprietary file format used to store copies of messages, calendar events, and other items within Microsoft software such as Microsoft Exchange Client, Windows Messaging, and Microsoft Outlook. The open format is controlled by Microsoft who provide free specifications and free irrevocable technology licensing."

It presents a rather interesting (and scary) use-case where prospects might want to do some analytics on the .pst files made available to them by their IT team. As defined above, a .pst is not just for email archives but also calendar events and windows messaging. It can be a part of a huge dataset when clubbed with mailing list, social media feeds, comments and feedback received by the customer service department in an organization.

It used the mail.jar library along with libpst library to read the .pst. It then generates a xml document based on the header and body of the email message for ingestion into MarkLogic. It places attachments associated with a message in the attachment folder. You can use

    xdmp:document-filter() on xdmp:external-binary($path)
    $path : attachment-details/attachment-path

to extract the contents of the attachment and embed it into the message.xml created by this utility.

Steps to extract from .pst

    Place the jar file in the same folder as the .pst
    java - jar ML-PST-Extract.jar OR dbl click the jar file
