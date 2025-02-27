# cpp-01-project-ja
ドライビングアドベンチャーゲームのソースコード一式が srcフォルダにアップロードされています。
## ゲームの実行方法

1. ソースコードのビルド
srcフォルダ直下で、下記コマンドを実行し、main.cppをビルドしてください。
```sh
g++ -std=c++17 -o main main.cpp
```

2. プログラム実行
下記コマンドでゲームが実行されます。
```sh
./main
```

## ゲーム説明

* ゲーム上のマップでは、"E" (自車), "G" (ガソリンスタンド), "-" (道路)、ランドマークとして "T" (東京タワー)と "W" (Wovenオフィス)の5種類の情報が表示されています。

* 下記のユーザーコマンドが受け付けられます。対応外のコマンドを入力した場合は、エラーメッセージが表示されます。

| 対応コマンド | 説明 |
| ---- | ---- |
| tl | Turn Leftの略です。進行方向が左に変わります。<br> 例えば、自車が北を向いていた場合には、向きが西に、東を向いていた場合には向きが北に変わります。 |
| tr | Turn Rightの略です。進行方向が右に変わります。<br> 例えば、自車が北を向いていた場合には、向きが東に、東を向いていた場合には向きが南に変わります。|
| gs | Go Straightの略です。自車を進行方向に自車の速度分だけ進めます。 |
| su | Speed Upの略です。自車の速度が1増えます。最高制限速度は3に設定されており、4以上に速度を上げようとするとエラーメッセージが表示されます。 |
| sd | Speed Downの略です。自車の速度が1減ります。速度を0未満にしようとするとエラーメッセージが表示されます。 |
| stop | 自車の速度が0になります。 |
| end | ゲームが終了します。 |

### ゲームの流れ

gsコマンドで自車を動かしていくことができます。

mapの端に到達してさらにその方向に進もうとするとエラーメッセージが表示されます。
tl, trで方向を変えたり、su, sdコマンドで速度を変えた後に、gsコマンドを入力することで、map上のどこにでも移動することができます。


コマンドを実行するたびに、現在のマップと、自車の向き、位置、速度、ガソリン残量、最も近いランドマークとその距離が表示されます。

ガソリン残量がゼロになってしまうとゲームオーバーとなり、ゲームが終了してしまいます。
ガソリン残量が半分以下になると、ガソリンスタンドに行くことを促すメッセージが表示されますので、残量がゼロになる前に、"G" のガソリンスタンドを目指してください。ガソリンスタンドに到着すると、到着したことを表すメッセージとともに、ガソリン残量が満タンになります。

ランドマークの "T" や "W" に到着した場合は、到着したことを表すメッセージが表示されます。