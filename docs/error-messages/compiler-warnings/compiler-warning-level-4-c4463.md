---
title: 編譯器警告 （層級 4） C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: e125a532f87533958ec43ed5580665ad4108856b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400795"
---
# <a name="compiler-warning-level-4-c4463"></a>編譯器警告 （層級 4） C4463

> 溢位;指派*值*只能保留值的位元欄位*low_value*到*high_value*

受指派*值*超出範圍的位元欄位可以保留的值。 帶正負號的位元欄位類型使用的高位位元表示正負號，因此，如果*n*是帶正負號的位元欄位是-2 位元欄位大小，範圍<sup>n-1</sup> 2<sup>n-1</sup>-1，而不帶正負號位元欄位必須介於 0 到 2<sup>n</sup>-1。

## <a name="example"></a>範例

此範例會產生 C4463，因為它會嘗試將值 3 指派給位元欄位的型別`int`緩衝區的大小為 2，其具有 1 的範圍從-2。

若要修正此問題，您可以變更指派的值，以允許的範圍中的項目。 如果位元欄位是保存不帶正負號的值，範圍從 0 到 3 中，您可以變更的宣告型別`unsigned`。 如果欄位是儲存於範圍-4 到 3 的值，您可以將位元欄位大小變更為 3。

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
