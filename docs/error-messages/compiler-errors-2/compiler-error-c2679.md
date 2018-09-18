---
title: 編譯器錯誤 C2679 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2679
dev_langs:
- C++
helpviewer_keywords:
- C2679
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a01a79dfdff06c50b65bde33de62676e6df64a82
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069491"
---
# <a name="compiler-error-c2679"></a>編譯器錯誤 C2679

二元 'operator': 找不到運算子後者會採用右方運算元類型 'type' （或沒有可接受的轉換）

若要使用運算子，您必須針對指定類型進行多載，或針對已定義運算子的類型定義轉換。

下列範例會產生 C2679:

```
// C2679.cpp
class C {
public:
   C();   // no constructor with an int argument
} c;

class D {
public:
   D(int) {}
   D(){}
} d;

int main() {
   c = 10;   // C2679
   d = 10;   // OK
}
```