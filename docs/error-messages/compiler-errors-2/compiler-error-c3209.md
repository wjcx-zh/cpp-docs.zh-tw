---
title: 編譯器錯誤 C3209
ms.date: 11/04/2016
f1_keywords:
- C3209
helpviewer_keywords:
- C3209
ms.assetid: 1de44e39-69d1-4894-8f89-ff92136e8e5d
ms.openlocfilehash: f907d0605cccf0a36abd1361d8c87a783bb81506
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243241"
---
# <a name="compiler-error-c3209"></a>編譯器錯誤 C3209

'class': 泛型類別必須是 managed 或 WinRTclass

泛型類別必須是 Managed 類別或 Windows 執行階段類別。

下列範例會產生 C3209，並示範如何修正此問題：

```
// C3209.cpp
// compile with: /clr
generic <class T>
class C {};   // C3209

// OK - ref class can be generic
generic <class T>
ref class D {};
```