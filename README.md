# VRChat Bone Viewer

VRChatのログからボーンデータを抽出し、3Dで可視化するためのビューアです。  
ブラウザだけで動作し、CSVファイルまたはVRChatログファイルを直接読み込めます。

## 公開URL

- Viewer: https://faruco10032.github.io/vrchat-bone-viewer/
- VRChat World (Bone Logger): https://vrchat.com/home/world/wrld_8008d371-071e-482e-aba7-60caec9d625d/info
- 使い方動画: https://youtu.be/0hO65QIS824

## できること

- VRChatログ (`.txt` / `.log`) を直接読み込み
- 既存のCSV (`frame, unity_time, bone, pos_x, pos_y, pos_z ...`) を読み込み
- 骨格の再生
  - FPS固定再生
  - Realtime再生（ログ時刻ベース）
- カメラ操作
  - 右ドラッグ: 回転
  - 中ドラッグ: 平行移動
  - ホイール: ズーム
- Realtimeモード中の `DATA FPS` 表示（unity_time差分から算出）

## 利用手順（最短）

1. VRChatでBone Loggerワールドに入る  
ログはワールド入室直後からVRChatログファイルへ書き込まれます。
2. Viewerを開く  
https://faruco10032.github.io/vrchat-bone-viewer/
3. `LOG LOAD` を押してログファイルを選択  
通常のログ保存先:  
`%USERPROFILE%\AppData\LocalLow\VRChat\VRChat`
4. タイムラインや再生ボタンでモーションを確認

## ログ形式（想定）

以下のような `[BoneLogger]` 行を解析します。

- フレーム行  
`[BoneLogger] Frame:<frame> Time:<unity_time>`
- ボーン行  
`[BoneLogger] <bone> | pos(x,y,z) | rot(x,y,z,w)`

## 計測メモ（現状）

- 単独入室時: おおむね `120-140 fps` でロギング確認
- 参加人数増加やワールド機能追加によりフレームレート低下の可能性あり

