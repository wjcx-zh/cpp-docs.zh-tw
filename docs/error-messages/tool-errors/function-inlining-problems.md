---
title: 函式內嵌問題 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98d0ed20881ef89264f7c162750f600c7f68412b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088133"
---
# <a name="function-inlining-problems"></a>函式內嵌問題

如果您使用內嵌函式，您必須：

- 已實作您包含標頭檔中的內嵌函式。

- 具有內嵌開啟標頭檔。

```
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

然後，

```
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

如果您使用`#pragma inline_depth`編譯器指示詞，請確定您有設定的值為 2 或更新版本。 值為零會關閉內嵌。 也請確定您使用 **/Ob1**或是 **/ob2**編譯器選項。

混用內嵌和非內嵌在不同模組的編譯選項有時會造成問題。 如果函式內嵌開啟建立 c + + 程式庫 ([/Ob1](../../build/reference/ob-inline-function-expansion.md)或是[/ob2](../../build/reference/ob-inline-function-expansion.md))，但對應的標頭檔描述該函式具有內嵌已關閉 （無選項），您會收到錯誤 LNK2001。 函式無法取得內嵌程式碼從標頭檔，但因為它們不在程式庫檔案中沒有任何位址，解析參考。

同樣地，使用內嵌函式的專案尚未定義函式的.cpp 檔案中而不是在標頭檔也會取得 LNK2019。 標頭檔會包含所有位置被視為適當，但函式只會內嵌時的.cpp 檔通過編譯器;因此，連結器會將函式視為其他模組中使用時，無法解析外部符號。

```
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

然後，

```
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

然後，

```
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>另請參閱

[連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)