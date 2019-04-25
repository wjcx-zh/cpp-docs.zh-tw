---
title: 編譯器警告 (層級 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: c96db3d4bd1124c96b22363531b7739d0757b613
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160805"
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