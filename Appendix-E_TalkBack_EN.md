---
Type:
  - Notes
tags:
  - Test/Accessibility
  - Android
  - TalkBack
Comment: TalkBack commands cheat sheet for mobile accessibility testing
---

# Appendix E — TalkBack (Android): Accessibility Testing Cheat Sheet

> **Scope.** Gestures below apply to **TalkBack 9.1 and later** on devices that support multi-finger gestures (to check: with TalkBack on, do a three-finger tap — if the TalkBack menu opens, multi-finger gestures are supported). Single-finger alternatives are given where they exist. Exact behaviour may vary with the device manufacturer, Android version and TalkBack version.

---

## 1. Turn TalkBack on and off

| Method | How | Note |
|---|---|---|
| Settings | Settings > Accessibility > TalkBack > Use TalkBack | Always available |
| Volume-key shortcut | Hold both volume keys for a few seconds | Must be enabled (Settings > Accessibility > TalkBack > TalkBack shortcut) |
| Google Assistant | "Hey Google" then "Turn on TalkBack" / "Turn off TalkBack" | If Assistant is set up |
| External keyboard | Action + Alt + T | Latest Android 16 only |

**Tip:** enable the volume-key shortcut **before** the first test, so TalkBack can be turned off quickly.

---

## 2. Core navigation gestures

| Action | Gesture | Purpose in testing |
|---|---|---|
| Hear the item under the finger | Drag one finger on the screen (explore by touch) | Check what is announced at a given position |
| Select an item | Tap | Focus element and hear its label |
| Next item | Swipe right | Forward navigation order |
| Previous item | Swipe left | Backward navigation order |
| Activate item | Double-tap | Trigger the control |
| Long press | Double-tap and hold | Check long-press actions |
| Scroll | Two-finger swipe up / down / left / right | Scroll content |
| Pause / resume speech | Two-finger tap | Control speech output |

---

## 3. Reading controls (equivalent of the VoiceOver rotor)

| Action | Gesture |
|---|---|
| Next reading control | Three-finger swipe down (or one-finger swipe up then down) |
| Previous reading control | Three-finger swipe up (or one-finger swipe down then up) |
| Next item of the selected control | Swipe down |
| Previous item of the selected control | Swipe up |

**Default reading controls:** Characters · Words · Lines · Paragraphs · Rows and columns (tables) · **Headings** · **Controls** (buttons, checkboxes, text fields) · **Links** · Speech rate · Spoken language · Screen search.

| Reading control | Testing purpose |
|---|---|
| Headings | Validate the heading structure of the page |
| Controls | Check that every input and button is reachable and labelled |
| Links | Check link names out of context |
| Rows and columns | Check data table navigation |

**Edit the list:** TalkBack settings > Edit menus > Customize reading controls.

**Note:** landmarks are not among the default reading controls — headings carry most of the structural navigation on Android.

---

## 4. TalkBack menu

| Action | Gesture |
|---|---|
| Open the TalkBack menu | Three-finger tap (or swipe down then right in one motion) |

Default options include: **Read from focused item** · Copy last spoken phrase · Spoken language · **Screen search** · **Hide or show screen** · Voice commands · TalkBack settings · Text-to-speech settings · Braille settings.

Depending on the focused item, the menu can also show **Actions**, **Links**, edit options, or label options — use it to verify that custom actions are exposed.

---

## 5. Android system gestures with TalkBack

| Action | Single-finger gesture | Multi-finger gesture (gesture navigation on) |
|---|---|---|
| Back | Swipe down then left | Two-finger swipe from the left or right edge |
| Home | Swipe up then left | Two-finger swipe up from the bottom |
| Recent apps | Swipe left then up | Two-finger swipe up from the bottom and hold |
| Notifications | Swipe right then down | Two-finger swipe down from the top |

---

## 6. Text editing

| Action | Gesture |
|---|---|
| Start / end selection mode | Two-finger double tap and hold |
| Copy selected text | Three-finger double tap |
| Cut (in selection mode) | Three-finger double tap and hold |
| Paste | Three-finger triple tap |

---

## 7. Help and practice

| Action | Gesture |
|---|---|
| Practice gestures | Four-finger tap |
| TalkBack help | Four-finger double tap |
| Pass-through (next gesture interpreted as if TalkBack were off) | Four-finger double tap and hold |

---

## 8. Hide screen (important for realistic testing)

| Feature | How | Why it matters |
|---|---|---|
| Hide or show screen | TalkBack menu > Hide or show screen | **Hides the display while TalkBack stays active** — the tester relies only on what is announced, like a blind user |
| Hide screen shortcut | Press both volume keys 3 times | Google documents this shortcut only for **TalkBack 8.2 and earlier**; with the versions covered by this cheat sheet, use the TalkBack menu |

---

## 9. Chrome navigation with TalkBack (web testing focus)

| Action | Gesture | Purpose in testing |
|---|---|---|
| Next / previous page element | Swipe right / left | Move through text, links, buttons, fields |
| Read from the current element | TalkBack menu > Read from focused item | Audit the content flow |
| Navigate by headings | Reading control **Headings** + swipe down / up | Validate semantic structure |
| Navigate by form controls | Reading control **Controls** + swipe down / up | Ensure inputs are reachable and labelled |
| Navigate by links | Reading control **Links** + swipe down / up | Check link structure and labelling |
| Find text on screen | TalkBack menu > Screen search | Locate a specific element quickly |
| Activate link or button | Double-tap | Trigger navigation or action |
| Go back | Back gesture (section 5) | Leave a dialog or return to the previous page |

---

## 10. Accessibility QA checkpoints

| Area | Validation target |
|---|---|
| Focus order | Logical and complete when swiping right |
| Labels | Every element announced meaningfully |
| Actions | All interactions reachable with TalkBack |
| Modals | Content behind an open dialog not reachable |
| Updates | Dynamic changes and messages announced |
| Hidden UI | No access to hidden or inactive elements |
| Screen hidden | Main task can be completed with Hide screen enabled |

---

## 11. Common failures

| Issue | Observable symptom |
|---|---|
| Missing labels | Only the role ("Button") announced, without a name |
| Broken order | Skipped or looping navigation |
| Non-focusable UI | Elements unreachable by swiping |
| Silent updates | No audio feedback after an action |
| Modal escape issues | Background still reachable |
| Gesture-only functions | Function impossible without a swipe, pinch or drag |

---

## Sources

- Google — [Turn on TalkBack](https://support.google.com/accessibility/android/answer/6007100?hl=en)
- Google — [Use TalkBack gestures](https://support.google.com/accessibility/android/answer/6151827?hl=en)
- Google — [Use the TalkBack menu & reading controls](https://support.google.com/accessibility/android/answer/6007066?hl=en)
- Google — [Learn about TalkBack settings](https://support.google.com/accessibility/android/answer/6006589?hl=en)
- Google — [Get started on Android with TalkBack](https://support.google.com/accessibility/android/answer/6283677)
