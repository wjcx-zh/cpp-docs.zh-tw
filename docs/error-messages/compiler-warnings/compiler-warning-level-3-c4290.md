---
title: 編譯器警告 （層級 3） C4290 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4290
dev_langs:
- C++
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a6f09d8f3396381f34a0fbe3c7150b5948cee01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46015962"
---
# <a name="compiler-warning-level-3-c4290"></a>編譯器警告 (層級 3) C4290

忽略除了將函式的 c + + 例外狀況規格不是 __declspec （nothrow）

使用例外狀況規格，其中 Visual c + + 接受，但不會實作來宣告的函式。 設定程式碼在編譯期間遭到忽略的規則可能需要重新編譯的例外狀況，並連結至可重複使用在未來支援例外狀況規格的版本。

如需詳細資訊，請參閱 <<c0> [ 例外狀況規格 (throw)](../../cpp/exception-specifications-throw-cpp.md) 。

您可以使用，以避免這個警告[警告](../../preprocessor/warning.md)pragma:

```
#pragma warning( disable : 4290 )
```

下列程式碼範例會產生 C4290:

```
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```