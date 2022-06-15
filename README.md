## A11yFABTest - Test Floating Action Button accessibility reading order

This project demonstrates issues with manipulating the accessibility reading order of a Floating Action Button.
If accessibilityTraversalAfter is not used to coerce the reading order, then a FAB will always appears last in 
reading order in the layouts I've tried, particularly FrameLayout and ConstraintLayout. 

This sample does not demonstrate the alternative layouts I've tried to manipulate FAB reading order
without accessibilityTraversalAfter, but instead focuses on how even with accessibilityTraversalAfter, 
the reading order of a FAB is unreliable when the page becomes long enough to scroll.

I've tested this on Android 5.1 (Moto G1), Android 8.1.0 (Moto G5), and Android 12 (Pixel 3) phones,
as well as and Android 11 (Samsung Galaxy Tab A8) tablet with additional content on the second fragment (now commented out).

This sample has two screens: one with less content (which should not be scrollable in portrait mode) 
and one with more content so it will force scrolling on phones (although not tablets). 
On the first screen, the FAB reads reliably after the initial fragment heading text. 
On the second screen, TalkBack emits a click-like sound after the initial fragment heading text, 
and the FAB is not read at all if you continue to swipe to the next item. However, if the screen
is scrolled to the bottom first, TalkBack will read the FAB after reading the appbar items.

The sample is based on the Android Studio-generated Basic Activity template, but with the FAB moved
from activity_main.xml and MainActivity.kt into the two fragments. 

Any solutions, either layout or code-based, which preserve the visual layout of these pages 
(particularly the FAB in the lower-right corner with text scrollable under it) and reliably 
place the FAB in reading order after the heading text would be appreciated.