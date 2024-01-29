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

### 20240129
提出ファイル：
eeg_idと[seizure/lpd/gpd/lrda/grda/other]_voteを含むcsvファイル。それぞれの活動ラベルの、専門家投票の確率分布を予想する。

地力を身につけるのか、スコアをとりに行くのかで戦略が変わる。
地力→codeやdiscussionの手法だけを見て、自分で調べて0から実装する
スコア→公開コードで編集できそうな部分を変更して、特徴量とかを追加して他のコードとアンサンブルする

コンペの序盤と終盤で戦い方を変えるべき。序盤は自力をつける、終盤はハイスコアを目指す。結局結果が出ないとやっている意味がないが、自力をつけたい気持ちもわかる。コードも更新されるので、
方針
・最初の2/3は手法のみをインプットして自力実装(参照しても良い。ただ自分で理解して記述すること。出来るだけsubmitすること。)
・後半の1/3は公開コードをそのまま利用して、アンサンブルやら特徴料の追加やらdiscussionの情報やらを全部組み合わせてスコアを上げる。

