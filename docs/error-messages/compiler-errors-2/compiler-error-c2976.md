---
title: 編譯器錯誤 C2976 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2976
dev_langs:
- C++
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a82cbe896d44190c5d7e6ee098f0f5a7a27e9378
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072910"
---
# <a name="compiler-error-c2976"></a>編譯器錯誤 C2976

'identifier': 類型引數太少

泛型或樣板遺漏一或多個實際的引數。 請檢查泛型或樣板宣告，以找出正確的參數數目。

此錯誤可能因缺少範本引數，在 c + + 標準程式庫元件。

下列範例會產生 C2976:

```
// C2976.cpp
template <class T>
struct TC {
   T t;
};
int main() {
   TC<>* t;   // C2976
   TC<int>* t2;   // OK
}
```

使用泛型時，也會發生 C2976:

```
// C2976b.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC<>^ g;   // C2976
   GC<int>^ g2;   // OK
}
```