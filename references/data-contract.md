# Data Contract

## Person record

Keep the local map's established fields where present:

`name`, `dest`, `type`, `role`, `bytedance`, `time`, `skills`, `background`, `source`, `status`, `updateBatch`.

The `source` field should retain readable source labels and full URLs. A paper author is a research contribution, not proof of a current employer. A community participant is a lead, not proof of membership or employment.

## Channel record

Use the established channel shape:

`channel`, `state`, `access`, `discovery`, `coverage`, `gap`, `verification`, `cadence`, `priority`, `status`, `updateBatch`.

Recommended states are `已使用`, `公开索引`, `待登录深扫`, and `待补充`.

## Relationship record

Use the existing lineage fields when available:

`subject`, `relation`, `target`, `context`, `confidence`, `evidence`, `source`, `value`, `next`.

The `next` field should say exactly what source would upgrade the relationship. A public paper can support `共同作者`; it cannot by itself support `师从` or `曾汇报`.

## Source-to-claim matrix

| Source | Safe primary use | Claims requiring another source |
| --- | --- | --- |
| Official team/company page | current affiliation and public role | complete team membership, reporting line |
| Personal website / LinkedIn | self-described current and historical profile | employer truth when stale or incomplete |
| Signed paper / model card | technical contribution and author identity | current employment, title, management scope |
| GitHub / ModelScope / Hugging Face | maintainership, commits, releases, model contribution | employment and full team membership |
| WeChat / Xiaohongshu / X | first-party announcements and discovery | reposted claims, screenshots, anonymous comments |
| Slack / Discord / WeChat / Feishu groups | public announcements, event information, project links | private membership, identity, employment |
| Conference / workshop speaker page | appearance, talk topic, stated affiliation at event time | current affiliation after the event |

## Storage invariants

Never replace the annotation export or localStorage backup as part of a data refresh. Keep stable `data-mark-key` values and existing module/order identifiers. If a schema migration is unavoidable, make it additive and preserve old keys.
