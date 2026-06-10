# Controle de Missão Espacial - Orbital Mission Control Platform 

## Descrição do Projeto
Este projeto consiste no desenvolvimento de uma solução integrada para o controle de missões espaciais, composta por um backend robusto e um aplicativo mobile funcional. O sistema visa gerenciar sensores, módulos, eventos operacionais e alertas críticos de uma missão em tempo real.

## Integrantes
* Geovana Pederneschi - 559092
* Thais Helena Ferreira Vieira - 552387

## Tecnologias Utilizadas

### Backend
* **Linguagem:** Java 
* **Framework:** Spring Boot 
* **Banco de Dados:** H2 Database (modo file) 

### Mobile
* **Framework:** React Native 
* **Linguagem:** TypeScript

## Funcionalidades

### API (Backend)
* Cadastro e consulta de sensores e módulos computacionais[cite.
* Gerenciamento de sistemas monitorados e eventos operacionais.
* Registro e monitoramento de alertas críticos.
* Persistência de dados utilizando H2 em modo.

### Aplicativo (Mobile)
* Integração com a API para envio de dados via requisições POST.
* Exibição detalhada de status da missão, leituras de sensores, alertas e registros operacionais.
* Navegação intuitiva entre telas.

## Como Executar
1. **Backend:** Clone o repositório, configure o ambiente Java/Spring Boot e inicie a aplicação para que o banco H2 seja gerado.
2. **Mobile:** Configure o ambiente React Native, instale as dependências e inicie o app, garantindo que o endereço da API esteja apontando corretamente para o servidor local.

---
