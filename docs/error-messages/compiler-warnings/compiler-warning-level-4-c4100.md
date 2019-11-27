---
title: 編譯器警告 (層級 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 80794d270b40a8f40d44630da70455c015158423
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541236"
---
# <a name="compiler-warning-level-4-c4100"></a>編譯器警告 (層級 4) C4100

' identifier '：未參考的型式參數

函式主體中未參考正式參數。 忽略未參考的參數。

當程式碼在基本類型的未參考參數上呼叫析構函式時，也可以發出 C4100。  這是 Microsoft C++編譯器的限制。

下列範例會產生 C4100：

```cpp
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