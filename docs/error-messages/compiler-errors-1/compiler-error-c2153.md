---
title: 編譯器錯誤 C2153 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2153
dev_langs:
- C++
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb3283ff4d27b6c939434ac3df8f8c1febf0eb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051421"
---
# <a name="compiler-error-c2153"></a>編譯器錯誤 C2153

必須至少一個十六進位數字十六進位常數。

十六進位常數 0x0x 和 \x 不會是有效項目。 至少一個十六進位數字必須遵循 x。

下列範例會產生 C2153:

```
// C2153.cpp
int main() {
   int a= 0x;    // C2153
   int b= 0xA;   // OK
}
```