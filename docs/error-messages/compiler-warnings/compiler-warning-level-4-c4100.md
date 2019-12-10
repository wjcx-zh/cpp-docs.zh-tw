---
title: 編譯器警告 (層級 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: bcd51c66359d0553b7657d85f5b45ee22d4648ff
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991655"
---
# <a name="compiler-warning-level-4-c4100"></a>編譯器警告 (層級 4) C4100

'identifier'：未參考的型式參數

未在函式主體中參考此型式參數。 已忽略未參考的參數。

當程式碼在屬於基本類型之未參考的參數上呼叫解構函式時，也可能發出 C4100。  這是 Microsoft C++編譯器的限制。

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
