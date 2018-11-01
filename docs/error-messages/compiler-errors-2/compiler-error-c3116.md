---
title: 編譯器錯誤 C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: 3f587bc677d64bda0fb5eea0b7ebc8d5761a2e75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612011"
---
# <a name="compiler-error-c3116"></a>編譯器錯誤 C3116

'儲存體 specifier': 介面方法的無效儲存類別

您可以使用`typedef`， `register`，或`static`為介面方法的儲存體類別。 在介面成員上不允許這些儲存體類別。

下列範例會產生 C3116:

```
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```