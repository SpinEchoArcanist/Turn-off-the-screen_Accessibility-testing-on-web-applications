# Appendix B — Guideline for Testing Accessibility

## Introduction

WCAG, while comprehensive, can be complex to interpret for non-specialist teams. This guide simplifies the interpretation of WCAG criteria and helps teams concretely validate the accessibility of web interfaces for **blind users relying on screen readers, low-vision users, color-blind users, users with motor or cognitive impairments, and mobile/zoom users**. It focuses on the essential WCAG 2.2 criteria that directly affect the experience of people using screen readers and other assistive technologies, as well as the visual perception, zoom/responsive, contrast, touch-interaction, readability, and interface-consistency criteria that screen-reader testing alone cannot validate.

Rather than an exhaustive restatement of the WCAG standard, this document takes a **pragmatic approach**: it provides a structured checklist for concretely testing keyboard navigability, semantic structure, forms, dynamic components, critical business journeys, time-based constraints, zoom and reflow behavior, text spacing, color contrast, responsive/orientation behavior, touch and pointer interactions, target size, and interface consistency. Each item is cross-referenced to its corresponding WCAG criterion and level, so teams can return to the official source when needed.

**Target conformance level:** WCAG 2.2 Level AA.

**Note:** This guide does not replace the official WCAG standard — it is a targeted, practical implementation of it. These tests also do not replace a full accessibility audit (see section 4.6 of the lecture material). The full list of WCAG 2.2 success criteria and their levels is in Appendix A.

---

## Checklist by Theme

This checklist is designed to guide accessibility validation step by step, breaking down WCAG 2.2 requirements by major application feature (navigation, forms, interactive components, visual presentation, responsive behavior, etc.).

Each section targets a clear objective (e.g., *"Ensure smooth and logical navigation"*) and lists the specific checks to perform, each directly cross-referenced to its corresponding WCAG criterion. Checks marked **good practice** or **APG** (ARIA Authoring Practices Guide) are recommended conventions, not WCAG requirements.

For each feature area, you will find:

- A list of verifiable actions, phrased simply and directly (e.g., *"Keyboard focus is visible at all times"*).
- The associated WCAG references and levels, for quick return to the official requirements.
- Acceptance criteria at the end of the section, summarizing the minimum expectations to validate conformance (e.g., *"100% of areas are accessible via keyboard"*).

**Goal:** Make the audit fast and reproducible, giving teams a structured framework to test every aspect of the application without requiring deep WCAG expertise.

### 1. General Navigation (including Focus Visibility)

**Objective:** Ensure smooth, logical navigation throughout the application, with a focus indicator that is always clearly visible — including on custom components.

- Keyboard navigation (Tab, Shift+Tab, arrow keys) works correctly **(WCAG 2.1.1, 2.1.2 - A)**
- Tab order follows a logical sequence that preserves meaning and operability (usually top to bottom, left to right) **(WCAG 2.4.3 - A)**
- Main navigation areas are identifiable (header, navigation, main content, footer) **(WCAG 1.3.1 - A)**
- Blocks of content repeated on several pages can be bypassed: a "Skip to main content" link, or landmarks and headings **(WCAG 2.4.1 - A)**
- More than one way is available to locate a page within a set of pages (e.g., search, sitemap, or navigation menu), except for pages that are a step in, or the result of, a process **(WCAG 2.4.5 - AA)**
- No keyboard trap exists (it is possible to exit every area) **(WCAG 2.1.2 - A)**
- Single-character keyboard shortcuts (a letter, digit or punctuation key alone) can be turned off or remapped, or are active only when the component has focus **(WCAG 2.1.4 - A)**
- Navigation does not depend solely on the mouse **(WCAG 2.1.1 - A)**
- A visible focus indicator is present on every focusable element, including custom-built components **(WCAG 2.4.7 - AA)**
- The focus indicator is never removed by CSS (e.g., `outline: none` without a visible replacement) **(WCAG 2.4.7 - AA)**
- The focused element is never entirely hidden by other content, such as a sticky header, a cookie banner or a chat widget **(WCAG 2.4.11 - AA)**
- The focus indicator has sufficient contrast against the adjacent background to be clearly perceptible **(WCAG 1.4.11 - AA)** — see Theme 13 (Visual Contrasts) for the numeric ratio requirement

**Acceptance criteria:**

- ✅ 100% of areas are accessible via keyboard
- ✅ The tab order contains no inconsistencies
- ✅ The bypass mechanism (skip link, or landmarks and headings) works on every page
- ✅ 100% of focusable elements display a visible focus indicator
- ✅ The focus indicator has sufficient contrast
- ✅ No component removes focus or entirely hides the focused element

---

### 2. Interactive Elements (Buttons, Links, Controls)

**Objective:** Ensure that every interactive element is accessible and understandable.

- All buttons are operable via keyboard (native buttons respond to both Enter and Space) **(WCAG 2.1.1 - A)**
- Buttons have explicit, descriptive labels **(WCAG 4.1.2 - A, 2.4.6 - AA)**
- Where a component has a visible text label, the accessible name includes that visible text **(WCAG 2.5.3 - A)**
- The purpose of each link can be determined from its text or its context **(WCAG 2.4.4 - A)**, ideally from the link text alone **(WCAG 2.4.9 - AAA)**
- Link text is meaningful (avoid "click here", "learn more" without context) **(WCAG 2.4.4 - A)**
- Clickable elements have an appropriate ARIA role only when not already implicit (e.g. `<a>`, `<button>`) **(WCAG 4.1.2 - A)**
- Dropdown menus are operable with the keyboard **(WCAG 2.1.1 - A)**; the expected keys (arrows, Enter, Escape) follow the APG menu patterns
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

- All form fields have a visible label or instructions **(WCAG 3.3.2 - A)**, programmatically associated with the field (`<label for='field_id'>`, or `aria-labelledby`) **(WCAG 1.3.1, 4.1.2 - A)**. An `aria-label` gives the field an accessible name **(WCAG 4.1.2 - A)**, but it is not visible: on its own, it does not meet 3.3.2
- Input instructions are visible, and announced before or during data entry **(WCAG 3.3.2 - A)**
- Required fields are clearly identified, visually and in code (`required` or `aria-required`) **(WCAG 3.3.2, 1.3.1 - A)**
- Expected formats are communicated (e.g., DD/MM/YYYY, +41 XX XXX XX XX) **(WCAG 3.3.2 - A)**
- Dropdown lists (`<select>`) are accessible and their options readable **(WCAG 4.1.2 - A)**
- Checkboxes and radio buttons have associated labels **(WCAG 3.3.2, 1.3.1 - A)**
- Field groups are logically grouped (`<fieldset>` with `<legend>`) **(WCAG 1.3.1 - A)**
- Fields that collect information about the user (name, email, address, phone…) expose their purpose with the `autocomplete` attribute **(WCAG 1.3.5 - AA)**
- Information already entered in the same process is pre-filled or available for selection, instead of being requested again — except where re-entering it is essential, required for security, or the information is no longer valid **(WCAG 3.3.7 - A)**
- Search areas are identifiable (`<search>` element or `role="search"` landmark) **(WCAG 1.3.1 - A)**
- Errors detected by client-side validation are identified and described in text **(WCAG 3.3.1 - A)**

**Acceptance criteria:**

- ✅ All fields are identifiable and fillable via keyboard
- ✅ Instructions and constraints are visible and announced before data entry
- ✅ No required field lacks an indication

---

### 4. Messages and User Feedback

**Objective:** Clearly inform the user about completed actions and any errors.

- Automatically detected input errors identify the field in error and describe the error in text, not only with color or an icon **(WCAG 3.3.1 - A)**
- Error messages that appear without moving the focus are announced via live regions (`role="alert"`) **(WCAG 4.1.3 - AA)**. When the focus is moved to the error message or to an error summary, this is a change of context, not a status message
- Success messages that appear without moving the focus are announced automatically **(WCAG 4.1.3 - AA)**
- Real-time validation is perceptible without being intrusive **(WCAG 3.3.1 - A)**
- Alerts and notifications that do not take the focus are clearly announced **(WCAG 4.1.3 - AA)**
- No change of context (new window, page change, focus jump) happens when an element receives focus, and none happens when a field value changes unless the user has been advised beforehand **(WCAG 3.2.1, 3.2.2 - A)**
- Error messages suggest corrections when they are known, unless this would jeopardize security or the purpose of the content **(WCAG 3.3.3 - AA)**
- Loading/waiting messages are announced **(WCAG 4.1.3 - AA)**

**Acceptance criteria:**

- ✅ All error messages are tested and accessible
- ✅ Important notifications do not go unnoticed
- ✅ Temporary messages do not disappear too quickly, unless the same information remains available elsewhere **(WCAG 2.2.1 - A)**

---

### 5. Content Structure and Hierarchy (including Page Titles and Consistency)

**Objective:** Organize information logically and navigably, and ensure structural and navigational consistency across the site.

- The heading structure is hierarchical and reflects the structure of the content (H1 → H2 → H3) **(WCAG 1.3.1 - A)**
- Each page has a unique, descriptive H1 heading (⚠️ good practice, not a WCAG criterion: 2.4.2 concerns the page's `<title>` element — see the dedicated bullet below)
- Headings and labels describe the topic or purpose of their content **(WCAG 2.4.6 - AA)**
- Lists are marked up semantically (`<ul>`, `<ol>`, `<li>`) **(WCAG 1.3.1 - A)**
- Data tables have appropriate headers (`<th>`, `scope`) **(WCAG 1.3.1 - A)**
- Complex tables use `id` and `headers` for association **(WCAG 1.3.1 - A)**
- Landmark regions are used correctly (`<main>`, `<header>`, `<footer>`, `<nav>`, `<aside>`, etc.) **(WCAG 1.3.1 - A)**
- Content follows a logical reading order **(WCAG 1.3.2 - A)**
- Quotations are marked up with `<blockquote>` **(WCAG 1.3.1 - A)**
- Definitions use `<dl>`, `<dt>`, `<dd>` **(WCAG 1.3.1 - A)**
- Each page has a descriptive `<title>` element **(WCAG 2.4.2 - A)**
- Navigation menus repeated on several pages appear in the same relative order, unless the user changes it **(WCAG 3.2.3 - AA)**
- Components with the same functionality are identified consistently (same label, icon and accessible name) everywhere they appear **(WCAG 3.2.4 - AA)**
- Help mechanisms repeated on several pages (contact details, contact form or chat, self-help such as an FAQ) appear in the same order relative to the other page content **(WCAG 3.2.6 - A)**

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
- Text is real text, not an image of text, except for logos and where a particular presentation is essential **(WCAG 1.4.5 - AA)**
- Prerecorded videos have synchronized captions **(WCAG 1.2.2 - A)**
- Live videos have synchronized captions **(WCAG 1.2.4 - AA)**
- Prerecorded videos have an audio description or a text transcript **(WCAG 1.2.3 - A)**
- Prerecorded videos have an audio description of important visual information **(WCAG 1.2.5 - AA)**
- Prerecorded audio-only content has a transcript; prerecorded video-only content has a text alternative or an audio track **(WCAG 1.2.1 - A)**
- Audio that plays automatically for more than 3 seconds can be paused or stopped, or its volume controlled independently of the system volume **(WCAG 1.4.2 - A)**
- Moving, blinking or scrolling content that starts automatically, lasts more than 5 seconds and is shown alongside other content can be paused, stopped or hidden **(WCAG 2.2.2 - A)**
- No content flashes more than three times in any one-second period, unless the flashes are below the general and red flash thresholds **(WCAG 2.3.1 - A)**
- Interactive graphics have accessible alternatives **(WCAG 1.1.1 - A)**
- Infographics have complete text descriptions **(WCAG 1.1.1 - A)**
- CAPTCHAs describe their purpose in text and offer an alternative form using another sense (e.g., visual and audio versions) **(WCAG 1.1.1 - A)**

**Acceptance criteria:**

- ✅ No information depends solely on visual content
- ✅ All critical videos have captions
- ✅ Text alternatives are relevant and sufficient
- ✅ No auto-playing audio or animation runs without a way to stop it, and nothing flashes more than three times per second

---

### 7. Dynamic Content and Advanced Interactions

**Objective:** Handle dynamic updates and complex interactions accessibly.

- Status messages (results, confirmations, progress) are announced without receiving focus (`aria-live`, `role="status"`) **(WCAG 4.1.3 - AA)**
- Modals/popups are identified (`role="dialog"` or `role="alertdialog"`) **(WCAG 4.1.2 - A)**
- Focus is automatically moved into modals when they open **(WCAG 2.4.3 - A)**
- Focus returns to the triggering element when modals close **(WCAG 2.4.3 - A)**
- Modals can be closed via keyboard, which returns keyboard control to the page **(WCAG 2.1.1, 2.1.2 - A)**; closing with Escape is the APG convention
- Accordions indicate their state (open/closed) via `aria-expanded` **(WCAG 4.1.2 - A)**
- Tabs are operable with the keyboard **(WCAG 2.1.1 - A)**; left/right arrows are the APG convention
- Tabs indicate the active tab via `aria-selected` **(WCAG 4.1.2 - A)**
- Carousels that rotate automatically can be paused **(WCAG 2.2.2 - A)**
- Carousels are keyboard-controllable **(WCAG 2.1.1 - A)**
- Tooltips and other content shown on hover or focus can be displayed with the keyboard **(WCAG 2.1.1 - A)**, can be dismissed without moving the pointer or the focus (e.g., Escape), stay visible while the pointer is over them, and remain visible until dismissed or no longer relevant **(WCAG 1.4.13 - AA)**. Native browser tooltips (the `title` attribute) are exempt from 1.4.13
- When content is loaded asynchronously (AJAX), the resulting status message (e.g., "20 results loaded") is announced **(WCAG 4.1.3 - AA)**

**Acceptance criteria:**

- ✅ All modals are identified and focus is correctly managed
- ✅ Critical updates are announced automatically
- ✅ No dynamic content is invisible to the screen reader

---

### 8. Readability and Comprehension

**Objective:** Ensure content is clear and understandable, independent of visual or language-based assumptions.

- All visual information has a text equivalent **(WCAG 1.1.1 - A)**
- The page's main language is correctly defined in code **(WCAG 3.1.1 - A)**
- The language used is clear and appropriate for the target audience (related to **WCAG 3.1.5 - AAA**, which targets a reading level no higher than lower secondary education)
- Abbreviations and acronyms can be expanded (e.g., expansion at first use, glossary, `<abbr title="">`) **(WCAG 3.1.4 - AAA)**
- Instructions do not rely solely on sensory characteristics (shape, color, size, visual location, orientation or sound) **(WCAG 1.3.3 - A, 1.4.1 - A)**
- Language changes within the content are indicated in code (`lang` attribute), except for proper names, technical terms and words that have become part of the surrounding language **(WCAG 3.1.2 - AA)**
- Words used in an unusual or restricted way (jargon, idioms, technical terms) are defined or explained **(WCAG 3.1.3 - AAA)**
- Complex content is accompanied by explanations (related to **WCAG 3.1.5 - AAA**)

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
- No step of the login requires a cognitive function test (remembering or transcribing a password or code, solving a puzzle) unless an alternative method or a mechanism to assist the user is available — for example, password managers and copy-paste are not blocked. Recognizing objects and identifying content the user provided are allowed at this level **(WCAG 3.3.8 - AA)**
- Registration / account creation is achievable
- Important transactions can be completed (purchase, payment, submission)
- Submissions that create legal or financial commitments, modify or delete user data, or submit test answers are reversible, checked for input errors with a chance to correct them, or can be reviewed and confirmed before being finalized **(WCAG 3.3.4 - AA)**
- Search is usable and results are accessible
- Filters and sorting are keyboard-accessible
- Pagination is keyboard-navigable
- File download actions are achievable
- File upload actions are accessible
- Dashboards and statistics are understandable
- Logout is accessible

Apart from the two bullets referenced above, this section is not itself a WCAG criterion. It verifies the operational conformance of the A and AA criteria across business journeys — primarily the keyboard-accessibility criteria 2.1.1 and 2.1.2, and the complete-process conformance requirement (WCAG 2.2, section 5.2.3: when a page is part of a process, all pages of the process must conform).

**Acceptance criteria:**

- ✅ All identified critical journeys are tested end-to-end
- ✅ No journey presents a major blocking issue
- ✅ Core business functionality is validated

---

### 10. Time Management and Temporal Constraints

**Objective:** Prevent time limits from blocking task completion.

- Each time limit set by the content can be turned off, adjusted (to at least ten times the default), or extended after a warning — except real-time events, essential time limits and limits longer than 20 hours **(WCAG 2.2.1 - A)**
- Before a session expires, the user is warned and can extend it with a simple action, with at least 20 seconds to respond **(WCAG 2.2.1 - A)**
- Moving or animated content can be paused, stopped or hidden **(WCAG 2.2.2 - A)**
- Content that updates automatically alongside other content (news feed, live scores) can be paused, stopped, hidden, or its update frequency controlled **(WCAG 2.2.2 - A)**
- Automatic page refreshes and content updates can be postponed or turned off by the user **(WCAG 2.2.4 - AAA)**
- Interruptions (e.g., pop-ups) can be postponed or suppressed, except emergencies **(WCAG 2.2.4 - AAA)**
- Timing is not an essential part of the activity: no time limit is imposed, except for non-interactive synchronized media and real-time events **(WCAG 2.2.3 - AAA)**

**Acceptance criteria:**

- ✅ No time limit blocks task completion
- ✅ Expiry warnings are accessible
- ✅ Problematic animations can be controlled

---

### 11. Zoom and Resizing

**Objective:** Ensure usability at high zoom levels and small viewport widths.

- Text can be resized to 200% (browser zoom) without loss of content or functionality **(WCAG 1.4.4 - AA)**
- At 400% zoom on a window 1280 CSS px wide (equivalent to a 320 CSS px viewport), content reflows without loss of information or functionality **(WCAG 1.4.10 - AA)**
- No horizontal scrolling is required to read vertically scrolling content **(WCAG 1.4.10 - AA)**
- No text is truncated or overlapping **(WCAG 1.4.4, 1.4.10 - AA)**
- Content that needs a two-dimensional layout (data tables, maps, diagrams) is exempt from 1.4.10 and may keep horizontal scrolling, but the content around it (headings, search fields, pagination) must still reflow **(WCAG 1.4.10 - AA)**. Placing a wide table in its own scrollable container is a common solution

**Acceptance criteria:**

- ✅ 100% of content and functionality remain accessible at 200%
- ✅ At 400%, no reading requires horizontal scrolling (except within data tables and other two-dimensional content)
- ✅ No critical component becomes unusable
- ✅ No content is hidden or cut off

---

### 12. Text Spacing

**Objective:** Ensure robustness against readability adaptations.

Manual application of the following values (for example via DevTools or a text-spacing bookmarklet):

- Line height: 1.5 × the font size (`line-height: 1.5`)
- Spacing after paragraphs: 2 × the font size (e.g., `p { margin-bottom: 2em }`)
- Letter spacing: 0.12 × the font size (`letter-spacing: 0.12em`)
- Word spacing: 0.16 × the font size (`word-spacing: 0.16em`)

Checks **(WCAG 1.4.12 - AA)**:

- No overlap occurs
- No content is lost
- Components remain usable

**Acceptance criteria:**

- ✅ The application remains fully functional
- ✅ No text overlaps
- ✅ No additional horizontal scroll is generated (good practice)

---

### 13. Visual Contrasts

**Objective:** Ensure the perceivability of content and components.

- Normal text contrast ≥ 4.5:1 **(WCAG 1.4.3 - AA)**
- Large text (at least 18 pt, or 14 pt bold — about 24 px, or 18.5 px bold) contrast ≥ 3:1 **(WCAG 1.4.3 - AA)**
- Text in disabled components, purely decorative text and logos have no contrast requirement **(WCAG 1.4.3 - AA)**
- UI components and meaningful graphics (field borders that identify a field, informative icons, buttons, chart elements) have a contrast ≥ 3:1 against adjacent colors **(WCAG 1.4.11 - AA)**
- Focus indicators meet the same non-text contrast ratio as other UI components **(WCAG 1.4.11 - AA)** — see Theme 1 for the requirement that focus be visible at all times
- States (error, active, selected) are not conveyed by color alone **(WCAG 1.4.1 - A)**, and the visual indicator of a state has a contrast ≥ 3:1 **(WCAG 1.4.11 - AA)**

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
- No content or interaction is restricted to one orientation, unless a specific orientation is essential (e.g., a piano application, a bank check) **(WCAG 1.3.4 - AA)**

**Acceptance criteria:**

- ✅ All critical functionality is accessible in both orientations
- ✅ No essential content is hidden

---

### 15. Touch and Pointer Interactions

**Objective:** Ensure accessibility for touch and motor-impaired users.

- Multipoint or path-based gestures (pinch, swipe, drawing a path) have a single-pointer alternative without a path, unless the gesture is essential **(WCAG 2.5.1 - A)**
- Actions are not triggered on the "down" event (touch down, mouse down), unless this is essential **(WCAG 2.5.2 - A)**
- An action started by mistake can be aborted before it completes (moving the pointer away before releasing) or undone afterwards **(WCAG 2.5.2 - A)**
- Functions triggered by device or user motion (shaking, tilting) can also be operated with interface controls, and responding to motion can be disabled **(WCAG 2.5.4 - A)**
- Every drag-and-drop action has a single-pointer alternative without dragging (e.g., buttons or a menu) **(WCAG 2.5.7 - AA)**

**Acceptance criteria:**

- ✅ 100% of complex gestures, dragging movements and motion-based functions have an alternative
- ✅ No irreversible action is triggered accidentally
- ✅ Critical actions are confirmable (good practice)

---

### 16. Target Size

**Objective:** Reduce activation errors.

- Pointer targets measure at least 24 × 24 CSS px, or smaller targets are spaced so that a 24 CSS px diameter circle centered on each one does not intersect another target or the circle of another small target **(WCAG 2.5.8 - AA)**
- Exceptions to 2.5.8: an equivalent control on the same page meets the size, the target is inline in a sentence, its size is set by the browser and not modified, or a particular presentation is essential or legally required **(WCAG 2.5.8 - AA)**
- Targets measure at least 44 × 44 CSS px **(WCAG 2.5.5 - AAA)** — beyond the AA requirement, recommended at least for critical actions
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

This section turns the themes above into three short, practical checklists, one per conformance level, to apply during integration and system testing. Each row groups success criteria that can be tested together, with the same tools and in the same pass; it is not the full WCAG list sorted by level.

- **Fundamental criteria (Level A)**: the 31 Level A success criteria of WCAG 2.2, grouped into 20 checks. A failure at this level usually blocks some users completely.
- **Legal criteria (Level AA)**: the 24 Level AA success criteria, grouped into 18 checks. Level AA is the level required by the legal frameworks.
- **Excellence criteria (Level AAA and good practices)**: a selection of AAA criteria and good practices that are useful in business applications.

For each check, the table gives a short label, what to check, the WCAG success criteria and level it covers, and how to verify it.

**Goal:** prepare the application for the expert review (see section 4.6 of the lecture material) by finding and fixing the most frequent issues early. These checklists do not replace that review: passing every row does not prove conformance, because the expert review evaluates each success criterion in detail, on a representative sample of pages and on complete processes.

### Fundamental Criteria (Level A — Eliminating Blockers)

This table covers the 31 Level A success criteria of WCAG 2.2. These criteria guarantee basic access to information and functionality, without which some users with disabilities could simply not use the service.

| Criterion | Description | WCAG | How to verify |
| --- | --- | --- | --- |
| **Keyboard access** | Every feature and every critical journey (login, forms, transactions, search, logout) can be completed with the keyboard alone, and focus can always leave every component | 2.1.1, 2.1.2 (A) | 1. Stop using the mouse or trackpad.<br>2. Complete each critical journey (login, main form, transaction, search, logout) using only Tab, Shift+Tab, Enter, Space, the arrow keys and Escape.<br>3. In every widget (menu, dialog, date picker, embedded player), try to leave it with Tab, Shift+Tab or Escape.<br>✅ **Pass:** every journey can be completed, and the focus never gets stuck. |
| **Focus order and focus management** | Focus moves in an order that preserves meaning; it moves into a dialog when it opens and returns to a logical place (usually the trigger) when it closes | 2.4.3 (A) | 1. From the top of the page, press Tab repeatedly and watch where the focus goes.<br>2. Open each dialog: the focus must land inside it.<br>3. Close it: the focus must return to the button that opened it, or to another logical place.<br>4. Submit a form with an error and note where the focus lands.<br>✅ **Pass:** the focus follows the logical order of the page and never jumps to an unexpected place (for example, back to the top of the page). |
| **Character key shortcuts** | Single-character shortcuts (letter, digit, punctuation) can be turned off or remapped, or are active only when their component has focus | 2.1.4 (A) | 1. Turn the screen reader off (in browse mode, it uses single letters itself).<br>2. Click on an empty area of the page, outside any text field.<br>3. Press single letter, digit and punctuation keys (for example s, k, 1, ?).<br>4. If something happens, look for a setting to turn the shortcut off or change it, or check that it only works while its component has focus.<br>✅ **Pass:** no single-key shortcut is triggered, unless it can be turned off or remapped, or works only on the focused component. |
| **Page titles and bypass blocks** | Each page has a descriptive `<title>`; blocks repeated on several pages can be bypassed with a skip link, landmarks or headings | 2.4.2, 2.4.1 (A) | 1. Open several pages and read the title in the browser tab (or listen to the screen reader when the page loads).<br>2. Reload a page and press Tab once: a "Skip to main content" link should appear; press Enter on it.<br>3. If there is no skip link, open the screen reader's list of landmarks and list of headings (see Appendices C–E).<br>✅ **Pass:** each title describes the topic or purpose of the page (for example "Payment – Step 2 of 3 – MyApp"); the skip link moves you to the main content, or the landmarks or headings let you jump past the repeated blocks. |
| **Semantic structure** | Headings, landmarks, lists, data-table headers, field groups (`<fieldset>`/`<legend>`), label associations and required fields are conveyed in code, not only visually | 1.3.1 (A) | 1. Open the screen reader's list of headings, then its list of landmarks (see Appendices C–E).<br>2. In each data table, move cell by cell with the screen reader's table commands.<br>3. In each form, Tab into the fields and listen.<br>4. In DevTools (Elements panel, Accessibility pane), check that what looks like a heading, a list or a table uses the matching HTML element.<br>✅ **Pass:** every visual heading and region appears in the lists; column and row headers are read with each cell; each field is read with its label, its group (legend) and "required" when it applies. |
| **Meaningful sequence** | The reading order in code matches the meaning of the content (e.g., context before details) | 1.3.2 (A) | 1. With the screen reader, start continuous reading at the top of the page.<br>2. Follow along on screen and compare the reading order with the visual order.<br>✅ **Pass:** the content is read in an order that makes sense: labels before their fields, a status before its details, no text from one column read in the middle of another. |
| **Text alternatives** | Informative images, icon-only controls, charts and CAPTCHAs have a text alternative that serves the same purpose; decorative images are hidden from assistive technologies | 1.1.1 (A) | 1. With the screen reader, move from image to image (graphics list or graphics navigation) and listen to each one.<br>2. In DevTools, check that each `<img>` has an `alt` attribute (`alt=""` for decorative images), and that each icon-only button has a name in the Accessibility pane.<br>3. For each chart or diagram, look for the same information in text or in a table.<br>✅ **Pass:** each informative image or icon is announced with text that gives the same information or function; decorative images are not announced. |
| **Prerecorded audio and video** | Audio-only content has a transcript; video-only content has a text or audio alternative; videos with sound have synchronized captions, and an audio description or a full text alternative | 1.2.1, 1.2.2, 1.2.3 (A) | 1. Play each video with captions on: the captions must match the speech and important sounds, at the same time.<br>2. For each video, look for an audio-described version or a full text alternative that also describes the important visual information.<br>3. For audio-only content (for example a podcast), look for a transcript; for video without sound, look for a text description or an audio track.<br>✅ **Pass:** every prerecorded media item has the alternatives listed above. |
| **Moving, flashing and auto-playing content** | Content that moves, blinks or scrolls for more than 5 seconds, or updates automatically, can be paused, stopped or hidden; audio that plays automatically for more than 3 seconds can be stopped or its volume controlled; nothing flashes more than three times per second (unless below the flash thresholds) | 2.2.2, 1.4.2, 2.3.1 (A) | 1. Load each page and wait at least 5 seconds; list everything that moves, blinks, scrolls or updates by itself (carousel, ticker, animation, live feed).<br>2. For each one, find a pause, stop or hide button and use it with the keyboard.<br>3. If audio starts by itself and lasts more than 3 seconds, find a control on the page to stop it or lower its volume.<br>4. If anything flashes more than three times in one second, check it with a photosensitive-epilepsy analysis tool (for example PEAT), or report it for the expert review.<br>✅ **Pass:** every item from step 1 can be paused, stopped or hidden; auto-playing audio can be stopped; nothing flashes above the thresholds. |
| **Time limits** | Each time limit can be turned off, adjusted (at least ten times the default) or extended after a warning (at least 20 seconds, simple action), except real-time, essential and over-20-hour limits | 2.2.1 (A) | 1. Ask the team which time limits exist (session timeout, timed steps, reservations held for a limited time).<br>2. Trigger each one: stay inactive until shortly before it expires (ask for a test environment with a short timeout if needed).<br>3. Check that a warning appears, that the screen reader announces it, and that one simple action (for example one button) extends the time.<br>✅ **Pass:** every time limit can be turned off, adjusted or extended with at least 20 seconds to react, or is a real-time, essential or over-20-hour limit. |
| **Not by color or senses alone** | Information, states and instructions do not rely only on color, or only on shape, size, position or sound | 1.4.1, 1.3.3 (A) | 1. In Chrome DevTools, open Rendering > Emulate vision deficiencies > Achromatopsia (grayscale).<br>2. Look at links inside text, form errors, required fields, charts and status indicators.<br>3. Read the instructions and look for references such as "the green button", "the field on the right" or "when you hear the beep".<br>✅ **Pass:** in grayscale, all information and states remain understandable; every instruction also names the element (for example "the Submit button"). |
| **Link purpose and label in name** | The purpose of each link is clear from its text or its context; the accessible name of links, buttons and controls contains their visible text | 2.4.4, 2.5.3 (A) | 1. Open the screen reader's list of links and read each one, together with its sentence, paragraph or table cell when needed.<br>2. For each link and button with visible text, compare that text with the accessible name in DevTools (Elements panel, Accessibility pane, "Name").<br>✅ **Pass:** no link is ambiguous ("click here" with no context); each accessible name contains the visible text, ideally at the start. |
| **Name, role, value** | All controls, native and custom, expose a name, a role, and their states and values (expanded, selected, checked, disabled), and changes are passed to assistive technologies | 4.1.2 (A) | 1. With the screen reader, Tab to each control and listen: it must say the name, the type (button, checkbox, tab, menu…) and the state (checked, expanded, selected, disabled).<br>2. Change the state (open the accordion, tick the box, select the tab) and listen again.<br>3. For custom components, check the role and the ARIA states in DevTools (Accessibility pane).<br>✅ **Pass:** every control announces its name, role and current state, and the new state is announced after each change. |
| **Form labels and instructions** | Every field has a visible label or instructions, including the indication of required fields and of expected formats | 3.3.2 (A) | 1. Look at each form without the screen reader: each field must have a visible label; required fields and expected formats (date, phone) must be shown before input, not only in a placeholder that disappears when typing.<br>2. Tab through the form with the screen reader.<br>✅ **Pass:** every label, required indicator and format is visible and is also announced. |
| **Error identification** | Automatically detected input errors identify the field in error and describe the error in text | 3.3.1 (A) | 1. Submit each form empty.<br>2. Submit it again with invalid values (email without @, date in the wrong format).<br>3. Check each error on screen and with the screen reader.<br>✅ **Pass:** each field in error is identified (message next to the field, or field name in the message), and the error is described in text, not only with a red border or an icon. |
| **Predictable focus and input** | Receiving focus never causes a change of context; changing a field value does not either, unless the user has been advised beforehand | 3.2.1, 3.2.2 (A) | 1. Tab through every control without activating anything.<br>2. Change the values of drop-down lists, radio buttons and checkboxes with the keyboard (arrow keys, Space), without pressing any button.<br>✅ **Pass:** no new window opens, the page does not change, no form is submitted and the focus does not jump. For value changes only, this is allowed if a visible text explained it beforehand. |
| **Consistent help** | Help mechanisms repeated on several pages (contact details, contact form or chat, FAQ) appear in the same order relative to the other page content | 3.2.6 (A) | 1. List the help mechanisms of the site (contact details, contact form, chat, FAQ link).<br>2. Open at least three pages where they appear and note their position relative to the rest of the content (for example "in the footer, after the legal links").<br>✅ **Pass:** on every page, they appear in the same order relative to the other content. |
| **Redundant entry** | Information already entered in the same process is pre-filled or selectable, except where re-entry is essential, required for security, or the information is no longer valid | 3.3.7 (A) | 1. Go through each multi-step process (registration, order, request).<br>2. Note every piece of information asked more than once (for example the address in step 2, then again in step 4).<br>✅ **Pass:** information asked again is pre-filled or offered for selection (for example "Same as delivery address"), unless re-entering it is essential, needed for security (for example a password) or the earlier value is no longer valid. |
| **Pointer gestures, cancellation and motion** | Multipoint or path-based gestures have a single-pointer alternative; actions do not trigger on the down event, or can be aborted or undone; motion-triggered functions have a control alternative and can be disabled | 2.5.1, 2.5.2, 2.5.4 (A) | 1. On a touch device, list every gesture (pinch, swipe, multi-finger tap, drawing a path) and use its alternative (button, link, single tap).<br>2. Press a button with the mouse or a finger, keep pressing, move away from the button, then release.<br>3. For features triggered by shaking or tilting the device, look for an on-screen button and a setting to turn motion off.<br>✅ **Pass:** each gesture has a single-tap or single-click alternative; releasing outside the button does nothing (or the action can be undone); each motion feature has a button and can be turned off. |
| **Page language** | The default language of each page is declared in code (`lang` on `<html>`) | 3.1.1 (A) | 1. In DevTools, select the `<html>` element and read its `lang` attribute (for example `lang="fr"`).<br>2. Listen to the start of the page with the screen reader.<br>✅ **Pass:** the `lang` attribute is present and matches the page language; the screen reader uses the right pronunciation. |

---

### Legal Criteria (Level AA — Required Conformance)

This table covers the 24 Level AA success criteria of WCAG 2.2. Level AA is the level required by the legal frameworks presented in chapter 2 of the lecture material: EN 301 549 for the EU directives (V4.1.1 is aligned with WCAG 2.2), RGAA 4.1.2 in France and eCH-0059 V3.0 in Switzerland (both still based on WCAG 2.1). Conformance at Level AA also requires all the Level A criteria of the previous table.

| Criterion | Description | WCAG | How to verify |
| --- | --- | --- | --- |
| **Focus visible and not obscured** | A visible focus indicator is shown on every focusable element and never removed by CSS; the focused element is never entirely hidden by sticky headers, banners or chat widgets | 2.4.7, 2.4.11 (AA) | 1. Keep all sticky elements displayed (header, cookie banner, chat button): do not close them.<br>2. Press Tab through the whole page, down to the footer, and watch the focus indicator.<br>✅ **Pass:** you can always see which element has the focus, and the focused element is never completely hidden behind a sticky header, banner or widget (partly hidden is allowed at Level AA). |
| **Contrast** | Text ≥ 4.5:1 (large text ≥ 3:1); UI components, state indicators, focus indicators and meaningful graphics ≥ 3:1 against adjacent colors. Disabled components, decoration and logos are exempt | 1.4.3, 1.4.11 (AA) | 1. Run an automated checker (axe DevTools or WAVE) to find text contrast failures.<br>2. With a contrast checker (for example the WebAIM Contrast Checker, or the contrast ratio in the DevTools color picker), measure what the automated tool cannot evaluate: text on images or gradients, field borders, icons, focus indicators and chart elements, each against the color next to it.<br>3. Repeat on the hover, focus, error and selected states.<br>✅ **Pass:** normal text ≥ 4.5:1; large text (≥ 24 px, or ≥ 18.5 px bold) ≥ 3:1; components, states, focus indicators and meaningful graphics ≥ 3:1. |
| **Resize text** | Text can be resized to 200% without loss of content or functionality | 1.4.4 (AA) | 1. Set the browser zoom to 200% (Ctrl or Cmd and +).<br>2. Go through every page and component (menus, dialogs, forms, tables).<br>✅ **Pass:** all text is larger, nothing is cut off, hidden or overlapping, and every function still works. |
| **Reflow** | At 320 CSS px wide (400% zoom on a 1280 CSS px window), content reflows without horizontal scrolling and without loss of information or functionality; data tables, maps and diagrams are exempt | 1.4.10 (AA) | 1. Set the browser window to 1280 px wide and the zoom to 400%; or, alternatively, use the DevTools device toolbar with a width of 320 px and zoom at 100%.<br>2. Go through each page, scrolling only up and down.<br>✅ **Pass:** you can read all content and use every function without scrolling sideways; only data tables, maps and diagrams may scroll horizontally. |
| **Text spacing** | Increasing line height, paragraph, letter and word spacing to the 1.4.12 values causes no loss of content or functionality | 1.4.12 (AA) | 1. In DevTools, add these rules to the page: `* { line-height: 1.5 !important; letter-spacing: 0.12em !important; word-spacing: 0.16em !important; } p { margin-bottom: 2em !important; }` (or use a text-spacing bookmarklet).<br>2. Go through each page.<br>✅ **Pass:** no text is cut off, hidden or overlapping, and every function still works. |
| **Content on hover or focus** | Tooltips, sub-menus and pop-overs shown on hover or focus can be dismissed without moving the pointer or focus, stay visible while hovered, and remain until dismissed or no longer relevant | 1.4.13 (AA) | For each tooltip, sub-menu or pop-over:<br>1. Make it appear with the mouse, then with the keyboard (Tab).<br>2. Press Escape (or the close mechanism provided): it must close without moving the pointer or the focus.<br>3. Make it appear with the mouse again, then move the pointer onto it: it must stay visible.<br>4. Wait without moving: it must stay until you move away or close it.<br>✅ **Pass:** steps 2 to 4 succeed for each one. Step 2 is not required if the content hides no other content or shows an input error; native `title` tooltips are exempt. |
| **Images of text** | Text is real text, not an image of text, except logos and essential presentations | 1.4.5 (AA) | 1. Zoom to 200%: images of text become blurry, real text stays sharp.<br>2. Try to select the suspicious text with the mouse.<br>3. In DevTools, check whether the element is an `<img>`, an SVG image or a CSS background image.<br>✅ **Pass:** all text is real text, except logos and cases where the exact visual presentation is essential. |
| **Orientation** | The interface works in portrait and landscape, unless one orientation is essential | 1.3.4 (AA) | 1. On a phone or tablet, turn the rotation lock off.<br>2. Open each page in portrait, then turn the device to landscape (and back).<br>✅ **Pass:** content is displayed and works in both orientations; no message asks you to rotate the device, unless one orientation is essential. |
| **Identify input purpose** | Fields collecting information about the user expose their purpose with `autocomplete` | 1.3.5 (AA) | 1. In DevTools, inspect each field that asks for the user's own data (name, email, phone, address, date of birth…).<br>2. Read its `autocomplete` value and check that it matches the data (for example `given-name`, `email`, `tel`, `postal-code`, `bday`).<br>3. Optionally, with autofill data saved in the browser, check that the browser suggests the right values.<br>✅ **Pass:** each of these fields has the correct value from the WCAG list "Input Purposes for User Interface Components". |
| **Status messages** | Errors, confirmations, result counts and loading or progress messages that appear without moving the focus are announced by the screen reader | 4.1.3 (AA) | 1. Turn the screen reader on.<br>2. Trigger each message that appears without moving the focus: inline form error, "Saved" confirmation, "12 results found" after a search or filter, loading message, basket counter update.<br>3. Do not move the focus; listen.<br>✅ **Pass:** each message is read automatically. If one is not, check in DevTools that its container has `role="status"`, `role="alert"` or `aria-live`, and that the container is already in the page (empty) before the message is inserted — `role="alert"` is generally announced even when injected with its message. |
| **Error suggestion and prevention** | Error messages suggest a correction when one is known; submissions with legal or financial consequences, that modify or delete user data, or that submit test answers can be reversed, checked or confirmed before finalization | 3.3.3, 3.3.4 (AA) | **Error suggestion:**<br>1. Enter typical wrong values (email without @, date in the wrong format, number out of range) and submit.<br>2. Read each error message.<br>✅ **Pass:** when the expected format or value is known, the message says it (for example "Enter the date as DD.MM.YYYY").<br>**Error prevention:**<br>3. List the forms that commit the user legally or financially (contract, payment, tax return), that change or delete their saved data (profile, account deletion), or that submit test answers.<br>4. Fill in each one and submit it.<br>✅ **Pass:** at least one of these is true: a summary page lets you check, correct and confirm the data before the final submission; or the data is checked and errors can be corrected before it is finalized; or the submission can be cancelled afterwards. |
| **Descriptive headings and labels** | Headings and labels describe the topic or purpose of their content | 2.4.6 (AA) | 1. Open the screen reader's list of headings and read the headings alone, without the page.<br>2. Tab through the forms and listen to the labels alone.<br>✅ **Pass:** each heading tells what its section is about, and each label tells what to enter (no "Field 1", "Info" or "Details" without a subject). |
| **Multiple ways** | More than one way (search, sitemap, menu) leads to each page, except pages that are a step in a process | 2.4.5 (AA) | 1. Pick about five pages of the site that are not a step in a process.<br>2. For each one, try to reach it in two different ways: main menu, search, sitemap, links from related pages, table of contents.<br>✅ **Pass:** each page can be reached in at least two ways. |
| **Consistent navigation and identification** | Repeated navigation appears in the same relative order on every page; the same functions carry the same labels, icons and accessible names | 3.2.3, 3.2.4 (AA) | 1. Open at least three pages that share the same navigation.<br>2. Compare the menus: the items must appear in the same relative order (items can be added or removed, not reordered).<br>3. Compare the functions that appear on several pages (search, print, download, close, help): same label, same icon, same accessible name.<br>✅ **Pass:** no menu is reordered and no function changes name or icon from one page to another. |
| **Language of parts** | Passages in another language are marked with `lang`, except proper names and technical terms | 3.1.2 (AA) | 1. Find passages in a language other than the page language (for example an English quote on a French page, or "Deutsch" and "Italiano" in a language switcher).<br>2. In DevTools, check that each one has a `lang` attribute (for example `lang="de"`).<br>3. Listen with the screen reader: the pronunciation should change.<br>✅ **Pass:** each passage in another language is marked, except proper names, technical terms and words commonly used in the page language. |
| **Live captions and audio description** | Live videos have captions; prerecorded videos have an audio description of important visual information | 1.2.4, 1.2.5 (AA) | 1. For live streams (webinars, events), turn captions on during a broadcast and check that they appear in real time.<br>2. For each prerecorded video, look for an audio-description track or an audio-described version; play it and check that it describes the important visual information (on-screen text, actions, scene changes).<br>✅ **Pass:** live videos have captions; prerecorded videos have an audio description, unless the soundtrack already conveys all the important visual information. |
| **Dragging and target size** | Every drag action has a single-pointer alternative without dragging; targets measure at least 24 × 24 CSS px or are sufficiently spaced (see Theme 16 for the exceptions) | 2.5.7, 2.5.8 (AA) | **Dragging:**<br>1. List every drag interaction (sortable list, slider, file drop zone, map, kanban board).<br>2. Perform the same action with single clicks or taps only (for example a "Move up" button, a click on the slider track, a "Browse" button).<br>**Target size:**<br>3. In DevTools, hover the small targets (icons, close buttons, links in lists, pagination) with the element picker: it shows their width × height.<br>✅ **Pass:** every drag action has a click or tap alternative; each target measures at least 24 × 24 CSS px, or is spaced as described in Theme 16, or is one of its exceptions (for example a link inside a sentence). |
| **Accessible authentication** | Login does not rely on a cognitive function test without an alternative or an assisting mechanism; password managers and copy-paste work | 3.3.8 (AA) | 1. Save the test account in a password manager and log in with autofill.<br>2. Log out, copy the password and paste it into the password field.<br>3. If there is a code step (code sent by SMS or email, one-time password), check that you can paste the code, or that an alternative exists (for example a login link in the email).<br>4. If there is a CAPTCHA or a puzzle, check that an alternative exists that does not require transcribing or solving anything (recognizing objects is allowed at Level AA).<br>✅ **Pass:** login works with the password manager and with paste, and no step requires remembering, transcribing or solving something without an alternative. |

---

### Excellence Criteria (Level AAA and Good Practices — Optimization)

This section presents a selection of Level AAA criteria and good practices that are not WCAG requirements, which aim to provide optimal accessibility and an exceptional user experience. Unlike Levels A and AA, these criteria are not imposed by regulation, and WCAG does not recommend requiring Level AAA as a general policy for entire sites. Applied criterion by criterion where the content allows it, they improve comfort for everyone, including users with specific or complex needs.

| Criterion | Description | WCAG | How to verify |
| --- | --- | --- | --- |
| **Link purpose (link only)** | The purpose of each link is clear from the link text alone | 2.4.9 (AAA) | 1. Open the screen reader's list of links (it shows the link texts without their context).<br>2. Read each link.<br>✅ **Pass:** each link is understandable on its own (for example "Download the 2026 annual report (PDF)" rather than "Download"). |
| **Location and progress** | The user knows where they are in the site (breadcrumb, current item in the navigation with `aria-current`) and in a multi-step process ("Step 2 of 4") | 2.4.8 (AAA) for the location within a set of pages; step indicators: good practice | 1. On several pages, check that you can tell where you are: breadcrumb, highlighted current item in the menu, page heading.<br>2. With the screen reader, check that the current menu item is announced as "current".<br>3. In each multi-step process, check that the current step and the total number of steps are shown and announced (for example "Step 2 of 4: Address").<br>✅ **Pass:** location and progress are visible and announced. |
| **Context-sensitive help** | Help is available where users need it (help text, help link, tooltip next to complex fields) | 3.3.5 (AAA) | 1. Identify the complex fields and functions (for example IBAN, tax codes, accepted file formats).<br>2. Check that a help text, help link or help button is next to them.<br>3. Open the help with the keyboard and with the screen reader.<br>✅ **Pass:** help is available next to each complex field or function, and it can be reached and read with the keyboard and the screen reader. |
| **Unusual words and abbreviations** | Jargon, technical terms and abbreviations are defined or expanded | 3.1.3, 3.1.4 (AAA) | 1. Ask someone outside the project, or new to the business domain, to read the main pages and note every word or abbreviation they do not understand.<br>2. For each one, look for a definition or an expansion: at first use, in a glossary, or with `<abbr title="">`.<br>✅ **Pass:** every term noted in step 1 is defined or expanded. |
| **Reading level** | Text that requires more than a lower-secondary reading level has a simpler version or supplementary content | 3.1.5 (AAA) | 1. Paste the main texts (instructions, error messages, help) into a readability tool for the language of the content.<br>2. For texts above the lower-secondary level, look for a simpler version, a summary or illustrations.<br>✅ **Pass:** every text above that level has a simpler version or supplementary content. |
| **Target size (enhanced)** | Interactive targets measure at least 44 × 44 CSS px | 2.5.5 (AAA) | 1. In DevTools, hover each interactive element with the element picker and read its width × height.<br>✅ **Pass:** each target measures at least 44 × 44 CSS px, except links inside text, targets with an equivalent control of that size on the same page, browser-default controls and essential presentations. |
| **Interruptions and automatic updates** | Pop-ups, automatic refreshes and content updates can be postponed or suppressed, except emergencies | 2.2.4 (AAA) | 1. Stay for a few minutes on pages that show notifications or pop-ups, or that refresh by themselves (dashboards, inboxes).<br>2. Look for a way to postpone or turn them off (for example "Pause updates", notification settings).<br>✅ **Pass:** every interruption that is not an emergency can be postponed or turned off. |
| **Changes on request and new windows** | Changes of context happen only on user request; links that open a new window or tab say so in their text | 3.2.5 (AAA) | 1. Activate each link and control that opens a new window or tab.<br>2. Stay on pages without acting and watch for automatic refreshes or redirects.<br>✅ **Pass:** each link that opens a new window or tab says so in its text (for example "(opens in a new tab)", W3C technique H83); no refresh or redirect happens without a user action. |
| **No timing** | No time limit is imposed, except for non-interactive synchronized media and real-time events | 2.2.3 (AAA) | 1. Ask the team for the list of time limits (the same list as for 2.2.1).<br>✅ **Pass:** no time limit exists, except in non-interactive synchronized media and real-time events (for example a live auction). |
| **Heading hierarchy** | One H1 per page and no skipped heading levels | — (good practice, not a WCAG requirement) | 1. Open the screen reader's list of headings, or use a heading-outline browser extension.<br>2. Check the heading levels.<br>✅ **Pass:** exactly one H1 per page, and no skipped level (for example no H2 followed directly by an H4). |

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
