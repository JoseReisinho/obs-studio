# Relatório Arquitectura de Software

## *OBS Studio*

O **Open Broadcast Software** é um gestor de captura utilizado para a gravação e transmição em directo de video e audio. Escrito maioritariamente em C e C++, este software permite a **captura em tempo real de janelas/aplicações e dispositivos, gestão de cenas, codificação de video/audio, gravação para ficheiro e transmissão**. A transmissão é feita através do protocolo RTMP e pode ser enviado para qualquer destino que o suporte (ex. Youtube, Twitch.tv).

O **OBS Studio** é um *rewrite* do OBS original. Com objectivo de suportar outros sistemas operativos além do Windows, conter uma API mais poderosa e uma colecção de funcionalidades mais rica.

## Arquitectura de Software

Um dos modelos usados para organizar as diferentes vistas arquitecturais em engenharia de *software* é o modelo de arquitetura 4+1. Este organiza a descrição da arquitectura de software em 5 vistas concorrentes. Cada vista trata um conjunto de objectivos específicos do projecto, de acordo com os diferentes *stakeholders*, como os utilizadores, utilizadores finais, programadores e gestores de projeto.
As vistas propostas pelo modelo são: a **vista lógia**, a **vista de implementação**, a **vista do processo**, a **vista de** **_deployment_** e a **vista de casos de uso**. Esta última serve para ilustrar e validar as demais.

## Vista Exemplo

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean in nunc risus. Ut vel erat urna. Proin rutrum pretium urna a varius. Aliquam erat volutpat. Phasellus ac velit tincidunt sem pulvinar venenatis. Fusce dictum tempor magna, finibus laoreet elit pulvinar vitae. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Morbi quis eleifend nunc, id cursus velit. Fusce pretium ipsum vitae turpis cursus, sed accumsan justo fringilla. Aliquam elementum ex urna, eu consequat magna tempor at. Cras mattis, sapien et euismod tincidunt, est magna ornare est, maximus eleifend ex mi sed libero. 

Maecenas vitae augue sollicitudin, malesuada mauris sit amet, elementum erat. Quisque maximus dignissim finibus. Sed sit amet sem iaculis, sodales elit sed, porta urna. Vivamus ut arcu placerat mauris scelerisque mattis. Phasellus nec elit enim. Praesent vestibulum scelerisque diam. Ut vel ex purus. 

![Some-View](https://github.com/JoseReisinho/obs-studio/blob/master/ArchSW-docs/Images/exemplo.png)

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean in nunc risus. Ut vel erat urna. Proin rutrum pretium urna a varius. Aliquam erat volutpat. Phasellus ac velit tincidunt sem pulvinar venenatis. Fusce dictum tempor magna, finibus laoreet elit pulvinar vitae. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Morbi quis eleifend nunc, id cursus velit. Fusce pretium ipsum vitae turpis cursus, sed accumsan justo fringilla. Aliquam elementum ex urna, eu consequat magna tempor at. Cras mattis, sapien et euismod tincidunt, est magna ornare est, maximus eleifend ex mi sed libero. 

Maecenas vitae augue sollicitudin, malesuada mauris sit amet, elementum erat. Quisque maximus dignissim finibus. Sed sit amet sem iaculis, sodales elit sed, porta urna. Vivamus ut arcu placerat mauris scelerisque mattis. Phasellus nec elit enim. Praesent vestibulum scelerisque diam. Ut vel ex purus. 

## Vista Lógica 

![Logic-View](https://github.com/JoseReisinho/obs-studio/blob/master/ArchSW-docs/Images/LogView%20(3).png)

## Vista de Implementação


## Vista de Processo

A **vista de processo** tem por objectivo ilustrar a forma como o software se divide em processos(ou threads) e se vai comportando em tempo de execução. Neste software em particular temos uma correlação directa entre a interecção do utilizador e o comportamento do programa. Por este motivo escolhemos um **diagrama de atividades** que, de uma forma muito simples, representa a paralelidade dos processos.

![Process-View](https://github.com/JoseReisinho/obs-studio/blob/master/ArchSW-docs/Images/Process%20View.png)

Como este software na sua raiz se resume a duas tarefas elementares. O diagrama de atividades acaba por ser algo bastante simples.
No momento que o software é iniciado as configurações gravadas são usadas. O utilizador tem então a opção de dar inicio à gravação e/ou dar inicio à transmissão do que pretende capturar. Ambas estas tarefas podem ser executadas em simultaneo.
E, a qualquer altura da execução do programa, o utilizador pode alterar qualquer configuração que assim pretender. Desde perfis e cenas a dispositivos de captura.
Além disto o utilizador pode repetidamente dar inicio às tarefas de transmição e gravação sem sair da aplicação. Criando um diagrama de atividades sem um fim concreto.

## Vista de *Deployment* 


## Vista de Casos de Uso


## Análise Crítica

