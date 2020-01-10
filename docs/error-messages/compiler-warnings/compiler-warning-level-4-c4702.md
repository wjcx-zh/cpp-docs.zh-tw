---
title: 編譯器警告 (層級 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 5e46bfef925f999ed7f04b5bbe7c88800209ed14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990643"
---
# <a name="compiler-warning-level-4-c4702"></a>編譯器警告 (層級 4) C4702

無法連線的程式碼

這項警告是針對 Visual Studio .NET 2003：無法連線的程式碼所進行的編譯器一致性工作所產生的結果。 當編譯器（後端）偵測到無法連線的程式碼時，它會產生 C4702，這是層級4警告。

對於在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++中都有效的程式碼，請移除無法連接的程式碼，或確定某個執行流程可以連線到所有原始程式碼。

## <a name="example"></a>範例

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

## <a name="example"></a>範例

使用 **/gx**、 **/EHc**、 **/ehsc**或 **/EHac**進行編譯並使用 extern c 函式時，程式碼可能會變成無法存取，因為 extern c 函式假設為不擲回，因此無法連線到 catch 區塊。  如果您覺得這個警告無效，是因為函式可以擲回、使用 **/eha**或 **/ehs**進行編譯（視擲回的例外狀況而定）。

如需詳細資訊，請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md) 。

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
