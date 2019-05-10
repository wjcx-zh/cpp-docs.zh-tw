---
title: 編譯器警告 (層級 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: ccb438cf7c80edb1403683ac4817617ffccc690d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447738"
---
# <a name="compiler-warning-level-4-c4100"></a>編譯器警告 (層級 4) C4100

'identifier': 未參考的型式參數

函式主體中未參考的型式參數。 會忽略未參考的參數。

程式碼上呼叫解構函式時，也可能發出 C4100 未參考的基本類型的參數。  這是 Microsoft 的限制C++編譯器。

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