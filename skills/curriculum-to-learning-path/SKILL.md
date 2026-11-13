---
name: curriculum-to-learning-path
description: Turns a school or university curriculum, syllabus, module descriptor or scheme of work into a MEXTY learning path with courses and evaluations. Use when a teacher, lecturer or academic lead shares learning outcomes, a syllabus, a term plan or a programme specification and wants it built as online or blended learning, wants a course per outcome, a year or a semester laid out as a path, or content to export to the institution's existing LMS.
---

# A curriculum as a learning path

Needs the MEXTY MCP (Authoring; the LMS to assign and track, or export to SCORM for another LMS).

## 1. Read the curriculum as it is written

Take the official document and list, without rewording: the learning outcomes, their grouping (units, strands, weeks), the level, the hours, and how it is assessed. Number each outcome as the document does. Every course and every question will point back to one.

If outcomes are vague, ask the teacher what a student who has met it can do. Do not sharpen the official wording yourself.

## 2. Map outcomes to the path

| Curriculum | Path |
|---|---|
| A unit or strand | A group of courses, in teaching order |
| One outcome, or two that are taught together | One course |
| A unit test | An evaluation after the unit |
| The final exam or project | One final evaluation at the end |
| Optional or elective content | A parallel branch |

Show the teacher the map as a table (outcome, course, how it is checked) before building. It is the cheapest moment to change it.

## 3. Build

- `create_program`, then nodes and links in bulk. The new path display is a grid of numbered cells that unlock in order; a cell can hold several items, all required or any one.
- Prerequisites become locks. Deadlines only show on calendars; use them for term dates.
- Each course follows one rhythm so students know what to expect: an opener, the content, an activity where they use it, a short check. Use a template series for a consistent look (`list_course_template_series`).
- The same activity type every time is tiring. Vary by what the outcome asks: classify, order, calculate, explain, build.
- Evaluations: see `assessment-design`.

## 4. Fit the classroom

- Say how each course is meant to be used: before class, in class, as homework.
- Give the teacher what the path does not: discussion questions, a practical, a project brief.
- Languages: build in the language of instruction. A second language is a second set of content, not a machine pass over the first.
- Accessibility: readable without colour, usable by keyboard, captions on video.

## 5. Review and release

Draft, review by the teacher or department (`build-together`), then publish. Assign to a class group, or export to SCORM for the institution's LMS. Follow progress per student in Analytics or a custom dashboard (`analytics-dashboards`).

## Rules

- The curriculum is the authority. Where the textbook and the curriculum differ, follow the curriculum and tell the teacher.
- Do not claim alignment you did not check, outcome by outcome.
- Students' names and results stay in the workspace.
