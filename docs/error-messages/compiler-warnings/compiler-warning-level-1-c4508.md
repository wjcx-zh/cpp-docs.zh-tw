---
title: 編譯器警告 （層級 1） C4508 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4508
dev_langs:
- C++
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5abc1d81c3e94c02a63f73c84f3f5e5c7e9b0b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038934"
---
# <a name="compiler-warning-level-1-c4508"></a>編譯器警告 (層級 1) C4508

'function': 函式應傳回值。'void' 的傳回型別假設

此函式有沒有指定的傳回類型。 在此情況下，應該也會引發 C4430 和編譯器實作的 C4430 （預設值是 int） 所報告的修正。

若要解決這個警告，明確宣告函式的傳回型別。

下列範例會產生 C4508:

```
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```