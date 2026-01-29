# Refatorando um dicionário comum
Repositório público para a entrega das atividades 1, 2 e 3

# Atividades Pydantic e FastAPI

Este repositório contém uma série de exercícios focados em validação de dados com **Pydantic** e criação de APIs modernas com **FastAPI**.

## 🛠️ Atividades Implementadas

### Atividade 1: Modelagem de Criaturas (`atividade_1.py`)
Nesta etapa, transformamos um dicionário Python em um modelo robusto do Pydantic.
- **O que faz:** Define a classe `Creature`, instancia objetos a partir de dicionários (usando *unpacking*) e imprime os nomes das criaturas.

### Atividade 2: Validação e Tratamento de Erros (`atividade_2.py`)
Exploração de como o Pydantic reage a dados inválidos.
- **O que faz:** Força erros de validação ao enviar tipos incorretos ou valores que violam restrições de tamanho.

### Atividade 3: API de Usuários com Persistência (`main.py`)
Criação de um endpoint real utilizando FastAPI.
- **O que faz:** Recebe dados de usuário, valida o formato do e-mail e o tamanho do nome, armazena em memória e persiste os dados em um arquivo `users.json`.

---

## ❌ Exemplos de Erros de Validação (Atividade 2)

Durante os testes, foram identificados os seguintes erros gerados automaticamente pelo Pydantic:

### 1. Erro de Tipo (Type Error)
* **Campo:** `description`
* **Valor enviado:** `["Grande", "Peludo"]` (uma lista)
* **Mensagem de erro:** `Input should be a valid string`
* **Causa:** O modelo espera uma `str`, mas recebeu um objeto `list`. O Pydantic não consegue converter uma lista diretamente para texto de forma segura.

### 2. Erro de Valor (Value Error)
* **Campo:** `country`
* **Valor enviado:** `"CONGO"`
* **Mensagem de erro:** `String should have at most 2 characters`
* **Causa:** O campo foi definido com a restrição `Field(max_length=2)`. Como "CONGO" possui 5 caracteres, a validação impede a criação do objeto.

---

## 🚀 Como Executar

### 1. Instalar dependências
Certifique-se de ter o Python instalado e execute:
```bash
pip install fastapi uvicorn "pydantic[email]"
