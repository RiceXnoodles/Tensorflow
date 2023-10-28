# Tensorflow
•人工智慧期中報告 
•11122108林哲賢   初学者的 TensorFlow 2.0教程
##目錄
•準備資料
實際操作
##準備資料
準備一個可使用的google ccolab的帳號
##實際操做
將tensorflow匯入colab
![螢幕擷取畫面 2023-10-28 095905](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/d8d32f68-bd9c-4b6a-8885-bd043dee8f6a)
載入mnist資料集，將樣本資料整數轉成浮點數
建構tf.keras.Sequential模型。
每個樣本，模型都會傳回一個包含logits或log-odds分數的向量，每個類別一個
透過tf.nn.softmax函數將這些logits 轉換為每個類別的機率
使用losses.SparseCategoricalCrossentropy為訓練定義損失函數，它會接受logits 向量和True索引，並為每個樣本傳回一個標量損失
未經訓練的模型給出的機率接近隨機（每個類別為1/10），因此初始損失應該接近-tf.math.log(1/10) ~= 2.3
開始訓練之前，使用KerasModel.compile配置和編譯模型。將optimizer類別設為adam，將loss設定為您先前定義的loss_fn函數，並透過將metrics參數設為 來accuracy指定要為模型評估的指標
使用Model.fit方法調整您的模型參數並最小化損失
Model.evaluate方法通常在" Validation-set " 或" Test-set " 上檢查模型效能
想讓模型傳回機率，可以封裝經過訓練的模型，並將softmax 附加到該模型
##參考資料
https://tensorflow.google.cn/tutorials/quickstart/beginner?hl=zh_cn 初學者的Tensorflow教學
