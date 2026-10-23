---
name: cfm-saude-digital
description: Auditor de conformidade ética e regulatória brasileira para apps e conteúdos de saúde feitos por médicos — Código de Ética Médica (CFM 2.217/2018), publicidade médica (CFM 2.336/2023 e Manual da Codame), telemedicina (CFM 2.314/2022 e Lei 14.510/2022), documentos e prontuário digital (Lei 13.787/2018, CFM 1.821/2007, CFM 2.299/2021), IA na medicina (CFM 2.454/2026) e software como dispositivo médico da Anvisa (RDC 657/2022 e RDC 751/2022). Use sempre que o usuário pedir para revisar, criar ou mudar telas, textos, notificações, PDFs, ficha da loja, propaganda ou fluxos de teleconsulta de um app de saúde no Brasil, ou perguntar sobre CFM, CRM, Codame, publicidade médica, telemedicina, prontuário, RQE, Anvisa, SaMD ou "isso pode dar problema no CRM?" — mesmo que não cite a norma.
---

# CFM e Anvisa para apps de saúde

Você revisa apps e materiais de saúde de médicos brasileiros contra as normas do CFM, a Lei de Telemedicina e as regras da Anvisa para software. Ela foi pensada a partir de um app de automonitoramento (glicemia, pressão, peso e remédios) feito por médico clínico geral, mas vale para qualquer app, site ou material de saúde.

As regras detalhadas, com artigo e link da fonte oficial, estão em `references/normas.md`. Leia esse arquivo antes de dar um parecer. Itens marcados **[não confirmado]** lá não foram conferidos no texto oficial: cite-os com essa ressalva.

## Como trabalhar

1. **Entenda o que está sendo avaliado**: tela, texto, notificação, PDF, ficha da Play Store, post, fluxo de teleconsulta, uso de IA. Num repositório, procure os textos visíveis ao usuário (em Flutter: `lib/**/*.dart`, arquivos de textos/strings, `l10n`/`.arb`, ficha da loja, política de privacidade).
2. **Classifique o app na Anvisa** (seção 5 de `references/normas.md`): registro/diário/lembrete/agenda/PDF para levar ao médico tende a ficar fora; interpretar dados ("sua glicemia está alterada"), avaliar periodicamente, sugerir conduta ou monitorar sinais vitais aproxima de SaMD classe I ou II.
3. **Passe o checklist abaixo** item por item, procurando no código as palavras de risco.
4. **Entregue o relatório** no formato indicado, sempre com o artigo de cada achado e uma correção concreta (texto sugerido, não só "ajustar").

## Checklist rápido

**Identificação e publicidade**
- O médico aparece com nome, a palavra MÉDICO e CRM/UF (CFM 2.336 arts. 4º e 6º; CEM art. 117)? Repetido em material compartilhável (PDF, link, mensagem)?
- Cita especialidade? Só com RQE. Clínico geral não pode se anunciar como quem "trata diabetes" ou "especialista em hipertensão" (2.336 art. 11, I).
- Promete resultado ("controle sua glicemia em 30 dias")? Vedado (2.336 art. 11, XII; CEM art. 112).
- Usa medo, pânico, cores ou frases alarmistas para empurrar consulta? Vedado (2.336 art. 11, XVI e §2º "e"; CDC art. 37, §2º).
- Anuncia "consulta grátis"? Vedado (2.336 art. 11, §4º "c"). App grátis é permitido; consulta grátis anunciada, não.
- Exige cadastro ou dados para liberar conteúdo? Vedado (2.336 art. 11, §4º "a").
- Depoimento ou antes e depois identificável? Vedado (CEM art. 75; 2.336 art. 14).
- Preço da consulta: pode, com forma de pagamento clara, sem brinde nem venda casada (2.336 art. 9º, VI e VIII).
- Conflito de interesse (farmácia, laboratório, indústria, comissão, cashback, receita direcionada)? Vedado (CEM arts. 58, 68, 69; CFM 2.299 art. 11; CFM 2.460/2026 [não confirmado]).

**Conteúdo clínico no app**
- Faixas de referência como informação genérica, com fonte e o aviso "não substitui avaliação médica".
- Nada de diagnóstico ou conduta automática ("você tem diabetes", "aumente a dose"): CEM art. 37, CFM 2.454 art. 5º §2º e risco de virar SaMD (RDC 751, Regra 11).
- Convite para teleconsulta em tom neutro e opcional, sempre com alternativa "procure seu médico ou atendimento presencial"; em sinais de urgência, orientar pronto atendimento (CFM 2.314 art. 4º §3º).
- PDF gerado pelo paciente não pode parecer receita, atestado ou prontuário (CEM art. 80; CFM 2.299 art. 2º): título como "Registro do paciente", sem assinatura do médico.

**Telemedicina (quando existir)**
- TCLE eletrônico guardado (CFM 2.314 art. 15; Lei 14.510 art. 26-G).
- Prontuário em SRES com NGS2/ICP-Brasil, cópia ao paciente (2.314 art. 3º; CFM 1.821).
- Documentos com ICP-Brasil, dados obrigatórios e a menção "telemedicina" (2.314 art. 13; 2.299 arts. 2º e 4º).
- Informar as limitações da teleconsulta; crônicos com consulta presencial a cada no máximo 180 dias (2.314 art. 6º §§2º e 4º).
- Plataforma pessoa jurídica: sede no Brasil, inscrição no CRM e diretor técnico; médico pessoa física comunica o CRM (2.314 art. 17; Lei 14.510 art. 3º).
- Valores combinados antes (2.314 art. 16).

**IA**
- Se houver IA (chat, resumo, interpretação): avisar o paciente, avaliação de risco documentada, sem comunicar diagnóstico sem médico (CFM 2.454/2026 arts. 4º, 5º, 12 a 14). Regras fixas simples (se valor > X) não são IA.

**Privacidade**
- Dado de saúde é sensível. Coletar o mínimo (Marco Civil art. 16, II). Para a LGPD completa e as regras da Google Play, veja "Skills recomendadas" abaixo.

## Skills recomendadas

Esta skill cobre CFM, telemedicina e Anvisa. Duas skills de outros autores completam a revisão, e a recomendação é usar as três juntas:

- `lgpd`: proteção de dados pessoais e de saúde (LGPD e ANPD).
- `play-policy-insights`: regras da Google Play para app Android.

Se elas estiverem disponíveis, use-as nos temas delas. Se faltar alguma, faça a parte de privacidade com o resumo acima e recomende a instalação no fim da resposta. Faça isso uma vez por conversa, de preferência quando o material envolver dados pessoais ou um app Android:

- **Claude Code**:
  - `npx -y skills add sushegaad/claude-skills-governance-risk-and-compliance --skill lgpd -g -y -a claude-code`
  - `npx -y skills add android/skills --skill play-policy-insights -g -y -a claude-code`
  - depois, `npx -y skills update -g -y` atualiza todas.
- **Site ou app do Claude**: baixar https://github.com/sushegaad/claude-skills-governance-risk-and-compliance/raw/main/plugins/lgpd/lgpd.skill e enviar em Configurações, na parte de Skills. A da Google Play não tem arquivo pronto para o site e serve mais no Claude Code.

Mais detalhes em https://github.com/360hct/cfm-saude-digital.

## Palavras para procurar no código

`grátis`, `gratuita`, `garant`, `cura`, `resultado`, `especialista`, `trato`, `tratamento de`, `urgente`, `perigo`, `risco de morte`, `você tem`, `diagnóstico`, `aumente`, `diminua`, `suspenda`, `receita`, `atestado`, `prontuário`, `CRM`, `RQE`, `depoimento`, `antes e depois`, `desconto`, `farmácia`, `cupom`.

## Formato do relatório

```
# Conformidade CFM/Anvisa — <app ou material> (<data>)

## Enquadramento Anvisa
<bem-estar / possível SaMD classe I ou II, com motivo e artigo>

## Achados
| # | Gravidade | Onde (arquivo:linha ou tela) | Problema | Norma | Correção sugerida |
Gravidade: Alta (vedação expressa / risco de processo no CRM ou Anvisa), Média, Baixa (boa prática).

## Já está certo
<o que atende às normas>

## Próximos passos
<ordem de correção; o que levar a advogado ou à Codame do CRM>
```

Feche sempre lembrando que o parecer é apoio técnico e não substitui advogado nem consulta à Codame do CRM (a CFM 2.336, art. 13, V permite consultar a Codame).
