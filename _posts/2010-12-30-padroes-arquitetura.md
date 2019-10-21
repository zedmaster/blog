---
title:  "Evolução das Camadas nas Aplicações Corporativas"
subtitle: "Padrões de Arquitetura"
author: "Alexandre"
avatar: "img/authors/zed.jpg"
image: "img/2010-12-30/00.jpg"
date:   2015-04-21 12:12:12
---

Texto retirado do livro **Padrões de Arquitetura de Aplicações Corporativas** do Martin Fowler.


Embora eu seja jovem demais para ter feito algum trabalho nos velhos tempos dos sistemas em batch, não sinto que as pessoas pensassem muito em camadas naquele tempo. Você escrevia um programa que manipulava algum tipo de arquivo (ISAM, VSAM, etc.) e essa era sua aplicação. Não era necessário aplicar nenhuma camada.

A noção de camadas se tornou mais visíveis nos anos 90, com o advento dos cliente-servidores. Estes eram sistemas em duas camadas: o cliente mantinha a interface com o usuário e um ou outro código código da aplicação, e o servidor era normalmente um banco de dados relacional. Ferramentas comuns para o lado cliente eram, por exemplo, VB, Powerbuilder e Delphi. Essas ferramentas tornaram particularmente fácil criar aplicações que faziam uso intensivo de dados, uma vez que elas disponibilizavam componentes visuais que trabalhavam o SQL. Assim, você podeia criar uma tela arrastando controles para uma área de desenho e então usando páginas de propriedades para conectar os controles ao banco de dados.

Se a aplicação tivesse somente de exibir e fazer atualizações simples em dados ralacionais, então esses sistemas cliente-servidor funcionavam muito bem. O problema surgiu com a lógica de domínio: regras de negócio, validações, cálculos, e assim por diante. Normalmente, as pessoas escreviam essa lógica no cliente, mas isso era desejado e , normalmente, feito embutindo-se a lógica diretamente nas telas da interface com o usuário. À medida que a lógica do domínio se tornava mais complexa, ficava muito mais difícil trabalhar com este código. Além disso, embutir a lógica nas telas facilitava a duplicação de códgio, o que significava que alterações simples resultavam em buscas de código semelhante em muitas telas.


**Uma alternativa era colocar a lógica de domínio no banco de dados na forma de procedimentos armazenados (stored procedures). Estes, no entanto, forneciam mecanismos limitados de estruturação, o que mais uma vez levava o código desajeitado. Além disso, muitas pessoas gostavam de banco de dados ralacionais porque SQL era um padrão, o que lhes permitia a qualquer tempo mudar o fornecedor do banco de dados. Ainda que poucas pessoas realmente fizessem isso, muitas gostavam de ter a opção de mudar de fornecedor sem que isto implicasse em custos de migração altos demais. Por serem todos proprietários, os procedimentos armazenados eliminavam esta opção.**


Ao mesmo tempo em que a arquitetura cliente-servidor estava ganhando popularidade, o mundo o mundo orientado a objetos estava ascendendo. A comunidade de objetos tinha a resposta para o problema da lógica de domínio: migrar para um sistema em três camadas. Nesta abordagem, você tinha uma camada de apresentação para a sua interface com o usuário, uma camada de domínio para a sua lógica de domínio e uma camada de dados. Desta maneira, você poderia tirar toda a complexa lógica de domínio da interface com o usuário e coloca-la em uma camada na qual você poderia estruturá-la apropriadamente utilizando objetos.

Apesar disso, a popularidade dos objetos fez pouco progresso. A verdade era que muitos sistemas eram simples, ou pelo menos começavam simples. Embora a abordagem em três camadas tivesse muitos benefícios, o ferramental para o desenvolvimento cliente-servidor era convincente se o seu problema fosse simples. Além disso, as ferramentas para o desenvolvimento de cliente-servidor eram difíceis, ou mesmo impossíveis, de usar em uma configuração com três camadas.

Acho que o abalo sísmico aqui foi o advento da Web. De repente as pessoas passaram a querer instalar aplicações cliente-servidor usando um navegador Web. No entanto, se toda a sua lógica de negócio estivesse enterrada em um cliente rico, então toda ela precisaria ser refeita para ter uma interface Web. Um sistema bem projetado, em três camadas, poderia simplesmente acrescentar uma nova camada de apresentação e estaria pronto. Além disso, com a linguagem JAVA, vimos uma linguagem orientada a Objetos ocupar sem pudores. **As ferramentas que surgiram para criar páginas Web eram muito menos amarradas à linguagem SQL e, assim mais adaptáveis a uma terceira camada.**


### As Três Camadas Principais

**Apresentação** – diz respeito a como tratar a interação entre o usuário e o software. Isto pode ser tão simples quanto uma linha de comando ou um menu baseado em texto, porém, hoje é mais provável que seja uma interface gráfica em um cliente rico ou um navegador com interface baseada em HTML. As responsabilidades primárias da camada de apresentação são exibir informações para o usuário e traduzir comandos do usuário em ações sobre o domínio e a camada de dados.

**Lógica de domínio** – também chamada de lógica de negócio. Este é o trabalho que esta aplicação tem de fazer para o domínio com o qual você esta trabalhando. Envolve cálculos baseados nas entradas e em dados armazenados, validação de quaisquer dados provenientes da camada de apresentação e a compreensão exata de qual lógica de dados executar, dependendo dos comandos recebidos da apresentação.

**Camada de dados** – diz respeito à comunicação com outros sistemas que executam tarefas no interesse da aplicação. Estes podem ser monitores de transações, outras aplicações, sistemas de mensagem e assim por diante. Para a maioria das aplicações corporativas, a maior parte da lógica de dados é um banco de dados responsável, antes de mais nada, pelo armazenamento de dados persistentes.

Há também uma regra estabelecida sobre dependências: o domínio e a camada de dados nunca devem ser dependentes da apresentação, isto é, não deve haver chamadas de sub-rotinas da apresentação a partir do código do domínio ou da camada de dados. Essa regra torna mais fácil utilizar apresentações diferentes sobre a mesma base e torna mais fácil modificar a apresentação sem ramificações sérias mais abaixo. O relacionamento entre o domínio e a camada de dados é mais complexo e depende dos padrões arquiteturais usados para a fonte de dados.