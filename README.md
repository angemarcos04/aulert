# Aulert

**Aulert** is a planned AI-powered campus concern reporting and triage system for school environments.

It helps students submit school-related concerns while using AI to classify, summarize, prioritize, and route each report to the appropriate campus office for staff review.

> **Status:** Pre-development / Planning Stage
> **Project Type:** Side Project / Portfolio Prototype
> **Core Idea:** AI triage for campus concerns

---

## Overview

Schools often receive student concerns through scattered channels such as direct messages, verbal reports, paper forms, group chats, or social media posts. This can make it difficult for staff to identify urgent issues, assign responsibility, avoid duplicate reports, and track whether a concern has been resolved.

Aulert is designed to provide a more organized reporting flow.

Students can submit campus concerns through a simple form. The system then uses AI to convert each unstructured report into a structured, staff-reviewable action ticket.

The AI does not make final decisions. It assists by suggesting classifications, priorities, summaries, routing, and possible risk flags. School staff remain responsible for reviewing and resolving each report.

---

## Problem

Common school concerns may include:

* Broken classroom equipment
* Wi-Fi or computer laboratory issues
* Facility maintenance concerns
* Safety risks
* Academic or schedule-related issues
* Lost-and-found reports
* Administrative concerns
* Student welfare concerns
* Cleanliness or environment concerns

Without a centralized system, these reports can be:

* Delayed
* Misrouted
* Repeated multiple times
* Ignored accidentally
* Difficult to track
* Hard to prioritize

---

## Proposed Solution

Aulert provides a centralized platform where:

1. Students submit a school concern.
2. Students choose whether to submit anonymously or with their name/contact details.
3. The system generates a tracking code.
4. AI analyzes the report.
5. AI classifies the issue.
6. AI generates a short summary.
7. AI estimates urgency or priority.
8. AI suggests the appropriate office or department.
9. Staff review the AI output.
10. Staff update, route, and resolve the report.
11. Students track the report status using their tracking code.

---

## Core Workflow

```text
Submit Concern
    ↓
Choose Anonymous or Named Report
    ↓
AI Triage
    ↓
Staff Review
    ↓
Status Updates
    ↓
Resolved Report
```

---

## Report Types

### Anonymous Report

Anonymous reports allow students to submit concerns without sharing their identity.

This is useful for:

* Safety concerns
* Sensitive reports
* General facility issues
* Campus problems that do not require direct follow-up

Anonymous reports should not include names, student IDs, passwords, private documents, or unnecessary personal details.

### Named Report

Named reports allow students to provide their name and contact details for follow-up.

This is useful for:

* Lost-and-found cases
* Academic concerns
* Reports requiring clarification
* Issues where staff may need to contact the reporter

---

## Planned AI Features

Aulert will use AI as a triage assistant, not as a replacement for human judgment.

### Issue Classification

The AI will classify reports into categories such as:

* ICT / Technology
* Facilities
* Academic
* Safety
* Student Welfare
* Administrative
* Lost and Found
* Cleanliness / Environment
* Other

### Report Summarization

The AI will generate a short, staff-friendly summary of the submitted report.

Example:

```text
Original report:
"The projector in Room 204 has not been working for three days, and our class cannot continue our presentations properly."

AI summary:
"Projector in Room 204 has been broken for three days, affecting class presentations."
```

### Priority Detection

The AI will estimate the urgency of a concern.

Possible priority levels:

* Low
* Medium
* High
* Urgent

### Office Routing Suggestion

The AI will suggest which school office or department should handle the report based on the selected campus and available offices.

Example:

```text
Concern:
"The Wi-Fi in the library keeps disconnecting."

Suggested office:
ICT Office
```

### Privacy and Safety Flagging

The AI may flag reports that appear to contain:

* Personal information
* Student IDs
* Contact details in anonymous reports
* Safety risks
* Sensitive welfare concerns

### Confidence Score

The AI may provide a confidence score to help staff know whether the suggestion is reliable or needs closer review.

### Human Review

AI suggestions are not final decisions. Staff members can accept, edit, or override AI-generated classifications, priorities, and routing suggestions.

---

## Example AI Output

```json
{
  "category": "ICT / Technology",
  "priority": "Medium",
  "summary": "The library Wi-Fi keeps disconnecting and affects student research.",
  "suggested_office": "ICT Office",
  "risk_flag": "None",
  "privacy_warning": false,
  "requires_human_review": false,
  "confidence": 0.89,
  "recommended_action": "Check the library router, access points, and connection stability."
}
```

---

## Planned Core Features

### Student Side

* Submit a campus concern
* Choose anonymous or named submission
* Add issue title and description
* Add campus or branch
* Add location
* Receive a tracking code
* Track report status

### Staff/Admin Side

* Admin login
* View submitted reports
* Filter by category, priority, status, campus, or office
* See AI-generated triage results
* Review AI classification and summary
* Accept or override AI suggestions
* Update report status
* Add internal notes
* Add resolution notes

### Status Flow

```text
Pending → Reviewing → In Progress → Resolved
```

Optional future status:

```text
Needs More Info
```

---

## Institution-Aware Design

Aulert is planned to support institution and campus-based routing.

This means each school, branch, or campus may have its own:

* Offices
* Concern categories
* Routing rules
* Admin accounts
* Report records

Example structure:

```text
Institution
└── Campus / Branch
    ├── Offices
    ├── Concern Categories
    ├── Routing Rules
    ├── Admin Accounts
    └── Reports
```

For the initial prototype, Aulert may use sample branch-based school data to demonstrate how campus-specific routing works.

---

## Planned Tech Stack

The final stack may change during development.

### Preferred Stack

* Laravel
* Filament
* PostgreSQL
* Gemini API or OpenAI API
* Tailwind CSS

### Alternative Stack

* SvelteKit
* Supabase
* Gemini API or OpenAI API
* Tailwind CSS

---

## Possible Database Structure

### institutions

| Field      | Description                   |
| ---------- | ----------------------------- |
| id         | Unique institution ID         |
| name       | Institution name              |
| slug       | URL-friendly institution name |
| created_at | Creation date                 |

### campuses

| Field          | Description           |
| -------------- | --------------------- |
| id             | Unique campus ID      |
| institution_id | Related institution   |
| name           | Campus or branch name |
| code           | Campus code           |
| address        | Campus address        |
| created_at     | Creation date         |

### offices

| Field       | Description           |
| ----------- | --------------------- |
| id          | Unique office ID      |
| campus_id   | Related campus        |
| name        | Office name           |
| description | Office responsibility |

### concern_categories

| Field       | Description          |
| ----------- | -------------------- |
| id          | Unique category ID   |
| name        | Category name        |
| description | Category description |

### routing_rules

| Field       | Description              |
| ----------- | ------------------------ |
| id          | Unique routing rule ID   |
| campus_id   | Related campus           |
| category_id | Related concern category |
| office_id   | Suggested office         |

### reports

| Field          | Description                            |
| -------------- | -------------------------------------- |
| id             | Unique report ID                       |
| institution_id | Related institution                    |
| campus_id      | Related campus                         |
| tracking_code  | Public tracking code                   |
| report_type    | Anonymous or named                     |
| reporter_name  | Nullable reporter name                 |
| reporter_email | Nullable reporter email                |
| title          | Report title                           |
| description    | Full concern description               |
| location       | School location related to the concern |
| status         | Current report status                  |
| created_at     | Submission date                        |

### ai_analyses

| Field                 | Description                               |
| --------------------- | ----------------------------------------- |
| id                    | Unique AI analysis ID                     |
| report_id             | Related report                            |
| category              | AI-detected issue category                |
| priority              | AI-detected priority level                |
| summary               | AI-generated summary                      |
| suggested_office      | AI-suggested office                       |
| risk_flag             | AI-detected safety or sensitivity flag    |
| privacy_warning       | Whether privacy issues were detected      |
| requires_human_review | Whether staff review is strongly required |
| confidence            | AI confidence score                       |
| recommended_action    | AI-suggested next step                    |
| raw_response          | Original AI response                      |

### status_updates

| Field      | Description       |
| ---------- | ----------------- |
| id         | Unique update ID  |
| report_id  | Related report    |
| status     | Updated status    |
| note       | Staff update note |
| updated_by | Staff/admin user  |
| created_at | Update date       |

---

## MVP Scope

The minimum viable prototype should include:

* Landing page
* Student report form
* Anonymous or named report option
* Institution and campus selector
* AI classification
* AI-generated summary
* AI priority detection
* AI office routing suggestion
* Tracking code system
* Report tracking page
* Admin login
* Admin dashboard
* Report status updates
* Human review and override for AI suggestions

---

## Future Improvements

Possible future features include:

* Email notifications
* Image uploads
* Duplicate report detection
* Report analytics dashboard
* Sentiment analysis
* Multilingual report support
* Exportable reports
* Role-based staff accounts
* Department-specific dashboards
* AI-generated weekly issue summaries
* Public API for institution integrations
* Mobile-friendly progressive web app

---

## Project Goals

Aulert aims to:

* Make school issue reporting easier for students
* Support anonymous and named reporting
* Help staff understand reports faster
* Reduce misrouted or ignored concerns
* Improve response time for school problems
* Provide a clearer record of submitted and resolved issues
* Route reports based on institution and campus context
* Use AI as a support tool, not as a replacement for staff judgment

---

## Development Notes

This project is currently in the planning stage.

The first development target is to build the complete core loop:

```text
Submit → AI Triage → Admin Review → Status Update → Track Report
```

The project will be built as a portfolio-focused prototype and may later be expanded into a more complete institution-aware reporting platform.

---

## License

License to be decided.

---

## Author

Created by **Angellie D. Marcos**.
