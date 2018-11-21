---
title: 結構對齊範例
ms.date: 11/19/2018
helpviewer_keywords:
- structure alignment
- examples [C++], structure alignment
ms.assetid: 03d137bf-5cc4-472e-9583-6498f2534199
ms.openlocfilehash: 7c4b3ae29674e9c4fc27e8e175867339001b9a0d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175336"
---
# <a name="examples-of-structure-alignment"></a>結構對齊範例

下列四個範例每個宣告的對齊的結構或等位和對應的圖表說明該結構或等位在記憶體中的版面配置。 在圖中的每個資料行代表一個位元組的記憶體，以及資料行中的數字表示該位元組位移。 每一個圖形的第二個資料列中的名稱對應中宣告的變數的名稱。 網底的資料行表示填補，才能達到指定的對齊方式。

## <a name="example-1"></a>範例 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![AMD 轉換範例 1 結構配置](../build/media/vcamd_conv_ex_1_block.png "AMD 轉換範例 1 結構配置")

## <a name="example-2"></a>範例 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![AMD 轉換範例 2 結構配置](../build/media/vcamd_conv_ex_2_block.png "AMD 轉換範例 2 結構配置")

## <a name="example-3"></a>範例 3

```C
// Total size = 22 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![AMD 轉換範例 2 結構配置](../build/media/vcamd_conv_ex_3_block.png "AMD 轉換範例 2 結構配置")

## <a name="example-4"></a>範例 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD 轉換範例 4 的聯集 layouit](../build/media/vcamd_conv_ex_4_block.png "AMD 轉換範例 4 的聯集 layouit")

## <a name="see-also"></a>另請參閱

[類型和儲存區](../build/types-and-storage.md)<br/>
