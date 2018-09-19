---
title: 編譯器警告 （層級 1） C4103 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4103
dev_langs:
- C++
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1942acc2d9c5c274806e06127f9f98d4bfcb5077
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085533"
---
# <a name="compiler-warning-level-1-c4103"></a>編譯器警告 （層級 1） C4103

'filename': 包含標頭之後, 變更的對齊方式可能是因為缺少 #pragma pack(pop)

封裝會影響配置的類別，而且情況下，如果封裝標頭檔之間的變更，可以有問題。

使用 #pragma[組件](../../preprocessor/pack.md)(pop) 前結束標頭檔，若要解決這個警告。

下列範例會產生 C4103:

```
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

然後，

```
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```