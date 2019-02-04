I recently read this blog post from <a href="https://twitter.com/LuiseFreese" target="_blank" rel="noopener">Luis Freese</a> about <a href="https://todo.microsoft.com/" target="_blank" rel="noopener">Microsoft To-do</a> - <a href="https://link.medium.com/DfCakRc20T" target="_blank" rel="noopener">11 reasons why I fell in love with Microsoft To-Do</a> and I couldn't agree more. In-fact, I can add 10 more to that list! :)

One of the reasons mentioned was around moving flagged e-mails to To-Do using <a href="http://flow.microsoft.com">Microsoft Flow</a> . To take this a step further, I wanted a way to <strong><span style="color: #3a47ba;">assign due dates and reminders for the e-mails based on some priority level</span></strong>. Below is a step-by-step approach to achieve this -

Note: This applies only for desktop Outlook
<ul>
	<li>Step 1: Create Outlook shortcuts to flag an e-mail and assign an importance level.</li>
</ul>
[caption id="attachment_147" align="aligncenter" width="392"]<img class=" size-full wp-image-147 aligncenter" src="https://thatapiguytech.files.wordpress.com/2019/02/2019-02-04-09_31_45-inbox-vivek.bavishi40regalbeloit.com-outlook.png" alt="2019-02-04 09_31_45-Inbox - Vivek.Bavishi@regalbeloit.com - Outlook" width="392" height="94" /> Open Quick Steps in Microsoft Outlook.[/caption]

[caption id="attachment_146" align="aligncenter" width="543"]<img class="alignnone size-full wp-image-146" src="https://thatapiguytech.files.wordpress.com/2019/02/2019-02-04-09_34_20-manage-quick-steps.png" alt="2019-02-04 09_34_20-Manage Quick Steps" width="543" height="390" /> Click on 'New' or if you already have a configured quick step, click on 'Edit'.[/caption]

[caption id="attachment_145" align="aligncenter" width="494"]<img class=" size-full wp-image-145 aligncenter" src="https://thatapiguytech.files.wordpress.com/2019/02/2019-02-04-09_35_07-edit-quick-step.png" alt="2019-02-04 09_35_07-Edit Quick Step" width="494" height="561" /> Click on "Add Action" and choose "Set Importance" action and then select the Importance level from the drop down. Also, select the shortcut key so that you can assign the quick step from your keyboard.[/caption]

[caption id="attachment_144" align="aligncenter" width="493"]<img class=" size-full wp-image-144 aligncenter" src="https://thatapiguytech.files.wordpress.com/2019/02/2019-02-04-09_36_55-edit-quick-step.png" alt="2019-02-04 09_36_55-Edit Quick Step" width="493" height="559" /> Similarly, set up similar shortcuts for the 3 different levels of Importance. Choose the shortcut keys wisely! For the High Importance I chose the "Ctrl+Shift+1", for Medium Importance - "Ctrl+Shift+2" and for Low Importance - "Ctrl+Shift+3".[/caption]

So now you can use these shortcuts to quickly assign an importance level and flag the e-mails.
<ul>
	<li>Step 2 - Set up the Flow in Microsoft Flow to assign the flagged e-mail as a task in To-Do with a due date based on the Importance. (Download the Flow files from her)</li>
</ul>
[caption id="attachment_149" align="aligncenter" width="652"]<img class=" size-full wp-image-149 aligncenter" src="https://thatapiguytech.files.wordpress.com/2019/02/2019-02-04-10_01_44-edit-your-flow-_-microsoft-flow.png" alt="2019-02-04 10_01_44-Edit your flow _ Microsoft Flow" width="652" height="363" /> Start with the trigger "When an email is flagged" and  then initialize a variable to store the number of days before due date.[/caption]

[caption id="attachment_148" align="alignnone" width="1847"]<img class="alignnone size-full wp-image-148" src="https://thatapiguytech.files.wordpress.com/2019/02/2019-02-04-10_02_34-edit-your-flow-_-microsoft-flow.png" alt="2019-02-04 10_02_34-Edit your flow _ Microsoft Flow" width="1847" height="425" /> Based on the 'Importance' value from the e-mail, set the DueDays variable value. Personally, I wanted to set High Importance - 1 day, Medium Importance to 3 days and Low Importance to 5 days. For e-mails where I don't set the importance level, I set the value to 7 days.[/caption]

[caption id="attachment_150" align="aligncenter" width="757"]<img class=" size-full wp-image-150 aligncenter" src="https://thatapiguytech.files.wordpress.com/2019/02/2019-02-04-11_57_37-edit-your-flow-_-microsoft-flow.png" alt="2019-02-04 11_57_37-Edit your flow _ Microsoft Flow" width="757" height="570" /> Now, add the "Add a to-do" action and set the values as defined above. You can customize it based on your liking. Remember to set the body content type to HTML to have a nice looking e-mail in the note of the to-do. For due date and reminder, use the expressions as defined below.[/caption]

 

<img class="aligncenter size-full wp-image-152" src="https://thatapiguytech.files.wordpress.com/2019/02/2019-02-04-11_55_33-edit-your-flow-_-microsoft-flow-e1549305248535.png" alt="2019-02-04 11_55_33-Edit your flow _ Microsoft Flow" width="532" height="104" />

<img class=" size-full wp-image-151 aligncenter" src="https://thatapiguytech.files.wordpress.com/2019/02/2019-02-04-11_56_20-edit-your-flow-_-microsoft-flow.png" alt="2019-02-04 11_56_20-Edit your flow _ Microsoft Flow" width="526" height="71" />

<em>Due date expression - addDays(utcNow(),variables('DueDays')) </em>

The expression above adds the number of days before the task is due to the current time.

<em>Reminder date time expression - addDays(utcNow(),sub(variables('DueDays'),1))</em>

The expression above reduces the number of due days by 1 day and adds it to the current time, so you can get the reminder 1 day before the task is due. Of-course, you can customize this as well to your liking.

Step 3 - Sit back and enjoy!

 

Bonus tip -

When you try adding emojis to be used as an icon for a List category, you get very limited options. If you want to use some other emoji, try out the method described below. To get the emoji menu in Windows 10 press "Windows key + ;" . You can also search for emojis from this menu. In my case, I searched for 'target" and got the emoji I wanted.

<img class=" size-full wp-image-153 aligncenter" src="https://thatapiguytech.files.wordpress.com/2019/02/ezgif.com-add-text.gif" alt="ezgif.com-add-text.gif" width="646" height="304" />

 
<p style="text-align: center;">Have fun using To-Do!</p>
