---
name: Advanced Issue
about: This template is mostly used for Stackable staff. It contains an elaborate checklist of things to consider/refine when creating an issue.
title: ''
labels: ''
assignees: ''

---

# Title

<!--
- Ensure the title is specific and descriptive
- Avoid acronyms if possible
-->

## Description
    
<!--
- Briefly describe what this epic aims to achieve
- "What" are we trying to achieve

Examples:
  - As devs we want an OpenShift certification process that is automated as far as possible.
-->

## Value
         
<!--
- Clearly define the value this brings to customers or why else it is important if not _directly_ for customers (e.g. internal tooling or improvements, technical debt, ...)
- "Why" do we want to do this
- Explain how to showcase the outcome of this issue to users/customers or developers (add tasks for this if needed), how can we market this

Examples:
  - "We want CRD versioning so we can make backwards compatible changes to our CRDs"
  - "We want CRD versioning because we're making contractual stability promises to our customers around CRDs, and we can only honor these using CRD versioning"
  - "Manual steps in the OpenShift certification process have lead to costly (time wise) errors in the past, these steps also mean that it is currently not easy for us to do a 'quick' patch release: These changes would allow this leading to a better experience for OpenShift users as well as making it easier to fulfill our contractual obligations, which might require us to release patches on short notice."
-->

## Dependencies
    
<!--
- Consider and name any internal and external dependencies and constraints
- List all known necessary resources (e.g. cluster, customers, people, repositories, libraries...)

Examples:
- This epic will require changes to docker image XY, it will require a change to the listener operator, and we'll need an OpenShift 4.15 cluster to test
-->

## Tasks

<!--
- List all known tasks that need to be completed to finish this epic
    - Not all tasks might be known at the beginning!
    - Task types
        - Technical
        - Testing
        - Documentation
        - Marketing / Showcase
- Initial tasks might just be _separate_ research tasks, which, upon completion, lead to more tasks in this epic
- When creating the list of tasks make sure to put them in an order and focus on creating minimum marketable features
- This is the _Definition of Done_ which (mostly, exception are marketing tasks) represents the technical "completeness" of a task 

Example:
  - Marketing: Prepare a blog post outlining the new CRD versioning support, our policies around CRD versioning and the current versions we do support
-->

## Acceptance Criteria
  
<!--
- List acceptance criteria
- Define clear objective criteria for when we would consider this issue "Done"
    - It differs from the _Definition of Done_ in _Tasks_ above by focusing on the "what" (an expanded version of the Description)
    - One example that should always if relevant be included is accessibility:
      - We don't yet do much UI work so this is underspecified right now

Example:
  - Bad example: All tests pass (that should be implied for anything and is not a functional requirement)
  - Good examples:
    - Traces are exported via OTLP and can be seen in Jaeger (or equivalent trace visualisation tool) (achieves a goal, while only being as prescriptive as necessary)
    - CRD versioning is seamlessly integrated into our operators, allowing for the specification of multiple versions within CRDs.
    - Backward compatibility is maintained for at least two previous versions of CRDs.
    - 

-->

## (Information Security) Risk Assessment
      
<!--
- Outline any information security (this includes cybersecurity) or any other obvious risks and the controls how to mitigate them
- This is relevant for ISO 27001, the Cyber Resilience Act and other standards/norms
- Examples:
    - Does this open any new ports? If so, how are they secured
    - Do we ask for the least amount of privileges required
    - Does this require any secrets?
    - Which ciphers might be used and how can they be configured
    - Does it introduce a dependency? Have you reviewed it for vulnerabilities, licenses issues, recent activity etc.
    - Bugs in this feature could lead to data loss for our customers
    - ...
-->

## Accessibility Assessment

<!--
- Outline anything on

-->

## Quality
          
<!--
- Outline how this epic will be tested
- Compatibility:
  - Try to ensure compatibility with all our supported versions (e.g. Kubernetes, OpenShift, product versions)
  - List any potential compatibility issues you're aware of
-->   


## Release Notes
                     
<!--
- Write a short sentence or abstract that can go into the release notes
- This way it is also documented for anyone finding _just this_ epic later
- This does not need to be filled out during refinement but can/should be added later before closing the epic
-->

<!--
# Todos / Remarks

NOTE: This section is not meant to be displayed, therefore it is in a comment. You can leave it here, commented, or delete it.

- [ ] Fill out as many sections above as you can, not everything is known at the beginning. Please leave a comment in any section that is unknown.
- [ ] Delete everything that is irrelevant for this particular issue.
- [ ] Add appropriate labels


- There are different types of epics, which might require different subsets (or no) sections of the above
    - e.g. "Update product versions"
    - e.g. "Implement new feature"
- In the whole issue write out all acronyms that are not industry standard at least once. Example: OpenPolicyAgent (OPA)
- If this is part of another issue please make sure to link the two in both places (parent & child)
- If CRD changes (not necessarily breaking) are required, make sure structs/enums/fields are documented and are rendered properly in the CRD generation tool
- Also see our [Development Philosophy](https://app.nuclino.com/Stackable/Stackable-Handbook/Development-Philosophy-ba280b20-b8cd-4fb6-a863-ff6d8c9f1af2)
-->    
