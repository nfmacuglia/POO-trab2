# ACMEPolling — Trabalho II (Final) de POO

Esqueleto base do sistema de eleições (PUCRS, Programação Orientada a Objetos,
prof. Marcelo H. Yamaguti, 2026/2). Contém as classes, os pacotes e as
assinaturas combinadas pelo grupo; a lógica ainda está por fazer.

## Estrutura

```
src/
  Main.java                      ponto de entrada (diagrama)
  aplicacao/AppACMEPolling.java  inicializar() + abertura da interface
  dados/                         Partido, Localidade, Candidato (abstrata),
                                 Presidente, Governador, Voto,
                                 TipoLocalidade, SituacaoCandidato
  cadastro/                      CadastroPartidos, CadastroLocalidades,
                                 CadastroCandidatos, CadastroVotos, Apuracao
  persistencia/                  LeitorCSV (entrada), ArquivoDados (salvar/carregar)
  excecoes/                      CadastroException, DadosInvalidosException
  gui/                           JanelaPrincipal + Painel* (Swing)
arquivos/                        CSVs de exemplo do Apêndice do enunciado
```

## Compilar e executar

Execute sempre a partir da **raiz do projeto**, para que a pasta `arquivos/`
seja encontrada. Em IDE: marque `src` como pasta de código-fonte e rode `Main`.

```
mkdir -p out
javac -encoding UTF-8 -d out $(find src -name "*.java")
java -cp out Main
```

(No PowerShell: `javac -encoding UTF-8 -d out (Get-ChildItem -Recurse src -Filter *.java).FullName`)

## Regras do esqueleto

- As assinaturas públicas são o **contrato** do grupo. Antes de mudar o nome,
  os parâmetros ou as exceções de um método ou construtor, avise os colegas.
- Métodos com `throw new UnsupportedOperationException("TODO: ...")` são os que
  faltam implementar. Getters e associações triviais já estão prontos.
- Cada classe tem **um único dono** (tabela abaixo). Para mudar a classe de
  outra pessoa, peça a ela ou abra um Pull Request.
- Entidades validam dados no construtor e lançam `DadosInvalidosException`;
  os catálogos lançam `CadastroException` (duplicado, não encontrado etc.).
  Nenhum método deve devolver `null` para indicar erro.

| Responsável | Pacotes / classes |
|---|---|
| Pessoa 1 — modelo e regras | `dados/*`, `excecoes/*`, `cadastro/Apuracao` |
| Pessoa 2 — catálogos e arquivos | `cadastro/Cadastro*`, `persistencia/*`, `aplicacao/*`, `Main` |
| Pessoa 3 — interface gráfica | `gui/*` |

## Fluxo no Git

- Este esqueleto é o primeiro commit da `main`. Depois, cada pessoa trabalha em
  sua branch (`feature/modelo`, `feature/catalogos`, `feature/gui`) e integra
  por Pull Request.
- Commits pequenos e `git pull --rebase` com frequência.

## Checklist do enunciado

- [ ] Todos os atributos `private`; evitar `static` (só `main`)
- [ ] Coleções da API Java, sem arrays (`[]`) para guardar objetos
- [ ] CRUD apenas nas classes `Cadastro*`
- [ ] Exceções tratadas: sem interrupção nem mensagem de erro da JVM
- [ ] Interface gráfica com as 14 opções
- [ ] Remoção lógica de candidato
- [ ] Java Code Conventions
- [ ] Relatório em PDF (capa, diagrama UML, coleções, persistência)
- [ ] Entrega individual no Moodle (30/11/2026) e apresentação

## Decisões em aberto

- Formato de persistência das opções 12 e 13 (CSV, TXT, JSON ou serialização)
- `listar()` de candidatos inclui os REMOVIDOS?
- Biblioteca gráfica: o esqueleto usa Swing
