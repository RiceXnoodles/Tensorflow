# Tensorflow
•人工智慧期中報告 
•11122108林哲賢   初学者的 TensorFlow 2.0教程
##目錄
•準備資料
•實際操作
##準備資料
•準備一個可使用的google ccolab的帳號
##實際操做
•將tensorflow匯入colab
![螢幕擷取畫面 2023-10-28 095905](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/d8d32f68-bd9c-4b6a-8885-bd043dee8f6a)
•載入mnist資料集，將樣本資料整數轉成浮點數
![螢幕擷取畫面 2023-10-28 101811](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/223696fb-ad60-4199-9a73-51fadcc372e4)
•建構tf.keras.Sequential模型。
![螢幕擷取畫面 2023-10-28 102032](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/26434779-4d9c-4719-9286-44cf525c4a38)
•每個樣本，模型都會傳回一個包含logits或log-odds分數的向量，每個類別一個
![螢幕擷取畫面 2023-10-28 102043](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/cd2d0e26-0526-45ec-b5f0-f47281dd7db5)
•透過tf.nn.softmax函數將這些logits 轉換為每個類別的機率
![螢幕擷取畫面 2023-10-28 102049](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/eb628684-ec9b-4c51-8460-979dce0ac05e)
•使用losses.SparseCategoricalCrossentropy為訓練定義損失函數，它會接受logits 向量和True索引，並為每個樣本傳回一個標量損失
![螢幕擷取畫面 2023-10-28 102056](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/d46167a9-dc28-4ff0-a714-157e12315f9e)
•未經訓練的模型給出的機率接近隨機（每個類別為1/10），因此初始損失應該接近-tf.math.log(1/10) ~= 2.3
![螢幕擷取畫面 2023-10-28 102102](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/48c4c650-f3cb-4194-a058-60624901797d)
•開始訓練之前，使用KerasModel.compile配置和編譯模型。將optimizer類別設為adam，將loss設定為您先前定義的loss_fn函數，並透過將metrics參數設為 來accuracy指定要為模型評估的指標
![螢幕擷取畫面 2023-10-28 102109](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/e10561bb-f6fc-4a0c-afed-579b1afd1283)
•使用Model.fit方法調整您的模型參數並最小化損失
![螢幕擷取畫面 2023-10-28 102116](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/d5ae4c19-df39-4bcb-abea-dbecf72b07f3)
•Model.evaluate方法通常在" Validation-set " 或" Test-set " 上檢查模型效能
![螢幕擷取畫面 2023-10-28 102131](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/6b5637de-b172-45c2-a5ca-94dedab78b7a)
想讓模型傳回機率，可以封裝經過訓練的模型，並將softmax 附加到該模型
![螢幕擷取畫面 2023-10-28 102155](https://github.com/RiceXnoodles/Tensorflow/assets/148970977/7c5a252b-167b-43c4-9da0-d48865a6ffee)
##參考資料
https://tensorflow.google.cn/tutorials/quickstart/beginner?hl=zh_cn 初學者的Tensorflow教學
