<div align="center">

## Simple GuestBook or Feedback Page Requiring No Database Implementation


</div>

### Description

On a simple website without a database, creating one with or without a database simply for the purpose of a guestbook/feedback page is a waste of resources. This single-file ASP guestbook does not require a database or server-side inlcudes. It self creates an XML compatible text file to store the entries.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Ken Alabi](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/ken-alabi.md)
**Level**          |Beginner
**User Rating**    |4.3 (30 globes from 7 users)
**Compatibility**  |ASP \(Active Server Pages\), HTML, VbScript \(browser/client side\)

**Category**       |[Complete Applications](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/complete-applications__4-7.md)
**World**          |[ASP / VbScript](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/asp-vbscript.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/ken-alabi-simple-guestbook-or-feedback-page-requiring-no-database-implementation__4-7780/archive/master.zip)





### Source Code

<p>As a web designer, I have been faced with the need for a simple and
   quick testimonial or guest book application on a basic website with no
   database backing. At every ocassion, I shirked at the prospect of
   requiring the website have a database (with or without an expensive DSN)
   simply for this purpose. I
   developed this simple text file powered database in ASP to serve the many
   times I will again be faced with this situation and it has made my work
   look good to many clients since.</p>
   <p>The guestbook application is in the form of a single ASP script file.
   The application receives input from site visitors and stores the input in
   a simple &quot;tag&quot; delimited text file. The text file implementation is such
   that it is XML compatible. The current implementation displays the log of
   feedbacks entered by site visitors but could also be implemented to not
   display the entries. The solution could be adapted to email the guestbook
   entries to a specified address.</p>
   <p><b>How It Works</b></p>
   <p>There are four parts to the ASP page<br>
   (1) Entry of information or feedback by site visitors<br>
   (2) Validation of the entered information<br>
   (3) Appending the information to a text file containing all entries<br>
   (4) Displaying all feedback that resides in the text file</p>
   <p><u>Entry of Information</u><br>
   This is achieved by a simple html form containing a textbox for the
   message and an input box. A salient feature of the form shown below is the
   hidden form object named &quot;submitted&quot; which will be used in
   determining the action taken by the page when accessed. Notice that the
   action property of the form returns to the same file as represented by the
   ASP string (Request.ServerVariables(&quot;SCRIPT_NAME&quot;))</p>
   <div align="center">
    <center>
    <table border="1" cellpadding="0" cellspacing="0" width="600">
     <tr>
      <td width="5%" valign="top">1<br>
       2<br>
       3<br>
       4<br>
       5<br>
       6<br>
       7<br>
       8<br>
       9<br>
       10<br>
       11<br>
       12<br>
       13<br>
       14<br>
       15<br>
       16<br>
       17<br>
       18</td>
      <td width="580" bgcolor="#FFFFCC" valign="top">  	 &lt;form name="feedform" method="POST"
       <b>action </b>= &quot;&lt;%=Request.ServerVariables("SCRIPT_NAME")%>"
       OnSubmit="return Validate()"><br>
	  &lt;input type="hidden" name=&quot;<b>submitted</b>&quot; value><br>
     &lt;table border="0" cellspacing="0" width="100%"><br>
       <br>
      &lt;tr>&lt;td width="30%">&lt;b>Enter your comments&lt;/b>&lt;/td><br>
	   &lt;td width="70%">&lt;textarea Name="feedbody" COLS="40" ROWS="4">&lt;/textarea>&lt;/td>&lt;/tr><br>
       <br>
      &lt;tr>&lt;td width="30%">&lt;b>Enter your Name&lt;/b>&lt;/td><br>
       &lt;td width="70%">&lt;input maxLength="50" Name="feedname" VALUE SIZE="45">&lt;/td><br>
	  &lt;/tr><br>
       <br>
      &lt;tr>&lt;td width="30%">&lt;/td><br>
       &lt;td width="70%">&lt;input type="submit" value=" Submit  ">&lt;/td>&lt;/tr><br>
       <br>
     &lt;/table><br>
     &lt;/form></td>
     </tr>
    </table>
    </center>
   </div>
   <p><u>Validation</u><br>
   There are two validation features in the javascript validation subroutine
   &quot;Validate()&quot;. First is to check that an input was entered before
   the form is submitted to the server. The advantage of this procedure is
   that validation is completed on the client computer and requests are not
   sent to the server (consuming central resources) until they are
   processable.
   </p>
   <p>The second function of the validation subroutine is to set the
   submitted form object to true (Line 3). When the page is accessed the
   second time by the server, the submitted flag determines that the page is
   to be processed for input. This allows the entire application to be
   completed with one single ASP file!
   </p>
   <div align="center">
    <center>
    <table border="1" cellpadding="0" cellspacing="0" width="600">
     <tr>
      <td width="5%" valign="top">1<br>
       2<br>
       3<br>
       4<br>
       5<br>
       6<br>
       7<br>
       8<br>
       9<br>
       10<br>
       11<br>
       12<br>
       13<br>
       14<br>
       15</td>
      <td width="580" bgcolor="#FFFFCC" valign="top">  	 &lt;script language="JavaScript"><br>
       function Validate() {<br>
		document.feedform.submitted.value=true;
       <p>    var string1 = document.feedform.feedbody.value;<br>
		 if (string1 == ""){alert("You have not entered a message"); return false;}<br>
		 if (string1.length >4000){alert("Your message is too long. This server accepts messages totalling only 4000&nbsp;
       characters"); return false;}</p>
       <p>var string1 = document.feedform.feedname.value;<br>
		 if (string1 == ""){alert("You have not entered your name or signature");return false;}</p>
       <p>return true;<br>
       }<br>
       &lt;/script></p>
      </td>
     </tr>
    </table>
    </center>
   </div>
   <p><u>Processing</u><br>
   The processing procedure performs additional activities to ensure that
   only one message is posted by the website visitor in one session as well
   as to strip the entry of any html elements.
   </p>
   <div align="center">
    <center>
    <table border="1" cellpadding="0" cellspacing="0" width="600">
     <tr>
      <td width="5%" valign="top">1<br>
       2<br>
       3<br>
       4<br>
       5<br>
       6<br>
       7<br>
       8<br>
       9<br>
       10<br>
       11<br>
       12<br>
       13<br>
       14<br>
       15<br>
       16<br>
       17<br>
       18<br>
       19<br>
       20<br>
       21<br>
       22<br>
       23<br>
       24<br>
       25<br>
       26<br>
       27<br>
       28<br>
       29<br>
       30<br>
       31<br>
       32<br>
       33<br>
       34<br>
       35<br>
       36</td>
      <td width="580" bgcolor="#FFFFCC" valign="top">  	 if (lcase(Request.Form("submitted")) = "true" )Then<br>
       &nbsp;&nbsp; if (IsNull(Session("feedbacked"))) then<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Session("feedbacked") = False<br>
       &nbsp;&nbsp; end if<br>
       &nbsp;&nbsp; if (Session("feedbacked")=True) then<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; errStr = "You are allowed only one message per session.&lt;/font>&lt;br>"<br>
       &nbsp;&nbsp; else<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Session("feedbacked")=True<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; smessage = Request.Form("feedbody")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; smessage = Trim(smessage)<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; smessage = Replace(smessage,"&lt;","")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; smessage = Replace(smessage,">","")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sname = Request.Form("feedname")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sname = Trim(sname)<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sname = Replace(sname,"&lt;","")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sname =
       Replace(sname,&quot;&gt;&quot;,&quot;&quot;)<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sdate = Now()<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; smessage = smessage &amp; "&lt;br>&lt;b>&lt;font color=blue>- " &amp; sname<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; smessage = smessage &amp; " (" &amp; sdate &amp;
       ")&lt;/font>&lt;/b>"<br>
       <br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sfile = "_feedback.txt"<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; whichFN=server.mappath(sfile)<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (whichfN &lt;> "") and (Not
       IsNull(whichFN)) then<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set fstemp = server.CreateObject("Scripting.FileSystemObject")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (fstemp.FileExists(whichFN) = True) then<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       Set filetemp = fstemp.OpenTextFile(whichfN, 8, false, 0)<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       filetemp.writeLine("&lt;FEEDBACK>")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       filetemp.WriteLine(smessage)<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       filetemp.writeLine("&lt;/FEEDBACK>")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       filetemp.Close<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       set filetemp=Nothing<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end if<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; set fstemp=Nothing<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end if<br>
       &nbsp;&nbsp; end if<br>
       end if</td>
     </tr>
     <tr>
      <td width="5%" valign="top">&nbsp;</td>
      <td width="580" bgcolor="#FFFFCC" valign="top">  	 &nbsp;</td>
     </tr>
    </table>
    </center>
   </div>
   <p>The entire processing section is wrapped within the if block (Line 1
   and Line 36) that checks if this form is being submitted for processing.
   </p>
   <p>Lines 2 - 8 ensures that a website visitor can only enter one feedback
   in one visit from the same browser. To enter another feedback, the visitor
   will have to close and reopen their browser.
   </p>
   <p>Lines 9 through 16 strips the entries of any html entries that could
   polute the feedback file.
   </p>
   <p>Line 22 ensures that this application will work irrespective of which
   folder on the website it is copied into. Infact, a feedback could be
   created in as many different web folders. Line 26 opens the feedback text
   file in append mode (8).
   </p>
   <p>Lines 27 - 29 appends the entry to the feedback text file. Each entry
   in the text file is delimited within the lines
   &lt;FEEDBACK&gt;&lt;/FEEDBACK&gt; making the file readable by an XML
   procedure. This is useful for cross-website integration.
   </p>
   <p><u>Display of Information</u><br>
   The contents of the storage text file is read and displayed on the
   feedback page.&nbsp;
   </p>
   <div align="center">
    <center>
    <table border="1" cellpadding="0" cellspacing="0" width="600">
     <tr>
      <td width="5%" valign="top">1<br>
       2<br>
       3<br>
       4<br>
       5<br>
       6<br>
       7<br>
       8<br>
       9<br>
       10<br>
       11<br>
       12<br>
       13<br>
       14<br>
       15<br>
       16<br>
       17<br>
       18<br>
       19<br>
       20<br>
       21<br>
       22</td>
      <td width="580" bgcolor="#FFFFCC" valign="top">  	 sfeedback = "&lt;font name=Verdana size=2>"<br>
	sfile = "_feedback.txt"<br>
	whichFN=server.mappath(sfile)<br>
	if (whichfN &lt;> "") and (Not ISNull(whichFN)) then<br>
       &nbsp;&nbsp;&nbsp; Set fstemp1 = server.CreateObject("Scripting.FileSystemObject")<br>
       &nbsp;&nbsp;&nbsp; if (fstemp1.FileExists(whichFN) = True) then<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set filetemp = fstemp1.OpenTextFile(whichfN, 1, false, 0)<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Do while (filetemp.AtEndofStream &lt;> True)<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       strLine = filetemp.ReadLine<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       strLine = Replace(strLine,"&lt;FEEDBACK>","")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       strLine = Replace(strLine,"&lt;/FEEDBACK>","&lt;hr>")<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
       sfeedback = sfeedback &amp; strLine<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Loop<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; filetemp.Close<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set filetemp = Nothing<br>
       &nbsp;&nbsp;&nbsp; else<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set filetemp = fstemp1.CreateTextFile(whichfN, false)<br>
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; filetemp.close<br>
       &nbsp;&nbsp;&nbsp; end if<br>
       &nbsp;&nbsp;&nbsp; Set fstemp1 = Nothing<br>
	end if<br>
	sfeedback = sfeedback &amp; "&lt;/font>"</td>
     </tr>
    </table>
    </center>
   </div>
   <p>At first access, when there is no feedback and no text file, the text
   file is created (Line 17), otherwise, the file is opened in read mode
   (Line 7). This means only one file (the ASP) file needs to be copied and
   installed in the required directory.
   </p>
   <p>The data delimited &lt;FEEDBACK&gt;&lt;/FEEDBACK&gt; is removed and
   replaced by a line break (Line 10 and 11). Data separation can be
   implemented using a different character or an image at this line instead
   of the line break tag &lt;hr&gt;.
   </p>
   <p>The string &quot;sfeedback&quot; contains the total feedback that have
   been accumulated at the site can can be inserted anywhere on the html
   section of the page within the ASP script limiter &lt;% %&gt;. If a
   display of the feedback on the site is not desired this activity may be
   ignored. In addition, Lines 1, 22, and 7-15 may be safile deleted.
   </p>
   <p>To ensure that the page is always refreshed an ASP command &lt;%<br>
   Response.Expires =0<br>
   %> is inserted at the top of the page.
   </p>
   <p>A comment must be made about the appropriateness of this application on
   a high volume site. It is a concern that there may be concurrency issues
   in the very rare situation that users try to commit their feedback at the
   same time. The chances of this situation ocurring increases with the rate
   of feedback entries. However, it goes without say that this solution would
   already prove undesirable given the size, volume, and time it would take
   for this file to load and view in that situation.
   </p>
   <p><a href="http://www.netvios.com/Downloads/Demos/feedback.asp" target=_blank>See this application in
   action</a>.
   </p>
   <p><a href="http://www.netvios.com/Downloads/plainfeedback.zip">Download the application
   (zipped ASP page)</a>.
   </p>
   <p><a href="http://www.netvios.com/Downloads/feedback.zip">Download a NetVIOS version of the
   application</a>.
   </p>

