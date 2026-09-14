# Restoring `P1-human-readable-FINAL.pdf`

GitHub does not accept individual files larger than 100 MB. The original lossless PDF is stored here as two sequential parts:

- `P1-human-readable-FINAL.pdf.part-aa`
- `P1-human-readable-FINAL.pdf.part-ab`

The SHA-256 checksum for each part is in `P1-human-readable-FINAL.pdf.parts.sha256`.

Restore the PDF with:

```sh
cat P1-human-readable-FINAL.pdf.part-aa P1-human-readable-FINAL.pdf.part-ab > P1-human-readable-FINAL.pdf
```
