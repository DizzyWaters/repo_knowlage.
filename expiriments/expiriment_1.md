# EXP-2026-06-12 Pure Function Experiment

## Experiment Goal

The goal of this experiment was to test whether an AI assistant could generate clean feature logic when given a small engineering harness made from BDD requirements and a Mermaid architecture diagram.

## Selected Feature

Contact form validation for the Commercial Website Prototype.

## Prompt Provided to AI

````text
You are helping me implement one small feature for a TypeScript commercial website prototype.

Feature: Contact Form Validation

User Story:
As a website visitor, I want to submit a contact form with my name, email address, and message, so that I can send an inquiry to the business without using external communication tools.

Acceptance Criteria:

AC1: Valid contact form input
Given the visitor has entered a non-empty name, a valid email address, and a non-empty message
When the contact form is validated
Then the form input should be accepted as valid

AC2: Missing required fields
Given the visitor leaves one or more required fields empty
When the contact form is validated
Then the form input should be rejected and an error message should be returned for each missing required field

AC3: Invalid email format
Given the visitor enters an email address in an invalid format
When the contact form is validated
Then the form input should be rejected and an email validation error should be returned

Architecture diagram:

```mermaid
flowchart TD
    A[Visitor opens contact section] --> B[Visitor enters name, email, and message]
    B --> C[Validate contact form input]

    C --> D{Are all required fields filled?}
    D -- No --> E[Return validation errors for missing fields]
    D -- Yes --> F{Is email format valid?}

    F -- No --> G[Return email validation error]
    F -- Yes --> H[Return valid result]

    E --> I[Display errors in UI]
    G --> I
    H --> J[Allow form submission]
````

Strict constraint:
Write the logic for this feature as a Pure Function. It must have no side effects, be stateless, and return a predictable output. Do not call APIs, do not modify UI state, and do not use global variables.

````

## AI Output

```ts
export type ContactFormInput = {
  name: string;
  email: string;
  message: string;
};

export type ContactFormErrors = Partial<Record<keyof ContactFormInput, string>>;

export type ContactFormValidationResult =
  | {
      isValid: true;
      data: ContactFormInput;
      errors: {};
    }
  | {
      isValid: false;
      data: ContactFormInput;
      errors: ContactFormErrors;
    };

export function validateContactForm(
  input: ContactFormInput
): ContactFormValidationResult {
  const data: ContactFormInput = {
    name: input.name.trim(),
    email: input.email.trim(),
    message: input.message.trim(),
  };

  const errors: ContactFormErrors = {};

  if (data.name.length === 0) {
    errors.name = "Name is required.";
  }

  if (data.email.length === 0) {
    errors.email = "Email is required.";
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(data.email)) {
    errors.email = "Email must be in a valid format.";
  }

  if (data.message.length === 0) {
    errors.message = "Message is required.";
  }

  if (Object.keys(errors).length > 0) {
    return {
      isValid: false,
      data,
      errors,
    };
  }

  return {
    isValid: true,
    data,
    errors: {},
  };
}
````

## Result

The AI succeeded in writing a pure function on the first try.

The generated function is pure because:

* It only depends on the input argument.
* It does not call an API.
* It does not modify UI state.
* It does not use global variables.
* It always returns the same output for the same input.
* It returns validation data instead of performing form submission directly.

## Requirement Adjustment

No major adjustment was needed.

However, the BDD requirements helped keep the AI focused. Without the acceptance criteria, the AI might have mixed validation logic with UI logic or form submission logic.

## Conclusion

The experiment showed that a small engineering harness improves AI output quality. The BDD requirements defined expected behavior, the Mermaid diagram defined the logic flow, and the pure-function constraint prevented side effects and unnecessary implementation details.

