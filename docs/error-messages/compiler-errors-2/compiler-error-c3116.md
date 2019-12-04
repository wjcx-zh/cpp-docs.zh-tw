---
title: 編譯器錯誤 C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: d0c8e7cab936171f89b33c90b4134a97c40b2c81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741179"
---
# <a name="compiler-error-c3116"></a>編譯器錯誤 C3116

' storage 規範 '：介面方法的儲存類別無效

您使用 `typedef`、`register`或 `static` 做為介面方法的儲存類別。 介面成員上不允許這些儲存類別。

下列範例會產生 C3116：

```cpp
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```
