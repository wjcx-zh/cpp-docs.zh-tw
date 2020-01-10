---
title: 嚴重錯誤 C1016
ms.date: 11/04/2016
f1_keywords:
- C1016
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
ms.openlocfilehash: b5774503297c596a351d72f3af4de6040628b078
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756951"
---
# <a name="fatal-error-c1016"></a>嚴重錯誤 C1016

\#ifdef 預期識別碼 # ifndef 必須是識別碼

條件式編譯指示詞 ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md) 或 `#ifndef`) 沒有要評估的識別項。 若要解決這個錯誤，請指定識別項。

下列範例會產生 C1016：

```cpp
// C1016.cpp
#ifdef   // C1016
#define FC1016
#endif

int main() {}
```

可能的解決方案：

```cpp
// C1016b.cpp
#ifdef X
#define FC1016
#endif

int main() {}
```
