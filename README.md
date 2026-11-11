# Miltinho Manager v1.0
**Startup TechVision · Challenge 2º Bimestre**

Sistema de gestão de pedidos e produtos para o Bar e Restaurante Miltinho.

---

## Tecnologias

| Camada | Tecnologia |
|---|---|
| Linguagem | Java 17 |
| Framework | Spring Boot 3.2 |
| Persistência | Spring Data JPA + Hibernate |
| Banco de dados | H2 (arquivo em `./data/miltinhodb`) |
| Interface gráfica | Java Swing |
| Build | Maven 3.6+ |
| IDE recomendada | NetBeans 17 / IntelliJ IDEA |

---

## Como executar

### Pré-requisitos
- Java 17 ou superior
- Maven 3.6+

### 1. Clonar / descompactar o projeto
```bash
unzip miltinho-manager.zip
cd miltinho-manager
```

### 2. Compilar e rodar
```bash
mvn spring-boot:run
```

A janela de **Login** abrirá automaticamente.

**Credenciais padrão:**
| Login | Senha |
|---|---|
| admin | admin123 |
| miltinho | miltinho |

> O banco H2 é criado automaticamente em `./data/miltinhodb.mv.db` na primeira execução,
> com produtos e pedidos de exemplo já inseridos.

### 3. Console H2 (opcional)
Enquanto o sistema estiver rodando, acesse:
```
http://localhost:8080/h2-console
JDBC URL: jdbc:h2:file:./data/miltinhodb
Usuário: sa | Senha: (em branco)
```

---

## Estrutura do projeto

```
miltinho-manager/
├── pom.xml
└── src/
    ├── main/
    │   ├── java/com/miltinho/manager/
    │   │   ├── MiltinhoApp.java          ← ponto de entrada Spring Boot
    │   │   ├── model/
    │   │   │   ├── Produto.java          ← entidade JPA
    │   │   │   ├── Pedido.java           ← entidade JPA (enum Status)
    │   │   │   └── Usuario.java          ← entidade JPA
    │   │   ├── repository/
    │   │   │   ├── ProdutoRepository.java
    │   │   │   ├── PedidoRepository.java
    │   │   │   └── UsuarioRepository.java
    │   │   ├── service/
    │   │   │   ├── ProdutoService.java
    │   │   │   ├── PedidoService.java
    │   │   │   └── UsuarioService.java
    │   │   ├── config/
    │   │   │   └── DataInitializer.java  ← popula banco na 1ª execução
    │   │   └── ui/                       ← telas Swing
    │   │       ├── UIEstilo.java         ← paleta de cores e fábrica de componentes
    │   │       ├── LoginFrame.java       ← Tela 1: Login
    │   │       ├── MenuFrame.java        ← Tela 2: Menu Principal
    │   │       ├── ProdutoFrame.java     ← Tela 3: Cadastro de Produtos
    │   │       ├── PedidoFrame.java      ← Tela 4: Cadastro de Pedidos
    │   │       ├── ConsultaPedidoFrame.java ← Tela 5: Consulta e Gestão
    │   │       ├── RelatorioFrame.java   ← Tela 6: Relatórios
    │   │       └── SobreFrame.java       ← Tela 7: Sobre
    │   └── resources/
    │       └── application.properties
    └── test/
        └── java/com/miltinho/manager/
            └── MiltinhoAppTests.java     ← testes com H2 em memória
```

---

## Funcionalidades

- **Login** com autenticação via banco H2
- **Cadastro de Produtos** — criar, editar, excluir, listar
- **Cadastro de Pedidos** — associar cliente + produto + quantidade + data
- **Consulta e Gestão** — buscar por cliente ou status, atualizar status, excluir
- **Relatórios** — produto mais pedido, estoque crítico, total de pedidos e faturamento do mês
- **Sobre** — informações sobre a startup e o sistema

---

## Executar testes
```bash
mvn test
```
Os testes rodam com H2 em memória, sem afetar o banco de dados de produção.

---

## Integrantes
Kauã Davi · Gustavo Gonsaga · Roger Miguel — TechVision, 2026
