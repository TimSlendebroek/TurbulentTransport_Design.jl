# sat1_em_iterfuse2s_azf-1

Residual TGLF-NN for ITER, sat1, ALPHA_ZF=-1: predicts the asinh-space
correction delta = asinh(TJLF) - asinh(base); inference is sinh(asinh(base) + delta),
clamped into the training label range (ybounds).
Standalone Track B model — standard OUT_* ynames, drop-in for run_tglfnn.
Method: Neiser et al. QLGYRO-NN residual pattern; labels are full TJLF on the
snowflake-perturbed ITER sat-rule-scan inputs (see iter_tglfnn_training_design.html).

- training records: 1498602 (of 1500000 labelled; MAD removed 1398; Qe clamp 82477, Qi clamp 69172)
- label files: labels_shard10of32.csv, labels_shard11of32.csv, labels_shard12of32.csv, labels_shard13of32.csv, labels_shard14of32.csv, labels_shard15of32.csv, labels_shard16of32.csv, labels_shard17of32.csv, labels_shard18of32.csv, labels_shard19of32.csv, labels_shard1of32.csv, labels_shard20of32.csv, labels_shard21of32.csv, labels_shard22of32.csv, labels_shard23of32.csv, labels_shard24of32.csv, labels_shard25of32.csv, labels_shard26of32.csv, labels_shard27of32.csv, labels_shard28of32.csv, labels_shard29of32.csv, labels_shard2of32.csv, labels_shard30of32.csv, labels_shard31of32.csv, labels_shard32of32.csv, labels_shard3of32.csv, labels_shard4of32.csv, labels_shard5of32.csv, labels_shard6of32.csv, labels_shard7of32.csv, labels_shard8of32.csv, labels_shard9of32.csv
- dropped degenerate inputs: DZMAJDX_LOC (constant 0.0), RLTS_3 (duplicate of RLTS_2), TAUS_3 (duplicate of TAUS_2), ZMAJ_LOC (constant 0.0)
- architecture: encoder-8xResBlock(64)-decoder
- ensemble: 20 members, 200 epochs, seed 1
- val asinh-MSE: base alone 10.12 -> corrected 0.09598
- R2(asinh) G_elec: 0.9672 (base -0.8589)
- R2(asinh) P_ions: 0.9687 (base -1.3926)
- R2(asinh) Q_elec: 0.9764 (base -2.1122)
- R2(asinh) Q_ions: 0.9792 (base -1.9378)

Gate results (G1-G4): see gate reports in tglf/models/gates/.
Attribution: method Neiser et al. (TGLF-NN/QLGYRO-NN) and Cao et al. 2026 NF 66 076031;
ITER training set and validation gate are ours.
