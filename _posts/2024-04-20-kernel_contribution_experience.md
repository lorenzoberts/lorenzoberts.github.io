# Linux Kernel Contribution

### What have we done?
	
We refactored a small driver implementation to prevent memory leak when the developer forgets to free a reference. Besides that, this modification also made error handling clearer. The contribution consists of using a macro called `device_for_each_child_node_scoped()` instead of `device_for_each_child_node()`.

In the **ti-ads131e08** driver, when the loop:

```c
for (child = device_get_next_child_node(dev, NULL); child;    \
     	child = device_get_next_child_node(dev, child))
```

 finished early, a `goto` was used for the logic of freeing the reference to `child` and returning. With the macro `device_for_each_child_node_scoped()` we could remove the `goto` and just return the function result instead.

### Motivation

As we were more interested in the process of producing the patch than in the contribution itself, we decided to choose a simple task that didn't require much context about the `iio` subsystem. Also, we had a messy experience installing and compiling the kernel, so we were more cautious this time. We preferred a chore that did not demand much time, so we could put more effort into the patch-sending process.

### Difficulties

The change itself was simple, but we had problems while trying to compile the modified code. The errors indicated that the macro `device_for_each_child_node_scoped()` did not exist. We tried to find the file where the macro should be, but we didn't achieve success. Analyzing the modification introduced by the last commit, we found out that the branch we were in was not updated since 2022. Because of that, the desired macro hadn't yet been implemented.
We tried to reach an updated branch so we could send the modification, but this was only clarified during the class with the monitor's help. After obtaining the correct branch for development, we only had to re-do the modification and send the patch.

<!-- ### O que fizemos?
	
Refatoramos o código de um driver para evitar vazamento de memória caso o desenvolvedor esquecesse de liberar uma referência. Além disso, essa modificação também deixou o tratamento de erro mais claro.
No caso do nosso driver, sempre que o loop

for (child = device_get_next_child_node(dev, NULL); child;    \
     	child = device_get_next_child_node(dev, child))

terminava cedo, utilizava-se um goto para a lógica de liberar a referência e retornar. Com o uso da macro device_for_each_child_node_scoped(), pudemos excluir o goto e apenas devolver o resultado da função.

### Motivação

Como estávamos mais interessados no processo de produção do patch, e não na contribuição em si, decidimos escolher uma tarefa simples e que não exigisse muito contexto a respeito do subsistema. Além disso, tivemos uma experiência conturbada com a instalação e compilação do kernel, entã### What have we done?
	
We refactored a small driver implementation to prevent memory leak when the developer forgets to free a reference. Besides that, this modification also made error handling clearer. The contribution consists of using a macro called `device_for_each_child_node_scoped()` instead of `device_for_each_child_node()`.

In the **ti-ads131e08** driver, when the loop finished early, a `goto` was used for the logic of freeing the reference to `child` and returning. With the macro `device_for_each_child_node_scoped()` we could remove the `goto` and just return the function result instead.

### Motivation

As we were more interested in the process of producing the patch than in the contribution itself, we decided to choose a simple task that didn't require much context about the `iio` subsystem. Also, we had a messy experience installing and compiling the kernel, so we were more cautious this time. We preferred a chore that did not demand much time, so we could put more effort into the patch-sending process.

### Difficulties

The change itself was simple, but we had problems while trying to compile the modified code. The errors indicated that the macro `device_for_each_child_node_scoped()` did not exist. We tried to find the file where the macro should be, but we didn't achieve success. Analyzing the modification introduced by the last commit, we found out that the branch we were in was not updated since 2022. Because of that, the desired macro hadn't yet been implemented.
We tried to reach an updated branch so we could send the modification, but this was only clarified during the class with the monitor's help. After obtaining the correct branch for development, we only had to re-do the modification and send the patch.
o ficamos mais precavidos nessa segunda fase. Preferimos uma tarefa que não demandasse muito tempo, de forma que pudéssemos colocar mais esforço no processo de envio do patch. 

### Dificuldades

A alteração necessária era simples, porém encontramos um problema ao tentar compilar o código modificado. Os erros indicavam que a macro device_for_each_child_node_scoped() não existia. Tentamos achar o arquivo onde essa macro estaria definida, mas não obtivemos sucesso. Analisando a modificação introduzida pelo último commit, descobrimos que a branch que estávamos não era atualizada desde 2022. Por isso, a macro desejada ainda não havia sido implementada.

Procuramos por uma branch atualizada para enviarmos a modificação, mas só conseguimos esclarecer isso durante a aula, com a ajuda dos monitores. Depois de obter a branch correta para desenvolvimento, bastou fazer a alteração no driver e enviar o patch.
 -->