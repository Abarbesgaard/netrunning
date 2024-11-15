---
{"dg-publish":true,"permalink":"/acid/","created":"2024-11-15T13:41:54.712+01:00"}
---

ACID står for **Atomicity**, **Consistency**, **Isolation** og **Durability**. Det er fire vigtige egenskaber, der definerer databasetransaktioner og sikrer dataintegritet i databasesystemer [1](https://www.yugabyte.com/acid/) [2](https://en.wikipedia.org/wiki/ACID_transactions) [3](https://www.starburst.io/data-glossary/acid-transactions/).Her er en kort forklaring af hver egenskab:
![Pasted image 20241115134410.png](/img/user/Pasted%20image%2020241115134410.png)
*Billedet er fra [scyllab](https://www.scylladb.com/glossary/acid-database/)*

1. **Atomicity (Atomaritet)**: En transaktion behandles som en enkelt, udelelig enhed. Enten gennemføres hele transaktionen, eller også fejler den helt [1](https://www.yugabyte.com/acid/) [2](https://en.wikipedia.org/wiki/ACID_transactions).
2. **Consistency (Konsistens)**: En transaktion bringer databasen fra én gyldig tilstand til en anden, og overholder alle definerede regler og begrænsninger [1](https://www.yugabyte.com/acid/) [2](https://en.wikipedia.org/wiki/ACID_transactions).
3. **Isolation (Isolation)**: Samtidige transaktioner udføres uafhængigt af hinanden, uden at påvirke hinandens resultater [1](https://www.yugabyte.com/acid/) [2](https://en.wikipedia.org/wiki/ACID_transactions).
4. **Durability (Holdbarhed)**: Når en transaktion er gennemført, er dens resultater permanent gemt i databasen, selv i tilfælde af systemfejl eller strømsvigt [1](https://www.yugabyte.com/acid/) [2](https://en.wikipedia.org/wiki/ACID_transactions).

ACID-egenskaberne er afgørende for at opretholde dataintegritet og pålidelighed i databasesystemer. De sikrer, at transaktioner udføres korrekt og fuldstændigt, selv under vanskelige forhold som systemnedbrud eller samtidige opdateringer [3](https://www.starburst.io/data-glossary/acid-transactions/) [4](https://www.simplilearn.com/acid-properties-in-dbms-article).Disse egenskaber er særligt vigtige i systemer, der kræver høj dataintegritet, som f.eks. banksystemer, hvor nøjagtighed og pålidelighed er afgørende [4](https://www.simplilearn.com/acid-properties-in-dbms-article) [5](https://www.javatpoint.com/acid-properties-in-dbms).