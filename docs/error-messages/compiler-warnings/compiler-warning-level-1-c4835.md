---
title: 編譯器警告（層級1） C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: e59c8a7c9cdd9b892155a7d8ee8c8259324c2045
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052311"
---
# <a name="compiler-warning-level-1-c4835"></a>編譯器警告（層級1） C4835

' variable '：在主機元件中第一次執行 managed 程式碼之前，將不會執行已匯出資料的初始化運算式

在受管理元件之間存取資料時，建議您不要使用原生C++匯入和匯出機制。 相反地，請在 managed 類型中宣告您的資料成員，並使用用戶端中的 `#using` 來參考中繼資料。 如需詳細資訊，請參閱 [#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C4835。

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>範例

下列範例會使用上一個範例中所建立的元件，顯示變數的值不會如預期般。

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