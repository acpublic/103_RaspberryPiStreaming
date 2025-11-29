# 環境設定
## 使用カメラ
- ロジクール ウェブカメラ C270nd

## カメラ接続
- 接続確認
```
lsusb
Bus 001 Device 004: ID 0c45:6366 Microdia Webcam
```

# カメラ映像配信ソフト
## mjpg-streamer
### インストール
```
sudo apt install mjpg-streamer v4l-utils
```
```
Error: Unable to locate package mjpg-streamer
```
- エラーが出たら、別の方法
1. ソースからビルド
```
sudo apt install git cmake libjpeg-dev g++ build-essential libv4l-dev
git clone https://github.com/jacksonliam/mjpg-streamer.git
cd mjpg-streamer/mjpg-streamer-experimental
make
sudo make install
```
2. snapでインストール
```
sudo apt install snapd
sudo reboot
sudo snap install mjpg-streamer
```

### 起動
```
mjpg_streamer -i "input_uvc.so -d /dev/video0 -r 640x480 -f 15" -o "output_http.so -w /usr/local/share/mjpg-streamer/www -p 8080"
```

### 配信サイト
- http://<PiのIP>:8080
- "Stream" をクリックでリアルタイム映像

## motionEye

