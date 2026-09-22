# Colossus TTS Voice

A Piper TTS voice for Colossus from *Colossus: The Forbin Project*.

## Production voice
- Piper quality: medium
- Sample rate: 22,050 Hz
- Language and phoneme voice: `en_US`, `en-us` espeak

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
