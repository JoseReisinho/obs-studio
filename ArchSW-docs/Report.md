# Relatório Arquitectura de Software

## *OBS Studio*

O **Open Broadcast Software** é um gestor de captura utilizado para a gravação e transmissão em direto de vídeo e áudio. Escrito maioritariamente em C e C++, este software permite a **captura em tempo real de janelas/aplicações e dispositivos, gestão de cenas, codificação de vídeo/áudio, gravação para ficheiro e transmissão**. A transmissão é feita através do protocolo RTMP e pode ser enviado para qualquer destino que o suporte (ex. Youtube, Twitch.tv).

O **OBS Studio** é um *rewrite* do OBS original. Com objetivo de suportar outros sistemas operativos além do Windows, conter uma API mais poderosa e uma colecção de funcionalidades mais rica.

## Arquitectura de Software

Um dos modelos usados para organizar as diferentes vistas arquitecturais em engenharia de *software* é o modelo de arquitetura 4+1. Este organiza a descrição da arquitectura de software em 5 vistas concorrentes. Cada vista trata um conjunto de objetivos específicos do projeto, de acordo com os diferentes *stakeholders*, como os utilizadores, utilizadores finais, programadores e gestores de projeto.
As vistas propostas pelo modelo são: a **vista lógica**, a **vista de implementação**, a **vista do processo**, a **vista de** **_deployment_** e a **vista de casos de uso**. Esta última serve para ilustrar e validar as demais.

## Vista Lógica 

A **Vista Lógica** ilustra a funcionalidade que o software disponibiliza ao *end-user*. Representa também pedaços do sistema divididos em agrupamentos lógicos, mostrando as dependências entre eles.

![Logic-View](https://github.com/JoseReisinho/obs-studio/blob/master/ArchSW-docs/Images/LogView%20(3).png)

No OBS Studio em particular o utilizador consegue através de apenas uma janela, acima representada como *GUI*, executar todas as funcionalidades que lhe são disponibilizadas. Abrir projetos anteriormente criados, definir e editar as *sources* que está a capturar, criar *scenes* para organizar as *sources*, etc
Em simultâneo o cliente devolve em tempo real uma *preview* da *scene* que está a ser capturada.
Também em simultâneo o utilizador pode optar por guardar localmente o que está a capturar e/ou fazer *streaming* da captura para um dispositivo ou software que receba a transmissão em formato RTMP.

A secção a verde serve para ilustrar a dependência de três componentes em particular. Todas as configurações são gravadas num perfil. Um perfil contém várias *scenes* entra as quais o utilizador pode alternar durante a captura. E cada *scene* contém uma colecção de *sources* que compôem a *scene*. Podem ser imagens, janelas de programas, uma câmara de vídeo, etc.

## Vista de Implementação

A **Vista de Implementação** tem por objetivo ilustrar as ligações e dependências entre classes e objetos usados no programa, nomeadamente no seu funcionamento *core*.
Este *software* está feito em forma de vários componentes separados em diretórios de forma a encapsular os seus elementos como a parte gráfica(*GUI*), *plugins*, e funcionalidade principal(*core*). Este diagrama e feito sobre a funcionalidade *core* que realiza a captura e tratamento de informação.

![Implementation-View](https://github.com/JoseReisinho/obs-studio/blob/master/ArchSW-docs/Images/ImpView1.png)
![Implementation-View](https://github.com/JoseReisinho/obs-studio/blob/master/ArchSW-docs/Images/ImpView2.png)

Diagramas gerados com **_graphviz_** que apresentam as dependências entre ficheiros que refletem a interação entre as classes **obs_scene** e **obs_internal** que tratam de tudo que mostra no ecrã e o seu funcionamento interno.

## Vista de Processo

A **Vista de Processo** tem por objetivo ilustrar a forma como o software se divide em processos(ou *threads*) e se vai comportando em tempo de execução. Neste software em particular temos uma correlação direta entre a interação do utilizador e o comportamento do programa. Por este motivo escolhemos um **diagrama de atividades** que, de uma forma muito simples, representa a paralelidade dos processos.

![Process-View](https://github.com/JoseReisinho/obs-studio/blob/master/ArchSW-docs/Images/Process%20View.png)

Como este software na sua raiz se resume a duas tarefas elementares. O diagrama de atividades acaba por ser algo bastante simples.
No momento que o software é iniciado as configurações gravadas são usadas. O utilizador tem então a opção de dar inicio à gravação e/ou dar inicio à transmissão do que pretende capturar. Ambas estas tarefas podem ser executadas em simultâneo.
E, a qualquer altura da execução do programa, o utilizador pode alterar qualquer configuração que assim pretender. Desde perfis e cenas a dispositivos de captura.
Além disto o utilizador pode repetidamente dar inicio às tarefas de transmissão e gravação sem sair da aplicação. Criando um diagrama de atividades sem um fim concreto.

## Vista de *Deployment*

A **Vista de _Deployment_** é usada para modelar o *deployment* físico de nós e artefactos.
Neste caso em particular, os nós são os componentes de hardware e os artefactos são os componentes de software que correm nesse hardware.

![Deployment View](https://github.com/JoseReisinho/obs-studio/blob/master/ArchSW-docs/Images/Deployment%20View.png)

Acima temos a Vista de *Deployment* a que chegamos. No OBS Studio o único componente de hardware presente é o dispositivo que executa o programa, aqui ilustrado como um PC, mas pode ser qualquer dispositivo a correr um sistema operativo suportado (Android, Windows, Macbook, etc).
Existe uma possível ligação a um servidor quando está uma transmissão a ser feita, mas este é enviado por RTMP e recebido por um *3rd party software*. Não há a necessidade do OBS Studio ser *deployed* neste dispositivo de destino.
Existe também uma ligação a recursos físicos ligados ao computador. Uma webcam, um microfone ou uma placa de aquisição de vídeo. Mas tudo isto são *components* ligados ao dispositivo a executar o OBS Studio, e não dependem diretamente dele.

## Vista de Casos de Uso

A **Vista de Casos de Uso** ou **Vista de Cenários** é uma lista de acções ou passos que definem a interação entre um *actor* e o sistema a fim de atingir um objetivo em particular.
Um *actor* tem de ser capaz de fazer decisões, mas não tem de ser humano, pode ser, por exemplo, uma empresa, uma organização ou até um programa ou sistema de informação.
Uma pessoa pode exercer diferentes papeis como *actor*. No caso do OBS Studio, um utilizador pode por exemplo apenas usar a função de *recording*. Enquanto que outro pode simultaneamente incluir o *streaming*.

A Vista de Casos de Uso pode ser representada de várias formas. Enquanto que numa primeira fase um diagrama feito pelo *stakeholder* possa ser suficiente, em alguns casos pode ser necessário ter mais informação, ou mais detalhe. No nosso diagrama, uma tabela dividida entre *"User Input"* e *"System Response"* poderia ser, por exemplo, um bom complemento ao diagrama apresentado.
O mais importante nesta vista é alcançar um nível de abstração que proporcione a qualquer pessoa uma *overview* do sistema em poucos minutos e sem qualquer tipo de conhecimento a nível técnico do sistema.

Em baixo encontra-se a Vista de Casos de Uso a que chegamos para o OBS Studio.

![Use Cases View](https://github.com/JoseReisinho/obs-studio/blob/master/ArchSW-docs/Images/Use%20Cases.png)

## Análise Crítica

Na Vista de Implementação tivemos de recorrer a este método de apresentação pois um único grafo de relações entre as classes torna a navegação muito complicada para qualquer pessoa que olhe. Dois gráficos de relação entre os ficheiros que interessam conseguem transmitir a mensagem, apesar de não serem o ideal, refletindo o que é necessário para a tarefa pedida.

## Referências
http://epf.eclipse.org/wikis/openup/core.tech.common.extend_supp/guidances/examples/four_plus_one_view_of_arch_9A93ACE5.html


