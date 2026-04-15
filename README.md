# VRChat Bone Viewer

VRChatのログからボーンデータを抽出し、3Dで可視化するためのビューアです。
ブラウザだけで動作し、CSVファイルまたはVRChatログファイルを直接読み込めます。

## 公開URL

- Viewer: https://faruco10032.github.io/vrchat-bone-viewer/
- VRChat World (Bone Logger): https://vrchat.com/home/world/wrld_8008d371-071e-482e-aba7-60caec9d625d/info

## できること

- VRChatログ (`.txt` / `.log`) を直接読み込み
- 既存のCSV (`frame, unity_time, bone, pos_x, pos_y, pos_z ...`) を読み込み
- **マルチプレイヤー対応**: 複数プレイヤーのデータを含むログからプレイヤーを選択
- **プレイヤー名表示**: 選択中プレイヤーの名前を頭上に表示
- 骨格の再生
  - FPS固定再生（15/30/60/90 FPS）
  - Realtime再生（ログ時刻ベース、0.25x〜2x速度）
- カメラ操作
  - 右ドラッグ: 回転
  - 中ドラッグ: 平行移動
  - ホイール: ズーム
  - FOLLOW / WORLD FIXED 切替

## 対応ログ形式

### 新形式 `[MOTIONLOG]`（マルチプレイヤー対応）

```
[MOTIONLOG] SESSION_START SessionID:1 Avatar:true Voice:false PlayerCount:3 UnityTime:0.000
[MOTIONLOG] PLAYER ID:1 Name:UserA IsVR:true Role:subject
[MOTIONLOG] F:100 T:1.234 P:1
[MOTIONLOG] B P:1 Hips pos(0.5,1.2,0.3) rot(0,0,0,1)
[MOTIONLOG] B P:1 Spine pos(0.5,1.4,0.3) rot(0.1,0,0,0.995)
```

### 旧形式 `[BoneLogger]`（単一プレイヤー）

```
[BoneLogger] Frame:1234 Time:45.678
[BoneLogger] Hips | pos(0.5,1.2,0.3) | rot(0,0,0,1)
```

ログ形式は自動検出されます。

## 利用手順

1. Viewerを開く: https://faruco10032.github.io/vrchat-bone-viewer/
2. `LOG LOAD` を押してVRChatログファイルを選択
   ログ保存先: `%USERPROFILE%\AppData\LocalLow\VRChat\VRChat`
3. マルチプレイヤーデータの場合、ヘッダーのドロップダウンでプレイヤーを選択
4. タイムラインや再生ボタンでモーションを確認

## 表示されるボーン（22点）

Hips, Spine, Chest, UpperChest, Neck, Head,
LeftShoulder, LeftUpperArm, LeftLowerArm, LeftHand,
RightShoulder, RightUpperArm, RightLowerArm, RightHand,
LeftUpperLeg, LeftLowerLeg, LeftFoot, LeftToes,
RightUpperLeg, RightLowerLeg, RightFoot, RightToes

## 関連ツール

- [Q-Sort Analysis Viewer](https://faruco10032.github.io/qsort-analysis-viewer/) - VRChat内Q-Sortの結果を可視化
