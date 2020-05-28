---
layout: post
title: Color and contrast
authors:
  - dgash
  - megginkearney
  - rachelandrew
  - robdodson
date: 2020-05-28
description: |
  If you have good vision, it's easy to assume that everyone perceives colors, or text legibility, the same way you do — but of course that's not the case.
tags:
  - blog
  - accessibility
---

If you have good vision, it's easy to assume that everyone perceives colors,
or text legibility, the same way you do — but of course that's not the case.

As you might imagine,
some color combinations that are easy for some people to read are difficult or impossible for others.
This usually comes down to color contrast,
the relationship between the foreground and background colors' luminance.
When the colors are similar, the contrast ratio is low;
when they are different, the contrast ratio is high.

The [WebAIM guidelines](https://webaim.org/standards/wcag/) recommend an AA (minimum) contrast ratio of 4.5:1 for all text.
An exception is made for very large text (120-150% larger than the default body text),
for which the ratio can go down to 3:1. Notice the difference in the contrast ratios shown below.

<figure class="w-figure">
  <img src="./contrast-ratios.jpg" alt="An image showing the different contrast ratios">
</figure>

The contrast ratio of 4.5:1 was chosen for level AA
because it compensates for the loss in contrast sensitivity
usually experienced by users with vision loss equivalent to approximately 20/40 vision.
20/40 is commonly reported as typical visual acuity of people at about age 80.
For users with low vision impairments or color deficiencies,
we can increase the contrast up to 7:1 for body text.

You can use the Accessibility Audit in Lighthouse to check your color contrast.
Open DevTools, click Audits, and select Accessibility to run the report.

<figure class="w-figure">
  <img src="./accessibility-audit.jpg" alt="An image showing the different contrast ratios">
</figure>

For a more complete report, install the [Accessibility Insights Extension](https://accessibilityinsights.io/).
One of the checks in the Fastpass report, is color contrast.
You will get a detailed report of any failing elements.

<figure class="w-figure">
  <img src="./fastpass-contrast.jpg" alt="The report in Accessibility Insights">
</figure>

## Don't convey information with color alone

There are roughly 320 million people worldwide with color vision deficiency.
About 1 in 12 men and 1 in 200 women have some form of "color blindness";
that means about 1/20th, or 5%, of your users will not experience your site the way you intended.
When we rely on color to convey information, we push that number to unacceptable levels.

{% Aside %}
Note: The term "color blindness" is often used to describe a visual condition where a person has trouble distinguishing colors,
but in fact very few people are truly color blind.
Most people with color deficiencies can see some or most colors,
but have difficulty differentiating between certain colors such as reds and greens (most common),
browns and oranges, and blues and purples.
{% endAside %}

For example, in an input form,
a telephone number might be underlined in red to show that it is invalid.
But to a color deficient or screen reader user, that information is not conveyed well, if at all.
Thus, you should always try to provide multiple avenues for the user to access critical information.

<figure class="w-figure">
  <img src="./input-form1.png" alt="A image of an input form with an incorrect phone number highlighted only with a red color.">
</figure>

The [WebAIM checklist states in section 1.4.1](https://webaim.org/standards/wcag/checklist#sc1.4.1) that
"color should not be used as the sole method of conveying content or distinguishing visual elements."
It also notes that "color alone should not be used to distinguish links from surrounding text"
unless they meet certain contrast requirements.
Instead, the checklist recommends adding an additional indicator such as an underscore
(using the CSS text-decoration property) to indicate when the link is active.

An easy way to fix the previous example is to add an additional message to the field,
 announcing that it is invalid and why.

<figure class="w-figure">
  <img src="./input-form2.png" alt="The same input form as in the last example, this time with a text label indicating the problem with the field.">
</figure>

When you're building an app, keep these sorts of things in mind
and watch out for areas where you may be relying too heavily on color to convey important information.

If you're curious about how your site looks to different people,
or if you rely heavily on the use of color in your UI,
you can use DevTools to simulate various forms of visual impairment,
including different types of color blindness.
Chrome includes an Emulate Vision Deficiencies feature.
To access it open DevTools and select Rendering,
you can then emulate the following color deficiencies.

- Protanopia: the inability to perceive any red light.
- Deuteranopia: the inability to perceive any green light.
- Tritanopia: the inability to perceive any blue light.
- Achromatopsia: the inability to perceive any color except for shades of grey (extremely rare).

<figure class="w-figure">
  <img src="./emulate.jpg" alt="Emulating the vision of a person with Achromatopsia shows our page in greyscale.">
</figure>

## High contrast mode

High-contrast mode allows a user to invert foreground and background colors,
which often helps text stand out better.
For someone with a low vision impairment,
high-contrast mode can make it much easier to navigate the content on the page.
There are a few ways to get a high-contrast setup on your machine.

Operating systems like Mac OSX and Windows offer high-contrast modes
that can be enabled for everything at the system level.
Or users can install an extension, like the
[Chrome High Contrast extension](https://chrome.google.com/webstore/detail/high-contrast/djcfdncoelnlbldjfhinnjlhdjlikmph?hl=en)
to enable high-contrast only in that specific app.

A useful exercise is to turn on high-contrast settings
and verify that all of the UI in your application is still visible and usable.

For example, a navigation bar might use a subtle background color
to indicate which page is currently selected.
If you view it in a high-contrast extension, that subtlety completely disappears,
and with it goes the reader's understanding of which page is active.

<figure class="w-figure">
  <img src="./tab-contrast.png" alt="Screenshot of a navigation bar in high contrast mode where the acvtive tab is hard to read">
</figure>

Similarly, if you consider the example from the previous lesson,
the red underline on the invalid phone number field might be
displayed in a hard-to-distinguish blue-green color.

<figure class="w-figure">
  <img src="./high-contrast.jpg" alt="Screenshot of the address form used earlier, this time in high contrast mode. The color change of the invalid element is hard to read.">
</figure>

If you are meeting the contrast ratios covered earlier
you should be fine when it comes to supporting high-contrast mode.
But for added peace of mind, consider installing the
[Chrome High Contrast extension](https://chrome.google.com/webstore/detail/high-contrast/djcfdncoelnlbldjfhinnjlhdjlikmph?hl=en)
and giving your page a once-over just to check that everything works, and looks, as expected.