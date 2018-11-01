---
title: 編譯器錯誤 C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: a9183e1f62e7ebaf5db04a35a45806ec02169e69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637472"
---
# <a name="compiler-error-c3386"></a>編譯器錯誤 C3386

'type': __declspec （dllexport) /\__declspec(dllimport) 無法套用至 managed 或 WinRTtype

`dllimport`並[dllexport](../../cpp/dllexport-dllimport.md) `__declspec`修飾詞不適用於 managed 或 Windows 執行階段型別。

下列範例會產生 C3386，並示範如何修正此問題：

```
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```