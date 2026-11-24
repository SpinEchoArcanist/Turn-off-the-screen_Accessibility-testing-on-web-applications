# Appendix A — WCAG Summary

## Introduction

### What is WCAG?

The **WCAG** (*Web Content Accessibility Guidelines*) are a set of recommendations published by the **W3C** through its **WAI** (*Web Accessibility Initiative*).
Their purpose is to make websites, applications and digital services accessible to everyone, including people with disabilities (visual, auditory, motor, cognitive, etc.).

The current version is **WCAG 2.2** (W3C Recommendation of 5 October 2023, updated on 12 December 2024). An authorised French translation is published by the W3C.

[https://www.w3.org/TR/WCAG22/](https://www.w3.org/TR/WCAG22/)

### Objectives

WCAG pursues three main objectives:

- **Ensure universal accessibility**: enable use of the web regardless of users' physical, sensory or technological abilities.
- **Provide an international reference**: offer a recognised framework for designing accessible content. WCAG 2.2 is also published as the international standard **ISO/IEC 40500:2025**.
- **Support regulation**: serve as the basis for many digital accessibility laws and standards, such as the **RGAA** in France, the **EN 301 549** standard in Europe, the **eCH-0059** standard in Switzerland, or **Section 508** in the United States.

---

## Fundamental Principles of WCAG

WCAG rests on four **principles**, often summarised by the acronym **P.O.U.R.**
These principles set the foundations of all digital accessibility: content that fails one of them cannot be considered accessible.

Under each principle there are **guidelines** (13 in total in WCAG 2.2), which set the objectives to reach so that applications are accessible to users with disabilities. Guidelines are not testable.

Each guideline has a list of **success criteria**, which are testable and are used to validate conformance. WCAG 2.2 contains **86 success criteria** (criterion 4.1.1 Parsing is obsolete and has been removed).
To meet the needs of different groups and situations, three conformance levels are defined: A (the lowest), AA and AAA (the highest).

### Chapter 1 – Perceivable

Information and user interface components must be presentable to users in ways they can perceive.
The *Perceivable* principle reminds us that information must be presented so that every user can take it in, whatever their sensory abilities.
This means making content visible, audible or understandable through different formats.

- *Example: provide text alternatives for images, or ensure sufficient contrast between text and background.*

The guidelines of this principle are:

- **1.1 Text Alternatives**: provide text descriptions for images, icons and any non-text content.
- **1.2 Time-based Media**: provide captions, transcripts or audio descriptions for videos and multimedia content.
- **1.3 Adaptable**: allow content to be presented in different ways (for example, in a simplified reading mode or another layout) without loss of information or structure.
- **1.4 Distinguishable**: make sure that essential elements are easy to see and hear, thanks to sufficient contrast, resizable text and a clear separation between foreground and background.

### Chapter 2 – Operable

User interface components and navigation must be operable, whatever the means of navigation.
The *Operable* principle stresses that a website or application must be easy to operate, whatever the input method used (keyboard, mouse, touchscreen, voice commands, etc.). An accessible interface is not just visible: it must also be operable by everyone.

- *Example: allow full access to the site using only the keyboard, or make sure interactive areas are large enough to be operated easily.*

The guidelines of this principle are:

- **2.1 Keyboard Accessible**: allow full access to content and functionality without a mouse.
- **2.2 Enough Time**: give users enough time to read, understand and interact with content, without excessive time constraints.
- **2.3 Seizures and Physical Reactions**: limit content likely to cause adverse reactions (for example, avoid flashing animations that can trigger epileptic seizures).
- **2.4 Navigable**: provide clear ways to find one's way around the site (page titles, consistent menus, explicit headings, visible focus, etc.).
- **2.5 Input Modalities**: make functionality usable with inputs other than the keyboard (pointer, touch, gestures, device motion), for example with targets large enough and simple alternatives to complex gestures.

In short, operable content does not put any obstacle in the way of interaction, whatever the device or method used by the user.

### Chapter 3 – Understandable

Information and the operation of the user interface must be clear and predictable.
The *Understandable* principle means that the content and the operation of a website or application must be clear, predictable and easy to understand for all users.
It is not enough for information to be visible and operable: it must also be intelligible.

- *Example: use plain language, give explicit instructions, and avoid unexpected behaviour (such as a button that suddenly changes function).*

The guidelines of this principle are:

- **3.1 Readable**: make the language of the page and of its passages identifiable, and make text understandable (unusual words, abbreviations, reading level).
- **3.2 Predictable**: keep navigation and the behaviour of interactive elements consistent, so that users know what to expect.
- **3.3 Input Assistance**: help users avoid and correct mistakes, with labels, clear instructions, explicit error messages and suggestions, including for users with cognitive or learning difficulties.

In short, understandable content lets users grasp information and interact with it without confusion or frustration.

### Chapter 4 – Robust

Content must be technically reliable and interpretable by a wide variety of user agents, including current and future assistive technologies.
The *Robust* principle means that content must be reliably interpreted by different tools and technologies, including current and future assistive technologies.
The aim is to ensure that the website or application remains accessible even when the technical context or the device changes.

- *Example: follow web standards so that screen readers and other tools can interpret the page correctly.*

This principle has a single guideline:

- **4.1 Compatible**: maximise compatibility with current and future user agents, including assistive technologies. In practice: every component exposes a name, a role, states and values that assistive technologies can determine (correct use of HTML and ARIA), and status messages are announced without moving the focus.

In short, robust content remains reliable and usable, whatever the device, browser or assistive technology used.

---

## Chapter 1: Perceivable

This chapter lists all the success criteria of *WCAG 2.2 principle 1 – Perceivable*, with their number, conformance level (A, AA, AAA) and a brief description.

### 1.1 Text Alternatives

- **1.1.1 Non-text Content (A)**: all non-text content has a text alternative that serves the equivalent purpose (decorative content is ignored by assistive technologies).

### 1.2 Time-based Media

- **1.2.1 Audio-only and Video-only (Prerecorded) (A)**: provide a text alternative for prerecorded audio-only content, and a text or audio alternative for prerecorded video-only content.
- **1.2.2 Captions (Prerecorded) (A)**: captions are provided for all prerecorded audio content in synchronised media.
- **1.2.3 Audio Description or Media Alternative (Prerecorded) (A)**: prerecorded videos have an audio description or a full text alternative (transcript).
- **1.2.4 Captions (Live) (AA)**: captions are provided for all live audio content in synchronised media.
- **1.2.5 Audio Description (Prerecorded) (AA)**: an audio description is provided for prerecorded video content in synchronised media.
- **1.2.6 Sign Language (Prerecorded) (AAA)**: sign language interpretation is provided for prerecorded audio content in synchronised media.
- **1.2.7 Extended Audio Description (Prerecorded) (AAA)**: when pauses in the audio are too short for audio description, the video is paused to allow an extended description.
- **1.2.8 Media Alternative (Prerecorded) (AAA)**: a full text alternative is provided for all prerecorded synchronised media and video-only media.
- **1.2.9 Audio-only (Live) (AAA)**: an alternative (for example, live captions or a text transcript) is provided for live audio-only content.

### 1.3 Adaptable

- **1.3.1 Info and Relationships (A)**: structure and relationships between elements (headings, lists, tables, form fields and their labels) are programmatically determinable and understandable by assistive technologies.
- **1.3.2 Meaningful Sequence (A)**: the reading order is logical and can be programmatically determined, independently of the visual presentation.
- **1.3.3 Sensory Characteristics (A)**: instructions do not rely solely on sensory characteristics (shape, colour, size, visual position, orientation or sound).
- **1.3.4 Orientation (AA)**: content is not restricted to a single screen orientation (portrait/landscape), unless a specific orientation is essential.
- **1.3.5 Identify Input Purpose (AA)**: the purpose of fields collecting information about the user (name, email, address, etc.) can be programmatically determined, for example with the `autocomplete` attribute.
- **1.3.6 Identify Purpose (AAA)**: the purpose of interface components, icons and regions can be programmatically determined.

### 1.4 Distinguishable

- **1.4.1 Use of Color (A)**: colour is not the only means of conveying information, indicating an action or distinguishing an element.
- **1.4.2 Audio Control (A)**: audio that plays automatically for more than 3 seconds can be paused or stopped, or its volume controlled independently.
- **1.4.3 Contrast (Minimum) (AA)**: text and images of text have a contrast ratio of at least 4.5:1 with the background (3:1 for large text).
- **1.4.4 Resize Text (AA)**: text can be resized up to 200% without loss of content or functionality.
- **1.4.5 Images of Text (AA)**: real text is used rather than images of text, except for customisable images or where a particular presentation is essential (for example, a logo).
- **1.4.6 Contrast (Enhanced) (AAA)**: contrast of text and images of text raised to 7:1 (4.5:1 for large text).
- **1.4.7 Low or No Background Audio (AAA)**: prerecorded speech has no background sound, or the background can be turned off, or is at least 20 dB quieter than the speech.
- **1.4.8 Visual Presentation (AAA)**: blocks of text can be presented with user-chosen colours, limited line width, no justification, sufficient line spacing, and can be resized without horizontal scrolling.
- **1.4.9 Images of Text (No Exception) (AAA)**: images of text are used only for decoration or where a particular presentation is essential.
- **1.4.10 Reflow (AA)**: content can be presented without loss of information or functionality, and without scrolling in two dimensions, at a width equivalent to 320 CSS pixels.
- **1.4.11 Non-text Contrast (AA)**: user interface components (borders, states, focus indicator) and graphical objects needed to understand the content have a contrast ratio of at least 3:1.
- **1.4.12 Text Spacing (AA)**: no content or functionality is lost when the user increases line height, paragraph spacing, letter spacing and word spacing.
- **1.4.13 Content on Hover or Focus (AA)**: content that appears on hover or focus can be dismissed, can be hovered over, and stays visible until the user dismisses it.

---

## Chapter 2: Operable

This chapter lists all the success criteria of *WCAG 2.2 principle 2 – Operable*, with their number, conformance level (A, AA, AAA) and a brief description.

### 2.1 Keyboard Accessible

- **2.1.1 Keyboard (A)**: all functionality is operable with the keyboard, without requiring specific timings for individual keystrokes.
- **2.1.2 No Keyboard Trap (A)**: keyboard focus can always be moved away from a component using the keyboard alone.
- **2.1.3 Keyboard (No Exception) (AAA)**: all functionality is operable with the keyboard, without exception.
- **2.1.4 Character Key Shortcuts (A)**: keyboard shortcuts made of a single character key can be turned off, remapped, or are active only when the component has focus.

### 2.2 Enough Time

- **2.2.1 Timing Adjustable (A)**: for each time limit, the user can turn it off, adjust it or extend it (with exceptions for real-time events and essential limits).
- **2.2.2 Pause, Stop, Hide (A)**: moving, blinking, scrolling or auto-updating content can be paused, stopped or hidden.
- **2.2.3 No Timing (AAA)**: timing is not an essential part of the event or activity (except non-interactive synchronised media and real-time events).
- **2.2.4 Interruptions (AAA)**: interruptions (alerts, updates) can be postponed or suppressed by the user, except in emergencies.
- **2.2.5 Re-authenticating (AAA)**: when a session expires, the user can continue the activity without losing data after re-authenticating.
- **2.2.6 Timeouts (AAA)**: users are warned of the duration of inactivity that could cause data loss, unless data is preserved for more than 20 hours.

### 2.3 Seizures and Physical Reactions

- **2.3.1 Three Flashes or Below Threshold (A)**: pages contain nothing that flashes more than three times in any one-second period, or the flash is below the general flash and red flash thresholds.
- **2.3.2 Three Flashes (AAA)**: pages contain nothing that flashes more than three times in any one-second period.
- **2.3.3 Animation from Interactions (AAA)**: motion animation triggered by interaction can be disabled, unless the animation is essential.

### 2.4 Navigable

- **2.4.1 Bypass Blocks (A)**: a mechanism is available to bypass blocks of content repeated on several pages (skip link, landmarks, headings).
- **2.4.2 Page Titled (A)**: each page has a title that describes its topic or purpose.
- **2.4.3 Focus Order (A)**: focus order preserves meaning and operability.
- **2.4.4 Link Purpose (In Context) (A)**: the purpose of each link can be determined from its text, or from the link text together with its programmatically determined context.
- **2.4.5 Multiple Ways (AA)**: more than one way is available to locate a page within a set of pages (menu, search, sitemap…).
- **2.4.6 Headings and Labels (AA)**: headings and labels describe topic or purpose.
- **2.4.7 Focus Visible (AA)**: the keyboard focus indicator is visible.
- **2.4.8 Location (AAA)**: information about the user's location within a set of pages is available (breadcrumb, current page indicated).
- **2.4.9 Link Purpose (Link Only) (AAA)**: the purpose of each link can be identified from the link text alone.
- **2.4.10 Section Headings (AAA)**: section headings are used to organise the content.
- **2.4.11 Focus Not Obscured (Minimum) (AA)**: a component that receives keyboard focus is not entirely hidden by author-created content (sticky header, cookie banner…).
- **2.4.12 Focus Not Obscured (Enhanced) (AAA)**: no part of the focused component is hidden by author-created content.
- **2.4.13 Focus Appearance (AAA)**: the focus indicator meets minimum requirements of size and of contrast between the focused and unfocused states.

### 2.5 Input Modalities

- **2.5.1 Pointer Gestures (A)**: functionality that uses multipoint or path-based gestures can also be operated with a single pointer without a path-based gesture.
- **2.5.2 Pointer Cancellation (A)**: functionality operated with a single pointer is not triggered on the down-event alone, or the action can be aborted or undone.
- **2.5.3 Label in Name (A)**: the accessible name of a component with a visible text label contains that visible text.
- **2.5.4 Motion Actuation (A)**: functionality triggered by device or user motion can also be operated through the interface, and motion response can be disabled.
- **2.5.5 Target Size (Enhanced) (AAA)**: pointer targets measure at least 44 × 44 CSS pixels (with exceptions).
- **2.5.6 Concurrent Input Mechanisms (AAA)**: content does not restrict the use of input modalities available on the platform.
- **2.5.7 Dragging Movements (AA)**: functionality that uses dragging can also be achieved with a single pointer without dragging.
- **2.5.8 Target Size (Minimum) (AA)**: pointer targets measure at least 24 × 24 CSS pixels, or have sufficient spacing (with exceptions).

---

## Chapter 3: Understandable

This chapter lists all the success criteria of *WCAG 2.2 principle 3 – Understandable*, with their number, conformance level (A, AA, AAA) and a brief description.

### 3.1 Readable

- **3.1.1 Language of Page (A)**: the default human language of the page can be programmatically determined.
- **3.1.2 Language of Parts (AA)**: the language of each passage in a language other than the page language can be programmatically determined.
- **3.1.3 Unusual Words (AAA)**: a mechanism identifies the definitions of words used in an unusual or restricted way, including idioms and jargon.
- **3.1.4 Abbreviations (AAA)**: a mechanism identifies the expanded form or meaning of abbreviations.
- **3.1.5 Reading Level (AAA)**: when text requires a reading ability more advanced than lower secondary education level, supplemental content or a simpler version is available.
- **3.1.6 Pronunciation (AAA)**: a mechanism identifies the pronunciation of words whose meaning is ambiguous without it.

### 3.2 Predictable

- **3.2.1 On Focus (A)**: receiving focus does not initiate a change of context.
- **3.2.2 On Input (A)**: changing the setting of a component does not automatically cause a change of context, unless the user has been advised beforehand.
- **3.2.3 Consistent Navigation (AA)**: navigation mechanisms repeated on several pages occur in the same relative order.
- **3.2.4 Consistent Identification (AA)**: components with the same functionality are identified consistently across pages.
- **3.2.5 Change on Request (AAA)**: changes of context are initiated only by user request, or a mechanism is available to turn them off.
- **3.2.6 Consistent Help (A)**: help mechanisms (contact details, contact form, chat, FAQ) repeated on several pages appear in the same relative order.

### 3.3 Input Assistance

- **3.3.1 Error Identification (A)**: when an input error is automatically detected, the item in error is identified and the error is described to the user in text.
- **3.3.2 Labels or Instructions (A)**: labels or instructions are provided when content requires user input.
- **3.3.3 Error Suggestion (AA)**: when an input error is detected and suggestions for correction are known, they are provided to the user (unless this would jeopardise security or purpose).
- **3.3.4 Error Prevention (Legal, Financial, Data) (AA)**: for submissions with legal or financial consequences, or that modify or delete data, the submission is reversible, checked, or confirmed by the user.
- **3.3.5 Help (AAA)**: context-sensitive help is available.
- **3.3.6 Error Prevention (All) (AAA)**: the same protection as 3.3.4 applies to all submissions of information.
- **3.3.7 Redundant Entry (A)**: information already entered by the user in the same process is auto-populated or available for selection, rather than having to be entered again.
- **3.3.8 Accessible Authentication (Minimum) (AA)**: no step of an authentication process relies on a cognitive function test (remembering a password, solving a puzzle) unless an alternative or assistance mechanism is available (password managers, copy-paste, object recognition…).
- **3.3.9 Accessible Authentication (Enhanced) (AAA)**: same as 3.3.8, without the object-recognition and personal-content exceptions.

---

## Chapter 4: Robust

This chapter lists all the success criteria of *WCAG 2.2 principle 4 – Robust*, with their number, conformance level (A, AA, AAA) and a brief description.

### 4.1 Compatible

- **4.1.1 Parsing**: obsolete and removed in WCAG 2.2 (it is considered always satisfied for HTML and XML content).
- **4.1.2 Name, Role, Value (A)**: for all user interface components, the name and role can be programmatically determined; states, properties and values can be set programmatically, and changes are notified to assistive technologies.
- **4.1.3 Status Messages (AA)**: status messages (confirmation, error, progress, search results) can be programmatically determined, so that assistive technologies can announce them without moving the focus.

---

## WCAG Conformance

#### Official conformance framework and formal requirements

Conformance defines **how web content can be claimed to conform to WCAG** and under which conditions.
It does not concern user experience alone, but the **measurable satisfaction of the success criteria**.

### Conformance levels

Conformance is structured into three hierarchical levels:

- **Level A**: minimum requirements essential for accessibility.
- **Level AA**: intermediate level, generally required by regulations (e.g. public procurement).
- **Level AAA**: highest level. WCAG does not recommend requiring Level AAA conformance as a general policy for entire sites, because some content cannot satisfy all AAA criteria.

👉 To conform at Level AA, **all Level A and AA criteria must be satisfied** (or a conforming alternate version must be provided).

### The 5 conformance requirements

For a page to conform, WCAG 2.2 (section 5.2) sets **5 requirements**, all mandatory:

#### 1. Conformance level

One of the levels (A, AA or AAA) is **met in full**: the page satisfies all the success criteria of that level and of the levels below, or a conforming alternate version is provided.

#### 2. Full pages

Conformance applies to **the entire page**, not to an isolated part of it.

- If a section does not conform, the page as a whole does not conform.
- Integrated third-party components (widgets, external modules) are part of the page. If they cannot be fixed, the author can only make a *statement of partial conformance* for third-party content.

#### 3. Complete processes

When a service involves several steps (e.g. online order, registration, payment),
**all the steps must conform** at the claimed level.

A single non-conforming screen invalidates the whole process.

#### 4. Only accessibility-supported ways of using technologies

Only ways of using technologies that are:

- supported by users' assistive technologies (screen readers, keyboard navigation, etc.),
- and correctly implemented

can be relied on to satisfy the success criteria. Any information or functionality provided in another way must also be available in an accessibility-supported way.

#### 5. Non-interference

Content that does not conform is tolerated **only if it does not block access to the rest of the page**. Four criteria apply to all content without exception: 1.4.2 Audio Control, 2.1.2 No Keyboard Trap, 2.3.1 Three Flashes or Below Threshold and 2.2.2 Pause, Stop, Hide.

Example:

- A decorative animation must not prevent keyboard navigation.
- An inaccessible script must not trap a screen reader user.

#### Key points to remember

- WCAG conformance is **formal and verifiable**.
- It applies to a full page or to a complete process.
- Level AA is today the most common regulatory standard.
- Integrating third-party components does not remove the author's responsibility: they are part of the page.
- A conformance claim is optional in WCAG; when one is made, it must contain the required information and be transparent and documented.

---

## Conformance Statement and Regulatory Framework

### Official accessibility statement

#### Role and purpose

The accessibility statement is a public document that:

- informs users of the actual level of accessibility of the service,
- states the reference used (WCAG, EN 301 549, RGAA, eCH-0059, etc.),
- indicates the conformance status reached,
- details any non-conformities and the accessible alternatives,
- provides a contact and feedback mechanism to report a problem.

In the European Union, it is mandatory for the websites and mobile applications of **public sector bodies** (Directive (EU) 2016/2102), on the basis of a model set by Implementing Decision (EU) 2018/1523.

#### Recommended minimum content

A statement should include:

##### 1. Reference used

- Version of the standard applied (e.g. **WCAG 2.2**, or **EN 301 549**)
- Or national reference (e.g. **RGAA** in France, **eCH-0059** in Switzerland)

##### 2. Compliance status

- Fully compliant
- Partially compliant
- Not compliant

##### 3. Evaluation

- Date of the evaluation
- Method used (self-assessment or third-party evaluation)
- Testing tools

##### 4. Non-accessible content

- Precise list of criteria not met
- Possible justification (disproportionate burden, third-party content, content outside the scope, etc.)

##### 5. Contact mechanism

- Email or form to report a problem or request inaccessible content

##### 6. Enforcement procedure

- Information on the authority to contact if no satisfactory answer is received

#### Key points to remember

- The statement is public: it commits the organisation to the accessibility it describes.
- It must be kept up to date.
- It does not replace actual conformance: it documents it.

### Legal implications and regulatory frameworks

#### National references

WCAG is an international standard of the **World Wide Web Consortium**,
but legal obligations depend on national (and European) legislation.

In France:

- The official reference is the **Référentiel général d'amélioration de l'accessibilité (RGAA)**.
- It is mandatory for:
    - public services,
    - public service delegates,
    - certain large companies.

The current version, **RGAA 4.1.2**, is based on WCAG 2.1 Levels A and AA. **RGAA 5** is being drafted, with publication planned for the end of 2026.

#### European framework

The **European Accessibility Act** (EAA, Directive (EU) 2019/882):

- Harmonises accessibility requirements for certain products and services across the European Union, including in the private sector.
- Applies in particular to:
    - e-commerce services,
    - consumer banking services,
    - electronic communications services, e-books and some passenger transport services.
- Applies since **28 June 2025**.

The **Web Accessibility Directive** (Directive (EU) 2016/2102) covers the websites and mobile applications of public sector bodies.

Both directives rely on the harmonised European standard **EN 301 549**, whose web requirements take over the **WCAG Level A and AA** success criteria.

#### Swiss framework

**LHand and eCH-0059 (Switzerland)**:

- The federal law on the elimination of discrimination against people with disabilities (**LHand**, SR 151.3, in force since 1 January 2004) states in Article 14(2) that, where authorities offer their services on the Internet, access to these services must not be made difficult for people with visual impairments. Its implementing ordinance (**OHand**, SR 151.31) extends this to information and services for people with speech, hearing, visual or motor disabilities.
- Since 2004, the administrative units of the **Confederation** have been required to make their Internet and intranet content accessible.
- The technical requirements are set by the **eCH-0059 Accessibility Standard V3.0**, based on **WCAG 2.1** and covering websites and mobile applications. It is a binding IT directive for the federal administration, and federal accessibility statements state that it requires **WCAG 2.1 Level AA**.
- For cantons and communes, obligations depend on cantonal law; many align with eCH-0059.

#### Risks of non-conformity

Depending on the country and the framework:

- Administrative sanctions
- Financial penalties (for example, those set by EU Member States for the EAA)
- Legal disputes
- Damage to brand image
- Exclusion from public procurement

#### Project impact (Product / QA / Governance)

WCAG conformance is not only a development matter:

- **Product**: integrate the criteria from the design phase.
- **UX/UI**: respect contrast, focus and navigation.
- **Development**: accessible technical implementation.
- **QA**: systematic manual + automated testing.
- **Legal / compliance**: publication and updating of the statement.

#### Key points to remember

- WCAG is a technical standard; laws and national standards make it mandatory.
- The accessibility statement is a formal regulatory requirement for the public sector in the EU.
- Level AA is today the dominant legal reference in Europe and in Switzerland.
- Accessibility is a cross-cutting organisational responsibility.

---

## Theoretical Conformance vs Actual Accessibility

### WCAG conformance: normative approach

WCAG conformance is:

- Based on **measurable success criteria**
- Verifiable by audit
- Structured by levels (A, AA, AAA)
- Documentable through a conformance claim and an accessibility statement

It answers the question:

> "Does the site formally meet the criteria defined by WCAG?"

An application can conform at Level AA according to **WCAG 2.2** while still presenting usability difficulties that the criteria do not explicitly cover.

### Actual accessibility: experiential approach

Actual accessibility concerns:

- The real experience of a user with a disability
- Overall ergonomics
- Smoothness of user journeys
- Cognitive load
- Robustness in real-world conditions (screen reader, zoom, keyboard navigation, etc.)

It answers the question:

> "Can a user really complete their task without significant obstacles?"

### Limits of formal conformance

Even with AA conformance:

- Navigation can be technically correct but inefficient.
- A form can conform but be cognitively complex.
- An ARIA structure can be valid but poorly interpreted by some screen readers.
- Micro-interactions can greatly slow down keyboard use.

WCAG defines a **minimum baseline**, not a guarantee of UX excellence.

### Concrete examples of the gap

| Conforms to the criteria | But in practice |
|---|---|
| All fields have a label | The form has 25 ungrouped fields |
| Contrast meets 4.5:1 | The interface is visually overloaded |
| Keyboard navigation works | The tab order is long and inefficient |
| Errors are announced | The messages are too technical |

### Good practices to reduce the gap

#### 1. Real user testing

Include:

- screen reader users,
- 100% keyboard navigation,
- users with cognitive impairments.

#### 2. Hybrid audit

- Automated tests (axe, Lighthouse)
- Expert manual audit
- Tests in real conditions

#### 3. Continuous integration

- Accessibility from design (accessible Design System)
- Systematic QA review
- Non-regression in releases

### Key points to remember

- WCAG conformance is necessary but not sufficient.
- Actual accessibility goes beyond simply validating the criteria.
- A mature strategy combines normative conformance and experiential validation.
- Accessibility must be integrated as a product requirement, not only as a legal constraint.

---

## WCAG Version History

**WCAG** have evolved over the years to better meet users' needs and the technological evolution of the web:

- **WCAG 2.0 (11 December 2008)**: sets the foundations of digital accessibility, defining the four fundamental principles (Perceivable, Operable, Understandable, Robust) and the associated success criteria.
- **WCAG 2.1 (5 June 2018)**: extends version 2.0 with **1 new guideline (2.5 Input Modalities) and 17 new success criteria**, notably for **mobile devices**, low vision and cognitive disabilities.
- **WCAG 2.2 (5 October 2023, updated 12 December 2024)**: latest version, which adds **9 new success criteria** and removes criterion **4.1.1 Parsing**. The new criteria mainly help people with **cognitive disabilities**, people with **motor impairments**, people who cannot use a mouse, and people with **low vision**. WCAG 2.2 is backwards compatible: content that conforms to 2.2 also conforms to 2.1 and 2.0.
- **WCAG 3**: an early draft, not yet a standard. The W3C recommends meeting WCAG 2.2 in the meantime.

---

## Sources

- W3C — [Web Content Accessibility Guidelines (WCAG) 2.2](https://www.w3.org/TR/WCAG22/) (normative: principles, guidelines, success criteria, conformance requirements in section 5.2)
- W3C — [Understanding Conformance (WCAG 2.2)](https://www.w3.org/WAI/WCAG22/Understanding/conformance) (informative)
- W3C WAI — [WCAG 2 Overview](https://www.w3.org/WAI/standards-guidelines/wcag/) and [What's New in WCAG 2.2](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-22/) (informative)
- W3C — [Règles pour l'accessibilité des contenus Web (WCAG) 2.2, authorised French translation](https://www.w3.org/Translations/WCAG22-fr-20260922/)
- European Commission — [Web Accessibility (Directive (EU) 2016/2102)](https://digital-strategy.ec.europa.eu/en/policies/web-accessibility) (official)
- EUR-Lex — [Directive (EU) 2019/882 — European Accessibility Act](https://eur-lex.europa.eu/eli/dir/2019/882/oj) (official)
- DINUM — [Accessibilité numérique — RGAA](https://accessibilite.numerique.gouv.fr/) (official)
- Fedlex — [LHand, SR 151.3](https://www.fedlex.admin.ch/eli/cc/2003/667/fr) (official)
- BFEH — [Livingdocs: checklist for accessible content (LHand, OHand, eCH-0059)](https://www.ebgb.admin.ch/dam/fr/sd-web/G5Au8IXxycUv/Livingdocs%20%20liste%20de%20contr%C3%B4le%20pour%20contenus%20accessibles%20v2.1.pdf) (official)
- eCH — [eCH-0059 Accessibility Standard V3.0](https://www.ech.ch/de/ech/ech-0059/3.0) (official); Federal Department of Foreign Affairs — [Accessibility statement](https://www.eda.admin.ch/en/accessibility-statement) (official)
