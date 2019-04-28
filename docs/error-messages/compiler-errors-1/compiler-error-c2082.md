---
title: 編譯器錯誤 C2082
ms.date: 11/04/2016
f1_keywords:
- C2082
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
ms.openlocfilehash: 8bfb54dc91ef9132e3930e2c0799070f80f5cd0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338619"
---
# <a name="compiler-error-c2082"></a>編譯器錯誤 C2082

型式參數 'identifier' 重複定義

某個函式的型式參數已在函式主體內重新宣告。 若要解決此錯誤，請移除重複定義。

下列範例會產生 C2082：

```
// C2082.cpp
void func(int i) {
   int i;   // C2082
   int ii;   // OK
}
```