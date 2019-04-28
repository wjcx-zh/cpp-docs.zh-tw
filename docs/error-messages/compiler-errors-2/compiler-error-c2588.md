---
title: 編譯器錯誤 C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: 15f9ba62751d9b3cb17ab56659310292dab41adf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350448"
---
# <a name="compiler-error-c2588"></a>編譯器錯誤 C2588

':: ~ 識別碼 ': 不合法的全域解構函式

解構函式定義的項目以外的類別、 結構或等位。 這是不允許的。

此錯誤可能因遺失類別、 結構或等位名稱左邊的範圍解析 (`::`) 運算子。

下列範例會產生 C2588:

```
// C2588.cpp
~F();   // C2588
```