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

・eeg_id　：個別のeeg(脳波)を識別するid
・eeg_sub_id　：特定のeegの50秒ごとsubsetに割り当てられるid
・eeg_label_offset_seconds　：subsetが、連結された(元の)eegの、開始から何秒ずれているか
・spectrogram_id　；個別のeeg(spectrogram)に対する脳波を識別するid
・spectrogram_sub_id　：全体の脳波(spectrogram)に対する10分のsubsampleの識別id
・spectrogram_label_offset_seconds ：このspectrogramとsubsampleが開始してからの経過時間
・label_id ：上記のラベルに対応するid
・patient_id ：データ提供患者のid
・expert_consensus ：専門家によるアノテーションの結果。簡易的に示す 
以下、専門家が投票した脳活動の数を数字で示す
・seizure_vote
・lpd_vote
・gpd_vote
・lrda_vote
・grda_vote
・other_vote

