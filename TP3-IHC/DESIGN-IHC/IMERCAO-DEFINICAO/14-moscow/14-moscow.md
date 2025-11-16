# MoSCoW – Priorização de Requisitos do Aplicativo de Lembrete de Medicamentos

## 🟩 MUST HAVE (Obrigatórios)
Funcionalidades essenciais para que o app cumpra seu objetivo.

| ID | Requisito | Justificativa |
|----|-----------|---------------|
| M1 | Cadastro de medicamentos (nome, dosagem, horários, frequência) | Núcleo do app; sem isso não há lembretes. |
| M2 | Notificações push exatas no horário | Resolve o principal problema: esquecimento. |
| M3 | Alerta impossível de ignorar (som + vibração + tela) | Idosos frequentemente não percebem alertas fracos. |
| M4 | Interface extremamente simples com letras ≥ 24pt | Necessidades de visão reduzida (Sebastião e João). |
| M5 | Funcionamento 100% offline após cadastro | Idosos podem ficar sem internet. |
| M6 | Botão/ação para confirmar dose (“Tomei”) | Evita doses duplicadas e permite acompanhamento. |
| M7 | Cadastro configurável por cuidadores | Persona Maria representa esse uso real. |
| M8 | Suporte básico de acessibilidade (TalkBack + alto contraste) | Essencial para usuários com baixa visão. |

---

## 🟦 SHOULD HAVE (Importantes)
Agregam valor, mas o app funciona sem eles.

| ID | Requisito | Justificativa |
|----|-----------|---------------|
| S1 | Áudio/voz sintetizada para alertas | Ajuda idosos com baixa visão. |
| S2 | Histórico básico de tomadas | Facilita acompanhamento do cuidador. |
| S3 | Permissões para o cuidador limitar edições | Evita que idosos alterem dados sem querer. |
| S4 | Opções de som de alerta (3 opções simples) | Ajuste sem complexidade e sem assustar o idoso. |
| S5 | Tutorial inicial simples | Facilita uso para quem tem pouca familiaridade. |

---

## 🟪 COULD HAVE (Desejáveis)
Melhoram a experiência, mas não são prioridade agora.

| ID | Requisito | Justificativa |
|----|-----------|---------------|
| C1 | Enviar confirmação "Tomei" via WhatsApp | Ajuda cuidadores a monitorar à distância. |
| C2 | Integração com Google Calendar | Útil para cuidadores mais organizados. |
| C3 | Relatórios compartilháveis para médicos | Complementar, mas não essencial. |
| C4 | Ajuste de tamanho da fonte até 32pt | Para idosos com visão mais comprometida. |
| C5 | Modo super simples (apenas 1 tela) | Ajuda idosos com Alzheimer leve. |

---

## 🟥 WON’T HAVE (Não será feito agora)
Fora do escopo da primeira versão.

| ID | Requisito | Justificativa |
|----|-----------|---------------|
| W1 | Integração com pulseiras inteligentes | Complexo e pouco usado por idosos. |
| W2 | Limites dinâmicos baseados em análise médica | Exige validação profissional. |
| W3 | Cadastro por reconhecimento de voz | Aumenta complexidade do protótipo. |
| W4 | Relatórios clínicos avançados para hospitais | Fugiria do foco simples do app. |
| W5 | Lembretes ativados por geolocalização | Inadequado ao público e consome bateria. |

## Resumo Geral do MoSCoW

- **Must Have (8 itens):**  
  Tudo o que é essencial para que o idoso receba o lembrete, visualize claramente a informação e confirme a tomada do remédio.

- **Should Have (5 itens):**  
  Melhorias importantes que tornam o uso mais confortável e seguro, mas que não impedem o lançamento inicial.

- **Could Have (5 itens):**  
  Funcionalidades opcionalmente adicionadas em versões futuras, focadas em conveniência e integração externa.

- **Won’t Have (5 itens):**  
  Funcionalidades descartadas no momento por complexidade, baixa aderência ao público-alvo ou falta de validação.


