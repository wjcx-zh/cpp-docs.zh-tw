---
title: 編譯器警告（層級1） C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 6d110aa70a470382e274546e95599804fa3bc7d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199871"
---
# <a name="compiler-warning-level-1-c4190"></a>編譯器警告（層級1） C4190

' identifier1 ' 已指定 C-連結，但傳回的 UDT ' identifier2 ' 與 C 不相容

函式或函式的指標有 UDT （使用者定義型別，也就是類別、結構、列舉或等位）做為傳回型別，並 `extern` "C" 連結。 這在下列情況下是合法的：

- 此函式的所有呼叫都C++是從進行。

- 函數的定義在中C++。

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
