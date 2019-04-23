---
title: 編譯器錯誤 C3283
ms.date: 11/04/2016
f1_keywords:
- C3283
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
ms.openlocfilehash: 593b04b8593e261aa1980ada7693300b52a869c5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777402"
---
# <a name="compiler-error-c3283"></a>編譯器錯誤 C3283

'type': 介面不能有執行個體建構函式

CLR [介面](../../extensions/interface-class-cpp-component-extensions.md) 不能有執行個體建構函式。  允許靜態建構函式。

下列範例會產生 C3283：

```
// C3283.cpp
// compile with: /clr
interface class I {
   I();   // C3283
};
```

可能的解決方式：

```
// C3283b.cpp
// compile with: /clr /c
interface class I {
   static I(){}
};
```