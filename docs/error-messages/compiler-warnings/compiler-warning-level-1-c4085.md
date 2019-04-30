---
title: 編譯器警告 (層級 1) C4085
ms.date: 11/04/2016
f1_keywords:
- C4085
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
ms.openlocfilehash: cfd2296d2e58899bf818281716af2074c2f0ce91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406472"
---
# <a name="compiler-warning-level-1-c4085"></a>編譯器警告 (層級 1) C4085

pragma 參數必須為 'on' 或 'off'

pragma 需要 **on** 或 **off** 參數。 忽略 pragma。

下列範例會產生 C4085：

```
// C4085.cpp
// compile with: /W1 /LD
#pragma optimize( "t", maybe )  // C4085
```