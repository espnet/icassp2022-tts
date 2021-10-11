---
date: 2021-10-10T00:00:00+00:00
type: "index"
---

# ESPnet2-TTS: Extending the Edge of TTS Research

Submitted to ICASSP 2022

## Authors

- Tomoki Hayashi (Human Dataware Lab. Co., Ltd. / Nagoya University)
- Ryuichi Yamamoto (LINE Corp.)
- Takenori Yoshimura (Nagoya Institute of Technology)
- Peter Wu (Carnegie Mellon University)
- Jiatong Shi (Carnegie Mellon University)
- Takaaki Saeki (The University of Tokyo)
- Yooncheol Ju (AIRS Company, Hyundai Motor Group)
- Yusuke Yasuda (Nagoya University)
- Shinnosuke Takamichi (The University of Tokyo)
- Shinji Watanabe (Carnegie Mellon University)

## Abstract

This paper describes ESPnet2-TTS, an end-to-end text-to-speech (E2E-TTS) toolkit. ESPnet2-TTS extends our earlier version, ESPnet-TTS, by adding many new features, including: on-the-fly flexible pre-processing, joint training with neural vocoders, and state-of-the-art TTS models with extensions like full-band E2E text-to-waveform modeling, which simplify the training pipeline and further enhance TTS performance.
The unified design of our recipes enables users to quickly reproduce state-of-the-art E2E-TTS results.
We also provide many pre-trained models in a unified Python interface for inference, offering a quick means for users to generate baseline samples and build demos.
Experimental evaluations with English and Japanese corpora demonstrate that our provided models synthesize utterances comparable to ground-truth ones, achieving state-of-the-art TTS performance. 
The toolkit is available online at https://github.com/espnet/espnet.

## Demo

You can try real-time demo in [Google colab](https://colab.research.google.com/github/espnet/notebook/blob/master/espnet2_tts_realtime_demo.ipynb).

## Example of LJSpeech (English single speaker)

- **Transformer-TTS (icassp2020)**: Transformer-TTS + Mixture of density WaveNet vocoder with noise shaping. Our preivous best model.
- **CFS2**: Conformer-FastSpeech2 + HiFiGAN. Each model was separately trained.
- **CFS2 (ft)**: Same as the above model, but HiFi-GAN was fine-tuned with ground-truth aligned mel spectrograms.
- **CFS2 (joint-ft)**: Same as the above model, but both models were jointly fine-tuned.
- **CFS2 (joint-tr)**: Same as the above model, but both models were jointly trained from the scratch.
- **VITS**: End-to-end text-to-waveform model, VITS.

All models used `g2p_en` as the G2P function.  
You can find the detailed configurations in [`egs2/ljspeech/tts1/conf/tuning`](https://github.com/espnet/espnet/tree/master/egs2/ljspeech/tts1/conf/tuning).

**LJ050-0030**: The Commission also recommends

|     |     |
| --- | --- |
| **Groundtruth** | **Transformer-TTS (icassp2020)** |
|<audio controls="" ><source src="wav/ljspeech/gt/LJ050-0030.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/icassp2020/LJ050-0030_gen.wav"/></audio>|
| **CFS2** | **CFS2 (ft)** |
|<audio controls="" ><source src="wav/ljspeech/cfs2/LJ050-0030.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/cfs2_ft/LJ050-0030.wav"/></audio>|
| **CFS2 (joint-ft)** | **CFS2 (joint-tr)** |
|<audio controls="" ><source src="wav/ljspeech/cfs2_joint_ft/LJ050-0030.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/cfs2_joint_tr/LJ050-0030.wav"/></audio>|
| **VITS** | |
|<audio controls="" ><source src="wav/ljspeech/vits/LJ050-0030.wav"/></audio>||


**LJ050-0040**: and reports from other agencies which independently evaluate their information for potential sources of danger.

|     |     |
| --- | --- |
| **Groundtruth** | **Transformer-TTS (icassp2020)** |
|<audio controls="" ><source src="wav/ljspeech/gt/LJ050-0040.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/icassp2020/LJ050-0040_gen.wav"/></audio>|
| **CFS2** | **CFS2 (ft)** |
|<audio controls="" ><source src="wav/ljspeech/cfs2/LJ050-0040.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/cfs2_ft/LJ050-0040.wav"/></audio>|
| **CFS2 (joint-ft)** | **CFS2 (joint-tr)** |
|<audio controls="" ><source src="wav/ljspeech/cfs2_joint_ft/LJ050-0040.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/cfs2_joint_tr/LJ050-0040.wav"/></audio>|
| **VITS** | |
|<audio controls="" ><source src="wav/ljspeech/vits/LJ050-0040.wav"/></audio>||

**LJ050-0050**: As a result of these studies, the planning document submitted by the Secretary of the Treasury to the Bureau of the Budget on August thirty-one,

|     |     |
| --- | --- |
| **Groundtruth** | **Transformer-TTS (icassp2020)** |
|<audio controls="" ><source src="wav/ljspeech/gt/LJ050-0050.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/icassp2020/LJ050-0050_gen.wav"/></audio>|
| **CFS2** | **CFS2 (ft)** |
|<audio controls="" ><source src="wav/ljspeech/cfs2/LJ050-0050.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/cfs2_ft/LJ050-0050.wav"/></audio>|
| **CFS2 (joint-ft)** | **CFS2 (joint-tr)** |
|<audio controls="" ><source src="wav/ljspeech/cfs2_joint_ft/LJ050-0050.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/cfs2_joint_tr/LJ050-0050.wav"/></audio>|
| **VITS** | |
|<audio controls="" ><source src="wav/ljspeech/vits/LJ050-0050.wav"/></audio>||


### Analysis of wrong G2P results

- **CFS2 (g2p_en)**: Conformer-FastSpeech2 + HiFiGAN with `g2p_en` as the G2P function.
- **CFS2 (espeak_ng)**: Conformer-FastSpeech2 + HiFiGAN with `espeak_ng` as the G2P function.
- **VITS (g2p_en)**: VITS with `g2p_en` as the G2P function.
- **VITS (espeak_ng)**: VITS with `espeak_ng` as the G2P function.

**LJ050-0069**: the Secret Service had received from the **FBI** some nine thousand reports on members of the Communist Party.

**g2p_en**
```
DH AH0 <space> S IY1 K R AH0 T <space> S ER1 V AH0 S <space> HH AE1 D <space> R AH0 S IY1 V D <space> F R AH1 M <space> DH AH0 <space> B AY1 <space> S AH1 M <space> N AY1 N <space> TH AW1 Z AH0 N D <space> R IH0 P AO1 R T S <space> AA1 N <space> M EH1 M B ER0 Z <space> AH1 V <space> DH AH0 <space> K AA1 M Y AH0 N AH0 S T <space> P AA1 R T IY0 <space> .
```

**espeak_ng**
```
ð ə <space> s ˈ i ː k ɹ ᵻ t <space> s ˈ ɜ ː v ɪ s <space> h æ d <space> ɹ ᵻ s ˈ i ː v d <space> f ɹ ʌ m ð ɪ <space> ˌ ɛ f b ˌ i ː ˈ a ɪ <space> s ˌ ʌ m <space> n ˈ a ɪ n <space> θ ˈ a ʊ z ə n d <space> ɹ ᵻ p ˈ o ː ɹ t s <space> ˌ ɔ n <space> m ˈ ɛ m b ɚ z <space> ʌ v ð ə <space> k ˈ ɑ ː m j u ː n ˌ ɪ s t <space> p ˈ ɑ ː ɹ ɾ i .`
```

|     |     |
| --- | --- |
| **CFS2 (g2p_en)** | **CFS2 (espeak_ng)** |
|<audio controls="" ><source src="wav/ljspeech/cfs2/LJ050-0069.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/cfs2_espeak/LJ050-0069.wav"/></audio>|
| **VITS (g2p_en)** | **VITS (espeak_ng)** |
|<audio controls="" ><source src="wav/ljspeech/vits/LJ050-0069.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/vits_espeak/LJ050-0069.wav"/></audio>|

**LJ050-0070**: The **FBI** now transmits information on all defectors, a category which would, of course, have included Oswald.

**g2p_en**
```
DH AH0 <space> B AY1 <space> N AW1 <space> T R AE0 N Z M IH1 T S <space> IH2 N F ER0 M EY1 SH AH0 N <space> AA1 N <space> AO1 L <space> D IH0 F EH1 K T ER0 Z <space> , <space> AH0 <space> K AE1 T AH0 G AO2 R IY0 <space> W IH1 CH <space> W UH1 D <space> , <space> AH1 V <space> K AO1 R S <space> , <space> HH AE1 V <space> IH0 N K L UW1 D AH0 D <space> AO1 Z W AO0 L D <space> .
```

**espeak_ng**
```
ð ɪ <space> ˌ ɛ f b ˌ i ː ˈ a ɪ <space> n ˈ a ʊ <space> t ɹ æ n s m ˈ ɪ t s <space> ˌ ɪ n f ɚ m ˈ e ɪ ʃ ə n <space> ˌ ɔ n <space> ˈ ɔ ː l <space> d ᵻ f ˈ ɛ k t ɚ z , <space> ɐ <space> k ˈ æ ɾ ɪ ɡ ɚ ɹ i <space> w ˌ ɪ t ʃ <space> w ˈ ʊ d , <space> ʌ v <space> k ˈ o ː ɹ s , <space> h æ v <space> ɪ ŋ k l ˈ u ː d ᵻ d <space> ˈ ɑ ː s w ə l d .
```

|     |     |
| --- | --- |
| **CFS2 (g2p_en)** | **CFS2 (espeak_ng)** |
|<audio controls="" ><source src="wav/ljspeech/cfs2/LJ050-0070.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/cfs2_espeak/LJ050-0070.wav"/></audio>|
| **VITS (g2p_en)** | **VITS (espeak_ng)** |
|<audio controls="" ><source src="wav/ljspeech/vits/LJ050-0070.wav"/></audio>|<audio controls="" ><source src="wav/ljspeech/vits_espeak/LJ050-0070.wav"/></audio>|


## Example of VCTK (English multi-speaker)

- **Groundtruth**: Groundtruth speech.
- **SID-VITS**: VITS with one-hot speaker ID (SID) embeddings. Since this model cannot deal with unknown speakers, we trained it with all of the speakers.
- **X-VITS (avg)**: VITS with pre-trained X-vectors instead of one-hot speaker ID embeddings. This model was trained with all speakers except for the evaluation ones in the unseen speaker condition. For inference, we used X-vectors averaged over all the utterances of the target speaker except for the evaluation utterances.
- **X-VITS (random)**: The same as the above model except it used X-vectors extracted from a single utterance of the target speaker. This datapoint was randomly selected from all utterances of the speaker excluding the evaluation utterances.

All models used `espeak_ng` as the G2P function.  
You can find the detailed configurations in [`egs2/vctk/tts1/conf/tuning`](https://github.com/espnet/espnet/tree/master/egs2/vctk/tts1/conf/tuning).

### Seen-speaker condition

**p241_364**: We have to be sure that the taxation system can work.

|     |     |
| --- | --- |
| **GT** | **SID-VITS** |
|<audio controls="" ><source src="wav/vctk/gt_subset_b/p241_364.wav"/></audio>|<audio controls="" ><source src="wav/vctk/sid_vits_subset_b/p241_364.wav"/></audio>|
| **X-VITS (avg)** | **X-VITS (random)** |
|<audio controls="" ><source src="wav/vctk/x_avg_vits_subset_b/p241_364.wav"/></audio>|<audio controls="" ><source src="wav/vctk/x_random_vits_subset_b/p241_364.wav"/></audio>|

**p245_350**: Despite his senior position, he did not know in advance.

|     |     |
| --- | --- |
| **GT** | **SID-VITS** |
|<audio controls="" ><source src="wav/vctk/gt_subset_b/p245_350.wav"/></audio>|<audio controls="" ><source src="wav/vctk/sid_vits_subset_b/p245_350.wav"/></audio>|
| **X-VITS (avg)** | **X-VITS (random)** |
|<audio controls="" ><source src="wav/vctk/x_avg_vits_subset_b/p245_350.wav"/></audio>|<audio controls="" ><source src="wav/vctk/x_random_vits_subset_b/p245_350.wav"/></audio>|

**p265_343**: It's not pretty, but it's effective.

|     |     |
| --- | --- |
| **GT** | **SID-VITS** |
|<audio controls="" ><source src="wav/vctk/gt_subset_b/p265_343.wav"/></audio>|<audio controls="" ><source src="wav/vctk/sid_vits_subset_b/p265_343.wav"/></audio>|
| **X-VITS (avg)** | **X-VITS (random)** |
|<audio controls="" ><source src="wav/vctk/x_avg_vits_subset_b/p265_343.wav"/></audio>|<audio controls="" ><source src="wav/vctk/x_random_vits_subset_b/p265_343.wav"/></audio>|

**p333_416**: Their courage, and their honesty, should be respected.

|     |     |
| --- | --- |
| **GT** | **SID-VITS** |
|<audio controls="" ><source src="wav/vctk/gt_subset_b/p333_416.wav"/></audio>|<audio controls="" ><source src="wav/vctk/sid_vits_subset_b/p333_416.wav"/></audio>|
| **X-VITS (avg)** | **X-VITS (random)** |
|<audio controls="" ><source src="wav/vctk/x_avg_vits_subset_b/p333_416.wav"/></audio>|<audio controls="" ><source src="wav/vctk/x_random_vits_subset_b/p333_416.wav"/></audio>|

### Unseen-speaker condition

**p227_393**: You have to rely on each other.

|     |     |
| --- | --- |
| **GT** | **SID-VITS** |
|<audio controls="" ><source src="wav/vctk/gt_subset_a/p227_393.wav"/></audio>|<audio controls="" ><source src="wav/vctk/sid_vits_subset_a/p227_393.wav"/></audio>|
| **X-VITS (avg)** | **X-VITS (random)** |
|<audio controls="" ><source src="wav/vctk/x_avg_vits_subset_a/p227_393.wav"/></audio>|<audio controls="" ><source src="wav/vctk/x_random_vits_subset_a/p227_393.wav"/></audio>|

**p228_362**: It took about an hour for the gas to clear.

|     |     |
| --- | --- |
| **GT** | **SID-VITS** |
|<audio controls="" ><source src="wav/vctk/gt_subset_a/p228_362.wav"/></audio>|<audio controls="" ><source src="wav/vctk/sid_vits_subset_a/p228_362.wav"/></audio>|
| **X-VITS (avg)** | **X-VITS (random)** |
|<audio controls="" ><source src="wav/vctk/x_avg_vits_subset_a/p228_362.wav"/></audio>|<audio controls="" ><source src="wav/vctk/x_random_vits_subset_a/p228_362.wav"/></audio>|

**p300_391**: Form and structure are his music.

|     |     |
| --- | --- |
| **GT** | **SID-VITS** |
|<audio controls="" ><source src="wav/vctk/gt_subset_a/p300_391.wav"/></audio>|<audio controls="" ><source src="wav/vctk/sid_vits_subset_a/p300_391.wav"/></audio>|
| **X-VITS (avg)** | **X-VITS (random)** |
|<audio controls="" ><source src="wav/vctk/x_avg_vits_subset_a/p300_391.wav"/></audio>|<audio controls="" ><source src="wav/vctk/x_random_vits_subset_a/p300_391.wav"/></audio>|

**p304_415**: Parliament was evenly divided on the issue.

|     |     |
| --- | --- |
| **GT** | **SID-VITS** |
|<audio controls="" ><source src="wav/vctk/gt_subset_a/p304_415.wav"/></audio>|<audio controls="" ><source src="wav/vctk/sid_vits_subset_a/p304_415.wav"/></audio>|
| **X-VITS (avg)** | **X-VITS (random)** |
|<audio controls="" ><source src="wav/vctk/x_avg_vits_subset_a/p304_415.wav"/></audio>|<audio controls="" ><source src="wav/vctk/x_random_vits_subset_a/p304_415.wav"/></audio>|


## Example of JSUT (Japanese single speaker)

- **Groundtruth (22k)**: Groundtruth with 22.05 kHz sampling rate.
- **Groundtruth (44k)**: Groundtruth with 44.1 kHz sampling rate.
- **Tacotron2**: Tacotron2 + HiFiGAN. Each model was separately trained.
- **Transformer-TTS**: Transformer-TTS + HiFiGAN. Each model was separately trained.
- **CFS2**: Conformer-FastSpeech2 + HiFiGAN. Each model was separately trained.
- **CFS2 (ft)**: Same as the above model, but HiFi-GAN was fine-tuned with ground-truth aligned mel spectrograms.
- **VITS**: VITS trained with 22.05 kHz sampling rate.
- **FB-VITS**: Full-band VITS trained with 44.1 kHz sampling rate.

All models used `pyopenjtalk_prosody` as the G2P function.  
You can find the detailed configurations in [`egs2/jsut/tts1/conf/tuning`](https://github.com/espnet/espnet/tree/master/egs2/jsut/tts1/conf/tuning).

**BASIC5000_0001**: 水をマレーシアから買わなくてはならないのです。

|     |     |
| --- | --- |
| **GT (22k)** | **GT (44k)** |
|<audio controls="" ><source src="wav/jsut/gt_22k/BASIC5000_0001.wav"/></audio>|<audio controls="" ><source src="wav/jsut/gt_44k/BASIC5000_0001.wav"/></audio>|
| **Tacotron2** | **Transformer-TTS** |
|<audio controls="" ><source src="wav/jsut/taco2_22k/BASIC5000_0001.wav"/></audio>|<audio controls="" ><source src="wav/jsut/transformer_22k/BASIC5000_0001.wav"/></audio>|
| **CFS2** | **CFS2 (ft)** |
|<audio controls="" ><source src="wav/jsut/cfs2_22k/BASIC5000_0001.wav"/></audio>|<audio controls="" ><source src="wav/jsut/cfs2_ft_22k/BASIC5000_0001.wav"/></audio>|
| **VITS** | **FB-VITS** |
|<audio controls="" ><source src="wav/jsut/vits_22k/BASIC5000_0001.wav"/></audio>|<audio controls="" ><source src="wav/jsut/vits_44k/BASIC5000_0001.wav"/></audio>|


**BASIC5000_0005**: 血圧は、健康のパロメーターとして重要である。

|     |     |
| --- | --- |
| **GT (22k)** | **GT (44k)** |
|<audio controls="" ><source src="wav/jsut/gt_22k/BASIC5000_0005.wav"/></audio>|<audio controls="" ><source src="wav/jsut/gt_44k/BASIC5000_0005.wav"/></audio>|
| **Tacotron2** | **Transformer-TTS** |
|<audio controls="" ><source src="wav/jsut/taco2_22k/BASIC5000_0005.wav"/></audio>|<audio controls="" ><source src="wav/jsut/transformer_22k/BASIC5000_0005.wav"/></audio>|
| **CFS2** | **CFS2 (ft)** |
|<audio controls="" ><source src="wav/jsut/cfs2_22k/BASIC5000_0005.wav"/></audio>|<audio controls="" ><source src="wav/jsut/cfs2_ft_22k/BASIC5000_0005.wav"/></audio>|
| **VITS** | **FB-VITS** |
|<audio controls="" ><source src="wav/jsut/vits_22k/BASIC5000_0005.wav"/></audio>|<audio controls="" ><source src="wav/jsut/vits_44k/BASIC5000_0005.wav"/></audio>|


**BASIC5000_0009**: 無罪の人々は、もちろん放免された。

|     |     |
| --- | --- |
| **GT (22k)** | **GT (44k)** |
|<audio controls="" ><source src="wav/jsut/gt_22k/BASIC5000_0009.wav"/></audio>|<audio controls="" ><source src="wav/jsut/gt_44k/BASIC5000_0009.wav"/></audio>|
| **Tacotron2** | **Transformer-TTS** |
|<audio controls="" ><source src="wav/jsut/taco2_22k/BASIC5000_0009.wav"/></audio>|<audio controls="" ><source src="wav/jsut/transformer_22k/BASIC5000_0009.wav"/></audio>|
| **CFS2** | **CFS2 (ft)** |
|<audio controls="" ><source src="wav/jsut/cfs2_22k/BASIC5000_0009.wav"/></audio>|<audio controls="" ><source src="wav/jsut/cfs2_ft_22k/BASIC5000_0009.wav"/></audio>|
| **VITS** | **FB-VITS** |
|<audio controls="" ><source src="wav/jsut/vits_22k/BASIC5000_0009.wav"/></audio>|<audio controls="" ><source src="wav/jsut/vits_44k/BASIC5000_0009.wav"/></audio>|


## Example of JVS (Japanese single speaker adaptation)

- **Groundtruth**: Groundtruth speech..
- **VITS**: VITS adapted with 100 utteracnes. The base model was trained on JSUT with 22.05 kHz.

All models used `pyopenjtalk_prosody` as the G2P function.  
You can find the detailed configurations in [`egs2/jvs/tts1/conf/tuning`](https://github.com/espnet/espnet/tree/master/egs2/jvs/tts1/conf/tuning).

**BASIC5000_0408**: 私もパーティーに来るべきだ、と、彼はつけ加えた。

|     |     |
| --- | --- |
| **GT (jvs001)** | **VITS (jvs001)** |
|<audio controls="" ><source src="wav/jvs/jvs001_gt/jvs001_BASIC5000_0408.wav"/></audio>|<audio controls="" ><source src="wav/jvs/jvs001_vits/jvs001_BASIC5000_0408.wav"/></audio>|

**BASIC5000_0261**: 紙をとじるのに、ホチキスはとても便利だ。

|     |     |
| --- | --- |
| **GT (jvs010)** | **VITS (jvs010)** |
|<audio controls="" ><source src="wav/jvs/jvs010_gt/jvs010_BASIC5000_0261.wav"/></audio>|<audio controls="" ><source src="wav/jvs/jvs010_vits/jvs010_BASIC5000_0261.wav"/></audio>|

**BASIC5000_0238**: 西欧諸国は、この問題に対する日本の姿勢を、激しく非難しています。

|     |     |
| --- | --- |
| **GT (jvs054)** | **VITS (jvs054)** |
|<audio controls="" ><source src="wav/jvs/jvs054_gt/jvs054_BASIC5000_0238.wav"/></audio>|<audio controls="" ><source src="wav/jvs/jvs054_vits/jvs054_BASIC5000_0238.wav"/></audio>|

**BASIC5000_0012**: 溺れかかっていた乗客は、すべて救助された。

|     |     |
| --- | --- |
| **GT (jvs092)** | **VITS (jvs092)** |
|<audio controls="" ><source src="wav/jvs/jvs092_gt/jvs092_BASIC5000_0012.wav"/></audio>|<audio controls="" ><source src="wav/jvs/jvs092_vits/jvs092_BASIC5000_0012.wav"/></audio>|

## Contact

- [Tomoki Hayashi](https://kan-bayashi.github.io/) (hayashi.tomoki<at>g.sp.m.is.nagoya-u.ac.jp)
