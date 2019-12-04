---
title: 編譯器錯誤 C2372
ms.date: 11/04/2016
f1_keywords:
- C2372
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
ms.openlocfilehash: d5f4653ded6d2800d74418a712bbcb3d4d4d6676
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745612"
---
# <a name="compiler-error-c2372"></a>編譯器錯誤 C2372

' identifier '：重複定義;不同類型的間接取值

已使用不同的衍生型別定義識別碼。

下列範例會產生 C2326：

```cpp
// C2372.cpp
// compile with: /c
extern int *fp;
extern int fp[];   // C2372
extern int fp2[];   // OK
```
