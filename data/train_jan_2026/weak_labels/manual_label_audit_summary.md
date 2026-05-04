# January 405 Label Audit - 2026-05-01

Authoritative output folder: `/Users/kazimir/Desktop/BP/outputs/weak_label_classification_2026-05-01_jan405_current_rules_audit_v7`

## What Was Checked

- Regenerated labels for all 405 strict-valid January documents using current CRZ + document-title rules.
- Compared each weak label against the document title/front matter.
- Manually inspected all title/label disagreements and the full residual `other` bucket.
- Checked the classifier predictions against the audited weak labels.

## Result

I did not find a remaining clear wrong weak label after the final rule fixes. The saved label file to use is:

`/Users/kazimir/Desktop/BP/outputs/weak_label_classification_2026-05-01_jan405_current_rules_audit_v7/labels_all_documents.csv`

The remaining 8 title-signal disagreements are all cemetery contracts where the first title line says only `Zmluva o nájme`, but CRZ and/or the following document text specify `hrobove miesto`. I kept them as `hrobove_miesto`.

The residual `other` class has 52 documents. I checked the titles; they are mainly categories outside the current taxonomy: darovacia zmluva, výpožička, vecné bremeno, delimitačný protokol, zverenie majetku do správy, spoločný obecný úrad, zámenná zmluva, and similar.

## Class Distribution

| weak_category | count |
| --- | --- |
| najom | 92 |
| hrobove_miesto | 72 |
| other | 52 |
| dodatok | 43 |
| sluzby | 32 |
| dotacia | 23 |
| ramcova | 22 |
| spolupraca | 21 |
| prispevok | 13 |
| ukoncenie | 8 |
| dohoda_ine | 8 |
| kupa_predaj | 7 |
| kolektivna | 4 |
| dielo | 3 |
| energie | 2 |
| licencia_autorske | 2 |
| splatky_dlh | 1 |

## Classification Metrics

Best model: `tfidf_surface_logreg`

- Evaluated documents: 370 / 405
- Evaluated classes: 9
- Accuracy: 0.9785
- Macro F1: 0.9599
- Weighted F1: 0.9770

Important: `best_model_predictions_all_documents.csv` is not a replacement for the labels. The stable evaluation excludes classes with fewer than 10 examples. Therefore rare-class predictions in the all-document prediction file are expected to be wrong or collapsed into common classes.

## Prediction Audit

- All-document prediction mismatches vs weak labels: 37
- Rare-class mismatches caused by excluded classes: 35
- Stable-class model errors after manual check: 2

Stable-class model errors:

| contract_id | weak_category | predicted_category | crz_predmet |
| --- | --- | --- | --- |
| 11817741 | spolupraca | sluzby | Zmluva o spolupráci |
| 11818725 | spolupraca | sluzby | Zmluva o spolupráci pri zabezpečení umeleckého vystúpenia |

## Files Written

- `document_title_label_audit.csv`: all 405 labels with title-derived signal.
- `document_title_label_disagreements.csv`: the 8 remaining reviewed disagreements.
- `manual_edge_case_audit.csv`: manual decisions for remaining edge cases and stable prediction errors.
- `manual_label_audit_summary.md`: this report.
