# Audio Deepfake Detection: Is that voice note real?

Workshop by GDG On Campus Abu Dhabi University, 11 October 2026.

A forwarded voice note sounds like a company's CEO asking for an urgent transfer. The workshop follows that case from start to finish. It covers how sound is stored as numbers, what a human body leaves in a voice, how voice cloning works, and what calls and messaging apps remove from a clip. It ends with a detector you run yourself.

## Files

| File | Contents |
|---|---|
| `Audio_Deepfake_Detection_Short_Final.pdf` | The slides |
| `Audio_Deepfake_Detection_Notebook.ipynb` | The Colab notebook, with the 60 audio clips built in |

## Running the notebook

1. [Open the workshop notebook in Google Colab](https://colab.research.google.com/drive/1w1f2Ra1OMTv1U5mSBDQLt1wAViOMZkNR?usp=sharing). You can also upload the included `.ipynb` file to Colab.
2. Click **Runtime → Run all**. It takes about 5 minutes on the free CPU, and you don't need to write any code.
3. At Stop 4, click **Choose files** to test your own voice notes.

## What the notebook does

- **Stop 1:** listen to a real clip and an AI clip, and compare their spectrograms and file information.
- **Stop 2:** train a first detector (58 features and logistic regression). Then test it on sentences it never saw, under eight conditions: WhatsApp-style compression, MP3, a phone call, café noise, room echo, a noise filter, replay and the clean original.
- **Stop 3:** the first detector fails under noise, because it learned that noise means human. Detector v2 fixes most of this with 135 features (spectral, voice from Praat, and timing) and the same random noise and compression applied to both real and AI clips.
- **Stop 4:** score your own clip in 3-second windows and get a short report.

## Results (60 clips, sentences not seen in training)

| Condition | First detector | Detector v2 |
|---|---|---|
| Café noise | 50% | 92% |
| Replay through a speaker | 52% | 88% |

With a voice generator it never heard, after replay, detector v2 drops to 73%. This is a teaching result on a small dataset, not a production detector.

## Data and tools

- **Real speech:** Google FLEURS (CC BY 4.0).
- **AI speech:** Microsoft Edge TTS, gTTS and Piper.
- **Tools:** scikit-learn, Praat via parselmouth, ffmpeg.
