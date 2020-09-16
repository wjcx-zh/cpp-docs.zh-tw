---
title: 編譯器警告 (層級 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: a2d1f6f4bdc20a35638274e2099c00428f4f6ddf
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684283"
---
# <a name="compiler-warning-level-4-c4702"></a>編譯器警告 (層級 4) C4702

無法連線的程式碼

這項警告是針對 Visual Studio .NET 2003：無法連線的程式碼所進行的編譯器一致性工作所產生的結果。 當編譯器 (後端) 偵測到無法連線的程式碼時，它會產生 C4702，也就是層級4警告。

對於在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++ 中都有效的程式碼，請移除無法連接的程式碼，或確定某些執行流程可以連接到所有的原始程式碼。

## <a name="examples"></a>範例

下列範例會產生 C4702。

```cpp
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

使用 **/gx**、 **/EHc**、 **/ehsc**或 **/EHac** 進行編譯並使用 extern c 函式時，程式碼可能會變成無法存取，因為會假設 extern c 函式不會擲回，因此無法連線到 catch 區塊。  如果您認為這個警告無效是因為函式可能會擲回，請視擲回的例外狀況，使用 **/eha** 或 **/ehs**進行編譯。

如需詳細資訊，請參閱 [/EH (例外狀況處理模型) ](../../build/reference/eh-exception-handling-model.md) 以取得詳細資訊。

下列範例會產生 C4702。

```cpp
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```
