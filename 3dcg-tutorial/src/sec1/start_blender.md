# 1.2. Blender を使ってみる

## 概要

この節では、Blender の画面の見方や視点操作、移動・回転・拡大縮小、およびレンダリングについて扱います。

-----
## Blender の起動画面

Blender を起動すると以下のような画面が表示されると思います。

起動時には、Topbar, Status Bar の他に以下の「エリア」と呼ばれるものが表示されています。

- 3D Viewport
- Outliner
- Properties
- Timeline

![起動画面の説明](./img/1.2_areas.png)

<!--    //蛇足な気がする...
Topbar には様々なコマンド（ショートカットで代用することが多い）及びレイアウトを選択するタブが表示されています。

Status Bar にはマウスの機能、及びセーブなどの通知が表示されます。
マウスの機能はCtrl, Shiftなどの押下によって表示が変わります。
-->

Blender での作業は基本的にはこれらのエリアで行います。以下ではその中で特に重要な 3D Viewport, Outliner, Properties について簡単に解説をします。

### 3D Viewport

3D モデルやライト，カメラなどのオブジェクトの配置やモデリングなどの主要な作業は基本的にこのエリアで行います．

3D Viewport には Object Mode や Edit Mode など，いくつかのモードがあり，用途によって使い分けます．

### Outliner

シーンに存在するオブジェクトの一覧が表示されるエリアです．
数が増えるとどれが何なのかよくわからなくなるので，適宜いい感じの名前を与えると良いです．
名前の変更は Outliner 内でオブジェクトをダブルクリック，または F2 キーで可能です．

### Properties

オブジェクトの設定などが表示されるエリアです．
モディファイアやマテリアルと呼ばれるものの設定などを行います．

次回以降で詳しく見ていきます．

-----
## 3D Viewport での操作

Blender での作業で特に重要な 3D Viewport について，より詳しく見ていきましょう．

### 視点操作

3D での視点移動ははじめは少し大変だとは思いますが，
今後よく使うのでそのうち慣れてくると思います．
ゆっくり練習していきましょう．

視点操作の基本は**中クリック**（ホイール押し込み）でのドラッグです．
なので，中クリックが可能なマウスを使うのをおすすめします．

基本的な操作は以下のとおりです．

|           操作           | キー                                | UI上での操作（画面右上） |
| :----------------------: | :---------------------------------- | :----------------------- |
|           回転           | 中クリック                          | 座標軸のマーク           |
|         平行移動         | Shift + 中クリック                  | 手のひらマーク           |
| ズームイン，ズームアウト | Ctrl + 中クリック <br> ホイール回転 | 虫眼鏡マーク             |

中クリックができない場合は，エリア右上にある画像の部分から操作します．

![視点操作のUI](./img/1.2_view.png)

他にもいくつか便利なコマンドがあります．

|               操作               |         キー          |
| :------------------------------: | :-------------------: |
|     座標軸視点などへスナップ     |   Alt + 中クリック    |
|          カメラの視点へ          |      テンキー 0       |
| 選択したオブジェクトの近くへ寄る | テンキー . (ピリオド) |

テンキーの他のキーにも視点が割り当てられていますが，
まずはこれらを抑えておくと良いと思います．

### モードについて

3D Viewport にはいくつかのモードがあることを先ほど述べました．
これらの中で特に重要な Object Mode と Edit Mode について，もう少し詳しく見てみます．

3D Viewport での作業中に予想通りに操作できない場合は，現在のモードが正しいものになっているか確認してみてください．

### Object Mode

![Object Mode の画面](img/1.2_object.png)

Object Mode ではオブジェクト（3D モデルやライト，カメラなど）の配置などを行います．
3D モデルを構成する面などを直接編集はせず，レイアウトなどを考える際に選択します．

Edit Mode の状態で Tab キーを押すか，3D Viewport 左上のドロップダウンから選択して Object Mode へ遷移します
初期状態はこのモードです．

### Edit Mode

![Edit Mode の画面](img/1.2_edit.png)

Edit Mode は 3D モデルを構成する面の形などを編集し，3D モデルの形を作る時に使います．
モデリングの作業は基本的にこの状態で行われます．モデリングについては次節以降で見ていきます．

Object Mode の状態で Tab キーを押すか，3D Viewport 左上のドロップダウンから選択して Edit Mode へ遷移します．

### サイドバー

N キーでサイドバーの表示，非表示を切り替えます．
サイドバーにはオブジェクトなどの座標を指定する欄や，
一部のアドオンの UI などがあります．

![サイドバー](img/1.2_sidebar.png)

### シェーディング

右上の球が 4 つ並んでいる部分，または Z キーで
シェーディングを切り替えることが可能です．

左から順に，

- Wireframe
- Solid
- Material Preview
- Rendered

と呼ばれています．
初期状態は Solid です．
詳しい使い分けについては，次節以降で扱っていきます．
とりあえず今は，「とりあえず表示がおかしくなったら，シェーディングが Solid になっているか確認する」くらいに思っておいてください．

-----
## 座標について

今後 Blender を扱っていく中で，座標を扱うことがあると思います．
その際に躓きやすいであろうポイントとして，**Blender には複数の座標系が存在する**という点があります．
つまり，「見た目では全く同じ位置なのに，なぜか異なる座標になっている」ということが起こり得ます．
座標は 3D Viewport のサイドバーや Properties エリアなどから確認できます．

Blender には，グローバル座標とローカル座標が存在しています．
グローバル座標はオブジェクトの絶対的な位置を表します．
Object Mode で表示されるのはこの座標です．
この座標系では原点はシーンの原点（最初に Default Cube がある点）であり，
座標軸は 3D Viewport で表示されている赤・緑・青の直線です．
例えば，複数のオブジェクトを X 軸に沿って整列させる場合は，
グローバル座標における Y 座標，Z 座標を揃える必要があります．

これに対し，ローカル座標は相対的な位置を表します．
Edit Mode で表示されるのはこの座標です．
この座標系では原点はオブジェクトの中心であり，座標軸はそのオブジェクトのグローバル座標におけるオイラー角によって変化します．
なお，ここで出てきたオブジェクトの中心は
重心とは限らず，自由に設定可能なものです．
グローバル座標における座標では，そのオブジェクトの中心の座標が表示されています．

これらの違いがあることを頭の片隅にでも入れておくと，
今後混乱することが減ると思います．

-----
## オブジェクトの基本操作

それでは，移動や回転などの基本的な操作について見ていきましょう．
ここではとりあえず Object Mode のもとで操作をしていきます．

まずは以下の 3 つのコマンドを覚えてください．

|   操作   | キー  | 覚え方 |
| :------: | :---: | :----- |
|   移動   |   G   | Grab   |
|   回転   |   R   | Rotate |
| 拡大縮小 |   S   | Scale  |

G, R, S キーを押した後にマウスを動かすと，オブジェクトを操作できます．
クリックで操作を確定します．
右クリック，または ESC キーでその操作をキャンセルできます．

2D の画面上で三次元の操作を行うのは少し大変なので，操作を行う軸を指定することが多いです．
X, Y, Z キーを押すとそれぞれ押した軸の方向へ，操作を制限できます．
例えば X キーを押すと，

- 移動の場合は X 軸方向への移動
- 回転の場合は X 軸方向のまわりでの回転，つまり YZ 平面内での回転（オイラー角の話です）
- 拡大縮小の場合は，X 軸方向への拡大縮小

になります.

また，軸の制限を行うときに Shift を同時に押すとその軸以外の方向へ制限できます．
例えば，G の後に Shift + X を押すと，YZ 平面内での移動になります．

-----
## オブジェクトの追加・削除

新しいオブジェクトをシーン内に追加したり，既存のオブジェクトを削除したり方法を見ていきます．

ここで出てくるショートカットは以下の通りです．

| 操作  | キー          |
| :---: | :------------ |
| 追加  | Shift + A     |
| 削除  | X <br> Delete |
| 複製  | Shift + D     |

### オブジェクトの追加

Shift + A を押すと，オブジェクトを追加するメニューが表示されます．
オブジェクトは Mesh や Curve などのカテゴリに分けられています．
カテゴリ名にカーソルを合わせるとオブジェクトが表示され，どれかを選択するとオブジェクトを追加できます．

![オブジェクトの追加](img/1.2_add.png)

たくさんあって威圧感がありますが，とりあえず今は以下のものだけ抑えておきましょう．

- Mesh
- Light
- Camera (Camera は1種類のみ)

### オブジェクトの複製

あるオブジェクトを選択した状態で Shift + D を押すと，そのオブジェクトを複製 (Duplicate) できます．
立方体をたくさん配置したいときなどで，毎回 Shift +A 押して選択して... がめんどくさいときなどに使うと便利です．

### オブジェクトの削除

X キー，または Delete キーでオブジェクトを削除できます．
X キーでの削除の場合は一度確認のボタンが表示されますが，Delete キーの場合は直接削除されます．
Delete キーで間違えて削除してしまった場合でも，Ctrl + Z キーで戻せるので好きなほうを使えば良いと思います．

-----
## カメラ

ここまでオブジェクトの配置などについて見てきました．
画像を出力するレンダリングの段階へ進む前に，カメラを動かします．
（本当はライティングなども行うのですが，今回はほとんど触れずに進めます．）

テンキーの 0 を押すとカメラの視点へ切り替わります．
（Ctrl + Alt + Numpad 0 で現在の視点へカメラを持ってくることができます）

![カメラ視点](img/1.2_camera.png)

カメラの移動方法は色々ありますが，おそらく一番簡単な通常の視点移動で行う方法を使うことにします．
N キーを押してサイドバーを表示し，View タブを選択します．
View Lock の中にある Lock という部分で **Camera to View** の横のチェックボックスをONにします．
すると，カメラ視点の状態で中クリックなどで視点移動を行うと，カメラがついて来るようになります．

![Lock camera to view](img/1.2_lockCamera.png)

もう一度テンキーの0を押すとカメラ視点から抜けることができるので，
オブジェクトの配置などをさらに調整したくなったときなどは一度カメラ視点から外れて作業すると楽だと思います．

画像として出力されるのは点線で囲まれた少し明るくなっている部分です．
このことに注意して，自由にカメラを動かして見てください．

-----
## レンダリング

レンダリングとは，Blender 上で作ったものを .png などの普通の画像ファイルに出力することです．
Blender 上で設定したモデルやライトなどの情報を元にコンピューターが色々計算するため，そこそこ時間がかかります．

F12 キーを押すか，左上の Render → Render Image を選択するとできます，
レンダリングされるのはカメラから見たシーンの状態です．

処理が終わると，新しい画面に出力された画像が表示されていると思います．
左上の Image の中から Save を選択すると画像を保存できます．
File Format はとりあえず PNG を選んでおくと良いと思います．
細かい設定はデフォルトのままで大丈夫です．

Blender 上で作成した 3DCG を画像ファイルとして出力することができました．
これで自分が作ったものを Twitter に投稿したり友達に送ったりできるようになります．

## まとめ

長々と書いてきましたが，以上の流れをまとめると，

1. オブジェクトを追加する．
2. 自由に動かす
3. カメラを移動する
4. レンダリングして画像を保存

となります．是非一度自分でやってみてください．

![1.2 作例](img/1.2_example.jpg)

今回の重要なポイントは

- 視点操作は中クリック（+何か）
- オブジェクトの追加は Shift + A
- 移動は G，回転は R，拡大縮小は S
- レンダリングは F12

です．これらは今後毎回使う重要な操作です．押さえておきましょう．

今回はこれで以上です．ありがとうございました．