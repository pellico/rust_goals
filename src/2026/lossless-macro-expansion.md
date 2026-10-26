# Lossless macro expansion

> **Instructions:** Copy this template to a fresh file with a name based on your plan.
> Give it a title that names the overall theme of your goal
> (e.g., "Const Generics" or "Polonius" or "Cargo Script").
> Use the `What and why` metadata row for a more readable one-liner
> (e.g., "Permit structs/enums to be used as the value of a const generic parameter").
> Feel free to replace any text with anything, but there are placeholders
> designed to help you get started.
> See the [goal format reference](./about/goal-format.md) for full details on the format.
>
> The **contact** is the person responsible for providing updates.
>
> The **status** should be **Proposed** for new goals or **Accepted** once approved.
>
> If your goal needs a **contributor**, add a `## Help wanted` section (see below).
>
> If your goal needs **funding**, add a `## Funding` section (see below).

| Metadata       |                                                                                  |
| :------------- | -------------------------------------------------------------------------------- |
| Contact        | _must be a single GitHub username like @ghost_                                   |
| Status         | Proposed                                                                         |
| Tracking issue | _if this is a continuing goal, add the old tracking issue, else remove the row_  |
| Zulip channel  | N/A (an existing stream can be re-used or new streams can be created on request) |

## Summary

Lossless macro expansion aims to preserve all syntactic and semantic information in macro expansions, so the expanded code can be compiled without changing the original code's behavior.

## Motivation

### The status quo

**Audience**

This proposal targets developers in safety-critical or high-assurance projects who rely on macros.

Current proposals for safety-critical coding guidelines prohibit macros ([link](https://coding-guidelines.arewesafetycriticalyet.org/coding-guidelines/macros/index.html)) for several reasons:

- They can introduce subtle bugs that are difficult to detect and reason about.
- They can obscure a program's control and data flow.
- They can make code harder to maintain and understand.
- They can hinder tools such as linters and analyzers that rely on source structure.
- They can make test coverage harder to measure accurately.

This creates a challenge for developers who must follow these guidelines while relying on macros for code generation and abstraction.

A possible approach, drawn from C/C++, is to expand macros while preserving the original source information, then version, compile, and test the expanded code.
This simplifies test coverage measurement and avoids complex macro verification.

However, Rust's unstable [unpretty](https://doc.rust-lang.org/beta/unstable-book/compiler-flags/unpretty.html) feature does not preserve all syntactic and semantic information, limiting its usefulness for lossless macro expansion. See the [cargo-expand disclaimer](https://github.com/dtolnay/cargo-expand#disclaimer) and [issue #118197](https://github.com/rust-lang/rust/issues/118197) on syntactically meaningful braces removed by `unpretty=expanded`.

### What we propose to do about it

> _Explain your overall approach to solving the problem. Explain your design philosophy (including design axioms). Focus your discussion on what you aim to get done this year, but it is good to also give a sense for the "overall goal" you are working towards, if it extends beyond the work for this year. Team(s) should give you feedback on whether they are aligned both with your short-term and longer-term goals._

### Work items over the next year

> _Sketch out the specific things you are trying to achieve in this goal period. This should be short and high-level -- we don't want to see the design!_

| Task        | Owner(s) | Notes |
| ----------- | -------- | ----- |
| Do the work | _owner_  |       |

> **Subgoals:** If your goal has distinct workstreams, you can break them into
> subgoals using `####` headings. Each subgoal should have a specific, actionable
> title and its own task table. For example, a goal titled "Full Const Generics"
> might have subgoals "ADT const params" and "Min generic const arguments."
>
> Subgoals can optionally have their own `| Metadata | |` table to override
> `Roadmap`, `Timespan`, or `What and why` from the parent goal.
> See the [goal format reference](./about/goal-format.md) for details.

## Team asks

> This section outlines what support you need from the Rust teams. For each team, identify the level of support you need:
>
> - Small: You only need the team to do its routine activities, or you simply need the team's approval.
>   - _Example:_ Prototyping a new feature on crates.io that you hope to eventually upstream.
>   - _Example:_ Conducting research that might eventually become a language feature.
>   - _Example:_ A compiler change that will require a few small PRs to be reviewed.
>   - _Example:_ Asking the lang team to approve a lint.
> - Medium: You need dedicated support from one person, but the rest of the team doesn't have to do much.
>   - _Example:_ A compiler change that doesn't require any rearchitecting but
>   - _Example:_ Implementing a small, noncontroversial language feature.
> - Large: You need deeper review from the entire team.
>   - _Example:_ Rearchitecting part of the compiler.
>   - _Example:_ Implementing a complex language feature that will require design meetings.
>
> If you're not sure, leave it blank, the project goals team can help.
>
> "Small" asks require someone on the team to "second" your goal; "Medium" and "Large" asks require a dedicated champion from the team. If you don't have a second or a champion, the project goals team will help you find them, don't worry about it.

| Team       | Support level | Notes                                   |
| ---------- | ------------- | --------------------------------------- |
| [cargo]    |               |                                         |
| [compiler] |               |                                         |
| [infra]    |               |                                         |
| [lang]     |               |                                         |
| [libs]     |               |                                         |
| [opsem]    |               |                                         |
| [types]    |               |                                         |
| ...        | ...           | _Feel free to add rows for other teams_ |

## Help wanted

> **Instructions:** If your goal needs a contributor, fill in the table below
> describing the work, the experience level needed, and the expected time investment.
> The presence of this section signals that the goal is looking for someone to do the work.
> The project goals team will try to help you find someone.
> Delete this section if your goal does not need a contributor.

| Task                          | Experience level          | Time investment            |
| ----------------------------- | ------------------------- | -------------------------- |
| _e.g., Implement the feature_ | _e.g., Intermediate Rust_ | _e.g., 3 months part-time_ |

## Funding

> **Instructions:** If your goal needs funding to proceed, fill in the table below
> describing what the funding would cover and the estimated cost.
> The presence of this section signals that the goal is looking for financial support.
> Delete this section if your goal does not need funding.
>
> If you have a specific funding contact (e.g., an organization that can
> receive and administer funds), add a `Funding contact` row to the
> metadata table at the top of this file. If omitted, it defaults to the
> [Rust Funding team](https://rust-lang.org/governance/teams/launching-pad/#team-funding).

| Purpose                                   | Cost            | Funded | Sponsor(s) |
| ----------------------------------------- | --------------- | ------ | ---------- |
| _e.g., Contributor (6 months, full-time)_ | _e.g., $60,000_ | No     |            |
| _e.g., Maintenance_                       | _e.g., $10,000_ | No     |            |

> If you don't know the expected cost, enter `TBD`. If you do, but prefer to not have it public on the internet, enter `Ask` and the readers will be directed to ask the _Funding contact_ about the cost.

## Frequently asked questions

### What do I do with this space?

_This is a good place to elaborate on your reasoning above -- for example, why did you put the design axioms in the order that you did? It's also a good place to put the answers to any questions that come up during discussion. The expectation is that this FAQ section will grow as the goal is discussed and eventually should contain a complete summary of the points raised along the way._
