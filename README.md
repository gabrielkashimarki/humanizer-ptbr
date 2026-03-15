# humanizer-ptbr

Skill para Claude que remove padrões de escrita gerada por IA de textos em **português brasileiro** — especialmente para LinkedIn e comunicação B2B.

Baseado no [humanizer](https://github.com/blader/humanizer) (EN) com uma camada adicional de **27 padrões unificados** cobrindo estruturas retóricas típicas de LLM em PT-BR.

---

## O problema

LLMs escrevem para o maior denominador comum. O resultado é texto que:

- Infla qualquer coisa com "momento pivotal", "cenário atual" e "testemunho vivo"
- Abre com antíteses moralizantes: *"Produtividade sem foco não é eficiência. É ocupação."*
- Fecha com otimismo vago: *"O futuro é promissor para quem souber se adaptar."*
- Usa gerúndio decorativo: *"evidenciando a sinergia entre automação e julgamento humano"*
- Soa como post de LinkedIn de 100k likes sem nenhum contexto real

Essa skill força o modelo a produzir texto com **consequência real, agente claro e custo visível**.

---

## 27 padrões detectados

### Bloco 1 — Conteúdo
| # | Padrão | Status |
|---|---|---|
| 1 | Inflação de Significado e Legado | ❌ Proibido |
| 2 | Gerúndio Decorativo (-ing / -ando) | ❌ Proibido |
| 3 | Linguagem Promocional | ❌ Proibido |
| 4 | Promessa Vaga de Transformação | ❌ Proibido |
| 5 | Atribuições Vagas / Generalização Sem Fonte | ❌ Proibido |
| 6 | Seção Formulaica de Desafios e Perspectivas | ❌ Proibido |

### Bloco 2 — Linguagem e Gramática
| # | Padrão | Status |
|---|---|---|
| 7 | Vocabulário Superutilizado de IA (EN + PT-BR) | ❌ Proibido |
| 8 | Copula Avoidance ("atua como", "se configura como") | ❌ Proibido |
| 9 | Paralelismos Negativos ("não se trata apenas de...") | ❌ Proibido |
| 10 | Regra de Três Artificial | ❌ Proibido |
| 11 | Ciclagem de Sinônimos | ❌ Proibido |
| 12 | Falsas Amplitudes ("da captação à fidelização") | ❌ Proibido |

### Bloco 3 — Estrutura Retórica (PT-BR)
| # | Padrão | Status |
|---|---|---|
| 13 | Antítese Moralizante Binária ("X sem Y não é Z. É W.") | ❌ Proibido |
| 14 | Reenquadramento Conceitual Absoluto ("O problema não é X. É Y.") | ❌ Proibido |
| 15 | Frase de Efeito Autossuficiente ("Clareza é poder.") | ❌ Proibido |
| 16 | Perguntas Retóricas Encadeadas | ❌ Proibido |
| 17 | Autoridade Autodeclarada ("Como especialista...") | ❌ Proibido |
| 18 | Storytelling Artificial de Virada | ⚠️ Restrito |
| 19 | Lista Educacional Neutra | ⚠️ Restrito |

### Bloco 4 — Estilo Visual
| # | Padrão | Status |
|---|---|---|
| 20 | Emojis como Títulos ou Marcadores | ❌ Proibido |
| 21 | Negrito Excessivo / Inline-Header Lists | ❌ Proibido |
| 22 | Em Dash em Excesso | ❌ Proibido |
| 23 | Title Case em Títulos | ❌ Proibido |

### Bloco 5 — Comunicação e Enchimento
| # | Padrão | Status |
|---|---|---|
| 24 | Artefatos de Chatbot ("Espero ter ajudado!") | ❌ Proibido |
| 25 | Conclusão Moralizante / Genérica Positiva | ❌ Proibido |
| 26 | Frases de Enchimento (tabela com 20+ itens PT-BR + EN) | ❌ Proibido |
| 27 | Hedging Excessivo | ❌ Proibido |

---

## Exemplo

**Antes (cheira a IA):**
> No cenário atual, cada vez mais empresas estão adotando soluções inovadoras e transformadoras. Produtividade sem processo não é eficiência. É ocupação. Como especialista com anos de experiência, acredito que isso representa um marco fundamental. O futuro é promissor para quem souber se adaptar.

**Depois (humanizado):**
> Testamos a ferramenta em 3 clientes durante 60 dias. Em dois, o tempo de onboarding caiu pela metade. No terceiro, não fez diferença — o gargalo era comercial, não operacional.

---

## Formatos de substituição obrigatórios

A skill não só remove padrões — ela substitui por estruturas com substância:

**Formato A — Consequência Vivida**
> Fiz [ação]. O efeito foi [consequência concreta]. Demorou [tempo] para corrigir.

**Formato B — Custo Invisível**
> Todo mundo fala de [benefício]. Pouca gente fala de [custo]. É aí que o problema começa.

**Formato C — Tensão Operacional**
> Funciona no discurso. Quebra na rotina. Principalmente quando [condição real].

**Formato D — Pergunta que Não Moraliza**
> Você está tentando [objetivo]. Mas o sistema aguenta isso hoje?

---

## Instalação

### Claude Code
```bash
mkdir -p ~/.claude/skills/humanizer-ptbr
git clone https://github.com/SEU_USUARIO/humanizer-ptbr.git ~/.claude/skills/humanizer-ptbr
```

### Claude.ai (Projects)
1. Crie um novo Project no Claude.ai
2. Vá em **Project Instructions**
3. Cole o conteúdo do `SKILL.md`
4. Salve — a skill estará ativa em todas as conversas do projeto

---

## Uso

No Claude Code:
```
/humanizer-ptbr

[cole seu texto aqui]
```

Ou diretamente:
```
Humaniza esse texto: [seu texto]
```

O output segue 3 etapas:
1. Rascunho reescrito
2. "O que ainda cheira a IA?" (bullets com os sinais restantes)
3. Versão final revisada

---

## Regra de ouro

> **Se a estrutura funcionaria igualmente bem em qualquer tema — marketing, carreira, saúde, vida pessoal — ela é genérica demais. Reescreva.**

---

## Referências

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
- [humanizer by blader](https://github.com/blader/humanizer) — estrutura base (MIT)
- Camada Anti-Padrões PT-BR: adaptação original para português brasileiro

## Licença

MIT
