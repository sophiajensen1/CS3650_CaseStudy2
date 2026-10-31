# CS3650_CaseStudy2
Case Study 02: Interactive Prototype Specification
Sophia Solon


## Step 1: Interaction Mechanics & Input Paradigm Mapping
In Phase 1 of my project, all 3 test participants said appointment booking was the most difficult task. This included confusing verbiage, unclear steps, and 

My redesign breaks booking into 5 clear steps:
1. Choose a service. Plain english options.
2. Choose an office. Clearly identifies which offices are available to book vs walk in.
3. Choose a date and time. In a smart, familiar calendar layout.
4. Enter contact information and review. With error indication and instructions.
5. Booking confirmation.

## Step 2: High-Fidelity Prototyping & Micro-Interaction Design
Mouse: Click buttons, fields, and selection cards.
Touch: Tap the same controls as a mouse. 
Keyboard: Tab to move between controls. Arrow keys move through radio choices. Space selects choice. Enter activates choice/screen next. 
Screen Reader: Read labels, choices, instructions, and errors. 

Keyboard focus paths:
-Service: Service choices > Continue
-Office: Search field > Search > Office choices > Continue
-Date and Time: Date choices > Time choices > Continue
-Details and review: Name > Email > Change options > Book
-Confirmation: Confirmation heading

Changing an office clears previous data and time selection. 
Going back saves information.


# Fitts Law Target Sizing
Continue, Back, Search, and Book buttons: At least 48x48 px
Service and office cards: Full card is clickable, at least 48 px tall
Date tiles & time cards: at least 48x48 px
Contact fields: at least 48px tall
Change actions: at least 48x48px clickable area

Targets next to each other should have at least 8px of space between them.

## Wireframes
[View the Figma design](https://www.figma.com/design/bUafh85D3lDC3oB4IlIQnD/DMV-Booking-Prototype)

## Prototype
[Open the interactive prototype](https://www.figma.com/proto/bUafh85D3lDC3oB4IlIQnD/DMV-Booking-Prototype?node-id=20-236&scaling=scale-down&content-scaling=fixed&page-id=0%3A1)


# State Transition Definitions

-Default/resting: Clear labels, visible borders, and readable instructions. 
-Hover/Pointer-over: Buttons & selectable cards darken on hover. 
-Focus: A high-contract outline identifies focused control. 
-Active/Pressed: Buttons change appearance while pressed, selected options show a filled radio, filled color, and stronger border.
-Disabled/unavailable choices: include clear explanations like "Booked", X indicators, or grey out color. 
-Loading/System Processing: Spinner and "Loading available times..." or "Booking appointment..."
-Error/Validation alert: Show error summary banner, inline messages, and highlighted fields. Use contrasting red color. 


## Step 3: Accessibility Architecture & WCAG Specification
 Semantic HTML Markup

-Service: <section> containing <form>, <fieldset>, <legend>, radio choices, and continue button
-Office: <section> contains a form with labeled search field, search button, and office-choice fieldset
-Date and Time: <section> contains a form with separate fieldsets and legends for date and time choices
-Details and review: <section> contains a form with labeled contact fields and submission button
-Confirmation: <section> contains heading, appointment details, and preparation items list.

# ARIA and Screen Reader Hooks
-Labels: Connect each <label> to its input
-Instructions and errors: Use 'aria-describedby' to associate them with the field
-Invalid fields: set 'aria-invalid="true"' for the active step
-Progress: Update 'aria-current="step"' for active step
-Loading: Use a persistent 'aria-live="polite"' region and 'aria-busy="true"' on the results container
-Booking failure: Use 'aria-live="assertive"' to announce the failure and retry instruction

 # Visual Accessibility

 Contrast requirements:
 -Normal text: at least 4.5:1
 -Large text: at least 3:1
 -Meaninful control boundaries and indicators: 3:1

Body text on white: 16.49:1
Helper text on white: 7.58:1
White button text on navy: 12.46:1
Green Availability text on its background: 6.52:1
Error text on light red: 5.75:1
Grey text on grey background: 6.06:1


## Step 4: Technical Specification Deck Compilation


# Post-Mortem Reflection (Metacognition)

How did explicitly defining every component state (Hover, Focus, Active, Loading, Error) during the specification phase prevent dynamic usability bugs that static wireframes completely fail to address?

I initially did not consider what loading screens might look like, but then thought about how slow the DMV website generally is and realized that was actually necessary. 

Describe a scenario in your prototype where system latency or asynchronous data processing required specialized micro-interaction feedback (e.g., loading skeletons or aria-live announcements). How does your design keep the user informed and prevent repeated submission errors?

 The date and time step displays "Loading available times..." while availability is retrieved. A screen reader announcement would give the same information without requiring the user to see a spinner or other loading animation. 

 During booking, the interface displays a "booking appointment..." message and blocks additional button clicks indications. If booking fails, there is an error view as well prompting the user to re-enter information and try again. This keeps users informed and from clicking submission buttons repeatedly. 









