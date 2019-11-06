---
title: 編譯器警告 (層級 1) C4185
ms.date: 11/04/2016
f1_keywords:
- C4185
helpviewer_keywords:
- C4185
ms.assetid: 37e7063a-35b1-4e05-ae31-e811dced02b9
ms.openlocfilehash: 6c818f99afb4cd60f5e129f48494aee0c24ba86a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626204"
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