---
title: 編譯器錯誤 C2492 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fcb9058bf1aac584e8b7728616f821bda4b33f6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096271"
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