---
title: 編譯器警告 (層級 1) C4293
description: 描述 MSVC 編譯器警告 C4293 的原因，並說明如何修正此問題。
ms.date: 07/15/2020
f1_keywords:
- C4293
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
ms.openlocfilehash: 3b5a05d4a744b084f1cc34210a5374962064e85d
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446472"
---
# <a name="compiler-warning-level-1-c4293"></a>編譯器警告 (層級 1) C4293

> '*operator*'：移位元數目為負值或太大，未定義的行為

如果移位元數目為負數或太大，則產生之影像的行為會是未定義的。

## <a name="remarks"></a>備註

若要解決這個問題，您可以在第一個運算元上使用 cast，將它展開為結果類型的大小。

## <a name="example"></a>範例

下列範例會產生 C4293，並顯示解決此問題的方法：

```cpp
// C4293.cpp
// compile with: /c /W1
unsigned __int64 combine (unsigned lo, unsigned hi)
{
   return (hi << 32) | lo;   // C4293

   // In C, try the following line instead:
   // return ( (unsigned __int64)hi << 32) | lo;
   // In C++, try this line instead:
   // return (static_cast<unsigned __int64>(hi) << 32) | lo;
}
```
