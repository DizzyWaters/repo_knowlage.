# EXP-2026-06-12 Pattern Implementation

## Experiment Goal

The goal of this experiment was to test whether an AI assistant could implement the selected contact form validation feature using a classical GoF design pattern while keeping the code modular and maintainable.

## Selected Feature

Contact form validation.

## Selected Pattern

Strategy Pattern.

## Why This Pattern Was Chosen

The feature has multiple validation rules:

- Required name.
- Required email.
- Required message.
- Valid email format.

Each rule can be represented as a separate strategy. This allows the module to be extended later without rewriting one large validation function.

## Prompt Provided to AI

```text
You are working in a TypeScript commercial website prototype.

Before implementing, follow these repository rules:
- Read AGENTS.md.
- Keep the code understandable for a student-level software engineering project.
- Use TypeScript.
- Use meaningful names.
- Keep functions small and focused.
- Do not add unnecessary dependencies.
- Update documentation when architecture changes.

Selected feature:
Contact form validation.

User story:
As a website visitor, I want to submit a contact form with my name, email address, and message, so that I can send an inquiry to the business without using external communication tools.

Acceptance criteria:
1. Given the visitor has entered a non-empty name, a valid email address, and a non-empty message, when the contact form is validated, then the form input should be accepted as valid.
2. Given the visitor leaves one or more required fields empty, when the contact form is validated, then the form input should be rejected and an error message should be returned for each missing required field.
3. Given the visitor enters an email address in an invalid format, when the contact form is validated, then the form input should be rejected and an email validation error should be returned.

Task:
Implement the business logic for this feature using the Strategy design pattern.

Required structure:
Create a dedicated module at:
src/features/contact-validation/

The module must include:
- Contact form input types.
- Validation result types.
- A ValidationStrategy interface.
- RequiredFieldStrategy.
- EmailFormatStrategy.
- ContactFormValidator as the context that runs strategies.
- A factory function that creates the default validator.
- A simple exported validateContactForm function for UI usage.
- A README.md explaining the pattern choice and module interaction.

Strict constraints:
- Do not call an API.
- Do not modify UI state.
- Do not use browser storage.
- Do not submit the form.
- Do not add dependencies.
- Keep validation predictable and deterministic.
```

## Result Evaluation

The AI applied the Strategy Pattern accurately.

The implementation contains:

- A `ValidationStrategy` interface.
- Separate strategy classes for required fields and email format validation.
- A `ContactFormValidator` context that runs the strategies.
- A factory function that assembles the default strategies.
- A simple public `validateContactForm` function for UI components.

## Did the Pattern Help?

Yes. The Strategy Pattern helped clarify the code because each validation rule became independent and easy to understand.

The pattern also creates a clear extension point. For example, a future `MessageLengthStrategy` could be added without changing the existing required-field or email-format validation rules.

## Did It Cause Overengineering?

There is a small amount of extra structure compared with one simple pure function.

For a very small project, one function would be enough. However, for this course task, the Strategy Pattern is justified because the objective is to practice module design and create an architectural harness for AI-assisted development.

The implementation avoids excessive overengineering because it uses only one main pattern, no external dependencies, and a small number of files.

## Requirement Adjustments

The original feature remains the same. The main scope adjustment is that this implementation only covers validation logic. It does not include form submission, API calls, database storage, or UI state management.

## Conclusion

The experiment showed that a design pattern can help guide AI-generated code toward a cleaner structure. The Strategy Pattern made the validation module easier to extend and prevented the logic from becoming one large conditional block.
