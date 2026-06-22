# Riviera Ouro — Template por Cidade

Landing page da Riviera Compra de Ouro, construída em Astro com geração estática por cidade.

## Como funciona

- Cada cidade é uma entrada no arquivo `src/data/cidades.json`
- O Astro gera uma página estática em `/[slug-da-cidade]/` para cada entrada
- A raiz `/` redireciona para `/bauru/` (cidade padrão)

## Adicionar uma nova cidade

1. Abra `src/data/cidades.json`
2. Copie um objeto existente e cole ao final do array (antes do `]`)
3. Preencha todos os campos obrigatórios (veja estrutura abaixo)
4. Rode `npm run build` — a nova página será gerada automaticamente

### Campos do objeto de cidade

```json
{
  "slug": "nome-url-sem-acento",       // URL: /nome-url-sem-acento/
  "cidade": "Nome da Cidade",
  "estado": "SP",
  "regiao": "Região de referência",
  "endereco": "Rua, número",
  "complemento": "Andar, sala – Bairro",
  "cep": "00000-000",
  "bairro": "Centro",
  "telefone": "(11) 99999-9999",
  "telefoneRaw": "+5511999999999",
  "whatsappLink": "https://wa.me/5511999999999?text=...",
  "instagram": "https://www.instagram.com/...",
  "instagramHandle": "@usuario",
  "mapsEmbed": "URL do iframe do Google Maps",
  "geoLat": -00.0000,
  "geoLng": -00.0000,
  "bairrosAtendidos": ["Bairro 1", "Bairro 2"],
  "seo": {
    "title": "Compra de Ouro em [Cidade] | Riviera Ouro",
    "description": "Meta description única para a cidade (max 160 chars)",
    "canonical": "https://rivieraouro.com.br/compra-de-ouro-[slug]",
    "ogImage": "URL da imagem OG"
  },
  "textosUnicos": {
    "heroParagrafo": "Parágrafo único sobre a cidade no hero",
    "especialistaParagrafo": "Texto na seção de especialistas",
    "especialistaParagrafo2": "Segundo parágrafo da seção de especialistas",
    "ondeParagrafo": "Texto na seção 'Onde vender'",
    "ondeParagrafo2": "Segundo parágrafo da seção 'Onde vender'",
    "footerTagline": "Tagline no rodapé"
  },
  "horarioFuncionamento": {
    "diasSemana": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
    "abre": "09:00",
    "fecha": "18:00"
  }
}
```

> **Dica SEO:** Preencha `textosUnicos` com conteúdo genuinamente diferente para cada cidade. Evite simplesmente trocar o nome da cidade nos textos — isso caracteriza doorway pages e pode gerar penalização no Google.

## Rodar localmente

```sh
npm install       # instalar dependências (primeira vez)
npm run dev       # servidor de desenvolvimento em http://localhost:4321
```

Acesse `http://localhost:4321/bauru` ou `http://localhost:4321/marilia`.

## Gerar build estático

```sh
npm run build     # gera os arquivos em ./dist/
npm run preview   # visualiza o build localmente antes de subir
```

Os arquivos em `./dist/` são prontos para deploy em qualquer host estático (Cloudflare Pages, Netlify, Vercel, GitHub Pages).

## Estrutura do projeto

```
riviera-ouro/
├── public/
│   ├── images/          # Imagens e assets (logo, fotos de produtos)
│   └── favicon.svg
├── src/
│   ├── data/
│   │   └── cidades.json  # <-- adicione cidades aqui
│   ├── layouts/
│   │   └── Layout.astro  # Head, meta tags, Schema.org
│   ├── pages/
│   │   ├── index.astro   # Redireciona para /bauru/
│   │   └── [cidade].astro # Template dinâmico (não edite o nome do arquivo)
│   └── styles/
│       └── global.css    # Estilos globais + variáveis de cor
└── package.json
```

## Publicar no GitHub (primeira vez)

Depois de criar o repositório no GitHub (sem README, sem .gitignore), rode:

```sh
git remote add origin https://github.com/SEU_USUARIO/riviera-ouro.git
git branch -M main
git push -u origin main
```

Substituindo `SEU_USUARIO` pelo seu nome de usuário do GitHub.
