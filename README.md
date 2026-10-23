# cfm-saude-digital

Skill para o Claude que revisa apps, sites e textos de saúde de médicos brasileiros. Ela confere o material contra estas normas:

- Código de Ética Médica (Res. CFM 2.217/2018)
- publicidade médica (Res. CFM 2.336/2023 e Manual da Codame)
- telemedicina (Res. CFM 2.314/2022 e Lei 14.510/2022)
- prontuário e documentos digitais (Lei 13.787/2018 e Res. CFM 1.821/2007 e 2.299/2021)
- IA na medicina (Res. CFM 2.454/2026)
- software como dispositivo médico na Anvisa (RDC 657/2022 e 751/2022)

Cada achado vem com o artigo, a gravidade e uma sugestão de texto corrigido. As normas foram conferidas nos textos oficiais em 21/10/2026.

A skill é apoio técnico. Ela não substitui advogado nem consulta à Codame do CRM.

## Instalar

**Recomendado: instale junto as skills de LGPD e de regras da Google Play.** Esta skill cobre CFM, telemedicina e Anvisa. As outras duas completam a revisão:

- **lgpd**: proteção dos dados dos pacientes (LGPD e ANPD). Autor: sushegaad, licença MIT.
- **play-policy-insights**: regras da Google Play para publicar app Android. Autor: Google, licença Apache 2.0.

As duas são de outros autores e vêm direto dos repositórios deles, então recebem as atualizações deles.

### No Claude Code

Cole os três comandos no Terminal. O primeiro instala esta skill e os outros dois instalam as recomendadas:

```bash
npx -y skills add 360hct/cfm-saude-digital -g -y -a claude-code
npx -y skills add sushegaad/claude-skills-governance-risk-and-compliance --skill lgpd -g -y -a claude-code
npx -y skills add android/skills --skill play-policy-insights -g -y -a claude-code
```

Depois, abra uma sessão nova.

### No site ou no app do Claude

1. Baixe os arquivos:
   - esta skill: [cfm-saude-digital.zip](https://github.com/360hct/cfm-saude-digital/releases/latest/download/cfm-saude-digital.zip);
   - a recomendada de LGPD: [lgpd.skill](https://github.com/sushegaad/claude-skills-governance-risk-and-compliance/raw/main/plugins/lgpd/lgpd.skill).
2. No Claude, abra Configurações e vá até a parte de Skills. Se ela não aparecer, ligue antes a execução de código e criação de arquivos.
3. Envie cada arquivo como ele veio, sem descompactar.

A skill da Google Play não tem arquivo pronto para o site. Ela é mais útil no Claude Code, para quem desenvolve app Android.

## Atualizar

No Claude Code, este comando busca a versão nova das três skills, e de qualquer outra instalada pelo `npx skills`:

```bash
npx -y skills update -g -y
```

No site ou no app do Claude, as skills não se atualizam sozinhas. Para atualizar, baixe os arquivos de novo pelos mesmos links e envie outra vez. Os links sempre entregam a versão mais recente.

Se você instalou só esta skill, ela mesma vai lembrar de instalar as duas recomendadas quando o assunto for dados pessoais ou app Android.

## Como usar

Basta pedir normalmente. Por exemplo:

- "Revise os textos do meu site pelas regras do CFM."
- "Meu app de saúde precisa de registro na Anvisa?"
- "Posso divulgar o valor da consulta no Instagram?"

## Licença

MIT. Veja o arquivo [LICENSE](LICENSE).
