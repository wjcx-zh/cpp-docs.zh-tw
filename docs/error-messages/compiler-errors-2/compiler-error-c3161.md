---
title: 編譯器錯誤 C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 22ecc176036308699c3ad7bd8c015836be910073
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174206"
---
# <a name="compiler-error-c3161"></a>編譯器錯誤 C3161

'interface': 巢狀類別、 結構、 等位或介面中的介面是不合法;類別、 結構或等位中的巢狀介面是不合法

[__Interface](../../cpp/interface.md)只可以出現在全域範圍或命名空間內。 類別、 結構或等位不能出現在介面中。

## <a name="example"></a>範例

下列範例會產生 C3161。

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```