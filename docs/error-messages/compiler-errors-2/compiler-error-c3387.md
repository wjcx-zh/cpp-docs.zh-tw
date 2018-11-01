---
title: 編譯器錯誤 C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: bd783d9510b1699b33f108a4ce8d8c491028b758
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541892"
---
# <a name="compiler-error-c3387"></a>編譯器錯誤 C3387

'member': __declspec （dllexport) /\__declspec(dllimport) 無法套用至成員的 managed 或 WinRT 類型

`dllimport`並[dllexport](../../cpp/dllexport-dllimport.md) `__declspec`修飾詞不是有效的 managed 成員或 Windows 執行階段型別上。

下列範例會產生 C3387，並示範如何修正此問題：

```
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```