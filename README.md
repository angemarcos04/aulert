# Aulert

**Aulert** is a planned AI-powered campus concern reporting and triage system designed for school environments.

The project aims to help students report school-related issues while using AI to classify, summarize, prioritize, and route each report to the appropriate school office or staff member.

> **Status:** Pre-development / Planning Stage
> **Project Type:** Hackathon Prototype
> **Theme:** Artificial Intelligence for solving real school problems

---

## Overview

Schools often receive student concerns through scattered channels such as messages, verbal reports, paper forms, or social media posts. This can make it difficult for staff to identify urgent issues, assign responsibility, and track whether a concern has been resolved.

Aulert is designed to simplify that process.

Students will be able to submit campus concerns through a simple reporting form. The system will then use AI to analyze the report and generate structured information that can help school staff respond faster and more efficiently.

---

## Problem

Common school issues can include:

* Broken classroom equipment
* Wi-Fi or computer laboratory problems
* Facility maintenance concerns
* Safety risks
* Academic or schedule-related issues
* Lost-and-found reports
* Administrative concerns
* Student welfare concerns

Without a proper system, these reports can be delayed, misrouted, ignored, or repeated multiple times.

---

## Proposed Solution

Aulert will provide a centralized platform where:

1. Students submit a school concern.
2. AI analyzes the report.
3. The system classifies the issue.
4. The report is assigned a priority level.
5. The system suggests the appropriate office or department.
6. Staff can review, update, and resolve the report.
7. Students can track the status of their submitted concern.

---

## Planned AI Features

Aulert will use AI for the following tasks:

### Issue Classification

The AI will classify each report into categories such as:

* Facilities
* ICT / Technology
* Academic
* Safety
* Student Welfare
* Administrative
* Lost and Found
* Other

### Report Summarization

The AI will generate a short and clear summary of the submitted concern.

Example:

```text
Original report:
"The projector in Room 204 has not been working for three days, and our class cannot continue our presentations properly."

AI summary:
"Projector in Room 204 has been broken for three days, affecting class presentations."
```

### Priority Detection

The AI will estimate the urgency of the concern.

Possible priority levels:

* Low
* Medium
* High
* Urgent

### Office Routing Suggestion

The AI will suggest which school office or department should handle the report.

Example:

```text
Concern: "The Wi-Fi in the library keeps disconnecting."

Suggested office:
ICT Office
```

### Human Review

AI suggestions will not be final decisions. Staff members will still review reports before taking action.

---

## Planned Core Features

### Student Side

* Submit a campus concern
* Add issue title and description
* Add location
* Choose anonymous or named submission
* Receive a tracking code
* Check report status

### Staff/Admin Side

* View submitted reports
* See AI-generated classification
* See AI-generated summary
* See suggested priority level
* Update report status
* Add resolution notes
* Filter reports by category, priority, and status

### Status Flow

```text
Pending → Reviewing → In Progress → Resolved
```

---

## Planned Tech Stack

The final stack may change during development.

### Option 1: Laravel Stack

* Laravel
* Filament
* PostgreSQL
* Gemini API or OpenAI API
* Tailwind CSS

### Option 2: JavaScript Stack

* SvelteKit
* Supabase
* Gemini API or OpenAI API
* Tailwind CSS

---

## Possible Database Structure

### reports

| Field         | Description                               |
| ------------- | ----------------------------------------- |
| id            | Unique report ID                          |
| tracking_code | Public tracking code                      |
| title         | Report title                              |
| description   | Full concern description                  |
| location      | School location related to the concern    |
| is_anonymous  | Whether the student submitted anonymously |
| status        | Current report status                     |
| created_at    | Submission date                           |

### ai_analyses

| Field              | Description                |
| ------------------ | -------------------------- |
| id                 | Unique AI analysis ID      |
| report_id          | Related report             |
| category           | AI-detected issue category |
| priority           | AI-detected priority level |
| summary            | AI-generated summary       |
| suggested_office   | AI-suggested office        |
| recommended_action | AI-suggested next step     |
| raw_response       | Original AI response       |

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

## Example AI Output

```json
{
  "category": "ICT / Technology",
  "priority": "Medium",
  "summary": "The library Wi-Fi keeps disconnecting and affects student research.",
  "suggested_office": "ICT Office",
  "recommended_action": "Check the library router, access points, and connection stability."
}
```

---

## MVP Scope

The minimum viable prototype should include:

* Student report form
* AI classification
* AI-generated summary
* AI priority detection
* Admin dashboard
* Report status update
* Tracking code system

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
* Role-based accounts
* Mobile-friendly interface
* Department-specific dashboards

---

## Project Goals

Aulert aims to:

* Make school issue reporting easier for students
* Help staff understand reports faster
* Reduce misrouted or ignored concerns
* Improve response time for school problems
* Provide a clearer record of reported and resolved issues
* Use AI as a support tool, not as a replacement for human judgment

---

## Hackathon Notes

This project is intended to be developed during the hackathon period.

Pre-existing full project code will not be used. Public libraries, frameworks, and APIs may be used where allowed by the hackathon rules.

---

## License

License to be decided.

---

## Author

Created by Angellie D. Marcos
