# Mês 13: Python Fundamentos

**Carga Horária:** 96 horas (4 semanas)
**Período:** Semanas 1-4
**Status:** Módulo Essencial ⭐⭐⭐

## Visão Geral

Este módulo introduz Python, uma linguagem essencial para desenvolvimento backend moderno, ciência de dados e automação. Os alunos aprenderão sintaxe, estruturas de dados, programação orientada a objetos e funcional, preparando-se para Django nos meses seguintes.

## Objetivos de Aprendizado

Ao final deste módulo, o aluno será capaz de:

- Entender filosofia e características do Python
- Trabalhar com tipos e estruturas de dados
- Controlar fluxo e lógica de programa
- Implementar funções e módulos
- Dominar programação orientada a objetos
- Trabalhar com paradigmas funcionais
- Manipular arquivos e dados
- Debugar e testar código Python
- Usar bibliotecas e pacotes populares

## Estrutura de Aprendizado

### SEMANA 1: Fundamentos Python

#### Aula 1: Introdução e Setup (4h)
- História e filosofia do Python
- Por que Python é popular
- Python 2 vs Python 3
- Setup de ambiente (venv, pip)
- IDEs (VS Code, PyCharm)
- REPL e primeiros comandos
- Comentários e style guide (PEP 8)

**Projeto Prático:** Setup ambiente Python profissional

```bash
# Criar virtual environment
python3 -m venv venv
source venv/bin/activate  # ou venv\Scripts\activate no Windows

# Instalar pacotes
pip install requests numpy pandas
pip freeze > requirements.txt
```

#### Aula 2: Tipos de Dados e Variáveis (4h)
- Tipos primitivos (int, float, str, bool)
- Type hints e anotações
- Variáveis e escopo
- Conversão de tipos
- Strings (formatting, f-strings, operações)
- None e valores especiais

**Projeto Prático:** Manipulação de tipos de dados

```python
# Type hints
name: str = "John"
age: int = 30
score: float = 9.5
active: bool = True

# F-strings
message = f"{name} é {age} anos e tem score {score}"

# Conversão
text = "123"
number = int(text)
```

#### Aula 3: Operadores e Controle de Fluxo (4h)
- Operadores aritméticos, lógicos, comparativos
- If/else/elif
- Operador ternário
- Loops (for, while)
- Break, continue, else em loops
- Match/case (Python 3.10+)

**Projeto Prático:** Jogo de adivinhar número

```python
import random

target = random.randint(1, 100)
attempts = 0

while True:
    guess = int(input("Adivinhe: "))
    attempts += 1

    if guess == target:
        print(f"Acertou em {attempts} tentativas!")
        break
    elif guess < target:
        print("Maior")
    else:
        print("Menor")
```

#### Aula 4: Estruturas de Dados (4h)
- Listas (criação, acesso, métodos)
- Tuplas (imutabilidade)
- Dicionários (chaves-valores)
- Conjuntos (sets)
- List comprehension
- Unpacking

**Projeto Prático:** Manipulação de estruturas

```python
# Listas
numbers = [1, 2, 3, 4, 5]
squared = [x**2 for x in numbers if x > 2]

# Dicionários
person = {"name": "John", "age": 30, "city": "NYC"}
for key, value in person.items():
    print(f"{key}: {value}")

# Sets
tags = {"python", "web", "backend", "web"}  # duplicata removida
unique = set([1, 1, 2, 2, 3])
```

### SEMANA 2: Funções e Programação Funcional

#### Aula 5: Funções Básicas (4h)
- Definição e chamada
- Parâmetros e argumentos
- Default values
- *args e **kwargs
- Return e múltiplos retornos
- Escopo e closure

**Projeto Prático:** Biblioteca de funções

```python
def greet(name: str, greeting: str = "Hello") -> str:
    """Saudação com mensagem customizável."""
    return f"{greeting}, {name}!"

def process_args(*args, **kwargs):
    """Aceita múltiplos argumentos."""
    for arg in args:
        print(f"Arg: {arg}")
    for key, value in kwargs.items():
        print(f"{key}: {value}")

# Unpacking
data = ("John", 30)
name, age = data
```

#### Aula 6: Programação Funcional (4h)
- Funções como first-class objects
- Map, filter, reduce
- Lambda functions
- Decorators
- Generators
- Iterators

**Projeto Prático:** Utilitários com programação funcional

```python
from functools import reduce

# Lambda com map/filter
numbers = [1, 2, 3, 4, 5]
doubled = list(map(lambda x: x * 2, numbers))
even = list(filter(lambda x: x % 2 == 0, numbers))

# Reduce
total = reduce(lambda a, b: a + b, numbers)

# Decorators
def timer(func):
    def wrapper(*args, **kwargs):
        import time
        start = time.time()
        result = func(*args, **kwargs)
        print(f"Tempo: {time.time() - start}s")
        return result
    return wrapper

@timer
def slow_function():
    import time
    time.sleep(1)

# Generators
def count_up_to(n):
    i = 0
    while i < n:
        yield i
        i += 1

for num in count_up_to(5):
    print(num)
```

#### Aula 7: Módulos e Pacotes (4h)
- Importação (import, from import)
- Criando módulos
- __main__ e __name__
- Pacotes e __init__.py
- Instalação com pip
- Virtual environments
- Estrutura de projeto

**Projeto Prático:** Criar módulo reutilizável

```
meu_projeto/
├── main.py
├── utils/
│   ├── __init__.py
│   ├── math_utils.py
│   └── string_utils.py
└── venv/

# utils/__init__.py
from .math_utils import add, multiply
from .string_utils import uppercase, reverse

# main.py
from utils import add, uppercase
```

#### Aula 8: Tratamento de Exceções (4h)
- Try/except/finally
- Tipos de exceções
- Raising exceções
- Context managers (with)
- Custom exceptions
- Debugging

**Projeto Prático:** Error handling robusto

```python
class CustomError(Exception):
    pass

def divide(a, b):
    try:
        if b == 0:
            raise CustomError("Divisão por zero não permitida")
        return a / b
    except CustomError as e:
        print(f"Erro: {e}")
        return None
    except Exception as e:
        print(f"Erro inesperado: {e}")
    finally:
        print("Operação finalizada")

# Context manager
with open("file.txt", "r") as f:
    content = f.read()
# Arquivo fechado automaticamente
```

### SEMANA 3: Programação Orientada a Objetos

#### Aula 9: Classes e Objetos (4h)
- Definição de classes
- Atributos e métodos
- __init__ e self
- Atributos de classe vs instância
- Propriedades (@property)
- Métodos especiais (__str__, __repr__)

**Projeto Prático:** Sistema de classes

```python
class Animal:
    """Classe base para animais."""
    species_count = 0

    def __init__(self, name: str, age: int):
        self.name = name
        self.age = age
        Animal.species_count += 1

    def __str__(self) -> str:
        return f"{self.name} ({self.age} anos)"

    @property
    def info(self) -> str:
        return f"Nome: {self.name}, Idade: {self.age}"

    def make_sound(self) -> str:
        return "Som genérico"

class Dog(Animal):
    def make_sound(self) -> str:
        return "Au au!"

dog = Dog("Rex", 5)
print(dog)  # Rex (5 anos)
print(dog.make_sound())  # Au au!
```

#### Aula 10: Herança e Polimorfismo (4h)
- Herança simples e múltipla
- MRO (Method Resolution Order)
- super()
- Polimorfismo
- Método abstracto (ABC)
- Interfaces

**Projeto Prático:** Arquitetura com herança

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    def __init__(self, brand: str):
        self.brand = brand

    @abstractmethod
    def start(self):
        pass

class Car(Vehicle):
    def start(self):
        return f"{self.brand} car started"

class Motorcycle(Vehicle):
    def start(self):
        return f"{self.brand} motorcycle started"

# Polymorphism
vehicles = [Car("Toyota"), Motorcycle("Harley")]
for vehicle in vehicles:
    print(vehicle.start())
```

#### Aula 11: Encapsulamento e Convenções (4h)
- Atributos privados (_private, __private)
- Métodos privados
- Getters e setters
- Dunder methods
- Comparação de objetos
- Hashing

**Projeto Prático:** Classe bem encapsulada

```python
class BankAccount:
    def __init__(self, owner: str, balance: float = 0):
        self.owner = owner
        self.__balance = balance  # Private

    @property
    def balance(self) -> float:
        return self.__balance

    def deposit(self, amount: float) -> None:
        if amount > 0:
            self.__balance += amount

    def withdraw(self, amount: float) -> bool:
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            return True
        return False

    def __eq__(self, other) -> bool:
        return self.__balance == other.__balance

    def __lt__(self, other) -> bool:
        return self.__balance < other.__balance
```

#### Aula 12: Composição e Design (4h)
- Composição vs Herança
- Mixins
- Padrões de design em Python
- Singleton
- Factory
- Strategy

**Projeto Prático:** Padrões de design

```python
# Strategy pattern
from abc import ABC, abstractmethod

class PaymentStrategy(ABC):
    @abstractmethod
    def pay(self, amount: float):
        pass

class CreditCardPayment(PaymentStrategy):
    def pay(self, amount: float):
        return f"Pagando ${amount} com cartão"

class PayPalPayment(PaymentStrategy):
    def pay(self, amount: float):
        return f"Pagando ${amount} com PayPal"

class Order:
    def __init__(self, strategy: PaymentStrategy):
        self.strategy = strategy

    def pay(self, amount: float):
        return self.strategy.pay(amount)

# Uso
order = Order(CreditCardPayment())
print(order.pay(100))
```

### SEMANA 4: Arquivos, Testes e Projeto

#### Aula 13: Manipulação de Arquivos (4h)
- Leitura e escrita
- JSON, CSV, XML
- Serialização (pickle)
- Operações de filesystem
- Path handling
- Context managers

**Projeto Prático:** Processamento de arquivos

```python
import json
import csv
from pathlib import Path

# Trabalhar com JSON
with open("data.json", "w") as f:
    json.dump({"name": "John", "age": 30}, f)

# Ler CSV
with open("data.csv", "r") as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(row)

# Usando pathlib
config_dir = Path.home() / ".config" / "myapp"
config_dir.mkdir(parents=True, exist_ok=True)
```

#### Aula 14: Testes em Python (4h)
- unittest framework
- pytest basics
- Fixtures
- Mocking
- Test-Driven Development
- Coverage

**Projeto Prático:** Suite de testes

```python
import unittest
from calculator import add, subtract

class TestCalculator(unittest.TestCase):
    def test_add(self):
        self.assertEqual(add(2, 3), 5)

    def test_subtract(self):
        self.assertEqual(subtract(5, 3), 2)

    def test_add_negative(self):
        self.assertEqual(add(-1, 1), 0)

if __name__ == '__main__':
    unittest.main()

# Pytest
# def test_add():
#     assert add(2, 3) == 5
# pytest test_calculator.py
```

#### Aula 15: Bibliotecas Populares (4h)
- Requests (HTTP)
- Beautiful Soup (web scraping)
- NumPy (matemática)
- Pandas (dados)
- DateTime
- Collections

**Projeto Prático:** Usar bibliotecas externas

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
from datetime import datetime, timedelta

# HTTP com requests
response = requests.get("https://api.github.com/users/github")
user_data = response.json()

# Web scraping
html = requests.get("https://example.com").text
soup = BeautifulSoup(html, "html.parser")
titles = soup.find_all("h1")

# Pandas para dados
df = pd.DataFrame({
    "name": ["John", "Jane"],
    "age": [30, 25]
})
print(df.mean())

# DateTime
now = datetime.now()
tomorrow = now + timedelta(days=1)
```

#### Aula 16: Projeto Integrador (8h)
- Aplicação CLI interativa
- Múltiplas classes
- Persistência de dados
- Testes completos
- Documentação

## Conteúdo Técnico Detalhado

### Exemplo Completo de Classe

```python
from datetime import datetime
from typing import List

class Book:
    """Representação de um livro."""

    books_created = 0

    def __init__(self, title: str, author: str, pages: int):
        self.title = title
        self.author = author
        self.pages = pages
        self.created_at = datetime.now()
        Book.books_created += 1

    def __str__(self) -> str:
        return f"{self.title} por {self.author}"

    def __repr__(self) -> str:
        return f"Book(title='{self.title}', author='{self.author}')"

    @property
    def info(self) -> str:
        return f"{self.title} - {self.pages} páginas"

    def read(self, pages: int) -> None:
        print(f"Lendo {pages} páginas...")

    @classmethod
    def from_string(cls, book_str: str):
        """Factory method."""
        title, author, pages = book_str.split(",")
        return cls(title, author, int(pages))

class Library:
    """Biblioteca de livros."""

    def __init__(self, name: str):
        self.name = name
        self.__books: List[Book] = []

    def add_book(self, book: Book) -> None:
        self.__books.append(book)

    def list_books(self) -> List[str]:
        return [str(book) for book in self.__books]

    def find_by_author(self, author: str) -> List[Book]:
        return [b for b in self.__books if b.author == author]
```

## Projetos do Módulo

### Projeto 1: Sistema de Tarefas CLI
**Duração:** 16 horas
**Funcionalidades:**
- Criar, listar, completar, deletar tarefas
- Persistência em JSON
- Interface CLI
- Prioridades e datas
- Testes unitários

### Projeto 2: Sistema de Biblioteca
**Duração:** 32 horas
**Funcionalidades:**
- Gestão de livros e membros
- Empréstimos e devoluções
- Multas por atraso
- Relatórios
- Persistência de dados
- Testes completos

### Projeto 3: Revisor de Conceitos
**Duração:** 8 horas

## Stack Tecnológico

- **Python 3.10+**
- **pip e venv**
- **VS Code**
- **pytest** (testes)
- **Pandas** (dados)
- **Requests** (HTTP)

## Cronograma Recomendado

| Semana | Horas | Foco | Projeto |
|--------|-------|------|---------|
| 1 | 24 | Fundamentos Python | Exercícios |
| 2 | 24 | Funções e OOP | Projeto 1 |
| 3 | 24 | OOP avançado | Projeto 2 |
| 4 | 24 | Integração | Projeto Final |

## Requisitos de Conhecimento Prévio

- Conhecimento sólido de programação (do semestre anterior)
- Conceitos de algoritmos
- Terminal/CLI

## Avaliação

### Critérios
- Frequência 75%+
- Projetos nota 7.0+
- Código bem estruturado
- Testes implementados

### Cálculo de Notas
- Projeto 1: 30%
- Projeto 2: 40%
- Qualidade de Código: 30%

---

**Última atualização:** Janeiro de 2025
**Versão:** 2.0
**Nível:** Iniciante a Intermediário
