---
title: 編譯器錯誤 C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: 9f083f5c21e494d08374e72155b44ee14719881f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743142"
---
# <a name="compiler-error-c3387"></a>編譯器錯誤 C3387

' member '： __declspec （dllexport）/\__declspec （dllimport）無法套用至 managed 或 WinRT 類型的成員

`dllimport` 和[dllexport](../../cpp/dllexport-dllimport.md) `__declspec` 修飾詞在 managed 或 Windows 執行階段類型的成員上無效。

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
