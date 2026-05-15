# Handoff-prompt for ny studieøkt-session

Lim inn dette i en ny Claude Code-samtale når den forrige skal "cleares":

---

Jeg er Marcus, leser til eksamen i VOS4 / 15SPM (managerial economics).
Jeg har 15 spørsmål (Q01–Q15) i `notes/questions/` og ~45 teorifiler i `notes/theories/`.
Tidligere økter er oppsummert i `handoff/2026-05-14.md`.

**Vi gjør dette nå:** Jeg går gjennom notatene mine og stiller deg spørsmål om innhold jeg ikke skjønner. Du skal:

1. Slå opp i riktig fil (q-fil eller teorifil) før du svarer — bruk Read, ikke gjett.
2. Forklar **kort, konkret, og på en måte jeg lett kan huske** (gjerne en analogi). Ikke akademisk svada.
3. Loggfør hvert spm + svar i `notes/study_session_<dato>.md` med formatet:
   - **Spm:** ...
   - **Hvor:** q-fil/teorifil + linje
   - **Forklaring (Marcus-vennlig):** ...
   - **Husk:** 1–3 stikkord
4. **Token-disiplin (VIKTIG):** Jeg bryr meg om token-bruk.
   - Ikke les hele filer når et utdrag holder. Bruk `grep` / `offset+limit` på Read.
   - Ikke spawn Agent/subagents for forklaringer.
   - Korte svar. Ingen avsluttende oppsummering. Ingen gjentagelse av spørsmålet.
   - Loggfør komprimert i `notes/study_session_<dato>.md` (2–4 setninger + stikkord).
   - Varsle tidlig: etter ~6–8 spørsmål eller etter ett tungt fil-tungt spm, si: "Vi nærmer oss tokengrensa — clear nå?"
5. Når jeg sier jeg er ferdig for økten, oppdater `handoff/<dato>.md` med:
   - Hvilke spørsmål vi gikk gjennom
   - Hvilke konsepter jeg slet med
   - Hva som gjenstår

**Viktig:** Jeg snakker norsk. Svar på norsk. Vær kortfattet — jeg skal lese dette under tidspress på eksamen.

Start med å lese `handoff/2026-05-14.md` og siste `notes/study_session_*.md` for å se hvor vi slapp.
