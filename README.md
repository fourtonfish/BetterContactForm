Better Contact Form
=================
![A better contact form experience](/screenshot.png)


This is more of an **idea for UX improvement** rather than a complete solution<sup>1</sup>. My proposal is to: 

1. allow your visitors to include **any form of contact** on your contact form (eg: phone number or Twitter handle instead of an email)

2. include **an option to use user's email client** if he or she really doesn't like contact forms

3. if your visitor uses an email in the form, **send him or her a confirmation email**

To try the form, download the code from this repository and change the _mail.php_, specifically these two parts: 

	$recipient = "your@email.com";
	...
	<a href=\"http://YOURSITE.COM\">

Also, in _index.html_:

	<a id="contactmelink" onclick="javascript:sendEmail();" href="mailto:your@email.com">Send me an email</a>


I am including **two versions** of the form, a simple one (which has one small issue<sup>2</sup>) and a fancier one that uses Twitter Bootstrap.


***
<sup>1</sup> These contact forms **don't validate the email**, which is pretty much the whole point. If your visitor wants to use a fake email, it is not hard to make one up. If you go as far as to try to see if the email really exists, it is still trivial to bypass your form by creating yet another free email account.

Furthermore, I am using **a very simple implementation of the honeypot technique** to prevent spam. You can read more about this method here: http://nedbatchelder.com/text/stopbots.html (or just google it). In a nutshell: you are creating a **hidden input field**, here called _fullname_. The _email.php_ script will check if the field was filled out (bots don't process CSS, so to them it will be visible).

One drawback of this technique is that the hidden field is visible to people using screen readers (or certain browsers), to which one simple solution is to use something like _"Ignore this field, thank you"_ for a title.

Again, this is **not a complete solution**, so please feel free to implement your own security method(s) here.

<sup>2</sup> I seem to have a problem in Chrome when using Gmail as my default email client. Attempting to show the form automatically opens a new email in Gmail. The only solution I came up with is to remove the no-javascript fallback, that is in index.html I would change this:

	<a id="contactmelink" onclick="javascript:sendEmail();" href="mailto:your@email.com">Send me an email</a>

To this:

	<a id="contactmelink" onclick="javascript:sendEmail(); return false;" href="#">Send me an email</a>

On Linux, I have the problem even when using Firefox (In Windows it's limited only to Chrome, Firefox works fine).

The "fancy" version doesn't have this problem at all.