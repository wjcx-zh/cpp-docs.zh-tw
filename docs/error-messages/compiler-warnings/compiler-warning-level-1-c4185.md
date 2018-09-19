---
title: 編譯器警告 （層級 1） C4185 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4185
dev_langs:
- C++
helpviewer_keywords:
- C4185
ms.assetid: 37e7063a-35b1-4e05-ae31-e811dced02b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acd6750eff911f52cdf656aa4e9a54cfe084ff00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027371"
---
# <a name="compiler-warning-level-1-c4185"></a>編譯器警告 (層級 1) C4185

忽略未知的 #import 屬性 'attribute'

屬性不是 `#import`的有效屬性。 會忽略此項。

## <a name="example"></a>範例

```
// C4185.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_such_attribute   // C4185
```