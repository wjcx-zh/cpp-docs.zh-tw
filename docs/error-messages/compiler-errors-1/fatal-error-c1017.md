---
title: 嚴重錯誤 C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: 0feda3bc4c3729d3101be356220aa0124ba85190
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756938"
---
# <a name="fatal-error-c1017"></a>嚴重錯誤 C1017

無效的整數常數運算式

`#if` 指示詞中的運算式不存在，或未評估為常數。

使用 `#define` 所定義的常數，如果用於 `#if`、`#elif`或 `#else` 指示詞中，則其值必須評估為整數常數。

下列範例會產生 C1017：

```cpp
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

可能的解決方案：

```cpp
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

因為 `CONSTANT_NAME` 會評估為字串，而不是整數，所以 `#if` 指示詞會產生嚴重錯誤 C1017。

在其他情況下，預處理器會將未定義的常數評估為零。 這可能會導致非預期的結果，如下列範例所示。 `YES` 未定義，因此會評估為零。 運算式 `#if` `CONSTANT_NAME` 會評估為 false，而且預處理器會移除 `YES` 上所使用的程式碼。 `NO` 也是未定義的（零），因此 `#elif` `CONSTANT_NAME==NO` 會評估為 true （`0 == 0`），使預處理器將程式碼保留在語句的 `#elif` 部分中，這與預期的行為相反。

```cpp
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

若要查看編譯器處理預處理器指示詞的確切方式，請使用[/p](../../build/reference/p-preprocess-to-a-file.md)、 [/e](../../build/reference/e-preprocess-to-stdout.md)或[/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)。
