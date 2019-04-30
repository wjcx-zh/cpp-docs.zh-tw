---
title: 編譯器錯誤 C2208
ms.date: 11/04/2016
f1_keywords:
- C2208
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
ms.openlocfilehash: 7970ba5d8d2b19bd6e330fad1879880fc5cbf32d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400444"
---
# <a name="compiler-error-c2208"></a>編譯器錯誤 C2208

'type': 沒有使用此類型定義的成員

解析為型別名稱識別項是在彙總的宣告中，但編譯器無法宣告的成員。

下列範例會產生 C2208:

```
// C2208.cpp
class C {
   C;   // C2208
   C(){}   // OK
};
```