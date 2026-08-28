# Foco 02: Engenharia Reversa & Modelagem BPMN

## Introdução e Contexto de Aplicação

Esta página apresenta as etapas desenvolvidas do processo de Engenharia Reversa conduzido pela **Sub-equipe 01**, dedicado ao mapeamento e à modelagem comportamental dos mecanismos de **Autenticação, Cadastro e Gestão de Perfil do Usuário** do site da [Decatlhon Brasil](https://www.decathlon.com.br/?utm_id=446506642-1166583788952155&msclkid=091f92b84b35170e8da3f8341b2d1eb0&utm_source=bing&utm_medium=cpc&utm_campaign=br_ct-search_t-perf_nc-brand-nacional_ts-bra_f-cv_o-roas_pnl-ecom_bm-ish_xx-microsoft-ads_&utm_term=esporte%20decathlon&utm_content=yy-institucional-termos-aon_).
A análise tomou como **objeto de estudo** a plataforma web em execução. A investigação foi realizada **exclusivamente via interface gráfica**, simulando a jornada e as interações de um usuário comum sem acesso prévio ao código-fonte ou às bases de dados do sistema. 

---

## Objetivos

A partir da observação empírica orientada por casos de teste estruturados, esta etapa do projeto buscou alcançar os seguintes objetivos:

* **Elicitar Regras Implícitas:** Identificar comportamentos, validações de segurança, tratamentos de exceção e falhas de qualidade em tempo de execução.
* **Modelagem Formal em BPMN:** Representar com clareza e precisão a sequência de interações entre o usuário e o sistema, explicitando os pontos de decisão e desvios de fluxo na notação **BPMN 2.0 (*Business Process Model and Notation*)**.
* **Fundamentar Artefatos Complementares:** Fornecer uma base de evidências operacionais sólidas para respaldar a análise de Requisitos Não-Funcionais (NFRs) e os demais modelos arquiteturais do projeto.

---

## Escopo do Estudo

A análise está delimitada estritamente às interações do **Fluxo: Autenticação, Cadastro e Gestão de Perfil do Usuário**, contemplando as seguintes etapas:

* Login convencional e validação de e-mail;
* Login social (OAuth) e permissões;
* Cadastro manual e validação de CPF/OTP;
* Recuperação de acesso e senha;
* Autenticação *Passwordless* (Senha de acesso único);
* Encerramento de sessão (*Logout*) e gestão de cache;
* Gerenciamento do perfil em painel SSO;
* Proteção das informações de conta e alteração de credenciais;
* Privacidade, visibilidade de dados e exclusão de conta (LGPD).

> **Nota:** O modelo foi delimitado para o referido fluxo, não abrangendo as demais funcionalidades do e-commerce, como busca de produtos, carrinho e pagamento.

---

# [Processo de Engenharia Reversa](#processo-de-engenharia-reversa)

## Metodologia de Análise Comportamental

Para realizar o mapeamento do sistema sem acesso prévio ao seu código-fonte ou banco de dados, adotou-se a **Engenharia Reversa Comportamental baseada em Testes de Caixa-Preta**. O site da [Decatlhon Brasil](https://www.decathlon.com.br/?utm_id=446506642-1166583788952155&msclkid=091f92b84b35170e8da3f8341b2d1eb0&utm_source=bing&utm_medium=cpc&utm_campaign=br_ct-search_t-perf_nc-brand-nacional_ts-bra_f-cv_o-roas_pnl-ecom_bm-ish_xx-microsoft-ads_&utm_term=esporte%20decathlon&utm_content=yy-institucional-termos-aon_) foi submetido a estímulos de entrada deliberados para observar as respostas da interface, comportamentos de sessão, mensagens de validação e desvios de fluxo.

A condução do estudo seguiu quatro etapas estruturadas:
* **Mapeamento de Vias Críticas:** Identificação e navegação pelos caminhos operacionais de autenticação (convencional, *passwordless* e social/OAuth), cadastro, recuperação e gestão de conta.
* **Estimulação e Injeção de Dados:** Submissão de dados sintéticos (ex.: e-mails inexistentes, senhas incorretas repetidas, CPFs duplicados) para forçar o acionamento de cenários de exceção e limites do sistema.
* **Avaliação de Sessão e Cache:** Verificação da persistência e destruição de tokens de sessão após o *logout* através da navegação pelo histórico do navegador.
* **Mapeamento de Regras e NFRs:** Tradução das respostas observadas em regras de negócio e atributos de Requisitos Não-Funcionais (Segurança, Usabilidade, Integridade, Rastreabilidade).

---

## Levantamento Empírico e Ensaios de Teste

O levantamento que serviu de insumo direto para a elaboração dos diagramas BPMN é sintetizado na tabela abaixo, consolidando os 12 casos de teste operacionais executados durante a Engenharia Reversa:

| ID | Título do Caso de Teste | Ação Executada / Estímulo | Resultado Observado | Requisito / Atributo Mapeado |
| :--- | :--- | :--- | :--- | :--- |
| **CT-01** | Enumeração de Usuários no Login | Inserção de e-mail inexistente na tela inicial. | Retorno do aviso: *"Conta Decathlon não encontrada..."*. | Falha de Confidencialidade |
| **CT-02** | Autenticação Social e Opt-in | Login via provedor externo (OAuth). | Exige 6 cliques e opt-in obrigatório de marketing. | Usabilidade / Privacidade |
| **CT-03** | Encerramento de Sessão (Logout) | Clique em "Sair" e uso da navegação "Voltar" do browser. | Invalidação do cache e redirecionamento imediato para login. | Segurança da Sessão (Positivo) |
| **CT-04** | Validação via Código OTP | Início do cadastro manual. | Disparo de código OTP de 6 dígitos via e-mail (validade 15 min). | Autenticidade / Posse |
| **CT-05** | Complexidade de Senha e Unicidade | Submissão de senha e CPF. | Exige 8 caracteres, maiúscula, número e símbolo; bloqueia CPF duplicado. | Integridade e Unicidade |
| **CT-06** | Falhas Consecutivas de Senha | Inserção deliberada de senha errada por 5 vezes. | Retorno repetido de *"Senha inválida"* sem *lockout* ou CAPTCHA. | Vulnerabilidade a Força Bruta |
| **CT-07** | Reutilização de Senha no Perfil | Tentativa de redefinir senha para a mesma já usada. | Trava do sistema: *"Introduz outra palavra-passe"*. | Integridade (Positivo) |
| **CT-08** | Alerta de Alteração de Credenciais | Conclusão do processo de troca de senha. | Nenhuma notificação por e-mail é enviada ao usuário. | Falha de Rastreabilidade |
| **CT-09** | Transição de Painel (SSO) | Acesso às configurações avançadas de perfil/segurança. | Redirecionamento para interface/layout divergente da loja. | Inconsistência Visual (SSO) |
| **CT-10** | Exclusão de Dados Pessoais | Busca por opções de cancelamento de conta. | Presença do botão *"Eliminar a minha conta"*. | Conformidade Legal (LGPD) |
| **CT-11** | Esqueci Minha Senha (Recuperação) | Solicitação de redefinição informando e-mail. | Envio de e-mail com link/código temporário de redefinição. | Recuperabilidade |
| **CT-12** | Senha de Acesso Único (*Passwordless*) | Solicitação de login direto sem senha fixa. | Disparo de token OTP por e-mail para autenticação direta. | Usabilidade / Autenticidade |

---

## Principais Achados e Vínculo com a Modelagem BPMN

As constatações extraídas do processo de Engenharia Reversa ditaram os pontos de decisão (Gateways Exclusivos) e os caminhos de exceção refletidos nos diagramas de processo:

* **Gargalos de Segurança Mapeados no BPMN:** A ausência de mecanismos de *lockout* após múltiplas falhas (CT-06) e a enumeração de e-mails no login (CT-01) demonstraram que os fluxos de autenticação do sistema privilegiam o retorno de loops simples em vez de estados de bloqueio temporário.
* **Validações de Negócio:** A inclusão de verificações de unicidade de CPF (CT-05) e a proibição de reuso do mesmo segredo na alteração de senha (CT-07) fundamentaram os desvios de regra modelados na raia do *Sistema*.
* **Múltiplas Vias de Autenticação:** A coexistência de autenticação por senha mestra, código OTP temporário (CT-04 / CT-12) e login social via OAuth (CT-02) exigiu que a modelagem contemplasse subfluxos flexíveis para acesso e recuperação de conta.

> **Documentação Completa de Suporte:** A especificação detalhada de cada caso de teste, com suas relativas telas capturadas, análises de impacto arquitetural e detalhamento de vulnerabilidades, encontra-se registrada no [Relatório de Casos de Tese](Base/assets/relatorio-casos-de-teste.pdf ':ignore').

---

# [Modelagem BPMN](#modelagem-bpmn)

Para formalizar visualmente o comportamento do sistema mapeado durante a Engenharia Reversa, os fluxos de processo foram modelados no padrão internacional **BPMN 2.0** utilizando a ferramenta [**Miro**](https://miro.com/pt/). 

A representação unifica a jornada do usuário e o processamento do sistema para os três eixos operacionais críticos do **Fluxo A**: Autenticação, Alteração de Credenciais e Cadastro de Novo Usuário.

---

## Organização em Piscinas e Raias

Com o propósito de delimitar o escopo de atuação e dar clareza às responsabilidades arquiteturais, os processos foram estruturados em uma piscina principal dividida em duas raias paralelas:

* **Usuário:** Representa o ator externo, responsável pelo acionamento de eventos, entrada de dados e tomada de decisão na interface gráfica.
* **Sistema:** Representa as operações internas, requisições de backend, validações de regras de negócio em base de dados e respostas de interface.

---

## Diagramas e Descrição dos Fluxos de Processo

### 1. Fluxo de Autenticação (Login)

<p align="center">
    <img src="Base/assets/Subgrupo1.1.1/diagrama/Login.png" alt="Diagrama BPMN do fluxo de login" width="100%">
</p>

<p align="center">
    <em>Figura 1: Diagrama BPMN do fluxo de autenticação. <strong>Autor:</strong> Samuel Felipe.</em>
</p>

**Descrição e Funcionamento do Fluxo:**
  O processo inicia-se quando o usuário insere suas credenciais de acesso na interface. O fluxo avança para a validação no backend, onde o Gateway Exclusivo **"Credenciais corretas?"** avalia o estado das informações:
  * **Sim:** A sessão do usuário é criada com sucesso, redirecionando-o à área logada da aplicação.
  * **Não:** O sistema emite uma mensagem de erro e retorna o fluxo para a tarefa de preenchimento, permitindo novas tentativas sem acionar trava temporária de bloqueio (*lockout*).

---

### 2. Fluxo de Redefinição de Credenciais (Alteração de Senha)

<p align="center">
    <img src="Base/assets/Subgrupo1.1.1/diagrama/Recuperacao_senha.png" alt="Diagrama BPMN do fluxo de alteração de senha" width="100%">
</p>

<p align="center">
    <em>Figura 2: Diagrama BPMN do fluxo de alteração de senha. <strong>Autor:</strong> Samuel Felipe.</em>
</p>

**Descrição e Funcionamento do Fluxo:**
  O usuário solicita a atualização de credenciais informando seu endereço de e-mail cadastrado. O Gateway Exclusivo **"E-mail existe na base de dados?"** controla a bifurcação do processo:
  * **Sim:** O sistema gera e envia o link/token de redefinição para o e-mail informado, autorizando a atualização do segredo.
  * **Não:** O fluxo é encerrado sem expor confirmações detalhadas ao solicitante, forçando o reinício da operação.

---

### 3. Fluxo de Criação de Conta (Cadastro)

<p align="center">
    <img src="Base/assets/Subgrupo1.1.1/diagrama/Cadastro.png" alt="Diagrama BPMN do fluxo de cadastro" width="100%">
</p>

<p align="center">
    <em>Figura 3: Diagrama BPMN do fluxo de cadastro. <strong>Autor:</strong> Samuel Felipe.</em>
</p>

**Descrição e Funcionamento do Fluxo:**
  O usuário fornece seus dados pessoais e documento de identificação (CPF). O Gateway Exclusivo **"Os dados são válidos?"** processa a consistência das entradas:
  * **Sim:** Os registros são gravados na base de dados do sistema, concluindo a criação do perfil e liberando o acesso.
  * **Não:** O sistema aponta as inconsistências de preenchimento (ex.: CPF duplicado ou formato inválido) e retorna o controle ao usuário para correção.

---

## Convenção e Semântica de Notação (BPMN 2.0)

* **Gateway Exclusivo Baseado em Dados (`◇` com X):** Elemento de decisão excludente que direciona a sequência do processo para apenas um caminho possível com base no resultado da avaliação lógica.
* **Fluxo de Sequência (Seta Contínua):** Define a ordem cronológica e a dependência de execução das atividades entre as raias do processo.

> **Validação do Modelo:** A lógica representada em todos os diagramas foi estritamente confrontada e validada em relação ao comportamento em tempo de execução observado durante os testes de Engenharia Reversa, garantindo fidelidade entre o sistema real e a sua documentação.

---

## Tabela de Contribuições

| Nome do Membro | Contribuições no Foco (Engenharia Reversa & BPMN) |
| :--- | :--- |
| [Dylan Cavalcante](https://github.com/dylancavalcante) | Coautor na documentação da Metodologia de Engenharia Reversa; Participei da consolidação e redação da análise crítica dos achados de segurança e NFRs com base nos testes empíricos e da revisão técnica da consistência do documento. |
| [Mariana Ribeiro](https://github.com/marianagonzaga0) | Coautora da estrutura e detalhamento da tabela consolidada de Casos de Teste (CT-01 a CT-12); Auxiliei no mapeamento das regras de negócio e validações do sistema que fundamentaram as decisões (Gateways) do BPMN. |
| [Rafaela Andrea](https://github.com/RadamesGuerra) | Responsável pela execução prática dos ensaios de teste na interface (Black-Box), extração das evidências comportamentais de autenticação/cadastro e apoio no mapeamento das raias do usuário e sistema para os fluxos. |
| [Samuel Felipe](https://github.com/TerminaKng05) | Autor principal e modelador dos diagramas BPMN 2.0 (Login, Alteração de Senha e Cadastro) na ferramenta Miro; Coautor da especificação descritiva dos fluxos e semântica de notação utilizada. |

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
| 1.2 | 27/08/2026 | Correção links quebrados| [Dylan Cavalcante](https://github.com/dylancavalcante) | ----- |
| 1.3 | 28/08/2026 | Adição da introdução e contexto| [Mariana Ribeiro](https://github.com/marianagonzaga0) | ----- |
| 1.4 | 28/08/2026 | Acrescenta conteúdo do estudo de Engenharia Reversa | [Rafaela Andrea](https://github.com/RadamesGuerra) | ----- |
