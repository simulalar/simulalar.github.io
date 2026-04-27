# 🏠 Como funciona o Simulador de Financiamento Imobiliário

Este simulador foi desenvolvido para mostrar, de forma prática e visual, como diferentes estratégias afetam um financiamento imobiliário ao longo do tempo.

A lógica é totalmente executada no navegador (client-side), sem necessidade de backend.

---

## 🔢 1. Entrada de dados

O usuário define os principais parâmetros do financiamento:

* **Valor do imóvel**
* **Entrada**
* **Prazo (em meses)**
* **Orçamento mensal disponível**
* **Quantidade de meses amortizando acima da parcela**

Com isso, o sistema calcula automaticamente:

👉 **Valor financiado = Valor do imóvel − Entrada**

Também é exibido o percentual da entrada, indicando se está dentro do recomendado (~20%).

---

## 📊 2. Taxa de juros

O usuário escolhe:

* Uma taxa pré-definida (com contexto de mercado)
* Ou uma taxa personalizada

Internamente, o sistema converte a taxa anual para mensal:

[
i_{mensal} = (1 + i_{anual})^{1/12} - 1
]

Essa taxa é usada em todos os cálculos de juros.

---

## 🧮 3. Sistemas de amortização

O simulador calcula 4 cenários diferentes:

### 🟢 SAC — Estratégia 1

* Amortização constante
* Parcela começa alta e diminui com o tempo
* Amortização extra reduz prazo + parcela

### 🟢 SAC — Estratégia 2

* Recalcula a amortização após pagamentos extras
* Queda mais agressiva na parcela

### 🔵 PRICE — Estratégia 1

* Parcela fixa
* Amortização extra reduz apenas o prazo

### 🟣 PRICE — Estratégia 2

* Recalcula a parcela após amortização extra
* Reduz valor da parcela ao longo do tempo

---

## 💸 4. Amortização extra

Se o usuário define um orçamento maior que a parcela:

👉 A diferença vira **amortização extra**

Essa amortização:

* reduz o saldo devedor mais rápido
* diminui juros totais
* pode reduzir prazo ou parcela (dependendo da estratégia)

---

## 🔄 5. Portabilidade de crédito

Se ativada, o sistema simula:

* Troca de banco em um mês específico
* Nova taxa de juros
* Custo da portabilidade

### O que acontece internamente:

1. No mês escolhido:

   * o saldo devedor é recalculado
   * a nova taxa passa a ser aplicada
2. O prazo restante é mantido
3. A parcela pode ser recalculada (dependendo do sistema)

O simulador também compara:

* cenário **com portabilidade**
* cenário **sem portabilidade**

E calcula:

👉 **Economia líquida = economia em juros − custo da portabilidade**

---

## 📈 6. Simulação mês a mês

Para cada cenário, o sistema gera uma tabela completa contendo:

* Parcela
* Juros do mês
* Amortização
* Amortização extra
* Saldo devedor restante

O cálculo segue este fluxo:

1. Calcula juros do mês:
   [
   juros = saldo \times taxa_mensal
   ]

2. Define amortização (SAC ou PRICE)

3. Aplica amortização extra (se houver)

4. Atualiza saldo devedor:
   [
   saldo = saldo - (amortização + extra)
   ]

5. Repete até quitar a dívida

---

## 🏆 7. Comparação de cenários

Após rodar a simulação, o sistema:

* soma todos os juros pagos em cada cenário
* identifica o menor custo total
* destaca automaticamente o melhor resultado

Também mostra:

* redução de prazo
* queda de parcela
* economia com portabilidade

---

## 📉 8. Gráfico

O gráfico exibe:

* evolução das parcelas ao longo do tempo
* impacto da amortização extra
* efeito da portabilidade

Inclui marcações para:

* fim da amortização extra
* momento da portabilidade

---

## 📋 9. Tabelas detalhadas

Cada estratégia possui uma tabela com:

* visualização mensal
* destaques para:

  * portabilidade
  * fim da amortização
  * meses com pagamento extra

---

## ⚠️ Observações

* Os cálculos são aproximados e educacionais
* Bancos podem usar regras adicionais (TR, seguros, taxas administrativas)
* O simulador foca em:

  * comportamento financeiro
  * impacto das decisões

---

## 💡 Resumo

O simulador permite responder perguntas como:

* Vale a pena amortizar ou investir?
* Portabilidade compensa?
* Qual sistema gera menos juros?
* Vale mais reduzir prazo ou parcela?

Tudo isso de forma visual, comparativa e interativa.

---
