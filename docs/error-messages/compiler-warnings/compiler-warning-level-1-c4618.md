---
title: 編譯器警告 (層級 1) C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: 5e6c945932699119f97bca2d3d118a03665f6f9f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185876"
---
# <a name="compiler-warning-level-1-c4618"></a>編譯器警告 (層級 1) C4618

pragma 參數包含空字串;已忽略 pragma

指定 null 字串做為 **#pragma**的引數。

未以引數處理 pragma。

下列範例會產生 C4618：

```cpp
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```
