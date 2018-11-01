---
title: 編譯器警告 （層級 2） C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: 4c5c10ee0ea3242e52e6db5391694c9ddf941a78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527669"
---
# <a name="compiler-warning-level-2-c4150"></a>編譯器警告 （層級 2） C4150

刪除的指標不完整類型 'type';呼叫沒有解構函式

**刪除**刪除的類型已宣告但未定義，因此編譯器找不到解構函式呼叫運算子。

下列範例會產生 C4150:

```
// C4150.cpp
// compile with: /W2
class  IncClass;

void NoDestruct( IncClass* pIncClass )
{
   delete pIncClass;
} // C4150, define class to resolve

int main()
{
}
```