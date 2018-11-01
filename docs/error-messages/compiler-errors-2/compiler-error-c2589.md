---
title: 編譯器錯誤 C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 18d8f7130c34f5e1e33bc7aa9b9463f50c243045
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587303"
---
# <a name="compiler-error-c2589"></a>編譯器錯誤 C2589

'identifier': 不合法的語彙基元，在右側 ':: '

如果類別、 結構或等位名稱左邊的範圍解析運算子 （雙冒號），在右邊的語彙基元必須是類別、 結構或等位成員。 否則，任何全域識別項可以出現在右邊。

範圍解析運算子無法多載。

下列範例會產生 C2589:

```
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```