---
title: 編譯器警告 (層級 1) C4185
ms.date: 11/04/2016
f1_keywords:
- C4185
helpviewer_keywords:
- C4185
ms.assetid: 37e7063a-35b1-4e05-ae31-e811dced02b9
ms.openlocfilehash: 32da9c7758c00459056a5bbc002e2884cb3c0e3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163438"
---
# <a name="compiler-warning-level-1-c4185"></a>編譯器警告 (層級 1) C4185

忽略未知的 #import 屬性 'attribute'

屬性不是 `#import`的有效屬性。 會忽略此項。

## <a name="example"></a>範例

```cpp
// C4185.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_such_attribute   // C4185
```
