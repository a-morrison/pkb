---
title: "Git"
---
# Git[^1]

## GitFlow[^2]
Simple but powerful workflow for stucturing complex git repos.
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

## Further Reference
[^1]: [Documentation](https://git-scm.com/docs)
[^2]: https://nvie.com/posts/a-successful-git-branching-model/