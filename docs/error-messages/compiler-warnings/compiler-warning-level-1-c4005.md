---
title: 編譯器警告（層級1） C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 4e95f8deeb61c5a4d56e0643beb6a746f848e33e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164725"
---
# <a name="compiler-warning-level-1-c4005"></a>編譯器警告（層級1） C4005

' identifier '：宏重新定義

宏識別碼定義了兩次。 編譯器會使用第二個巨集定義。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 使用 `#define` 指示詞，在命令列和程式碼中定義宏。

1. 從 include 檔案匯入的宏。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 請移除其中一個定義。

1. 在第二個定義之前，請使用[#undef](../../preprocessor/hash-undef-directive-c-cpp.md)指示詞。

下列範例會產生 C4005：

```cpp
// C4005.cpp
// compile with: /W1 /EHsc
#include <iostream>
using namespace std;

#define TEST "test1"
#define TEST "test2"   // C4005 delete or rename to resolve the warning

int main() {
   cout << TEST << endl;
}
```
