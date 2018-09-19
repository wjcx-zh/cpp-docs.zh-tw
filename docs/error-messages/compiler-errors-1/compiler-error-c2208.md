---
title: 編譯器錯誤 C2208 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2208
dev_langs:
- C++
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6721166efad2fc214ccf2c2a45ec2342b67c39e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101710"
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