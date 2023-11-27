# Voice Cloning and Lip Syncing Process

## Voice Cloning

### 1. Data Preparation:
- **Get Audio:** Record or download a long audio file of the person speaking.
- **Generate Subtitles:** Create subtitles for the audio.
- **Process Audio:** Prepare WAV files and a TOC to map subtitles to durations of the WAV file. Then, split and label the WAV files.

### 2. Training Tacotron2:
- **Model Training:** Feed the prepared data into Tacotron2 to train it on generating spectrums.

### 3. Wavenet Synthesis:
- **Spectrum Processing:** Use the generated spectrums and pre-downloaded weights, and feed them into Wavenet.
- **Voice Generation:** Prompt Wavenet to synthesize the voice to say desired phrases.

_Default Model for Training: LG Speech, trained on a nonfictional reading of 24 hours._

### Other Approaches

### 1. Real-Time Cloning:

- **Try Real-Time Cloning:** For efficient voice cloning, consider using [Real-Time Voice Cloning](https://github.com/CorentinJ/Real-Time-Voice-Cloning).

### 2. Voice Cloning Apps:
- [Voice AI Voice Changer Clone](https://apps.apple.com/us/app/voice-ai-voice-changer-clone/id6446296700)
- [Voice Face Cloning - Clony AI](https://apps.apple.com/us/app/voice-face-cloning-clony-ai/id6445868360)
- [Voice AI Clone Generator](https://apps.apple.com/us/app/voice-ai-clone-generator/id6450326506)

### 3. Online Voice Cloning Services(they are pretty bad and low-quality):
- [Play.ht Voice Cloning](https://play.ht/voice-cloning/)
- [Speechify Voice Cloning](https://speechify.com/voice-cloning/?landing_url=https%3A%2F%2Fspeechify.com%2Fvoice-cloning%2F)

## Lip Syncing

### 1. Video and Voice Processing:
- **Syncing Tool:** Use [Wav2Lip](https://github.com/Rudrabha/Wav2Lip) to synchronize the video with the voice.
- **Output Quality:** The resulting file might be of lower quality.

### 2. GAN Inference for Video Enhancement:
- **Frame Processing:** Split the video frames and feed them into GPFGAN.
- **Video Upscaling:** Enhance the video quality by upscaling.

## Further Fine-Tuning:
- **Emotion and Expression Adjustments:** The basic approach might require fine-tuning for more natural emotions and facial expressions, especially concerning mouth and teeth movements.
