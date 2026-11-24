# Appendix C — Windows Narrator: Web Accessibility Testing Guide

## Purpose

This guide is intended for accessibility testers who have never used Windows Narrator. It lets them run web accessibility tests with Narrator without any other documentation.

It focuses exclusively on using Narrator to navigate and inspect web applications. It does **not** explain accessibility concepts, WCAG requirements, or testing methodologies.

The guide covers:

- Starting and configuring Narrator
- Navigating web pages and reading their content
- Using Scan Mode
- Moving between common web elements (headings, links, buttons, form controls, landmarks)
- Checking the keyboard focus
- Testing a form step by step
- Understanding Narrator announcements

[Complete guide to Narrator \| Microsoft Support](https://support.microsoft.com/en-us/accessibility/windows/narrator/complete-guide-to-narrator)

---

## 1. Starting and Stopping Narrator

### Turn Narrator On/Off

```text
Ctrl + Windows + Enter
```

Turns Narrator on or off.

---

## 2. The Narrator Key

By default, both of these keys act as the Narrator modifier key:

```text
Caps Lock
```

```text
Insert
```

Throughout this guide:

```text
Narrator = Caps Lock
```

Example:

```text
Narrator + T
```

means

```text
Caps Lock + T
```

---

## 3. Confirm Narrator Is Running

After Narrator starts:

- The currently focused element is announced.
- Keyboard navigation is spoken.
- Accessible roles and states are announced.

Example announcements:

```text
Home link

Search button

Name edit

Selected checkbox
```

---

## 4. Fundamental Commands

### Read the current item

```text
Narrator + Tab
```

Announces the element currently holding keyboard focus. Very useful during testing.

---

### Read the current window title

```text
Narrator + T
```

Useful after page navigation or when opening dialogs.

---

### Read the current time and date

```text
Narrator + F12
```

---

### Show the list of Narrator commands

```text
Narrator + F1
```

---

## 5. Scan Mode

Scan Mode is the primary navigation mode for browsing web pages.

Toggle Scan Mode:

```text
Narrator + Spacebar
```

When Scan Mode is enabled:

- The Up and Down arrow keys move through the page content.
- Single-letter navigation is available.
- Enter or Spacebar activates the current item.
- Navigation behaves similarly to a traditional screen reader.

Always check that Scan Mode is on when testing a web page.

---

## 6. Reading Page Content

### Start reading the document

```text
Narrator + Ctrl + R
```

or

```text
Narrator + Down Arrow
```

Starts continuous reading of the document. Microsoft names this command "Start reading document".

---

### Read from the cursor

```text
Narrator + R
```

---

### Stop reading

```text
Ctrl
```

Immediately stops speech.

---

## 7. Basic Navigation (Scan Mode)

Move to the next text or item:

```text
Down Arrow
```

Move to the previous text or item:

```text
Up Arrow
```

---

## 8. Quick Navigation (Scan Mode)

These commands work only when Scan Mode is enabled.

---

### Headings

Next heading:

```text
H
```

Previous heading:

```text
Shift + H
```

Narrator announces the heading text and its level.

Example:

```text
Heading level 2
Personal Information
```

Checks:

- The heading hierarchy H1–H6 reflects the structure of the page
- No heading level is skipped (good practice)

---

### Navigate by Heading Level

Next Heading Level 1:

```text
1
```

Previous Heading Level 1:

```text
Shift + 1
```

Similarly:

```text
2 / Shift + 2
3 / Shift + 3
4 / Shift + 4
5 / Shift + 5
6 / Shift + 6
```

These commands are useful for quickly reviewing heading hierarchy.

---

### Links

Next link:

```text
K
```

Previous link:

```text
Shift + K
```

Narrator announces whether a link has been visited.

Example:

```text
Visited link
```

or

```text
Link
```

Checks:

- Every link has an accessible name
- The link text is meaningful

---

### Buttons

Next button:

```text
B
```

Previous button:

```text
Shift + B
```

Narrator announces the button name and state when applicable.

Checks:

- The name is announced
- The state is announced

---

### Form Controls

Next form control:

```text
F
```

Previous form control:

```text
Shift + F
```

This navigates through all form controls, not only text fields.

Narrator typically announces:

- Label
- Control type
- Required state
- Current value
- Invalid state (if applicable)

Example:

```text
First Name
Edit
Required
```

Checks:

- The label is read
- The required state is announced
- The invalid state is announced

---

### Combo Boxes

Next combo box:

```text
C
```

Previous combo box:

```text
Shift + C
```

---

### Radio Buttons

Next radio button:

```text
R
```

Previous radio button:

```text
Shift + R
```

---

### Checkboxes

Next checkbox:

```text
X
```

Previous checkbox:

```text
Shift + X
```

---

### Graphics

Next graphic:

```text
G
```

Previous graphic:

```text
Shift + G
```

Useful for reviewing alternative text.

---

### Lists

Next list:

```text
L
```

Previous list:

```text
Shift + L
```

---

### List Items

Next list item:

```text
I
```

Previous list item:

```text
Shift + I
```

---

### Tables

Next table:

```text
T
```

Previous table:

```text
Shift + T
```

---

### Landmarks

Next landmark:

```text
D
```

Previous landmark:

```text
Shift + D
```

Landmark navigation is essential when testing against WCAG. It lets you check the presence of the banner, navigation, main, complementary, contentinfo and search regions.

Examples include:

```text
Banner

Navigation

Main

Search

Content Information
```

---

## 9. Lists of Headings, Links and Landmarks

Open a list of page elements:

```text
Narrator + F5
```

List of landmarks.

```text
Narrator + F6
```

List of headings.

```text
Narrator + F7
```

List of links.

These lists give a quick overview of the page structure and allow direct navigation to an element. They are among the most useful navigation tools for accessibility testing.

---

## 10. Keyboard Focus Navigation

Move focus forward:

```text
Tab
```

Move focus backward:

```text
Shift + Tab
```

To identify the currently focused element after each move:

```text
Narrator + Tab
```

Points to check:

- Logical focus order
- No keyboard trap
- Visible focus

---

## 11. Activating Controls

When the focus is on a button, a link or a checkbox, activate it with:

```text
Enter
```

or

```text
Spacebar
```

depending on the control type.

---

## 12. Testing a Form (Step by Step)

Recommended method.

### Step 1

Navigate with:

```text
Tab
```

Check:

- The focus order
- The consistency of the path through the form

---

### Step 2

On each field, check that Narrator announces:

```text
Label
Field type
Required (if applicable)
Value
```

Expected example:

```text
First Name
Edit
Required
```

---

### Step 3

Trigger the errors (submit empty or invalid values).

Check:

- The error messages are announced
- The invalid states are announced

---

### Step 4

Submit the form.

Check that the focus lands on:

- The main heading of the resulting page
- Or the first relevant element (for example, the first error or the confirmation message)

Never on a random element.

---

## 13. Common Narrator Announcements

During testing, Narrator may announce information such as:

### Heading

```text
Heading level 1
Heading level 2
```

---

### Links

```text
Link

Visited link
```

---

### Buttons

```text
Button
```

---

### Form Controls

```text
Edit

Required

Invalid entry
```

---

### Expandable Controls

```text
Expanded

Collapsed
```

---

### Selection

```text
Selected

Not selected
```

---

### Checkboxes

```text
Checked

Not checked

Mixed
```

---

### Radio Buttons

```text
Selected radio button
```

---

### Landmarks

```text
Banner

Navigation

Main

Search

Content Information
```

---

## 14. Minimum WCAG Checks with Narrator

| Area | Checks | WCAG 2.2 |
|---|---|---|
| Structure | An H1 is present; the heading hierarchy is consistent | 1.3.1 (A), 2.4.6 (AA) |
| Links | Every link has a meaningful name; no isolated "Click here" | 2.4.4 (A) |
| Buttons | Name and state are announced correctly | 4.1.2 (A) |
| Forms | Every field has a label; required fields and errors are announced | 3.3.2, 3.3.1 (A), 4.1.3 (AA) |
| Navigation | Landmarks are present, including the main content | 1.3.1, 2.4.1 (A) |
| Keyboard | Logical focus order; no keyboard trap | 2.4.3, 2.1.2 (A) |

---

## 15. Essential Commands Summary

| Command | Action |
|---------|--------|
| Ctrl + Windows + Enter | Start / Stop Narrator |
| Narrator + Spacebar | Toggle Scan Mode |
| Narrator + Tab | Read current item |
| Narrator + T | Read window title |
| Narrator + F1 | Show the list of Narrator commands |
| Narrator + Ctrl + R (or Narrator + Down Arrow) | Start reading the document |
| Narrator + R | Read from the cursor |
| Ctrl | Stop speech |
| Down Arrow / Up Arrow (Scan Mode) | Next / Previous text or item |
| Tab | Next focusable element |
| Shift + Tab | Previous focusable element |
| H / Shift + H | Next / Previous heading |
| 1–6 | Next heading of specific level |
| Shift + 1–6 | Previous heading of specific level |
| K / Shift + K | Next / Previous link |
| B / Shift + B | Next / Previous button |
| F / Shift + F | Next / Previous form control |
| C / Shift + C | Next / Previous combo box |
| R / Shift + R | Next / Previous radio button |
| X / Shift + X | Next / Previous checkbox |
| G / Shift + G | Next / Previous graphic |
| L / Shift + L | Next / Previous list |
| I / Shift + I | Next / Previous list item |
| T / Shift + T | Next / Previous table |
| D / Shift + D | Next / Previous landmark |
| Narrator + F5 / F6 / F7 | List of landmarks / headings / links |
| Enter | Activate focused control |
| Spacebar | Activate or toggle focused control |

---

## 16. Testing Recommendation

For professional web accessibility audits, use Narrator **in addition to** the most used desktop screen readers, JAWS and NVDA. Narrator is rarely the primary screen reader (0.4% of respondents in the WebAIM Screen Reader User Survey #11), but 36.1% of respondents commonly use it. Testing with Narrator confirms compatibility with the screen reader built into Windows, available on every Windows computer without installation.

---

## Sources

- Microsoft — [Complete guide to Narrator](https://support.microsoft.com/en-us/accessibility/windows/narrator/complete-guide-to-narrator)
- Microsoft — [Appendix B: Narrator keyboard commands and touch gestures](https://support.microsoft.com/help/22806)
- Microsoft — [Chapter 3: Using scan mode](https://support.microsoft.com/help/22809)
- WebAIM — [Screen Reader User Survey #11 Results](https://webaim.org/projects/screenreadersurvey11/) (survey data — not a standard)
