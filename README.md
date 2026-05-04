# BP Contract Data Repository

Samostatný repozitár pre dátové súbory k bakalárskej práci o predspracovaní slovenských právnych textov.

## Obsah

### `data/train_jan_2026`

Tréningový/pracovný korpus použitý pri vývoji pipeline a klasifikácii.

- `pdfs/` obsahuje PDF zmluvy z pracovného korpusu z januára 2026.
- `cleaned_txt_strict_valid/` obsahuje vyčistené texty dokumentov, ktoré prešli prísnou štruktúrnou kontrolou.
- `crz_exports/` obsahuje CRZ exporty z dátumov 1.1.2026, 2.1.2026 a 3.1.2026, vrátane spojeného exportu.
- `weak_labels/` obsahuje weak labels pre klasifikáciu a auditné súbory k ich kontrole.
- `manifests/` obsahuje manifesty použiteľných dokumentov.

Weak labels nie sú ručná ground truth anotácia. Boli odvodené deterministickými pravidlami z CRZ polí a titulnej časti dokumentu. Návrh kategórií a pravidiel bol pripravený s LLM asistenciou, skontrolovaný ďalším modelom a následne manuálne auditovaný.

### `data/test_extraction_jun_2025`

Ručne anotovaná testovacia množina pre extrakciu.

- `pdfs/` obsahuje PDF dokumenty ručne vybraného diverzifikovaného test setu.
- `txt/` obsahuje textové verzie tých istých dokumentov.
- `crz_exports/` obsahuje CRZ exporty a referenčné CRZ riadky pre test set.
- `annotations/` obsahuje ručnú ground truth anotáciu pre extrakciu a audit anotácie.
- `manifests/` obsahuje manifest vybraných testovacích dokumentov.

## Poznámky

- PDF súbory sú verejné dokumenty z Centrálneho registra zmlúv.
- XLSX a CSV anotácie sú určené na vyhodnocovanie extrakcie a klasifikácie.
- Ak sa repozitár bude pushovať na GitHub, je vhodné zvážiť Git LFS pre PDF súbory. V aktuálnom prostredí `git-lfs` nebol dostupný.
