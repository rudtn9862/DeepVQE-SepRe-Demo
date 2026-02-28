<style>
  /* 1. 최외곽 컨테이너의 폭 제한(800px~1000px)을 완전히 제거 */
  .wrapper {
    max-width: 98% !important; 
    width: 98% !important;
    margin: 0 auto !important;
    display: flex !important; /* 사이드바와 본문을 유연하게 배치 */
    flex-wrap: wrap;
  }

  /* 2. 왼쪽 사이드바(제목/설명 부분) 폭 고정 및 조정 */
  header {
    width: 280px !important; /* 사이드바 폭을 적당히 고정 */
    float: none !important;
    position: sticky !important; /* 스크롤 내려도 제목이 보이게 고정 (선택) */
    top: 20px;
  }

  /* 3. 본문 영역을 나머지 가로 공간 전체로 확장 */
  section {
    width: calc(100% - 320px) !important; /* 전체에서 사이드바 폭을 뺀 나머지 전부 */
    float: none !important;
    max-width: none !important;
    padding-left: 20px !important;
  }

  /* 4. 테이블이 본문 너비에 맞춰 꽉 차게 확장 */
  table {
    display: table !important;
    width: 100% !important;
    margin: 20px 0 !important;
    table-layout: auto !important; /* 내용에 맞춰 열 너비 조절 */
  }

  /* 5. 모바일 환경(화면이 좁아질 때) 대응 */
  @media screen and (max-width: 1000px) {
    .wrapper {
      width: 95% !important;
      display: block !important;
    }
    header, section {
      width: 100% !important;
      position: static !important;
    }
  }

  /* 오디오 플레이어 크기 최적화 */
  audio {
    width: 100%;
    min-width: 120px;
  }
</style>

# AEC demo page for TASLP submission

## 1. Synthetic RIR Environment

### Synthetic RIR genereted by image source method

| <span style="font-size: 15px;">Signal (Model) | <span style="font-size: 15px;">Double-talk (DT) Scenario | <span style="font-size: 15px;">Far-end Single-Talk (FEST) Scenario |
| :--- | :--- | :--- |
| <span style="font-size: 15px;">**Far-end** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_far-end.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_far-end.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/Far-end_6_snr37_ser-7_d2532.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/Far-end_6_snr37_ser-7_d2532.wav"></audio> |
| <span style="font-size: 15px;">**Mic Input (Unprocessed)** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_input.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_input.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/Mic_Input_6_snr37_ser-7_d2532.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/Mic_Input_6_snr37_ser-7_d2532.wav"></audio> |
| <span style="font-size: 15px;">**Near-end(Label)** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_clean.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_clean.wav"></audio> | N/A |
| <span style="font-size: 15px;">**F-T-LSTM [1]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_ftlstm.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_ftlstm.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/ftlstm_6_snr37_ser-7_d2532.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/ftlstm_6_snr37_ser-7_d2532.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-S [2]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-S.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-S.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/DeepVQE-S_6_snr37_ser-7_d2532.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/DeepVQE-S_6_snr37_ser-7_d2532.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-L [2]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_DeepVQE-L.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_DeepVQE-L.wav"></audio> | <img src="Syntetic_RIR/FEST/spec/DeepVQE-L_6_snr37_ser-7_d2532.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/DeepVQE-L_6_snr37_ser-7_d2532.wav"></audio> |
| <span style="font-size: 15px;">**TSDPANet [3]** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_tsdpanet.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_tsdpanet.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/tsdpanet_6_snr37_ser-7_d2532.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/tsdpanet_6_snr37_ser-7_d2532.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(AEC-only)** | <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_prop1.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_prop1.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/Prop1_6_snr37_ser-7_d2532.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/Prop1_6_snr37_ser-7_d2532.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(Joint-training)**| <img src="Synthetic_RIR/DT/spec/snr24_ser-4_d9990_prop2.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/DT/audio/snr24_ser-4_d9990_prop2.wav"></audio> | <img src="Synthetic_RIR/FEST/spec/Prop2_6_snr37_ser-7_d2532.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Synthetic_RIR/FEST/audio/Prop2_6_snr37_ser-7_d2532.wav"></audio> |


## 2. Real-world RIR Environment

### Unseen real-world RIR from SMARD [4]

| <span style="font-size: 15px;">Signal (Model) | <span style="font-size: 15px;">Double-talk (DT) Scenario | <span style="font-size: 15px;">Far-end Single-Talk (FEST) Scenario |
| :--- | :--- | :--- |
| <span style="font-size: 15px;">**Far-end** | <img src="Real_RIR/DT/spec/Far-end_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/Far-end_132_snr30_ser-1_d5493.wav"></audio> | <img src="Real_RIR/FEST/spec/Far-end_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/Far-end_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**Mic Input** | <img src="Real_RIR/DT/spec/Mic_Input_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/Mic_Input_132_snr30_ser-1_d5493.wav"></audio> | <img src="Real_RIR/FEST/spec/Mic_Input_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/Mic_Input_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**Near-end (Label)** | <img src="Real_RIR/DT/spec/Near-end_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/Near-end_132_snr30_ser-1_d5493.wav"></audio> | N/A |
| <span style="font-size: 15px;">**F-T-LSTM [1]** | <img src="Real_RIR/DT/spec/ftlstm_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/ftlstm_132_snr30_ser-1_d5493.wav"></audio> | <img src="Real_RIR/FEST/spec/ftlstm_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/ftlstm_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-S [2]** | <img src="Real_RIR/DT/spec/DeepVQE-S_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/DeepVQE-S_132_snr30_ser-1_d5493.wav"></audio> | <img src="Real_RIR/FEST/spec/DeepVQE-S_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/DeepVQE-S_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-L [2]** | <img src="Real_RIR/DT/spec/DeepVQE-L_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/DeepVQE-L_132_snr30_ser-1_d5493.wav"></audio> | <img src="Real_RIR/FEST/spec/DeepVQE-L_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/DeepVQE-L_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**TSDPANet [3]** | <img src="Real_RIR/DT/spec/tsdpanet_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/tsdpanet_132_snr30_ser-1_d5493.wav"></audio> | <img src="Real_RIR/FEST/spec/tsdpanet_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/tsdpanet_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(AEC-only)** | <img src="Real_RIR/DT/spec/Prop1_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/Prop1_132_snr30_ser-1_d5493.wav"></audio> | <img src="Real_RIR/FEST/spec/Prop1_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/Prop1_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(Joint-training)**| <img src="Real_RIR/DT/spec/Prop2_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/DT/audio/Prop2_132_snr30_ser-1_d5493.wav"></audio> | <img src="Real_RIR/FEST/spec/Prop2_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="Real_RIR/FEST/audio/Prop2_47_snr28_ser-9_d2509.wav"></audio> |


## 3. AEC Challenge blind test set

### INTERSPEECH 2021 AEC Challenge blind test set [5]

| <span style="font-size: 15px;">Signal (Model) | <span style="font-size: 15px;">Double-talk (DT) Scenario | <span style="font-size: 15px;">Far-end Single-Talk (FEST) Scenario |
| :--- | :--- | :--- |
| <span style="font-size: 15px;">**Far-end** | <img src="AEC_Challenge/DT/spec/Far-end_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/Far-end_132_snr30_ser-1_d5493.wav"></audio> | <img src="AEC_Challenge/FEST/spec/Far-end_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/Far-end_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**Mic Input** | <img src="AEC_Challenge/DT/spec/Mic_Input_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/Mic_Input_132_snr30_ser-1_d5493.wav"></audio> | <img src="AEC_Challenge/FEST/spec/Mic_Input_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/Mic_Input_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**Near-end (Label)** | <img src="AEC_Challenge/DT/spec/Near-end_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/Near-end_132_snr30_ser-1_d5493.wav"></audio> | N/A |
| <span style="font-size: 15px;">**F-T-LSTM [1]** | <img src="AEC_Challenge/DT/spec/ftlstm_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/ftlstm_132_snr30_ser-1_d5493.wav"></audio> | <img src="AEC_Challenge/FEST/spec/ftlstm_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/ftlstm_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-S [2]** | <img src="AEC_Challenge/DT/spec/DeepVQE-S_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/DeepVQE-S_132_snr30_ser-1_d5493.wav"></audio> | <img src="AEC_Challenge/FEST/spec/DeepVQE-S_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/DeepVQE-S_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-L [2]** | <img src="AEC_Challenge/DT/spec/DeepVQE-L_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/DeepVQE-L_132_snr30_ser-1_d5493.wav"></audio> | <img src="AEC_Challenge/FEST/spec/DeepVQE-L_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/DeepVQE-L_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**TSDPANet [3]** | <img src="AEC_Challenge/DT/spec/tsdpanet_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/tsdpanet_132_snr30_ser-1_d5493.wav"></audio> | <img src="AEC_Challenge/FEST/spec/tsdpanet_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/tsdpanet_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(AEC-only)** | <img src="AEC_Challenge/DT/spec/Prop1_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/Prop1_132_snr30_ser-1_d5493.wav"></audio> | <img src="AEC_Challenge/FEST/spec/Prop1_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/Prop1_47_snr28_ser-9_d2509.wav"></audio> |
| <span style="font-size: 15px;">**DeepVQE-SepRe<br>(Joint-training)**| <img src="AEC_Challenge/DT/spec/Prop2_132_snr30_ser-1_d5493.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/DT/audio/Prop2_132_snr30_ser-1_d5493.wav"></audio> | <img src="AEC_Challenge/FEST/spec/Prop2_47_snr28_ser-9_d2509.jpg" width="500"><br><audio controls style="width: 500px;"><source src="AEC_Challenge/FEST/audio/Prop2_47_snr28_ser-9_d2509.wav"></audio> |



<span style="font-size: 15px;"> [1] S. Zhang, Y. Kong, S. Lv, Y. Hu, and L. Xie, “F-T-LSTM based complex network for joint acoustic echo cancellation and speech enhancement,” in Proc. Interspeech, 2021, pp. 4758–4762.

<span style="font-size: 15px;"> [2] N. C. Ristea, E. Indenbom, A. Saabas, T. P¨arnamaa, J. Guzhvin, and R. Cutler, “DeepVQE: Real time deep voice quality enhancement for joint acoustic echo cancellation, noise suppression and dereverberation,” in Proc. Interspeech, 2023, pp. 3819–3823.

<span style="font-size: 15px;"> [3] Z. Jiang, H. Li, and N. Zheng, “Two-stage acoustic echo cancellation network with dual-path alignment,” in Proc. IEEE Int. Conf. Acoust., Speech Signal Process., 2024, pp. 606–610.

<span style="font-size: 15px;"> [4] J. K. Nielsen, J. R. Jensen, S. H. Jensen, and M. G. Christensen, “The
single- and multichannel audio recordings database (SMARD),” in Proc. Int. Workshop Acoust. Signal Enhance., 2014, pp. 40–44.

<span style="font-size: 15px;"> [5] R. Cutler et al., “Interspeech 2021 acoustic echo cancellation challenge.” in Proc. Interspeech, 2021, pp. 4748–4752.