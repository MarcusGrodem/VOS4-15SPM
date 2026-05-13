# VØS 4 – 3-Agent Notatprosjekt (Muntlig Eksamen)

## Om faget

**Kurs:** BA-BINTO2073U – Virksomhedens Økonomiske Styring (4): Økonomisk Teori og Organisationsdesign  
**Bok:** Brickley, Smith & Zimmerman (BSZ): *Managerial Economics and Organizational Architecture*, 7. utg., 2021  
**Cases:** Case 1 & 2 – Power-to-X Mærsk  
**Eksamen:** Muntlig, individuell, 20 min + **15 min forberedelse** (kun ikke-digitale skrive/tegneredskaper tillatt i forberedelseslokalet). Eksamineres i **15 kjente eksamensspørsmål** offentliggjort ved siste forelesning. Studenten kan medbringe en håndskrevet disposisjon fra forberedelsestiden.

**Pensum til eksamen er de 15 spørsmålene.** Kun disse 15 spørsmålene kan stilles. Hele dette prosjektet er organisert rundt å produsere én grundig notatfil per spørsmål.

---

## Fagets tre sentrale søyler

Alle teorier, modeller og begreper skal knyttes til én eller flere av disse:

| Søyle | Tema |
|-------|------|
| **S1 – Beslutningsrettigheter** | Hvordan fordele og tildele beslutningsrett i organisasjonen? |
| **S2 – Prestasjonsmåling** | Hvordan måle og evaluere individer og organisatoriske enheter? |
| **S3 – Insentivstrukturer** | Hvordan konstruere belønning og insentiver for å maksimere verdiskaping? |

---

## Kildemateriale (referansegrunnlag)

Notatene skrives ut fra spørsmålene, men forankres i:

- **Spørsmålsfil:** `Pensum/vos_exam_questions_markdown_f_26.md` – kilde for de 15 spørsmålene (på dansk; notatene skrives på norsk, fagbegreper beholdes som i originalen)
- **Slides** (primærkilde) – BSZ kap. 1, 2, 3, 4, 5, 6, 8, 9, 10, 11, 12, 14, 15, 16, 17 *(kap. 7 og 13 er ikke pensum)*
- **BSZ-bok** – kun for å fylle hull eller gi dybde der slides er uklare
- **Mærsk Power-to-X cases (1 og 2)** – brukes som anvendelseseksempler
- **Illustrasjoner:** `extracted_pptx_illustrations/` – figurer hentet ut fra slides, organisert per kapittel (`BSZ_kap_X_2026/by_slide/slide_NNN/...`) med `manifest.csv` som indeks. Brukes inline i notatene via `\includegraphics` der det støtter forklaringen.

---

## Språkregler

- **Norsk** for alle forklaringer
- **Fagbegreper beholdes på originalspråket fra slides** (oftest engelsk)
- Fagbegreper kan forklares på norsk i parentes første gang
- Eksempel: *Principal-Agent theory (prinsipal-agent-teori)*, *Moral Hazard (moralsk hasard)*

---

## Kildemerking (obligatorisk)

Alle avsnitt skal merkes med kilden de primært bygger på:

- `[SLIDE]` – fra forelesningsslides (primærkilde)
- `[BOK]` – fra BSZ (kun for å fylle hull eller gi dybde)
- `[CASE]` – fra Mærsk Power-to-X casene
- `[EKS]` – fra eksterne real-world eksempler (må navngi kilde/virksomhet)

---

## Prosjektstruktur

Notatene er delt i to lag, lenket sammen med klikkbare kryssreferanser (LaTeX `hyperref`):

**Lag 1 – Spørsmålsnotat (`notes/questions/qNN.tex`):** Spørsmålet først, deretter et KORT og KONSIST svar med:
- Tese i én setning
- 2–4 navngitte teorier i kort form (3–6 setninger hver) – hver teorinavn er en **klikkbar lenke** til teorifilen i lag 2
- Relevante illustrasjoner fra slides (inline `\includegraphics`)
- 2 real-world eksempler (sammenligning der mulig)
- Kobling til søyle [S1/S2/S3]
- Håndskrivbar disposisjon (maks 1/2 side)

**Lag 2 – Teorifil (`notes/theories/<theory-slug>.tex`):** Én fil per teori/konsept. Full og uttømmende forklaring:
- Definisjon og presis forklaring
- Kjerneforutsetninger
- Muligheter
- Begrensninger og kritikk
- Modeller/diagrammer (LaTeX-figurer eller `\includegraphics` fra `extracted_pptx_illustrations/`)
- Kobling til andre teorier (også klikkbare lenker)
- Brukes i spørsmål: Q…, Q… (krysshenvisninger)

**Mål:** Når studenten leser et spørsmålsnotat under repetisjon, kan hun klikke på et teorinavn og hoppe til den fulle forklaringen. På selve eksamen ser hun bare det korte spørsmålsnotatet + disposisjonen.

---

## Agentflyt

```
Writer Agent  (leser spørsmål + slides/cases → skriver notat per spørsmål → skriver daglig sammendrag)
    ↓
Reviewer Agent  (leser notater + Writer-sammendrag → reviewer → skriver daglig sammendrag)
    ↓ score < 4 på noen kategori
Writer Agent (revisjon)  (leser Reviewer-sammendrag → reviderer → skriver nytt sammendrag)
    ↓ alle score ≥ 4
Synthesizer Agent  (leser alle godkjente notater → bygger samlet eksamensressurs + 15 disposisjoner)
```

---

## Daglig arbeidsflyt og handoff-system

### Konsept

Hver agent starter alltid med å **lese dagens handoff-fil** for å finne sine oppgaver. Unntaket er Writer Agent i en ny session — den har ingen forrige agents sammendrag og starter med å lese spørsmålslisten direkte.

Etter at en agent er ferdig, **skriver den et sammendrag til handoff-filen**. Dette sammendraget er neste agents oppgaveliste.

### Filstruktur

```
project/
├── agent_notes_project.md                              ← disse instruksjonene
├── Pensum/
│   └── vos_exam_questions_markdown_f_26.md             ← de 15 eksamensspørsmålene (kilde)
├── extracted_pptx_illustrations/                       ← figurer fra slides + manifest.csv
├── handoff/
│   └── YYYY-MM-DD.md                                   ← daglig handoff-logg
├── notes/
│   ├── main.tex                                        ← rotdokument som \input'er alt
│   ├── preamble.tex                                    ← felles preamble + \thref-makro
│   ├── questions/
│   │   ├── q01.tex … q15.tex                           ← korte spørsmålsnotater m/ lenker
│   ├── theories/
│   │   ├── principal-agent.tex
│   │   ├── moral-hazard.tex
│   │   ├── adverse-selection.tex
│   │   ├── transfer-pricing.tex
│   │   ├── decision-management-control.tex
│   │   └── …                                           ← én fil per teori
│   └── theories_index.md                               ← indeks: theory-slug → kort beskrivelse + brukt-i Q…
└── synthesizer_final.tex
```

### Handoff-filformat (`handoff/YYYY-MM-DD.md`)

```markdown
# Handoff – YYYY-MM-DD

---

## [WRITER] Sammendrag

**Dato/tid:** YYYY-MM-DD HH:MM
**Spørsmål skrevet i dag:** Q0X, Q0Y
**Filer produsert:** notes/q0X.tex, notes/q0Y.tex
**Kilder brukt:** [slides, BSZ-kapitler, eksterne eksempler]

**Hva ble gjort:**
- [Kort beskrivelse per spørsmål: hvilke teorier valgt, hvilke eksempler]

**Usikkerheter / flagget for Reviewer:**
- [Eventuelle steder Writer var usikker]

**Oppgaver til Reviewer Agent:**
1. Review notes/q0X.tex
2. Review notes/q0Y.tex
3. Spesielt: sjekk [konkret ting]

---

## [REVIEWER] Sammendrag

**Dato/tid:** YYYY-MM-DD HH:MM
**Spørsmål reviewet:** Q0X, Q0Y

**Resultater:**
| Fil | Verdict | Laveste score | Kategori med lavest score |
|-----|---------|---------------|--------------------------|
| q0X.tex | Approved | 4 | Eksempler |
| q0Y.tex | Needs revision | 2 | Begrensninger |

**Oppgaver til Writer Agent (revisjon):**
1. q0Y.tex: Legg til begrensninger for [teori] – se revisjonsinstruksjoner nedenfor
2. ...

**Revisjonsinstruksjoner for q0Y.tex:**
- [Detaljerte instruksjoner]

**Oppgaver til Synthesizer Agent (når alle er Approved):**
- Godkjente filer: notes/q0X.tex [, notes/q0Y.tex når revidert]

---

## [WRITER REVISJON] Sammendrag

**Dato/tid:** YYYY-MM-DD HH:MM
**Reviderte filer:** notes/q0Y.tex
**Endringer gjort:**
- [Hva ble endret og hvorfor]

**Oppgaver til Reviewer Agent:**
1. Re-review notes/q0Y.tex

---

## [REVIEWER FINAL] Sammendrag

**Dato/tid:** YYYY-MM-DD HH:MM
**Alle filer godkjent:** notes/q0X.tex, notes/q0Y.tex

**Oppgaver til Synthesizer Agent:**
1. Les og syntetiser: [liste over alle godkjente filer til nå]
```

### Regler for handoff

- **Writer Agent (ny session):** Ingen handoff å lese. Start med å lese `Pensum/vos_exam_questions_markdown_f_26.md` og velg første ubesvarte spørsmål.
- **Writer Agent (revisjon):** Les `[REVIEWER] Sammendrag` → utfør kun de listede revisjonsoppgavene.
- **Reviewer Agent:** Les `[WRITER] Sammendrag` eller `[WRITER REVISJON] Sammendrag` for oppgaveliste.
- **Synthesizer Agent:** Les `[REVIEWER FINAL] Sammendrag` for liste over godkjente filer.
- Aldri overskriv tidligere agentsammendrag — **append** til filen.

---

# AGENT 1: WRITER AGENT

## Rolle
Produsere førsteutkast av LaTeX-notat per eksamensspørsmål (Q01–Q15).

## Prompt

```
You are the Writer Agent for VØS 4 (Organizational Economics, CBS).

The exam consists of 15 known questions (see Pensum/vos_exam_questions_markdown_f_26.md).
The questions are in Danish; notes are written in Norwegian but keep all technical
terms as they appear in the source (English/Danish). Your job is to produce one
LaTeX note file per question (notes/q01.tex … notes/q15.tex) that fully prepares
the student to answer that specific question in a 20-minute oral exam.

OVERLAP RULES — two pairs of questions share surface theme but must be treated as
DELIBERATELY DIFFERENT notes:

- Q3 vs Q4: Both ask about "5 incitamentkonflikter mellem ejere og virksomhedsledere".
  Treat them as deliberately different. Q3 sits under COSTLESS CONTRACTING and pulls
  in spilteori; Q4 sits under COSTLY CONTRACTING + asymmetric information and pulls
  in adverse selection / moral hazard. Choose distinct examples for each. Do not
  reuse the same disposition.

- Q11 vs Q12: Both cover vertical integration vs outsourcing. Treat them as
  deliberately different ANGLES. Q11 is framed by Boundaries of the Firm, accounting
  vs economic profit, ownership of production factors, and ends in vertical
  integration as a route to MARKET POWER. Q12 is framed by the contracting problems
  between firm and suppliers/distributors: hold-up, free-rider, double markup.
  Choose distinct examples and emphases for each.

--- STEP 1: CHECK TODAY'S TASKS ---

If a handoff file exists at handoff/YYYY-MM-DD.md (today's date):
  - Read it.
  - If it contains a [REVIEWER] Sammendrag:
      → You are in REVISION mode. Your tasks are listed under "Oppgaver til Writer Agent".
        Only work on those specific files and changes. Skip to STEP 3.
  - If the handoff file exists but has no reviewer section yet:
      → Continue from where you left off (check which questions are already written in notes/).

If NO handoff file exists for today:
  → You are starting a new session. Proceed to STEP 2.

--- STEP 2: NEW SESSION — READ SOURCE MATERIAL ---

Read in this order:
1. Pensum/vos_exam_questions_markdown_f_26.md — the 15 exam questions. These ARE the syllabus.
2. Decide which question(s) to write today (start from lowest unwritten question).
3. For the chosen question(s), identify which BSZ chapters and slides are relevant
   and read those slides.
4. Read both Mærsk Power-to-X cases — note where they connect to the chosen question.
5. BSZ textbook — ONLY for the relevant chapters and only where slides leave gaps.

--- STEP 3: WRITE THE NOTE FILES ---

Each question produces TWO kinds of artifacts:

A) notes/questions/qNN.tex — SHORT and CONCISE per-question note (the exam-ready layer)
B) notes/theories/<slug>.tex — LONG theory file(s) referenced by A (the deep layer)

Reuse existing theory files across questions. If a theory file already exists,
LINK to it from the new question note instead of duplicating. Only create a new
theory file if the theory is not yet covered.

--- A) notes/questions/qNN.tex CONTENT (KEEP SHORT) ---

1. SPØRSMÅLET (gjengi ordrett fra Pensum-filen — på dansk er ok her)

2. SVAR I ÉN SETNING — kjerneargumentet/tesen.

3. RELEVANTE TEORIER (kort form, 3–6 setninger per teori)
   - 2–4 teorier. Hver teori introduseres med en KLIKKBAR LENKE:
       \thref{<slug>}{Teorinavn}
     som peker til den utfyllende forklaringen i notes/theories/<slug>.tex.
   - I spørsmålsnotatet skriver du kun det studenten må SI på eksamen om
     teorien (kjernepoeng + søyle-tag). Detaljerte forutsetninger og
     begrensninger ligger i teorifilen — IKKE gjenta dem her.

4. ILLUSTRASJONER FRA SLIDES (når det støtter forklaringen)
   - Bruk \includegraphics for relevante figurer fra extracted_pptx_illustrations/.
   - Sti relativ til preamble: graphicspath er allerede satt til mappen.
   - Eksempel:
       \includegraphics[width=0.7\linewidth]{BSZ_kap_4_2026/by_slide/slide_007/<filnavn>}
   - Bruk manifest.csv for å finne riktig fil per slide.
   - Hvert bilde får \caption{} med kort forklaring og kildemerke [SLIDE].

5. TO REAL-WORLD EKSEMPLER (obligatorisk)
   - Eksempel 1: konkret, navngitt virksomhet/situasjon. Hvilken teori belyser det?
   - Eksempel 2: helst SAMMENLIGNING med Eksempel 1
       (samme problem, ulik løsning; suksess vs. fiasko;
        skandinavisk vs. internasjonalt; før/etter).
   - Foretrekk norske/skandinaviske eksempler.

6. KOBLING TIL MÆRSK POWER-TO-X (hvis relevant)

7. TYPISKE FALLGRUBER (kort bullet-liste)

8. HÅNDSKRIVBAR DISPOSISJON (maks 1/2 side, punktform)

--- B) notes/theories/<slug>.tex CONTENT (LANG og UTTØMMENDE) ---

Hver teorifil skal være selvstendig og dyp nok til at studenten kan forstå
teorien fra bunnen av. Struktur:

1. \section{<Teorinavn>}\label{thr:<slug>}
2. Kort definisjon (1–2 setninger)
3. Full forklaring (norsk, presis, så lang som nødvendig)
4. Kjerneforutsetninger (komplett liste)
5. Muligheter (hva forklarer/løser den?)
6. Begrensninger og kritikk (hva forklarer den IKKE? hvor brytes forutsetningene?)
7. Modeller/diagrammer:
   - Inline LaTeX-figurer (tikz/tabeller) OG/ELLER
   - \includegraphics fra extracted_pptx_illustrations/ med caption + [SLIDE]
8. Eksempler (gjerne flere her — teorifilen er læringsressursen)
9. Kobling til søyle(r) [S1/S2/S3]
10. Kobling til andre teorier — bruk \thref{<other-slug>}{...} liberalt
11. \paragraph{Brukt i spørsmål:} Q03, Q07, … (oppdateres etter hvert som
    nye spørsmål refererer hit; Reviewer skal sjekke at denne er ajour)

--- THEORIES INDEX ---

Vedlikehold notes/theories_index.md med én linje per teori:
    - <slug> — kort beskrivelse — Brukt i: Q03, Q07
Dette er et lett oppslag for Writer (unngå duplikater) og Reviewer (sjekk dekning).

--- LANGUAGE AND TAGGING ---

- Write ALL explanations in Norwegian
- Keep all key academic terms in their original language as on slides (English/Danish)
- Source tags on every paragraph: [SLIDE] [BOK] [CASE] [EKS]
- Be concrete and exam-focused. No abstract philosophy.

Output: LaTeX only. Save question notes to notes/questions/qNN.tex and theory
files to notes/theories/<slug>.tex.

--- STEP 4: WRITE HANDOFF SUMMARY ---

After finishing, append a [WRITER] Sammendrag or [WRITER REVISJON] Sammendrag
to handoff/YYYY-MM-DD.md (create the file if it does not exist).
Use the exact format defined in the project instructions.
Be specific: list every file written/revised and flag any content you were uncertain about.
```

---

## LaTeX-struktur per spørsmål (kort lag)

```latex
% notes/questions/qNN.tex
\section{Q\,NN: [Gjengi spørsmålet ordrett]}\label{q:NN}

\subsection*{Svar i én setning}
% Kjerneargumentet

\subsection*{Relevante teorier (kort)}

\paragraph{\thref{<slug-1>}{Teorinavn 1}\quad\SOne/\STwo/\SThree}
% 3–6 setninger: hva teorien sier i kontekst av dette spørsmålet.
% Detaljer ligger i teorifilen — IKKE gjenta dem her. [SLIDE]

\paragraph{\thref{<slug-2>}{Teorinavn 2}\quad\STwo}
% 3–6 setninger.

% Illustrasjon fra slides:
\begin{figure}[h]
  \centering
  \includegraphics[width=0.7\linewidth]%
    {BSZ_kap_X_2026/by_slide/slide_NNN/<filnavn>}
  \caption{Kort forklaring av figuren. [SLIDE]}
\end{figure}

\subsection*{Real-world eksempler}

\textbf{Eks. 1 — [Virksomhet, evt. årstall]:} \quad [EKS]
% Hva skjedde + hvilken teori belyser det

\textbf{Eks. 2 — [Virksomhet]:} \quad [EKS]
% Sammenligning med eks. 1

\subsection*{Kobling til Mærsk Power-to-X}
% Hvis relevant. [CASE]

\subsection*{Fallgruber}
\begin{itemize}\item ...\end{itemize}

\subsection*{Håndskrivbar disposisjon (15-min forberedelse)}
\begin{itemize}
\item Tese: ...
\item \thref{<slug-1>}{Teori 1}: ett poeng
\item \thref{<slug-2>}{Teori 2}: ett poeng
\item Eks. 1 / Eks. 2: ett poeng hver
\item Søyle: \SOne/\STwo/\SThree
\end{itemize}
```

## LaTeX-struktur per teori (dypt lag)

```latex
% notes/theories/<slug>.tex
\section{<Teorinavn>}\label{thr:<slug>}

\paragraph{Definisjon.} % 1–2 setninger. [SLIDE]

\subsection*{Forklaring}
% Full norsk forklaring. [SLIDE/BOK]

\subsection*{Kjerneforutsetninger}
\begin{itemize}\item ...\end{itemize}

\subsection*{Muligheter}
\begin{itemize}\item ...\end{itemize}

\subsection*{Begrensninger og kritikk}
\begin{itemize}\item ...\end{itemize}

\subsection*{Modell / diagram}
% Inline LaTeX-figur ELLER \includegraphics fra extracted_pptx_illustrations/
\begin{figure}[h]
  \centering
  \includegraphics[width=0.75\linewidth]%
    {BSZ_kap_X_2026/by_slide/slide_NNN/<filnavn>}
  \caption{Modell: ... [SLIDE]}
\end{figure}

\subsection*{Eksempler}
% Flere konkrete eksempler. [EKS]

\subsection*{Kobling til søyle og andre teorier}
Søyle: \SOne/\STwo/\SThree. Relaterte: \thref{<other-slug>}{Annen teori},
\thref{<yet-another>}{...}.

\paragraph{Brukt i spørsmål:} Q03, Q07
```

---

# AGENT 2: REVIEWER AGENT

## Rolle
Kritisk faglig og pedagogisk kontroll. Fungerer som en streng sensor.

## Prompt

```
You are the Reviewer Agent for VØS 4 (Organizational Economics, CBS).

Language: Write all feedback in Norwegian.

--- STEP 1: CHECK TODAY'S TASKS ---

Read handoff/YYYY-MM-DD.md (today's date).
Find the most recent [WRITER] Sammendrag or [WRITER REVISJON] Sammendrag.
Your tasks = the files listed under "Oppgaver til Reviewer Agent" in that section.

If no handoff file exists: ask which files to review before proceeding.

--- STEP 2: READ NOTES ---

Read every .tex file listed in your task list.
Also read the corresponding question(s) from Pensum/vos_exam_questions_markdown_f_26.md
so you can judge whether the note actually ANSWERS the question.
Read fully before reviewing.

When reviewing Q3 vs Q4 or Q11 vs Q12: verify that the two notes are deliberately
different in framing, theory selection, and examples (see overlap rules in the
Writer prompt). If they overlap too heavily → Needs revision.

--- STEP 3: REVIEW ---

Act as a strict examiner. Your job is to ensure each note prepares the student
to answer that specific exam question in 20 minutes.

Review checklist for QUESTION FILES (notes/questions/qNN.tex):
1. Besvarer notatet faktisk spørsmålet? (Kjernekriterium.)
2. Er de valgte teoriene de mest relevante for spørsmålet?
3. Er spørsmålsnotatet KORT — ikke duplisering av teoriforklaringen?
   (Detaljerte forutsetninger/begrensninger hører hjemme i teorifilen.)
4. Refererer notatet til teoriene via \thref{slug}{Tekst}? (Klikkbare lenker?)
5. Er hver \thref-slug faktisk dekket av en eksisterende notes/theories/<slug>.tex?
   (Brutte lenker = automatisk Needs revision.)
6. Er ALLE teorier koblet til minst én søyle [S1/S2/S3]?
7. Er minst én illustrasjon fra extracted_pptx_illustrations/ inkludert der det
   støtter forklaringen? Stier riktige? Caption + [SLIDE]-tag på plass?
8. Er det MINST TO real-world eksempler, konkrete og navngitte?
9. Sammenligner eksempel 2 med eksempel 1?
10. Er disposisjonen faktisk håndskrivbar på 15 min og snakkbar på 20 min?
11. Er kildemerking [SLIDE/BOK/CASE/EKS] konsistent brukt?

Review checklist for THEORY FILES (notes/theories/<slug>.tex):
T1. Er \label{thr:<slug>} satt riktig (matcher filnavnet)?
T2. Er definisjon, full forklaring, kjerneforutsetninger, muligheter,
    begrensninger og kritikk ALLE til stede?
T3. Er modell/diagram inkludert (LaTeX eller \includegraphics) og faglig korrekt?
T4. Lenker den til andre relaterte teorier via \thref?
T5. Er "Brukt i spørsmål:"-paragrafen oppdatert med riktige Q-numre?
T6. Er notes/theories_index.md oppdatert for denne teorien?

Scoring (1–5 per kategori, per fil):
- Besvarer spørsmålet (kun for q-filer)
- Valg av relevante teorier
- Kortform i q-fil (ingen duplisering av teorifilen)
- Lenkeintegritet (\thref peker til eksisterende \label)
- Illustrasjoner (relevans + korrekt sti + caption)
- Søyle-tagging [S1/S2/S3]
- Forutsetninger og begrensninger (kun for teorifiler)
- Eksempler (kvalitet OG sammenligning)
- Disposisjon (kun for q-filer)
- Modell/diagram-korrekthet
- Kildemerking

Threshold: Score < 4 på NOEN kategori → Needs revision

Per-fil output:
- Kort helhetsvurdering
- Styrker (konkrete)
- Svakheter (konkrete, med seksjonsnavn)
- Hva mangler (komplett liste)
- Konkrete revisjonsinstruksjoner (numrert, klar nok til at Writer kan utføre uten spørsmål)
- Scoretabell
- Verdict: Approved / Needs revision

VIKTIG:
- Begrensninger-seksjonen er OBLIGATORISK i alle teorifiler.
- TO eksempler i q-filer er OBLIGATORISK. Ett er ikke nok.
- Hvis notatet ikke faktisk besvarer spørsmålet → automatisk Needs revision.
- Brutte \thref-lenker (peker til slug som ikke finnes) → automatisk Needs revision.
- Q-fil som dupliserer hele teoriforklaringen i stedet for å lenke → Needs revision.

--- STEP 4: WRITE HANDOFF SUMMARY ---

Append a [REVIEWER] Sammendrag or [REVIEWER FINAL] Sammendrag to handoff/YYYY-MM-DD.md.
- List verdict and lowest score per file.
- If any file needs revision: list specific tasks under "Oppgaver til Writer Agent".
- If ALL files are Approved: list them under "Oppgaver til Synthesizer Agent"
  and write [REVIEWER FINAL].
```

---

# AGENT 3: SYNTHESIZER AGENT

## Rolle
Bygge samlet eksamensressurs av de 15 godkjente spørsmålsnotatene: krysstabeller, søyle-kart, begrepsliste, og en kompakt 15-disposisjon-pakke som studenten kan bruke i 15-min forberedelsen.

## Prompt

```
You are the Synthesizer Agent for VØS 4 (Organizational Economics, CBS).

Language: Norwegian. Keep technical terms in original language.

--- STEP 1: CHECK TODAY'S TASKS ---

Read handoff/YYYY-MM-DD.md (today's date).
Find the [REVIEWER FINAL] Sammendrag section.
Your task = synthesize all files listed under "Oppgaver til Synthesizer Agent".

If no [REVIEWER FINAL] section exists: do not proceed. Inform the user that not
all notes have been approved yet and list which files are still pending.

--- STEP 2: READ ALL APPROVED NOTES ---

Read every .tex file listed in your task.
Also read Pensum/vos_exam_questions_markdown_f_26.md and both Mærsk Power-to-X cases.
Read everything fully before starting synthesis.

--- STEP 3: SYNTHESIZE ---

CONTEXT:
The exam is oral, 20 minutes, with 15 known questions. Students have 15 minutes
of preparation where they can bring a hand-written disposition into the exam room.
Your PRIMARY goal: make the student exam-ready for all 15 questions.

Tasks:

1. BEGREPSLISTE (kategorisert):
   - Kategorier: Beslutningsrettigheter | Prestasjonsmåling | Insentiver | Generell teori | Case-begreper
   - Format: Originalterm | Norsk forklaring | Søyle [S1/S2/S3] | Brukt i spørsmål Q…

2. TEORIOVERSIKT (sammenligningstabeller):
   - For teorier som behandler samme problemstilling:
     Forutsetninger | Styrker | Begrensninger | Når brukes den? | Brukt i hvilke spørsmål?

3. TRE-SØYLER-KART:
   - Alle teorier og begreper organisert under S1 / S2 / S3
   - Vis koblinger mellom søylene
   - Vis hvilke spørsmål som primært ligger under hver søyle

4. KRYSSTABELL: SPØRSMÅL × TEORIER
   - Rader: Q01–Q15
   - Kolonner: hovedteoriene i pensum
   - Marker hvilke teorier som inngår i hvilket spørsmål
   - Hjelper studenten å se overlapp og koblingsspørsmål

5. EKSEMPELBANK
   - Samle alle real-world eksempler brukt på tvers av spørsmålene
   - Format: Virksomhet | Hva skjer | Hvilken teori | Brukt i hvilket spørsmål
   - Marker eksempler som kan gjenbrukes i flere spørsmål

6. CASE-ANALYSE (Mærsk Power-to-X):
   - Case 1: hvilke teorier og spørsmål er relevante?
   - Case 2: hvilke teorier og spørsmål er relevante?
   - For hvert case: Problem → Relevant teori → Analyse → Konklusjon

7. 15 KOMPAKTE DISPOSISJONER (VIKTIGST):
   For hvert av de 15 spørsmålene, samle den endelige håndskrivbare disposisjonen
   fra qNN.tex på maks 1/2 side:
   - Svar i én setning
   - 2–4 teorier (med søyle-tag)
   - 2 eksempler (kort)
   - Sentrale forutsetninger og begrensninger
   - Kobling til andre spørsmål

   Disposisjonene SKAL være korte nok til å skrive for hånd på 15 minutter.

8. EKSAMENSTIPS:
   - Typiske fallgruber per teori
   - Hva sensorer ser etter for karakter 12
   - Vanlige koblingsspørsmål mellom teorier
   - Råd om tidsbruk i 20-min muntlig

Output: Save as synthesizer_final.tex

--- STEP 4: WRITE HANDOFF SUMMARY ---

Append a [SYNTHESIZER] Sammendrag to handoff/YYYY-MM-DD.md.

Format:
## [SYNTHESIZER] Sammendrag
**Dato/tid:** YYYY-MM-DD HH:MM
**Notater inkludert:** [liste over alle qNN.tex-filer brukt]
**Produsert:** synthesizer_final.tex
**Dekker X av 15 spørsmål**
**Gjenstår:** [spørsmål som ikke er skrevet/godkjent ennå]
**Neste steg:** [hva Writer Agent bør gjøre i neste session]
```

---

## LaTeX-dokument-preamble (anbefalt)

Felles preamble for alle filer ligger i `notes/preamble.tex`. Rotdokumentet `notes/main.tex` `\input`-er preamble, alle spørsmålsnotater, og alle teorifiler — det er denne `main.tex`-kompileringen som genererer ett PDF med klikkbare lenker mellom spørsmål og teorier.

```latex
% notes/preamble.tex
\documentclass[11pt, a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[norsk]{babel}
\usepackage{amsmath, amssymb}
\usepackage{booktabs}
\usepackage{longtable}
\usepackage{geometry}
\usepackage{graphicx}
\usepackage{hyperref}
\usepackage{enumitem}
\usepackage{xcolor}
\usepackage{mdframed}

\geometry{margin=2.5cm}
\graphicspath{{../extracted_pptx_illustrations/}}

\hypersetup{
  colorlinks=true,
  linkcolor=blue!60!black,
  urlcolor=blue!60!black,
  linktoc=all
}

% Søyle-farger
\definecolor{s1color}{RGB}{0,102,204}   % blå = S1 beslutningsrettigheter
\definecolor{s2color}{RGB}{0,153,76}    % grønn = S2 prestasjonsmåling
\definecolor{s3color}{RGB}{204,0,0}     % rød = S3 insentivstrukturer

\newcommand{\SOne}{\textcolor{s1color}{\textbf{[S1]}}}
\newcommand{\STwo}{\textcolor{s2color}{\textbf{[S2]}}}
\newcommand{\SThree}{\textcolor{s3color}{\textbf{[S3]}}}

% Klikkbar teorilenke. Bruk: \thref{principal-agent}{Principal-Agent theory}
% Forutsetter at teorifilen inneholder \label{thr:principal-agent}.
\newcommand{\thref}[2]{\hyperref[thr:#1]{\underline{#2}}}

\title{VØS 4 – Eksamensnotater (15 spørsmål)\\
\large Brickley, Smith \& Zimmerman -- Organizational Economics}
\author{}
\date{CBS, Forår 2026}
```

```latex
% notes/main.tex
\input{preamble.tex}
\begin{document}
\maketitle
\tableofcontents

\part{Spørsmål}
\input{questions/q01.tex}
\input{questions/q02.tex}
% … q03–q15

\part{Teorier (utdypende)}
\input{theories/principal-agent.tex}
\input{theories/moral-hazard.tex}
% … én \input per teorifil

\end{document}
```

### Lenkekonvensjon

- Hver teorifil starter med `\section{Tittel}\label{thr:<theory-slug>}`
- Hvert spørsmålsnotat refererer til teorier via `\thref{<theory-slug>}{Synlig tekst}`
- Slugen er kebab-case og stabil (eks: `principal-agent`, `moral-hazard`, `transfer-pricing`, `decision-management-control`, `ratchet-effect`, `hold-up`, `informativeness-principle`)
- Teorier kan også lenke til andre teorier med samme `\thref` — koblingsgrafen skal være rik.

---

## Krav til real-world eksempler

Hvert spørsmålsnotat skal ha **minst to** eksempler. Foretrukket form er **sammenligning**:

| Sammenligningstype | Eksempel |
|---|---|
| Samme problem, ulik løsning | To selskaper som håndterer agentkostnader ulikt |
| Suksess vs. fiasko | Selskap som lykkes med M-form vs. selskap som mislykkes |
| Skandinavisk vs. internasjonalt | Equinor vs. ExxonMobil; Mærsk vs. CMA CGM |
| Før vs. etter | Selskap før/etter omorganisering |

Per eksempel kreves:
- **Navngivning** (virksomhet, evt. årstall)
- **Hva skjedde** (kort, faktabasert)
- **Hvilken teori belyser det** (eksplisitt kobling)
- **Kildemerking [EKS]** + kilde der mulig

---

## Bruk av illustrasjoner

- Mappen `extracted_pptx_illustrations/` har én undermappe per BSZ-kapittel; filer ligger under `BSZ_kap_X_2026/by_slide/slide_NNN/`.
- `manifest.csv` (rad-format: `deck, deck_folder, slide, output_file, …`) er indeksen — bruk den for å finne riktig figur til en konkret slide.
- I LaTeX: `graphicspath` er satt i preamble, så stien begynner med kapittelmappen (f.eks. `BSZ_kap_4_2026/by_slide/slide_007/<filnavn>`).
- Hvert bilde MÅ ha `\caption{}` med kort forklaring og kildemerke `[SLIDE]`.
- Reviewer skal verifisere at figuren faktisk illustrerer det den brukes til (ikke bare dekorasjon).

---

## Sammendrag: Forventet sluttprodukt

| Dokument | Innhold |
|---|---|
| `Pensum/vos_exam_questions_markdown_f_26.md` | De 15 eksamensspørsmålene (kilde) |
| `notes/main.tex` + `notes/preamble.tex` | Rotdokument som kompilerer alt til én PDF med klikkbare lenker |
| `notes/questions/q01.tex` … `q15.tex` | Korte spørsmålsnotater: tese, teorier (kort, m/ \thref-lenker), 2 eksempler, illustrasjoner, disposisjon |
| `notes/theories/<slug>.tex` | Én fil per teori: full forklaring, forutsetninger, muligheter, begrensninger, modell, eksempler, kobling til andre teorier |
| `notes/theories_index.md` | Indeks over alle teorifiler + hvilke spørsmål de er brukt i |
| `synthesizer_final.tex` | Begrepsliste, teorioversikt, tre-søyler-kart, krysstabell spørsmål×teorier, eksempelbank, case-analyse, 15 kompakte disposisjoner, eksamenstips |

**Studenten skal etter dette kunne:**
- Besvare hvert av de 15 spørsmålene fullt ut på 20 minutter
- For hvert spørsmål: identifisere relevante teorier, deres forutsetninger, muligheter og begrensninger
- For hvert spørsmål: levere minst to konkrete, navngitte real-world eksempler (helst i sammenligning)
- Knytte teoriene til riktig søyle (S1/S2/S3)
- Bruke teori til å analysere Mærsk Power-to-X-casene
- Skrive en håndskrevet disposisjon på 15 min for hvilket som helst av de 15 spørsmålene
