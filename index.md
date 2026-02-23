## 1. Synthetic RIR Environment

### 1-1. Double-Talk (DT) Scenario

| Signal / Model | Audio Player | Spectrogram |
| :--- | :--- | :--- |
| **Far-end** | <audio controls><source src="Synthetic_RIR/Double-talk/snr24_ser-4_d9990_far-end.wav"></audio> | <img src="Synthetic_RIR/Double-talk/1.png" width="350"> |
| **Near-end (Label)** | <audio controls><source src="Synthetic_RIR/Double-talk/snr24_ser-4_d9990_input.wav"></audio> | <img src="Synthetic_RIR/Double-talk/2.png" width="350"> |
| **Mic Input** | <audio controls><source src="Synthetic_RIR/Double-talk/snr24_ser-4_d9990_clean.wav"></audio> | <img src="Synthetic_RIR/Double-talk/3.png" width="350"> |
| **Baseline 1** | <audio controls><source src="Synthetic_RIR/Double-talk/snr24_ser-4_d9990_ftlstm.wav"></audio> | <img src="Synthetic_RIR/Double-talk/4.png" width="350"> |
| **Baseline 2** | <audio controls><source src="Synthetic_RIR/Double-talk/snr24_ser-4_d9990_DeepVQE-S.wav"></audio> | <img src="Synthetic_RIR/Double-talk/5.png" width="350"> |
| **Baseline 3** | <audio controls><source src="Synthetic_RIR/Double-talk/snr24_ser-4_d9990_DeepVQE-L.wav"></audio> | <img src="Synthetic_RIR/Double-talk/6.png" width="350"> |
| **Baseline 4** | <audio controls><source src="Synthetic_RIR/Double-talk/snr24_ser-4_d9990_tsdpanet.wav"></audio> | <img src="Synthetic_RIR/Double-talk/7.png" width="350"> |
| **Proposed (AEC-only)** | <audio controls><source src="Synthetic_RIR/Double-talk/snr24_ser-4_d9990_prop1.wav"></audio> | <img src="Synthetic_RIR/Double-talk/8.png" width="350"> |
| **Proposed (Joint-training)**| <audio controls><source src="Synthetic_RIR/Double-talk/snr24_ser-4_d9990_prop2.wav"></audio> | <img src="Synthetic_RIR/Double-talk/9.png" width="350"> |