# VT100 Terminal Emulator for Wio Terminal

Arduino Wio Terminal (SAMD) 用の VT100 エミュレータです。

![image](https://user-images.githubusercontent.com/14885863/102246470-2967ec00-3f42-11eb-9473-d38e3aeaa6e6.png)

## 必要なハードウェア
特にありません。

※キーボードは USB 接続のものが使えます。  
※USB Type-C の変換コネクタはダイソーにあります。  
※ブザーは Wio Terminal のものを使います。  
※LED は Wio Terminal のものを使います。  
※ボタンや 5 方向スイッチも認識します。  
※困った事があったら [STM32 版](https://github.com/ht-deko/vt100_stm32) を参考にすると解決するかもです。  

## シリアルバッファのサイズ調整

デフォルトの 256 だと 9600bps で描画が追い付かない事があるためシリアルバッファを増やします (RingBuffer.h)。　

```cpp:RingBuffer.h
# define SERIAL_BUFFER_SIZE 512
```

 ## 使い方
 USB キーボードを Wio Terminal の Type-C コネクタに接続し、背面の GPIO ソケットで通信相手とつなぎます。

| COM | Wio Terminal (SAMD) |
|:--------|:------------------|
| TXD| RXD0 |
| RXD| TXD0 |
| GND| GND|

[RunCPM](https://github.com/MockbaTheBorg/RunCPM) や [CP/M 8266](https://github.com/SmallRoomLabs/cpm8266) と接続してみました。

 ![image](https://user-images.githubusercontent.com/14885863/102247268-14d82380-3f43-11eb-9e77-a9cc465f63db.png)
 
※ この VT100 エミュレータの通信速度は 9600 bps、画面サイズは 53 x 30 です。 

## VT100 の参考資料
VT100 のエスケープシーケンスは以下のサイトを参考にしました。

 - [VT100のエスケープシーケンス (BK class)](http://bkclass.web.fc2.com/doc_vt100.html)
 - [対応制御シーケンス - Tera Term ヘルプ 目次 (Tera Term Home Page)](https://ttssh2.osdn.jp/manual/ja/about/ctrlseq.html)
 - [Chapter 3 Programmer Information - VT100 User Guide (VT100.net)](https://vt100.net/docs/vt100-ug/chapter3.html)
 - [ANSI/VT100 Terminal Control Escape Sequences (termsys.demon.co.uk)](http://www.termsys.demon.co.uk/vtansi.htm)
 - [VT100 escape codes](https://www.csie.ntu.edu.tw/~r92094/c++/VT100.html)
 - [ANSI Escape sequences - VT100 / VT52](http://ascii-table.com/ansi-escape-sequences-vt-100.php)
