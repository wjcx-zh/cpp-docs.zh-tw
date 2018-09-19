---
title: 編譯器警告 （層級 1） C4190 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d398331c159c6fc639160dbe54d6ab5f969d3dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063732"
---
# <a name="compiler-warning-level-1-c4190"></a>編譯器警告 （層級 1） C4190

'identifier1' 具有 C 連結指定，但傳回 UDT 與 C 不相容的 ' identifier2'

函式或函式指標具有 UDT （使用者定義型別，也就是類別、 結構、 列舉或等位） 的傳回型別和`extern`"C"連結。 這是合法的如果：

- 此函式所有呼叫都都由 c + +。

- 函式的定義是以 c + +。

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