# Ponto Color — Site institucional

Site estático com tema escuro/dramático. **Sem backend** (não usa Supabase).

## Estrutura

```
ponto-color/
├── index.html         ← Página única — edite valores no <script> ao final
├── README.md          ← Este arquivo
└── assets/
    ├── wheel.png      ← Roda de cores 3D (extraída do logo original)
    └── gallery-*.svg  ← 5 ilustrações vetoriais da galeria
```

## Como funciona

Todos os botões da página apontam pro WhatsApp com mensagem pré-preenchida:
- **Botões principais** → "Olá! Quero um orçamento de pintura."
- **Rodapé** → "Olá! Quero mais informações sobre os serviços da Ponto Color."
- **Cada card de serviço** → "Olá! Quero um orçamento para [Pintura residencial / Fachada / etc]"

Pra editar essas mensagens ou trocar o número, abre o `index.html` no fim do arquivo:

```js
const WHATSAPP_PHONE = '5512988703175';
const MSG_GERAL = 'Olá! Quero um orçamento de pintura.';
const MSG_INFO  = 'Olá! Quero mais informações sobre os serviços da Ponto Color.';
```

---

## Deploy — passo a passo (igual ao JD Climatização)

### 1. Testar local

```powershell
cd "C:\caminho\onde\descompactou\ponto-color"
python -m http.server 8000
```

Abre http://localhost:8000 e verifica:
- Hero escuro com roda de cores flutuando à direita
- Confetti de blobs coloridos animados no fundo
- 6 cards de serviços com bordas coloridas diferentes ao hover
- 2 cards de "modelo de cobrança" (Premium + Apenas mão de obra)
- 5 ilustrações na galeria
- 4 depoimentos com avatares coloridos
- Botões WhatsApp abrem com mensagem certa

### 2. Push pro GitHub

Cria repo `ponto-color` em https://github.com/new (público, vazio).

```powershell
cd "C:\caminho\ponto-color"
git init
git add .
git commit -m "Site Ponto Color"
git branch -M main
git remote add origin https://github.com/paxelbr177-spec/ponto-color.git
git push -u origin main
```

### 3. Ativar GitHub Pages

- Repo → **Settings** → **Pages**
- Source: Deploy from branch
- Branch: `main` / `/(root)` → **Save**
- Aguarda ~1-2 min

URL final: `https://paxelbr177-spec.github.io/ponto-color/`

---

## Customizações

### Trocar marcas premium

Busca por `brand-tag` no HTML. Cada `<span class="brand-tag">Suvinil</span>` é uma marca.
Editar nome ou adicionar/remover quantos quiser.

### Trocar testimonials

Busca por `testimonial-card`. Cada bloco tem:
- `.stars` — estrelas
- `.testimonial-text` — texto
- `.avatar` — iniciais e classe de cor (c1=vermelho/laranja, c2=amarelo, c3=verde/teal, c4=teal/roxo)
- `.author-info` — nome e descrição

### Mudar paleta

Topo do `<style>` em `:root`:
```css
--yellow:    #FFB800;
--orange:    #F4A261;
--red:       #E84855;
--green:     #4CAF50;
--teal:      #1B9AAA;
--purple:    #7B3FBF;
```

---

## Próximos passos

- **Domínio próprio**: `pontocolor.com.br` (ou `puntocolor.com.br`) via Registro.br
- **Google My Business** com mesmo CNPJ
- Se quiser, posso fazer um logo SVG mais limpo no futuro
