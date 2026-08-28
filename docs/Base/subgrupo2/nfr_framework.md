# NFR Framework

A modelagem dos requisitos não funcionais da Sub-equipe 02 foi realizada utilizando o **NFR Framework**, tendo como softgoal principal a **Acessibilidade da Decathlon**. O SIG foi elaborado a partir das preocupações identificadas durante a análise da interface, buscando representar o refinamento da acessibilidade em aspectos mais específicos e relacioná-los a possíveis operacionalizações.

## Softgoal principal

O softgoal **Acessibilidade Decathlon** representa a preocupação central de qualidade considerada nesta modelagem. A partir dele, foram definidos três refinamentos principais:

- **Operabilidade por Teclado**;
- **Perceptibilidade**;
- **Adaptabilidade ao zoom de 200%**.

Esses refinamentos permitem analisar a acessibilidade da interface a partir de diferentes aspectos observados durante a avaliação.

## Refinamento dos softgoals

O softgoal **Operabilidade por Teclado** foi refinado em:

- **Navegação Sequencial**;
- **Acionamento de Controles**;
- **Ordem de Foco Coerente**.

Esses elementos representam preocupações relacionadas à utilização da interface sem depender exclusivamente do mouse, considerando a possibilidade de percorrer os elementos da página, acionar seus controles e manter uma sequência de foco compreensível.

O softgoal **Perceptibilidade** foi refinado em **Foco Visual Perceptível**, relacionado à necessidade de o usuário conseguir identificar visualmente qual elemento da interface está em foco durante a navegação.

Por sua vez, o softgoal **Adaptabilidade ao zoom de 200%** foi refinado em:

- **Legibilidade do Conteúdo**;
- **Operabilidade dos Controles**.

Esses elementos representam preocupações relacionadas ao comportamento da interface quando seu conteúdo é ampliado, considerando tanto a apresentação das informações quanto a possibilidade de continuar utilizando seus controles.

## Operacionalizações

A partir dos refinamentos, foram representadas no SIG operacionalizações que tornam as preocupações de qualidade mais concretas.

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

## SIG de Acessibilidade

<p align="center"><b>Figura 1</b> - SIG de Acessibilidade da Decathlon na notação do NFR Framework</p>

<p align="center">
  <img src="Base/assets/Subgrupo1.1.2/SIGNFRDecathlon.png" alt="SIG de Acessibilidade da Decathlon" width="800">
</p>

<p align="center"><sub>Fonte: Elaborado pelos autores (Diassis Bezerra Nascimento, Nayra Silva Nery e Uires Carlos de Oliveira), 2026.</sub></p>

## Claim identificado

Durante a análise da interface com ampliação de 200%, foi registrado no SIG o claim **"Filtros parcialmente fora da área visível"**.

| Claim | Softgoal relacionado | Contribuição |
| --- | --- | --- |
| Filtros parcialmente fora da área visível | Legibilidade do Conteúdo | Negativa |

O claim registra uma evidência observada durante a avaliação da interface. Nesse caso, a presença de filtros parcialmente fora da área visível representa uma contribuição negativa para a **Legibilidade do Conteúdo**, evidenciando uma limitação na adaptação da interface ao zoom de 200%.

## Relação com o Rich Picture

O [Rich Picture](/Base/subgrupo2/rich_picture.md) elaborado anteriormente permitiu levantar preocupações relacionadas à utilização da interface, incluindo a navegação por teclado, a interpretação dos controles e aspectos de acessibilidade.

A construção do SIG aprofundou essas preocupações ao representar a **Acessibilidade da Decathlon** como softgoal e refiná-la em aspectos específicos relacionados à operabilidade por teclado, perceptibilidade e adaptação da interface ao zoom de 200%.

Dessa forma, os dois artefatos apresentam continuidade na análise: o Rich Picture auxilia na compreensão e identificação inicial das preocupações do domínio, enquanto o NFR Framework permite estruturar e refinar as preocupações de qualidade.

## Rastreabilidade dos resultados

A modelagem mantém uma relação entre as preocupações identificadas durante a análise e os elementos representados no SIG.

De forma resumida, a rastreabilidade pode ser representada como:

**Análise da interface -> preocupações de acessibilidade -> softgoal -> refinamentos -> operacionalizações -> evidências observadas -> claim.**

## Bibliografia



## Histórico de versões

| Versão | Data | Descrição | Autores | Revisor |
| --- | --- | --- | --- | --- |
| 1.0 | 27/08/2026 | Documentação do NFR Framework da Sub-equipe 02 | Diassis Bezerra Nascimento | A definir |
