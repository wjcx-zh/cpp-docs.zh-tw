---
title: 編譯器錯誤 C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 62afcb1fafc19d3d61a86f2fbc10cb99e095afc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393658"
---
# <a name="compiler-error-c2388"></a>編譯器錯誤 C2388

'symbol': 符號不能宣告這兩個 __declspec(appdomain) 和\__declspec(process)

`appdomain` 和 `process` `__declspec` 修飾詞不能用在相同的符號上。 變數的儲存體依處理序或應用程式定義域而存在。

如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和 [處理序](../../cpp/process.md)。

下列範例會產生 C2388：

```
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```