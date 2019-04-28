---
title: 編譯器錯誤 C2458
ms.date: 11/04/2016
f1_keywords:
- C2458
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
ms.openlocfilehash: 8131b259f89c5cacd07d04edbf6c45adaa25b145
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367989"
---
# <a name="compiler-error-c2458"></a>編譯器錯誤 C2458

'identifier': 重複定義內定義

類別、 結構、 等位或列舉型別重新定義它自己宣告中。

下列範例會產生 C2458:

```
// C2458.cpp
class C {
   enum i { C };   // C2458
};
```