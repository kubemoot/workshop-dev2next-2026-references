# What makes an ADL specification well formed

ADL, the Architecture Definition Language, states an architecture as rules a reviewer
or a tool can check. A specification is a list of definitions and the rules inside
them. This page is the checklist a reviewer works through. Written for this workshop,
Apache License 2.0.

## The forms

| Form | Meaning |
|---|---|
| `DEFINE SYSTEM <name>` | The system the specification describes. One per specification. |
| `DEFINE COMPONENT <name>` | A part of the system. Rules that follow belong to it until the next DEFINE. |
| `DESCRIPTION <text>` | One line saying what the thing just defined is for. |
| `ALWAYS <action>` | A rule the component always follows. |
| `NEVER <action>` | Something the component never does. |
| `WHEN <condition> THEN <action>` | A rule that applies when the condition holds. |
| `ASSERT <invariant>` | A statement about the system that must hold; it names the components it constrains. |

## The checks

1. **Every DEFINE has a DESCRIPTION.** The line after each `DEFINE SYSTEM` and `DEFINE
   COMPONENT` is its `DESCRIPTION`. A definition without one leaves its purpose to
   guesswork, and a rule cannot be judged against a purpose nobody wrote down.
2. **Every name an ASSERT uses is defined.** An `ASSERT` constrains components by name;
   each of those names must appear in a `DEFINE COMPONENT` in the same specification.
   An ASSERT about an undefined component has nothing to attach to and cannot be
   enforced.
3. **No rule contradicts a NEVER in the same component.** A `WHEN ... THEN` or `ALWAYS`
   that does what a `NEVER` in the same component forbids makes the component
   impossible to build as written. Read each NEVER against every other rule of its
   component.
4. **One behaviour per line.** A rule that says two things cannot be checked as one.
5. **Rules name real counterparts.** A rule that mentions another component names one
   the specification defines, or an external system it says is external.

## Reporting a problem

Quote the line, name the check it breaks, and say what would fix it. Report each
problem once. A specification that passes every check has no problems to report, and
saying so is a finding too.
