<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<p>Expression Search / GMailUI is an extension to Thunderbird (versions 31.0+) which adds powerful message searching features.
Init by Ken Mixter, developed over many years by Opera Wang, updated to TB 78+ by Klaus Buecher/opto.</p>
<p>
Type "hello world" to search within the current view for this string in subject/from/to/cc.<br/>
Type "from:fred to:tom attachment:yes" or "f:fred t:tom att:yes" to see all messages from Fred to Tom in the current view that have an attachment.<br/>
Type "s:bbb t:(oo -pp)" to see all messages with subject bbb, send to oo but not to pp.
Press Ctrl+Enter to have this search apply to all folders through virtual folder.<br/>
Press Shift+Enter to invoke Gloda Search in all indexed folders.<br/>
Use Ctrl/Shift+Right Click to search the clicked subject/From/Recipient.<br/>
</p>

<p>Expression Search's features are described below.</p>
<p>The compatibility to TB 115 Supernova is underway. Some features may not work yet. You can report issues at the plugin homepage: <a href='https://github.com/opto/expression-search-NG/issues'>expression-search-NG</a>
<p> It is gratefully appreciated if you can support the transfer to TB 115 with a <a target = "_blank" href = 'https://www.paypal.com/donate?hosted_button_id=EMVA9S5N54UEW'>donation.</a> </p>
</p>
<h3>Search expressions and quick search key</h3>
<p>
This extension adds a new search text box to the end of your quick search bar. Whatever phrase you enter
is searched for in your currently selected folder's to/from/cc/subject fields.  Notice that by default
the body is not searched for your search phrase.  If that results in too many matches,you can focus the search
using "operators".  Operators are just short words followed by a colon, such as "from:amazon.com".
</p>

Here are some examples:
<ol><li>
<p><b>weekend plans</b></p>
<p>This expression searches all messages in the current folder or view for 
'weekend plans' in the <i>from</i>, <i>to</i>, <i>cc</i>, or <i>subject</i>
fields.</p>
<p>If "Act as normal filter" enabled, the "Sender", "Recipients", "Subject" and "Body" buttons will
determine to search in which fields.
</p></li><li><p>

<b>from:mike</b> or <b>f:mike</b>
</p>
<p>This expression searches all messages in the current folder or view for 'mike' in the <i>from</i>
field.
</p></li><li><p>

<b>to:bill</b> or <b>t:bill</b>
</p>
<p>This expression searches all messages in the current folder or view for 'bill' in the
<i>to</i> or <i>cc</i> fields of the message.
</p></li><li><p>

<b>tonocc:bill</b> or <b>cc:tom</b> or <b>bcc:riddle</b>
</p>
<p>Like above, <b>tonocc</b> will search <i>to</i> field only, <b>cc/bcc</b> will search <i>cc/bcc</i> field only. Case insensitive.
</p></li><li><p>

<b>only:tom</b> or <b>o:tom</b>
</p>
<p>Search for 'tom', and 'tom' should be the only recipients in <i>to</i> filed. Case insensitive.<br/>
Note: 'only:(tom or jerry)' will get message that <i>to</i> filed is 'tom' or 'jerry' only, while 'only:(tom and jerry)' will get nothing, please use 'only:(tom,jerry)' instead if you want to search emails that recipients contain and only contain both 'tom' and 'jerry'.
</p></li><li><p>

<b>fromto:tom</b> or <b>ft:tom</b>
</p>
<p>Search for 'tom', and 'tom' can be in either <i>from</i>, <i>to</i>, <i>cc</i>, or <i>bcc</i>. Case insensitive.
</p></li><li><p>

<b>subject:electric bill</b> or <b>s:electric bill</b>
</p>
<p>This expression searches all messages in the current folder or view for 'electric bill' 
in the <i>subject</i> fields of the message. Case insensitive.
</p></li><li><p>

<b>simple:this subject contains special characters like ( ) ' " - etc</b>
</p>
<p>This expression searches all messages in the current folder or view in the <i>subject</i>
fields of the message. And the pattern can contain special characters. unlike "subject" search, this search won't suffer from <a href='https://bugzilla.mozilla.org/show_bug.cgi?id=124641'>Bug 124641</a>.
</p><p>This pattern must be the last pattern. Case <b>sensitive</b>.
</p></li><li><p>

<b>regex:/^begin/i</b> or <b>re:end$</b> or <b>r:/\d+\s*\d+/</b>
</p>
<p>This expression searches all messages in the current folder or view with <a href='https://developer.mozilla.org/en/JavaScript/Guide/Regular_Expressions'>Regular Expressions</a>
in the <i>subject</i> fields of the message.
</p><p>This pattern must be the last pattern. Case <b>sensitive</b> unless you have //i.
</p></li><li><p>

<b>headerre:List-Id=/all-test/i</b> or <b>h:list-id</b> or <b>h:sender=/^Bob/</b> or <b>hr:header~/^value/</b>
</p>
<p>This expression searches all messages in the current folder or view with <a href='https://developer.mozilla.org/en/JavaScript/Guide/Regular_Expressions'>Regular Expressions</a>
in the header of the message. The header should be already saved in Thunderbird's .msf database.
You can <a href="https://developer.mozilla.org/en-US/docs/Extensions/Thunderbird/customDBHeaders_Preference">config</a> the headers in 'options/Search More Headers', If you added one header, it will only affect
newly added emails unless you do 'repaire folder'.
</p><p>This pattern must be the last pattern. Header is case insensitive, Value is case <b>sensitive</b> unless you have //i.
If the value is empty, Any message has the header will match.
</p></li><li><p>

<b>fromre:/^begin/i</b> or <b>fr:end$</b>
</p>
<p>This expression searches all messages in the current folder or view with <a href='https://developer.mozilla.org/en/JavaScript/Guide/Regular_Expressions'>Regular Expressions</a>
in the <i>from</i> fields of the message.
</p><p>This pattern must be the last pattern. Case <b>sensitive</b> unless you have //i.
</p></li><li><p>

<b>tore:/^begin/i</b> or <b>tr:end$</b>
</p>
<p>This expression searches all messages in the current folder or view with <a href='https://developer.mozilla.org/en/JavaScript/Guide/Regular_Expressions'>Regular Expressions</a>
in the <i>recipients</i>(to/cc/bcc) fields of the message.
</p><p>This pattern must be the last pattern. Case <b>sensitive</b> unless you have //i.
</p></li><li><p>

<b>attachment:yes</b> or <b>a:yes</b>
</p>
<p>This expression searches all messages in the current folder or view for an attachment,
Notice that it does not search for attachments named "yes".  You can also use "y" or "1" for 
"yes".  You can use "no", "n", or "0" to search for messages without attachments.
</p></li><li><p>

<b>filename:foo.doc</b> or <b>fi:image</b> or <b>fn:msword</b> or <b>file:html</b>
</p>
<p>This expression searches all messages in the current folder or view for an attachment name or type. Case insensitive.
If you just want to search messages that have attachment, use attachment:yes instead of using this one.
</p></li><li><p>

<b>is:replied</b> or <b>i:UnRead</b> or <b>status:Forwarded</b> or <b>status:F</b>
</p>
<p>This expression searches all messages in the current folder or view for status, The
status can be one of Replied, Read, Marked/Star, Forwarded, UnRead, New, ImapDeleted or Attachment.
</p></li><li><p>

<b>before:2011/03/09 07:12:00</b> or <b>be:09 Mar 2011 05:00:00</b> or <b>after:Mar 10, 2011</b> or <b>af:(2011/03/01 -2011/03/09)</b>
</p>
<p>This expression searches all messages in the current folder or view within the <i>date</i> range, The
date format can be checked <a href='https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Date/parse'>Here</a>.
</p></li><li><p>

<b>before:07:12:00</b> or <b>be:5:9</b> or <b>after:03:07:05</b> or <b>af:(3:0 -4:0)</b>
</p>
<p>This expression searches all messages in the current folder or view within the time range.
af:(3:0 -4:0) will search for messages in current view that <i>date</i> between 3am to 4am EVERY day. 
</p></li><li><p>

<b>date:2011/01</b> or <b>date:2011/01/03</b> or <b>d:" 03:"</b> or in zh-CN locale <b>d:2011?3?</b>
</p>
<p>This expression searches all messages in the current folder or view to match date.
The internal format for compare is "yyyy/mm/dd hh:mm:ss", locale date is also supported.
</p></li><li><p>

<b>ag:3</b> or <b>da:3</b> or <b>age:3</b> or <b>older_than:3</b> or <b>days:(3 -5)</b> or <b>age:today</b> or <b>newer_than:8week</b>
</p>
<p>This expression searches all messages in the current folder or view to match age in days.
days:(3 -5) will search for messages that age between 3 to 5 days.
</p></li><li><p>

<b>size:10</b> or <b>si:(0.5M -2M)</b> or <b>larger:1G</b> or <b>smaller:1024</b> or <b>sm:10</b>
</p>
<p>This expression searches all messages in the current folder or view to match size in KB or MB/GB.
size:(3 -5) will search for messages that size is larger than 3KB and less than 5KB, that is 4.x KB.
</p></li><li><p>

<b>body:electric bill</b>
</p>
<p>This expression searches all messages in the current folder or view for 'electric bill' 
in the body of the message. On large or remote folders it may take some time. Also, if you 
combine this with other search operators like "from:", "subject:" or "to:" this will speed 
things up considerably. 
</p></li><li><p>

<b>bodyre:/hello.*world/i</b> or <b>br:test</b>
</p>
<p>This expression searches the body of all messages in the current folder or view with <a href='https://developer.mozilla.org/en/JavaScript/Guide/Regular_Expressions'>Regular Expressions</a>. Case sensitive and should be the last pattern.
Only search <b>offline</b> messages.
</p></li><li><p>

<b>label:Important</b> or <b>tag:TODO</b> or <b>l:NA</b>
</p>
<p>This expression searches all messages in the current folder or view which has the tag
Important. l:NA means all messages without tag.
</p></li><li><p>

<b>all: weekend plans</b>
</p>
<p>This expression searches all messages in the current folder or view for
'weekend plans' anywhere in the message, including the <i>from</i>, <i>to</i>, <i>cc</i>, or <i>subject</i>
fields, and the <i>body</i>.
</p></li><li><p>

<b>g: weather</b>
</p>
<p>This will call gloda (faceted) search if gloda enabled. This mode can't be used together will other specifications like 'f:' or 't:'.
</p></li><li><p>

<b>3+2</b>
</p>
<p>If the expression looks like an arithmetic one, when you press enter, it will be calculated and the result will be shown in the search box.
</p></li>

<li><p>
<b>from:-foo from:-bar [...]</b>
</p>
<p>So-called <a href='https://github.com/wangvisual/expression-search/issues/47'>Inverted Search</a>.
This is a <kbd>not x and not y [...]</kbd> search for the selected attribute (Here: <var>from:</var>).<br/>
This is the GMail search-equivalent of: <kbd>-foo -bar</kbd>.
</p></li>

</ol>

<h3>Hot Key</h3>
<p>
By default, Press Ctrl+Shift+K, your cursor will appear in the expression search bar and
you will be able to type.</p>
<p>Expression Search add one additional hot key "Ctrl+B".</p>
<p>Once you are typing in your search query, and you hit enter or otherwise let
it begin searching, your cursor will remain inside of the query box to allow you 
to modify the query.  However, if you'd rather go back to browsing your messages,
instead of clicking on the message headers in your search results, you can just
press 'ESC' to to clear the search criteria, and press 'ESC' again to refocus back</p>

<h3>Quick Search Virtual Folder</h3>
<p>If you haven't before used 'virtual folders' in Thunderbird, let me introduce them.
This standard feature of Thunderbird lets you create a search, name it, and then
have that name appear in your folders list.  You can select that folder from the
list and see the current result of the saved search.  Note two useful things: 1)
the 'contents' of the virtual folder can actually be in any of your real folders,
and so a virtual folder actually can 'contain' messages that span many folders,
and 2) the virtual folder's contents are recomputed each time you view it, so if
you saved a virtual folder with 'sender' field containing 'Donald', then if you
receive a new message from someone named Donald, it will be placed in your INBOX,
but you'll immediately be able to switch to your Donald virtual folder, and find
it there.</p>
<p>So that's what regular virtual search folders do in Thunderbird. But this
extension makes it extremely easy to create them.  Now, when you normally hit
'enter' in the Expression search quick search bar, you can instead hit
'ctrl-enter' and a virtual folder called 'ExressionSearch' will be created (or modified
if it already existed) to search for that search across ALL of your folders in the
current account.</p>
<p>The resulting virtual folder 'ExpressionSearch' can then be modified
by editing properties, or can be renamed to make it a permanent virtual search folder.
If you do not rename the folder, the next time you use ctrl-enter the ExpressionSearch 
virtual folder is reused to show your new quick search result.</p>

<a name='keep_saved_search'></a>
<p>The option "<b>Keep selected folders for saved search</b>" to have the "ExpressionSearch"
virtual folder being persistent not only allows you to mark it as "Preferred" without
the setting being lost when restarting TB, but also you can edit the properties of the
"ExpressionSearch" virtual folder to specify once for all which of your physical folders
should be searched or not with a global non-faceted search (CTRL+Enter).</p>
<p>Where "ExpressionSearch" is created can also be set in the option dialog, By default, it's
the root folder of the current disaplyed folder</p>
<p>You can back to original folder by press Ctrl+Alt+LEFT</p>

<h3>More complex searching</h3>
<p>The quick search bar allows you use the simple expressions from above, but it also
allows you to compose more complex searches.  For instance, if you want to search for
a message from Bob Barker to Dave Letterman about monologues, you can use:

</p>
<p><b>f:Bob Barker t:Dave Letterman s:monologues</b>
</p>
<p>If you are tired of getting results that have jokes about "Monica", you can instead use:

</p>
<p><b>f:Bob Barker t:Dave Letterman s:monologues -Monica</b>
</p>
<p>If you are interested in messages from either of these celebrities:

</p>
<p><b>f:Bob Barker or f:Dave Letterman</b>
</p>
<h3>Notes</h3>
<p>Note 1: For the average user, the above information is usually adequate.  If you
are curious, this feature still relies upon an underlying Thunderbird message searching
mechanism.  That mechanism cannot always perform searches correctly that have a combination of boolean
operators.  So, if you try to perform a search that mixes "ands" and "ors" you may get back
too many results.  As an example, if you were to search for "t:dan and f:(bob or dave)" you
will be mixing boolean operators and the results may be over inclusive or may work.  As an extra technical
note, if you did "t:dan and -f:(bob or dave)", DeMorgan's theorem takes place and you are actually
composing a search of "t:dan and f:-bob and f:-dave".
</p>
<p>
However, due to restrictions in Thunderbird's virtual search folder, the complex searching results maybe correct
in your current search results, but maybe NOT in you search folder. as the search folder can only handle 'Match all'
and 'Match any' types.
</p>
<p>
Note 2: If you want search all folders using expression, you can create a virtual folder manually (Ctrl+Shift+F) with 'Match all messages',
then using expression search in the virtual folder.
</p>
<p>
Note 3: In case you also using the normal search filter, the final results is logically "AND", that means
both filter are effective.
</p>

<h3>Click 2 Search</h3>
<p>
If Enabled, you can use Ctrl/Shift+Right Click on sender/recipient/subject column to search for the same sender,
recipient or subject.
</p>
<p>
<a name="c2s_Replace"></a>
For subject line, if provided regular expression match/replace patterns and enabled the replace for corresponding key combo, the pattern will be first executed
<pre>Replace subject before search.
Multiple matches are ORed. Example:
    Match:   \[#(\d*)\]
    Replace: $1
    Subject: [#1212][#2323]Some text
    Result:  (1212 or 2323)</pre>
</p>
<p>
Also common prefix like 'Re:', 'Fw:', [mail-list-name] will be removed before search.
</p>

<a name="version_history"></a>
<h3>Version history</h3>
<ul><li>
  Version 2.4beta: <ul>
    <li>Works with TB78, drop support for old TB pre 78</li>
    <li></li>
    </ul>
    </li><li>Version 1.4: <ul>
<li>Works with TB 63 nightly, drop support for TB older than 60</li>
<li>Change from legacy XUL overly addon to restartless addon</li>
</ul>
</li><li>
Version 1.3: <ul>
<li>Works with TB 60 nightly, drop support for TB older than 52</li>
<li>Fixed issue with 'only' filter</li>
</ul>
</li><li>
Version 1.2: <ul>
<li>Add 'fromto' token</li>
<li>Add option for search input box timeout</li>
<li>Fixed issue with OSX</li>
<li>Fixed issue with TB 55</li>
</ul>
</li><li>
Version 1.1: <ul>
<li>Works with TB 56 nightly</li>
</ul>
</li><li>
Version 1.0: <ul>
<li>Works with TB 45 nightly</li>
</ul>
</li><li>
Version 0.9: <ul>
<li>Compatible with TB40 nightly and drop support for TB version less than 31</li>
<li>Attachment search is fully supported and won't crash TB any more, for offline messages only.</li>
<li>Add option to put the Expression Search field into the Tab bar</li>
<li>Add option to (not) remove the domain name for click2search</li>
<li>Add option to hide the quick search filter icons</li>
<li>Looks better on OSX and Ubuntu</li>
</ul>
</li><li>
Version 0.8.8: <ul>
<li>Compatible with TB31 nightly and drop support for TB 5~11</li>
<li>regex search in body is fully supported and won't crash TB any more, for offline messages only.</li>
</ul>
</li><li>
Version 0.8.7: <ul>
<li>Compatible with TB29 nightly</li>
<li>Added regex search for from/to</li>
<li>Added option to make the "search results" doesn't looks so big when search is not active</li>
<li>Changed hotkey from Ctrl+Left to Ctrl+Alt+Left for back to original folder after Ctrl+Enter</li>
</ul>
</li><li>
Version 0.8.6: <ul>
<li>getCellProperties API change for TB22</li>
<li>Add options for tooltip show/hide time</li>
<li>change the flexibility of other element to make my search box bigger</li>
<li>Add "Re: " to subject if it's a reply email for subject regex search</li>
<li>Add 'Select All', 'Clear All' & select mode when modify virtual folder's folders.</li>
<li>Fix bug: Donate through palpay directly not working because I'm in China</li>
</ul>
</li><li>
Version 0.8.5: <ul>
<li>Added options for show or hide text labels of 'quick filter' buttons</li>
<li>Added options to seperate subject replacment for Ctrl/Shift+RightClick</li>
<li>Added options for load Saved Search folder in a new Tab</li>
<li>Added hotkey Ctrl+Left for back to original folder after Ctrl+Enter</li>
<li>Added regex search for headers</li>
<li>Added regex search for body</li>
<li>Added newer_than/older_than support</li>
<li>Added size/larger/smaller support</li>
<li>Support NA for tag search, Star for status search</li>
<li>Added today/yesterday/day/month/year for days search</li>
<li>Added status bar icon & tips</li>
<li>Added donate buttons</li>
<li>Added scrollbar for option window when needed</li>
<li>Fixed crash issue when ctrl2search on headers</li>
<li>Fixed bugs for Ctrl+Enter launch gloda search when no messages found</li>
<li>Fixed bugs for pined quick search buttons not work when switch between folders</li>
<li>Fixed bugs for transparent background help page on Mac OS</li>
<li>Fixed bugs for click2search triggers context menu on Mac OS</li>
<li>Compatible with TB5~TB23</li>
</ul>
</li><li>
Version 0.8.4: <ul>
<li>Added tonocc/bcc/cc/only/age search</li>
<li>Added options for show verbose information</li>
<li>Added options for where to create expression search folders</li>
<li>Fixed '<>' in search pattern issue when use click2search</li>
<li>Fixed search issue when use click2search and address is in address book</li>
<li>Fixed hang issue when '\t' exists in search pattern</li>
<li>Fixed minor bug that extension defined search terms show when search in address book</li>
<li>Fixed one bug that icons for quick search may missing when move search buttons to menubar or toolbar</li>
</ul>
</li><li>
Version 0.8.3: Fixed context menu missing issue when click right button.
</li><li>
Version 0.8.2: Work with Thunderbird 5. Fixed search bar shown issue. Fixed issue when search with complicated expressions.
</li><li>
Version 0.8.1: Fixed a bug: During search, 'Continue search with all folders' message will shown.
</li><li>
Version 0.8: <ul>
<li>Work with Thunderbird 3.3.</li>
<li>Added Click2Search similar to The Bat!</li>
<li>Added options to move expression search box to toolbar/menubar</li>
<li>Added options to act as normal search box</li>
<li>Added options to select 1st messages after hit enter in search box</li>
<li>Hit enter will launch gloda search if no message found</li>
<li>Hit Ctrl+B will focus on search box</li>
<li>before/after search can now search time within day</li>
<li>Added simple/regex/date search</li>
<li>Added filename for attachment name/type search (experimental, may crash)</li>
</ul>
</li><li>
Version 0.7: Added 'status/is' search. Added 'before/after' search. Added numerical calculation.
</li><li>
Version 0.6: Added Help & Contact link to Options dialog.
</li><li>
Version 0.5: Added Options dialog.
</li><li>
Version 0.4: Work with Thunderbird 3.1 .
</li><li>
Version 0.3: Shift+Enter to launch gloda search. Fix 'Cc','Cu','Ci','Cr' redefine error.
</li><li>
Version 0.2: Added 'g:' search mode for gloda search. Press 'Esc' in thread tree will clear the search criteria.
</li><li>
Version 0.1: First version, changed from GMailUI to make it works for Thunderbird 3.
</li></ul>

<h3>Known Issues of this extension or Thunderbird</h3>
<ul><li>
Shift+RightClick May not work for some versions of Thunderbird.
</li><li>
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=224392'>Bug 224392</a> - Add ability to filter by attachment name (extension)
</li><li>
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=338761'>Bug 338761</a> - searching body of emails for text doesn't match word-wrapped text
</li><li>
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=460737'>Bug 460737</a> -  Quickfilter ignores searches for friendly display names from address book contacts, as displayed on message header and message list by default (no or incomplete results for From, To, CC, BCC)
</li><li>
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=522886'>Bug 522886</a> - Implement "Recipients" column that shows all recipients (To, CC, and BCC)
</li><li>
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=546925'>Bug 546925</a> - custom header search is non-functional ('Run search on server' of Edit/Find/Search Messages doesn't work any more)
</li><li>
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=570815'>Bug 570815</a> - (qfwidget) Make Quickfilter optionally available as simple searchbox widget+stickypin (with filter criteria in persistent popup panel &/or dropdown; toolbar customization)
</li><li class="bz_closed">
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=124641'>Bug 124641</a> - Thunderbird does not handle multi-line headers correctly when search term spans lines
</li><li class="bz_closed">
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=363238'>Bug 363238</a> - saved searches fail for searches on x-headers
</li><li class="bz_closed">
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=474730'>Bug 474730</a> -  should search newest first - searching returns messages in bad order, making searches very time-consuming and irrelevant for large databases
</li><li class="bz_closed">
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=564328'>Bug 564328</a> - Keyboard shortcut Ctrl+F conflict and cmd_find ambiguity, used for both Find in This Message and Quick Filter 
</li><li class="bz_closed">
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=600140'>Bug 600140</a> - 'Unread' quick filter hides some unread messages (the beginning of a thread) 
</li><li class="bz_closed">
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=607295'>Bug 607295</a> - Provide UI for new archive granularity and folder structure options
</li><li class="bz_closed">
<a href='https://bugzilla.mozilla.org/show_bug.cgi?id=625472'>Bug 625472</a> - Quick search processes input after hiding it with escape
</li></ul>
<p>Compared with original GMailUI 0.6, these features are still missing:
<ul>
<li>Use 'Y' to archive selected mail to archive folder (use 'a')</li>
<li>Use J/K to move messages up and down, and Ctrl+J to mark a message as junk (conflict with builtin key mapping, use 'f/b' instead)</li>
<li>Key '/' focuses on the quick search bar (use Ctrl+F)</li>
</ul>
If you do need to change the hotkeys, please try other extensions below.
</p>

<h3>Other Extensions</h3>
You can try the following extensions to make your Thunderbird more convenient.<br/>
<ul>
<!--<li><a href='https://addons.thunderbird.net/en-US/thunderbird/addon/gmail-conversation-view/'>GMail Conversation View</a> and <a href='https://github.com/protz/GMail-Conversation-View/wiki/displaying-your-own-messages-in-the-inbox'>How to display sent messages in Inbox?</a></li>
<li><a href='http://kb.mozillazine.org/Keyconfig_extension'>Keyconfig</a></li>
-->
<li><a href='https://addons.thunderbird.net/en-US/thunderbird/addon/nostalgy_ng/'>Nostalgy++: easy archiving of emails</a></li>
<li>Other addons proposed by Opera Wang no longer work in TB 78</li></ul>

<h3>Thanks</h3>
<ul><li>
Ken Mixter - Original Author of GMailUI
</li><li>
Opera Wang 15 years of developing Expression Search/GmailUI
</li><li>
savo_msu - Author of <a href='https://addons.thunderbird.net/af/thunderbird/addon/one-click-search/'>One Click Search</a>
</li><li>
Kent James - Author of <a href='https://addons.thunderbird.net/en-US/thunderbird/addon/filtaquilla/'>FiltaQuilla</a>
</li><li>
Jiten Dedhia - Suggest for 'toonly' search
</li><li>
Jonathan Kamens - Patch for TB56 support
</li><li>
Greg Cowan - Suggest for date search
</li><li>
Mike Martinez - Suggest for bcc search
</li><li>
Olivier - Suggest for Shift/Ctrl+Enter
</li><li>
Paul Sednaoui - Suggest for 'only' search
</li><li>
Randolf Ebelt - Find a bug when search with complicate expressions
</li><li>
Olivier Brodeur - Find a bug when no messages found, gloda launched when Ctrl+Enter
</li><li>
Lee Yeoh - Find a bug for pined quick search buttons not work
</li><li>
Tom Zhu - Suggest for Enter to focus message pane, and validations before release.
</li></ul>

<h3>Feedback, Suggestions, and on-going Development</h3>
<p>Klaus Buecher/Opto's Home Page for TB 78+: <a href='https://github.com/opto/expression-search-NG'>expression-search-NG</a> </p>
<p>Opera Wang's Home Page (TB 60): <a href='https://github.com/wangvisual/expression-search'>expression-search</a>, not in active development      </p>
<p>Ken Mixters Home Page: <a href='http://sites.google.com/site/kmixter/gmailui'>GMailUI</a>, pre 2005    </p>

<p>&nbsp;</p>
</div>
</body>
</html>
