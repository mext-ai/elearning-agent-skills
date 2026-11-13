---
name: build-together
description: Sets up and runs shared work on MEXTY content and EdVerse games, where several people and their AI assistants build the same course, learning path or game. Use when someone wants to co-author, invite a colleague, a class or a friend to build with them, work in a draft without touching what learners or players see, ask for or give a review, comment on content, compare or restore versions, merge someone's changes, or when two people edited the same thing and it conflicts.
---

# Build together

Both MEXTY and EdVerse keep one live version that learners and players see, and let people work beside it in drafts. Nothing in a draft reaches a learner or a player until it is published or merged.

## In the MEXTY workspace (courses, activities, evaluations, learning paths)

Who can do what comes from the organisation's roles. Check before editing something that is not yours: `get_my_access` returns `canEdit`, `canWorkOnDrafts` and the role (owner, admin, editor, contributor, reviewer).

| Step | Tool | Notes |
|---|---|---|
| Start a draft of live content | `create_content_draft` | When `canEdit` is false, a draft or a comment is the only way in |
| Bring people in | `add_draft_members`, `add_draft_reviewers`, `set_coauthor` | Co-authors are credited on the content |
| Discuss | `add_content_comment`, `list_content_comments` | Comments stay with the content |
| See what changed | `get_content_draft_diff`, `get_draft_impact` | Read the impact before publishing: who is enrolled, what they would lose |
| Ask for a review | `request_content_review` | |
| Give a review | `review_content_draft` | Approve or send back with reasons |
| Catch up with Live | `update_content_draft_from_live` | When Live moved while the draft was open |
| Release | `publish_content_draft` or `schedule_content_draft` | Only with the person's yes |
| Go back | `list_content_versions`, `compare_content_version`, `restore_version_as_draft` | A restore opens as a draft, never straight to Live |

Rules:

- Never publish or schedule for someone. Show the diff and the impact, then ask.
- A reviewer reviews; they do not rewrite the author's draft. Put changes in comments unless asked to edit.
- Learners' names and results seen during a review stay in the workspace.

## In EdVerse (games)

A game's world and its code can be edited by several people and assistants at the same time. Edits merge; nothing is locked.

**Roles.** The owner and maintainers edit the main version and merge drafts. Everyone who joins by the share link starts as a contributor: they work in drafts and ask for a review. Store staff can read and comment.

**People.** The owner manages them from the Studio's Share dialog or with the tools: `list_game_collaborators` (people, invitations, link), `invite_game_collaborators` (by email, with a role), `set_game_collaborator_role` (maintainer or contributor), `remove_game_collaborator` (or yourself, to leave), `resend_game_invite`, `withdraw_game_invite`, `set_game_share_link` (on, off, or a new link).

**Open for collaboration.** The owner can also open a game to every signed-in maker, not only invited ones. It then appears in the Studio's Collaborative games and in `list_collaborative_games`. An outsider reads main and works only in their own drafts (at most 3 open per game); when the owner merges one, its author becomes a contributor. Closing it again stops new drafts; outsiders keep read-only access to drafts they already made. See `edverse-publish-and-earn` for how merged work is paid.

**The flow.**

1. The owner shares the game's link from the editor. Each person who joins gets the live 3D editor.
2. A contributor's work goes into a draft: `create_draft({ game_id })`, then pass `draft_id` to the scene and file tools. A contributor's assistant works in their draft automatically.
3. `get_draft_diff` shows what changed, object by object and file by file.
4. `request_review` emails the owner and maintainers.
5. The owner or a maintainer merges with `merge_draft`. `update_draft_from_main` catches a draft up first; `close_draft` drops one.

**Editing code at the same time.** Prefer `edit_game_files` (old text to new text) for small changes. For whole files, pass back the `bases` that `read_game_files` returned, so the write merges against the version you read. A region someone else changed meanwhile comes back with conflict markers and is not written: read it, resolve it, write again.

**Conflicts on merge.** What only one side changed merges by itself. The same field or the same lines changed on both sides, or an object changed on one side and deleted on the other, is a conflict. `merge_draft` lists them; call it again with a pick for each (`main` or `draft`, or an edited version for code). Ask the people involved when the right pick is not obvious.

**Credit.** When a draft is merged, its authors are credited, not the person who merged it. Only merged work counts for the learner pool.

## A class or a club building one game

- The teacher owns the game and keeps it as the main version.
- Each student or pair joins by the share link and works in their own draft: one level, one character, one set of questions.
- The teacher reviews each draft with the class, then merges it. Conflicts become a discussion, which is the lesson.
- The game goes through `edverse-game-qa` before anyone submits it. The owner takes the game test.

## When to stop and ask

- Before merging or publishing anything.
- Before closing or discarding someone else's draft.
- When a conflict pick would delete another person's work.
