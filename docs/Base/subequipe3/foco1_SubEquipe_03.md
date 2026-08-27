
### Rich Picture

<div align="center">

![Rich picture de pagamento](../assets/rich_picture_subgrupo3.png)

</div>

Utilizou-se a técnica do Rich Picture para mapear o ecossistema do checkout no e-commerce da Decathlon. O objetivo foi visualizar a dinâmica entre os atores (Usuário, Empresa, Banco e Suporte) e destacar os gargalos que impactam a experiência do cliente e as metas do negócio.

Análise do Ponto Crítico: Acessibilidade no Checkout

* O Problema de Layout: Ao aplicar o recurso de Zoom em 200%, a interface do checkout sofre uma distorção grave de proporcionalidade: a área inferior destinada ao resumo do carrinho passa a ocupar a maior parte da tela, enquanto o formulário de pagamento fica espremido em uma faixa extremamente reduzida.
* Impacto no Usuário: A limitação do espaço útil dificulta a leitura, a digitação e a conferência dos dados do cartão ou boleto. Isso gera frustração, incerteza sobre o preenchimento correto e leva o cliente a acionar o Suporte/Atendimento ou abandonar a compra.
* Impacto no Negócio: Essa falha de renderização entra em atrito direto com os objetivos estratégicos da Decathlon de reduzir o abandono de carrinho e oferecer uma boa experiência, resultando em perda de conversão.
* Requisito Arquitetural: O problema evidencia a necessidade de refatorar a arquitetura do frontend (CSS/Layout Grid/Flexbox) para seguir as diretrizes de acessibilidade web (WCAG). A interface deve adaptar a hierarquia visual dinamicamente sob ampliação, garantindo que o formulário principal continue visível e utilizável sem ser soterrado por elementos secundários da página.