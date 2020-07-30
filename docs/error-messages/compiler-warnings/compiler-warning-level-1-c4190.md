---
title: 編譯器警告（層級1） C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 8187926f2477a4d3f1ca3019cc8c3c71710c1dff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233297"
---
# <a name="compiler-warning-level-1-c4190"></a>編譯器警告（層級1） C4190

' identifier1 ' 已指定 C-連結，但傳回的 UDT ' identifier2 ' 與 C 不相容

函式或函式的指標有 UDT （使用者定義型別，也就是類別、結構、列舉或等位）做為傳回型別和 `extern "C"` 連結。 這在下列情況下是合法的：

- 所有對此函式的呼叫都會從 c + + 進行。

- 函式的定義是在 c + + 中。

## <a name="example"></a>範例

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```
