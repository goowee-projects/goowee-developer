---
name: goowee-developer
description: |
  Expert knowledge for developing Goowee full-stack applications using Groovy and Grails.
  Covers architecture, UI (Goowee), business logic, security, and advanced features.
  Use this skill when building or modifying Goowee applications, UI components, services, or system configuration.
version: 1.0.0
tags:
  - groovy
  - grails
  - goowee
  - fullstack
  - enterprise
  - backend
  - low-code
---

# Goowee Developer Skill

## When to use this skill
Use this skill when the task involves:
- Initializing or modifying a Goowee application
- Designing UI in controllers with Goowee Elements (ContentTable, ContentForm, etc.)
- Implementing business logic with GORM / Grails services
- Configuring security (Spring Security / roles / permissions)
- Customizing application UI or behavior

---

## Initialize the application
See the reference documentation to initialize the application.

## Create a CRUD
To create a CRUD, create the following:
- [ ] Create a domain class.
- [ ] Create a service.
- [ ] Create a controller.

## Create a Domain Class
See the reference documentation to create a domain class.
IMPORTANT: Verify with the Compliance Checklist and correct if needed

## Create a Service
See the reference documentation to create a service.
IMPORTANT: Verify with the Compliance Checklist and correct if needed

## Create a Controller
See the reference documentation to create a controller.
IMPORTANT: Verify with the Compliance Checklist and correct if needed

### Contents
See the reference documentation for the available contents.
IMPORTANT: Verify with the Compliance Checklist and correct if needed

### Components
See the reference documentation for the available components.
IMPORTANT: Verify with the Compliance Checklist and correct if needed

### Controls
See the reference documentation for the available controls.
IMPORTANT: Verify with the Compliance Checklist and correct if needed

### Actions
See the reference documentation for the available actions.
IMPORTANT: Verify with the Compliance Checklist and correct if needed

### Features
See the reference documentation for the available features.
IMPORTANT: Verify with the Compliance Checklist and correct if needed

---

## Compliance Checklist
Verify each of the following steps before proceeding:

- [ ] Format code following the `coding-style` reference
- [ ] Verify forbidden deviations
- [ ] Verify forbidden practices

### Forbidden Deviations
Generated code MUST NOT:

- Rename `c`, `obj`, or `params`.
- Inline form definitions.
- Skip `with {}` blocks.
- Introduce business logic.
- Bypass `display`.

## Forbidden Practices
- Business logic inside controllers.
- Direct persistence access.
- Bypassing `createContent`.
- Building UI outside Goowee Elements APIs.
- Defining forms outside `buildForm`.
- Heavy logic inside `eachRow`.
