---
title: 編譯器警告 (層級 1) C4555
ms.date: 11/04/2016
f1_keywords:
- C4555
helpviewer_keywords:
- C4555
ms.assetid: 50b286c1-f7bf-4292-b1fa-baaac9538611
ms.openlocfilehash: a0f2eb7ea4412e7d4f07711e59218abd8c0115b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397324"
---
# <a name="compiler-warning-level-1-c4555"></a>編譯器警告 (層級 1) C4555

運算式無效; 必須是具有副作用的運算式

這個警告會通知您運算式時沒有任何作用。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

例如: 

```
// C4555.cpp
// compile with: /W1
#pragma warning(default:4555)

void func1()
{
   1;   // C4555
}

void func2()
{
   int x;
   x;   // C4555
}

int main()
{
}
```