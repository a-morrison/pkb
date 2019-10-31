---
title: "Git"
---
# Git
Version Control[^1]

## GitFlow
Simple but powerful workflow for stucturing complex git repos[^2].

EX:
{{< mermaid >}}
gitGraph:
options
{
    "nodeSpacing": 70,
    "nodeRadius": 10
}
end
commit
branch releases
branch develop
branch feature
checkout releases
commit
checkout develop
commit
checkout feature
commit
checkout develop
commit
checkout releases
commit
checkout feature
commit
commit
checkout develop
merge feature
checkout releases
merge develop
checkout master
merge releases
{{< /mermaid >}}

## Environment Based Branch Model
{{< hint info >}}
This could be an effective git model for GovGrants.
{{< /hint >}}
Applicable when each branch should represent an environment (Prod, QA, Dev, etc)[^3].

Rules:

- Don't commit directly to an envrionment branch
- Don't merge one environment branch into another
- Feature branches should be based on master and envrionment agnostic

## Further Reference
[^1]: [Documentation](https://git-scm.com/docs)
[^2]: https://nvie.com/posts/a-successful-git-branching-model/
[^3]: https://www.wearefine.com/mingle/env-branching-with-git/