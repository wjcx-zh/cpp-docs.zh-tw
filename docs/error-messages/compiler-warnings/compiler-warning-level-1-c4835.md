---
title: 編譯器警告 （層級 1） C4835 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4835
dev_langs:
- C++
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70492be13d312c5d167990cfa0b6c0d741e1055f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080099"
---
# <a name="compiler-warning-level-1-c4835"></a>編譯器警告 (層級 1) C4835

'variable': 匯出資料的初始設定式將不會執行，直到主機組件中第一次執行 managed 程式碼

當存取受管理的元件之間的資料，建議您不使用原生 c + + 匯入和匯出機制。 相反地，宣告您的資料成員內的 managed 類型，並參考中繼資料與`#using`在用戶端。 如需詳細資訊，請參閱 [#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C4835。

```
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>範例

下列範例使用先前的範例中，顯示變數的值未如預期般內建的元件。

```
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