---
title: 編譯器錯誤 C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: 8218233bb7a92c699952f7a506f6728386af4d17
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221064"
---
# <a name="compiler-error-c3387"></a>編譯器錯誤 C3387

' member '： __declspec （dllexport）/ \_ _declspec （dllimport）無法套用至 managed 或 WinRT 類型的成員

`dllimport`和[dllexport](../../cpp/dllexport-dllimport.md)修飾詞 **`__declspec`** 在 managed 或 Windows 執行階段類型的成員上無效。

下列範例會產生 C3387，並示範如何修正此問題：

```cpp
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```
