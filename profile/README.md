<p align="center">
  <img src="./assets/banner.svg" alt="StockProof — Firmar o no firmar" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/BSC-mainnet-F0B90B?style=for-the-badge&logo=binance&logoColor=black" alt="BSC mainnet">
  <img src="https://img.shields.io/badge/mercado-solo%20spot-2EBD85?style=for-the-badge" alt="Solo spot">
  <img src="https://img.shields.io/badge/bStocks%20·%20Ondo%20·%20xStocks-1E2329?style=for-the-badge" alt="bStocks, Ondo, xStocks">
  <img src="https://img.shields.io/badge/BNB%20Hack-Tokenized%20Stocks-F0B90B?style=for-the-badge" alt="BNB Hack: Tokenized Stocks">
</p>

<p align="center">
  Dado un <b>ticker</b> y un <b>monto en dólares</b>, StockProof dice si conviene firmar<br>
  el swap de esa acción tokenizada en BSC. <b>Si una pregunta falla, no hay transacción.</b>
</p>

---

## 🎯 El problema

Las acciones tokenizadas se operan las 24 horas, pero los riesgos no aparecen en la pantalla del swap:

| | Riesgo | Qué pasa |
|:-:|---|---|
| 🎭 | **Impostores** | Hay contratos que se llaman igual que el token pero no son el oficial. |
| 🌊 | **Liquidez** | Una orden grande rompe el pool, y a veces se entra pero no se puede salir. |
| 🧮 | **Precio engañoso** | Con dividendos o tokens de retorno total, el precio de la wallet no es el de la acción. |
| 🌙 | **Fuera de horario** | El sábado casi no afecta a un nombre líquido, pero en un nombre fino puede salir caro. |

## 🛡️ Las cuatro preguntas

<p align="center">
  <img src="./assets/questions.svg" alt="Las cuatro preguntas de StockProof" width="100%">
</p>

```mermaid
flowchart LR
    A(["Ticker + monto"]) --> Q1{"1 · ¿Contrato real?"}
    Q1 -- no --> X["❌ Corta y devuelve<br/>la orden que sí firmaría"]
    Q1 -- sí --> Q2{"2 · ¿Entra y sale?"}
    Q2 -- no --> X
    Q2 -- sí --> Q3{"3 · ¿Es la acción?"}
    Q3 -- sin causa --> X
    Q3 -- sí --> Q4{"4 · ¿Régimen ok?"}
    Q4 -- no --> X
    Q4 -- sí --> S(["✅ Firma un solo wrapper"])

    classDef ok fill:#2EBD85,stroke:#2EBD85,color:#0B0E11
    classDef no fill:#F6465D,stroke:#F6465D,color:#ffffff
    classDef q fill:#1E2329,stroke:#F0B90B,color:#F0B90B
    class S ok
    class X no
    class Q1,Q2,Q3,Q4 q
```

## 🚪 La salida se mide antes de entrar

<p align="center">
  <img src="./assets/exit.svg" alt="Exit Now, Exit Availability y Exit Risk" width="100%">
</p>

StockProof no predice el precio ni la liquidez futura. Mide lo que cuesta salir **ahora** y muestra lo que está publicado.

## ✨ Lo que lo hace distinto

> [!IMPORTANT]
> **Su trabajo visible es negarse.** Toda negativa devuelve la orden que sí firmaría: el mismo ticker y el mismo wrapper, con un monto más chico.

- 🔍 **No cambia de wrapper en silencio.** Muestra las tres cotizaciones y nombra el wrapper elegido y los que quedaron afuera.
- ⚖️ **Elige con reglas claras.** Firma el wrapper con compra y venta bajo el tope; si hay más de uno, el de menor impacto.
- 💬 **Entiende frases en castellano**, como *«comprame $200 de NVIDIA si el costo es menor al 1%»*. La frase suma condiciones, pero nunca apaga las cuatro preguntas.

## 🧰 Construido con

<p>
  <img src="https://img.shields.io/badge/Binance-Web3%20APIs-F0B90B?style=flat-square&logo=binance&logoColor=black" alt="Binance Web3 APIs">
  <img src="https://img.shields.io/badge/Agentic-Wallet-F0B90B?style=flat-square" alt="Agentic Wallet">
  <img src="https://img.shields.io/badge/Next.js-15-000000?style=flat-square&logo=nextdotjs" alt="Next.js 15">
  <img src="https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React 19">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white" alt="Vitest">
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white" alt="Playwright">
</p>

APIs de Binance que usa: **RWA Data**, **Market**, **Trading**, **Transaction** y **Wallet**.

## 📦 Repositorios

| Repo | Qué tiene |
|---|---|
| [**stock-proof**](https://github.com/StkProof/stock-proof) | La app y la lógica de decisión de las cuatro preguntas |
| [**vault-stockproof**](https://github.com/StkProof/vault-stockproof) | El contexto de producto: idea, MVP, brief y fuentes de cada número |

---

<p align="center">
  <sub>Construido para <a href="https://www.bnbchain.org/en/hackathons/tokenized-stocks">BNB Hack: Tokenized Stocks Edition</a> · 2026 · Solo spot · Solo BSC mainnet</sub>
</p>
