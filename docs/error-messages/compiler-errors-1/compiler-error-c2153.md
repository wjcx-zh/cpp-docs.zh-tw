---
title: 編譯器錯誤 C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: eeb7da509ffb1b8c408763c79d471586eb94f383
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605929"
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