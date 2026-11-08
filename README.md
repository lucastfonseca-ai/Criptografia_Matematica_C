<p align="center">
  <img src="https://img.shields.io/badge/Linguagem-C-00599C?style=for-the-badge&logo=c&logoColor=white" alt="Linguagem C">
  <img src="https://img.shields.io/badge/Área-Criptografia%20e%20Matemática-7B2CBF?style=for-the-badge" alt="Criptografia e Matemática">
  <img src="https://img.shields.io/badge/Projeto-Educacional-2D6A4F?style=for-the-badge" alt="Projeto educacional">
</p>

> Um projeto educacional que combina **criptografia simples**, **progressões matemáticas** e **fundamentos de programação** em um único algoritmo desenvolvido em Linguagem C.

---

## 🧭 Sumário

- [🎯 Sobre o projeto](#-sobre-o-projeto)
- [🧠 Objetivo educacional](#-objetivo-educacional)
- [🔑 Como funciona a criptografia](#-como-funciona-a-criptografia)
- [📐 Sequências matemáticas](#-sequências-matemáticas)
- [⚙️ Conceitos computacionais aplicados](#️-conceitos-computacionais-aplicados)
- [▶️ Como executar](#️-como-executar)
- [🧪 Exemplo de execução](#-exemplo-de-execução)
- [📄 Arquivo de resultado](#-arquivo-de-resultado)
- [⚠️ Limitações e melhorias](#️-limitações-e-melhorias)
- [📁 Estrutura do repositório](#-estrutura-do-repositório)

---

## 🎯 Sobre o projeto

O projeto propõe a criação de um programa em **C** capaz de transformar uma palavra em texto codificado por meio de **duas camadas de deslocamento**. A primeira camada utiliza a Cifra de César, com um deslocamento fixo informado pelo usuário. A segunda utiliza uma sequência matemática, cujo termo muda de acordo com a posição de cada letra.

O usuário informa:

1. **Uma palavra secreta:** até 15 letras minúsculas, sem espaços, acentos ou caracteres especiais.
2. **Um valor de SHIFT:** número que define o deslocamento fixo da Cifra de César.
3. **Uma sequência numérica:** PA, PG, Fibonacci ou Quadrados.

Ao final, o programa exibe a palavra criptografada e registra os dados principais da execução no arquivo `resultado_criptografia.txt`.

### 🌟 Objetivo geral

Unificar, em um projeto desenvolvido na Linguagem C, os conceitos de **criptografia simples**, **matemática aplicada (progressões e sequências)** e **programação**, promovendo o aprendizado ativo, lógico e analítico.

---

## 🧠 Objetivo educacional

O desenvolvimento está relacionado à **Taxonomia de Bloom**, que organiza o aprendizado em níveis de complexidade crescente. Cada etapa do projeto estimula uma competência diferente.

| Nível | Ação no projeto | Competência desenvolvida |
|---|---|---|
| 🧩 **Lembrar** | Reconhecer o alfabeto, os códigos ASCII e as sequências numéricas. | Identificar fundamentos matemáticos e computacionais. |
| 💡 **Compreender** | Entender o deslocamento das letras e o funcionamento da Cifra de César. | Relacionar lógica matemática e codificação. |
| 🛠️ **Aplicar** | Implementar as duas camadas de criptografia e as sequências em C. | Utilizar a teoria em um contexto computacional. |
| 🔎 **Analisar** | Comparar os resultados obtidos com diferentes sequências. | Investigar como os padrões matemáticos alteram a codificação. |
| ⚖️ **Avaliar** | Examinar as diferenças entre os resultados e as limitações do método. | Desenvolver pensamento crítico e argumentação técnica. |
| 🚀 **Criar** | Modificar o algoritmo, adicionar sequências e desenvolver novas funcionalidades. | Integrar conhecimentos e exercitar a criatividade. |

---

## 🔑 Como funciona a criptografia

O algoritmo utiliza o alfabeto de `a` até `z`, com 26 letras, e aplica duas transformações em cada caractere.

### 1. Primeira camada: Cifra de César

Cada letra é deslocada por uma quantidade fixa de posições, definida pelo usuário no campo `SHIFT`.

Por exemplo, com `SHIFT = 3`:

```text
Alfabeto original:  a b c d e f g h ... x y z
Alfabeto deslocado: d e f g h i j k ... a b c
```

Assim, a letra `a` passa a ser `d`, a letra `b` passa a ser `e` e assim sucessivamente. Ao chegar ao final do alfabeto, o deslocamento retorna ao início.

### 2. Segunda camada: deslocamento pela sequência

Depois da Cifra de César, cada letra recebe um segundo deslocamento. Esse valor é obtido a partir do termo da sequência matemática escolhido pelo usuário.

A posição da letra determina qual termo será utilizado:

```text
Deslocamento total = SHIFT + termo da sequência
```

O uso do operador módulo (`% 26`) mantém o resultado dentro das 26 letras do alfabeto.

**Representação simplificada:**

```text
Palavra original
      │
      ▼
Camada 1: Cifra de César (SHIFT fixo)
      │
      ▼
Camada 2: Deslocamento (sequência matemática)
      │
      ▼
Palavra criptografada
      │
      ▼
Exibição na tela + gravação em arquivo
```

---

## 📐 Sequências matemáticas

O programa oferece quatro opções. Cada sequência fornece um deslocamento diferente para cada letra da palavra.

| Opção | Sequência | Termos utilizados | Regra aplicada no código |
|---|---|---|---|
| `1` | **Progressão Aritmética (PA)** | 2, 5, 8, 11, 14... | `t = 2 + 3 * n` |
| `2` | **Progressão Geométrica (PG)** | 1, 2, 4, 8, 16... | `t = a`, depois `a *= 2` |
| `3` | **Fibonacci** | 1, 1, 2, 3, 5, 8, 13... | Utiliza os valores de `a` e `b` para gerar o próximo termo. |
| `4` | **Números quadrados** | 1, 4, 9, 16, 25... | `t = (n + 1) * (n + 1)` |

> **Atenção:** a contagem de `n` começa em zero no programa. Por isso, a PA começa em 2, a PG em 1, Fibonacci em 1 e a sequência dos quadrados em 1.

### Exemplo de deslocamentos

Para a palavra `codigo`, com `SHIFT = 3`, os deslocamentos adicionais da sequência Fibonacci serão:

| Letra | Posição (`n`) | Termo Fibonacci | SHIFT | Deslocamento total |
|---|---:|---:|---:|---:|
| c | 0 | 1 | 3 | 4 |
| o | 1 | 1 | 3 | 4 |
| d | 2 | 2 | 3 | 5 |
| i | 3 | 3 | 3 | 6 |
| g | 4 | 5 | 3 | 8 |
| o | 5 | 8 | 3 | 11 |

---

## ⚙️ Conceitos computacionais aplicados

O projeto utiliza recursos fundamentais da Linguagem C:

| Conceito | Aplicação no código |
|---|---|
| 📦 **Variáveis** | Armazenam a palavra, o SHIFT, o tipo de sequência e os termos matemáticos. |
| 🔤 **Strings e vetores** | O vetor `char p[16]` armazena a palavra de até 15 caracteres e o terminador `\0`. |
| ⌨️ **Entrada de dados** | `printf()` apresenta as solicitações e `scanf()` recebe os valores digitados. |
| 🔀 **Condicionais múltiplas** | `switch` seleciona a sequência matemática escolhida. |
| 🔁 **Laço de repetição** | `for` percorre a palavra e processa cada letra individualmente. |
| ➗ **Operações matemáticas** | Soma, multiplicação e módulo realizam os deslocamentos e controlam o retorno ao início do alfabeto. |
| 🔡 **ASCII** | A subtração de `'a'` transforma a letra em uma posição numérica relativa ao alfabeto. |
| 📄 **Manipulação de arquivos** | `fopen()`, `fprintf()` e `fclose()` gravam o resultado em um arquivo `.txt`. |

### 🧰 Linguagem e ferramentas

- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg" width="18" alt="C"> **Linguagem C:** implementação da lógica e das operações matemáticas.
- **Biblioteca `stdio.h`:** entrada, saída e manipulação básica de arquivos.
- **Compilador GCC:** compilação do código-fonte.
- **Git e GitHub:** versionamento e documentação do projeto.

---

## ⚠️ Limitações e melhorias

O código atual atende à demonstração das duas camadas de deslocamento, mas alguns pontos podem ser aprimorados em versões futuras:

- ✅ **Validar a entrada:** verificar se `scanf()` conseguiu ler os dados e se a palavra contém somente letras minúsculas de `a` a `z`.
- ✅ **Validar a sequência:** aceitar apenas opções de `1` a `4`, em vez de tratar uma opção inválida como deslocamento zero.
- ✅ **Tratar SHIFT negativo:** normalizar o valor para o intervalo de `0` a `25`, evitando resultados incorretos com o operador `%` em C.
- ✅ **Verificar o arquivo:** confirmar se `fopen()` retornou um ponteiro válido antes de chamar `fprintf()`.
- ✅ **Criar a descriptografia:** implementar a operação inversa, subtraindo os mesmos deslocamentos na ordem inversa.
- ✅ **Guardar histórico:** adicionar novas execuções ao arquivo, em vez de sobrescrever o resultado anterior.
- ✅ **Expandir as sequências:** incluir números primos, outras progressões ou sequências definidas pelo usuário.

> 🔒 **Importante:** este é um exercício didático de substituição de letras. A Cifra de César e os deslocamentos por sequências não oferecem segurança criptográfica real e não devem ser usados para proteger senhas, dados pessoais ou informações confidenciais.

---

## 👨‍💻 Aprendizados e propósito

Mais do que transformar letras, este projeto demonstra como conceitos de matemática podem ser convertidos em instruções computacionais. Ao combinar progressões, manipulação de caracteres, estruturas de controle e arquivos, o estudante percorre diferentes etapas do raciocínio lógico: compreender um padrão, transformá-lo em algoritmo, testar resultados e avaliar suas limitações.

**Matemática + lógica + programação = conhecimento aplicado.** 🧠💻

---

<p align="center">
  Desenvolvido como atividade educacional em <strong>Linguagem C</strong>.
  <br>
  ⭐ Explore, teste e aprimore o algoritmo!
</p>
