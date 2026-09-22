# Colossus TTS Voice

A Piper TTS voice for Colossus from *Colossus: The Forbin Project*.

## Production voice

The production voice is the Colossus v11 model exported from training epoch 5919.
It was selected as the best requested trained checkpoint in the fixed evaluation
battery:

- 56/75 exact Whisper matches
- Mean WER: 0.080206
- 75/75 valid generated WAV files
- Whisper diagnostic model: `large-v3`, CUDA, `float16`, VAD disabled
- Training data: 73 approved lines
- Piper quality: medium
- Sample rate: 22,050 Hz
- Language and phoneme voice: `en_US`, `en-us` espeak

The pretrained control scored higher on the automated battery, but epoch 5919
is the selected trained production voice. Human listening confirmed that the
apparent word drops reported for phrases 0030 and 0034 were false positives.

## Files

```text
voices/colossus-medium/
├── en_US-colossus-medium.onnx
├── en_US-colossus-medium.onnx.json
└── README.md
```

Keep the `.onnx` and matching `.onnx.json` files together. The JSON file
contains the model configuration required by Piper.

## Use with Piper

Install Piper by using the method for your platform. Then run:

```bash
printf '%s\n' 'This is the voice of Colossus.' | \
  piper \
    --model voices/colossus-medium/en_US-colossus-medium.onnx \
    --output_file colossus.wav
```

For a text file:

```bash
piper \
  --model voices/colossus-medium/en_US-colossus-medium.onnx \
  --output_file colossus.wav < input.txt
```

The default model settings are recorded in the companion JSON file. You can
adjust Piper's `--length-scale`, `--noise-scale`, and `--noise-w-scale` options
for a particular use.

## Provenance

This model comes from the reviewed Colossus v11 source revision and the
corrected full-audio, no-VAD training cache. The project retained the earlier
VAD-trimmed cache for diagnosis and did not use it for the production run.

The source project and evaluation evidence are maintained separately from this
small distribution repository.

## Licence

No licence is specified yet. Add a licence before redistributing this model.
