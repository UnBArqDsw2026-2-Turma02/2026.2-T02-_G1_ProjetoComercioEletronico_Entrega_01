# Foco 02: Engenharia Reversa & BPMN

Este foco reúne o processo de Engenharia Reversa realizado pela Sub-equipe 02 no site de comércio eletrônico da Decathlon e a modelagem, na notação BPMN, do fluxo de busca, seleção e compra de produtos identificado durante a análise.

## Participantes

| Participante | Atuação |
| --- | --- |
| Uires Carlos de Oliveira | Autor principal |
| Diassis Bezerra Nascimento | Coparticipante |
| Nayra Silva Nery | Coparticipante |

## Metodologia

O desenvolvimento do Foco 02 foi conduzido por Uires Carlos de Oliveira, como autor principal, com a coparticipação de Diassis Bezerra Nascimento e Nayra Silva Nery.

A Sub-equipe 02 adotou uma abordagem colaborativa e iterativa para analisar o subdomínio de navegação, descoberta, seleção e compra de produtos na plataforma de comércio eletrônico da Decathlon.

Como a equipe não teve acesso ao código-fonte, ao banco de dados, às APIs ou à documentação interna da plataforma, a Engenharia Reversa foi realizada a partir da observação da interface e do comportamento externamente visível do sistema.

Durante a análise, foram observados diferentes fluxos e páginas da Decathlon, incluindo a página inicial, menus de navegação, páginas de modalidade, categorias, listagens de produtos, página individual de produto, carrinho e etapas de finalização da compra. A organização dos registros de Engenharia Reversa foi planejada em três documentos individuais da Sub-equipe 02, sendo um documento de Diassis Bezerra Nascimento, um de Nayra Silva Nery e um de Uires Carlos de Oliveira.

A investigação combinou duas estratégias:

- **observação estática:** identificação dos menus, campos de pesquisa, filtros, botões, banners, carrosséis, cards e demais elementos visuais;
- **análise dinâmica:** execução de ações de pesquisa, navegação por modalidades e categorias, aplicação de filtros, ordenação, seleção de produtos, escolha de variações, inclusão no carrinho e avanço no processo de compra.

As evidências encontradas foram registradas em documentos produzidos pela equipe. Posteriormente, as ações e decisões observadas foram organizadas em um fluxo de maior nível de abstração e representadas na notação BPMN.

Foram utilizados:

- o site da Decathlon como objeto de análise;
- o Microsoft Teams para comunicação e alinhamento;
- documentos de texto para registrar as evidências;
- o Bizagi Modeler para elaborar o BPMN;
- o GitHub para armazenar e versionar os artefatos.

## Artefatos de Engenharia Reversa

| Integrante | Artefato / Documento | Descrição e objetivo | Link do comprobatório | Contribuição |
| :--- | :--- | :--- | :---: | :--- |
| Diassis Bezerra Nascimento | **Relatório de Engenharia Reversa da Página Inicial da Decathlon** | Análise da homepage da Decathlon com foco em navegabilidade e acessibilidade, contemplando fluxos entre modalidades e categorias, testes exploratórios com teclado e zoom, requisitos recuperados e modelo navegacional. | [Visualizar Relatório (PDF)](Base/assets/Relatorio_Engenharia_Reversa_Decathlon.pdf ':ignore') | Autor do relatório |
| Nayra Silva Nery | **Relatório de Engenharia Reversa — Funcionalidades, Regras de Negócio e Acessibilidade da Decathlon** | Análise de fluxos e comportamentos da plataforma Decathlon, abrangendo promoções, Clube Decathlon, novidades e cartão-presente, com recuperação de requisitos funcionais, regras de negócio, requisitos não funcionais de acessibilidade e registro de inconsistências observadas. | [Visualizar Relatório (PDF)](Base/assets/relatorio-engenharia-reversa-funcionalidades-extras-nayra.pdf ':ignore') | Autora do relatório |
| Uires Carlos de Oliveira | **Relatório de Engenharia Reversa — Listagem, Produto e Carrinho da Decathlon** | Análise do fluxo de descoberta, seleção e inclusão de produtos no carrinho, contemplando menus, pesquisa, filtros, ordenação, informações e variações do produto, testes exploratórios de acessibilidade com teclado e zoom de 200%, além das respostas apresentadas pelo sistema. Os resultados obtidos serviram de base para a elaboração do modelo BPMN. | [Visualizar Relatório (PDF)](Base/assets/Engenharia_Rev.pdf ':ignore') | Autor do relatório BPMN |

## Processo de engenharia reversa aplicado

A Engenharia Reversa foi aplicada ao site da Decathlon com o objetivo de compreender como o usuário navega pela plataforma, localiza um produto, consulta suas informações, adiciona-o ao carrinho e avança para a finalização da compra.

A análise partiu dos elementos concretos da interface e das respostas apresentadas pelo sistema. Os menus, botões, campos, filtros, resultados, páginas e decisões observadas foram transformados em atividades e fluxos de maior nível de abstração.

O processo foi executado nas seguintes etapas:

### 1. Definição do escopo

O escopo da análise compreendeu:

- homepage;
- menus e modalidades esportivas;
- categorias;
- pesquisa de produtos;
- filtros e ordenação;
- listagem de produtos;
- página individual do produto;
- escolha de cor e tamanho;
- inclusão no carrinho;
- revisão do carrinho;
- entrega;
- pagamento;
- confirmação do pedido.

### 2. Observação da homepage

Na página inicial, foram identificados os menus **Esportes**, **Novidades**, **Feminino**, **Masculino**, **Infantil**, **Acessórios**, **Equipamentos** e **Marcas**.

Também foram observados banners, promoções, campanhas, atalhos rápidos, carrosséis, recomendações, marcas próprias e serviços da Decathlon.

A homepage foi identificada como o ponto inicial para diferentes formas de descoberta de produtos.

### 3. Navegação por modalidade e categoria

A equipe navegou pelas páginas das modalidades **Natação** e **Futebol**. Essas páginas funcionam como áreas temáticas intermediárias, reunindo categorias, campanhas, carrosséis e agrupamentos de produtos.

No fluxo **Home → Futebol → Society**, verificou-se que a seleção da modalidade conduz a uma página temática e, posteriormente, a uma categoria e a uma listagem específica.

A hierarquia recuperada foi:

> **Homepage → modalidade → página temática → categoria → listagem de produtos.**

### 4. Análise da listagem

Na listagem de produtos, foram executadas as seguintes ações:

1. pesquisar um termo;
2. observar os resultados;
3. identificar os filtros;
4. aplicar um filtro;
5. alterar a ordenação;
6. abrir um produto.

Foram observados o campo de pesquisa, a quantidade de resultados, os filtros, as opções de ordenação, as imagens, os nomes, as marcas, os preços, os descontos, o cashback, as cores, as avaliações e a identificação do vendedor.

### 5. Análise do produto

Na página individual do produto, foram observados:

- imagens e ampliação;
- nome e marca;
- preço, parcelamento e desconto;
- avaliações;
- descrição e especificações;
- cores disponíveis;
- tamanhos;
- guia de tamanhos;
- disponibilidade;
- seleção da quantidade;
- cálculo da entrega;
- retirada em loja;
- identificação do vendedor;
- botão para adicionar ao carrinho.

Essa etapa permitiu identificar decisões relacionadas à disponibilidade do produto e à escolha de características obrigatórias, como cor e tamanho.

### 6. Análise do carrinho e da compra

Após adicionar o produto ao carrinho, foram observadas as opções para:

- conferir os produtos;
- alterar a quantidade;
- remover produtos;
- continuar comprando;
- avançar para a finalização.

Na continuação do fluxo, foram identificadas as etapas de confirmação do endereço, escolha da modalidade de entrega, escolha da forma de pagamento e confirmação do pedido.

### 7. Recuperação do fluxo

A Engenharia Reversa permitiu identificar atividades e decisões como:

- pesquisar ou navegar pelos produtos;
- aplicar filtros e ordenação;
- selecionar um produto;
- verificar sua disponibilidade;
- escolher cor e tamanho;
- adicionar o produto ao carrinho;
- alterar ou remover itens;
- continuar comprando ou finalizar;
- selecionar a entrega;
- selecionar a forma de pagamento;
- verificar a aprovação do pagamento;
- confirmar o pedido.

Essas atividades e decisões foram utilizadas para construir o modelo BPMN.

## Modelagem BPMN

O modelo BPMN representa o fluxo de busca, seleção e compra de produtos recuperado durante a Engenharia Reversa do site da Decathlon.

A modelagem apresenta o comportamento observado na interface e não a implementação interna da plataforma.

O diagrama foi organizado em duas raias:

- **Cliente:** representa as atividades executadas pelo usuário;
- **Sistema Decathlon:** representa as respostas, validações e atualizações realizadas pelo sistema.

O fluxo começa quando o cliente acessa o site e navega ou pesquisa por produtos. O sistema apresenta os resultados e permite que filtros e opções de ordenação sejam utilizados.

Quando encontra o produto desejado, o cliente abre a página individual, consulta as informações, verifica a disponibilidade e seleciona as características necessárias.

Depois de adicionar o produto ao carrinho, o cliente pode revisar os itens, alterar a quantidade, remover um produto ou continuar comprando. Caso prossiga, seleciona a modalidade de entrega e a forma de pagamento.

O sistema processa o pagamento. Se a operação for aprovada, o pedido é registrado e confirmado. Caso o pagamento não seja aprovado, o cliente pode informar uma nova forma de pagamento.

O modelo utiliza:

- evento de início;
- atividades;
- gateways exclusivos;
- fluxos de sequência;
- raias de responsabilidade;
- evento de fim.

<p align="center"><b>Figura 1</b> — Modelo BPMN do fluxo de busca, seleção e compra de produtos da Decathlon</p>

<p align="center">
  <img src="Base/assets/nota_BPMN.jpg" alt="Modelo BPMN do fluxo de busca, seleção e compra de produtos da Decathlon" width="1000">
</p>

<p align="center">
  <sub>Fonte: Elaborado por Uires Carlos de Oliveira, com a coparticipação de Diassis Bezerra Nascimento e Nayra Silva Nery, 2026.</sub>
</p>

O arquivo editável produzido no Bizagi Modeler encontra-se disponível no repositório:

[Arquivo editável do modelo BPMN](Base/assets/nota_BPMN.jpg ':ignore')

## Histórico de versões

| Versão | Data | Descrição | Autores | Revisor |
| --- | --- | --- | --- | --- |
| 1.0 | 27/08/2026 | Criação da página do Foco 02 da Sub-equipe 02 | Diassis Bezerra Nascimento | Nayra Silva Nery |
| 1.1 | 27/08/2026 | Inclusão da metodologia e do processo de Engenharia Reversa | Uires Carlos de Oliveira | Diassis Bezerra Nascimento |
| 1.2 | 27/08/2026 | Inclusão da descrição e da imagem do modelo BPMN | Uires Carlos de Oliveira | Nayra Silva Nery |
| 1.3 | 28/08/2026 | Inclusão da tabela de artefatos de Engenharia Reversa, com o relatório da página inicial da Decathlon e espaços reservados para as contribuições dos demais integrantes | Diassis Bezerra Nascimento | A definir |
| 1.4 | 28/08/2026 | Inclusão do relatório de Engenharia Reversa  na tabela de artefatos, contemplando funcionalidades, regras de negócio e aspectos de acessibilidade da Decathlon | Nayra Silva Nery | Diassis Bezerra Nascimento  |
| 1.5 | 28/08/2026 | Inclusão do relatório de Engenharia Reversa de listagem, produto e carrinho da Decathlon, contemplando pesquisa, filtros, ordenação, acessibilidade por teclado e zoom de 200% | Uires Carlos de Oliveira | Nayra Silva Nery |
