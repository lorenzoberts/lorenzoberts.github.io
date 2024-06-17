## Final experience

[The first contribution,](https://github.com/kworkflow/kworkflow/pull/1099) adding regular expression support to the `kw -d –uninstall` command, was merged into the unstable branch after a few more review cycles.

[The second contribution](https://github.com/kworkflow/kworkflow/pull/1120), adding git bisect support to the `kw bd` command, was not accepted as it was. Three suggestions were left on the PR: close the PR, open a PR resolving another [issue](https://github.com/kworkflow/kworkflow/issues/1123), and open a PR creating a new file.

It was suggested that we close the PR adding git bisect to the `kw bd` command and only revisit this issue after completing the other suggestions.

After closing the PR, we tried to address the second suggestion. To do this, we needed to complete an issue involving the implementation of a library with utilities that use git commands in `kw`. The idea was that later we could create a utility using git bisect within this library and leverage it in the `kw bd` command. Since this issue was not our focus, we considered creating the lib in a simplified way, i.e., containing only the git bisect utility. After opening the [PR](https://github.com/kworkflow/kworkflow/pull/1136https://github.com/kworkflow/kworkflow/pull/1136), we received feedback that it should be more comprehensive to include all existing uses of git in `kw`, replacing all occurrences across the project with the utilities created in the lib. Additionally, the changes should be thoroughly tested.

The last suggestion was to open a PR creating a new file that would isolate the logic of the `kw bd` command. We had already made this change as part of the original PR that was closed, but ideally, we should open a PR solely for this.

Initially, we decided to follow all the suggestions. In the case of the git lib issue, we started its implementation but did not proceed because we felt it was a significant shift in focus from what we initially intended. However, we opened the [PR](https://github.com/kworkflow/kworkflow/pull/1138) creating the new file with the `kw bd` implementation and hope it gets approved. Unfortunately, it is likely that the git bisect functionality will not be delivered. However, the PR can be used as a reference for this task to be completed later.
