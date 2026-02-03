# Aula 01 - Introdução à Programação e Como a Web Funciona

> **Duração**: 2 horas | **Tipo**: Teórica + Prática

## 🎯 Objetivos da Aula

Ao final desta aula, você será capaz de:
- Entender o que é programação e por que aprender
- Compreender como a internet e a web funcionam
- Conhecer as principais tecnologias web (HTML, CSS, JavaScript)
- Configurar o ambiente de desenvolvimento
- Criar seu primeiro arquivo HTML

## 📋 Agenda

| Horário | Atividade | Duração |
|---------|-----------|---------|
| 00:00 - 00:15 | Apresentações e boas-vindas | 15min |
| 00:15 - 00:45 | Como a web funciona | 30min |
| 00:45 - 01:00 | Tecnologias web (HTML/CSS/JS) | 15min |
| 01:00 - 01:15 | **Intervalo** | 15min |
| 01:15 - 01:45 | Configuração do ambiente | 30min |
| 01:45 - 02:00 | Primeiro código + Fechamento | 15min |

---

## 📚 Conteúdo Teórico

### 1. O que é Programação?

**Programação** é a arte de dar instruções precisas a um computador para realizar tarefas.

#### Analogia do Mundo Real

Imagine que você está ensinando alguém a fazer um sanduíche. Você precisa:

1. Pegar o pão
2. Abrir o pão ao meio
3. Passar manteiga
4. Colocar o recheio
5. Fechar o pão

Isso é um **algoritmo** - uma sequência de passos para resolver um problema!

#### Por que aprender programação?

- 💼 **Mercado aquecido**: Milhares de vagas abertas
- 💰 **Bons salários**: Acima da média nacional
- 🌍 **Trabalho remoto**: Empresas do mundo todo
- 🚀 **Criar soluções**: Resolver problemas reais
- 🧠 **Desenvolver raciocínio**: Lógica e criatividade

---

### 2. Como a Internet Funciona?

#### Internet vs Web

- **Internet**: Rede global de computadores conectados
- **Web (World Wide Web)**: Serviço que roda sobre a internet (páginas, sites)

#### Modelo Cliente-Servidor

```
┌─────────────┐                      ┌─────────────┐
│   CLIENTE   │                      │  SERVIDOR   │
│             │                      │             │
│  (Você no   │   1. Requisição      │   (Google,  │
│  navegador) │ ──────────────────► │   Netflix)  │
│             │                      │             │
│             │   2. Resposta        │             │
│             │ ◄────────────────── │             │
└─────────────┘                      └─────────────┘
```

**Exemplo prático**:
1. Você digita `www.google.com` no navegador (CLIENTE)
2. Seu computador envia uma requisição para os servidores do Google (SERVIDOR)
3. O servidor processa e envia de volta o HTML/CSS/JS da página
4. Seu navegador renderiza (exibe) a página

#### HTTP/HTTPS

- **HTTP**: Hypertext Transfer Protocol (protocolo de comunicação)
- **HTTPS**: HTTP Secure (comunicação criptografada - mais segura)

---

### 3. Tecnologias Web

Desenvolvimento web usa 3 pilares fundamentais:

#### 🏗 HTML (HyperText Markup Language)
**Função**: Estrutura e conteúdo

```html
<h1>Título da Página</h1>
<p>Este é um parágrafo.</p>
```

**Analogia**: O esqueleto e ossos de uma casa

---

#### 🎨 CSS (Cascading Style Sheets)
**Função**: Aparência e estilização

```css
h1 {
  color: blue;
  font-size: 24px;
}
```

**Analogia**: A pintura, decoração e acabamento da casa

---

#### ⚡ JavaScript
**Função**: Interatividade e comportamento

```javascript
alert("Olá, mundo!");
```

**Analogia**: A parte elétrica, hidráulica - o que faz a casa "funcionar"

---

### 4. Navegadores e DevTools

#### Principais Navegadores
- Google Chrome ⭐ (vamos usar este)
- Firefox
- Microsoft Edge
- Safari

#### DevTools (Ferramentas do Desenvolvedor)

Pressione `F12` ou `Ctrl+Shift+I` para abrir.

**Principais abas**:
- **Elements**: Ver HTML e CSS da página
- **Console**: Executar JavaScript e ver erros
- **Network**: Ver requisições HTTP
- **Sources**: Ver arquivos do site

---

## 💻 Parte Prática

### Atividade 1: Configurar o Ambiente (30min)

#### Passo 1: Instalar o VS Code

1. Acesse: https://code.visualstudio.com/
2. Baixe a versão para Windows
3. Instale (Next > Next > Finish)

#### Passo 2: Instalar Extensões

No VS Code, vá em Extensions (Ctrl+Shift+X) e instale:

- ✅ **Live Server** (por Ritwick Dey)
- ✅ **HTML CSS Support**
- ✅ **Auto Rename Tag**
- ✅ **Prettier** (formatador de código)

#### Passo 3: Criar uma Pasta de Projetos

```
C:\Users\SeuNome\projetos\edtech\
```

#### Passo 4: Abrir a Pasta no VS Code

- File > Open Folder
- Selecione a pasta `edtech`

---

### Atividade 2: Primeiro Código HTML (15min)

#### Passo 1: Criar o arquivo

No VS Code:
1. Clique com botão direito na sidebar
2. New File
3. Nome: `index.html`

#### Passo 2: Digitar o código

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minha Primeira Página</title>
</head>
<body>
    <h1>Olá, Mundo!</h1>
    <p>Esta é minha primeira página web!</p>
    <p>Estou aprendendo programação no EdTech 🚀</p>
</body>
</html>
```

#### Passo 3: Visualizar no navegador

**Opção 1 - Manual**:
- Salve o arquivo (Ctrl+S)
- Clique com botão direito no arquivo
- Abrir com Chrome

**Opção 2 - Live Server** (melhor):
- Botão direito no arquivo > Open with Live Server
- Abrirá automaticamente no navegador
- Qualquer alteração atualiza automaticamente!

---

## 🎯 Desafio da Aula

Modifique o arquivo `index.html` e adicione:

1. Um título diferente (altere o `<title>`)
2. Mais um parágrafo com seu nome
3. Um parágrafo dizendo por que você quer aprender programação

**Dica**: Use `<p>Seu texto aqui</p>` para criar parágrafos.

---

## 📝 Resumo da Aula

Hoje você aprendeu:

- ✅ O que é programação
- ✅ Como a internet e web funcionam (cliente-servidor)
- ✅ As 3 tecnologias web: HTML, CSS, JavaScript
- ✅ Como configurar o ambiente de desenvolvimento
- ✅ Como criar e visualizar seu primeiro arquivo HTML

---

## 🏠 Tarefa de Casa (Opcional)

1. Explore sites que você usa (YouTube, Instagram, etc)
   - Abra o DevTools (F12)
   - Veja o HTML na aba Elements
   - Tente modificar algum texto e veja o resultado

2. Leia o artigo:
   - [Como a web funciona - MDN](https://developer.mozilla.org/pt-BR/docs/Learn/Getting_started_with_the_web/How_the_Web_works)

---

## 🔜 Próxima Aula

Na próxima aula, vamos aprofundar em **HTML** e aprender:
- Estrutura completa de um documento
- Tags essenciais
- Como criar listas, links e imagens

---

## 💬 Dúvidas Frequentes

**Q: Preciso saber inglês para programar?**
A: Não é obrigatório, mas ajuda muito! A maioria dos recursos e documentações estão em inglês.

**Q: Quanto tempo leva para se tornar um programador?**
A: Com dedicação, em 12-18 meses você já pode conseguir sua primeira vaga júnior!

**Q: É difícil?**
A: No início pode parecer, mas com prática constante fica natural. É como aprender a dirigir!

---

**Ótima primeira aula! Nos vemos na próxima!** 🎉
