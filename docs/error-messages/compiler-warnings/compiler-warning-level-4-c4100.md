---
title: 編譯器警告 (層級 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 84a0b27203cd43e8a8992c4ba599f1400c6909ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401393"
---
# <a name="compiler-warning-level-4-c4100"></a>編譯器警告 (層級 4) C4100

'identifier': 未參考的型式參數

函式主體中未參考的型式參數。 會忽略未參考的參數。

程式碼上呼叫解構函式時，也可能發出 C4100 未參考的基本類型的參數。  這是視覺效果的限制C++編譯器。

下列範例會產生 C4100:

```
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```