


## Issue selection

Choosing an issue to implement was not easy. Among the open issues, a large portion were marked as **done**. Others had not tags, but upon checking the code, we could see that they had already been implemented. For this reason, we found few viable options to work on, and ended up choosing a very old issue from 2021 ([add regex support for kw d --uninstall #344](https://github.com/kworkflow/kworkflow/issues/344)).

## Implementation: [PR](https://github.com/kworkflow/kworkflow/pull/1099/)

The `kw deploy --uninstall` command from the Kernel Workflow takes a comma-separated list of kernels and removes them from the target machine. Our task was to enable this command to support regular expressions to facilitate kernel removal. To achieve this, we added a new flag `--regex` that the user can use to pass the regular expression instead of the list of kernels. In this case, we apply the regular expression to the list of installed kernels, adding the matched elements to the list of kernels to be removed.

## Feedback

The author of the issue suggested that we take advantage of this pull request to fix a pre-existing bug in the logic of `--uninstall`. The issue is as follows: if the kernel `5.5.0-rc2-VKMS` is passed, and there is an installed kernel called `5.5.0-rc2-VKMS` and another called `5.5.0-rc2-VKMS+`, both would be removed.

The other feedback is related to our decision to add a new flag to the command. According to the maintainers, ideally, we should not modify the interface. The suggestion would be to remove the flag and interpret the input as a list of elements separated by commas, where each element is a regular expression. For example, if the installed kernels are `kernel1, kernel2, kernel3`' and the input list is `kernel1, kernel[2-4]`, we want all three to be removed.
