---
title: 編譯器警告 (層級 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: b587a4ca2a78bc2ac54640adb2b149d97bef4def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174657"
---
# <a name="compiler-warning-level-1-c4920"></a>編譯器警告 (層級 1) C4920

enum 列舉成員 (成員=值) 已出現在 enum 列舉中作為成員=值

如果您傳遞至 #import 的 .tlb 具有定義於兩個或多個列舉中的相同符號，則這個警告表示後續相同的符號將被忽略，而且會在 .tlh 檔中標記為註解。

假設 .tlb 包含：

```
library MyLib
{
    typedef enum {
        enumMember = 512
    } AProblem;

    typedef enum {
        enumMember = 1024
    } BProblem;
};
```

下列範例會產生 C4920。

```cpp
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```
