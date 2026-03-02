<style>
  html, body {
    overflow-x: hidden !important;
    width: 100%;
  }

  .wrapper {
    max-width: 98% !important;
    width: 98% !important;
    margin: 0 auto !important;
    display: flex !important;
  }

  table {
    display: table !important; 
    width: 100% !important;
    table-layout: auto !important; 
    overflow-x: visible !important; 
    border-collapse: collapse;
  }

  th:nth-child(1), td:nth-child(1) {
    width: 15% !important;   
    min-width: 160px !important;
    word-break: keep-all !important;
    white-space: normal !important;
    text-align: left;
  }

  img {
    max-width: 100% !important;  
    height: auto !important;
    display: block;
    margin: 0 auto;
  }

  audio {
    width: 100% !important;
    min-width: 140px;   
  }

  header { width: 26px !important; flex-shrink: 0; }
  section { 
    width: calc(100% - 280px) !important; 
    flex-grow: 1;
    overflow: hidden; 
  }

  @media screen and (max-width: 1000px) {
    .wrapper { display: block !important; }
    header, section { width: 100% !important; }
  }
</style>

# AEC demo page for TASLP submission

## 1. Synthetic RIR Environment

### Synthetic RIR genereted by image source method
#### 1) Double-talk (DT) Scenario: SER=-4 dB, bulk delay=0.624 s
#### 2) Far-end single-talk (FEST) Scenario: bulk delay=0.158 s

| <span style="font-size: 15px;">Signal (Model) | <span style="font-size: 15px;">Double-talk (DT) Scenario | <span style="font-size: 15px;">Far-end single-talk (FEST) Scenario |
| :--- | :--- | :--- |
| <span style="font-size: 15px;">**Far-end** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_far-end.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_far-end.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_far-end.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_far-end.wav"></audio> |
| <span style="font-size: 15px;">**Mic Input (Unprocessed)** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_mic.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_mic.wav"></audio> |
| <span style="font-size: 15px;">**Near-end(Label)** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_clean.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_clean.wav"></audio> |  |
| <span style="font-size: 15px;">**F-T-LSTM [1]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_F-T-LSTM.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_F-T-LSTM.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-S [2]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-S.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_DeepVQE-S.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-L [2]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-L.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_DeepVQE-L.wav"></audio> |
| <span style="font-size: 15px;">**TSDPANet [3]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_TSDPANet.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_TSDPANet.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(AEC-only)** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-SepRe_aec.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_DeepVQE-SepRe_aec.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(Joint-training)**| <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-SepRe_joint.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_DeepVQE-SepRe_joint.wav"></audio> |


## 2. Real-world RIR Environment

### Unseen real-world RIR from SMARD [4]
#### 1) Double-talk (DT) Scenario: SER=-3 dB, bulk delay=0.403 s
#### 2) Far-end single-talk (FEST) Scenario: bulk delay=0.157 s

| <span style="font-size: 15px;">Signal (Model) | <span style="font-size: 15px;">Double-talk (DT) Scenario | <span style="font-size: 15px;">Far-end single-talk (FEST) Scenario |
| :--- | :--- | :--- |
| <span style="font-size: 15px;">**Far-end** | <img src="Real_RIR/DT/spec/snr39_ser-3_d6448_far-end.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr39_ser-3_d6448_far-end.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_far-end.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_far-end.wav"></audio> |
| <span style="font-size: 15px;">**Mic Input** | <img src="Real_RIR/DT/spec/snr39_ser-3_d6448_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr39_ser-3_d6448_mic.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_mic.wav"></audio> |
| <span style="font-size: 15px;">**Near-end (Label)** | <img src="Real_RIR/DT/spec/snr39_ser-3_d6448_clean.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr39_ser-3_d6448_clean.wav"></audio> | |
| <span style="font-size: 15px;">**F-T-LSTM [1]** | <img src="Real_RIR/DT/spec/snr39_ser-3_d6448_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr39_ser-3_d6448_F-T-LSTM.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_F-T-LSTM.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-S [2]** | <img src="Real_RIR/DT/spec/snr39_ser-3_d6448_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr39_ser-3_d6448_DeepVQE-S.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_DeepVQE-S.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-L [2]** | <img src="Real_RIR/DT/spec/snr39_ser-3_d6448_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr39_ser-3_d6448_DeepVQE-L.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_DeepVQE-L.wav"></audio> |
| <span style="font-size: 15px;">**TSDPANet [3]** | <img src="Real_RIR/DT/spec/snr39_ser-3_d6448_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr39_ser-3_d6448_TSDPANet.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_TSDPANet.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(AEC-only)** | <img src="Real_RIR/DT/spec/snr39_ser-3_d6448_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr39_ser-3_d6448_DeepVQE-SepRe_aec.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_DeepVQE-SepRe_aec.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(Joint-training)**| <img src="Real_RIR/DT/spec/snr39_ser-3_d6448_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr39_ser-3_d6448_DeepVQE-SepRe_joint.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_DeepVQE-SepRe_joint.wav"></audio> |


## 3. AEC Challenge blind test set

### INTERSPEECH 2021 AEC Challenge blind test set [5]

| <span style="font-size: 15px;">Signal (Model) | <span style="font-size: 15px;">Double-talk (DT) Scenario | <span style="font-size: 15px;">Far-end single-talk (FEST) Scenario |
| :--- | :--- | :--- |
| <span style="font-size: 15px;">**Far-end** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_lpb.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_lpb.wav"></audio> | <img src="AEC_Challenge/FEST/spec/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_lpb.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_lpb.wav"></audio> |
| <span style="font-size: 15px;">**Mic Input** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_mic.wav"></audio> | <img src="AEC_Challenge/FEST/spec/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_mic.wav_"></audio> |
| <span style="font-size: 15px;">**F-T-LSTM [1]** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_F-T-LSTM.wav"></audio> | <img src="AEC_Challenge/FEST/spec/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_F-T-LSTM.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-S [2]** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-S.wav"></audio> | <img src="AEC_Challenge/FEST/spec/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_DeepVQE-S.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-L [2]** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-L.wav"></audio> | <img src="AEC_Challenge/FEST/spec/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_DeepVQE-L.wav"></audio> |
| <span style="font-size: 15px;">**TSDPANet [3]** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_TSDPANet.wav"></audio> | <img src="AEC_Challenge/FEST/spec/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_TSDPANet.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(AEC-only)** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE_SepRe_aec.wav"></audio> | <img src="AEC_Challenge/FEST/spec/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_DeepVQE-SepRe_aec.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(Joint-training)**| <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE_SepRe_joint.wav"></audio> | <img src="AEC_Challenge/FEST/spec/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/zykCkY0BZEWhtSbeZJm7pw_farend_singletalk_DeepVQE-SepRe_joint.wav"></audio> |

# References

<span style="font-size: 15px;"> [1] S. Zhang, Y. Kong, S. Lv, Y. Hu, and L. Xie, “F-T-LSTM based complex network for joint acoustic echo cancellation and speech enhancement,” in Proc. Interspeech, 2021, pp. 4758–4762.

<span style="font-size: 15px;"> [2] N. C. Ristea, E. Indenbom, A. Saabas, T. P¨arnamaa, J. Guzhvin, and R. Cutler, “DeepVQE: Real time deep voice quality enhancement for joint acoustic echo cancellation, noise suppression and dereverberation,” in Proc. Interspeech, 2023, pp. 3819–3823.

<span style="font-size: 15px;"> [3] Z. Jiang, H. Li, and N. Zheng, “Two-stage acoustic echo cancellation network with dual-path alignment,” in Proc. IEEE Int. Conf. Acoust., Speech Signal Process., 2024, pp. 606–610.

<span style="font-size: 15px;"> [4] J. K. Nielsen, J. R. Jensen, S. H. Jensen, and M. G. Christensen, “The
single- and multichannel audio recordings database (SMARD),” in Proc. Int. Workshop Acoust. Signal Enhance., 2014, pp. 40–44.

<span style="font-size: 15px;"> [5] R. Cutler et al., “Interspeech 2021 acoustic echo cancellation challenge.” in Proc. Interspeech, 2021, pp. 4748–4752.