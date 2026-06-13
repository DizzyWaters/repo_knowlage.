# EXP-2026-06-12 Spec-Driven UI

## Experiment Goal

The goal of this experiment was to test whether a strict design contract could guide an AI assistant to generate a usable frontend interface without producing generic, inaccessible, or inconsistent UI code.

The UI had to connect to the existing contact form validation module from the Product Repository.

## Selected Feature

Contact form validation for the Commercial Website Prototype.

## Design Contract Used

The AI assistant was given `docs/DESIGN.md` as the design contract.

The contract defined:

- Framework choice: React + TypeScript with Next.js App Router.
- Color palette with exact hex values.
- Typography and spacing rules.
- Button, form, and card component rules.
- Accessibility rules.
- Prohibited output, including generic dashboard UI and duplicated validation logic.

## Prompt Provided to AI

```text
You are working in my Product Repository for a commercial website prototype.

Task:
Generate a frontend UI for the existing Contact Form Validation feature.

Context:
- Follow `docs/DESIGN.md` strictly.
- The existing business logic is in `src/features/contact-validation`.
- The UI must import and call `validateContactForm` from that module.
- The validation module already uses the Strategy Pattern. Do not rewrite the validation logic inside the UI.

Framework:
- Use React + TypeScript.
- Use Next.js App Router.
- Use plain CSS in `src/app/globals.css`.

Requirements:
1. Create a contact form UI with fields for name, email, and message.
2. Add a submit/validate button.
3. On button click or form submit, call `validateContactForm`.
4. If validation fails, display returned validation errors beside the correct fields.
5. If validation succeeds, display a success message.
6. Do not call an API.
7. Do not store data in localStorage or a database.
8. Keep the React component small and readable.
9. Use semantic and accessible HTML.
10. Follow all colors, spacing, typography, component, and accessibility rules from `docs/DESIGN.md`.

Expected output:
- `src/components/ContactFormSection.tsx`
- `src/app/page.tsx`
- `src/app/layout.tsx`
- `src/app/globals.css`
- Any minimal config files required to run the Next.js prototype.
```

## Result

The AI succeeded in creating a frontend UI that connected to the existing validation module.

The generated UI used a React form component and called `validateContactForm` when the form was submitted. The UI displayed field-level validation errors and a success message when the input passed validation.

## Did the AI Follow DESIGN.md?

Mostly yes.

The useful parts of the design contract were the exact color palette, the component rules, and the accessibility constraints. These reduced the chance of generic styling and helped prevent the common problem where the AI produces a default blue dashboard layout.

The AI followed these constraints well:

- Used the specified primary color `#2563EB`.
- Used the specified background and surface colors.
- Created a card-style form with rounded corners and visible borders.
- Used semantic form elements.
- Added visible labels for every input.
- Connected errors to inputs with accessibility attributes.

## Number of Prompts Needed

It took one main prompt to generate the first working version.

A small review step was still needed to verify that the UI called the existing module instead of duplicating validation logic. The final version imports `validateContactForm` from the contact validation feature module.

## Was the UI Accessible and Structurally Sound?

Yes, for a prototype.

The UI uses:

- `main`, `section`, `form`, `label`, `input`, `textarea`, and `button` elements.
- Visible labels instead of placeholder-only labels.
- `aria-invalid` for invalid fields.
- `aria-describedby` to connect field errors to inputs.
- `role="alert"` and `aria-live` for validation feedback.
- Clear focus states.

## Did SDD Help?

Yes.

The design contract made the AI output more controlled. Instead of asking the AI to "build a contact form" in a vague way, the prompt constrained visual style, accessibility, and module integration.

The strongest benefit was that the UI connected to the existing Strategy Pattern validation module instead of creating new validation rules inside the component.

## Overengineering Check

This task did not create unnecessary complexity.

The UI is still simple:

- One React form component.
- One page that renders the component.
- One global CSS file.
- The existing validation module remains separate.

The structure is more maintainable than mixing validation, styling, and business rules in one place.

## Conclusion

Spec-Driven Development improved the AI-generated UI. The `DESIGN.md` file acted as a frontend harness, while the existing Strategy Pattern module acted as the backend/business-logic harness.

Together, they helped produce a more maintainable and reviewable result than a vague UI prompt would have produced.
