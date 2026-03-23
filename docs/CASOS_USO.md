# SGAA - Casos de Uso

## 1. Introdução

Este documento descreve os casos de uso do Sistema de Gestão de Abastecimento de Água (SGAA), utilizando diagramas UML e especificações textuais detalhadas. Os casos de uso representam as interações entre os atores (utilizadores) e o sistema, descrevendo as funcionalidades principais da plataforma.

---

## 2. Atores do Sistema

| Ator | Descrição | Perfil |
|------|-----------|--------|
| **SuperAdmin** | Utilizador com acesso total ao sistema, responsável pela gestão de administradores e configurações globais | Nível máximo de permissão |
| **Admin** | Utilizador responsável pela operação diária: gestão de clientes, vistorias, facturas e pagamentos | Gestor operacional |
| **Cliente** | Consumidor final de água, acede ao portal para consultar facturas e histórico | Utilizador final |
| **Sistema** | Ator secundário que representa serviços externos (envio de emails, mapas, etc.) | Serviços de infraestrutura |

---

## 3. Diagrama Geral de Casos de Uso

```
┌─────────────────────────────────────────────────────────────────────────────────────────────┐
│                                    SISTEMA SGAA                                              │
│                                                                                              │
│  ┌─────────────────┐     ┌─────────────────────────────────────────────────────────────┐    │
│  │   SuperAdmin    │     │                                                             │    │
│  │                 │     │  ┌─────────────────────────────────────────────────────┐    │    │
│  │  • Gerir Admins │────▶│  │                 CASOS DE USO                        │    │    │
│  │  • Ver Logs     │     │  │                                                     │    │    │
│  │  • Configurar   │     │  │  ┌─────────────────┐    ┌─────────────────────────┐ │    │    │
│  └─────────────────┘     │  │  │  Autenticação  │    │   Gestão de Clientes    │ │    │    │
│                          │  │  │                 │    │                         │ │    │    │
│  ┌─────────────────┐     │  │  │  • Login       │    │  • Cadastrar Cliente    │ │    │    │
│  │     Admin       │     │  │  │  • Logout      │    │  • Editar Cliente       │ │    │    │
│  │                 │────▶│  │  │  • Recuperar   │    │  • Buscar Cliente       │ │    │    │
│  │  • Gerir        │     │  │  │    Senha       │    │  • Ver Histórico        │ │    │    │
│  │    Clientes     │     │  │  └─────────────────┘    └─────────────────────────┘ │    │    │
│  │  • Realizar     │     │  │                                                      │    │    │
│  │    Vistorias    │     │  │  ┌─────────────────┐    ┌─────────────────────────┐ │    │    │
│  │  • Gerir        │     │  │  │   Vistorias    │    │      Facturação         │ │    │    │
│  │    Facturas     │     │  │  │                 │    │                         │ │    │    │
│  │  • Confirmar    │     │  │  │  • Registar    │    │  • Gerar Factura        │ │    │    │
│  │    Pagamentos   │     │  │  │    Leitura     │    │  • Visualizar Factura   │ │    │    │
│  │  • Publicar     │     │  │  │  • Calcular    │    │  • Baixar PDF           │ │    │    │
│  │    Comunicados  │     │  │  │    Consumo     │    │  • Ver Status           │ │    │    │
│  │  • Configurar   │     │  │  └─────────────────┘    └─────────────────────────┘ │    │    │
│  │    Taxas        │     │  │                                                      │    │    │
│  └─────────────────┘     │  │  ┌─────────────────┐    ┌─────────────────────────┐ │    │    │
│                          │  │  │   Pagamentos   │    │        Mapas            │ │    │    │
│  ┌─────────────────┐     │  │  │                 │    │                         │ │    │    │
│  │    Cliente      │     │  │  │  • Registar    │    │  • Visualizar Mapa      │ │    │    │
│  │                 │────▶│  │  │    Pagamento   │    │    Clientes             │ │    │    │
│  │  • Ver Facturas │     │  │  │  • Confirmar   │    │  • Traçar Rota          │ │    │    │
│  │  • Baixar PDF   │     │  │  │    Pagamento   │    │  • Marcar Visitado      │ │    │    │
│  │  • Ver Consumo  │     │  │  │  • Gerar       │    │  • Ver Mapa Secretaria  │ │    │    │
│  │  • Ver Mapa     │     │  │  │    Recibo      │    │                         │ │    │    │
│  │    Secretaria   │     │  │  └─────────────────┘    └─────────────────────────┘ │    │    │
│  └─────────────────┘     │  │                                                      │    │    │
│                          │  │  ┌─────────────────┐    ┌─────────────────────────┐ │    │    │
│                          │  │  │  Relatórios    │    │   Configurações         │ │    │    │
│  ┌─────────────────┐     │  │  │                 │    │                         │ │    │    │
│  │    Sistema      │     │  │  │  • Financeiro  │    │  • Gerir Taxas          │ │    │    │
│  │                 │────▶│  │  │  • Consumo     │    │  • Gerir Comunicados    │ │    │    │
│  │  • Enviar Email │     │  │  │  • Operacional │    │  • Configurar Sistema   │ │    │    │
│  │  • Processar    │     │  │  │  • Exportar    │    │  • Ver Logs             │ │    │    │
│  │    Rotas        │     │  │  └─────────────────┘    └─────────────────────────┘ │    │    │
│  └─────────────────┘     │  └─────────────────────────────────────────────────────┘    │    │
│                          │                                                             │    │
└─────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 4. Diagrama de Casos de Uso - Autenticação

```
┌─────────────────────────────────────────────────────────────────────┐
│                         UC - Autenticação                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   ┌─────────────┐                                                  │
│   │  Utilizador │                                                  │
│   │  (qualquer  │                                                  │
│   │   perfil)   │                                                  │
│   └──────┬──────┘                                                  │
│          │                                                         │
│          ▼                                                         │
│   ┌─────────────────────────────────────────────────────────────┐  │
│   │                                                             │  │
│   │  ┌─────────────────┐    ┌─────────────────────────────────┐ │  │
│   │  │    <<include>>  │    │                                 │ │  │
│   │  │   Validar       │◀───│         Fazer Login             │ │  │
│   │  │   Credenciais   │    │                                 │ │  │
│   │  └─────────────────┘    └───────────────┬─────────────────┘ │  │
│   │                                          │                   │  │
│   │                                          ▼                   │  │
│   │                              ┌─────────────────────────────┐ │  │
│   │                              │      <<extend>>             │ │  │
│   │                              │   Conta Inativa/Incorreta  │ │  │
│   │                              │   Exibir Mensagem de Erro  │ │  │
│   │                              └─────────────────────────────┘ │  │
│   │                                                             │  │
│   │  ┌─────────────────┐                                        │  │
│   │  │   Recuperar     │                                        │  │
│   │  │     Senha       │                                        │  │
│   │  └────────┬────────┘                                        │  │
│   │           │                                                  │  │
│   │           ▼                                                  │  │
│   │  ┌─────────────────────────────────────────────────────────┐│  │
│   │  │  <<include>>              <<include>>                   ││  │
│   │  │  Enviar Email             Validar Token                 ││  │
│   │  └─────────────────────────────────────────────────────────┘│  │
│   │                                                             │  │
│   └─────────────────────────────────────────────────────────────┘  │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 5. Diagrama de Casos de Uso - Gestão de Clientes e Vistorias

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                      UC - Gestão de Clientes e Vistorias                            │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│   ┌─────────────┐                              ┌─────────────┐                      │
│   │   Admin     │                              │   Cliente   │                      │
│   └──────┬──────┘                              └──────┬──────┘                      │
│          │                                            │                             │
│          ▼                                            ▼                             │
│   ┌─────────────────────────────────────────────────────────────────────────────┐   │
│   │                                                                             │   │
│   │  ┌─────────────────────────┐          ┌─────────────────────────────────┐   │   │
│   │  │     Gestão de Clientes  │          │        Portal do Cliente       │   │   │
│   │  │                         │          │                                 │   │   │
│   │  │  • Cadastrar Cliente    │          │  • Visualizar Facturas         │   │   │
│   │  │  • Editar Cliente       │          │  • Baixar PDF Factura          │   │   │
│   │  │  • Buscar Cliente       │          │  • Visualizar Consumo          │   │   │
│   │  │  • Ver Histórico        │          │  • Visualizar Mapa Secretaria  │   │   │
│   │  │  • Marcar Localização   │          │                                 │   │   │
│   │  └─────────────────────────┘          └─────────────────────────────────┘   │   │
│   │              │                                                                   │
│   │              ▼                                                                   │
│   │  ┌─────────────────────────────────────────────────────────────────────────┐   │
│   │  │                         Vistorias                                      │   │
│   │  │                                                                         │   │
│   │  │  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────────┐ │   │
│   │  │  │  Selecionar     │───▶│   Registrar     │───▶│   Calcular          │ │   │
│   │  │  │  Cliente        │    │   Leitura       │    │   Consumo           │ │   │
│   │  │  └─────────────────┘    └─────────────────┘    └─────────────────────┘ │   │
│   │  │         │                       │                       │               │   │
│   │  │         ▼                       ▼                       ▼               │   │
│   │  │  ┌─────────────────────────────────────────────────────────────────┐   │   │
│   │  │  │                      <<extend>>                                 │   │   │
│   │  │  │                     Atualizar Mapa                              │   │   │
│   │  │  │          Marcador muda de vermelho para verde                  │   │   │
│   │  │  └─────────────────────────────────────────────────────────────────┘   │   │
│   │  │                              │                                          │   │
│   │  │                              ▼                                          │   │
│   │  │  ┌─────────────────────────────────────────────────────────────────┐   │   │
│   │  │  │                      <<include>>                                │   │   │
│   │  │  │                     Gerar Factura                               │   │   │
│   │  │  │           (após confirmação da vistoria)                        │   │   │
│   │  │  └─────────────────────────────────────────────────────────────────┘   │   │
│   │  └─────────────────────────────────────────────────────────────────────────┘   │
│   │                                                                                 │
│   └─────────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 6. Diagrama de Casos de Uso - Facturação e Pagamentos

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                       UC - Facturação e Pagamentos                                  │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│   ┌─────────────┐                              ┌─────────────┐                      │
│   │   Admin     │                              │   Cliente   │                      │
│   └──────┬──────┘                              └──────┬──────┘                      │
│          │                                            │                             │
│          ▼                                            ▼                             │
│   ┌─────────────────────────────────────────────────────────────────────────────┐   │
│   │                                                                             │   │
│   │  ┌─────────────────────────────────────────────────────────────────────┐   │   │
│   │  │                         Facturação                                   │   │   │
│   │  │                                                                      │   │   │
│   │  │  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐   │   │   │
│   │  │  │   Gerar         │───▶│   Aplicar       │───▶│   Emitir        │   │   │
│   │  │  │   Factura       │    │   Taxas/Multas  │    │   PDF           │   │   │
│   │  │  └─────────────────┘    └─────────────────┘    └─────────────────┘   │   │   │
│   │  │                                                                      │   │   │
│   │  │  ┌─────────────────────────────────────────────────────────────────┐   │   │
│   │  │  │                      <<extend>>                                 │   │   │
│   │  │  │                     Enviar Email                               │   │   │
│   │  │  │              Notificação de factura gerada                     │   │   │
│   │  │  └─────────────────────────────────────────────────────────────────┘   │   │
│   │  └─────────────────────────────────────────────────────────────────────┘   │   │
│   │                                                                             │   │
│   │  ┌─────────────────────────────────────────────────────────────────────┐   │   │
│   │  │                         Pagamentos                                   │   │   │
│   │  │                                                                      │   │   │
│   │  │  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐   │   │   │
│   │  │  │   Registar      │───▶│   Confirmar     │───▶│   Gerar         │   │   │
│   │  │  │   Pagamento     │    │   Pagamento     │    │   Recibo        │   │   │
│   │  │  └─────────────────┘    └─────────────────┘    └─────────────────┘   │   │   │
│   │  │         │                       │                       │               │   │   │
│   │  │         ▼                       ▼                       ▼               │   │   │
│   │  │  ┌─────────────────────────────────────────────────────────────────┐   │   │
│   │  │  │                      <<extend>>                                 │   │   │
│   │  │  │               Actualizar Status da Factura                     │   │   │
│   │  │  │           (pendente → pago / parcial)                          │   │   │
│   │  │  └─────────────────────────────────────────────────────────────────┘   │   │
│   │  └─────────────────────────────────────────────────────────────────────┘   │   │
│   │                                                                             │   │
│   └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 7. Diagrama de Casos de Uso - Mapas e Rotas

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                         UC - Mapas e Rotas                                          │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│   ┌─────────────┐                              ┌─────────────┐                      │
│   │   Admin     │                              │   Cliente   │                      │
│   └──────┬──────┘                              └──────┬──────┘                      │
│          │                                            │                             │
│          ▼                                            ▼                             │
│   ┌─────────────────────────────────────────────────────────────────────────────┐   │
│   │                                                                             │   │
│   │  ┌─────────────────────────────────────────────────────────────────────┐   │   │
│   │  │                    Mapas para Admin                                  │   │   │
│   │  │                                                                      │   │   │
│   │  │  ┌─────────────────────────────────────────────────────────────────┐ │   │   │
│   │  │  │                      Visualizar Mapa                            │ │   │   │
│   │  │  │                                                                  │ │   │   │
│   │  │  │  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐         │ │   │   │
│   │  │  │  │  Marcadores │    │   Filtros   │    │   Pop-up    │         │ │   │   │
│   │  │  │  │  (Vermelho/ │    │  (Bairro,   │    │  Informação │         │ │   │   │
│   │  │  │  │   Verde)    │    │   Status)   │    │             │         │ │   │   │
│   │  │  │  └─────────────┘    └─────────────┘    └─────────────┘         │ │   │   │
│   │  │  └─────────────────────────────────────────────────────────────────┘ │   │   │
│   │  │                                                                      │   │   │
│   │  │  ┌─────────────────────────────────────────────────────────────────┐ │   │   │
│   │  │  │                      Traçar Rota Optimizada                     │ │   │   │
│   │  │  │                                                                  │ │   │   │
│   │  │  │  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐         │ │   │   │
│   │  │  │  │  Calcular   │───▶│  Ordem de   │───▶│  Exibir     │         │ │   │   │
│   │  │  │  │  Rotas      │    │  Visita     │    │  Rota no    │         │ │   │   │
│   │  │  │  │             │    │             │    │  Mapa       │         │ │   │   │
│   │  │  │  └─────────────┘    └─────────────┘    └─────────────┘         │ │   │   │
│   │  │  └─────────────────────────────────────────────────────────────────┘ │   │   │
│   │  └─────────────────────────────────────────────────────────────────────┘   │   │
│   │                                                                             │   │
│   │  ┌─────────────────────────────────────────────────────────────────────┐   │   │
│   │  │                   Mapas para Cliente                                 │   │   │
│   │  │                                                                      │   │   │
│   │  │  ┌─────────────────────────────────────────────────────────────────┐ │   │   │
│   │  │  │                  Visualizar Secretaria                          │ │   │   │
│   │  │  │                                                                  │ │   │   │
│   │  │  │  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐         │ │   │   │
│   │  │  │  │  Detectar   │───▶│  Traçar     │───▶│  Exibir     │         │ │   │   │
│   │  │  │  │  Localização│    │  Rota       │    │  Instruções │         │ │   │   │
│   │  │  │  │  Actual     │    │  (vermelho) │    │  Passo-a-   │         │ │   │   │
│   │  │  │  │             │    │             │    │  Passo      │         │ │   │   │
│   │  │  │  └─────────────┘    └─────────────┘    └─────────────┘         │ │   │   │
│   │  │  └─────────────────────────────────────────────────────────────────┘ │   │   │
│   │  └─────────────────────────────────────────────────────────────────────┘   │   │
│   │                                                                             │   │
│   └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 8. Especificações Textuais dos Casos de Uso

### 8.1 UC01 - Realizar Login

| Campo | Descrição |
|-------|-----------|
| **Identificador** | UC01 |
| **Nome** | Realizar Login |
| **Ator Principal** | Utilizador (SuperAdmin, Admin, Cliente) |
| **Pré-condições** | Utilizador possui credenciais válidas (email/telefone e senha) |
| **Pós-condições** | Utilizador autenticado, token gerado, redirecionado para dashboard conforme perfil |

**Fluxo Principal (Cenário de Sucesso)**

1. O utilizador acede à página de login do sistema.
2. O sistema exibe o formulário com campos: login (email ou telefone) e senha.
3. O utilizador preenche os campos com suas credenciais.
4. O sistema valida o formato do email/telefone e senha não vazia.
5. O sistema verifica se o login corresponde a um email ou telefone cadastrado.
6. O sistema verifica a senha utilizando hash bcrypt.
7. O sistema verifica se a conta está activa (is_active = true).
8. O sistema gera um token de acesso via Laravel Sanctum.
9. O sistema regista o evento de login no log de auditoria (IP, data, utilizador).
10. O sistema redireciona o utilizador para o dashboard correspondente ao seu perfil.
    - SuperAdmin → /admin/dashboard
    - Admin → /admin/dashboard
    - Cliente → /client/dashboard

**Fluxos Alternativos**

| Fluxo | Descrição |
|-------|-----------|
| **3a. Campos vazios** | Sistema exibe mensagem "Preencha todos os campos" |
| **5a. Login não encontrado** | Sistema exibe mensagem "Credenciais inválidas" |
| **6a. Senha incorreta** | Sistema exibe mensagem "Credenciais inválidas" |
| **7a. Conta inactiva** | Sistema exibe mensagem "Sua conta está inactiva. Contacte o administrador." |
| **9a. Múltiplas tentativas falhas** | Após 5 tentativas falhas, sistema bloqueia login por 30 minutos |

**Regras de Negócio**

| Regra | Descrição |
|-------|-----------|
| RN01 | O campo login aceita formato de email (usuario@dominio.com) ou número de telefone (+258 84 000 0000) |
| RN02 | A senha deve ter no mínimo 8 caracteres |
| RN03 | O token gerado tem validade de 24 horas |
| RN04 | O sistema mantém registo de todas as tentativas de login (sucesso e falha) |

---

### 8.2 UC02 - Realizar Vistoria

| Campo | Descrição |
|-------|-----------|
| **Identificador** | UC02 |
| **Nome** | Realizar Vistoria |
| **Ator Principal** | Admin |
| **Pré-condições** | Admin autenticado, cliente cadastrado, contador associado ao cliente |
| **Pós-condições** | Vistoria registada, consumo calculado, factura gerada, marcador do mapa actualizado para verde |

**Fluxo Principal (Cenário de Sucesso)**

1. O Admin acede à página de vistorias.
2. O sistema exibe um mapa com marcadores de clientes (vermelho = não visitados, verde = visitados).
3. O Admin selecciona um cliente por busca textual ou clicando no marcador vermelho no mapa.
4. O sistema exibe um formulário com os dados do cliente e a última leitura registada.
5. O Admin regista a nova leitura do contador.
6. O sistema calcula automaticamente o consumo: (leitura actual - leitura anterior).
7. O sistema calcula o valor da factura aplicando as taxas configuradas:
   - Consumo ≤ mínimo → taxa mínima
   - Consumo > mínimo → taxa mínima + (excedente × taxa adicional)
8. O sistema exibe o valor calculado para confirmação.
9. O Admin adiciona observações (opcional) e fotos da vistoria.
10. O Admin confirma a vistoria.
11. O sistema regista a vistoria e associa as fotos.
12. O sistema gera automaticamente a factura com número sequencial.
13. O sistema actualiza a última leitura do contador.
14. O sistema altera a cor do marcador de vermelho para verde.
15. O sistema regista a data/hora da última visita.

**Fluxos Alternativos**

| Fluxo | Descrição |
|-------|-----------|
| **4a. Cliente não encontrado** | Sistema exibe mensagem "Cliente não encontrado" |
| **6a. Leitura inferior à anterior** | Sistema exibe aviso: "Leitura actual não pode ser inferior à anterior" e solicita confirmação do Admin |
| **8a. Valor calculado inválido** | Sistema exibe erro e permite que Admin revise as taxas configuradas |
| **12a. Falha na geração da factura** | Sistema mantém vistoria registada e agenda geração da factura para processamento em fila |

**Regras de Negócio**

| Regra | Descrição |
|-------|-----------|
| RN05 | A leitura actual não pode ser inferior à leitura anterior, exceto em caso de substituição do contador |
| RN06 | Cada vistoria gera uma factura obrigatoriamente |
| RN07 | Fotos da vistoria são armazenadas com tamanho máximo de 2MB por arquivo |
| RN08 | O status do marcador só é alterado após confirmação da vistoria |

---

### 8.3 UC03 - Gerar Factura

| Campo | Descrição |
|-------|-----------|
| **Identificador** | UC03 |
| **Nome** | Gerar Factura |
| **Ator Principal** | Sistema (automático após vistoria) |
| **Atores Secundários** | Admin, Cliente |
| **Pré-condições** | Vistoria registada e confirmada, taxas configuradas no sistema |
| **Pós-condições** | Factura gerada, notificação enviada ao cliente, factura disponível para download |

**Fluxo Principal (Cenário de Sucesso)**

1. O sistema recebe a confirmação da vistoria.
2. O sistema obtém a leitura anterior e actual.
3. O sistema calcula o consumo em metros cúbicos.
4. O sistema consulta as taxas activas configuradas pelo Admin.
5. O sistema calcula o valor base:
   - Se consumo ≤ consumo mínimo: valor = taxa mínima
   - Se consumo > consumo mínimo: valor = taxa mínima + (consumo excedente × taxa adicional)
6. O sistema verifica se há multas aplicáveis:
   - Se houver facturas anteriores vencidas, aplica percentagem de multa configurada
7. O sistema gera número de factura sequencial único (INV-AAAAAMMDD-XXXX).
8. O sistema regista a factura no banco de dados com status "pendente".
9. O sistema associa a factura à vistoria e ao cliente.
10. O sistema envia notificação por email ao cliente com a factura anexada.
11. O sistema regista a emissão no log de auditoria.

**Fluxos Alternativos**

| Fluxo | Descrição |
|-------|-----------|
| **4a. Taxas não configuradas** | Sistema exibe erro para o Admin: "Configure as taxas antes de realizar vistorias" |
| **6a. Cliente sem email cadastrado** | Sistema gera factura normalmente, mas não envia email; cliente deve aceder ao portal |
| **8a. Número de factura duplicado** | Sistema gera novo número sequencial |

**Regras de Negócio**

| Regra | Descrição |
|-------|-----------|
| RN09 | O número de factura segue o formato: INV + ano + mês + dia + sequencial de 4 dígitos |
| RN10 | A factura tem vencimento em 15 dias após a data de emissão (configurável) |
| RN11 | A multa é calculada sobre o valor total da factura, com percentagem configurável |
| RN12 | Facturas com pagamento confirmado não podem ser alteradas ou canceladas |

**Pós-condições Detalhadas**

| Item | Descrição |
|------|-----------|
| Dados registados | invoice_number, client_id, previous_reading, current_reading, consumption, minimum_fee, additional_fee, late_fee, total_amount, due_date, status, issued_by |
| Notificações | Email enviado com PDF anexado, notificação no portal do cliente |
| Disponibilidade | Factura disponível para download em PDF via portal do cliente |

---

### 8.4 UC04 - Confirmar Pagamento

| Campo | Descrição |
|-------|-----------|
| **Identificador** | UC04 |
| **Nome** | Confirmar Pagamento |
| **Ator Principal** | Admin |
| **Atores Secundários** | Cliente, Sistema |
| **Pré-condições** | Factura gerada e com status "pendente" ou "parcial", pagamento realizado pelo cliente |
| **Pós-condições** | Pagamento confirmado, status da factura actualizado, recibo emitido |

**Fluxo Principal (Cenário de Sucesso)**

1. O Admin acede à lista de pagamentos pendentes.
2. O sistema exibe todas as facturas com status "pendente" ou "parcial".
3. O Admin localiza o pagamento correspondente (por número de factura ou nome do cliente).
4. O Admin selecciona a factura.
5. O sistema exibe detalhes da factura: valor total, valor já pago (se houver), saldo.
6. O Admin informa o valor recebido e o método de pagamento (dinheiro, transferência, dinheiro móvel, etc.).
7. O Admin insere o número de referência ou comprovativo (opcional).
8. O sistema valida se o valor informado não excede o saldo da factura.
9. O Admin confirma o pagamento.
10. O sistema regista o pagamento com data e hora.
11. O sistema regista o nome do operário que realizou a confirmação.
12. O sistema actualiza o status da factura:
    - Se valor pago = saldo total → status = "pago"
    - Se valor pago < saldo total → status = "parcial"
13. O sistema gera um recibo com número de confirmação único.
14. O sistema disponibiliza o recibo para download em PDF.

**Fluxos Alternativos**

| Fluxo | Descrição |
|-------|-----------|
| **3a. Factura não encontrada** | Sistema exibe mensagem "Factura não encontrada" |
| **8a. Valor excede saldo** | Sistema exibe erro: "Valor informado excede o saldo da factura" e solicita correcção |
| **10a. Falha no registo** | Sistema mantém o registo em fila para processamento posterior |

**Regras de Negócio**

| Regra | Descrição |
|-------|-----------|
| RN13 | Um pagamento pode ser parcial, mantendo o saldo para pagamentos futuros |
| RN14 | Cada pagamento gera um recibo com número de confirmação único |
| RN15 | Pagamentos só podem ser confirmados por utilizadores com perfil Admin |
| RN16 | O recibo deve conter: dados da empresa, dados do cliente, valor pago, data, método, operário responsável |

**Pós-condições Detalhadas**

| Item | Descrição |
|------|-----------|
| Dados registados | payment_id, client_id, invoice_id, amount, payment_method, reference, status, payment_date, confirmed_by, confirmed_at, confirmation_code |
| Documentos gerados | Recibo em PDF com layout padronizado |
| Notificações | Cliente notificado via portal sobre confirmação do pagamento |

---

### 8.5 UC05 - Traçar Rota Optimizada

| Campo | Descrição |
|-------|-----------|
| **Identificador** | UC05 |
| **Nome** | Traçar Rota Optimizada |
| **Ator Principal** | Admin |
| **Pré-condições** | Admin autenticado, clientes georreferenciados no mapa, existem clientes com marcadores vermelhos (não visitados) |
| **Pós-condições** | Rota optimizada calculada e exibida no mapa com distância total e tempo estimado |

**Fluxo Principal (Cenário de Sucesso)**

1. O Admin acede ao mapa de clientes.
2. O sistema exibe todos os clientes com marcadores coloridos.
3. O Admin activa a opção "Calcular Rotas" no menu.
4. O sistema identifica todos os clientes com marcadores vermelhos (não visitados no período).
5. O sistema obtém a localização actual do Admin (opcional) ou utiliza a primeira localização como ponto de partida.
6. O sistema aplica algoritmo de otimização (vizinho mais próximo) para ordenar os pontos de visita.
7. O sistema calcula a distância total em quilómetros.
8. O sistema calcula o tempo estimado de percurso baseado em velocidade média (20 km/h).
9. O sistema traça a rota no mapa, conectando os pontos na ordem optimizada.
10. O sistema exibe uma lista ordenada dos clientes a visitar.
11. O Admin pode salvar a rota para referência futura.

**Fluxos Alternativos**

| Fluxo | Descrição |
|-------|-----------|
| **4a. Nenhum cliente não visitado** | Sistema exibe mensagem "Não há clientes pendentes para visita" |
| **5a. Localização do Admin não disponível** | Sistema utiliza a primeira localização da lista como ponto de partida |
| **7a. Falha no serviço de rotas (OSRM)** | Sistema utiliza distância em linha reta como fallback |

**Regras de Negócio**

| Regra | Descrição |
|-------|-----------|
| RN17 | A rota considera apenas clientes com marcadores vermelhos (não visitados no período) |
| RN18 | O algoritmo utilizado é o "Vizinho Mais Próximo" (Nearest Neighbor) |
| RN19 | O tempo estimado é calculado considerando velocidade média de 20 km/h em zona urbana |
| RN20 | O Admin pode salvar até 10 rotas personalizadas |

**Pós-condições Detalhadas**

| Item | Descrição |
|------|-----------|
| Rota calculada | Ordem de visita, distância total, tempo estimado, geometria da rota |
| Visualização | Linha colorida no mapa (azul/ciano) conectando os pontos |
| Informações exibidas | Lista ordenada com nomes dos clientes, endereços e distância entre pontos |

---

## 9. Resumo dos Casos de Uso

| ID | Nome | Ator Principal | Descrição |
|----|------|----------------|-----------|
| UC01 | Realizar Login | Utilizador | Autenticação no sistema com email/telefone e senha |
| UC02 | Realizar Vistoria | Admin | Registo de leitura de contador com cálculo de consumo |
| UC03 | Gerar Factura | Sistema | Geração automática de factura após vistoria |
| UC04 | Confirmar Pagamento | Admin | Registo e confirmação de pagamentos com emissão de recibo |
| UC05 | Traçar Rota Optimizada | Admin | Cálculo de rota otimizada para vistorias |

---
