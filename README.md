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
