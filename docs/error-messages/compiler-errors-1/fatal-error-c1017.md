---
title: 嚴重錯誤 C1017 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1017
dev_langs:
- C++
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc2cb8ef9c7c9fe8eea7c506e55c49878b9bd809
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108519"
---
# <a name="fatal-error-c1017"></a>嚴重錯誤 C1017

無效的整數常數運算式

中的運算式`#if`指示詞不存在或未評估為常數。

使用定義的常數`#define`必須評估為整數常數，如果所使用的值`#if`， `#elif`，或`#else`指示詞。

下列範例會產生 C1017:

```
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

可能的解決方式：

```
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

因為`CONSTANT_NAME`成字串，而不是整數，會評估`#if`指示詞會產生嚴重錯誤 C1017。

在其他情況下，前置處理器會評估為零未定義的常數。 這會導致非預期的結果，如下列範例所示。 `YES` 未定義，因此它會評估為零。 運算式`#if``CONSTANT_NAME`評估為 false，而且在上使用的程式碼`YES`由前置處理器會移除。 `NO` 也是未定義 （零），因此`#elif``CONSTANT_NAME==NO`評估為 true (`0 == 0`)，造成離開程式碼中的前置處理器`#elif`陳述式部分 — 完全預期的行為相反。

```
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

若要查看確切編譯器如何處理前置處理器指示詞，請使用[/P](../../build/reference/p-preprocess-to-a-file.md)， [/E](../../build/reference/e-preprocess-to-stdout.md)，或[/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)。