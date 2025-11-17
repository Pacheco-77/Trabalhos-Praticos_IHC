# a) Avaliação dos itens a serem comparados
Este benchmarking segue o cenário do aplicativo em questão. O foco é em um App mobile semelhante para lembretes de medicamentos, priorizando usabilidade para idosos e cuidadores.  Incluindo reviews de acessibilidade, funcionalidades e problemas resolvidos. Selecionamos 4 apps principais: Medisafe, MyTherapy, CareZone e DoseMed.  Os itens comparados foram definidos com base nas prioridades do projeto:  

- Funcionalidades: Cadastro de remédios, notificações push, confirmação de tomada.  
- Acessibilidade: Interface simples, fontes grandes (≥24pt), voz, contraste alto.
- Layout/UX: Número de telas/ações, complexidade para idosos (ex.: tutoriais, offline).  
- Experiência do Usuário (Idoso/Cuidador): Modo cuidador, relatórios, integração familiar.  
- Offline: Funcionamento sem internet.

---

# b) Definição dos similares-alvo

Selecionamos apps com foco em idosos, baseados em popularidade e reviews. Exemplos:

- Medisafe: App popular para múltiplos perfis, com alertas para famílias.
  
- <img width="863" height="306" alt="image" src="https://github.com/user-attachments/assets/f93fc9df-fbbb-4c1a-bf5f-2657793fbf5b" />

- MyTherapy: Tracker com mood/symptoms, mas setup inicial complexo.
  
- <img width="536" height="442" alt="image" src="https://github.com/user-attachments/assets/a60ea416-25d6-4303-9046-8c6590b14bfc" />

- CareZone: Gerenciamento familiar, com scan de rótulos.
  
- <img width="478" height="429" alt="image" src="https://github.com/user-attachments/assets/a8afc0c7-4e74-455e-a048-c424a7b03c66" />

- DoseMed: Novo em 2025, com IA adaptável e interface minimalista para idosos.
  
- <img width="1568" height="654" alt="image" src="https://github.com/user-attachments/assets/862f3d4d-7127-4537-baf0-94a451624419" />

---

# c) Estabelecimento de indicadores e obtenção de dados

Para cada app, respondemos: 

1. Quais problemas o produto resolve? Esquecimento de doses, rastreio de adesão, suporte familiar.  
2. Como os problemas são resolvidos? Via notificações, logs e compartilhamento.  
3. Quais os pontos fortes e fracos dessas soluções? (Foco em IHC: usabilidade para visão/memória reduzida).

Na tabela abaixo, é mostrado como ficou feita a divisão das respostas com base nos App estudados:

| App Similar | Problemas Resolvidos | Como Resolvidos | Pontos Fortes | Pontos Fracos |
|-------------|----------------------|-----------------|---------------|---------------|
| Medisafe | Esquecimento de horários; falta de acompanhamento familiar; múltiplas dosagens. | Notificações push com som/vibração; perfis múltiplos para cuidadores; relatórios PDF/Excel exportáveis. |  Alto score MARS (4/5) em usabilidade; tutoriais educativos; integração com wearables; alertas para refil. | Relatórios difíceis de navegar; anúncios na versão free; sobrecarga visual em telas com gráficos. |
| MyTherapy | Adesão a regimes complexos; monitoramento de sintomas/mood. | Lembretes flexíveis + tracker de sintomas; relatórios semanais por e-mail. | Gráficos coloridos claros; foco em motivação (recompensas); >10M usuários. | Setup inicial desafiador para idosos; não offline total; interface com muitos menus. |
| CareZone | Organização de múltiplos remédios; agendamentos médicos; reações a doses. | Scan de rótulos para cadastro rápido; notas sobre sintomas; compartilhamento familiar. | Fácil para cuidadores (desktop + mobile); trackers de sintomas; HIPAA-compliant. | Dependente de internet para sync; interface não otimizada para fontes gigantes; sem voz. |
| DoseMed | Rotinas personalizadas; interações com comida/álcool; suporte para pets/família. | IA para lembretes adaptáveis; alertas de interações; histórico simples. | Interface minimalista (1-2 toques); AI para idosos (voz personalizada); offline parcial. | Novo (menos reviews); premium para IA full; foco em customização pode confundir iniciantes. |

---

# d) Comparação das Informações Coletadas

Matriz comparativa consolidada, destacando se cada similar atende (✅) ou não (❌) aos requisitos IHC do LembreMed (baseados em certezas/suposições da Matriz CSD). Escala: Verde = atende bem; Amarelo = parcial; Vermelho = não atende.  

| Similar | Funcionalidades | Acessibilidade | Layout/UX | Experiência Usuário | Offline | **Score IHC (1-5)** |
|---------|-----------------|----------------|-----------|----------------------|---------|---------------------|
| **Medisafe** | ✅ | 🟡 | 🟡 | ✅ | ❌ | 4.0 |
| **MyTherapy** | ✅ | 🟡 | ❌ | 🟡 | ❌ | 3.0 |
| **CareZone** | ✅ | 🟡 | ✅ | ✅ | ❌ | 4.0 |
| **DoseMed** | ✅ | ✅ | ✅ | ✅ | 🟡 | **4.5** |

> **Legenda:** ✅ Atende | 🟡 Parcial | ❌ Não atende

---

## Resultados Estratégicos

- **Nenhum app é 100% offline** → Oportunidade crítica para o nosso App.  
- **DoseMed é o mais próximo** em simplicidade, mas falta WhatsApp e botão gigante.  
- **75% exigem internet** → Problema para idosos rurais (IBGE 2023).  
- **Acessibilidade parcial**: Apenas **25% com TTS nativo**.  
