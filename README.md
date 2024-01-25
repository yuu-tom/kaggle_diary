# kaggle日記

### 20240119
HMS - Harmful Brain Activity Classification join!
期限　4/8

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

公開codeのEfficientNetB2 Starterを確認

