---
title: 編譯器錯誤 C2838
ms.date: 11/04/2016
f1_keywords:
- C2838
helpviewer_keywords:
- C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
ms.openlocfilehash: 1482efa8b018914a4ebc509464622726ae9ebb20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383005"
---
# <a name="compiler-error-c2838"></a>編譯器錯誤 C2838

'member': 成員宣告中不合法的限定的名稱

類別、 結構或等位會使用完整限定的名稱，來重新宣告另一個類別、 結構或等位的成員。

下列範例會產生 C2838:

```
// C2838.cpp
// compile with: /c
class Bellini {
public:
    void Norma();
};

class Bottesini {
   Bellini::Norma();  // C2838
};
```