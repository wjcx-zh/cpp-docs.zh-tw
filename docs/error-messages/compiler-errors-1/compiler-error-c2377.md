---
title: 編譯器錯誤 C2377
ms.date: 11/04/2016
f1_keywords:
- C2377
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
ms.openlocfilehash: 2bf73aa9aee2a45e5271570b4c45c8fecaa4a4bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225536"
---
# <a name="compiler-error-c2377"></a>編譯器錯誤 C2377

'identifier' : 重複定義; typedef 無法以其他符號多載

**`typedef`** 已重新定義識別碼。

下列範例會產生 C2377：

```cpp
// C2377.cpp
// compile with: /c
typedef int i;
int i;   // C2377
int j;   // OK
```
