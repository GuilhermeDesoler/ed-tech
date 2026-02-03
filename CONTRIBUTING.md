# 🤝 Guia de Contribuição - EdTech

Obrigado por considerar contribuir com o projeto EdTech! Este documento contém diretrizes para contribuir com o conteúdo do curso.

## 📋 Índice

- [Como Posso Contribuir?](#como-posso-contribuir)
- [Reportando Bugs ou Erros](#reportando-bugs-ou-erros)
- [Sugerindo Melhorias](#sugerindo-melhorias)
- [Contribuindo com Conteúdo](#contribuindo-com-conteúdo)
- [Padrões de Código](#padrões-de-código)
- [Processo de Pull Request](#processo-de-pull-request)

---

## Como Posso Contribuir?

Há várias formas de contribuir:

- 📝 **Corrigir erros** (typos, links quebrados, código)
- ✨ **Melhorar conteúdo** existente
- 🆕 **Adicionar novos exercícios** ou projetos
- 📚 **Criar material complementar**
- 🎨 **Melhorar visualizações** e diagramas
- 🌐 **Traduzir** conteúdo (se aplicável)
- 💡 **Sugerir novos tópicos** ou tecnologias

---

## Reportando Bugs ou Erros

Encontrou um erro no conteúdo? Siga estes passos:

### 1. Verifique se já foi reportado
- Busque nas [Issues](https://github.com/seu-usuario/edtech-curso-programacao/issues) existentes

### 2. Crie uma nova Issue
Se não encontrou, crie uma nova issue com:

**Título**: Descrição clara e concisa
```
Exemplo: "Erro no código da Aula 5 - Mês 2"
```

**Descrição**:
```markdown
**Localização**:
- Arquivo: `1-semestre-fundamentos-web/mes-02-css-avancado/aulas/aula-05.md`
- Linha: 42

**Erro Encontrado**:
Descrição do erro...

**Correção Sugerida**:
Como deveria ser...

**Contexto Adicional**:
Qualquer informação relevante...
```

---

## Sugerindo Melhorias

Tem uma ideia para melhorar o curso?

### 1. Abra uma Issue de Feature Request

**Título**:
```
[SUGESTÃO] Adicionar módulo sobre TypeScript
```

**Descrição**:
```markdown
**Descrição da Melhoria**:
Explicação clara do que você sugere...

**Justificativa**:
Por que isso seria útil...

**Implementação Sugerida**:
Como poderia ser implementado...

**Alternativas Consideradas**:
Outras abordagens que você pensou...
```

---

## Contribuindo com Conteúdo

### Tipos de Contribuição

#### 1. Correções Simples (Typos, Links)
- Fork o repositório
- Faça as correções
- Envie um Pull Request

#### 2. Novos Exercícios
Siga o template:

```markdown
# Exercício X - Título do Exercício

## Objetivo
Descrição clara do que o exercício treina...

## Instruções
1. Passo 1
2. Passo 2
...

## Exemplo de Entrada/Saída
[Se aplicável]

## Dica
[Opcional] Ajuda sutil sem dar a resposta

## Solução
[Em arquivo separado ou spoiler]
```

#### 3. Novos Projetos
Siga o template:

```markdown
# Projeto X - Título do Projeto

## Objetivo
O que o aluno vai construir...

## Requisitos

### Obrigatórios
- [ ] Requisito 1
- [ ] Requisito 2

### Extras (Opcional)
- [ ] Extra 1

## Tecnologias
- HTML, CSS, JavaScript

## Estrutura Sugerida
\`\`\`
projeto/
├── index.html
├── style.css
└── script.js
\`\`\`

## Critérios de Avaliação
- Funcionalidade: 40%
- Código: 30%
- Design: 20%
- Criatividade: 10%
```

#### 4. Novas Aulas
Siga a estrutura padrão:

```markdown
# Aula X - Título da Aula

> **Duração**: 2 horas | **Tipo**: Teórica/Prática

## Objetivos da Aula
- Objetivo 1
- Objetivo 2

## Agenda
| Horário | Atividade | Duração |
|---------|-----------|---------|
| ... | ... | ... |

## Conteúdo Teórico
...

## Parte Prática
...

## Desafio da Aula
...

## Resumo
...

## Tarefa de Casa
...

## Próxima Aula
...
```

---

## Padrões de Código

### Markdown

#### Títulos
```markdown
# H1 - Apenas para título principal do documento
## H2 - Seções principais
### H3 - Subseções
#### H4 - Detalhes
```

#### Listas
```markdown
- Use `-` para listas não ordenadas
1. Use `1.` para listas ordenadas
```

#### Code Blocks
````markdown
```javascript
// Sempre especifique a linguagem
const exemplo = "código";
```
````

#### Links
```markdown
- Internos: [Texto](./caminho/arquivo.md)
- Externos: [Texto](https://url.com)
```

#### Emojis
Use moderadamente para melhorar visualização:
```markdown
✅ ⭐ 📚 💻 🎯 🚀 ⚠️ 💡 📝 🔗
```

### Código JavaScript

```javascript
// Use const/let, nunca var
const nome = "valor";

// Nomes descritivos em camelCase
const nomeDoUsuario = "João";

// Funções arrow quando apropriado
const soma = (a, b) => a + b;

// Comentários quando necessário
// Explica o "por quê", não o "o quê"
```

### Código Python

```python
# Nomes em snake_case
nome_usuario = "João"

# Funções documentadas
def calcular_soma(a, b):
    """
    Calcula a soma de dois números.

    Args:
        a (int): Primeiro número
        b (int): Segundo número

    Returns:
        int: Soma dos números
    """
    return a + b
```

---

## Processo de Pull Request

### 1. Fork e Clone

```bash
# Fork no GitHub, depois:
git clone https://github.com/SEU-USUARIO/edtech-curso-programacao.git
cd edtech-curso-programacao
```

### 2. Crie uma Branch

```bash
# Nome descritivo
git checkout -b corrige-aula-05-mes02
# ou
git checkout -b adiciona-exercicios-javascript
```

### 3. Faça suas Mudanças

- Siga os padrões acima
- Teste links e código
- Verifique ortografia

### 4. Commit

```bash
git add .
git commit -m "Corrige erro de sintaxe na Aula 5"
```

**Padrão de commits**:
- `Adiciona: [descrição]` - Novo conteúdo
- `Corrige: [descrição]` - Correção de erro
- `Atualiza: [descrição]` - Melhoria de conteúdo
- `Remove: [descrição]` - Remoção de conteúdo

### 5. Push

```bash
git push origin sua-branch
```

### 6. Abra Pull Request

No GitHub:
1. Vá ao seu fork
2. Click em "Compare & pull request"
3. Preencha o template:

```markdown
## Descrição
Breve descrição das mudanças...

## Tipo de Mudança
- [ ] Correção de bug/erro
- [ ] Nova funcionalidade
- [ ] Melhoria de conteúdo
- [ ] Documentação

## Checklist
- [ ] Código/conteúdo testado
- [ ] Sem erros de digitação
- [ ] Links funcionando
- [ ] Segue padrões do projeto
```

### 7. Revisão

- Responda feedbacks
- Faça ajustes se necessário
- Aguarde aprovação

---

## 📝 Checklist do Contribuidor

Antes de enviar um PR, verifique:

- [ ] Li e entendi este guia
- [ ] Meu conteúdo segue os padrões
- [ ] Testei código e links
- [ ] Escrevi commits claros
- [ ] Criei uma branch específica
- [ ] Preenchi o template do PR
- [ ] Não incluí arquivos desnecessários

---

## 🎯 Boas Práticas

### DO ✅

- Seja claro e objetivo
- Teste seu código antes de enviar
- Siga a estrutura existente
- Peça ajuda se tiver dúvidas
- Seja respeitoso com outros contribuidores

### DON'T ❌

- Não envie mudanças não relacionadas no mesmo PR
- Não quebre a estrutura existente
- Não copie conteúdo de terceiros sem atribuição
- Não ignore feedbacks de revisão

---

## ❓ Dúvidas?

- Abra uma [Issue de Discussão](https://github.com/seu-usuario/edtech-curso-programacao/issues)
- Entre em contato no Discord da turma
- Envie email para [contato]

---

## 🙏 Agradecimentos

Suas contribuições ajudam a democratizar o acesso à educação em tecnologia!

**Obrigado por fazer parte do EdTech!** 🚀
