# EXP-2026-06-13 Deployment Retrospective

## Experiment Goal

The goal of this experiment was to move the Commercial Website Prototype from a local development environment to a publicly accessible cloud deployment.

The application was built with Next.js, React, and TypeScript and deployed through a platform connected to the GitHub repository.

## Initial State

Before deployment, the application worked locally and included:

* A contact form user interface
* Validation logic implemented with the Strategy design pattern
* A design contract in `docs/DESIGN.md`
* A Next.js frontend connected to the validation module
* BDD requirements and Mermaid architecture documentation

## Deployment Process

The deployment process included the following steps:

1. Verified that the application worked with `npm run dev`.
2. Tested the production build using `npm run build`.
3. Corrected dependency version conflicts.
4. Added a `.gitignore` file.
5. Removed `node_modules` and build files from Git tracking.
6. Pushed the corrected project to the `main` branch.
7. Connected the GitHub repository to the cloud hosting platform.
8. Tested the deployed application through its public URL.

## Problems Encountered

### Committed `node_modules`

The first push included the `node_modules` directory because the repository did not have a `.gitignore` file.

GitHub rejected the push because some Next.js binary files were larger than GitHub's 100 MB file limit.

The issue was fixed by:

* Creating a `.gitignore`
* Excluding `node_modules`
* Removing generated dependencies from Git tracking
* Keeping only `package.json` and `package-lock.json`

This showed that generated dependencies must never be committed to the repository.

### Node.js Version Mismatch

The initial environment used Node.js 18.19.1, while the installed Next.js version required Node.js 20.9 or newer.

The issue was fixed by using Node.js 20 and documenting the required runtime version.

This demonstrated that source code alone is not enough for reproducibility. The runtime environment must also be controlled.

### Dependency Version Conflict

The project initially mixed incompatible versions:

* Next.js 16
* React 18
* ESLint 8
* `eslint-config-next` 16

The dependency tree could not be installed because `eslint-config-next` required a newer ESLint version.

The project was stabilized using compatible versions:

* Next.js 14.2.35
* React 18.3.1
* React DOM 18.3.1
* ESLint 8.57.1
* `eslint-config-next` 14.2.35
* TypeScript 5.5.4

After aligning the dependency versions, installation and production builds succeeded.

## AI Evaluation

The AI was useful for:

* Generating deployment instructions
* Identifying dependency conflicts
* Explaining GitHub's large-file rejection
* Producing configuration suggestions
* Structuring troubleshooting steps

However, the AI-generated project setup still required human verification.

Some recommendations initially mixed incompatible dependency versions. This showed that AI output must be tested instead of accepted as automatically correct.

## Hallucinations and Assumptions

The biggest risk was not fabricated application logic, but incorrect assumptions about the development environment.

The AI could not automatically know:

* Which Node.js version was active
* Whether `node_modules` was tracked
* Whether the local and remote repositories matched
* Which package versions were already installed
* Whether the deployment platform used the same runtime configuration

Commands such as `node --version`, `npm list`, `git status`, and `npm run build` were necessary to verify the real state of the project.

## Overengineering Reflection

The Strategy pattern introduced more files and abstractions than a small contact form strictly required.

For the current MVP, a single validation function could have been simpler.

However, the pattern made each validation rule independent and demonstrated how the module could support additional rules later. The pattern was valuable as an architectural exercise, but it should only be retained if the application continues to grow.

## Main Lessons

The most important lessons were:

* AI-generated code is only a starting point.
* Precise requirements improve the quality of generated code.
* Design patterns can improve structure but can also introduce unnecessary complexity.
* Dependency versions must be deliberately aligned.
* Generated files and dependencies must be excluded from Git.
* A successful local development server does not guarantee a successful production build.
* Deployment is part of software engineering, not a separate final step.
* The software engineer remains responsible for architecture, validation, testing, security, and deployment decisions.

## Future Role of the Software Engineer

The future software engineer will spend less time writing every line manually and more time:

* Defining contracts and constraints
* Designing architecture
* Reviewing AI-generated code
* Testing assumptions
* Managing dependencies
* Protecting maintainability
* Verifying production behavior

AI can generate implementations quickly, but the engineer must ensure that the implementation is correct, maintainable, reproducible, and aligned with the product requirements.

## Result

The application was successfully built and deployed to a public cloud platform.

The experiment demonstrated that AI can accelerate development, but successful delivery still depends on disciplined engineering practices and human oversight.

