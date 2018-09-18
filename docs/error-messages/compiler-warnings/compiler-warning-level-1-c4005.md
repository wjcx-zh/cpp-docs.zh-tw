---
title: 編譯器警告 （層級 1） C4005 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4005
dev_langs:
- C++
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8be172086e316c991f461b3ac42f58739801cfa7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022964"
---
# <a name="compiler-warning-level-1-c4005"></a>編譯器警告 （層級 1） C4005

'identifier': 巨集重複定義

巨集識別項定義了兩次。 編譯器會使用第二個巨集定義。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 在命令列上，以及程式碼中定義的巨集`#define`指示詞。

1. 從包含檔案匯入的巨集。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 請移除其中一個定義。

1. 使用[#undef](../../preprocessor/hash-undef-directive-c-cpp.md)指示詞，第二個定義之前。

下列範例會產生 C4005:

```
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