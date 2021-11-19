# PyCon-mini-Shizuoka-2021-Talk4
このリポジトリはPyCon mini Shizuoka 2021「[トーク4 - Raspberry Pi 4でリアルタイムなディープラーニング](https://shizuoka.pycon.jp/2021/info)」の補足資料です。<br>
トーク内で紹介したモデルのサンプルスクリプトと訓練済みモデルを格納しています。<br>

https://user-images.githubusercontent.com/37477845/142657300-e6f231fb-1188-4602-a980-3f49cdcc1231.mp4

# Requirements
* Tensorflow 2.6.0 or Later
* onnxruntime 1.8.0 or Later
* OpenCV 3.4.2 or Later
* Pillow 6.1.0 or Later

# 01．クラス分類(Image Clasification)
<img src="https://user-images.githubusercontent.com/37477845/142651114-cdd515db-8ae1-4e35-873d-010ab6d5942e.gif" loading="lazy" width="40%"><br>
ソースコード：[01_image_classification/demo.py](https://github.com/Kazuhito00/PyCon-mini-Shizuoka-2021/blob/main/01_image_classification/demo.py)<br>
ライセンス：[Apache-2.0](LICENSE(Apache-2.0))<br>
実行方法：python demo.py<br>
<details>
<summary>実行時オプション</summary>

* --device<br>
カメラデバイス番号の指定<br>
デフォルト：0
* --width<br>
カメラキャプチャ時の横幅<br>
デフォルト：640
* --height<br>
カメラキャプチャ時の縦幅<br>
デフォルト：480
* --crop_width<br>
7セグメント画像1枚の切り抜き横幅<br>
デフォルト：96
* --crop_height<br>
7セグメント画像1枚の切り抜き縦幅<br>
デフォルト：96
* --num_digits<br>
7セグメントディスプレイの桁数<br>
デフォルト：4
* --check_count<br>
7セグメント画像識別時に直近何回の数値をもとに判断するか<br>
指定数値を保持し、最多の数値を識別値とする<br>
デフォルト：5
* --use_binarize<br>
7セグメント画像の識別時に2値化(大津の2値化)を使用するか否か<br>
デフォルト：指定なし
* --use_binarize_inverse<br>
2値化を行う際に値を反転するか否か<br>
デフォルト：指定なし
* --binarize_th<br>
2値化の閾値(0～255)を指定<br>
このオプションを指定した場合、大津の2値化ではなく単純2値化を実施<br>
デフォルト：None
</details>

# 02．物体検出(Object Detection)
<img src="https://user-images.githubusercontent.com/37477845/142651124-1eff547b-a0ca-4ce9-a738-46dd38e75330.gif" loading="lazy" width="40%"><br>
ソースコード：[02_object_detection/demo_onnx.py](https://github.com/Kazuhito00/PyCon-mini-Shizuoka-2021/blob/main/02_object_detection/demo_onnx.py)<br>
ライセンス：[Apache-2.0](LICENSE(Apache-2.0))<br>
実行方法：python demo_onnx.py<br>
<details>
<summary>実行時オプション</summary>

* --device<br>
カメラデバイス番号の指定<br>
デフォルト：0
* --movie<br>
動画ファイルの指定 ※指定時はカメラデバイスより優先<br>
デフォルト：指定なし
* --image<br>
画像ファイルの指定 ※指定時はカメラデバイスや動画より優先<br>
デフォルト：指定なし
* --width<br>
カメラキャプチャ時の横幅<br>
デフォルト：960
* --height<br>
カメラキャプチャ時の縦幅<br>
デフォルト：540
* --model<br>
ロードするモデルの格納パス<br>
デフォルト：model/nanodet_m_320.onnx
* --input_shape<br>
モデルの入力サイズ<br>
デフォルト：320
* --score_th<br>
クラス判別の閾値<br>
デフォルト：0.35
* --nms_th<br>
NMSの閾値<br>
デフォルト：0.6
</details>

# 03．顔検出(Face Detection)
<img src="https://user-images.githubusercontent.com/37477845/142651129-cf775179-2813-4dbd-8e6b-ca15793414d7.gif" loading="lazy" width="40%"><br>
ソースコード：[03_face_detection/demo_onnx.py](https://github.com/Kazuhito00/PyCon-mini-Shizuoka-2021/blob/main/03_face_detection/demo_onnx.py)<br>
ライセンス：[Apache-2.0](LICENSE(Apache-2.0))<br>
実行方法：python demo_onnx.py<br>
<details>
<summary>実行時オプション</summary>

* --device<br>
カメラデバイス番号の指定<br>
デフォルト：0
* --movie<br>
動画ファイルの指定 ※指定時はカメラデバイスより優先<br>
デフォルト：指定なし
* --image<br>
画像ファイルの指定 ※指定時はカメラデバイスや動画より優先<br>
デフォルト：指定なし
* --width<br>
カメラキャプチャ時の横幅<br>
デフォルト：960
* --height<br>
カメラキャプチャ時の縦幅<br>
デフォルト：540
* --model<br>
ロードするモデルの格納パス<br>
デフォルト：model/face_detection_yunet_120x160.onnx
* --input_shape<br>
モデルの入力サイズ<br>
デフォルト：160,120
* --score_th<br>
クラス判別の閾値<br>
デフォルト：0.6
* --nms_th<br>
NMSの閾値<br>
デフォルト：0.3
* --topk<br>
topk指定値<br>
デフォルト：5000
* --keep_topk<br>
keep_topk指定値<br>
デフォルト：750
</details>

# 04．姿勢推定(Pose Estimation)
<img src="https://user-images.githubusercontent.com/37477845/142651165-eedc542b-f3b3-4844-a2c7-049a6a635950.gif" loading="lazy" width="40%"><br>
ソースコード：[03_face_detection_demo.py](https://github.com/Kazuhito00/PyCon-mini-Shizuoka-2021/blob/main/04_pose_estimation/demo_onnx.py)<br>
ライセンス：[Apache-2.0](LICENSE(Apache-2.0))<br>
実行方法：python demo_onnx.py<br>
<details>
<summary>実行時オプション</summary>

* --model<br>
モデル格納パス<br>
デフォルト：model/model_float32.onnx
* --input_size<br>
モデルへの入力する画像の一辺のサイズ<br>
デフォルト：192
</details>

# Authors
高橋かずひと(https://twitter.com/KzhtTkhs)
