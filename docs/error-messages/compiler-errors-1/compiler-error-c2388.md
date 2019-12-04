---
title: 編譯器錯誤 C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 21658a659468a6e2a0d911af70eefdaed320446c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745053"
---
# <a name="compiler-error-c2388"></a>編譯器錯誤 C2388

' symbol '：符號不能同時以 __declspec （appdomain）和 \__declspec （進程）宣告

`appdomain` 和 `process` `__declspec` 修飾詞不能用在相同的符號上。 變數的儲存體依處理序或應用程式定義域而存在。

如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和 [處理序](../../cpp/process.md)。

下列範例會產生 C2388：

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
