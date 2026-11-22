# AvaSlate translation models

Translation models for the **AvaSlate** Android app, which translates speech on the phone, offline.
Each direction (for example `bg-en`, Bulgarian → English) is one
[release](https://github.com/iivp/avaslate-models/releases). The app downloads only the directions it needs,
from `https://github.com/iivp/avaslate-models/releases/download/<direction>/<file>`.

| File | What it is |
|---|---|
| `encoder.onnx` | Encoder, int8. It also computes each decoder layer's cross-attention keys and values. |
| `decoder.onnx` | One decoding step with a self-attention cache, int8. |
| `source.tsv` | The source-language SentencePiece model: `piece TAB score TAB type`. |
| `vocab.tsv` | Vocabulary: `piece TAB id`. |
| `pack.json` | Sizes, SHA-256 of every file, token ids, and the original model and revision. |

## Where they come from

These are [OPUS-MT](https://github.com/Helsinki-NLP/Opus-MT) models by **Helsinki-NLP, University of
Helsinki**, converted to ONNX and quantised to int8. Each `pack.json` names the original Hugging Face
repository (`Helsinki-NLP/opus-mt-…`) and the exact revision. Nothing was retrained.

When checked against the original PyTorch models with greedy decoding, most sentences come out
word for word the same. The others differ in small word choices because of int8.

## Licence

The OPUS-MT models are licensed **CC-BY 4.0**: you may use and share them, including commercially, if you
credit the authors:

> OPUS-MT, Helsinki-NLP (University of Helsinki), https://github.com/Helsinki-NLP/Opus-MT.
> Jörg Tiedemann and Santhosh Thottingal, "OPUS-MT — Building open translation services for the World",
> EAMT 2020.

The conversion is shared under the same CC-BY 4.0 licence.
