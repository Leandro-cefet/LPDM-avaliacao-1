# LPDM Avaliação 1 — Cartão de Perfil Profissional

## 1. Nome do projeto e descrição

**Nome do projeto:** Cartão de Perfil Profissional

Este projeto consiste em um aplicativo Android nativo desenvolvido em Kotlin utilizando Jetpack Compose. O aplicativo funciona como um cartão de perfil profissional digital, apresentando em uma única tela as principais informações de um profissional.

A tela apresenta uma imagem de perfil, uma saudação em destaque, o nome completo do profissional, seu cargo, uma breve descrição na seção "Sobre" e informações de contato.

O aplicativo foi desenvolvido como parte da atividade de avaliação da disciplina de LPDM, utilizando conceitos de desenvolvimento de interfaces Android com Jetpack Compose, organização de layouts, componentes visuais, ícones do Material Icons e funções `@Composable` reutilizáveis.

O perfil apresentado no aplicativo utiliza dados fictícios para representar um profissional da área de desenvolvimento Android.

---

## 2. Tecnologias utilizadas

As principais tecnologias utilizadas no desenvolvimento do projeto foram:

* **Kotlin** — linguagem de programação utilizada no desenvolvimento do aplicativo.
* **Jetpack Compose** — toolkit utilizado para criação da interface gráfica de forma declarativa.
* **Material 3** — componentes e recursos visuais utilizados na interface.
* **Material Icons** — biblioteca utilizada para os ícones das informações de contato.
* **Android SDK** — conjunto de ferramentas utilizado para desenvolvimento Android.
* **Android Studio** — IDE utilizada para desenvolvimento, edição, compilação e execução do projeto.
* **Gradle** — sistema utilizado para gerenciamento da compilação e das dependências do projeto.

**IDE utilizada:** Android Studio, Versão: 2026.1.4.

---

## 3. Como compilar e executar o projeto

### 3.1 Clonar o repositório

Primeiramente, é necessário clonar o repositório do projeto utilizando o Git.

No terminal, execute:

```bash
git clone https://github.com/Leandro-cefet/LPDM-avaliacao-1.git
```

Depois, entre na pasta do projeto:

```bash
cd LPDM-avaliacao-1
```

### 3.2 Abrir o projeto no Android Studio

1. Abra o **Android Studio**.
2. Selecione a opção para abrir um projeto existente.
3. Localize a pasta `LPDM-avaliacao-1`.
4. Aguarde o Android Studio realizar a sincronização do projeto com o Gradle.
5. Aguarde o download das dependências necessárias, caso seja solicitado.

### 3.3 Preparar o emulador

1. Abra o **Device Manager** do Android Studio.
2. Crie ou selecione um dispositivo virtual Android.
3. Inicie o emulador.
4. Aguarde o carregamento completo do sistema Android.

### 3.4 Executar o aplicativo

Com o projeto aberto e o emulador em execução:

1. Selecione o dispositivo virtual no Android Studio.
2. Clique no botão **Run ▶**.
3. Aguarde a compilação do projeto.
4. O aplicativo será instalado e executado automaticamente no emulador.

Também é possível executar o projeto pelo terminal, utilizando o Gradle:

```bash
./gradlew assembleDebug
```

Para instalar e executar o aplicativo em um dispositivo conectado, pode-se utilizar o Android Studio ou o `adb`.

---

## 4. Estrutura e descrição dos arquivos e Composable Functions

### 4.1 `MainActivity.kt`

O arquivo `MainActivity.kt` contém a Activity principal do aplicativo.

A classe `MainActivity` herda de `ComponentActivity` e possui o método `onCreate()`, responsável por iniciar a interface do aplicativo através do `setContent`.

Dentro do `setContent`, a função `ProfileCard()` é chamada para construir a tela principal.

Trecho principal:

```kotlin
setContent {
    ProfileCard()
}
```

### 4.2 `MainActivity`

A classe `MainActivity` é responsável por ser o ponto de entrada da aplicação Android.

Sua principal responsabilidade é inicializar a Activity e carregar a interface desenvolvida com Jetpack Compose.

---

### 4.3 `ProfileCard()`

A função `ProfileCard()` é o principal `Composable` da aplicação.

Ela é responsável por construir toda a tela do cartão de perfil profissional.

A função utiliza um `Column` para organizar verticalmente os elementos da tela, incluindo:

* Imagem de perfil;
* Saudação;
* Nome;
* Cargo profissional;
* Seção "Sobre";
* Informações de contato.

Também é definida uma cor de fundo diferente do branco padrão:

```kotlin
.background(Color(0xFFE3F2FD))
```

A função utiliza `Modifier.padding()` para criar espaçamento interno e `Alignment.CenterHorizontally` para organizar os elementos horizontalmente no centro da tela.

---

### 4.4 `ContactInfo()`

A função `ContactInfo()` é um `Composable` reutilizável criado para exibir cada informação de contato.

Ela recebe dois parâmetros:

```kotlin
icon: ImageVector
text: String
```

O parâmetro `icon` determina qual ícone será exibido e o parâmetro `text` determina o conteúdo do contato.

A função utiliza um `Row` para colocar o ícone ao lado do texto.

Ela é reutilizada três vezes na tela:

* Telefone;
* E-mail;
* Site.

Essa reutilização evita a necessidade de repetir a estrutura de código para cada informação de contato.

---

### 4.5 Recursos utilizados

#### `res/drawable/avatar`

O arquivo de imagem `avatar` é utilizado como imagem principal do perfil.

Ele é carregado através de:

```kotlin
painterResource(id = R.drawable.avatar)
```

A imagem é exibida utilizando o `Composable` `Image`.

---

### 4.6 Ícones utilizados

O aplicativo utiliza ícones da biblioteca Material Icons:

* `Icons.Filled.Phone` — utilizado para representar o telefone.
* `Icons.Filled.Email` — utilizado para representar o e-mail.
* `Icons.Filled.Web` — utilizado para representar o site.

Os ícones são exibidos através do `Composable` `Icon`.

---

## 5. Diagrama textual da hierarquia de Composables

A estrutura hierárquica da interface pode ser representada da seguinte forma:

```text
MainActivity
└── setContent
    └── ProfileCard
        └── Column
            ├── Image
            │   └── avatar
            │
            ├── Box
            │   └── Text
            │       └── "Bem-vindo ao meu perfil!"
            │
            ├── Spacer
            │
            ├── Text
            │   └── "Leandro Silva"
            │
            ├── Text
            │   └── "Desenvolvedor Android"
            │
            ├── Spacer
            │
            ├── Text
            │   └── "Apaixonado por tecnologia e inovação."
            │
            ├── Spacer
            │
            ├── ContactInfo
            │   ├── Icon (Phone)
            │   └── Text
            │       └── "(35) 99999-8888"
            │
            ├── ContactInfo
            │   ├── Icon (Email)
            │   └── Text
            │       └── "leandro.dev@gmail.com"
            │
            └── ContactInfo
                ├── Icon (Web)
                └── Text
                    └── "www.leandrodev.com"
```

## 6. Funcionalidades implementadas

O aplicativo atende aos requisitos propostos na atividade, apresentando:

* Imagem de perfil no topo da tela;
* Saudação em destaque com fonte maior e centralizada;
* Nome completo do profissional;
* Cargo profissional com hierarquia visual diferente do nome;
* Seção "Sobre" com uma breve apresentação;
* Três informações de contato;
* Ícones do Material Icons associados aos contatos;
* Cor de fundo personalizada, diferente do branco padrão;
* Interface desenvolvida integralmente utilizando Jetpack Compose;
* Função `ContactInfo()` reutilizável para organização dos contatos.

O projeto demonstra a utilização de componentes básicos do Jetpack Compose, organização hierárquica de composables, modificadores de layout, tipografia, imagens, ícones e reutilização de componentes.

## 7. Informações do aluno

**Aluno:** Leandro Otávio de Almeida

**Disciplina:** LPDM

**Atividade:** Avaliação 1 — Cartão de Perfil Profissional

**Turma:** Informática, 3º ano.
