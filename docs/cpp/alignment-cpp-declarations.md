---
title: 對齊方式 (C++ 宣告)
description: 資料對齊在現代化的指定方式C++。
ms.date: 05/30/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: b6e03ac2b89624a0eb6602183d4ff4bf8b518f8d
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450766"
---
# <a name="alignment-c-declarations"></a>對齊方式 (C++ 宣告)

C++ 的其中一項低階功能可指定記憶體中物件的精確對齊方式，以充份利用特定的硬體架構。 根據預設，編譯器會根據大小值的類別和結構成員對齊：`bool`並`char`1 個位元組界限上`short`2 位元組界限上`int`， `long`，和`float`4 位元組界限，以及`long long`， `double`，和`long double`8 位元組界限上。 在大部分情況下，您永遠不必擔心對齊，因為已達到最佳的預設對齊方式。 在某些情況下，不過，您可以達到顯著的效能改善或節省記憶體空間中，指定您的資料結構的自訂對齊方式。 在 Visual Studio 2015 之前，您可以使用 Microsoft 專有關鍵字`__alignof`和`declspec(alignas)`來指定大於預設值的對齊方式。 啟動 Visual Studio 2015 中，則應該使用的 C + + 11 標準關鍵字[alignof 和 alignas](../cpp/alignof-and-alignas-cpp.md)最大化程式碼可攜性。 New 關鍵字的行為方式實際上與 Microsoft 專有擴充功能。 這些延伸模組的文件也適用於新的關鍵字。 如需詳細資訊，請參閱 < [__alignof 運算子](../cpp/alignof-operator.md)並[對齊](../cpp/align-cpp.md)。 C++標準不指定封裝的行為對齊界限小於目標平台的編譯器預設值，您仍然需要使用 Microsoft #pragma [pack](../preprocessor/pack.md)在此情況下。

使用[aligned_storage 類別](../standard-library/aligned-storage-class.md)具有自訂對齊的資料結構的記憶體配置。 [Aligned_union 類別](../standard-library/aligned-union-class.md)用於非一般建構函式或解構函式使用指定的等位的對齊方式。

## <a name="about-alignment"></a>關於對齊方式

對齊是記憶體位址的屬性，以數字位址取 2 乘冪的模數來表示。 例如，位址 0x0001103F 取 4 的模數是 3。 該位址便稱為對齊 4n + 3，其中 4 表示所選的 2 的乘冪。 位址的對齊方式取決於所選 2 的乘冪。 相同位址取 8 的模數為 7。 如果位址的對齊方式為 Xn+0，則稱為對齊 X。

Cpu 會儲存在記憶體中的資料上執行操作的指示。 資料會在記憶體中的地址所識別。 之外，資料也有大小。 我們呼叫 datum*自然對齊*如果其位址對齊其大小。 它會呼叫*不當*否則。 比方說，如果用來識別它的位址必須是 8 位元組對齊 8 位元組浮點數資料是自然對齊。

## <a name="compiler-handling-of-data-alignment"></a>資料對齊的編譯器處理

編譯器嘗試要在不會將資料對齊錯誤中的資料配置。

針對簡單的資料類型，編譯器指派的位址會是以位元組為單位之資料類型大小的倍數。 比方說，編譯器會將位址指派給類型的變數`long`是 4，將下方的地址的 2 位元設定為零的倍數。

編譯器也會填補在某種程度的自然對齊結構的每個項目中的結構。 請考慮結構`struct x_`以下的程式碼範例：

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} MyStruct;
```

編譯器會填補這個結構，以便強制執行自然對齊。

下列程式碼範例會示範編譯器如何將填補好的結構放在記憶體中：

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
}
```

1. 這兩個宣告都傳回`sizeof(struct x_)`12 個位元組。

1. 第二個宣告包含兩個填補項目：

1. `char _pad0[3]` 若要對齊`int b`4 位元組界限上的成員

1. `char _pad1[1]` 若要對齊陣列的項目結構 `struct _x bar[3];`

1. 邊框距離對齊的項目`bar[3]`允許自然存取的方式。

下列程式碼範例示範`bar[3]`陣列配置：

```Output
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="see-also"></a>另請參閱

[資料結構對齊](https://en.wikipedia.org/wiki/Data_structure_alignment)
