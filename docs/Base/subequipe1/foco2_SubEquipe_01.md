# Foco 02: Engenharia Reversa e BPMN

## Introdução

Este documento apresenta os resultados da Engenharia Reversa realizada pela Sub-equipe 01, com foco nos principais fluxos de autenticação e gerenciamento de conta da plataforma analisada. A partir da observação prática desses fluxos, foram elaborados diagramas utilizando a notação **BPMN (Business Process Model and Notation)**, com o objetivo de representar de forma clara e estrutura das interações entre o usuário e o sistema, bem como os pontos de decisão presentes em cada processo.

## Contexto

Para a realização da Engenharia Reversa, foram inicialmente determinados casos de teste que guiaram a navegação e observação dos fluxos analisados. A análise foi conduzida utilizando **exclusivamente a interface do site base**, sem acesso ou análise ao código-fonte da aplicação, o levantamento das etapas, decisões e comportamentos do sistema foram feito por meio da interação direta com a plataforma, como faria um usuário comum.

## Escopo

A análise está concentrada nos seguintes fluxos:

- Login;
- Login social;
- Cadastro;
- Recuperação de acesso;
- Alteração de senha;
- Logout;
- Gerenciamento do perfil;
- Proteção das informações da conta;
- Privacidade e visibilidade dos dados.

## Metodologia

A metodologia adotada consiste na realização de **Engenharia Reversa** sobre os fluxos de autenticação e gerenciamento de conta da plataforma analisada. A partir da observação das interações disponíveis ao usuário, foram identificadas as etapas, decisões e comportamentos apresentados pelo sistema.

Posteriormente, os fluxos identificados foram organizados e representados utilizando a notação **BPMN (Business Process Model and Notation)**, permitindo uma representação visual e estruturada das atividades realizadas pelo usuário e pelo sistema.

## Processo de Engenharia Reversa Aplicado

O processo de Engenharia Reversa foi realizado a partir da navegação e observação dos fluxos de **login, alteração de senha e cadastro** da plataforma analisada.

Durante a análise, foram identificadas as ações executadas pelo usuário, as respostas fornecidas pelo sistema e os pontos de decisão existentes em cada fluxo. Essas informações serviram como base para a construção dos modelos BPMN apresentados nesta página.

## Modelagem BPMN

Foi utilizada a notação **BPMN (Business Process Model and Notation)** para representar os fluxos identificados durante a Engenharia Reversa.

A modelagem foi realizada utilizando a ferramenta [**Miro**](https://miro.com/pt/), reunindo em uma representação estruturada os principais elementos observados nos processos de login, alteração de senha e cadastro.

### Diagrama 1: Login

<p align="center">
    <img src="Base/assets/Subgrupo1.1.1/diagrama/Login.png" alt="Diagrama BPMN do fluxo de login" width="100%">
</p>

<p align="center">
    <em>Figura 1: Diagrama BPMN do fluxo de login. Autor: Samuel Felipe.</em>
</p>

### Diagrama 2: Alteração de senha

<p align="center">
    <img src="Base/assets/Subgrupo1.1.1/diagrama/Recuperacao_senha.png" alt="Diagrama BPMN do fluxo de alteração de senha" width="100%">
</p>

<p align="center">
    <em>Figura 2: Diagrama BPMN do fluxo de alteração de senha. Autor: Samuel Felipe.</em>
</p>

### Diagrama 3: Cadastro

<p align="center">
    <img src="Base/assets/Subgrupo1.1.1/diagrama/Cadastro.png" alt="Diagrama BPMN do fluxo de cadastro" width="100%">
</p>

<p align="center">
    <em>Figura 3: Diagrama BPMN do fluxo de cadastro. Autor: Samuel Felipe.</em>
</p>

## Piscinas e Raias

Nos três diagramas, a modelagem é dividida em duas raias:

- **Usuário:** representa o ator que interage diretamente com o sistema e executa as ações necessárias para alcançar seu objetivo;
- **Sistema:** representa as operações realizadas pelo sistema durante a execução do fluxo.

Essa divisão foi adotada para diferenciar visualmente as ações realizadas pelo usuário das respostas e operações executadas pelo sistema.

## Fluxos Modelados

### 1. Login

O usuário decide realizar o login em sua conta e informa suas credenciais. Em seguida, o gateway **"Credenciais corretas?"** determina o caminho a ser seguido.

- **Sim:** o usuário é redirecionado para a tela principal do sistema com o login efetuado;
- **Não:** o fluxo retorna à etapa de inserção das credenciais, permitindo que o usuário tente novamente.

### 2. Alteração da senha

O usuário decide alterar a senha de sua conta e informa seu e-mail cadastrado. O gateway **"E-mail existe na base de dados?"** determina o caminho do fluxo.

- **Sim:** o sistema envia um link de redefinição de senha, permitindo que o usuário altere sua senha e mantenha seu cadastro atualizado;
- **Não:** o processo não prossegue, levando o usuário a reiniciar o fluxo.

### 3. Cadastro

O usuário decide criar uma conta no sistema e informa seus dados. O gateway **"Os dados são válidos?"** determina o caminho do fluxo.

- **Sim:** os dados são registrados na base de dados e o cadastro é concluído;
- **Não:** o fluxo retorna à etapa de preenchimento e validação dos dados, permitindo que o usuário faça as correções necessárias.

## Legenda de Notação

- **Gateway Exclusivo (◇ com X):** representa uma decisão excludente, na qual apenas um dos caminhos disponíveis é seguido;
- **Fluxo de Sequência:** representa a ordem em que as atividades e eventos são executados dentro do processo.

A lógica dos diagramas foi validada a partir das observações realizadas durante a Engenharia Reversa, garantindo a coerência entre os fluxos identificados e sua representação em BPMN.

## Referências Bibliográficas

- IBM. **O que é modelagem e notação de processos de negócios (BPMN)?** Disponível em: <https://www.ibm.com/br-pt/think/topics/bpmn>.

- SYDLE. **Notação BPMN: como aplicar para modelar processos?** Disponível em: <https://www.sydle.com/br/blog/notacao-bpmn-5ef510823130175de40cc4c2>.

- MIRO. **Diagrama BPMN.** Disponível em: <https://miro.com/pt/diagrama/o-que-e-bpmn/>.

- PROCESSMIND. **BPMN 2.0 Poster.** Disponível em: <https://processmind.com/resources/docs/reference/download-the-bpmn-2-0-poster-in-your-language>.

## Histórico de Versões

| Versão | Data | Descrição | Autor(es) | Revisor(es) |
| --- | --- | --- | --- | --- |
| 1.0 | 27/08/2026 | Criação da página do Foco 02 da Sub-equipe 01 | [Samuel Felipe](https://github.com/TerminaKng05) | ----- |
| 1.1 | 27/08/2026 | Adição das informações sobre a modelagem BPMN | [Samuel Felipe](https://github.com/TerminaKng05) | ----- |
| 1.2 | 27/08/2026 | Correção links quebrados| [Dylan Cavalcante](https://github.com/dylancavalcante) | A definir |
| 1.3 | 28/08/2026 | Adição da introdução e contexto| [Mariana Ribeiro](https://github.com/marianagonzaga0) | A definir |
