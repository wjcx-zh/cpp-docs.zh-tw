---
title: 編譯器錯誤 C3386
ms.date: 11/04/2016
f1_keywords:
- C3386
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
ms.openlocfilehash: ca78433fcb835ad60b553be28ea746f0f880b315
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743246"
---
# <a name="compiler-error-c3386"></a>編譯器錯誤 C3386

' type '： __declspec （dllexport）/\__declspec （dllimport）無法套用至 managed 或 WinRTtype

`dllimport` 和[dllexport](../../cpp/dllexport-dllimport.md) `__declspec` 修飾詞在 managed 或 Windows 執行階段類型上無效。

下列範例會產生 C3386，並示範如何修正此問題：

```cpp
// C3386.cpp
// compile with: /clr /c
ref class __declspec(dllimport) X1 {   // C3386
// try the following line instead
// ref class X1 {
};
```
