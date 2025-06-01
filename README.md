# Máquina de Turing Universal (MTU)

Este projeto implementa uma Máquina de Turing Universal (MTU) que interpreta e executa uma fita com símbolos e uma lista de transições. Os estados e os símbolos seguem um padrão baseado em sufixos de `1`, como `q1`, `q11`, `q111`, etc.

---

## 📐 Formato da Entrada

A entrada é formada por duas partes:

1. **Transições** — uma ou mais regras de transição no formato:  
   ```
   <estadoAtual><simboloLido><simboloEscrito><Direcao><proximoEstado>
   ```

2. **Fita** — uma sequência de símbolos que será manipulada pela máquina.

Essas duas partes são separadas por um símbolo `$`. As transições são separadas por `#`.

### Exemplo:

```
q1a1a11Rq11#q11a11a111Rqf$a1a11
```

- Transições:
  - `q1a1a11Rq11`: se estiver no estado `q1`, lendo `a1`, escreve `a11`, move para a direita e vai para `q11`.
  - `q11a11a111Rqf`: se estiver no estado `q11`, lendo `a11`, escreve `a111`, move para a direita e vai para o estado final `qf`.
- Fita: `a1 a11`

---

## ⚙️ Estratégia de Execução

A lógica da execução segue as etapas abaixo:

1. **Encontrar o início da fita:**
   - A fita de entrada começa após o símbolo `$`.

2. **Marcar o estado inicial e a transição atual:**
   - O estado inicial (`q1`) é marcado com `y` (por exemplo, `qy`).
   - A transição analisada é marcada com `x` (por exemplo, `ax`).

3. **Buscar o estado atual na lista de transições:**
   - A máquina percorre as transições até encontrar uma que começa com o estado atual (contando os y's).