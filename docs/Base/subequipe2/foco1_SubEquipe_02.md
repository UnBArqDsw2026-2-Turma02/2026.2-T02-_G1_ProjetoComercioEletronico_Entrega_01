# Foco 01: Artefatos Generalistas & NFR

Este foco reúne o artefato generalista e o SIG na notação do NFR Framework produzidos pela Sub-equipe 02.

## Participantes

| Participante |
| --- |
| Diassis Bezerra Nascimento |
| Nayra Silva Nery |
| Uires Carlos de Oliveira |

## Metodologia

A equipe adotou uma abordagem colaborativa e iterativa para o desenvolvimento dos artefatos deste foco. Com base nos materiais disponibilizados pela professora, os membros realizaram reuniões nos dias 24 e 25 de agosto de 2026, com participação integral dos integrantes em ambos os encontros, utilizando a plataforma Microsoft Teams como principal ferramenta de comunicação e alinhamento remoto.

O processo de trabalho foi estruturado em duas etapas principais. Na reunião do dia 24, dada a natureza mais livre e exploratória do Rich Picture, sua elaboração ocorreu por meio de uma sessão de brainstorming em equipe, na qual os membros puderam representar de forma colaborativa sua compreensão do problema e do contexto do software. No dia 25, com base nas discussões e na engenharia reversa do software analisado, conduziu-se a construção do SIG na notação do NFR Framework, permitindo a identificação e o refinamento dos critérios de qualidade relevantes ao sistema.

## Rich Picture

<p align="center"><b>Figura 1</b> - Rich Picture do subdomínio Projeto Comércio Eletrônico</p>

<p align="center">
  <img src="Base/assets/Subgrupo1.1.2/RichPicture.jpg" alt="Rich Picture - Sub-equipe 02" width="600">
</p>

<p align="center"><sub>Fonte: Elaborado pelos autores (Diassis Bezerra Nascimento, Nayra Silva Nery e Uires Carlos de Oliveira), 2026.</sub></p>

O Rich Picture representa o subdomínio de navegação e descoberta de conteúdo da plataforma de comércio eletrônico da Decathlon, ilustrando a relação entre o usuário, a homepage do site e a própria empresa. O usuário é representado com a necessidade central de encontrar o que procura, interagindo com a homepage por meio da navegação, enquanto a Decathlon utiliza essa mesma página para oferecer conteúdo com o objetivo de converter visitas em vendas.

A partir da homepage, dois fluxos de descoberta são destacados: o primeiro, relacionado à navegação por modalidade, categoria e listagem de produtos, evidenciando a hierarquia de busca disponível ao usuário; o segundo, relacionado às campanhas e promoções, que aparecem em banners e carrosséis na própria página inicial.

O artefato também evidencia preocupações transversais de qualidade, representadas na forma de questionamentos críticos levantados pela equipe, tais como:

- aderência da página às normas de acessibilidade;
- correta interpretação dos controles por leitores de tela;
- funcionalidade da navegação via teclado, usando Tab e Enter;
- facilidade de busca para o usuário;
- equilíbrio entre destacar ofertas promocionais e preservar a clareza da navegação.

Esses pontos sinalizam requisitos não funcionais, sobretudo relacionados à usabilidade e à acessibilidade, que posteriormente fundamentaram a construção do SIG na notação do NFR Framework.

## NFR Framework

A modelagem dos requisitos não funcionais foi realizada utilizando o NFR Framework, tendo como softgoal principal a **Acessibilidade da Decathlon**. O SIG foi elaborado a partir das preocupações identificadas durante a análise da interface, buscando representar o refinamento da acessibilidade em aspectos mais específicos e relacioná-los a possíveis operacionalizações.

### Softgoal principal

O softgoal **Acessibilidade Decathlon** representa a preocupação central de qualidade considerada nesta modelagem. A partir dele, foram definidos três refinamentos principais:

- **Operabilidade por Teclado**;
- **Perceptibilidade**;
- **Adaptabilidade ao zoom de 200%**.

### Refinamento dos softgoals

O softgoal **Operabilidade por Teclado** foi refinado em:

- **Navegação Sequencial**;
- **Acionamento de Controles**;
- **Ordem de Foco Coerente**.

O softgoal **Perceptibilidade** foi refinado em **Foco Visual Perceptível**, relacionado à necessidade de o usuário conseguir identificar visualmente qual elemento da interface está em foco durante a navegação.

O softgoal **Adaptabilidade ao zoom de 200%** foi refinado em:

- **Legibilidade do Conteúdo**;
- **Operabilidade dos Controles**.

### Operacionalizações

| Softgoal refinado | Operacionalização |
| --- | --- |
| Navegação Sequencial | Permitir percurso sequencial com Tab |
| Acionamento de Controles | Permitir acionamento com Enter |
| Ordem de Foco Coerente | Manter ordem de foco coerente |
| Foco Visual Perceptível | Exibir contorno visual no foco |
| Legibilidade do Conteúdo | Reorganizar interface com zoom de 200% |
| Operabilidade dos Controles | Manter controles operáveis em 200% |

As operacionalizações relacionadas à navegação sequencial, ao acionamento dos controles, à ordem de foco, ao foco visual e à operabilidade dos controles apresentam contribuições positivas para os respectivos softgoals representados no SIG.

No caso da **Legibilidade do Conteúdo**, a avaliação também evidenciou uma contribuição negativa relacionada ao comportamento da interface quando submetida à ampliação de 200%.

### SIG de Acessibilidade

<p align="center"><b>Figura 2</b> - SIG de Acessibilidade da Decathlon na notação do NFR Framework</p>

<p align="center">
  <img src="Base/assets/Subgrupo1.1.2/SIGNFRDecathlon.png" alt="SIG de Acessibilidade da Decathlon" width="800">
</p>

<p align="center"><sub>Fonte: Elaborado pelos autores (Diassis Bezerra Nascimento, Nayra Silva Nery e Uires Carlos de Oliveira), 2026.</sub></p>

### Claim identificado

Durante a análise da interface com ampliação de 200%, foi registrado no SIG o claim **"Filtros parcialmente fora da área visível"**.

| Claim | Softgoal relacionado | Contribuição |
| --- | --- | --- |
| Filtros parcialmente fora da área visível | Legibilidade do Conteúdo | Negativa |

O claim registra uma evidência observada durante a avaliação da interface. Nesse caso, a presença de filtros parcialmente fora da área visível representa uma contribuição negativa para a **Legibilidade do Conteúdo**, evidenciando uma limitação na adaptação da interface ao zoom de 200%.

## Rastreabilidade dos resultados

A modelagem mantém uma relação entre as preocupações identificadas durante a análise e os elementos representados no SIG.

De forma resumida, a rastreabilidade pode ser representada como:

**Análise da interface -> preocupações de acessibilidade -> softgoal -> refinamentos -> operacionalizações -> evidências observadas -> claim.**

## Bibliografia

1. SERRANO, Milene. **Arquitetura & Desenho de Software**. Faculdade de Ciências e Tecnologias em Engenharia, Universidade de Brasília (FCTE/UnB). Disponível em: [FCTE_ARQ-DSW](https://sites.google.com/view/unb-fcte-arqdsw). Acesso em: 27 ago. 2026.

## Histórico de versões

| Versão | Data | Descrição | Autores | Revisor |
| --- | --- | --- | --- | --- |
| 1.0 | 27/08/2026 | Criação da página do Foco 01 da Sub-equipe 02 | Diassis Bezerra Nascimento | Nayra Nery |
| 1.1 | 28/08/2026 | Contribuição na elaboração do Rich Picture e do SIG na notação do NFR Framework, incluindo pesquisas, análise dos requisitos de acessibilidade e indicação da ferramenta diagrams.net | Uires Carlos de Oliveira | Nayra Nery |
