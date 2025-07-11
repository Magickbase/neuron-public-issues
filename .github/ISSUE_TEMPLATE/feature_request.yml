name: Feature Request
description: This is the overall issue template for proposing new features or tasks
title: '[Top-Level Feature] <Name>'
labels:
  - feature-request
projects:
  - Magickbase/9
assignees:
  - Danie0918

body:
  - type: markdown
    attributes:
      value: 'Thank you for proposing a new feature! This is a **top-level issue** that will be broken down into sub-issues for tracking individual implementation phases. Please fill out the following template to help us collaborate better.'

  - type: textarea
    id: summary
    attributes:
      label: 'Summary'
      description: 'High-level overview of the feature request'
      placeholder: |
        Overview:
        - Brief description of the feature
        - Key business value proposition
        - Target user segments

        Strategic Alignment:
        - Business objectives supported
        - Expected outcomes
    validations:
      required: true

  - type: textarea
    id: business_context
    attributes:
      label: 'Business Context & Problem Statement'
      description: 'Detailed analysis of the business need and current challenges'
      placeholder: |
        Business Need:
        - Specific business goals
        - Market opportunity

        Current Challenges:
        - Problem description

    validations:
      required: true

  - type: textarea
    id: solution
    attributes:
      label: 'Solution & User Experience'
      description: 'Proposed solution and user experience design'
      placeholder: |
        Solution Overview:
        - Feature description
        - Technical approach
        - Key components

        User Experience:
        - User journey
        - Workflows
        - UI/UX requirements
        - Accessibility considerations
    validations:
      required: true

  - type: textarea
    id: success_metrics
    attributes:
      label: 'Success Metrics & Technical Requirements'
      description: 'Success criteria and technical specifications'
      placeholder: |
        Success Metrics:
        - Quantitative criteria
        - KPIs
        - Measurement method

        Technical Requirements:
        - Performance needs
        - Security requirements
        - Scalability considerations
        - Data requirements

        Dependencies:
        - External systems
        - Third-party services
        - Internal components
    validations:
      required: true

  - type: checkboxes
    id: implementation_phases
    attributes:
      label: 'Implementation Phases'
      description: '👉🏻 **Each checked phase should be converted into a separate sub-issue for tracking.** This helps break down complex features into manageable phases and provides better visibility into progress across the entire development lifecycle.'
      options:
        - label: 'Discovery - Requirements analysis and feasibility study'
        - label: 'Design - Technical design, architecture, and UI/UX'
        - label: 'Development - Implementation and unit testing'
        - label: 'Testing - QA, integration, and user acceptance testing'
        - label: 'Deployment - Release planning, documentation, and training'
        - label: 'Monitoring - Performance tracking and optimization'

  - type: textarea
    id: documentation
    attributes:
      label: 'Documentation & References'
      description: 'Supporting documentation and reference materials'
      placeholder: |
        Technical Documentation:
        - API specifications
        - Database schema
        - System architecture

        User Documentation:
        - User guides
        - Training materials
        - Release notes

        References:
        - Related issues/PRs
        - External documentation
        - Research materials
    validations:
      required: false
