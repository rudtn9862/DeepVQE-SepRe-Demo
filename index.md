<style>
  /* 1. 페이지 전체 가로 스크롤 방지 */
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

  /* 2. 테이블 가로 스크롤 강제 해제 */
  table {
    display: table !important;      /* block 속성으로 인한 스크롤 제거 */
    width: 100% !important;
    table-layout: auto !important;  /* 컨텐츠에 맞게 조절 */
    overflow-x: visible !important; /* 내부 스크롤 박멸 */
    border-collapse: collapse;
  }

  /* 3. 첫 번째 열: 텍스트가 넉넉히 들어가되 전체를 밀어내지 않게 설정 */
  th:nth-child(1), td:nth-child(1) {
    width: 15% !important;          /* 픽셀 대신 퍼센트로 유연하게 설정 */
    min-width: 160px !important;
    word-break: keep-all !important;
    white-space: normal !important;
    text-align: left;
  }

  /* 4. 이미지(스펙트로그램) 설정: 칸 너비에 맞춰 자동 축소 */
  img {
    max-width: 100% !important;     /* 이미지가 칸보다 크면 자동으로 줄어듦 */
    height: auto !important;
    display: block;
    margin: 0 auto;
  }

  /* 5. 오디오 플레이어 설정 */
  audio {
    width: 100% !important;
    min-width: 140px;               /* 너무 작아져서 컨트롤이 깨지는 것 방지 */
  }

  /* 6. 레이아웃 비율 고정 */
  header { width: 26px !important; flex-shrink: 0; }
  section { 
    width: calc(100% - 280px) !important; 
    flex-grow: 1;
    overflow: hidden;               /* 섹션 밖으로 튀어나가는 것 방지 */
  }

  /* 모바일 대응 */
  @media screen and (max-width: 1000px) {
    .wrapper { display: block !important; }
    header, section { width: 100% !important; }
  }
</style>

# AEC demo page for TASLP submission

## 1. Synthetic RIR Environment

### Synthetic RIR genereted by image source method

| <span style="font-size: 15px;">Signal (Model) | <span style="font-size: 15px;">Double-talk (DT) Scenario | <span style="font-size: 15px;">Far-end Single-talk (FEST) Scenario |
| :--- | :--- | :--- |
| <span style="font-size: 15px;">**Far-end** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_far-end.jpg.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_far-end.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_far-end.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_far-end.wav"></audio> |
| <span style="font-size: 15px;">**Mic Input (Unprocessed)** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_mic.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_mic.wav"></audio> |
| <span style="font-size: 15px;">**Near-end(Label)** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_clean.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_clean.wav"></audio> |  |
| <span style="font-size: 15px;">**F-T-LSTM [1]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_F-T-LSTM.jpg.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_F-T-LSTM.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_F-T-LSTM.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-S [2]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-S.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_DeepVQE-S.jpg.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_DeepVQE-S.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-L [2]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-L.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_DeepVQE-L.wav"></audio> |
| <span style="font-size: 15px;">**TSDPANet [3]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_TSDPANet.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_TSDPANet.jpgg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_TSDPANet.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(AEC-only)** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-SepRe_aec.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_DeepVQE-SepRe_aec.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(Joint-training)**| <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-SepRe_joint.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/snr37_ser-7_d2532_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/snr37_ser-7_d2532_DeepVQE-SepRe_joint.wav"></audio> |


## 2. Real-world RIR Environment

### Unseen real-world RIR from SMARD [4]

| <span style="font-size: 15px;">Signal (Model) | <span style="font-size: 15px;">Double-talk (DT) Scenario | <span style="font-size: 15px;">Far-end Single-talk (FEST) Scenario |
| :--- | :--- | :--- |
| <span style="font-size: 15px;">**Far-end** | <img src="Real_RIR/DT/spec/snr30_ser-1_d5493_far-end.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr30_ser-1_d5493_far-end.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_far-end.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_far-end.wav"></audio> |
| <span style="font-size: 15px;">**Mic Input** | <img src="Real_RIR/DT/spec/snr30_ser-1_d5493_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr30_ser-1_d5493_mic.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_mic.wav"></audio> |
| <span style="font-size: 15px;">**Near-end (Label)** | <img src="Real_RIR/DT/spec/snr30_ser-1_d5493_clean.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr30_ser-1_d5493_clean.wav"></audio> | |
| <span style="font-size: 15px;">**F-T-LSTM [1]** | <img src="Real_RIR/DT/spec/snr30_ser-1_d5493_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr30_ser-1_d5493_F-T-LSTM.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_F-T-LSTM.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-S [2]** | <img src="Real_RIR/DT/spec/snr30_ser-1_d5493_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr30_ser-1_d5493_DeepVQE-S.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_DeepVQE-S.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-L [2]** | <img src="Real_RIR/DT/spec/snr30_ser-1_d5493_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr30_ser-1_d5493_DeepVQE-L.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_DeepVQE-L.wav"></audio> |
| <span style="font-size: 15px;">**TSDPANet [3]** | <img src="Real_RIR/DT/spec/snr30_ser-1_d5493_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr30_ser-1_d5493_TSDPANet.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_TSDPANet.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(AEC-only)** | <img src="Real_RIR/DT/spec/snr30_ser-1_d5493_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr30_ser-1_d5493_DeepVQE_SepRe_aec.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_DeepVQE-SepRe_aec.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(Joint-training)**| <img src="Real_RIR/DT/spec/snr30_ser-1_d5493_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/snr30_ser-1_d5493_DeepVQE_SepRe_joint.wav"></audio> | <img src="Real_RIR/FEST/spec/snr28_ser-9_d2509_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/snr28_ser-9_d2509_DeepVQE-SepRe_joint.wav"></audio> |


## 3. AEC Challenge blind test set

### INTERSPEECH 2021 AEC Challenge blind test set [5]

| <span style="font-size: 15px;">Signal (Model) | <span style="font-size: 15px;">Double-talk (DT) Scenario | <span style="font-size: 15px;">Far-end Single-talk (FEST) Scenario |
| :--- | :--- | :--- |
| <span style="font-size: 15px;">**Far-end** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_lpb.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_lpb.wav"></audio> | <img src="AEC_Challenge/FEST/spec/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_lpb.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_lpb.wav.wav"></audio> |
| <span style="font-size: 15px;">**Mic Input** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_mic.wav"></audio> | <img src="AEC_Challenge/FEST/spec/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_mic.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_mic.wav_"></audio> |
| <span style="font-size: 15px;">**F-T-LSTM [1]** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_F-T-LSTM.wav"></audio> | <img src="AEC_Challenge/FEST/spec/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_F-T-LSTM.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_F-T-LSTM.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-S [2]** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-S.wav"></audio> | <img src="AEC_Challenge/FEST/spec/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_DeepVQE-S.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-L [2]** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-L.wav"></audio> | <img src="AEC_Challenge/FEST/spec/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_DeepVQE-L.wav"></audio> |
| <span style="font-size: 15px;">**TSDPANet [3]** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_TSDPANet.wav"></audio> | <img src="AEC_Challenge/FEST/spec/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_TSDPANet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_TSDPANet.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(AEC-only)** | <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE_SepRe_aec.wav"></audio> | <img src="AEC_Challenge/FEST/spec/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_DeepVQE-SepRe_aec.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_DeepVQE-SepRe_aec.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(Joint-training)**| <img src="AEC_Challenge/DT/spec/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/sLi810BoekuU3HSx14LT7A_doubletalk_DeepVQE_SepRe_joint.wav"></audio> | <img src="AEC_Challenge/FEST/spec/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_DeepVQE-SepRe_joint.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/xYuPW7feGkyc8a1rfcDv9w_farend_singletalk_with_movement_DeepVQE-SepRe_joint.wav"></audio> |



<span style="font-size: 15px;"> [1] S. Zhang, Y. Kong, S. Lv, Y. Hu, and L. Xie, “F-T-LSTM based complex network for joint acoustic echo cancellation and speech enhancement,” in Proc. Interspeech, 2021, pp. 4758–4762.

<span style="font-size: 15px;"> [2] N. C. Ristea, E. Indenbom, A. Saabas, T. P¨arnamaa, J. Guzhvin, and R. Cutler, “DeepVQE: Real time deep voice quality enhancement for joint acoustic echo cancellation, noise suppression and dereverberation,” in Proc. Interspeech, 2023, pp. 3819–3823.

<span style="font-size: 15px;"> [3] Z. Jiang, H. Li, and N. Zheng, “Two-stage acoustic echo cancellation network with dual-path alignment,” in Proc. IEEE Int. Conf. Acoust., Speech Signal Process., 2024, pp. 606–610.

<span style="font-size: 15px;"> [4] J. K. Nielsen, J. R. Jensen, S. H. Jensen, and M. G. Christensen, “The
single- and multichannel audio recordings database (SMARD),” in Proc. Int. Workshop Acoust. Signal Enhance., 2014, pp. 40–44.

<span style="font-size: 15px;"> [5] R. Cutler et al., “Interspeech 2021 acoustic echo cancellation challenge.” in Proc. Interspeech, 2021, pp. 4748–4752.