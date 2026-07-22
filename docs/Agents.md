# AI Agents

This document describes the AI agents that make up the system and explains the responsibility of each one.

The architecture follows a modular design where every agent has a single primary responsibility and communicates with the next agent in the workflow.

---

# 1. Job Discovery Agent

## Purpose

Search and discover relevant job opportunities across multiple job platforms.

## Responsibilities

* Search multiple job boards.
* Apply search filters based on the user's profile.
* Remove duplicate job listings.
* Filter out irrelevant opportunities.
* Normalize job information from different sources.
* Deliver a clean list of relevant jobs.

## Input

* User profile
* Search preferences
* Job platforms

## Output

* Relevant job opportunities

---

# 2. Ranking Agent

## Purpose

Rank job opportunities according to how well they match the user's profile.

## Responsibilities

* Compare job requirements with the user's skills.
* Calculate a matching score.
* Rank jobs from best to worst.
* Highlight high-priority opportunities.

## Input

* Relevant job opportunities
* User profile

## Output

* Ranked job opportunities

---

# 3. Resume Agent

## Purpose

Generate a resume tailored to a specific job.

## Responsibilities

* Analyze the job description.
* Highlight relevant skills and experience.
* Adapt resume content to the position.
* Preserve factual information.

## Input

* User resume
* Job description

## Output

* Customized resume

---

# 4. Cover Letter Agent

## Purpose

Generate a personalized cover letter for each application.

## Responsibilities

* Analyze the job description.
* Use the customized resume as context.
* Generate a professional cover letter.
* Adapt the writing style to the company.

## Input

* Job description
* Customized resume

## Output

* Personalized cover letter

---

# 5. Application Agent

## Purpose

Assist with the job application process.

## Responsibilities

* Prepare all required application documents.
* Fill application forms when possible.
* Track submitted applications.
* Store application history.

## Input

* Selected job
* Customized resume
* Cover letter

## Output

* Application status

---

# 6. Notification Agent

## Purpose

Keep the user informed about important events.

## Responsibilities

* Notify about new job opportunities.
* Notify when applications are submitted.
* Notify about application status updates.
* Report system errors.
* Send daily or weekly summaries.

## Input

* Events from all agents

## Output

* User notifications

---

# Agent Workflow

```text
                 User Profile
                      │
                      ▼
          ┌────────────────────────┐
          │ Job Discovery Agent    │
          └────────────────────────┘
                      │
                      ▼
          ┌────────────────────────┐
          │ Ranking Agent          │
          └────────────────────────┘
                      │
                      ▼
          ┌────────────────────────┐
          │ Resume Agent           │
          └────────────────────────┘
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
┌──────────────────┐     ┌────────────────────┐
│ Selected Resume  │     │ Cover Letter Agent │
└──────────────────┘     └────────────────────┘
          │                       │
          └───────────┬───────────┘
                      ▼
          ┌────────────────────────┐
          │ Application Agent      │
          └────────────────────────┘
                      │
                      ▼
          ┌────────────────────────┐
          │ Notification Agent     │
          └────────────────────────┘
                      │
                      ▼
                    User
```

---

# Future Agents

The architecture is designed to support additional specialized agents as the project grows.

Possible future agents include:

* Company Research Agent
* Interview Preparation Agent
* Salary Negotiation Agent
* Career Recommendation Agent
* Networking Agent
* Portfolio Review Agent
* Resume Feedback Agent
* Skill Gap Analysis Agent
* Learning Recommendation Agent
