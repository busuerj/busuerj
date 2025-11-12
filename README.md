# BusUERJ: Plataforma de Reserva de Assentos para Ônibus Universitários

> [https://busuerj.online](https://busuerj.online)

## O que é o BusUERJ?

O **BusUERJ** é uma **plataforma on-premise** desenvolvida para o **gerenciamento de reservas de assentos em viagens rodoviárias de ônibus universitários**.  

O projeto nasceu da **necessidade de otimizar a organização das viagens intermunicipais** da **UERJ – campus Nova Friburgo**, aliando a resolução de um problema real à **exploração de um tema para o Trabalho de Conclusão de Curso em Engenharia de Computação**.


## Principais Funcionalidades

| Funcionalidade | Status |
|----------------|---------|
| Autenticação e gestão de usuários com base em e-mails institucionais ou domínios previamente cadastrados | Feito |
| Gerenciamento completo de viagens, incluindo locais, rotas, motoristas e veículos | Em melhoria |
| Agendamento automático de viagens recorrentes, reduzindo tarefas manuais | Feito |
| Notificações via WhatsApp sobre status de viagens, reservas e cancelamentos | Feito |
| Validação facial para embarque, facilitando a identificação dos passageiros | Em desenvolvimento |
| Envio automatizado de alertas, passagens e informações importantes por e-mail | Backlog |
| Controle de reservas e assentos disponíveis, prevenindo overbooking | Feito |
| Rastreamento em tempo real da localização dos ônibus | Backlog |
| Exibição da previsão do tempo no destino da viagem | Backlog |

## Arquitetura
![diagram](diagram.svg)


```mermaid
---
config:
  layout: elk
  theme: redux-dark
  look: neo
---
flowchart TB
 subgraph s1["Facial Recognition"]
        H["FACIAL RECOGNITION (SERVER)"]
        I["FACIAL RECOGNITION (POSTGRES)"]
  end
 subgraph s2["Evolution"]
        J["EVOLUTION API (SERVER)"]
        K["EVOLUTION API (POSTGRES)"]
        L["EVOLUTION API (REDIS)"]
  end
    B["NGINX (REVERSE PROXY)"] --> C["PORTAINER"] & D["BUSUERJ (FRONTEND)"] & E["BUSUERJ (CORE)"] & J
    D --> E
    E --> F["BUSUERJ (REDIS)"] & G["BUSUERJ (POSTGRES)"] & J & H
    H --> I
    J --> K & L
    n1[" "] -- "https://busuerj.online" --> B
    n1@{ icon: "aws:res-internet", pos: "b", h: 100}
    style n1 stroke:#FFFFFF
    style s2 fill:transparent,stroke:#FFFFFF,color:#FFFFFF
    style s1 fill:transparent
```

## Stack de desenvolvimento
[![My Skills](https://skillicons.dev/icons?i=nodejs,typescript,postgres,redis,docker,flutter,dart,nginx,python,fastapi)](https://skillicons.dev)


