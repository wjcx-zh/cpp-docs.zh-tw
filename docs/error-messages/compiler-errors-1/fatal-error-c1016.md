---
title: 嚴重錯誤 C1016
ms.date: 11/04/2016
f1_keywords:
- C1016
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
ms.openlocfilehash: 7463c6962817716611f3571e073712f374773fa7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566032"
---
# <a name="fatal-error-c1016"></a>嚴重錯誤 C1016

\#ifdef 必須是識別項 #ifndef 必須是識別項

條件式編譯指示詞 ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md) 或 `#ifndef`) 沒有要評估的識別項。 若要解決這個錯誤，請指定識別項。

下列範例會產生 C1016：

```
// C1016.cpp
#ifdef   // C1016
#define FC1016
#endif

int main() {}
```

可能的解決方式：

```
// C1016b.cpp
#ifdef X
#define FC1016
#endif

int main() {}
```