---
title: 編譯器錯誤 C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: e2b08ef3e46681147c4efd77cbffadb096bbfc16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590450"
---
# <a name="compiler-error-c2492"></a>編譯器錯誤 C2492

'*變數*': 具有執行緒儲存期的資料可能不會有 dll 介面

在變數宣告與[執行緒](../../cpp/thread.md)屬性，並使用的 DLL 介面。 位址`thread`變數之前無法得知執行階段，因此它無法連結到 DLL 匯入或匯出。

下列範例會產生 C2492:

```
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```