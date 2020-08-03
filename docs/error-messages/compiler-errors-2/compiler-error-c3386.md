---
title: 編譯器錯誤 C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: efe882db447b9ebc69d02e3b10d9e484a3cfd8a8
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520444"
---
# <a name="compiler-error-c3386"></a>編譯器錯誤 C3386

> '*type-name*'： `__declspec(dllexport)` / `__declspec(dllimport)` 不能套用至 managed 或 WinRT 類型

和修飾詞 [`dllimport`](../../cpp/dllexport-dllimport.md) [`dllexport`](../../cpp/dllexport-dllimport.md) **`__declspec`** 在 managed 或 Windows 執行階段類型上無效。

下列範例會產生 C3386，並示範如何修正此問題：

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
