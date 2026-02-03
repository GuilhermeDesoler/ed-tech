# Projeto 01 - Página Pessoal Simples

> **Prazo**: 1 semana | **Dificuldade**: ⭐ Iniciante | **Tecnologia**: HTML puro

## 🎯 Objetivo

Criar uma página HTML simples de apresentação pessoal, aplicando os conceitos de estrutura HTML aprendidos nas primeiras aulas.

## 📋 Requisitos

### Obrigatórios

Sua página deve conter:

1. **Título da página** no `<head>`
2. **Cabeçalho** com seu nome completo
3. **Foto** sua (pode ser qualquer imagem se preferir)
4. **Seção "Sobre Mim"** com:
   - Breve biografia (3-5 linhas)
   - Idade e cidade onde mora
5. **Seção "Hobbies"** com:
   - Lista não ordenada de pelo menos 3 hobbies
6. **Seção "Contato"** com:
   - Email (pode ser fictício)
   - Links para redes sociais (pelo menos 2)

### Extras (Opcional)

- Lista ordenada de seus objetivos profissionais
- Seção com suas músicas/filmes favoritos
- Tabela com informações adicionais
- Mais de uma página (index.html + sobre.html, por exemplo)

## 🏗 Estrutura Sugerida

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meu Nome - Página Pessoal</title>
</head>
<body>
    <header>
        <h1>Seu Nome Aqui</h1>
        <p>Futuro Desenvolvedor Web</p>
    </header>

    <main>
        <section>
            <h2>Sobre Mim</h2>
            <img src="foto.jpg" alt="Minha foto">
            <p>Sua biografia aqui...</p>
        </section>

        <section>
            <h2>Hobbies</h2>
            <ul>
                <li>Hobby 1</li>
                <li>Hobby 2</li>
                <li>Hobby 3</li>
            </ul>
        </section>

        <section>
            <h2>Contato</h2>
            <p>Email: <a href="mailto:seuemail@example.com">seuemail@example.com</a></p>
            <p>
                <a href="https://github.com/seuusuario" target="_blank">GitHub</a> |
                <a href="https://linkedin.com/in/seuusuario" target="_blank">LinkedIn</a>
            </p>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 - Seu Nome. Desenvolvido no EdTech.</p>
    </footer>
</body>
</html>
```

## 📁 Estrutura de Arquivos

```
minha-pagina-pessoal/
├── index.html
├── foto.jpg (ou .png)
└── README.md
```

## ✅ Checklist de Verificação

Antes de entregar, certifique-se de que:

- [ ] O código está bem indentado (organizado)
- [ ] Todas as tags abertas foram fechadas
- [ ] Os links funcionam corretamente
- [ ] A imagem é exibida (caminho correto)
- [ ] O HTML está validado (sem erros)
- [ ] O código está no GitHub
- [ ] Há um README.md explicando o projeto

## 🎨 Exemplo de Resultado

**Sem CSS** (apenas HTML), sua página deve ter uma estrutura clara com:
- Títulos hierárquicos (H1, H2)
- Parágrafos de texto
- Uma imagem
- Listas
- Links clicáveis

*Não se preocupe com a aparência visual ainda! Vamos estilizar depois com CSS.*

## 📤 Como Entregar

### 1. Criar repositório no GitHub

```bash
# No terminal/Git Bash
cd C:\Users\SeuNome\projetos\edtech
mkdir pagina-pessoal
cd pagina-pessoal
git init
```

### 2. Adicionar arquivos

```bash
# Criar o index.html e adicionar ao Git
git add .
git commit -m "Adiciona página pessoal inicial"
```

### 3. Enviar para o GitHub

1. Crie um novo repositório no GitHub (sem README)
2. Execute os comandos mostrados pelo GitHub:

```bash
git remote add origin https://github.com/seuusuario/pagina-pessoal.git
git branch -M main
git push -u origin main
```

### 4. Publicar no GitHub Pages

1. Vá em Settings do repositório
2. Pages (menu lateral)
3. Source: Deploy from branch > `main` > `/root`
4. Save
5. Aguarde alguns minutos e acesse: `https://seuusuario.github.io/pagina-pessoal`

### 5. Enviar para avaliação

Preencha o formulário de entrega com:
- Link do repositório GitHub
- Link da página publicada (GitHub Pages)

## 🎓 Critérios de Avaliação

| Critério | Peso | Descrição |
|----------|------|-----------|
| **Estrutura HTML** | 40% | Tags corretas, semântica, hierarquia |
| **Requisitos** | 30% | Todos os itens obrigatórios presentes |
| **Organização** | 15% | Código indentado e legível |
| **GitHub** | 15% | Repositório bem organizado, README |

### Nota Mínima para Aprovação: 70%

## 💡 Dicas

1. **Use semântica HTML5**:
   - `<header>`, `<main>`, `<section>`, `<footer>`

2. **Valide seu código**:
   - https://validator.w3.org/

3. **Escreva bons commits**:
   - "Adiciona seção sobre mim"
   - "Corrige link do GitHub"

4. **Peça ajuda**:
   - Discord da turma
   - Colegas
   - Instrutores

## 🔗 Recursos Úteis

- [Guia de HTML - MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML)
- [Cheatsheet HTML](../recursos/cheatsheet-html.md)
- [Como usar GitHub Pages](https://pages.github.com/)

## ❓ Dúvidas Frequentes

**Q: Não tenho foto, posso usar um avatar?**
A: Sim! Use qualquer imagem que queira, ou busque em sites como [UI Faces](https://uifaces.co/) ou [Avatar Generator](https://www.avatargenerator.com/).

**Q: Meus links de redes sociais podem ser fictícios?**
A: Sim, nesta fase inicial pode ser. Mas recomendamos criar perfis reais (GitHub é essencial!).

**Q: Precisa ser em português?**
A: Sim, mas se quiser fazer uma versão em inglês também, é um ótimo extra!

**Q: Posso usar CSS mesmo não tendo sido ensinado ainda?**
A: Pode experimentar, mas não é obrigatório. Foque primeiro em HTML bem estruturado.

---

## 📅 Prazo de Entrega

**Data limite**: [Definido pelo instrutor]

## 🎉 Próximos Passos

Após concluir este projeto:
1. Continue praticando HTML
2. Na próxima semana, vamos estilizar esta página com CSS!
3. Guarde bem este código, ele será sua base

---

**Bom projeto! Esta é sua primeira página web!** 🚀
