# Linux Kernel Tutorials

### The tutorials that I will be referring to in this post are the following:
1. [Use QEMU to play with Linux](https://flusp.ime.usp.br/kernel/use-qemu-to-play-with-linux/)
2. [QEMU Libvirt setup](https://flusp.ime.usp.br/kernel/qemu-libvirt-setup/)
3. [Build Linux for ARM](https://flusp.ime.usp.br/kernel/build-linux-for-arm/)
4. [Modules Intro](https://flusp.ime.usp.br/kernel/modules-intro/)

### General experience


My experience with the tutorials was not easy in certain moments. In some cases it was caused by poor attention while reading it, or peculiarities of my machine, and also due to the tutorial not covering some aspect (or not being clear). I think the task was not easy by nature, with the amount of diverse problems that may appear along each step involved in the kernel compilation and deploy, so it would be difficult to go through all the tutorials without any setbacks. Maybe if in each tutorial step, there was a detailed description of possible problems/difficulties that might appear, it would be easier for those who are following the tutorial to detect when there was a mistake in some step or when the error is well known and easy to solve.

<!-- Minha experiência com os tutoriais não foi fácil em certos momentos. Algumas vezes por não ler com atenção o tutorial, algumas vezes por peculiaridades da minha máquina e outras por falta de cobertura do tutorial (ou falta de clareza). Acho que a tarefa não é fácil por natureza, principalmente com a quantidade de problemas diversos que podem aparecer ao longo das diversas etapas envolvidas na compilação e deploy do kernel, então seria difícil passar por todos os tutoriais ileso de dificuldades. Talvez se em cada passo do tutorial houvesse uma descrição mais detalhada sobre possíveis problemas/dificuldades que podem surgir, seria mais fácil de quem está seguindo o tutorial descobrir quando houve erro em seguir alguma etapa, e quando que o erro é recorrente e de fácil resolução. -->


### Experience in each tutorial

The first setback was my fault because I thought the tutorials would work on macOS. When running the first commands, I already realized that the support for this OS would not be sufficient for completing any of the tutorials. After changing to Linux, I managed to complete the first two tutorials without any big problems.

The third tutorial was also a pain in the neck, mostly to discover how to install all the missing dependencies needed to compile the kernel. The terminal returned some errors, and it was necessary to search for each of them on the web to understand how to solve them. I think all the problems were solved by installing some missing dependencies on my machine, but after each installation, I needed to run `make` again to check if the problems were gone. Another setback was that the compilation output sometimes didn't indicate that the compilation had errors, which also caused confusion.


The fourth tutorial was by far the most troubled. In the end, I could complete it, and everything worked correctly, but I'm not sure how it happened, since all the attempts to make it work could influence each other, so I don't know what the key point for completing it was. Basically, the problems started while saving the `.config`. When running the following command: \\
`time make O=../iio_workshop_build/ KCONFIG_CONFIG=../iio_workshop_build/.config Image.gz modules -j4` \\
an error appeared saying I needed to run another command, `make mrproper`, which apparently deleted the `.config`. At this moment, I also got confused about where the `../iio_workshop_build/` directory came from and why it should contain the `.config` previously generated. Another detail of this command is that the `-j4` flag may not be ideal for each machine, which can cause slowness when compiling.
Even after running this command, I had compilation problems which prevented me from generating the correct kernel image. I decided to run different variations of this command, for example without the `O=`, or without `Image.gz modules`, or even just `make`. In the end, some of them made it work, and I could complete the rest of the tutorial without further problems.

<!-- A primeira dificuldade ocorreu (por minha culpa) pois pensei que os tutoriais funcionariam no macOS, porém ao rodar os primeiros comandos já percebi que o suporte para esse SO não seria suficiente para completar nenhum dos tutoriais. Depois de trocar para o Linux consegui completar os dois primeiros tutoriais sem grandes problemas. 

O terceiro tutorial causou uma certa dor de cabeça também, principalmente para descobrir como instalar as dependências faltantes na hora de compilar o kernel. O terminal devolvia alguns erros e era necessário pesquisar na web cada um deles e entender como resolver. Creio que todos eles foram resolvidos instalando alguma dependência faltante na minha máquina, mas a cada instalação era necessário rodar o make novamente para checar se os problemas já haviam sumido. Outro problema é que a saída da compilação por vezes não indicava claramente que havia ocorrido algum erro, o que também causa confusão.
 -->
<!-- O quarto tutorial foi de longe o mais conturbado. No fim consegui completá-lo e tudo funcionou, mas para ser sincero nem tenho certeza como isso aconteceu, já que as diversas tentativas de fazer funcionar podem ter influenciado uma a outra e por isso não sei o que foi crucial para completá-lo. Basicamente os problemas iniciaram ao salvar o arquivo .config, já que ao rodar o comando seguinte:
`
time make O=../iio_workshop_build/ KCONFIG_CONFIG=../iio_workshop_build/.config Image.gz modules -j4
`
era dado um aviso de que precisaria ser rodado outro comando, `make mrproper`, que aparentemente deletava o `.config`. Nessa parte fica confuso também de onde surge o diretório `../iio_workshop_build/`, que aparentemente deveria conter o arquivo `.config` gerado anteriormente. Outro detalhe desse comando é que o `-j4` pode não ser ideal para a máquina de cada um, levando a possível lentidão na hora de compilar. -->
<!-- Mesmo depois de conseguir rodar esse comando, tive problemas na compilação que impediram a geração da imagem corretamente. Decidi rodar diferentes variações desse comando, sem o `O=`, sem o `Image.gz modules,` apenas o `make`, etc. e no fim algum deles funcionou e consegui completar o restante do tutorial sem mais problemas. -->
