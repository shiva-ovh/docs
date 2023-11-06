---
title: Change an environment's parent
slug: guide.en-au
section: Environments-Change-Parent
---

**Last updated 6th November 2023**



## Objective  

**Last updated 6th November 2023**



## Objective  

All environments default to having another environment as their parent.
If you [branched](../../glossary#branch) the environment from another,
its parent starts as the environment it was created from.
If you pushed a branch through Git or a [source integration](../integrations/source/_index.md),
the parent defaults to the default environment.

To change the environment's parent, follow these steps:

> [!tabs]      

If you're not using a [source integration](../integrations-source),
you can also set a parent for your environment when pushing changes to it.
To do so, run the following command:

```bash
git push -o "environment.parent={{< variable "PARENT_ENVIRONMENT_NAME" >}}"
```

Learn more about how to [trigger actions on `push`](../#push-options).
