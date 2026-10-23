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

### No Claude Code

```bash
npx -y skills add 360hct/cfm-saude-digital -g -y -a claude-code
```

Depois, abra uma sessão nova.

### No site ou no app do Claude

1. Baixe o arquivo: [cfm-saude-digital.zip](https://github.com/360hct/cfm-saude-digital/releases/latest/download/cfm-saude-digital.zip).
2. No Claude, abra Configurações e vá até a parte de Skills. Se ela não aparecer, ligue antes a execução de código e criação de arquivos.
3. Envie o arquivo como ele veio, sem descompactar.

## Atualizar

No Claude Code, este comando busca a versão nova de todas as skills instaladas pelo `npx skills`:

```bash
npx -y skills update -g -y
```

No site ou no app do Claude, a skill não se atualiza sozinha. Para atualizar, baixe o arquivo de novo pelo mesmo link e envie outra vez. O link sempre entrega a versão mais recente.

## Skills que combinam com esta

Elas são de outros autores e se atualizam pelo mesmo comando `npx -y skills update -g -y`.

- **LGPD**, para proteção de dados de pacientes (autor: sushegaad, licença MIT):

  ```bash
  npx -y skills add sushegaad/claude-skills-governance-risk-and-compliance --skill lgpd -g -y -a claude-code
  ```

  No site do Claude, baixe [lgpd.skill](https://github.com/sushegaad/claude-skills-governance-risk-and-compliance/raw/main/plugins/lgpd/lgpd.skill) e envie em Configurações, na parte de Skills.

- **Regras da Google Play**, para quem publica app Android (autor: Google, licença Apache 2.0):

  ```bash
  npx -y skills add android/skills --skill play-policy-insights -g -y -a claude-code
  ```

## Como usar

Basta pedir normalmente. Por exemplo:

- "Revise os textos do meu site pelas regras do CFM."
- "Meu app de saúde precisa de registro na Anvisa?"
- "Posso divulgar o valor da consulta no Instagram?"

## Licença

MIT. Veja o arquivo [LICENSE](LICENSE).
