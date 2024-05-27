## Second contribution experience

### What is git bisect?

`git bisect` is a Git command that uses binary search to find the commit that introduced a bug. The user must specify the search boundaries, that is, a commit prior to the bug's introduction and another commit that exhibits the anomalous behavior caused by the bug. Additionally, it is necessary to pass a Bash command that will be executed by git bisect on each target commit of the binary search. If the command fails, the search considers that the commit exhibits the defective behavior.

### What is kw bd?

`kw bd` is a kworkflow command used as a shortcut to build and deploy the kernel in a single command.

### What did we do?

In our second contribution, we chose an [issue](https://github.com/kworkflow/kworkflow/issues/664) that requested the integration of `kw bd` with `git bisect`. Kworkflow users were already accustomed to using the result of the `kw bd` command as the test for the binary search of `git bisect`. Our task was to make this combination a native kworkflow command. To accomplish this, we added the ability to input the arguments `--good` and `--bad` to the `kw bd` command, which can be used to specify the binary search limits of `git bisect`. If none of these arguments are passed, we execute kw bd normally.
