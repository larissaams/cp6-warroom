# FICHA DE DECISÕES · War Room FiapBank (CP6 · 3 aulas)

> Este arquivo é o **README.md do repositório do grupo** (`cp6-warroom-<nome-do-grupo>`).
> Vale **5,0 pontos** (rodadas 0,5 · relâmpagos 0,3), e a nota é pela
> **justificativa**, não pela letra. Preencham após cada aula e commitem até
> **23h59 do mesmo dia** (regras completas na seção 5 do enunciado).
>
> **Os incidentes da madrugada são revelados só em aula.** O título de cada registro
> será **ditado pelo professor na hora**; ninguém se antecipe.

**Grupo (nome da equipe plantonista):** ______________________________________

**Turma:** 2CCPG **Repo:** `cp6-warroom-____________________`

**Integrantes (nome + RM):**

| Nome | RM |

|Larissa|564168|

|Anny|565055|

|Raira|564850|

|Sofia|562767|

|Ana|563171|

|Gisleine|563804|

## 0. Setup do repositório (antes da 1ª aula; podem apagar esta seção depois)

1. Um integrante cria o repo **público** no GitHub: `cp6-warroom-<nome-do-grupo>`
   (ex.: `cp6-warroom-debugadores`), com um README qualquer
2. Substituam o conteúdo do `README.md` por este template (no navegador, pelo próprio
   GitHub, ou clonando):
   ```bash
   git clone https://github.com/<conta>/cp6-warroom-<nome-do-grupo>.git
   cd cp6-warroom-<nome-do-grupo>
   # substitua o conteúdo do README.md por este template e:
   git add .
   git commit -m "chore: ficha em branco do grupo"
   git push
   ```
3. Postem o **link no Teams** (o mesmo link para todo o grupo)

**Convenção de commits** (1 commit por rodada; relâmpagos podem ir junto com a
rodada seguinte):

```
decisao: R1 - opcao C (<resumo da justificativa em uma frase>)
decisao: R2 - opcao A (<resumo em uma frase>)
pos-mortem: relatorio de incidente da madrugada
```

---

## 📁 Dossiê técnico do FiapBank (MVP em produção)

**Stack:** Java 17 + Spring Boot + Spring Data JPA + Oracle. API com endpoints em
`/api/contas` e `/api/transferencias` (cenário visto desde a Aula 13).

**Contrato e regras de negócio que o banco prometeu aos clientes e aos reguladores:**

| Regra | Como deve ser |
|---|---|
| Transferência **PIX** | taxa **R$ 0,00** |
| Transferência **TED** | taxa fixa **R$ 5,00** |
| Saldo | **nunca fica negativo**: transferência/saque sem saldo é recusado com erro claro |
| Número de conta | **sequencial e único** (1001, 1002, 1003...), gerado pelo sistema |
| Extrato de transferência | grava **quem pagou** e **quem recebeu**, na ordem certa |
| CPF | **dado sensível**: nunca aparece nas respostas da API |
| Consultas ao banco | sempre parametrizadas, e cada operação **usa e libera** a conexão |
| Suíte de testes | roda antes de todo deploy; **verde** é pré-requisito pra subir |

**Como escrever a justificativa:** nomeie o **mecanismo técnico** em jogo (o
conceito das Aulas 11 a 15 que explica o incidente) e o **trade-off** (velocidade ×
segurança × faturamento × dívida). "Porque é mais seguro" não é justificativa.

---

# 📝 REGISTRO DE DECISÕES

> A cada incidente, o professor dita o título (ex.: "Rodada 1"). **Copiem o modelo
> abaixo, colem no fim desta seção** e preencham com o rascunho feito em aula, junto
> com o **placar do grupo** após a consequência. Commitem 1 commit por rodada até
> 23h59 do dia.
>
> **Eventos relâmpago:** registrem apenas se o grupo for **afetado** (o professor
> chama quem for; não ser chamado é bom sinal).

**Modelo (copiar para cada decisão):**

```
## <título ditado pelo professor>

**Tipo:** ( rodada / relâmpago ) · **Voto:** ( A / B / C / D )

**Justificativa:**

<2 a 3 linhas: mecanismo técnico + trade-off>

**Placar do grupo após esta decisão:** 🔥 __ · 💰 R$ __ mil · 🧹 __
```

*(as decisões entram aqui, na ordem em que a madrugada as trouxer; placar inicial:
🔥 7 · 💰 0 · 🧹 2)*

---

## 🔎 O caminho do MEU grupo (preencher na 3ª aula, quando o mapa for revelado)

Uma linha por decisão registrada acima (usem os títulos ditados em aula):


## O saldo que virou negativo  
 
**Tipo:** rodada 1 · **Voto:**  A 
 
**Justificativa:**  
 
Escolhemos o rollback para voltar à versão de terça-feira e evitar novas transferências sem saldo suficiente. Assim, reduzimos o risco de prejuízos, mas podemos perder correções recentes. 
 
**Placar do grupo após esta decisão:** 🔥 -1 · 💰 15 mil · 🧹 +2 
 

 
## A busca que não acha ninguém  



**Tipo**: relâmpago · **Voto:**  B  


**Justificativa:** 

Escolhemos usar a query findByTitular do repository, pois ela já está pronta e evita erros na busca por nome. Assim, aproveitamos uma solução existente e deixamos o código mais organizado  


**Placar do grupo após esta decisão:**  🔥 -1 · 💰 15 mil · 🧹 +1 
 


## A injeção que derreteu o banco 


**Tipo:** rodada 2 · **Voto:**  D 


**Justificativa:** 

Escolhemos usar a findByTitular do repository, pois ela já está pronta e evita a montagem manual de SQL. Assim, reduzimos o risco de injeção de SQL e deixamos o código mais seguro e organizado. 


**Placar do grupo após esta decisão:**  🔥 -1 · 💰 15 mil · 🧹 0

## A noite das contas gêmeas  

**Tipo:** rodada 3 · **Voto:**  D 

**Justificativa:** 


Escolhemos delegar a numeração ao banco de dados, que garante a geração de números únicos. Assim, evitamos contas duplicadas e reduzimos o risco de problemas em auditorias. 

**Placar do grupo após esta decisão:**  🔥 -1 · 💰 25 mil · 🧹 0 


## O comprovante que aponta pra pessoa errada 


**Tipo:** rodada 4 · **Voto:** A 

**Justificativa:** 

Escolhemos corrigir a gravação do extrato para que os dados das transferências futuras fiquem corretos. Porém, os históricos antigos continuarão errados, evitando um retrabalho imediato. 

**Placar do grupo após esta decisão:**  🔥 0 · 💰 40 mil · 🧹 1 

## A fábrica que devolve null 

  

**Tipo:** rodada 5 · **Voto:** A 

**Justificativa:** 

Escolhemos lançar uma exceção clara na factory quando o tipo de conta for inválido. Assim, identificamos o erro rapidamente e evitamos falhas difíceis de entender no repository. 

**Placar do grupo após esta decisão:**  🔥 -1 · 💰 40 mil · 🧹 1 


## O teste vermelho às 03h45 

**Tipo:** rodada 6 · **Voto:** D 

**Justificativa:** 

Escolhemos ajustar o teste para refletir o comportamento atual do código e conseguir realizar o deploy dentro do prazo. Porém, isso pode esconder um erro, já que o contrato com o cliente define a taxa da TED como R$ 5,00. 

**Placar do grupo após esta decisão:**  🔥 -1 · 💰 40 mil · 🧹 2 


## "A taxa é 5 ou 50?" 
  

**Tipo:** relâmpago · **Voto:** C 
  
**Justificativa:** 

Escolhemos reproduzir o problema com um teste antes de responder, para confirmar o valor correto da taxa. Assim, evitamos passar informações erradas aos clientes e à imprensa. 


**Placar do grupo após esta decisão:**  🔥 0 · 💰 40 mil · 🧹 2 


 

## Go/No-Go da Black Friday 

  

**Tipo** rodada 7 · **Voto:** B 

  

**Justificativa:** 

Escolhemos corrigir os bugs e garantir que todos os testes passem antes de liberar a campanha. Assim, priorizamos a segurança e a qualidade do sistema, mesmo com duas horas de atraso. 

**Placar do grupo após esta decisão:**  🔥 1 · 💰 80 mil · 🧹 1 


---

# 📋 PÓS-MORTEM · relatório de incidente (montar em sala na 3ª aula)

> Rascunho em aula e commit final `pos-mortem:` até 23h59 do dia da 3ª aula.

## 1. Linha do tempo da madrugada

19h12 — Rodada 1: Escolhemos o rollback para evitar novas transferências sem saldo.

20h10 — Relampago A: Usamos a query findByTitular para corrigir a busca por nome.

21h02 — Rodada 2: Escolhemos a query do repository para evitar injeção de SQL.

22h50 — Rodada 3: Escolhemos delegar a numeração das contas ao banco de dados.

00h47 — Rodada 4: Corrigimos a gravação dos extratos futuros.

01h30 — Rodada 5: Escolhemos lançar uma exceção clara para tipos de conta inválidos.

03h45 — Rodada 6: Ajustamos o teste para esperar R$ 50, mantendo o erro da taxa.

05h58 — Relampago E: Escolhemos reproduzir o problema com um teste antes de responder à imprensa.

06h15 — Rodada 7: Escolhemos corrigir os bugs e garantir que a suíte de testes estivesse verde antes de abrir a campanha.

## 2. Causa raiz de 2 incidentes (aula + mecanismo técnico)

**Incidente 1**: Saldo negativo após transferência. 

Exceção engolida (exception swallowing). O catch capturava a exceção de saldo insuficiente, mas não interrompia a operação. Dessa forma, o débito continuava mesmo sem saldo suficiente. 

**Incidente 2**: Injeção de SQL na busca por titular. 

JDBC puro e concatenação de strings na consulta SQL. O nome informado era inserido diretamente no comando, permitindo que uma entrada maliciosa alterasse a consulta e retornasse todas as contas.

## 3. O que faríamos diferente (2 rodadas + por quê)

Rodada 1: Escolheríamos corrigir o problema e criar um teste antes de publicar, em vez de fazer rollback. Assim, evitaríamos perder correções recentes e reduziríamos o risco de bugs antigos voltarem. 

Rodada 6: Investigaríamos a taxa incorreta antes do deploy, mesmo que perdêssemos a janela. O teste deveria continuar verificando o contrato de R$ 5, em vez de aceitar R$ 50.

## 4. A maior lição da equipe

Aprendemos que não basta fazer o sistema funcionar rapidamente. Precisamos respeitar as regras de negócio, criar testes confiáveis e corrigir as causas dos problemas. A segurança dos clientes deve ser prioridade, mesmo quando existe pressão para entregar rápido. 

Uma palavra para resumir a madrugada: Caótica
