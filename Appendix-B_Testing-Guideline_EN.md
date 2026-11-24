# Appendix B — Guideline for Testing Accessibility

## Introduction

WCAG, while comprehensive, can be complex to interpret for non-specialist teams. This guide simplifies the interpretation of WCAG criteria and helps teams concretely validate the accessibility of web interfaces for **blind users relying on screen readers, low-vision users, color-blind users, users with motor or cognitive impairments, and mobile/zoom users**. It focuses on the essential WCAG 2.2 criteria that directly affect the experience of people using screen readers and other assistive technologies, as well as the visual perception, zoom/responsive, contrast, touch-interaction, readability, and interface-consistency criteria that screen-reader testing alone cannot validate.

Rather than an exhaustive restatement of the WCAG standard, this document takes a **pragmatic approach**: it provides a structured checklist for concretely testing keyboard navigability, semantic structure, forms, dynamic components, critical business journeys, time-based constraints, zoom and reflow behavior, text spacing, color contrast, responsive/orientation behavior, touch and pointer interactions, target size, and interface consistency. Each item is cross-referenced to its corresponding WCAG criterion and level, so teams can return to the official source when needed.

**Target conformance level:** WCAG 2.2 Level AA.

**Note:** This guide does not replace the official WCAG standard — it is a targeted, practical implementation of it. These tests also do not replace a full accessibility audit (see section 4.6 of the lecture material). The full list of WCAG 2.2 success criteria and their levels is in Appendix A.

---

## Checklist by Theme

This checklist is designed to guide accessibility validation step by step, breaking down WCAG 2.2 requirements by major application feature (navigation, forms, interactive components, visual presentation, responsive behavior, etc.).

Each section targets a clear objective (e.g., *"Ensure smooth and logical navigation"*) and lists the specific checks to perform, each directly cross-referenced to its corresponding WCAG criterion.

For each feature area, you will find:

- A list of verifiable actions, phrased simply and directly (e.g., *"Keyboard focus is visible at all times"*).
- The associated WCAG references and levels, for quick return to the official requirements.
- Acceptance criteria at the end of the section, summarizing the minimum expectations to validate conformance (e.g., *"100% of areas are accessible via keyboard"*).

**Goal:** Make the audit fast and reproducible, giving teams a structured framework to test every aspect of the application without requiring deep WCAG expertise.

### 1. General Navigation (including Focus Visibility)

**Objective:** Ensure smooth, logical navigation throughout the application, with a focus indicator that is always clearly visible — including on custom components.

- Keyboard navigation (Tab, Shift+Tab, arrow keys) works correctly **(WCAG 2.1.1, 2.1.2 - A)**
- Tab order follows a logical sequence (top to bottom, left to right) **(WCAG 2.4.3 - A)**
- Main navigation areas are identifiable (header, navigation, main content, footer) **(WCAG 1.3.1 - A)**
- Skip links ("Skip to main content") are present and functional **(WCAG 2.4.1 - A)**
- More than one way is available to locate a page within a set of pages (e.g., search, sitemap, or navigation menu) **(WCAG 2.4.5 - AA)**
- No keyboard trap exists (it is possible to exit every area) **(WCAG 2.1.2 - A)**
- Single-character keyboard shortcuts (a letter, digit or punctuation key alone) can be turned off or remapped, or are active only when the component has focus **(WCAG 2.1.4 - A)**
- Navigation does not depend solely on the mouse **(WCAG 2.1.1 - A)**
- A visible focus indicator is present on every focusable element, including custom-built components **(WCAG 2.4.7 - AA)**
- The focused element is never entirely hidden by other content, such as a sticky header, a cookie banner or a chat widget **(WCAG 2.4.11 - AA)**
- The focus indicator has sufficient contrast to be clearly perceptible **(WCAG 1.4.11 - AA)** — see Theme 13 (Visual Contrasts) for the numeric ratio requirement

**Acceptance criteria:**

- ✅ 100% of areas are accessible via keyboard
- ✅ The tab order contains no inconsistencies
- ✅ Skip links work on every page
- ✅ 100% of focusable elements display a visible focus indicator
- ✅ The focus indicator has sufficient contrast
- ✅ No component removes focus or entirely hides the focused element

---

### 2. Interactive Elements (Buttons, Links, Controls)

**Objective:** Ensure that every interactive element is accessible and understandable.

- All buttons are operable via keyboard (Enter or Space) **(WCAG 2.1.1 - A)**
- Buttons have explicit, descriptive labels **(WCAG 4.1.2 - A, 2.4.6 - AA)**
- Where a component has a visible text label, the accessible name includes that visible text **(WCAG 2.5.3 - A)**
- Links are clearly identifiable and their destination is understandable **(WCAG 2.4.4 - A, 2.4.9 - AAA)**
- Link text is meaningful (avoid "click here", "learn more" without context) **(WCAG 2.4.4 - A)**
- Clickable elements have an appropriate ARIA role only when not already implicit (e.g. `<a>`, `<button>`) **(WCAG 4.1.2 - A)**
- Dropdown menus are keyboard-navigable (arrows, Enter, Escape) **(WCAG 2.1.1 - A)**
- Icon-only elements have text alternatives (`aria-label` or visually-hidden text) **(WCAG 1.1.1, 4.1.2 - A)**
- Toggle buttons clearly indicate their state (on/off) **(WCAG 4.1.2 - A)**
- Disabled elements are identifiable and announced as such **(WCAG 4.1.2 - A)**

**Acceptance criteria:**

- ✅ All critical buttons and links are tested and functional
- ✅ No interactive element is invisible to the screen reader
- ✅ States (enabled, disabled, selected) are correctly announced

---

### 3. Forms and Input Fields

**Objective:** Allow information to be entered clearly and without error.

- All form fields have a label (`<label for='field_id'>`, or `aria-labelledby` / `aria-label` when a visible `<label>` cannot be used) **(WCAG 3.3.2 - A)**, programmatically associated with the field **(WCAG 1.3.1, 4.1.2 - A)**
- Input instructions are announced before or during data entry **(WCAG 3.3.2 - A)**
- Required fields are clearly identified (visually and via `required` or `aria-required`) **(WCAG 3.3.2 - A)**
- Expected formats are communicated (e.g., DD/MM/YYYY, +41 XX XXX XX XX) **(WCAG 3.3.2 - A)**
- Dropdown lists (`<select>`) are accessible and their options readable **(WCAG 4.1.2 - A)**
- Checkboxes and radio buttons have associated labels **(WCAG 3.3.2, 1.3.1 - A)**
- Field groups are logically grouped (`<fieldset>` with `<legend>`) **(WCAG 1.3.1 - A)**
- Fields that collect information about the user (name, email, address, phone…) expose their purpose with the `autocomplete` attribute **(WCAG 1.3.5 - AA)**
- Information already entered in the same process is pre-filled or available for selection, instead of being requested again **(WCAG 3.3.7 - A)**
- Search areas are identifiable (`<search>` element or `role="search"` landmark) **(WCAG 1.3.1 - A)**
- Client-side validation is accessible **(WCAG 3.3.1 - A)**

**Acceptance criteria:**

- ✅ All fields are identifiable and fillable via keyboard
- ✅ Instructions and constraints are announced before data entry
- ✅ No required field lacks an indication

---

### 4. Messages and User Feedback

**Objective:** Clearly inform the user about completed actions and any errors.

- Error messages are readable and associated with the relevant fields **(WCAG 3.3.1 - A, 3.3.3 - AA)**
- Errors are announced via live regions (`role="alert"`) **(WCAG 4.1.3 - AA)**
- Success messages are announced automatically **(WCAG 4.1.3 - AA)**
- Real-time validation is perceptible without being intrusive **(WCAG 3.3.1 - A)**
- Alerts and notifications are clearly announced **(WCAG 4.1.3 - AA)**
- No change of context (new window, page change, focus jump) happens unexpectedly when an element receives focus or when a field value changes, unless the user has been advised beforehand **(WCAG 3.2.1, 3.2.2 - A)**
- Error messages suggest corrections **(WCAG 3.3.3 - AA)**
- Loading/waiting messages are announced **(WCAG 4.1.3 - AA)**

**Acceptance criteria:**

- ✅ All error messages are tested and accessible
- ✅ Important notifications do not go unnoticed
- ✅ Messages do not disappear too quickly **(WCAG 2.2.1 - A)**

---

### 5. Content Structure and Hierarchy (including Page Titles and Consistency)

**Objective:** Organize information logically and navigably, and ensure structural and navigational consistency across the site.

- The heading structure is hierarchical and consistent (H1 → H2 → H3) **(WCAG 1.3.1 - A, 2.4.6 - AA)**
- Each page has a unique, descriptive H1 heading. **[Inference]** The source material linked this requirement to WCAG 2.4.2; however, 2.4.2 formally concerns the page's `<title>` element (see the dedicated bullet below), not the H1. A unique, descriptive H1 supports the same navigational goal as a good practice, but is not itself the literal requirement of 2.4.2.
- Headings accurately reflect the structure of the content **(WCAG 2.4.6 - AA)**
- Lists are marked up semantically (`<ul>`, `<ol>`, `<li>`) and labeled **(WCAG 1.3.1 - A)**
- Data tables have appropriate headers (`<th>`, `scope`) **(WCAG 1.3.1 - A)**
- Complex tables use `id` and `headers` for association **(WCAG 1.3.1 - A)**
- Landmark regions are used correctly (`<main>`, `<header>`, `<footer>`, `<nav>`, `<aside>`, etc.) **(WCAG 1.3.1 - A)**
- Content follows a logical reading order **(WCAG 1.3.2 - A)**
- Quotations are marked up with `<blockquote>` **(WCAG 1.3.1 - A)**
- Definitions use `<dl>`, `<dt>`, `<dd>` **(WCAG 1.3.1 - A)**
- Each page has a descriptive `<title>` element **(WCAG 2.4.2 - A)**
- Navigation menus are positioned consistently across pages **(WCAG 3.2.3 - AA)**
- The same functionality carries the same label everywhere it appears **(WCAG 3.2.4 - AA)**
- Help mechanisms repeated on several pages (contact details, contact form, chat, FAQ) appear in the same relative order **(WCAG 3.2.6 - A)**

**Acceptance criteria:**

- ✅ Heading-based navigation allows the page structure to be understood
- ✅ No heading level is skipped (⚠️ this is good practice, not itself a WCAG criterion)
- ✅ Data tables are understandable
- ✅ 100% of pages have a descriptive `<title>`
- ✅ Navigation and help are consistent across the entire site
- ✅ No label contradicts itself for the same action

---

### 6. Multimedia Content

**Objective:** Make visual and audio content accessible.

- All informative images have relevant text alternatives (`alt`) **(WCAG 1.1.1 - A)**
- Decorative images have an empty `alt=""` attribute or `role="presentation"` **(WCAG 1.1.1 - A)**
- Complex images (charts, diagrams) have detailed descriptions **(WCAG 1.1.1 - A)**
- Prerecorded videos have synchronized captions **(WCAG 1.2.2 - A)**
- Live videos have synchronized captions **(WCAG 1.2.4 - AA)**
- Prerecorded videos have an audio description or a text transcript **(WCAG 1.2.3 - A)**
- Prerecorded videos have an audio description of important visual information **(WCAG 1.2.5 - AA)**
- Audio content has transcripts **(WCAG 1.2.1 - A)**
- Animations can be paused or disabled **(WCAG 2.2.2 - A)**
- Interactive graphics have accessible alternatives **(WCAG 1.1.1 - A)**
- Infographics have complete text descriptions **(WCAG 1.1.1 - A)**
- CAPTCHAs have audio or logic-based alternatives **(WCAG 1.1.1 - A)**

**Acceptance criteria:**

- ✅ No information depends solely on visual content
- ✅ All critical videos have captions
- ✅ Text alternatives are relevant and sufficient

---

### 7. Dynamic Content and Advanced Interactions

**Objective:** Handle dynamic updates and complex interactions accessibly.

- Dynamic content updates are announced (`aria-live`, `role="status"`) **(WCAG 4.1.3 - AA)**
- Modals/popups are identified (`role="dialog"` or `role="alertdialog"`) **(WCAG 4.1.2 - A)**
- Focus is automatically moved into modals when they open **(WCAG 2.4.3 - A)**
- Focus returns to the triggering element when modals close **(WCAG 2.4.3 - A)**
- Modals can be closed via keyboard (Escape) **(WCAG 2.1.1, 2.1.2 - A)**
- Accordions indicate their state (open/closed) via `aria-expanded` **(WCAG 4.1.2 - A)**
- Tabs are keyboard-navigable (left/right arrows) **(WCAG 2.1.1 - A)**
- Tabs indicate the active tab via `aria-selected` **(WCAG 4.1.2 - A)**
- Carousels can be paused **(WCAG 2.2.2 - A)**
- Carousels are keyboard-controllable **(WCAG 2.1.1 - A)**
- Tooltips are accessible via keyboard and focus, can be dismissed and stay visible while hovered **(WCAG 1.4.13 - AA)**
- AJAX-loaded content is announced **(WCAG 4.1.3 - AA)**

**Acceptance criteria:**

- ✅ All modals are identified and focus is correctly managed
- ✅ Critical updates are announced automatically
- ✅ No dynamic content is invisible to the screen reader

---

### 8. Readability and Comprehension

**Objective:** Ensure content is clear and understandable, independent of visual or language-based assumptions.

- All visual information has a text equivalent **(WCAG 1.1.1 - A)**
- The page's main language is correctly defined in code **(WCAG 3.1.1 - A)**
- The language used is clear and appropriate for the target audience **(WCAG 3.1.5 - AAA)**
- Abbreviations and acronyms are explained (`<abbr title="">`) **(WCAG 3.1.4 - AAA)**
- Instructions do not rely solely on visual characteristics (color, shape, position) **(WCAG 1.3.3 - A, 1.4.1 - A)**
- Language changes within the content are indicated in code (`lang` attribute) **(WCAG 3.1.2 - AA)**
- Technical terms are defined or explained **(WCAG 3.1.3 - AAA)**
- Complex content is accompanied by explanations **(WCAG 3.1.5 - AAA)**

> **Note:** Criteria specific to color contrast (1.4.3, 1.4.11), zoom and reflow (1.4.10), adjustable text size (1.4.4), and text spacing (1.4.12) are not duplicated here — see the dedicated **Zoom and Resizing**, **Text Spacing**, and **Visual Contrasts** themes below for their full verification steps and acceptance criteria.

**Acceptance criteria:**

- ✅ No instruction depends solely on color or position
- ✅ Critical abbreviations are explained
- ✅ Content is understandable without relying on visual perception
- ✅ The page language and any in-content language changes are correctly declared in code

---

### 9. Critical Functionality

**Objective:** Validate that essential user journeys are fully accessible.

- The login/authentication process is accessible
- Login does not require a cognitive function test (memorizing or transcribing a password, solving a puzzle) unless an alternative is offered — for example, password managers and copy-paste are not blocked **(WCAG 3.3.8 - AA)**
- Registration / account creation is achievable
- Important transactions can be completed (purchase, payment, submission)
- Submissions with legal or financial consequences can be reviewed, corrected, or confirmed before being finalized **(WCAG 3.3.4 - AA)**
- Search is usable and results are accessible
- Filters and sorting are keyboard-accessible
- Pagination is keyboard-navigable
- File download actions are achievable
- File upload actions are accessible
- Dashboards and statistics are understandable
- Logout is accessible

Apart from the two bullets referenced above, this section is not itself a WCAG criterion. It verifies the operational conformance of the A and AA criteria across business journeys — primarily the keyboard-accessibility criteria 2.1.1 and 2.1.2, and the complete-process conformance requirement (WCAG 2.2, section 5.2.3).

**Acceptance criteria:**

- ✅ All identified critical journeys are tested end-to-end
- ✅ No journey presents a major blocking issue
- ✅ Core business functionality is validated

---

### 10. Time Management and Temporal Constraints

**Objective:** Prevent time limits from blocking task completion.

- Time limits can be disabled or adjusted by the user **(WCAG 2.2.1 - A)**
- Sessions can be extended or saved before expiry **(WCAG 2.2.1 - A)**
- Moving or animated content can be paused or disabled **(WCAG 2.2.2 - A)**
- Automatic updates (e.g., page refresh) can be controlled by the user **(WCAG 2.2.4 - AAA)**
- Interruptions (e.g., pop-ups) can be postponed or disabled **(WCAG 2.2.4 - AAA)**
- Time allowed for user actions (e.g., form submission) is sufficiently long or adjustable **(WCAG 2.2.1 - A)**

**Acceptance criteria:**

- ✅ No time limit blocks task completion
- ✅ Expiry warnings are accessible
- ✅ Problematic animations can be controlled

---

### 11. Zoom and Resizing

**Objective:** Ensure usability at high zoom levels and small viewport widths.

- Content is usable at 200% zoom **(WCAG 1.4.4 - AA)**
- Content is usable at 400% zoom or at a 320px viewport width **(WCAG 1.4.10 - AA)**
- No horizontal scrolling is required to read the main content **(WCAG 1.4.10 - AA)**
- No text is truncated or overlapping
- Wide tables have an accessible alternative

**Acceptance criteria:**

- ✅ 100% of content and functionality remain accessible at 200%
- ✅ At 400%, no reading requires horizontal scrolling
- ✅ No critical component becomes unusable
- ✅ No content is hidden or cut off

---

### 12. Text Spacing

**Objective:** Ensure robustness against readability adaptations.

Manual application of the following values:

- `line-height: 1.5`
- `letter-spacing: 0.12em`
- `word-spacing: 0.16em`
- `paragraph spacing: 2em`

Checks **(WCAG 1.4.12 - AA)**:

- No overlap occurs
- No content is lost
- Components remain usable

**Acceptance criteria:**

- ✅ The application remains fully functional
- ✅ No text overlaps
- ✅ No additional horizontal scroll is generated

---

### 13. Visual Contrasts

**Objective:** Ensure the perceivability of content and components.

- Normal text contrast ≥ 4.5:1 **(WCAG 1.4.3 - AA)**
- Large text contrast ≥ 3:1 **(WCAG 1.4.3 - AA)**
- UI component contrast (field borders, informative icons, buttons) ≥ 3:1 **(WCAG 1.4.11 - AA)**
- Focus indicators meet the same non-text contrast ratio as other UI components **(WCAG 1.4.11 - AA)** — see Theme 1 for the requirement that focus be visible at all times
- States (error, active, selected) are not conveyed by color alone **(WCAG 1.4.1 - A)**

**Acceptance criteria:**

- ✅ 100% of text meets the required contrast ratio
- ✅ 100% of interactive components meet the required contrast ratio
- ✅ No state is conveyed by color alone
- ✅ Focus is perceptible without ambiguity

---

### 14. Responsive Design and Orientation

**Objective:** Ensure mobile adaptability.

- Works correctly in portrait orientation **(WCAG 1.3.4 - AA)**
- Works correctly in landscape orientation **(WCAG 1.3.4 - AA)**
- No interaction is blocked based on orientation **(WCAG 1.3.4 - AA)**

**Acceptance criteria:**

- ✅ All critical functionality is accessible in both orientations
- ✅ No essential content is hidden

---

### 15. Touch and Pointer Interactions

**Objective:** Ensure accessibility for touch and motor-impaired users.

- Complex gestures (multipoint or path-based) have a simple single-pointer alternative **(WCAG 2.5.1 - A)**
- Actions are not triggered solely on "touch down" **(WCAG 2.5.2 - A)**
- Critical actions can be cancelled **(WCAG 2.5.2 - A)**
- Every drag-and-drop action has a single-pointer alternative without dragging (e.g., buttons or a menu) **(WCAG 2.5.7 - AA)**

**Acceptance criteria:**

- ✅ 100% of complex gestures and dragging movements have an alternative
- ✅ No irreversible action is triggered accidentally
- ✅ Critical actions are confirmable

---

### 16. Target Size

**Objective:** Reduce activation errors.

- Targets measure at least 24 × 24 CSS px, or are spaced so that a 24 px circle centred on each target does not overlap another target **(WCAG 2.5.8 - AA)**
- Critical targets measure at least 44 × 44 CSS px **(WCAG 2.5.5 - AAA)**
- Nearby elements do not cause interaction errors **(WCAG 2.5.8 - AA)**

**Acceptance criteria:**

- ✅ 100% of targets meet the minimum target size (24 × 24 CSS px, AA)
- ✅ No accidental clicks observed during testing

---

### 17. Name, Role, Value — General Principle for Custom Components

**Objective:** Ensure the robustness of custom components beyond what is already itemized elsewhere in this guide.

For custom JS / non-native components:

- The component exposes a correct accessible name
- The role is correct
- The value/state is exposed
- State changes are detectable

**Checks (WCAG 4.1.2 - A):**

- Custom components expose an accessible name
- Roles are appropriate
- States are correctly exposed
- State changes are detectable

**Acceptance criteria:**

- ✅ 100% of interactive components expose Name/Role/Value
- ✅ No critical component is missing an accessible name
- ✅ Dynamic states are correctly updated

> **Note:** Many specific instances of this principle are already verified individually elsewhere in this guide — e.g., toggle-button state and disabled-state announcement (Theme 2), `<select>` roles (Theme 3), and dialog/accordion/tab state exposure (Theme 7). This theme provides the general verification approach for any custom component not already covered by those specific checks.

---

## Checklist by WCAG Conformance Level

This section organizes and summarizes the WCAG 2.2 requirements into three distinct categories:

- **Fundamental criteria**, indispensable for eliminating major blocking issues: Level A, plus a few Level AA criteria judged critical;
- **Legal criteria**, corresponding to Level AA, the level required by the legal frameworks;
- **Excellence criteria**, aligned with Level AAA, plus good practices that are not WCAG requirements, to improve user comfort.

Each category defines a conformance tier, from minimal requirements that prevent access blockages up to best practices for optimal accessibility.

For each criterion, a detailed table presents its precise label, a clear description of the requirement and its impact on user experience, the WCAG success criterion and level, a step-by-step verification method, and the relevant Xray test reference where one already exists. **Rows were sorted by WCAG level: each row keeps its original Xray test case and step, so one Xray test case can appear in more than one table. Rows without an Xray test case are left blank and are intended to be filled in once new test cases are created.**

The goal is to give teams a unified reference base for understanding the expectations associated with each conformance level, prioritizing fixes based on project constraints, and objectively measuring accessibility progress.

### Fundamental Criteria (Level A — Eliminating Blockers)

This section groups the minimum WCAG Level A requirements, along with certain Level AA criteria judged critical for preventing access **blockages** (marked **AA** in the WCAG column). These criteria guarantee basic access to information and functionality, without which some users with disabilities could simply not use the service.

| Criterion | Description | WCAG | How to verify | Xray Test | Step(s) |
| --- | --- | --- | --- | --- | --- |
| **Accessible critical functionality** | 100% of essential journeys (login, transactions, search, enabling/disabling services) are completable by keyboard with a screen reader | 2.1.1, 2.1.2 (A) | Test all major business journeys end-to-end without a mouse | AFCXRAY-12125 | Step 1 |
| **Complete keyboard navigation** | All areas and features are accessible without a mouse (Tab, Shift+Tab, Enter, Space, arrows) | 2.1.1 (A) | Browse the entire application using only the keyboard | AFCXRAY-12125 | Step 2 |
| **Focus management** | Keyboard focus follows a logical order, with no jumps or traps, and is always visible | 2.4.3, 2.1.2 (A); 2.4.7 (AA) | Visually check focus and confirm every area can be exited | AFCXRAY-12125 | Step 3 |
| **Accessible error messages** | All error messages are readable by the screen reader, announced automatically, and associated with the relevant fields | 3.3.1 (A); 4.1.3 (AA) | Deliberately trigger errors and verify their announcement | AFCXRAY-12125 | Step 4 |
| **Identifiable forms** | All fields have explicit labels (`<label for='field_id'>`, or `aria-labelledby` / `aria-label`) and required fields are identified | 3.3.2, 1.3.1, 4.1.2 (A) | Test all forms with the screen reader | AFCXRAY-12125 | Step 5 |
| **Identified modals/popups** | Modal windows are announced as such (`role="dialog"`), with focus managed on open/close | 4.1.2, 2.4.3 (A) | Open all modals and verify the announcement and focus handling | AFCXRAY-12125 | Step 6 |
| **Text alternatives** | All informative images have relevant `alt` attributes; decorative images are hidden | 1.1.1 (A) | Browse the application and listen to all image descriptions | AFCXRAY-12125 | Step 7 |
| **Consistent heading structure** | The H1–H6 hierarchy reflects the content structure on every page. No skipped levels and one H1 per page are good practices | 1.3.1 (A); 2.4.6 (AA) | Use the screen reader's heading navigation on every page | AFCXRAY-12125 | Step 8 |
| **Action context** | Actions (buttons, links) provide enough context to understand their effect without visual information | 2.4.4, 4.1.2 (A) | Test all buttons/links and verify their function is clear | AFCXRAY-12125 | Step 9 |
| **Logical presentation order** | Information is presented in an order that makes sense (context before details, status before contact info) | 1.3.2 (A) | Listen to the full announcement of each section and check for consistency | AFCXRAY-12126 | Step 1 |
| **Landmark regions** | Correct use of `<main>`, `<header>`, `<footer>`, `<nav>`, or of `role="main"`, `role="navigation"`, `role="search"`, etc. when the native elements are not used | 1.3.1 (A) | Check the landmark structure with developer tools and the screen reader's landmark navigation | AFCXRAY-12126 | Step 3 |
| **Component states** | States (open/closed, checked/unchecked, enabled/disabled) are correctly announced | 4.1.2 (A) | Test all interactive components and their various states | AFCXRAY-12126 | Step 5 |
| **Input instructions** | Expected formats and constraints are announced before or during input | 3.3.2 (A) | Test all fields with constraints (date, phone, email, etc.) | AFCXRAY-12126 | Step 6 |
| **Focus return after actions** | After an action (closing a modal, submitting a form), focus returns to a logical location | 2.4.3 (A) | Perform actions and check where focus lands | AFCXRAY-12126 | Step 7 |
| **Data tables** | Tables have appropriate headers and are understandable to the screen reader | 1.3.1 (A) | Browse all tables in the screen reader's table mode | AFCXRAY-12126 | Step 8 |
| **Skip links** | A "Skip to main content" link (or landmarks and headings) allows repeated blocks to be bypassed | 2.4.1 (A) | Press Tab immediately upon arriving on the page | AFCXRAY-12127 | Step 1 |
| **Character key shortcuts** | Single-character shortcuts can be turned off or remapped, or are active only on focus | 2.1.4 (A) | Test the shortcuts and verify they can be turned off or remapped | AFCXRAY-12127 | Step 2 |
| **Video captions** | Synchronized captions are present for all prerecorded video content | 1.2.2 (A) | Watch all videos with captions enabled | AFCXRAY-12127 | Step 3 |
| **Audio transcripts** | Prerecorded audio content has available text transcripts | 1.2.1 (A) | Check transcript availability | AFCXRAY-12127 | Step 4 |
| **Animation control** | Ability to pause, stop, or hide automatic animations | 2.2.2 (A) | Test carousels and automatic animations | AFCXRAY-12127 | Step 5 |
| **Detailed descriptions** | Complex graphics have long descriptions (`aria-describedby` or links to descriptions) | 1.1.1 (A) | Browse all charts and diagrams | AFCXRAY-12127 | Step 6 |
| **Descriptive page titles** | Every page has a descriptive `<title>` element | 2.4.2 (A) | Inspect the DOM `<title>` element on each page | | |
| **Use of color** | Information and state are not conveyed by color alone | 1.4.1 (A) | Perform a visual inspection of states and instructions | | |
| **Pointer gestures** | Complex gestures have a simple single-pointer alternative | 2.5.1 (A) | Perform a touch-based test of all gestures | | |
| **Pointer cancellation** | Critical actions can be cancelled and are not triggered solely on "touch down" | 2.5.2 (A) | Test with mouse and touch input | | |
| **Name/Role/Value** | Custom components expose a correct accessible name, role, and value/state via the DOM | 4.1.2 (A) | Inspect custom components' DOM/ARIA attributes with browser DevTools | | |
| **Label in Name** | Where a component has a visible text label, the accessible name programmatically includes that visible text | 2.5.3 (A) | Compare each component's visible label text against its computed accessible name in DevTools | | |
| **Consistent help** | Help mechanisms repeated on several pages appear in the same relative order | 3.2.6 (A) | Walk through several pages and compare the position of the help mechanisms | | |
| **Redundant entry** | Information already entered in the same process is not requested again, or is pre-filled or selectable | 3.3.7 (A) | Go through multi-step processes and note any data requested twice | | |
| **Reflow at 400% zoom** | Content remains usable at 400% zoom or at a 320px viewport width, with no horizontal scrolling needed to read the main content | 1.4.10 (AA) | Set zoom to 400% (or viewport to 320px) and confirm no horizontal scroll is needed and no content is lost | | |
| **Text and non-text contrast** | Text and UI-component contrast ratios meet WCAG thresholds — 4.5:1 normal text, 3:1 large text/UI components | 1.4.3, 1.4.11 (AA) | Measure contrast ratios with a contrast-checking tool | | |
| **Focus visible** | A focus indicator is always visible and sufficiently contrasted on every focusable element | 2.4.7, 1.4.11 (AA) | Navigate the entire interface by keyboard and confirm the indicator is always visible | | |
| **Resize text to 200%** | Content remains usable and no content is lost when zoomed to 200% | 1.4.4 (AA) | Set browser zoom to 200% and verify nothing is lost or broken | | |
| **Text spacing** | Applying increased line-height, letter-spacing, word-spacing, and paragraph-spacing values causes no overlap or content loss | 1.4.12 (AA) | Apply the specified spacing values via DevTools CSS and inspect for overlap | | |

---

### Legal Criteria (Level AA — Required Conformance)

This section summarizes the Level AA requirements, which constitute the legal reference level for digital accessibility (EN 301 549 for the EU directives, RGAA in France, eCH-0059 in Switzerland). Their application is required to ensure regulatory compliance and a fluid, autonomous user experience for people with disabilities. Conformance at Level AA also requires all the Level A criteria of the previous table.

These criteria go beyond the basic requirements of Level A by covering essential aspects such as consistent navigation, input purpose, status messages, focus visibility and target size.

| Criterion | Description | WCAG | How to verify | Xray Test | Step(s) |
| --- | --- | --- | --- | --- | --- |
| **Dynamic announcements** | Content updates are announced via `aria-live` or `role="alert"` without interrupting reading or moving the focus | 4.1.3 (AA) | Trigger updates and verify they are announced | AFCXRAY-12126 | Step 4 |
| **Error prevention (legal, financial, data)** | For submissions with legal or financial consequences, the user can reverse, check, or confirm the submission before it is finalized | 3.3.4 (AA) | Trigger a legal/financial/data submission and verify a review, correction, or confirmation step is offered before finalization | | |
| **Orientation** | The interface works correctly in both portrait and landscape orientation | 1.3.4 (AA) | Test on a mobile device or simulator in both orientations | | |
| **Consistent navigation** | Navigation menus are positioned consistently across pages | 3.2.3 (AA) | Walk through multiple pages and compare menu placement | | |
| **Multiple ways to locate content** | More than one way is available to locate a page within a set of pages, e.g. search plus a sitemap or navigation menu | 2.4.5 (AA) | Verify the presence of at least two independent wayfinding methods (search, sitemap, menu, breadcrumbs) | | |
| **Consistent identification** | The same functionality carries the same label everywhere it appears | 3.2.4 (AA) | Check UI labels across equivalent components | | |
| **Identify input purpose** | Fields collecting information about the user expose their purpose with `autocomplete` | 1.3.5 (AA) | Inspect the `autocomplete` values of personal-data fields in DevTools | | |
| **Focus not obscured** | The focused element is never entirely hidden by sticky headers, banners or overlays | 2.4.11 (AA) | Tab through the page with sticky elements and banners displayed | | |
| **Dragging movements** | Every drag-and-drop action can also be done with a single pointer without dragging | 2.5.7 (AA) | Identify every drag interaction and look for a click/tap alternative | | |
| **Target size (minimum)** | Pointer targets measure at least 24 × 24 CSS px or are sufficiently spaced | 2.5.8 (AA) | Measure small targets (icons, links in lists) in DevTools | | |
| **Accessible authentication** | Login does not rely on a cognitive function test without an alternative; password managers and copy-paste work | 3.3.8 (AA) | Log in with a password manager and with copy-paste | | |

---

### Excellence Criteria (Level AAA and Good Practices — Optimization)

This section presents Level AAA requirements and good practices that are not WCAG requirements, which aim to provide optimal accessibility and an exceptional user experience. Unlike Levels A and AA, these criteria are not imposed by regulation, but their implementation is strongly recommended to exceed legal standards and meet the most demanding needs.

Although implementing them can represent a technical or organizational challenge, these criteria achieve a remarkable level of inclusion, guaranteeing maximum usability comfort for everyone, including users with specific or complex needs. They mark a proactive commitment to exemplary accessibility.

| Criterion | Description | WCAG | How to verify | Xray Test | Step(s) |
| --- | --- | --- | --- | --- | --- |
| **Progress indicators** | Multi-step processes clearly indicate the current step | 2.4.8 (AAA) | Browse workflows and verify progress announcement | AFCXRAY-12127 | Step 7 |
| **Contextual help** | Accessible help and tooltips are available for complex features | 3.3.5 (AAA) | Test the accessibility of tooltips and help bubbles | AFCXRAY-12127 | Step 8 |
| **Target size (enhanced)** | Interactive targets measure at least 44 × 44 CSS px | 2.5.5 (AAA) | Inspect critical interactive elements | | |
| **General readability** | The overall interface is clear and easy to read | 3.1.5 (AAA, related) | Perform a general visual review | | |
| **External links identified** | Links that open a new tab or external site are announced as such | — (good practice, not a WCAG requirement) | Test all links and verify the context is clear | AFCXRAY-12126 | Step 2 |

---

## Conformance Levels

A reminder of the WCAG conformance levels.

### 1. Level A (Minimal)

Level A is the minimum WCAG conformance level. All Level A criteria must be validated 100% to reach this level. If even a single Level A criterion is not met, the site is not Level A conformant.

- **Example:** If 30 out of 31 Level A criteria are validated, the site is not conformant at Level A.
- **Consequence (author's recommendation):** Not fit for production (risk of blocking certain users).

### 2. Level AA (Target)

To reach Level AA, all Level A criteria AND all Level AA criteria must be validated 100%. This is the level required by the legal frameworks (EN 301 549 for the EU directives, RGAA in France, eCH-0059 in Switzerland).

- **Example:** If all Level A criteria are validated but a single AA criterion is missing, the site is not Level AA conformant.
- **Consequence (author's recommendation):** Fit for production only if 100% A + 100% AA.

### 3. Level AAA (Excellence)

To reach Level AAA, all A, AA, and AAA criteria must be validated 100%. This level is rare and difficult to achieve across all content: WCAG does not recommend requiring it as a general policy for entire sites.

- **Example:** Even if a single AAA criterion is missing, the site is not Level AAA conformant.
- **Consequence (author's recommendation):** Accessibility excellence (optional, but recommended criterion by criterion where the content allows it).

---

## Tools and Prerequisites

### Recommended screen readers

- **NVDA** (Windows – free)
- **JAWS** (Windows – paid)
- **VoiceOver** (macOS/iOS – built-in)
- **TalkBack** (Android – built-in)
- **Orca** (Linux – free)

### Compatible browsers

- Chrome / Edge
- Firefox
- Safari (for VoiceOver)

### Other recommended tools

- Browser DevTools (for modifying CSS)
- A contrast-checking tool (WCAG Contrast Checker, axe, WAVE, SilkTide)
- Browser zoom (200% and 400%)
- A mobile / responsive simulator
- Keyboard-only testing

### Required skills

- Basic knowledge of screen readers
- Proficiency with keyboard-only navigation
- Understanding of WCAG and ARIA standards, including criteria 1.4.x, 2.4.x, 2.5.x, 3.2.x, and 4.1.2
- Ability to test an interface without a screen reader

---

## Resources and References

### Standards and guidelines

- [WCAG 2.2 Quick Reference (How to Meet WCAG)](https://www.w3.org/WAI/WCAG22/quickref/)
- [RGAA - Référentiel Général d'Amélioration de l'Accessibilité](https://accessibilite.numerique.gouv.fr/)
- [ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/)
- [AcceDe Web - Accessibility notices](https://www.accede-web.com/)

### Validation tools

- **WAVE** (Web Accessibility Evaluation Tool)
- **axe DevTools** (Chrome/Firefox browser extension)
- **ARIA DevTools** (Chrome extension)
- **Lighthouse** (built-in Chrome audit)
- **Pa11y** (command-line tool)
- **Assistant RGAA** (extension for testing RGAA conformance)
- **Windows Narrator** (Windows default screen reader)

### Screen reader documentation

- [NVDA User Guide](https://www.nvaccess.org/files/nvda/documentation/userGuide.html)
- [JAWS Documentation](https://www.freedomscientific.com/training/jaws/)
- [VoiceOver Guide](https://support.apple.com/guide/voiceover/welcome/mac)
- [Complete guide to Narrator | Microsoft Support](https://support.microsoft.com/en-us/accessibility/windows/narrator/complete-guide-to-narrator)

### French-language resources

- [AcceDe Web - Resources and tools](https://www.accede-web.com/notices/)
- [ARIA en français - MDN](https://developer.mozilla.org/fr/docs/Web/Accessibility/ARIA)
- [Blog Access42](https://access42.net/blog)
- [Règles pour l'accessibilité des contenus Web (WCAG) 2.2 — W3C authorised French translation](https://www.w3.org/Translations/WCAG22-fr-20260922/)
