---
title: 編譯器錯誤 C2679
ms.date: 11/04/2016
f1_keywords:
- C2679
helpviewer_keywords:
- C2679
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
ms.openlocfilehash: de5613c306eb12bc11d45e868f502ca04d0a62e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386820"
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