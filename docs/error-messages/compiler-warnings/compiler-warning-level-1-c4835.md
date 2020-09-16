---
title: 編譯器警告 (層級 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: a298eb0c55f96289a0043f3a996b09798745c92d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684218"
---
# <a name="compiler-warning-level-1-c4835"></a>編譯器警告 (層級 1) C4835

' variable '：在主機元件中第一次執行 managed 程式碼之前，將不會執行匯出資料的初始化運算式

存取 managed 元件之間的資料時，建議您不要使用原生 c + + 匯入和匯出機制。 相反地，請將您的資料成員宣告在 managed 型別內，並 `#using` 在用戶端中參考的中繼資料。 如需詳細資訊，請參閱 [#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)。

## <a name="examples"></a>範例

下列範例會產生 C4835。

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

下列範例會使用上一個範例中所建立的元件，顯示變數的值不是預期的值。

```cpp
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```
