---
name: ai-talent-map-expander
description: Expand and maintain AI talent maps using verified social, community, research, open-source, and company sources.
---

# AI Talent Map Expander

Use this skill when the user asks to expand, refresh, verify, or reorganize an AI talent map, especially when the request includes social media, public or private communities, LinkedIn, Xiaohongshu, WeChat, research labs, AI infrastructure, model teams, or competitor mapping.

## Outcome

Produce source-traceable person and channel updates that can be merged into an existing map without disturbing user annotations or layout. Keep confirmed people, author/community leads, and unresolved clues distinct.

## Workflow

1. Inspect the existing map before editing. Identify the people array, channel array, relation/lineage data, update-batch marker, render functions, annotation keys, and localStorage/import mechanism.
2. Search multiple source classes relevant to the request: official company/team pages, personal sites, LinkedIn public pages, X, Xiaohongshu image/text posts, WeChat public indexes, GitHub, Hugging Face, ModelScope, Gitee, arXiv/OpenReview, conference speaker pages, YouTube descriptions, and public community announcements.
3. Treat communities as discovery channels. Slack, Discord, WeChat groups, Feishu groups, Knowledge Planet, GitHub Discussions, meetups, workshops, and event chats must not be used to infer employment from a nickname, anonymous post, or membership alone.
4. For each person, record current organization or mark it unresolved, role scope, skills, discovery time, source links, evidence strength, and a short next-verification action. Add a stable update batch to new or materially changed entries.
5. Add lineage only when supported by an explicit source: `师从`, `共同作者`, `同团队`, `共同创业`, `组织调动`, or `开源合作`. Do not turn proximity, co-attendance, or a paper author list into a reporting or employment relationship.
6. Preserve existing HTML structure, link formatting, CSS, annotations, notes, saved ordering, collapsed state, graph coordinates, and localStorage keys. New data must not reset or overwrite those states.
7. Render both portable and ordinary HTML copies from the same content, update the package README, and refresh the ZIP only when the user asks for a distributable package.

## Evidence rules

- Strong: official team/company page, person's own current profile or site, signed technical report with a matching current profile, or a first-party announcement.
- Medium: reputable interview, conference speaker page, repository ownership/maintainer history, or two independent reports that identify the same person and role.
- Discovery only: search snippets, reposts, anonymous community posts, comments, screenshots without provenance, or a model/repository upload alone.
- Label uncertainty in the data itself with wording such as `待核验`, `作者池`, `公开关联`, or `下一站待核验`; do not silently upgrade it.

## Update conventions

Use the map's existing object schema and stable keys. Prefer existing annotation keys, including `person-source:${name}:${dest}` and `social-source:${channel}`, rather than inventing replacements. Use the current date or user-specified batch for `updateBatch`. Avoid duplicate people by checking normalized English names, Chinese names, aliases, and organization variants before insertion.

When a channel is added or refreshed, include its access method, what it can discover, current coverage, gaps, verification rule, refresh cadence, priority, and update batch. Explicitly distinguish an open API from public web pages and login-only/manual inspection.

## Validation

Before handoff, verify:

- both HTML copies are byte-identical when the map uses mirrored files;
- no duplicate normalized person names were introduced;
- all new source URLs are preserved and rendered as links;
- the current batch appears in the latest-update view;
- existing localStorage/annotation files were not modified unless explicitly requested;
- the page still parses and the package contains the expected HTML, backup, import tool, and README files.

For the detailed data contract and evidence matrix, read [references/data-contract.md](references/data-contract.md).
