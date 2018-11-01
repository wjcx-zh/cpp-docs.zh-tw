---
title: 編譯器警告 (層級 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: c96db3d4bd1124c96b22363531b7739d0757b613
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624009"
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