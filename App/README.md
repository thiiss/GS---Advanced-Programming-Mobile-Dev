# Space Connect — Orbital Mission Control Platform

**Global Solution 2026 — FIAP | Turma 3ECR**

---

## Integrantes

| Nome Completo | RM |
|---|---|
| | |
| | |
| | |

---

## Sobre o Projeto

Plataforma mobile de controle de missão orbital que monitora sensores críticos instalados nos módulos da estação espacial, registra leituras operacionais em tempo real e gera alertas quando parâmetros excedem limites seguros.

O app se integra com uma API REST desenvolvida em Spring Boot que persiste os dados no banco de dados.

---

## Pré-requisitos

- Node.js 18+
- Backend Spring Boot rodando em `http://localhost:8080`
- Endpoints necessários:
  - `GET /sensores` e `POST /sensores`
  - `GET /leituras` e `POST /leituras`
  - `GET /alertas` e `PUT /alertas/{id}`

---

## Como Rodar

### 1. Criar o projeto (apenas na primeira vez)

```bash
npx create-expo-app@latest . --template blank-typescript
```

### 2. Instalar dependências

```bash
npm install @react-navigation/native @react-navigation/stack
npx expo install react-native-screens react-native-safe-area-context react-native-gesture-handler react-native-reanimated react-dom react-native-web @expo/metro-runtime
npm install axios
```

### 3. Iniciar o servidor de desenvolvimento

```bash
npx expo start --web
```

O app abrirá no navegador em `http://localhost:8081` (ou porta disponível).

### 4. Simular tela de celular no navegador

1. Pressione `F12` para abrir o DevTools
2. Pressione `Ctrl + Shift + M` para ativar o modo responsivo
3. Selecione **iPhone 12** no seletor de dispositivos

---

## Aviso sobre Expo Go

Este projeto utiliza **Expo SDK 56** e **React Navigation Stack Navigator**, que **não são compatíveis com o Expo Go**.

Rode **apenas via navegador web** com `npx expo start --web`.

---

## Telas e Fluxo de Navegação

```
ListaSensoresScreen (tela inicial)
├── [botão] Novo Sensor → CadastroSensorScreen
│                              └── [salvar] → volta para ListaSensores (recarrega)
├── [botão] Ver Alertas → ListaAlertasScreen
│                              └── [card] → DetalheAlertaScreen
│                                              └── [botão] Marcar Resolvido → volta
├── [botão] Ver Leituras → ListaLeiturasScreen
│                              └── [botão] Selecionar Sensor → ListaSensores
└── [card sensor] → CadastroLeituraScreen
                         └── [salvar] → volta para ListaSensores
```

### Descrição das telas

| Tela | Função |
|---|---|
| **ListaSensoresScreen** | Lista todos os sensores cadastrados. Permite navegar para cadastro de novo sensor, ver alertas e ver leituras. Toque em um sensor para registrar uma leitura. |
| **CadastroSensorScreen** | Formulário para cadastrar novo sensor com nome, tipo, localização e status ativo/inativo. |
| **ListaLeiturasScreen** | Histórico de todas as leituras operacionais registradas com valor, unidade, status e timestamp. |
| **CadastroLeituraScreen** | Formulário para registrar uma leitura de um sensor específico (valor, unidade, status, observações). |
| **ListaAlertasScreen** | Lista todos os alertas críticos, ordenados com os ativos primeiro. |
| **DetalheAlertaScreen** | Exibe detalhes completos de um alerta e permite marcá-lo como resolvido. |

---

## Integração com a API

O arquivo `src/services/api.ts` configura o cliente Axios apontando para `http://localhost:8080`.

Todas as telas fazem chamadas HTTP usando `async/await` com `try/catch`. Em caso de erro de rede, a mensagem é exibida na tela.

**Exemplo de fluxo completo:**
1. `ListaSensoresScreen` busca `GET /sensores` ao montar
2. Usuário toca em um sensor → navega para `CadastroLeituraScreen` com `sensorId` e `sensorNome`
3. Usuário preenche o formulário e salva → `POST /leituras` → volta para `ListaSensoresScreen`

---

## Tecnologias

| Tecnologia | Uso |
|---|---|
| React Native + Expo | Framework mobile |
| TypeScript | Tipagem estática |
| Expo SDK 56 | Plataforma de build |
| React Navigation (Stack) | Navegação entre telas |
| Axios | Chamadas HTTP para a API REST |
| React Native Web | Execução no navegador |
| StyleSheet.create | Estilização dos componentes |
