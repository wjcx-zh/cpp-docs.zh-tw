---
title: 編譯器錯誤 C2337
ms.date: 09/19/2019
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: bf9b3e782804add13aeaef0e6672d2dd66d193be
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158780"
---
# <a name="compiler-error-c2337"></a>編譯器錯誤 C2337

> '*attribute-name*'：找不到屬性

您的程式碼使用的屬性在此內容中不受支援。 或者，這個版本的編譯器中不提供屬性。 若要解決此問題，請移除不支援的屬性。

下列範例會產生 C2337：

```cpp
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```
