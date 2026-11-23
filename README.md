# Desafio: Do Alerta à Resposta — Investigação de um Achado do Amazon GuardDuty

## Objetivo

Neste desafio, desenvolvi um prompt para auxiliar na investigação de alertas do Amazon GuardDuty. A ideia é organizar a análise, levantar hipóteses, identificar evidências e ajudar na tomada de decisão, sem assumir que todo alerta representa um incidente confirmado.

Escolhi trabalhar com o achado `Policy:IAMUser/RootCredentialUsage`, relacionado ao uso das credenciais da conta Root da AWS, por se tratar de uma identidade com privilégios elevados e que exige atenção especial.

## Prompt desenvolvido

Quero analisar um alerta do Amazon GuardDuty de forma organizada, buscando entender o que aconteceu, quais possibilidades podem explicar o evento e quais informações preciso verificar antes de tomar alguma decisão.

### Informações do achado

- **Tipo:** Policy:IAMUser/RootCredentialUsage
- **Recurso afetado:** Usuário Root da conta AWS.
- **Severidade:** Média — valor utilizado como exemplo.
- **Quando:** Evento identificado durante um período recente de monitoramento, sem horário exato confirmado.
- **Descrição:** O GuardDuty identificou o uso das credenciais da conta Root da AWS. Como essa conta possui privilégios elevados, quero entender em que contexto ocorreu essa atividade e se existe algum motivo para preocupação.

### Público da análise

A análise será direcionada a um administrador responsável pelo ambiente AWS, que possui conhecimentos básicos de infraestrutura, IAM e segurança em nuvem.

Quero que a resposta seja clara, direta e fácil de entender, mesmo para quem ainda está desenvolvendo experiência na área de segurança cloud.

### Objetivo da investigação

Quero entender o alerta, avaliar as possíveis causas, identificar quais evidências precisam ser consultadas e ter uma base para decidir quais ações devem ser tomadas, sem tirar conclusões precipitadas.

### Contexto do ambiente

Até o momento, considero as seguintes informações:

- A conta Root possui privilégios administrativos abrangentes e pode realizar operações críticas dentro da AWS.
- Seu uso deve ser restrito a atividades que realmente exigem esse nível de acesso.
- Ainda não confirmei quem realizou a atividade, de onde partiu o acesso ou qual operação foi executada.
- Também preciso verificar se a conta possui MFA habilitado e quais registros estão disponíveis para analisar o evento.
- Não vou considerar nenhum controle de segurança como ativo ou configurado corretamente sem antes confirmar essa informação.

### Como quero que a análise seja organizada

Responda seguindo esta ordem:

1. **Entendimento do alerta:** explique em linguagem simples o que esse achado significa e por que merece atenção.
2. **Possíveis causas:** apresente hipóteses que possam explicar o evento, considerando tanto uma atividade administrativa legítima quanto a possibilidade de uma atividade não autorizada.
3. **Evidências:** explique quais informações podem ajudar a confirmar ou descartar cada hipótese e indique onde posso encontrar esses registros dentro da AWS.
4. **Possíveis ações:** apresente as medidas que podem ser consideradas, separando verificações que não causam impacto de ações que possam alterar acessos, credenciais ou afetar algum recurso.
5. **Pendências:** informe o que ainda preciso verificar para conseguir chegar a uma conclusão mais confiável.

### Cuidados durante a análise

- Não invente informações que eu não tenha fornecido, como IPs, horários, IDs, nomes de recursos ou configurações.
- Diferencie informações confirmadas de hipóteses e suposições.
- Não considere um alerta como incidente confirmado apenas por ter sido gerado pelo GuardDuty.
- Não classifique o evento como legítimo ou falso positivo sem evidências.
- Antes de sugerir alguma ação que possa interromper acessos ou afetar o ambiente, explique brevemente o possível impacto.
- Se alguma informação estiver faltando, informe o que preciso consultar, em vez de tentar completar os dados por conta própria.

Quero que a análise seja objetiva, organizada e baseada nas informações disponíveis, para que eu consiga entender o evento e decidir como prosseguir com a investigação.

---

## Testes realizados com o prompt

### Teste 1 — Análise do achado original

**Entrada:** `Policy:IAMUser/RootCredentialUsage`

**Objetivo:** verificar se o prompt consegue organizar a investigação, separar fatos de hipóteses e indicar evidências necessárias, sem concluir automaticamente que houve comprometimento.

### Teste 2 — Informações desconhecidas

**Pergunta adicional:** Qual país originou o acesso e qual IP foi utilizado?

**Objetivo:** verificar se o prompt respeita a ausência de informações e evita inventar dados que não foram fornecidos.

### Teste 3 — Contexto ambíguo

**Contexto adicional:** O uso da conta Root ocorreu durante uma migração planejada de infraestrutura AWS, mas ainda não foi confirmado se a atividade específica estava relacionada à migração.

**Objetivo:** verificar se o prompt considera uma possível atividade legítima sem descartar o alerta prematuramente, exigindo evidências para sustentar qualquer conclusão.

## Critérios de avaliação

Durante os testes, considerei importante verificar se a análise:

- Mantém a estrutura definida.
- Separa fatos, hipóteses e informações desconhecidas.
- Evita inventar IPs, países, horários e identificadores.
- Indica onde buscar evidências na AWS.
- Evita conclusões precipitadas.
- Separa ações de baixo impacto das que podem afetar o ambiente.
- Reconhece quando precisa de mais informações.

## Conclusão

O desenvolvimento desse prompt mostrou como a forma de escrever uma instrução pode influenciar a qualidade de uma análise feita por inteligência artificial.

Em uma investigação de segurança, não basta obter uma resposta que pareça completa. É importante saber de onde vieram as informações, quais pontos ainda são hipóteses e o que precisa ser verificado antes de tomar uma decisão.

A proposta deste prompt é servir como apoio à investigação, ajudando a organizar o raciocínio e as evidências, sem substituir a validação técnica ou a decisão do responsável pelo ambiente.
