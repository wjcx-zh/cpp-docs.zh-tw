---
title: 編譯器錯誤 C2458
ms.date: 11/04/2016
f1_keywords:
- C2458
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
ms.openlocfilehash: 93e0159ca680b37aed2031c6e2ec41463e7e389d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744000"
---
# <a name="compiler-error-c2458"></a>編譯器錯誤 C2458

' identifier '：定義內的重新定義

類別、結構、等位或列舉會在其本身的宣告中重新定義。

下列範例會產生 C2458：

```cpp
// C2458.cpp
class C {
   enum i { C };   // C2458
};
```
