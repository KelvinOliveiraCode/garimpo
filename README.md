# Garimpo

[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](index.html)
[![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](index.html)
[![SEO](https://img.shields.io/badge/SEO-JSON--LD%2Fsitemap-green?style=flat-square)](sitemap.xml)

Site estático de curação de produtos da Shopee com 131 itens em 8 categorias, busca, filtros por categoria, wishlist no navegador e links diretos para oferta — sem servidor e sem cadastro.

## Problema / Por que existe

Navegar pelo catálogo da Shopee significa percorrer milhares de anúncios para encontrar produtos que valem o preço. O Garimpo filtra esse catálogo e reúne produtos que as pessoas realmente compram, organiza por categoria e envia o visitante direto para a página oficial na Shopee, onde pagamento e entrega ficam por conta da loja. O visitante não cria conta e não insere dados de pagamento no Garimpo.

## O que faz

- Exibe 131 produtos em 8 categorias (Casa e Cozinha, Natal, Moda, Beleza, Tecnologia, Ferramentas, Pets e Fitness), com dados em produtos.json.
- Filtra por categoria via chips fixos no topo da lista de produtos; a contagem de cada categoria vem do próprio JSON.
- Busca por palavra-chave com destaque dos termos encontrados nos títulos.
- Ordena por relevância, mais vendidos, menor preço, maior preço e nome de A a Z.
- Carrega os produtos de 24 em 24 com botão "Carregar mais", sem recarregar a página.
- Mantém uma lista de salvos (wishlist) no localStorage do navegador, sem conta de usuário.
- Mostra um carrossel de destaques na página inicial e um contador de oferta do dia.
- Abre links de afiliado da Shopee (`rel="nofollow sponsored"`) ao clicar em "Ver oferta"; o Garimpo não processa pagamento nem vê o cartão do cliente.
- SEO com meta tags, Open Graph, Twitter cards, URL canônica, JSON-LD (Organization, WebSite, ItemList), sitemap.xml e robots.txt.

## Stack

- HTML5 semântico (`nav`, `section`, `main`, `footer`, `article`) com CSS inline no próprio `index.html`.
- CSS3 com variáveis CSS, grid responsivo (3, 2 ou 1 colunas), filtros e busca fixos no topo (sticky), transições e animações.
- JavaScript vanilla, sem frameworks: `fetch` do `produtos.json`, renderização do grid, filtros, busca, wishlist, carrossel e placeholders de analytics.
- Dados: `produtos.json` com 131 produtos.
- Hospedagem estática: Vercel (`.vercel/project.json`).

Preços observados em `produtos.json` vão de R$ 15,99 a R$ 843,60.

## Como funciona

1. `index.html` carrega `produtos.json` via `fetch`.
2. O JavaScript renderiza o grid, os chips de categoria com contagem, a barra de busca e a ordenação.
3. O visitante filtra, busca e ordena sem recarregar a página (renderização feita no cliente).
4. Clicando em "Ver oferta", o link leva à página oficial do produto na Shopee (afiliado). O Garimpo não vê cartão, não faz checkout e não calcula frete.
5. Salvos ficão armazenados apenas no navegador (localStorage).

## Como rodar

- Abra `index.html` diretamente no navegador (arquivo estático).
- Para comportamento mais próximo da produção (fetch de `produtos.json` sem restrições de arquivo local), sirva a pasta com qualquer servidor estático, por exemplo `python -m http.server`, `npx serve` ou Vercel.
- Não há dependências para instalar e não há backend. Mantenha `produtos.json` ao lado de `index.html`.

## Estrutura do projeto

```
Garimpo/
├── index.html                 # HTML, CSS inline, JavaScript e SEO em um único arquivo
├── produtos.json              # 131 produtos (preço, categoria, selo, imagem, link Shopee)
├── sitemap.xml                # sitemap para indexação pelos buscadores
├── robots.txt                 # regras de rastreamento
├── .gitignore                 # ignora WhatsApp*, .vercel, vídeos e relatórios; mantém img/
├── .vercel/project.json       # identificação do projeto na Vercel
├── logo.png / logo.jpg / logo-icon.png / favicon.jpg / apple-touch-icon.jpg
└── img/                       # imagens dos produtos (webp/jpeg)
```

## Trade-offs e decisões

- Tudo em um único arquivo (`index.html` com HTML, CSS e JS) simplifica o deploy em hospedagem estática, mas não escala para times grandes; o CSS não é modularizado.
- Sem backend: a wishlist persiste só no navegador (`localStorage`). Ao limpar os dados ou trocar de dispositivo, os salvos somem.
- Links de afiliado da Shopee: a receita depende de cliques externos; preço e estoque são da Shopee e podem mudar a qualquer momento.
- Quando a imagem de um produto falha, há um fallback via Unsplash (`onerror` na tag `img`).
- Os placeholders de analytics (Meta Pixel, gtag) precisam de IDs reais para funcionar.
- Não há servidor, portanto não há login, carrinho ou checkout dentro do Garimpo.

## Limitações conhecidas

- Produtos e preços são estáticos em `produtos.json` e atualizados manualmente; podem estar desatualizados em relação à Shopee.
- O contador de oferta do dia depende do relógio do navegador do visitante.
- A wishlist persiste apenas localmente (`localStorage`).
- O `sendBeacon` para `/api/track` não tem backend correspondente no repositório.
- Os IDs do Meta Pixel e do gtag são placeholders (`REPLACE_PIXEL_ID`).
- Não há PWA, carrinho, checkout nem conta de usuário.

## Licença

Este repositório não inclui arquivo `LICENSE`. Consulte o autor antes de reutilizar o código ou os conteúdos.

## Autor

Garimpo (garimpo-oficial.vercel.app). Redes: Instagram @garimpo0132, TikTok @garimpo0176, YouTube @Garimpoprodutos. O repositório não declara um nome de autor individual.
