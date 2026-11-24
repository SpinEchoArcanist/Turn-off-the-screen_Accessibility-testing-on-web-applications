---
Type:
  - Notes
Community:
  - Test Practice
Comment: VoiceOver commands cheat sheet for mobile accessibility testing
tags:
  - Test/Accessibility
  - iOS
  - VoiceOver
---

# Appendix D — VoiceOver (iOS): Accessibility Testing Cheat Sheet

> **Scope.** Gestures below are those documented by Apple for VoiceOver on iPhone. Exact behaviour may vary with the iOS version. Before the first test, practise the gestures in **Settings > Accessibility > VoiceOver > VoiceOver Practice**: once VoiceOver is on, the iPhone must be operated with VoiceOver gestures.

---

## 1. Turn VoiceOver on and off

| Method | How | Note |
|---|---|---|
| Settings | Settings > Accessibility > VoiceOver | Always available |
| Siri | "Turn on VoiceOver" / "Turn off VoiceOver" | If Siri is set up |
| Accessibility Shortcut | Triple-click the side button (iPhone with Face ID) | Works only once the Accessibility Shortcut is set to VoiceOver |

**Tip:** set the Accessibility Shortcut **before** the first test, so VoiceOver can be turned off quickly.

---

## 2. Core navigation gestures

|Action|Gesture|Purpose in testing|
|---|---|---|
|Hear the item under the finger|Touch or drag one finger over the screen|Check what is announced at a given position|
|Select item|1-finger tap|Focus element and announce label|
|Activate item|1-finger double tap|Trigger control|
|Next item|1-finger swipe right|Forward navigation order|
|Previous item|1-finger swipe left|Backward navigation order|
|First / last item on the screen|4-finger tap near the top / bottom of the screen|Check the start and end of the reading order|
|Read from top|2-finger swipe up|Full-screen review|
|Read from the current item|2-finger swipe down|Review from a given point|
|Pause / resume speech|2-finger tap|Control speech output|
|Scroll one page|3-finger swipe up / down|Scroll content|
|Item Chooser (list of items on screen)|2-finger triple tap|Find an element quickly|
|Escape / back|2-finger scrub (move two fingers back and forth three times quickly, making a "z")|Dismiss alerts, exit dialogs / views|

---

## 3. The rotor

|Action|Gesture|Testing purpose|
|---|---|---|
|Choose a rotor setting|2-finger rotation (as if turning a dial); VoiceOver announces each setting, lift the fingers to choose|Change navigation mode|
|Move to the next item of the chosen setting|1-finger swipe down|Validate structure (headings, form controls, landmarks, etc.)|
|Move to the previous item of the chosen setting|1-finger swipe up|Check semantic grouping|

**Edit the list:** Settings > Accessibility > VoiceOver > Rotor > Rotor Items.

---

## 4. Interaction behavior

|Action|Gesture|Testing purpose|
|---|---|---|
|Activate default action|Double tap|Equivalent of tap/click|
|Custom actions|When VoiceOver announces "Actions available": rotor **Actions**, 1-finger swipe up / down to hear each action, double tap to perform it|Verify custom actions|
|Long press or other standard gesture|Double tap and hold until three rising tones play, then perform the gesture|Check long-press behaviour; ensure secondary actions are also exposed in the Actions rotor|
|Adjust a slider or other adjustable control|Select it, then 1-finger swipe up / down|Check adjustable controls|
|Start or stop the current action (media, recording)|2-finger double tap|Check the main action of media controls|

---

## 5. Text editing

|Action|Gesture|Testing purpose|
|---|---|---|
|Enter edit mode|Double tap the field|Focus input and open the keyboard|
|Character / word navigation|Rotor **Characters** or **Words** + 1-finger swipe up / down|Validate granularity|
|Edit actions (select, copy, paste)|Rotor **Edit** (available while editing a text field) + 1-finger swipe up / down, then double tap|Verify text editing and selection|

---

## 6. System controls (testing support)

| Action | Gesture | Purpose |
| --- | --- | --- |
| Toggle VoiceOver | Triple-click the side button | **Enable or disable VoiceOver** (once the Accessibility Shortcut is set to VoiceOver) |
| Pause / resume speech | 2-finger tap | Control verbosity |
| Mute / unmute VoiceOver | 3-finger double tap | Silence speech while keeping VoiceOver active |
| VoiceOver Practice | Settings > Accessibility > VoiceOver > VoiceOver Practice | Practise gestures without triggering them |

---

## 7. Screen Curtain (important for realistic testing)

| Feature | Gesture | Why it matters |
| --- | --- | --- |
| Screen Curtain | 3-finger triple tap (3-finger quadruple tap if Zoom is also on) | **Turns the display off while keeping VoiceOver active** — the tester relies only on what is announced, like a blind user |

---

## 8. Safari navigation with VoiceOver (web testing focus)

| Action | Gesture / Command | Purpose in testing |
| --- | --- | --- |
| Go to next page element | 1-finger swipe right | Move through text, links, buttons, form fields |
| Go to previous element | 1-finger swipe left | Reverse navigation order |
| Activate link | 1-finger double tap | Open page / trigger navigation |
| Scroll page | 3-finger swipe up/down | Move through web content |
| Read continuously | 2-finger swipe up (from the top) or down (from the current item) | Audit full page content flow |
| Pause speech | 2-finger tap | Control verbosity during inspection |
| Go back | 2-finger scrub, or select Safari's Back button | Leave a dialog or return to the previous screen |
| Go forward | Select Safari's Forward button (VoiceOver has no "go forward" gesture) | Go to next page |

### Safari-specific navigation controls

| Action | Gesture / Command | Purpose in testing |
| --- | --- | --- |
| Open rotor (web items) | 2-finger rotate | Switch between Headings, Landmarks, Links, Visited Links, Form Controls, Tables, etc. |
| Navigate by headings | Rotor → Headings + swipe down/up | Validate semantic structure of page |
| Navigate by landmarks | Rotor → Landmarks + swipe down/up | Check the page regions |
| Navigate by links | Rotor → Links + swipe down/up | Check link structure and labeling |
| Navigate by form controls | Rotor → Form Controls + swipe down/up | Ensure inputs are reachable and labeled |
| List the items of the page | Item Chooser: 2-finger triple tap | Locate a specific element quickly |

---

## 9. Accessibility QA checkpoints

|Area|Validation target|
|---|---|
|Focus order|Logical and complete when swiping right|
|Labels|Every element announced meaningfully|
|Actions|All interactions reachable via VoiceOver|
|Modals|Content behind an open dialog not reachable|
|Updates|Dynamic changes and messages announced|
|Hidden UI|No access to hidden or inactive elements|
|Screen hidden|Main task can be completed with Screen Curtain on|

---

## 10. Common failures

| Issue | Observable symptom |
| --- | --- |
| Missing labels | Only the role ("Button") announced, without a name |
| Broken order | Skipped or looping navigation |
| Non-focusable UI | Elements unreachable by swiping |
| Silent updates | No audio feedback after an action |
| Modal escape issues | Background still reachable |

---

## Sources

- Apple — [iPhone User Guide, Use VoiceOver gestures on iPhone](https://support.apple.com/guide/iphone/use-voiceover-gestures-iph3e2e2281/ios)
- Apple — [Learn VoiceOver gestures on iPhone (iOS 13 edition, gesture tables)](https://support.apple.com/guide/iphone/iph3e2e2281/13.0/ios/13.0)
- Apple — [Turn on and practice VoiceOver on iPhone](https://support.apple.com/guide/iphone/turn-on-and-practice-voiceover-iph3e2e415f/ios)
- Apple Support — [About the VoiceOver rotor on iPhone or iPad](https://support.apple.com/en-us/111796)
- Apple Developer Forums — [Adjustable elements and custom accessibility actions (Actions rotor)](https://developer.apple.com/forums/thread/726964)
- AppleVis — [iDevice Primer 103: What is the rotor for and how do I use it?](https://applevis.com/guides/idevice-primer-103-what-rotor-how-do-i-use-it) (community guide: Edit rotor, Actions)
