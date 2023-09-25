# Diagrama Entidade Relacionamento (DER)

<!-- Descrição -->

<br/>

<div style="text-align: center">
    <img src='./imagens/diagramaEntidadeRelacionamento.png'>
    <p>Fonte: Autores</p>
</div>

# Modelo Entidade Relacionamento (MER)

O MER é um modelo de alta nível de abstração que representa as emtidades com os seus atributos, além dos seus respectivos relacionamentos.

## 1. Entidades
- **Dimensão**
- **Portal**
- **Local**
- **Estrutura**
- **Estado de Ambiente**
- **Personagem**
    - **PC**
    - **NPC**
- **Instância**
- **Conquista**
- **Inventário**
- **Item**
    - **Consumível**
    - **Não consumível**
## 2. Atributos

## 3. Relacionamentos

- **Dimensão (1,1) --possui-- (1,N) Local**

    - **Uma dimensão pode possuir N e no mínimo 1 Local.**

- **Local (1,N) --possui-- (1,N) Estruturas**

    - **Um ou vários Local(is) pode possuir N e no mínimo 1 Estrutura.**

- **PC (1,1) --possui-- (0,N) Conquista**

    - **Um PC possui nenhuma ou N conquistas.**
...