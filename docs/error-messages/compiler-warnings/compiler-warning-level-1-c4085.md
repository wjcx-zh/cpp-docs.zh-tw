---
title: 編譯器警告 (層級 1) C4085
ms.date: 11/04/2016
f1_keywords:
- C4085
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
ms.openlocfilehash: 8fc8ddc900299f372f0592b660b132188128c3d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200196"
---
# <a name="compiler-warning-level-1-c4085"></a>編譯器警告 (層級 1) C4085

pragma 參數必須為 'on' 或 'off'

pragma 需要 **on** 或 **off** 參數。 忽略 pragma。

下列範例會產生 C4085：

```cpp
// C4085.cpp
// compile with: /W1 /LD
#pragma optimize( "t", maybe )  // C4085
```
