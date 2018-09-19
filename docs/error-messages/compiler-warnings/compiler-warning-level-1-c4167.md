---
title: 編譯器警告 （層級 1） C4167 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4167
dev_langs:
- C++
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c154a91c21bf0b35493bb8033e5453ef1c536267
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082179"
---
# <a name="compiler-warning-level-1-c4167"></a>編譯器警告 (層級 1) C4167

函式：僅供用為內建函式

**#pragma 函式** 嘗試強制編譯器對必須用於內建形式的函式使用傳統呼叫。 忽略 pragma。

若要避免這個警告，請移除 **#pragma 函式**。

## <a name="example"></a>範例

```
// C4167.cpp
// compile with: /W1
#include <malloc.h>
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only
int main(){}
```