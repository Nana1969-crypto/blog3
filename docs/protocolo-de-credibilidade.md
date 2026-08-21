# Protocolo de Credibilidade — Blog #3 (Homeschool, EUA)

Regras permanentes de publicação deste site. Acordado com a dona em 2026-08-16.

Marcação: 🔒 = **cobrado pelo código** (o gate derruba o build e nada vai ao ar).
Sem marca = disciplina editorial. A diferença importa: só o primeiro grupo é
inquebrável.

---

## Contexto — por que este site existe

Nicho escolhido: **educação domiciliar nos EUA (homeschooling)**, em inglês.

A escolha saiu de 13 buscas reais de verificação de SERP. Sete nichos testados
(licenças de contractor, folha de pagamento, SaaS vertical, franquia/laundromat,
piscina/home services, barco, IEP) estavam ocupados por empresas que tratam
conteúdo como **custo de aquisição de cliente, não como receita** — ServiceTitan,
Angi, LendingTree, GEICO, Intuit. Contra esse tipo de concorrente, um publisher
solo com AdSense compete contra prejuízo subsidiado, indefinidamente.

Homeschool foi o único nicho onde **blogueiras independentes seguram a primeira
página**. Na busca "secular homeschool curriculum", 7 dos 9 resultados eram
operadores independentes — a SERP mais fraca de todas as testadas.

**A diferenciação do site** é a rotulagem sistemática de visão de mundo de cada
currículo (cristão / secular / não declarado), que hoje ninguém faz de forma
rigorosa. É também o maior risco do projeto: se o rótulo pode estar errado, ele
deixa de ser fosso e vira passivo. Este documento existe por causa disso.

**Postura editorial:** uma só, servindo os dois públicos —
*"dizemos exatamente qual visão de mundo cada material carrega; não dizemos qual
você deve ter."*

---

## Estado da implementação (2026-08-16)

As regras da seção 1 **já estão implementadas no motor** como os códigos CUR-1 a
CUR-5 em `platform/src/build.js`. Rótulo sem fonte, sem citação textual, sem data
ou sem escopo declarado **derruba o build**. O build também avisa quando um rótulo
passa de 6 meses sem reverificação.

**Pendências deliberadas, não esquecidas:**

| Pendente | Por quê |
|---|---|
| `curriculum.json` vazio | Cada entrada exige a frase textual da página da editora. O ambiente desta sessão bloqueia acesso às páginas externas, e inventar a citação seria exatamente a fabricação que este documento proíbe. |
| Pilar "State Laws & Funding" ausente da taxonomia | Cada guia estadual exige as regras publicadas pelo próprio estado. Mesmo motivo. Entra na taxonomia junto com o primeiro guia verificado. |
| Domínio e e-mail de contato | Ainda não registrados. A página `/contact/` declara isso em vez de listar um endereço que não funciona. |

Nenhuma dessas pendências bloqueia a publicação de artigos de método e julgamento,
que é o que já está no ar.

---

## 1. Rotulagem de visão de mundo — o risco central

- 🔒 Sem `worldviewSource` (link) + `worldviewQuote` (frase exata da editora) +
  `verifiedOn` + `edition`, **não existe rótulo** e o build cai.
- Rótulo por **currículo + matéria**, nunca por editora. Uma editora pode ser
  neutra em matemática e criacionista em ciências — rotular a editora inteira é
  onde se erra.
- **Dois campos separados, nunca fundidos:**
  - `contentWorldview` — existe conteúdo religioso **no material**?
  - `publisherAffiliation` — a **empresa** é religiosa?

  São perguntas diferentes e pais diferentes se importam com uma ou com outra.
  Reportando as duas em separado, o site nunca precisa dar o veredito
  contestável: reporta dois fatos e a mãe decide.
- Quarto valor obrigatório: **`unstated`** (não declarado), que **não** é sinônimo
  de "neutro".
- Escopo declarado em toda ficha: *"posição declarada pela editora + amostras
  públicas; não revisamos o curso completo."*

### Onde o erro mora (conhecer para evitar)

1. Variação por matéria dentro da mesma editora — maior risco.
2. "Neutro por omissão": empresa de origem cristã, conteúdo sem religião. Não há
   resposta objetiva — por isso os dois campos separados.
3. Edições mudam: material revisado ganha ou perde conteúdo religioso.
4. Grau dentro do cristão (terra jovem vs. terra antiga vs. ciência mainstream
   com enquadramento cristão). Errar aqui é tão grave quanto trocar cristão por
   secular.

---

## 2. Números e fatos

- 🔒 Todo artigo com pelo menos uma fonte real e verificável.
- Fonte primária sempre: página da própria editora, ou site oficial do estado
  para lei e programas de ESA.
- **Se a fonte não for encontrada, o número não entra.** Avisar a dona em vez de
  publicar.
- `verifiedOn` em todo dado volátil. O build alerta quando passa de 6 meses sem
  reverificação.

---

## 3. Autoria

- Assinatura institucional (`author_team`), como já funciona no CertNorth.
- **Nunca encenar fé que a autora não tem** — nem cristã, nem militantemente
  secular.
- **Nunca encenar experiência de mãe homeschooler**: nada de "usamos este
  currículo", nada de foto simulando estante própria.
- Zero credencial inventada.

**A forma honesta funciona e é mais útil.** Comparar:

> ❌ "Como mãe cristã, o Apologia abençoou nossa família…"

> ✅ "O Apologia ensina criacionismo de terra jovem de forma explícita. Se é isso
> que você quer para a sua família, é a opção mais completa nessa linha. Se você
> quer ciência mainstream, não é este."

A segunda frase serve as duas mães ao mesmo tempo.

---

## 4. Datas

- 🔒 `updatedAt` = `publishedAt` em artigo novo.
- Data só muda quando o conteúdo mudou de verdade. Nunca bump cosmético.

---

## 5. Afiliados

- Divulgação explícita na política editorial e nas páginas com link.
- Comissão **nunca** altera ranking ou veredito — inclusive quando o veredito é
  "não compre".
- Verificar os termos de cada programa antes da inscrição, incluindo se exige
  declaração de fé.
- Inscrição só depois do site ter tráfego (a maioria não aprova site vazio).

Verificado em 2026-08: **Sonlight** — 6% de comissão, cookie de 90 dias em
primeiro clique, saque mínimo US$ 50, pagamento mensal por PayPal. Critério de
aprovação comercial ("plataforma estabelecida"), sem exigência religiosa.
**Time4Learning** — programa próprio, comissão revelada só a aprovados, paga por
PayPal ou transferência.

Não verificados: Abeka, Apologia, The Good and the Beautiful, Teaching Textbooks,
CTCMath, Demme Learning, BookShark, Christianbook, Rainbow Resource, Outschool,
Amazon Associates.

---

## 6. Uma busca, uma URL

- 🔒 `primaryKeyword` única no site inteiro — o gate bloqueia canibalização.
- 🔒 Link interno para artigo inexistente derruba o build.
- "Best Christian X" e "best secular X" são intenções distintas, não
  canibalização. Cobrir os dois lados dobra o inventário do cluster comercial.

---

## 7. Antes de recomendar qualquer coisa à dona

- **Verificar a SERP com busca real e mostrar a evidência ANTES da
  recomendação.** Foi pular esse passo que produziu duas recomendações erradas na
  conversa de 2026-08-16 (licenças de contractor e SaaS vertical, ambas descritas
  como "concorrência fraca" sem verificação — ambas dominadas por empresas
  financiadas).
- Marcar explicitamente o que foi verificado e o que **não** foi.

---

## 8. Quando houver erro

- Linha visível de "reportar erro" em toda ficha de currículo.
- Correção datada, sem apagar o histórico.
- Nunca defender um rótulo errado para não admitir o erro.

---

## 9. Ritmo

- Começar com **12 currículos bem verificados**, não 40 por cima.
- 1 artigo/dia depois dos 15 iniciais. Publicação em massa em domínio novo é
  gatilho de desindexação — o `handoff-careers-site.md` do CertNorth já registra
  isso.

---

## O princípio que sustenta tudo

O que protege o site não é acertar sempre — é **nunca prometer mais do que foi
verificado**.

Com escopo declarado, um erro vira correção datada. Sem escopo declarado, um erro
só já basta para queimar a credibilidade dos dois lados de uma vez.

---

## Quando o domínio e o e-mail existirem

Uma única alteração destrava tudo. Em `platform/content/site.json`:

```json
"name": "<nome definitivo>",
"baseUrl": "https://<dominio>",
"contactEmail": "contact@<dominio>"
```

O build cuida do resto sozinho:

- `baseUrl` corrige sitemap, RSS e todas as URLs canônicas
- `contactEmail` **troca automaticamente o texto de quatro páginas** — Contato,
  Sobre, Privacidade e Termos deixam de dizer "endereço em breve" e passam a
  mostrar o e-mail real. Isso funciona pelos blocos condicionais
  `{{#email}}…{{/email}}` (só com e-mail) e `{{^email}}…{{/email}}` (só sem),
  processados em `build.js`. Nenhum texto precisa ser reescrito à mão.

Ambos os estados foram testados: com e-mail preenchido as quatro páginas mostram
o endereço e somem os avisos de pendência; sem e-mail acontece o inverso. Em
nenhum dos dois casos sobra resíduo de template na página.

**No Cloudflare, o e-mail é gratuito:** Email Routing encaminha `contact@` para o
Gmail sem caixa postal paga. É o mesmo caminho já usado no GridDojo.
