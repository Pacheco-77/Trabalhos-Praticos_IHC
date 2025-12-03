# 25. Heurísticas UX

## Tela 1: Login

Tela inicial de acesso ao aplicativo, focada na entrada de credenciais e opções de conta.

<img width="440" height="956" alt="login" src="https://github.com/user-attachments/assets/cf8e533b-63c4-4c51-8c07-d036d7d157a7" />


| **Aspecto**        | **Análise** |
|-------------------|-------------|
| Usabilidade       | A tela é direta e exige apenas dois campos, minimizando o esforço de input. O contraste visual do botão *Entrar* facilita o foco na ação principal. |
| UX (Experiência do Usuário) | Uso de caracteres ocultos na senha promove sensação de segurança. A frase instruicional é educada e informativa. |
| Comunicabilidade  | A regra da senha é comunicada antes do envio (“A senha deve conter apenas dígitos”). |
| Acessibilidade    | Alto contraste dos botões e hierarquia visual adequada entre ações. |

Heurísticas de Nielsen

| Heurística Aplicada | Onde e Como se Manifesta |
| :--- | :--- |
| **1 – Visibilidade do Status do sistema** | **Feedback nos Campos:** O texto "A senha deve conter apenas dígitos" dá feedback imediato sobre uma restrição do campo de senha. |
| **4 – Consistência e padronização** | **Elementos de Input:** Os campos de input para CPF e senha usam o mesmo estilo visual (retângulo branco com borda e fundo levemente arroxeados), mantendo a padronização. |
| **5 – Prevenção de erros** | **Máscara/Formato:** A formatação do campo CPF (000.000.000-00) sugere o uso de máscara, prevenindo erros de digitação de formato. |
| **8 – Estética e design minimalista** | **Foco:** O design é limpo, utiliza apenas os campos essenciais para login, evitando poluição visual. |


## Tela 2: Inicial App
Tela de boas-vindas e painel principal com ações rápidas e resumo de pendências.

<img width="440" height="956" alt="INICIAL APP" src="https://github.com/user-attachments/assets/d20837c1-4112-4057-8a9d-1091be219ac0" />

| **Aspecto**        | **Análise** |
|-------------------|-------------|
| Usabilidade       | Botões grandes com alta facilidade de toque favorecem interações frequentes. |
| UX                | Saudação personalizada que melhora a conexão emocional. |
| Comunicabilidade  | Badge vermelho indica prioridade de forma clara (Medicamentos Pendentes). |
| Acessibilidade    | Ícones com rótulos textuais na navegação oferecem redundância perceptiva. |


Heurísticas de Nielsen

| Heurística Aplicada | Onde e Como se Manifesta |
| :--- | :--- |
| **1 – Visibilidade do Status do sistema** | **Contador de Pendências:** O *badge* vermelho com o número **"6"** informa imediatamente o usuário sobre a quantidade de ações pendentes. |
| **3 – Controle e liberdade para o usuário** | **Ações Diretas:** O usuário tem controle sobre suas próximas ações, com botões bem definidos para tarefas chave (**ADICIONAR MEDICAMENTO**, **ROTINA**, etc.). |
| **4 – Consistência e padronização** | **Navegação Fixa:** A barra de navegação inferior (**Início, Horários, Perfil**) é consistente com as outras telas, permitindo um movimento padronizado. |
| **6 – Reconhecimento em vez de recordação** | **Ações Rotuladas e Iconizadas:** Botões com rótulos claros (ex: "ADICIONAR MEDICAMENTO") e ícones de suporte (`+` roxo) facilitam o reconhecimento da função. |

## Tela 3: Cadastro Medicamento
Tela de formulário dedicada à entrada de informações para adicionar um novo medicamento ao sistema.

<img width="440" height="956" alt="CADASTRO MEDICAMENTO" src="https://github.com/user-attachments/assets/4284ceff-14f6-4dd2-b359-e1c39e94161d" />

| **Aspecto**        | **Análise** |
|-------------------|-------------|
| Usabilidade       | Formulário simples, com campos empilhados e rótulos claros. |
| UX                | Botão de voltar dá controle e reduz frustração. |
| Comunicabilidade  | O título confirma o contexto da tarefa sendo realizada. |
| Acessibilidade    | Título e seta com forte contraste garantem visibilidade da tarefa principal. |


Heurísticas de Nielsen

| Heurística Aplicada | Onde e Como se Manifesta |
| :--- | :--- |
| **3 – Controle e liberdade para o usuário** | **Ação de Retorno:** O ícone de **seta para trás (←)** no cabeçalho dá ao usuário a liberdade de cancelar a ação e voltar à tela anterior. |
| **4 – Consistência e padronização** | **Layout e Campos:** O estilo dos campos de input (fundo arroxeado) é o mesmo usado na tela de Login, reforçando a coerência visual. |
| **8 – Estética e design minimalista** | **Clareza de Propósito:** A tela é dedicada a uma única tarefa ("ADICIONAR MEDICAMENTO") e exibe apenas os campos essenciais. |

## Tela 4: Cuidador 
Tela para visualizar informações de contato e a identidade do Cuidador Responsável.

<img width="440" height="1365" alt="CUIDADOR" src="https://github.com/user-attachments/assets/b930a077-98aa-474c-9a4b-ba2a469607ff" />

| **Aspecto**        | **Análise** |
|-------------------|-------------|
| Usabilidade       | Botão “LIGAR AGORA” grande e destacado para ação imediata. |
| UX                | Foto/ícone do cuidador traz confiança e relação humana. |
| Comunicabilidade  | Ícones comunicam claramente a natureza de cada dado (telefone, e-mail). |
| Acessibilidade    | Informações bem separadas em blocos para facilitar leitura. |

Heurísticas de Nielsen

| Heurística Aplicada | Onde e Como se Manifesta |
| :--- | :--- |
| **2 – Correspondência entre o sistema e o mundo real** | **Ícones Realistas:** O telefone azul e o envelope azul ao lado das informações de "Telefone" e "Email" correspondem à forma como as pessoas interagem com esses meios de comunicação no mundo real. |
| **3 – Controle e liberdade para o usuário** | **Ação Primária:** O botão grande e vermelho **"LIGAR AGORA"** oferece um atalho para a ação mais provável, dando eficiência e controle. |
| **4 – Consistência e padronização** | **Informações de Contato:** As informações são dispostas em blocos claros, seguindo um padrão de apresentação de dados de contato. |

## Tela 5: Lembretes
Tela para visualizar e gerenciar lembretes de rotina não relacionados a medicamentos (hábitos).

<img width="440" height="1206" alt="LEMBRETES" src="https://github.com/user-attachments/assets/d7d4b2b6-1c04-40e6-a9e6-44e2f373cb1f" />

| **Aspecto**        | **Análise** |
|-------------------|-------------|
| Usabilidade       | Diferenciação visual entre os lembretes facilita localização rápida. |
| UX                | Design colorido torna a tarefa mais engajadora. |
| Comunicabilidade  | Ícones e cores funcionam como código mnemônico para leitura rápida. |
| Acessibilidade    | Redundância de informações: cor + ícone + texto. |


Heurísticas de Nielsen

| Heurística Aplicada | Onde e Como se Manifesta |
| :--- | :--- |
| **2 – Correspondência entre o sistema e o mundo real** | **Iconografia Icônica:** O uso de ícones (Gota, Maçã, Sol, Lua) representa diretamente as ações (Beber, Comer, Caminhar, Dormir), facilitando a comunicabilidade. |
| **6 – Reconhecimento em vez de recordação** | **Design Distinto:** Cada lembrete tem um ícone e uma cor de fundo distintos (Azul, Laranja, Amarelo, Roxo), permitindo ao usuário reconhecer imediatamente o tipo de lembrete. |
| **7 – Eficiência e flexibilidade de uso** | **Ações Agrupadas:** Os lembretes são agrupados visualmente em blocos que podem funcionar como atalhos para configurar a rotina, oferecendo eficiência no acesso. |


## Tela 6: Lista de Medicamentos 
Tela principal para visualização de todos os medicamentos agendados e seus respectivos horários.

<img width="440" height="1048" alt="LISTA DE MEDICAMENTOS" src="https://github.com/user-attachments/assets/c26e609c-e4c2-4572-b163-345529c5e72e" />

| **Aspecto**        | **Análise** |
|-------------------|-------------|
| Usabilidade       | Lista com boa escaneabilidade para grandes quantidades de dados. |
| UX                | Elemento destacado indica a prioridade imediata (próximo remédio). |
| Comunicabilidade  | Layout consistente entre os itens comunica padrão de dados. |
| Acessibilidade    | Fonte legível e espaçamentos adequados evitam poluição visual. |


Heurísticas de Nielsen

| Heurística Aplicada | Onde e Como se Manifesta |
| :--- | :--- |
| **1 – Visibilidade do Status do sistema** | **Feedback Visual de Ação:** O item do medicamento **"SINVESTANTINA"** com fundo verde indica que está em um estado ativo/concluído. |
| **6 – Reconhecimento em vez de recordação** | **Estrutura de Lista:** A lista vertical e consistente é um padrão de design reconhecido, onde o usuário reconhece o formato e a hierarquia da informação (Nome, Dose, Horário). |
| **7 – Eficiência e flexibilidade de uso** | **Navegação Direta:** O ícone **"Horários"** na barra inferior está ativo (em verde/turquesa) e destacado, permitindo que usuários que acessam esta tela frequentemente o façam de forma eficiente. |

## Tela 7: Perfil Usuário Idoso
Tela para visualização de dados pessoais do usuário e gestão de configurações da conta.

<img width="440" height="957" alt="Perfil" src="https://github.com/user-attachments/assets/f1e4bc79-067d-4f60-9ae4-4069f782a411" />

| **Aspecto**        | **Análise** |
|-------------------|-------------|
| Usabilidade       | Botões claros para ações principais: editar perfil e sair. |
| UX                | Uso de vermelho para ação destrutiva ajuda a prevenir erros. |
| Comunicabilidade  | Conteúdo visual reforça o contexto da seção de perfil. |
| Acessibilidade    | Hierarquia transmitida por cor e peso visual dos botões. |

Heurísticas de Nielsen

| Heurística Aplicada | Onde e Como se Manifesta |
| :--- | :--- |
| **3 – Controle e liberdade para o usuário** | **Opções Claras:** O usuário tem controle total sobre as ações relacionadas ao perfil (**EDITAR PERFIL** e **SAIR**). O botão "SAIR" (vermelho) oferece a liberdade de encerrar a sessão. |
| **4 – Consistência e padronização** | **Ações por Cor:** A cor roxa para **"EDITAR PERFIL"** (ação primária/positiva) e o vermelho para **"SAIR"** (ação destrutiva/negativa) mantêm um padrão de comunicação por cores. |
| **8 – Estética e design minimalista** | **Hierarquia de Informação:** O nome e o CPF do usuário estão em destaque. A tela é simples e sem elementos desnecessários, focada na gestão do perfil. |
