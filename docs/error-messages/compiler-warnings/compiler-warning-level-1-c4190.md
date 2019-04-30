---
title: 編譯器警告 （層級 1） C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 05984594a57878aad8037861a15ac9284ff65192
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386495"
---
# <a name="compiler-warning-level-1-c4190"></a>編譯器警告 （層級 1） C4190

'identifier1' 具有 C 連結指定，但傳回 UDT 與 C 不相容的 ' identifier2'

函式或函式指標具有 UDT （使用者定義型別，也就是類別、 結構、 列舉或等位） 的傳回型別和`extern`"C"連結。 這是合法的如果：

- 此函式所有呼叫都都由C++。

- 函式的定義位於C++。

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