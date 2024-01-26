# kaggle日記

### 20240119
HMS - Harmful Brain Activity Classification join!
期限　4/8
賞金　300万円

### 20240125
目標：脳波データから発作などの有害事象を検出、分類する

種類：
・SZ 発作
・GPD
・LPD
・LRDA
・GRDA
・other

アノテーション
・idealized 専門家の意見が一致
・proto patterns 約1/2が意見を一致、約1/2が"other"を選択
・edge case 5つのパターンのうち、2つに意見が割れる

評価指標
KLダイバージェンス。確率分布の類似度

提出ファイル
各症状である確率を示すcsvファイル

#### データ概要
・train.csv
eeg_id - EEG記録全体に対する一意の識別子。
eeg_sub_id - この行のラベルが適用される特定の50秒のサブサンプルのID。
eeg_label_offset_seconds - 連結EEGの開始からこのサブサンプルまでの時間。
spectrogram_id - EEG記録全体に対する一意の識別子。
spectrogram_sub_id - この行のラベルが_用され特定の10分サブサンプルのID。
spectogram_label_offset_seconds - 連結スペクトログラムの先頭からこのサブサンプルまでの時間。
label_id - このラベルのセットのID。
patient_id - データを提供した患者のID。
expert_consensus - コンセンサスアノテータラベル。便宜上記載。
[seizure/lpd/gpd/lrda/grda/other]_vote - ある脳活動クラスに対するアノテータの投票数。活動クラスの正式名称は以下の通り： 
lpd: lateralized periodic discharges, gpd: generalized periodic discharges, lrd: lateralized rhythmic delta activity, grda: generalized rhythmic delta activity
・test.csv
eeg_id
spectrogram_id
patient_id
・submission.csv
eeg_id
_vote
特定のeeg_idがどの症状であると専門家が判断したか予測する

### 20240126
提供されているスペクトログラムデータと、それを加工したデータでモデルの性能に差が出るみたい


