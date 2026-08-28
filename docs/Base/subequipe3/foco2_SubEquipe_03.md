# Modelo BPMN – Fluxo de Pagamento (E-commerce Decathlon Brasil)

Modelagem do processo de pagamento do checkout da Decathlon Brasil, elaborada em notação **BPMN 2.0**, cobrindo desde a montagem do carrinho até a confirmação do pedido e o encaminhamento para separação/logística.

## Diagrama

Fonte editável: [`decathlon-fluxo-pagamento_subequipe3.bpmn`](Base/assets/decathlon-fluxo-pagamento_subequipe3.bpmn ':ignore')

## Atores e raias (pools / lanes)

| Pool | Lane | Responsabilidade |
|---|---|---|
| Cliente / Usuário | Cliente | Carrinho, escolha do meio de pagamento, pagamento efetivo (Pix/boleto), recebimento de confirmação |
| Decathlon E-commerce | Checkout | Validação de carrinho, dados de entrega/frete, regras promocionais, split de marketplace |
| Decathlon E-commerce | Orquestrador de pagamento | Roteamento por meio de pagamento, espera de confirmação (síncrona/assíncrona), decisão de aprovação |
| Suporte / Atendimento | Suporte | Recebe acionamento do cliente com dificuldade no checkout e orienta o preenchimento |
| Gateway / Adquirente | Processamento | Autorização de cartão, cobrança PayPal |
| Gateway / Adquirente | Banco emissor / Pix | Aprovação de cartão, confirmação Pix, compensação de boleto |
| Marketplace parceiro | — | Recebimento do pedido e repasse via split (produtos vendidos por parceiros) |
| Logística | — | Separação, embalagem e despacho do pedido |

## Descrição do processo

O cliente monta o carrinho e segue para o checkout, onde o sistema valida os itens e identifica se algum produto pertence a um vendedor parceiro (marketplace), aplicando a regra de split de pagamento quando necessário. Em seguida são capturados os dados de entrega e frete e aplicadas as regras promocionais vigentes (desconto de 5% no Pix, condições de parcelamento no cartão).

Ao selecionar o meio de pagamento, o processo verifica se o formulário permanece utilizável em zoom de 200%. Quando a renderização compromete o preenchimento, o cliente pode acionar o Suporte/Atendimento — que orienta o preenchimento e devolve o cliente ao checkout — ou abandonar a compra, cenário tratado como desfecho de exceção do processo.

A partir da seleção do meio de pagamento, o orquestrador direciona a transação:

- **Cartão de crédito** – dados tokenizados e enviados ao adquirente, que autoriza a transação junto ao banco emissor (resposta síncrona).
- **Pix** – geração de QR Code; a confirmação do banco chega de forma assíncrona.
- **Boleto bancário** – emissão do boleto; compensação confirmada em até 72h (assíncrono).
- **PayPal** – cobrança automática sobre o cartão cadastrado na conta do cliente.

O orquestrador aguarda o retorno de cada meio (evento de mensagem) e converge para o gateway de decisão "Pagamento aprovado?". Se aprovado, o pedido é confirmado, notificado ao cliente e encaminhado simultaneamente à logística (separação e despacho) e, quando aplicável, ao parceiro de marketplace (repasse via split). Se recusado, o cliente é notificado e pode tentar outro meio de pagamento ou abandonar a compra.

## Premissas de negócio

- **Cartão de crédito**: parcelamento em até 10x, conforme valor mínimo de parcela.
- **Pix**: 5% de desconto em compras acima de R$250 (produtos vendidos e entregues pela Decathlon).
- **Boleto bancário**: pagamento à vista, com confirmação em até 72 horas.
- **PayPal**: cobrança automática sobre cartão previamente cadastrado.
- **Marketplace**: produtos de parceiros têm regras promocionais próprias, exigindo split de pagamento e notificação ao parceiro após confirmação do pedido.
- **Acessibilidade do checkout**: em zoom de 200%, o formulário de pagamento pode ficar comprimido pela área de resumo do carrinho, motivando o desvio de exceção para Suporte/Atendimento ou abandono da compra.





# Engenharia Reversa: Fluxo de Pagamentos 
## Visão Geral

Esta documentação consolida o estudo de Engenharia Reversa conduzido pela **Sub-equipe 03**, direcionado ao ecossistema de pagamento do e-commerce Decathlon. A investigação mapeou a jornada do consumidor desde a consolidação do carrinho até a resposta da transação financeira. 

Os achados foram modelados por meio de um **Rich Picture** para visão sistêmica e diagramas **BPMN (Business Process Model and Notation)** para representação formal dos processos, identificando gargalos operacionais e de usabilidade.

---

## Cenário de Análise e Desafios Encontrados

A exploração baseou-se em testes ponta a ponta na interface pública da plataforma e simulação de jornadas de compra. O levantamento ocorreu sem acesso ao código-fonte ou documentação interna do sistema, focando no comportamento observável da aplicação.

### Ponto Crítico de Acessibilidade
Durante os testes de responsividade e acessibilidade, constatou-se que a aplicação do **zoom de 200% na interface** quebra a disposição dos elementos na tela. Esse comportamento oculta e sobrepõe campos essenciais para a inserção dos dados de pagamento, impondo uma barreira severa para usuários que dependem de ampliação de tela.

---

## Cobertura do Estudo

* Validação de itens e valores no Carrinho de Compras;
* Coleta e validação de informações de cadastro e endereço de entrega;
* Seleção e processamento de métodos de pagamento;
* Interface de comunicação e resposta das instituições financeiras (Aprovação/Recusa);
* Gestão pós-compra (estimativa de frete, prazos e rastreio);
* Atendimento e suporte ao cliente diante de falhas na transação;
* Impactos de acessibilidade sob ampliação de tela (zoom 200%).

---

## Execução Prática da Engenharia Reversa

O mapeamento seguiu o fluxo operacional executado pelo cliente final:

1. **Mapeamento da Jornada:** Acompanhamento sequencial de cada etapa do checkout, registrando os pontos de decisão e requisições de dados.
2. **Inspeção de Interface:** Análise do comportamento dos componentes visuais e tratativas de erro do formulário sob diferentes resoluções e níveis de zoom.
3. **Diagramação e Síntese:** Consolidação das interações no Rich Picture para evidenciar a relação entre usuário, e-commerce e empresa, refinando-as posteriormente em fluxos BPMN.

## Histórico de versões

| Versão | Data | Descrição | Autores | Revisor |
| --- | --- | --- | --- | --- |
| 1.0 | 27/08/2026 | Criação do Bpmn| Camile Barbosa Gonzaga de Oliveira | Letícia de Carvalho dos Santos|
| 1.1 | 28/08/2026 | Inclusão do tópico sobre engenharia reversa | Letícia de Carvalho dos Santos | A preencher |
