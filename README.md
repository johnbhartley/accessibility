# Accessibility Notes

> No one should be excluded from using your website simply because they have to access the Web in a different way. In other words, everyone can benefit in the end from making a site more accessible.

##Testing
* [Cynthia Says](http://www.cynthiasays.com/) (508, A, AA, AAA)
* [WAVE - Site](http://wave.webaim.org/)
* [WAVE - Chrome Extension](https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh?hl=en-US)
* [Total Validator - FireFox Extension](https://addons.mozilla.org/en-US/firefox/addon/total-validator/?src=search)
* [Section 508 - Technology Tools](http://www.section508.gov/technology-tools)
* [Fangs Screen Reader Emulator - Firefox Extension](https://addons.mozilla.org/en-US/firefox/addon/fangs-screen-reader-emulator/)
* Turn off CSS
* Turn off JS
* GreaseMonkey for adding scripts and styles
* Turn off mouse and try to get through full page
* Check tabindex of forms
* Form failures easy to figure out?
* Increase Mouse to maximum sensitivity to test user with steady but slower hand
* [Color Scheme Designer - Shows Multiple Color Blind Types](http://paletton.com/)
* [Sim Daltonism - Mac App of Color Blindness Simulation](https://michelf.ca/projects/sim-daltonism/)
* [VisCheck](http://www.vischeck.com/downloads/)
* [Daltonize - Color Blind Browser Extensions](http://www.daltonize.org/p/software.html)
* [Accessibility Developer Tools - Chrome Extension](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?hl=en)
* [Achecker - Accessibility Review w/ Paste HTML](http://achecker.ca/checker/index.php)

##Other Resources
* [The Paciello Group - Tools and Code Examples](http://www.paciellogroup.com/resources/)
* [Making Accessible Links](http://www.sitepoint.com/15-rules-making-accessible-links/)
* [Penn State WCAG2 Overview](http://accessibility.psu.edu/wcag2)
* [Chrome Accessibility Tools](https://code.google.com/p/google-axs-chrome/)
* [14 Tech Tools Used By Users With Disabilities](http://www.computerworld.com/article/2522955/computer-hardware/14-tech-tools-that-enhance-computing-for-the-disabled.html)
* [What Dyslexic Users See - Tips To Help](http://uxmovement.com/content/6-surprising-bad-practices-that-hurt-dyslexic-users/)
* [Accessibility Handbook by Katie Cunningham - digitally at libraries](http://shop.oreilly.com/product/0636920024514.do)
* [What Does Accessibility Mean? - Jonathan Snook](http://snook.ca/archives/accessibility_and_usability/what_does_accessibility_mean/)
* [Color Contrast Check - AA, AAA](http://snook.ca/technical/colour_contrast/colour.html)
* [PSU Image Map Tips](http://accessibility.psu.edu/imagemaps)

##508 Standards Summarized
1. Text equivalent. Alt, longdesc etc
1. Audio and Video/multimedia needs accompanying info that is =
1. All colored info can be seen without color
1. Organized for non-CSS -> Progressive enhancement
1. Redundant links shall be provided for each region of image map
1. Tables need row and column headers
1. Markup for tables
1. Frames need text
1. Be careful that pages don't flicker or blink between 2 Hz and 55 Hz
1. Use a Text Only Page when totally not able to make accessible
1. When scripting to add elements, information provided must have functional text
1. forms must have directions and cues to allow filling out
1. method to skip nav
1. Timed response needs to alert user about time

---

##Complete Blindness
* Rely on screen-readers
* not only those who are legally blind, but those who do not see well may also choose to use screen readers

> The completely blind will almost always have issues with the following: 

* Poorly structured HTML
* Images with no meaningful alt text 
* Flash that is inaccessible 
* Features that require vision, or where the fallback is poorly implemented
* Repetitive items that cannot be skipped
* Poorly structured forms

| Product | OS     | Availability | % Stats |
| ------- | ------ | ------------ | ---------- |
| JAWS    | Windows | Commercial |
| VoiceOver | Mac | Included
| Microsoft Narrator | Windows | Included
| Orca | Unix | Bundled With Gnome |
| BRLTTY | Unix | Included
|ChromeVox | All OS | Add-on for Chrome

Screen readers go from top to bottom, ignoring CSS-based layouts.

####In General all screen readers:
* List out headers
* read alt tags for images
* list links on a page
* use access keys
* read out tables in the column:content format
* __WILL__ obey `display: none` and `visibility: hidden`
* __WON'T__ pay attention to CSS layout order
* __WILL__ read text that's indented off the screen

Should always offer a "Skip Navigation" option as well as "Skip to Page Navigation"

####Language
* need language specifier: `<html lang="en">`
* if XHTML needs xml:lang too: `<html xml:lang="en" lang="en">`

####Tables
* should always include scope
	* indicate what type of data each column contains
	* head row `<th scope="col">`
	* body row starts with `<th scope="row">`
* needs summary on `<table>` element, `<caption>`, or `<synopsis>`
* allow user to skip table while also informing what information will be skipped

####Images
* for images added via CSS, use `text-indent` to hide text
* for images added in markup, use `alt` tag. Explain why the image was added in the first place
* If image is merely decorative use `alt=""`
* Try to use images in CSS if it is only decorative
* Graphs/charts need better explanations, what does the graph prove
* Use the TITLE tag instead to create tooltips or supplemental information, since it is supported in all browsers. [See the example] (http://accessibility.psu.edu/imageshtml#title) 
* [Tips for alt text] (http://webaim.org/articles/gonewild/#alttext)

####Image Maps
* should be client-side, not server-side
* If you want to use an image map, make it a client-side image map.
* Include meaningful alt-text for every <area> of the <map>, alt-text that conveys the function of that hotspot.
* Use an appropriate text alternative on the image itself. If there is no information beyond the hotspots then alt="" is appropriate.
* area element, target attribute values must contain any one of (case insensitive) _self, _top, _parent.

> Before the Target Corporation was sued by the [National Federation of the Blind](http://www.jimthatcher.com/law-target.htm) these image map areas did not have alt-text. In fact there were over a hundred hotspots on about a dozen image maps and none of the areas had alt-text. Screen readers try to find information to convey to a blind user when active images (including areas) lack alt-text. In the case of image maps, that will be the href of the area. [Jim Thatcher on Image Maps](http://www.jimthatcher.com/webcourse5.htm)

####Forms
* Labels, labels, labels. Always.
* Only form fields that don't need labels are buttons
* Make button text as helpful as possible
* Errors should be useful and explain the cause of the error
* CAPTCHAs should also have an audio option or human question
* Can also create hidden fields that bots would fill in. If filled in, form fails

####JavaScript
> According   to  a  2011  survey  by WebAIM.org ,  98.4%  of  respondents  had  JavaScript enabled... This doesn’t mean, however, that JavaScript is automatically accessible.

* Pure Text browsers still need to work properly
* Test by disabling JavaScript
* Inline JavaScript should be avoided
* [The Accessible Modal Window](http://accessibility.oit.ncsu.edu/training/aria/modal-window/version-3/)
* [Mozilla on ARIA dialog] (https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_dialog_role)
* [W3C on WAI-ARIA dialog box](http://www.w3.org/TR/wai-aria-practices/#dialog_modal)

###CSS
* stop removing outlines - [good article](http://tjvantoll.com/2013/01/28/stop-messing-with-the-browsers-default-focus-outline/)
* [outline from MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/outline)

####iframes
* must declare properly (if possible) `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/ frameset.dtd">`
* Title attribute that describes the content
* If iframes cannot be used, add a note like `<iframe src="menu.html"><a href="menu_noframe.html" title="Menu">Our menu</a></iframe>` to at least allow them to get to the page you wanted to show

####Access Keys
* Helps user move quickly around site
* `<a href="daytwo.html" accesskey="n">Next</a>`

| Key | Action |
| --- | ------ |
| 1 | Home Page |
|2|Skip to Content|
|3|Site Map|
|4|Search Field Focus|
|5|Advanced Search|
|6|Site Navigation Tree|
|9|Contact Information|
|0|Access Key Details|
|n|Next (from above example)|

* Could also assign numbers to nav items 1 - 10, 0

####WAI-ARIA
* Adding `role=` to elements
* Helpful for sites that auto-update
	* `<p role="status" aria-life="assertive">I'LL TELL YOU NOW</p>`
	* `<p role="status" aria-life="polite">I'll wait until the screen reader is done.</p>`
* `role="navigation"` will announce the navigation
* [Mozilla on ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)
* [Official WAI-ARIA documentation](http://www.w3.org/TR/wai-aria/)



##Low Vision Users
> a user with low vision is classified as anyone who must adjust the settings for the monitor to use a computer but is not using a screen reader.

* Common to increase the font size
* Entire site should grow without breaking
* Contrast between background and foreground should be as high as possible
* Add styling so when a field has focus, it is highlighted
* Try not to use colored images to show stats or information (*color blind folks*)
* Best to test once style guide is created

> Unlike  image  optimization  for  the  blind,  not  every  image  on  a  website  needs  to  be optimized for color blindness. The most important images to optimize are those that convey significant information to the user. *Maps, graphs and images with text especially*

*  Add a key for stylized graphics, maps, icons and/or charts

###Color contrast
* background: #fff; color must be darker than #595959


##Audio Accessibility
> Audio accessibility is more than making websites accessible for the profoundly deaf. This also covers those who are partially deaf and wear hearing aids.

> Subtitles are  more  than  simply  putting  the  text  beneath  the  image;  sounds,  cues  brought  by musical shifts, or tone should be included as well. 

* Avoid all caps when captioning if possible
* Colors should be highly readable
* Audio alerts need visual accompaniment 
* If a sound is vital to features, visual is needed as well

##Physical Accessibility
* might use eye-tracking devices, keyboard-only inputs, one-handed keyboards, special mice
* utilize tabindex for easier form traversal
* `<option>` should be unique for easier alphabetical selection
* use `<optgroup>` to better group items in a `<select>`
* Pop-ups should be created to be easily closed
	* ESC key is popular choice
	* "Close" buttons should have sizable target area
* Superfish similar navigation is nice, stays open for several seconds after mouseOut
* For timers, triple average user time to account for those with disabilities
* 

#####What not to do with the outline attribute
```
:focus {     
	outline: 0;
}
```

> __NOTE:__ With radio buttons, tabbing to that form element should hit only the first of the radio elements. If the user hits Tab again, she should move to the next form element, not the next radio button. The user would select a radio element by using arrow keys rather than by using tab.

##Cognitive Disabilities
* Users with mild to sever dyslexia, ADD, ADHD or information-processing disorder
* Easier to read Comic Sans or fonts where all letters are unique if dyslexic
* Custom stylesheet generally used by those with dyslexia
* Use web fonts instead of images with text for major elements
* Sans-serif fonts are easier to read for dyslexics
* ~10-15 words in a sentence
* Shorter paragraphs are easier to focus on (see "chunking")
* Off-black on off-white (like for color blindness) is best contrast, reduces eye strain
* Justified text is bad for dyslexic users, gaps can be distracting
* Meaningful Images are sometimes better than text (icons especially)
* If possible GIFs should only animate on mouseover
* Choose third-party adverts carefully
* Some users may invoke print stylesheet for easier reading
	* use sans-serif
	* no smaller than 12pt/16px
	* lines of text no longer than 60ish characters
* Search often not used by dyslexic users
* Don't hijack back, forward browser functionality
* Keep animations to a minimum
* Navigation should be global and consistent
* For longer forms consider "save progress" or auto-saving or even a progress bar
* Overly long pages can be problematic for AD/HD users

> Though graphical backgrounds can increase branding and interest for a web page, they can be distracting for someone with dyslexia and might also render text unreadable. The best practice is to never have images behind text. No matter how subtle the pattern is, it can make it more difficult to make out the word shape.


##General Trouble Spots:
* navigation that snaps back up 
* click target areas
* Menus in unreadable PDF-only or merely images of the menu are unusable
* Displaying addresses with images is bad
* Displaying any text with images instead of text is bad

---
---

#Pro HTML5 Accessibility
###Chapter 1
International Standards Organization defines accessibility this way:
> The usability of a product, service, environment or facility by people with the widest range of capabilities.

And the W3C says:
> Web accessibility means that people with disabilities can use the Web. More specifically, web accessibility means that people with disabilities can perceive, understand, navigate and interact with the Web, and that they can contribute to the Web. Web accessibility also benefits others, including older people with changing abilities due to aging. 

* *AT = abbreviation for Assistive Technology*
* *WAI = Web Accessibility Initiative*
* *WCAG = Web Content Accessibility Guidelines*
* *ADA = Americans with Disabilities Act*

####Section 504
Section 504, 29 USC 794. Short version, programs using federal funds cannot discriminate against those with disabilities. 
####Section 508
Bars government from collecting electronic information without allowing accessibility to those with disabilities, including services of web design.
####ADA Title II
Communications with persons with disabilities must be as effective as communications with others

###The WCAG's 4 Simple Principles (POUR)
* Content must be __Perceivable__
* Interface elements must be __Operable__
* Content and controls must be __Understandable__
* Content should be __Robust__ enough to work with current and future technologies

---

###Chapter 2
* 


---
---
---

#Lynda Foundations of UX: Accessibility
###2a - Managing Flow
* keyboard absolutely must work for all pages
* need to keep items grouped together more

###2b - Re-creating Visual Interactions
* accessible can be redundant, but needs to happen so people have access in multiple ways.

###2c - Ensuring Proximity
* if two things are related they need to be next to each other in the interface
* modal should be right after modal open button or manage flow so the two are connected

###2d - Setting Expectations
* disability can be an amplifier of trouble spots
* tough for regular user, even harder for user with disability
* auto-advancing fields can be troublesome and hard to edit via a keyboard. 

###2f - Designing for Memory Issues
* relying on placeholder text prevents folks from remembering what they're inputting
* errors are more helpful right next to the form where the error exists
* error colleciton bucket has it's uses, but right next to field is good for memory issues

###3a - Voice Recognition Software
* Dragon natural speaking is most common 

###3b - Screen Magnifiers
* sometimes use dual magnified, non-magnified view
* picture in picture magnified only on cursor hover

###3c - Screen Readers
* say everything mode - reads all
* keyboard navigation - tabs, arrows
* form to form, heading to heading, allows user to scan easier
* 







