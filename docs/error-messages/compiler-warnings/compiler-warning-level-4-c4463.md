---
title: 編譯器警告（層級4） C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: acc7957493942a9c0e19ce098b74ed0b5d75a12d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214356"
---
# <a name="compiler-warning-level-4-c4463"></a>編譯器警告（層級4） C4463

> 溢出將*值*指派給位欄位，其中只能保存從*low_value*到*high_value*的值

指派的*值*超出位欄位可以保存的值範圍。 帶正負號的位欄位類型會使用高序位的符號，因此如果*n*是位欄位的大小，已簽署之位欄位的範圍會是-2<sup>n-1</sup>到 2<sup>n-1</sup>-1，而不帶正負號的位欄位的範圍是從0到 2<sup>n</sup>-1。

## <a name="example"></a>範例

這個範例會產生 C4463，因為它會嘗試指派3的值給類型的位欄位 **`int`** ，其大小為2，其範圍從-2 到1。

若要修正這個問題，您可以將指派的值變更為允許範圍中的某個值。 如果位欄位的目的是要在0到3的範圍內保存不帶正負號的值，您可以將宣告類型變更為 **`unsigned`** 。 如果欄位要保存範圍-4 到3的值，您可以將 [位欄位大小] 變更為3。

```cpp
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S {
    int x : 2; // int type treats high-order bit as sign
};

int main() {
    S s;
    s.x = 3; // warning C4463: overflow; assigning 3
    // to bit-field that can only hold values from -2 to 1
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type
    // to unsigned.
}
```
