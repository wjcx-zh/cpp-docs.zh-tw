---
title: 編譯器警告 (層級 1) C4684
ms.date: 11/04/2016
f1_keywords:
- C4684
helpviewer_keywords:
- C4684
ms.assetid: e95f1a83-2784-4b05-ae94-12148e056e26
ms.openlocfilehash: 8ba3d75ecb370ac86c9a6ab47f05dd49fc12ba23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479114"
---
# <a name="compiler-warning-level-1-c4684"></a>編譯器警告 (層級 1) C4684

'attribute': 警告!! 屬性可能造成無效的程式碼產生： 請小心使用

您已使用應該不常使用的屬性。

下列範例會產生 C4684:

```
// C4684.cpp
// compile with: /W1 /LD
[module(name="xx")]; // C4684 expected
[no_injected_text];
```